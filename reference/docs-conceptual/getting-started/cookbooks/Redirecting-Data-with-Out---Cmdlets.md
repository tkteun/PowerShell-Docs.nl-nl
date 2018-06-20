---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Gegevens omleiden met Out-cmdlets
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 3ca7984e831a995e80cbd8a4d83ae9225c2a4f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952117"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Gegevens met Out - omleiden * Cmdlets

Windows PowerShell biedt diverse cmdlets waarmee die u gegevens uitvoer rechtstreeks beheren. Deze cmdlets kunt u twee belangrijke kenmerken delen.

Eerst transformeren ze doorgaans gegevens naar een vorm van tekst. Dit wordt gedaan omdat ze de gegevens naar de onderdelen van het systeem waarvoor tekstinvoer uitvoer. Dit betekent dat ze nodig hebben om weer te geven van de objecten als tekst. De tekst is daarom opgemaakt als u deze in het venster Windows PowerShell-console bekijken.

Deze cmdlets gebruik vervolgens de Windows PowerShell-opdracht **uit** omdat ze gegevens uit vanuit Windows PowerShell op een andere locatie verzonden. De **uitgaande Host** cmdlet vormt daarop geen uitzondering: de weergave in de host bevindt zich buiten het Windows PowerShell. Dit is belangrijk omdat wanneer gegevens worden verzonden buiten Windows PowerShell, wordt dit daadwerkelijk verwijderd. U kunt dit zien als u probeert te maken van een pijplijn die pagina's gegevens naar het hostvenster en vervolgens probeert te formatteren als een lijst als volgt te werk:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

U kunt de opdracht uit om de pagina's van de procesinformatie weergeven in lijstindeling zou verwachten. In plaats daarvan wordt de standaardlijst in tabelvorm weergegeven:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

De **uitgaande Host** cmdlet verzendt de gegevens rechtstreeks naar de console, zodat de **lijst indelen** opdracht ontvangt nooit iets te formatteren.

De juiste manier structuur van deze opdracht is te plaatsen de **uitgaande Host** cmdlet aan het einde van de pijplijn zoals hieronder wordt weergegeven. Dit zorgt ervoor dat de gegevens over het installatieproces worden ingedeeld in een lijst voordat wordt wisselbaar en weergegeven.

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

Dit geldt voor alle van de **uit** cmdlets. Een **uit** cmdlet moet altijd worden weergegeven aan het einde van de pijplijn.

> [!NOTE]
> Alle de **uit** cmdlets uitvoer weergegeven als tekst met de opmaak van kracht voor het consolevenster, met inbegrip van lengtebeperkingen regel.

#### <a name="paging-console-output-out-host"></a>Console-uitvoer van het wisselbestand (uitgaande Host)

Standaard Windows PowerShell gegevens verzendt naar het hostvenster precies wat is de uitgaande hosten cmdlet heeft. Het primaire gebruik voor de uitgaande hosten cmdlet is paginering gegevens, zoals eerder is besproken. Bijvoorbeeld de volgende opdracht gebruikt uitgaande als host optreden voor de uitvoer van de cmdlet Get-Command pagina:

```powershell
Get-Command | Out-Host -Paging
```

U kunt ook de **meer** functioneren op de paginagegevens. In Windows PowerShell **meer** is een functie die aanroept **uitgaande Host-Paging**. De volgende opdracht wordt gedemonstreerd met behulp van de **meer** functioneren op de pagina van de uitvoer van Get-opdracht:

```powershell
Get-Command | more
```

Als u een of meer bestandsnamen als argumenten voor de functie meer opneemt, wordt de functie de opgegeven bestanden lezen en wordt de inhoud naar de host pagina:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a>Een van de uitvoer (uitgaande Null)

De **uitgaande Null** cmdlet is ontworpen om onmiddellijk negeren invoer ontvangen. Dit is handig voor het negeren van onnodige gegevens die u als gevolg krijgt van een opdracht uit te voeren. Wanneer Typ de volgende opdracht, er iets terug van de opdracht:

```powreshell
Get-Command | Out-Null
```

De **uitgaande Null** cmdlet heeft geen foutuitvoer negeren. Bijvoorbeeld, als u de volgende opdracht invoert, een bericht weergegeven waarin wordt gemeld dat Windows PowerShell 'Is NotACommand' wordt niet herkend:

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a>Gegevens voor afdrukken (Out-Printer)

U kunt gegevens afdrukken met behulp van de **Out-Printer** cmdlet. De **Out-Printer** cmdlet standaardprinter wordt gebruikt als u de naam van een printer niet opgeeft. U kunt een printer op basis van Windows gebruiken door op te geven van de weergavenaam. Er is niet nodig voor elk soort printer poorttoewijzing of zelfs een echte fysieke printer. Bijvoorbeeld, als u de Microsoft Office-document replicatiehulpprogramma's geïnstalleerd hebt, kunt u de gegevens verzenden naar een afbeeldingbestand door te typen:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a>Opslaan van gegevens (out-File)

U kunt uitvoer naar een bestand in plaats van het consolevenster verzenden met behulp van de **out-File** cmdlet. De volgende opdrachtregel zendt een lijst van processen naar het bestand **C:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

De resultaten van het gebruik van de **out-File** cmdlet is wat u verwacht als u worden gebruikt voor traditionele uitvoeromleiding niet mogelijk. Om het gedrag te begrijpen, moet u rekening houden met de context waarin de **out-File** cmdlet werkt.

Standaard de **out-File** cmdlet maakt een Unicode-bestand. Dit is de aanbevolen standaardwaarde op de lange termijn, maar het betekent dat hulpprogramma's die ASCII-bestanden verwacht niet correct met de indeling van de standaard-uitvoer werken wordt. U kunt de standaardindeling van uitvoer in ASCII wijzigen met behulp van de **codering** parameter:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-File** indelingen bestand inhoud eruitzien zoals bij console-uitvoer. Dit zorgt ervoor dat de uitvoer moet net als in een consolevenster in de meeste gevallen worden afgekapt. Bijvoorbeeld, als u de volgende opdracht uitvoeren:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

De uitvoer ziet er als volgt:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Als u uitvoer die u hoeft niet regel terugloopt overeenkomen met de schermbreedte, kunt u de **breedte** lijnbreedte van de parameter. Omdat **breedte** een 32-bits geheel getal-parameter is de maximale waarde kan hebben is 2147483647. Typ het volgende om in te stellen van de breedte van de aan deze maximumwaarde:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

De **out-File** cmdlet is handig wanneer u opslaan uitvoer wilt zoals deze zou hebben weergegeven op de console. Voor een betere controle over de indeling van uitvoer moet u meer geavanceerde hulpprogramma's. Laten we zien die in het volgende hoofdstuk, samen met een aantal details van het object bewerken.