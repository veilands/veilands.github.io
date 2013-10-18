---
layout: post
title:  "Padoms visiem Latvijas Universitātes studentiem"
date:   2011-10-14 10:10:10
categories: university
---

Visiem [LU][lu] studentiem ir piešķirts [serveris][ieva] uz kura studenti var brīvi un pašrocīgi izmitināt statiskas HTML lapas. Uz servera, priekš studentiem nav nekā cita, kā tikai FTP un HTTP, jebkāda veida skriptēšanas iespējas ir liegtas, izņemot Server Side Include, bet par šo iespēju mums diemžēl neviens neko nepastāstīja. Lai pieslēgtos pie servera ir jāizmanto savs [luis][luis] autentifikācijas vārds (stud\_apl\_nr) un parole. Starp citu, FTP servera adrese ir `apse.lanet.lv`. Pirms pāris gadiem man tas likās gaužām vecmodīgi, ka [LU][lu] studentiem netiek nodrošināts super moderns serveris ar vismaz `PHP` preprocesoru, bet šodien, kad pie rokas ir tāds nezvērs kā [Jekyll][jl] man pilnībā pietiek ar šo pašu veco mīļo serverīti, jo tas ir drošāks pret ievainojamībām, nekā tie serveri uz kuriem lietotājiem ir atļauts izmantot dažādas skriptēšanas valodas un arī salīdzinoši atrāks statisku lapu pasniegšanā, jo nekas nav jārēķina, ņem gatavu failu un pa HTTP pūš projām pieprasītājam.

Ja nu gadījumā kādam interesē, tad par šo serverīti man izdevās iegūt sekojošu papildus informāciju, izantojot attālinātās piekļuves termināla konsoli. Šis uzticamais un ilggadējais serveris izrādās ir pietiekami jaudīgs vēl šodien, pēc saviem garajiem darba gadiem, lai pilnībā veiktu savas ikdienas funkcijas, tas nozīmē tikai to, ka uz `IBM` un `AIX` mēs varam pilnībā paļauties un uzticēties, jo šis serveris ir gods godam pildījis tam uzticētās funkcijas un stabīli darbojies jau visus pēdējos 10 gadus =]

{% highlight console %}
$ uname -a
AIX apse 3 5 000BFC0D4C00
$ oslevel -r
5300-08
$ prtconf
System Model: IBM,7028-6C1
Machine Serial Number: 10BFC0D
Processor Type: PowerPC_POWER3
Processor Implementation Mode: POWER 630
Processor Version: PV_630
Number Of Processors: 1
Processor Clock Speed: 375 MHz
CPU Type: 64-bit
Kernel Type: 32-bit
LPAR Info: -1 NULL
Memory Size: 512 MB
Good Memory Size: 512 MB
Platform Firmware level: Not Available
Firmware Version: IBM,CLT05208
Console Login: enable
Auto Restart: true
Full Core: false
 
Network Information
    Host Name: apse
    IP Address: 195.13.129.120
    Sub Netmask: 255.255.255.0
    Gateway: 195.13.129.254
    Name Server: 195.13.129.5
    Domain Name: lanet.lv
 
Paging Space Information
    Total Paging Space: 1024MB
    Percent Used: 6%
 
INSTALLED RESOURCE LIST

The following resources are installed on the machine.
+/- = Added or deleted from Resource List.
*   = Diagnostic support not available.
    
  Model Architecture: chrp
  Model Implementation: Multiple Processor, PCI bus
    
