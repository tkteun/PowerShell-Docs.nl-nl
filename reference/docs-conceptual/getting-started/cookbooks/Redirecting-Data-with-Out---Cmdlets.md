---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Gegevens omleiden met Out-cmdlets
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: f08879f436ce751b176af020aba21e90f09aa61f
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321006"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Gegevens omleiden met Out-* Cmdlets

Windows PowerShell biedt verschillende cmdlets waarmee die u gegevens rechtstreeks uitvoer beheren. Deze cmdlets delen twee belangrijke kenmerken.

Eerst, ze algemeen gegevens transformeren naar een vorm van tekst. Ze doen dit omdat ze de gegevens naar de onderdelen van het systeem waarvoor tekstinvoer uitvoer. Dit betekent dat ze nodig hebben om weer te geven van de objecten als tekst. De tekst is daarom opgemaakt als u deze in de Windows PowerShell-consolevenster bekijken.

Deze cmdlets gebruik vervolgens de Windows PowerShell-opdracht **uit** omdat ze gegevens vanuit Windows PowerShell op een andere locatie verzenden. De **uitgaande hosten** cmdlet vormt daar geen uitzondering: de weergave in de host is buiten Windows PowerShell. Dit is belangrijk omdat wanneer gegevens uit de Windows PowerShell wordt verzonden, wordt deze daadwerkelijk verwijderd. U kunt dit zien als u probeert te maken van een pijplijn die gegevens van de pagina's naar het hostvenster van de, en vervolgens probeert om deze als een lijst, zoals hier wordt weergegeven:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

U kunt de opdracht voor het weergeven van pagina's van de procesinformatie in lijstindeling had verwacht. In plaats daarvan wordt de lijst in tabelvorm met weergegeven:

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

De **uitgaande hosten** cmdlet verzendt die gegevens rechtstreeks naar de console, zodat de **lijst indeling** opdracht ontvangt nooit iets te formatteren.

De juiste manier te structureren met deze opdracht is te plaatsen de **uitgaande hosten** cmdlet aan het einde van de pijplijn, zoals hieronder weergegeven. Dit zorgt ervoor dat de gegevens verwerken is opgemaakt in een lijst voordat deze wordt gewisseld en weergegeven.

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
> Alle de **uit** cmdlets uitvoer weergegeven als tekst, met behulp van de opmaak van kracht voor het consolevenster, met inbegrip van regel lengtebeperkingen.

#### <a name="paging-console-output-out-host"></a>Console-uitvoer voor het wisselbestand (uitgaande Host)

Standaard Windows PowerShell verzendt gegevens naar het hostvenster, dat precies wat is de uitgaande hosten cmdlet is. Het primaire gebruik voor het hosten van uitgaande cmdlet zijn gepagineerde gegevens zoals we eerder is besproken. De volgende opdracht gebruikt Host bijvoorbeeld uitgaande pagina van de uitvoer van de cmdlet Get-opdracht:

```powershell
Get-Command | Out-Host -Paging
```

U kunt ook de **meer** functie waarmee u kunt paginagegevens. In Windows PowerShell, **meer** is een functie die worden aangeroepen **uitgaande Host-Wisselgeheugengebruik**. De volgende opdracht ziet u hoe de **meer** functie op de pagina van de uitvoer van Get-opdracht:

```powershell
Get-Command | more
```

Als u een of meer namen van bestanden als argumenten voor de functie meer opgeeft, wordt de functie de opgegeven bestanden lezen en pagina van de inhoud ervan op de host:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a>Uitvoer verwijderen (uitgaande Null)

De **uitgaande Null** cmdlet is ontworpen om onmiddellijk negeren invoer wordt ontvangen. Dit is handig voor het verwijderen van onnodige gegevens die u als een neveneffect krijgt van het uitvoeren van een opdracht. Wanneer Typ de volgende opdracht uit, er iets terug vanaf de opdrachtregel:

```powershell
Get-Command | Out-Null
```

De **uitgaande Null** cmdlet foutuitvoer komt niet te verwijderen. Bijvoorbeeld, als u de volgende opdracht invoert, een bericht weergegeven waarin wordt gemeld dat Windows PowerShell-Is-NotACommand' wordt niet herkend:

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a>Gegevens voor afdrukken (Out-Printer)

U kunt gegevens afdrukken met behulp van de **Out-Printer** cmdlet. De **Out-Printer** cmdlet wordt de standaardprinter gebruiken als u de naam van een printer niet opgeeft. U kunt een printer op basis van Windows gebruiken door de weergavenaam op te geven. Er is niet nodig voor elk soort printer poorttoewijzing of zelfs een echt fysiek printer. Bijvoorbeeld, als u de Microsoft Office-document replicatiehulpprogramma's geïnstalleerd hebt, kunt u de gegevens verzenden naar een afbeeldingbestand door te typen:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a>Opslaan van gegevens (out-File)

U kunt uitvoer ook verzenden naar een bestand in plaats van het consolevenster met behulp van de **out-File** cmdlet. De volgende opdrachtregel stuurt een lijst van processen naar het bestand **C:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

De resultaten van het gebruik van de **out-File** cmdlet mogelijk niet wat u verwacht als u worden gebruikt voor omleiding van traditionele uitvoer. Voor meer informatie over het gedrag, moet u op de hoogte van de context waarin de **out-File** cmdlet werkt.

Standaard de **out-File** met de cmdlet maakt een Unicode-bestand. Dit is de aanbevolen standaardwaarde op de lange termijn, maar dit betekent dat hulpprogramma's die u kunt ASCII-bestanden verwachten niet goed met de indeling van de standaard-uitvoer werken wordt. U kunt de standaarduitvoerindeling op ASCII wijzigen met behulp van de **Encoding** parameter:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-File** indelingen bestandsinhoud zodat het eruitziet als console-uitvoer. Dit zorgt ervoor dat de uitvoer moet worden afgekapt, net zoals het in een consolevenster weergegeven in de meeste gevallen. Bijvoorbeeld, als u de volgende opdracht uitvoeren:

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

Als u uitvoer die niet regel terugloopt hoeft zodat deze overeenkomen met de schermbreedte, kunt u de **breedte** parameter opgeven voor lijnbreedte. Omdat **breedte** is een 32-bits geheel getal-parameter, de maximale waarde kan hebben is 2147483647. Typ het volgende om in te stellen van de breedte van de aan deze maximumwaarde:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

De **out-File** cmdlet is vooral nuttig zijn wanneer u opslaan uitvoer wilt zoals deze zou hebben weergegeven in de console. Voor betere controle over de indeling van uitvoer moet u meer geavanceerde hulpprogramma's. We kijken die in het volgende hoofdstuk, samen met details over het bewerken van het object.