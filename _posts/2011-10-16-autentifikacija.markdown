---
layout: post
categories: university
title: "Primitīvs Lietotāja Autentifikācijas Piemērs"
date: 2011-10-16 10:10:10
---
Vienā no mācību priekšmetiem mums bija jārealizē uzdevums, kur tiek veikta lietotāja autentifikācija un pie sekmīga rezultāta lietotājs tiek autorizēts piekļūt tīmekļa vietnes sadaļai, kas ir paredzēta tikai autentificētiem lietotājiem, piemēram vietnes satura administratoriem. Tā kā mani kursa biedri bija aktīvi uzdodot jautājumus par to, kā tas viss notiek un strādā, tad zemāk ir vienkāršots `PHP` koda paraugs, kurus vari pārskatīt un brīvi izmantot savām vajadzībām.

Kopumā es izveidoju trīs atsevišķus failus un no tiem arī sastāv šis vienkāršotais autentifikācijas paraugs, pirmais fails `index.php`, ir vietnes indeksa fails, kas tiek izpildīts tai brīdi, kad lieotājs pieslēdzās tīmekļa vietnei, šis skripts pārbauda vai lietotājs ir autorizēts piekļūt vietnes administratīvajai sadaļa, vērtības tiek ņemta no globālā mainīgā `$_SESSION['authorized']`, ja šī vērtība ir uzstādīta, tad tiek iekļauta administratīvā sadaļa `admin_form.php` pretējā gadījumā, ja lietotājs nav autorizēts piekļūt administratīvajai sadaļai tiek ielādēta lietotāju autentifikācijas forma no faila `loginform.html`

Ja rūpīgāk aplūkosi `admin_form.php` tad pamanīsi, ka to skriptu var izsaukt arī pa tiešo no url un gadījumā, ja lietotājam nebūs piekļuves tiesības viņš tiks pārsūtīts uz lietotāja autentifikācijas formu uz `index.php` skriptu.

Šis vienkāršotais piemērs ir tikai priekš mācību nolūkiem un produkcijas vidē es nekādā ziņā to neieteiktu izmantot =]

faila `index.php` saturs
{% highlight php %}
<?php
    session_start();
    
    if($_POST['logout']) {
        session_destroy();
        header('Location: index.php');
    }
    
    function CheckPass($username,$password) {
        if ($username == 'user' and md5($password) == '098f6bcd4621d373cade4e832627b4f6') { // password ir test
            return true;
        } else {
            return false;
        }
    }
    
    if($_SESSION['authorized']) {
        include('admin_form.php');
        exit;
    } else {
        $username = trim($_POST['username']);
        $password = trim($_POST['password']);
        $_SESSION['authorized'] = CheckPass($username, $password);
        if($_SESSION['authorized']) {
            $_SESSION['username'] = $username;
            header('Location: index.php');
            exit;
        } else {
            if(isset($_POST['submitted'])) {
                $_SESSION['zinja'] = "Lietotāja autentifikācija ir nesekmīga!<br/><br/>
                            Lūdzu pārbaudi lietotāja vārdu un paroli, tad mēģini vēlreiz!";
            } else {
                $_SESSION['zinja'] = "Lūdzu ievadiet savu lietotāja vārdu un paroli";
            }
        }           
        header('Content-type: text/html; charset=utf-8');
        include('loginform.html');
    }
?>
{% endhighlight %}

faila `loginform.html` saturs
{% highlight html%}
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Lietotāja autentifikācijas forma</title>
    </head>
    <body style="text-align:center;margin:auto;padding:2em;">
        <h1><?php print $_SESSION['zinja']; ?></h1>
        <div style="margin:auto;">
        <form method="POST" accept-charset='UTF-8' action='index.php' style="width:38em;margin:auto;">
            <fieldset>
                <legend>Autentifikācija</legend>
                <input type='hidden' name='submitted' id='submitted' value='1'/>
                <div style="text-align:right;">
                    <label for='username' >Lietotājs:</label>
                    <input type='text' name='username' id='username'  maxlength="50"/>
                    <label for='password' >Parole:</label>
                    <input type='password' name='password' id='password' maxlength="50"/>
                </div>
                <input id="sender" type='submit' name='Submit' value='Nosūtīt'/>
            </fieldset>
        </form>
        </div>
    </body>
</html>
{% endhighlight %}

faila `admin_form.php` saturs
{% highlight php %}
<?php
    session_start();
    if(!$_SESSION['authorized']) {
        header('Location: index.php');
    } else {
        header('Content-type: text/html; charset=utf-8');
    }
?>
{% endhighlight %}
{% highlight html %}
<!DOCTYPE html>
<html>
<head>
    <meta content="text/html; charset=UTF-8" http-equiv="Content-Type" />
    <title>Autorizēta lietotāja sadaļa</title>
    <link rel="stylesheet" href="style.css" />
</head>
    <body>
    <h1>Sveiks lietotāj <?php print $_SESSION['username']; ?>, 
                laipni lūdzam vietnes administratīvajā sadaļā.</h1>

    <p>Šai vietā ir jāievieto saturs, kas ir paredzēts priekš autentificētiem lietotājiem.</p>

    <hr/>
    <div style="text-align:right;">
        <form name="f2" method="POST" accept-charset='UTF-8' action='index.php'>
            <label for="logout">pārtraukt autorizāciju:</label>
            <input type='submit' name='logout' value='Logout' />
        </form>
    </div>
    </body>
</html>
{% endhighlight %}
</br>