+ sys0                       System Object
+ sysplanar0                 System Planar
* pci1             P1        PCI Bus
* pci0             P1        PCI Bus
* isa0             P1        ISA Bus
+ fda0             P1/D1     Standard I/O Diskette Adapter
+ fd0              P1-D1     Diskette Drive
* siokma0          P1/K1     Keyboard/Mouse Adapter
+ sioka0           P1/K1     Keyboard Adapter
+ sioma0           P1/K1     Mouse Adapter
+ ppa0             P1/R1     CHRP IEEE1284 (ECP) Parallel Port Adapter
+ sa0              P1/S1     Standard I/O Serial Port
+ tty0             P1/S1-L0  Asynchronous Terminal
+ sa1              P1/S2     Standard I/O Serial Port
+ sa2              P1/S3     Standard I/O Serial Port
* ide0             P1/Q1     ATA/IDE Controller Device
+ cd0              P1/Q1-L0  IDE CD-ROM Drive I (650 MB)
+ scsi0            P1/Z1     Wide/Ultra-3 SCSI I/O Controller
+ hdisk0           P1/Z1-A0  16 Bit LVD SCSI Disk Drive (18200 MB)
+ hdisk1           P1/Z1-A1  16 Bit LVD SCSI Disk Drive (18200 MB)
+ safte0           P1/Z1-A9  SCSI Accessed Fault-Tolerant Enclosure Device
+ scsi1            P1/Z2     Wide/Ultra-3 SCSI I/O Controller
+ ent0             P1/E1     IBM 10/100 Mbps Ethernet PCI Adapter (23100020)
+ ent1             P1/E2     IBM 10/100 Mbps Ethernet PCI Adapter (23100020)
+ L2cache0                   L2 Cache
+ mem0                       Memory
+ proc0            P1-C1     Processor

{% endhighlight %}

Fakts, ka tikai nedaudzi [LU][lu] studenti izmanto šo lielisko iespēju, lai izmitinātu savas personīgās, statiskās tīmekļa vietnes ir nedaudz apbēdinošs, laikam jau šis mīļais, labais serverītis tiks reiz norakstīts un izslēgts, bet pagaidām, vēl viss notiek un es iedrošinu jūs visus [LU][lu] studentus pamēģināt un izmitināt savu personīgo tīmekļa vietni, kurā variet apkopot un uzgalbāt vērtīgu informāciju par studiju laikā gūtjām zināšanām. Tīmekļa vietnes publiskā adrese būs `http://home.lu.lv/~stud_apl_nr` manā gadījumā tas ir `http://home.lu.lv/~tv10012`

Lai izmitinātu savu tīmekļa vietni uz servera `apse.lanet.lv` lietotāja mājas direktorijā ir jāzveido jauna direktorija ar nosaukumu `public_html` un šai direktorijā ir jāievieto savas tīmekļa vietnes saturs, lai to izdarītu ir nepieciešams izmantot kādu mūsdienīgu FTP klientu, kas ļauj pieslēgties pie servera pa `SCP` protokolu, es rekomendēju [WinSCP][WinSCP], ko var brīvi lejupielādēt un darbināt uz savas darba stacijas. Tas arī ir viss, ko es vēlējos pateikt tiem [LU][lu] studentiem kuri vai nu ir aizmirsuši vai vēl nezina par šo lielisko iespēju, kā izmitināt personīgās studentu tīmekļa vietnes uz [LU][lu] publiskā servera.

p.s.

Papildus iespēja, ko nodrošina šis serveris ir iespēja izmantot epasta pāradresāciju, jo katram [LU][lu] studentam ir arī piešķirta viņam unikālā epasta adrese `stud_apl_nr@lu.lv`, bet ne visi studenti šo epasta adresi izmanto un bieži vien pat nezin, ka šāda adrese eksistē, savukārt augšupielādējot uz serveri, lietotāja mājas direktorijā failu ar nosaukumu `.forward` un faila saturā ierakstot savu epasta adresi, visi ienākošie epasti tiks automātiski pārsūtīti uz tavu norādīto epastu.

Vēlu veiksmi, lai Tev viss labi izdodās,</br>
Toms

[WinSCP]:    http://winscp.net
[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com
[jl]:        http://jekyllrb.com
[lu]:        http://www.lu.lv/eng
[ieva]:      http://home.lu.lv/
[ieva.sp.lanet.lv]: http://apse.lanet.lv
[luis]:      http://luis.lu.lv
