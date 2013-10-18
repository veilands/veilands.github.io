---
layout: post
categories: university
title: "Darba vide priekš tīmekļa vietnes attālinātas rediģēšanas"
date: 2011-10-15 10:10:10
---

Pirms mesties un izpildīt kādu no laboratorijas darbiem, lai kurā mācību priekšmetā tas arī nebūtu, es rekomendēju izmantot katram darbam atbilstošākus instrumentus, piemēram, ja Tev pēc katra faila rediģēšanas tas vēl ir atsevišķi jāpārsūta caur FTP klientu uz serveri, tas kopumā aizņems papildus laiku un pareizi organizējot savu darba vidi ir iespējams šo lietu nedaudz automatizēt, tas neprasīs vienā reizē vairāk kā 10 minūtes, lai sagatavotu darba vidi, savukārt nākotnē būs ērtāk un patīkamāk strādāt, veidojot tīmekļa vietnes un papildinot tās ar jaunu saturu.

Ņemot vērā darba specifiku un visus tos mācību priekšmetus, kuros mums ir nepieciešams izveidot failus un nogādāt tos līdz serverim es gribētu pievērst Tavu uzmanību divām lietotnēm. Pirmā ir `Notepad++`, kas ir paredzēta ērtai tekstu rediģēšanas ar sintakses vizuālu pasvītrošanu un otrā lietotne ir `WinSCP`, kas ir mūsdienīgs failu apmaiņas klients, ar kura palīdzību var lejupielādēt un augšupielādēt tīmekļa vietnes failus uz serveriem, kuri atbalsta dažādus failu apmaiņas protokolus, tādus kā: `FTP`, `SFTP` un `SCP`.
</br>
<img src="/images/wscp.png" alt="WinSCP Konfigurācijas Parametri" title="WinSCP Konfigurācijas Parametri" style="float:right; padding:0 0 0 1em;"/>
</br>
`Notepad++` ir lejupielādējams no šīs tīmekļa vietnes [notepad-plus-plus.org][notepad] un savukārt `WinSCP` ir lejupielādējams no šīs tīmekļa vietnes [WinSCP.net][winscp]

Šeit nav pareizā secība, kādā šie lietojumi ir jāuzstāda uz Tavas darba stacijas, galvenais šos abus letojumus ir sekmīgi lejupielādēt un uzstādīt līdz galam, tad atliks veikt nelielu `WinSCP` konfigurācijas papildināšanu ar jauniem parametriem un Tu varēsi sākt taupīt laiku uz izmainīto failu augšupielādēšanu.

Pēc abu lietojumu sekmīgas uzstādīšanas ir nepieciešams palaist lietojumu `WinSCP` un piespiest trīs taustiņu kombināciju `Ctr+Alt+P`, kas izsauks labajā pusē redzamo logu.

Šai logā ir nepieciešams ieklikšķināt uz sadaļas, kreisajā kolonnā `Editors` un tālāk ir jāklikšķina uz pogas `Add ...` kas ļaus pievienot jaunu teksta redaktoru šim sarakstam, šeit ir nepieciešams norādīt, ka vēlies izmantot tieši `Notepad++` un ar pogas `Up` palīdzību ir jānovieto `Notepad++` saraksta augšgalā, tas nodrošinās to, ka pēc noklusējuma, failu rediģēšanas režīmā tiks izmantota tieši šī lietotne.

Pēc noklusējuma, lietotne `Notepad++` tiek uzstādītā sekojošā lietojumu ceļā `C:\Program Files\Notepad++`, ja gadījumā lietojuma uzstādīšanas brīdī izvēlējies citu direktoriju, tad to ir nepieciešams norādīt augstāk minētajos nosacījumos.

<img src="/images/wscp-edit.png" alt="WinSCP failu rediģēšana tiešsaistē" title="WinSCP failu rediģēšana tiešsaistē" style="float:left; padding:.5em 1em .5em 0;"/>

Tālāk atliek tikai pieslēgties pie servera izmantojot `WinSCP` lietojumu un Tu varēsi sākt rediģēt failus attālinātā režīmā. Pēc sekmīgas pieslēgšanās pie attālinātā servera ir nepieciešams izvēlēties failu, kuru jārediģē, tad jāveic labais peles klikšķis uz faila nosaukuma un no iznirstošās izvēlnes ir nepieciešams izvēlēties `Edit`, kas atvērs šo failu `Notepad++` lietotnē, kur to ir iespējams rediģēt, saglabājot šo failu ar trīs taustiņu kombināciju `Ctrl+Alt+S` ir iespējams norādīt jaunu nosaukumu vai vienkārši piespiežot divus taustiņu `Ctrl+S`, fails automātiski tiks augšupielādēts un novietots serverī, aizstājot iepriekšējo failu, kas tika sākotnēji atvērts attālinātā rediģēšanas režīmā.

Šīs lapas kreisajā sadaļā ir redzams attēls, kurā ir parādīts, kāda izskatās iznirstošā izvēlne lietotnē `WinSCP`, kurā ir iekrāsota sadaļa `Edit`, kas Tev ir jāklikšķina uz faila nosaukuma, ja Tu to vēlies attālināti rediģēt. Šis ir vienkāršs, bet tai pat laikā gana ērts un parocīgs veids, kādā atvieglot ikdienas darbu ar attālinātiem failiem, pie visa tā lietotne `Notepad++` lieliski tiek galā arī ar `UTF-8` kodējumu, kas mums nodrošina latviešu un krievu valodas simbolus primitīvā tekstā, savukārt `Microsof Notepad` parasti rada vairāk problemu nekā labuma ar pareizu faila kodējuma noteikšanu vai konvertāciju.

Atļaušos atgādināt, lai maksimāli izvairītos no problēmsituācijām, kad tiek pazaudēts stundām vai reizēm pat dienām ilgi ieguldīts darbs, es rekomendēju veidot rezerves kopēšanu pirms sākt rediģēt failus tiešsaistē, tas palīdzēs izvairīties no nevajadzīgiem pārpratumiem un nepatīkamām situācijām, jo šis ir neliels trūkums failu rediģēšanai tiešsaistē, bet savukārt ja Tu rīkosies uzmanīgi un Tev pa rokai būs rezerves kopija no rediģējamā faila, tad gala rezultātā ietaupīsi laiku uz manulālo failu augšupielādēšanu un darbs kļūs patīkamāks, varēsi vairāk koncentrēties uz saturu un mazāk rūpēties par augšupielādi pēc katru izmaiņu izdarīšanas.

[notepad]: http://notepad-plus-plus.org/download/
[winscp]:  http://winscp.net/eng/download.php
