---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Inzicht in de Windows PowerShell-Pipeline
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 6d152e52d2fcfb9dd592eb9ac40500615f2186cb
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="understanding-the-windows-powershell-pipeline"></a>Inzicht in de Windows PowerShell-Pipeline
Piping werkt vrijwel overal in Windows PowerShell. Hoewel u tekst op het scherm ziet, wordt in Windows PowerShell tekst tussen opdrachten niet pipe. In plaats daarvan doorgesluisd deze objecten.

De notatie die wordt gebruikt voor pijplijnen is vergelijkbaar met die in andere houders gebruikt, dus op het eerste gezicht het niet altijd duidelijk is Windows PowerShell introduceert een nieuwe. Als u bijvoorbeeld de **uitgaande Host** cmdlet om af te dwingen van een weergave per pagina van de uitvoer van een andere opdracht, de uitvoer ziet er net zoals de normale tekst die wordt weergegeven op het scherm, opgedeeld in pagina's:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

De Out-Host-paginering opdracht is een nuttig pipeline-element wanneer u langdurige uitvoer die u wilt weergeven aan de trage kant. Dit is vooral nuttig als de bewerking het CPU-intensief is. Omdat de verwerking wordt overgebracht naar de cmdlet uitgaande Host wanneer er een volledige pagina Gereed om weer te geven, cmdlets die worden voorafgegaan door het in de pijplijn bewerking onderbroken totdat de volgende pagina van de uitvoer beschikbaar is. U kunt dit zien als u Windows Taakbeheer om te controleren van de CPU en geheugen gebruikt door Windows PowerShell.

Voer de volgende opdracht: **Get-ChildItem C:\\Windows-Recurse**. Vergelijk de CPU- en geheugengebruik op deze opdracht: **Get-ChildItem C:\\Windows-Recurse | Uitgaande Host-Paging**. Wat u ziet in het scherm is tekst, maar dat is omdat het is nodig om objecten te vertegenwoordigen als tekst in een consolevenster. Dit is alleen een weergave van wat er echt dat op in Windows PowerShell. Bijvoorbeeld, u kunt de cmdlet Get-locatie. Als u typt **Get-Location** terwijl uw huidige locatie de hoofdmap van station C is, ziet u de volgende uitvoer:

```
PS> Get-Location

Path
----
C:\
```

Als u Windows PowerShell gebruikt in een pijplijn tekst, waarop u een opdracht zoals **Get-Location | Uitgaande Host**, zou doorgeven van **Get-Location** naar **uitgaande Host** een reeks tekens in de volgorde waarin ze worden weergegeven op het scherm. Met andere woorden, als u de informatie van de kop negeren **uitgaande Host** zou ontvangen van het teken '**C'**, klikt u vervolgens het teken '**:'**, klikt u vervolgens het teken ' **\\'**. De **uitgaande Host** cmdlet kan niet worden bepaald welke betekenis koppelen aan de uitvoer van de tekens door de **Get-Location** cmdlet.

In plaats van via SMS-opdrachten in een pijplijn te laten communiceren, objecten maakt gebruik van Windows PowerShell. Vanuit het oogpunt van een gebruiker, objecten verwante informatie in een formulier dat het makkelijker wordt om te bewerken van de gegevens als eenheid van het pakket en extraheren van specifieke items die u nodig hebt.

De **Get-Location** opdracht geen waarde retourneert tekst met het huidige pad. Deze retourneert een reeks informatie aangeroepen een **PathInfo** -object dat het huidige pad samen met andere informatie bevat. De **uitgaande Host** cmdlet vervolgens verzendt **PathInfo** object naar het scherm en Windows PowerShell beslist wat gegevens om weer te geven en hoe weer te geven op basis van de regels voor opmaak.

In feite de informatie van de kop uitvoeren door de **Get-Location** cmdlet alleen aan het einde van het proces wordt toegevoegd als onderdeel van het proces van de opmaak van de gegevens worden weergegeven op het scherm. Wat u ziet op het scherm wordt een samenvatting van gegevens en niet een volledige weergave van het object uitvoer.

Gezien het feit dat er mogelijk meer informatie de uitvoer van een Windows PowerShell opdracht dan zien we in het consolevenster weergegeven hoe kunt u de niet-zichtbare elementen ophalen? Hoe bekijkt u de extra gegevens? En wat gebeurt er als u wilt weergeven van de gegevens in een indeling die anders dan een Windows PowerShell normaal gesproken gebruikt?

De rest van dit hoofdstuk wordt beschreven hoe u kunt detecteren de structuur van de specifieke Windows PowerShell-objecten selecteren van specifieke items en opmaak ze gemakkelijker weergegeven en hoe deze gegevens worden verzonden naar alternatieve uitvoerlocaties, zoals bestanden en printers.

