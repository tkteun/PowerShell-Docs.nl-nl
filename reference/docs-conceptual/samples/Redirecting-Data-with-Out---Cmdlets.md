---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Gegevens omleiden met Out-cmdlets
ms.openlocfilehash: d4cc14e26bdef0f973f948177d0c1e68929605fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030076"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Gegevens omleiden met out-*-cmdlets

Windows Power shell biedt verschillende cmdlets waarmee u gegevens uitvoer rechtstreeks kunt beheren. Deze cmdlets delen twee belang rijke kenmerken.

Eerst transformeren ze gegevens naar een vorm van tekst. Ze doen dit omdat ze de gegevens uitvoeren naar systeem onderdelen waarvoor tekst invoer is vereist. Dit betekent dat de objecten als tekst moeten worden aangeduid. Daarom wordt de tekst opgemaakt zoals deze wordt weer gegeven in het Windows Power shell-console venster.

Ten tweede gebruiken deze cmdlets het Windows Power shell-werk woord **uit** , omdat ze informatie vanuit Windows Power shell naar een andere locatie verzenden. De cmdlet **out-host** is geen uitzonde ring: het venster host wordt weer gegeven buiten Windows Power shell. Dit is belang rijk omdat wanneer gegevens vanuit Windows Power shell worden verzonden, ze daad werkelijk worden verwijderd. U kunt dit zien als u probeert een pijp lijn te maken die pagina's met gegevens naar het venster host en vervolgens probeert te Format teren als een lijst, zoals hier wordt weer gegeven:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

U kunt de opdracht voor het weer geven van pagina's met proces gegevens in de lijst indeling verwachten. In plaats daarvan wordt de standaard lijst in tabel vorm weer gegeven:

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

De cmdlet **out-host** verzendt de gegevens rechtstreeks naar de-console, waardoor de opdracht voor het **Format teren** van de lijst nooit wordt ontvangen.

De juiste manier om deze opdracht te structureren, is door de cmdlet **out-host** aan het einde van de pijp lijn te plaatsen, zoals hieronder wordt weer gegeven. Dit zorgt ervoor dat de proces gegevens in een lijst worden opgemaakt voordat ze worden gewisseld en weer gegeven.

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

Dit geldt voor alle **out** -cmdlets. Een **out** -cmdlet moet altijd aan het einde van de pijp lijn worden weer gegeven.

> [!NOTE]
> Alle **out** -cmdlets genereren uitvoer als tekst, met behulp van de opmaak van het console venster, met inbegrip van de limieten voor de regel lengte.

## <a name="paging-console-output-out-host"></a>Uitvoer van de console pagineren (out-host)

Standaard worden gegevens door Windows Power shell naar het venster host verzonden. Dit is precies wat de out-host-cmdlet doet. Het primaire gebruik voor de out-host-cmdlet is het pagineren van gegevens zoals eerder is beschreven. De volgende opdracht gebruikt bijvoorbeeld out-host om de uitvoer van de cmdlet Get-opdracht uit te voeren:

```powershell
Get-Command | Out-Host -Paging
```

U kunt ook de functie **meer** gebruiken voor pagina gegevens. In Windows Power shell is **meer** een functie waarmee u **out-host-paging**aanroept. De volgende opdracht laat zien hoe u met behulp van de functie **meer** op pagina de uitvoer van Get-opdracht kunt gebruiken:

```powershell
Get-Command | more
```

Als u een of meer bestands namen als argumenten voor de functie meer opneemt, worden de opgegeven bestanden en de inhoud van de functie naar de host gelezen:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a>Uitvoer verwijderen (out-null)

De **out-null-** cmdlet is ontworpen voor het direct negeren van de invoer die wordt ontvangen. Dit is handig voor het verwijderen van overbodige gegevens die u krijgt als een neven effect van het uitvoeren van een opdracht. Wanneer u de volgende opdracht typt, haalt u niets terug van de opdracht:

```powershell
Get-Command | Out-Null
```

De uitzonderings **-Null** -cmdlet verwijdert geen fout uitvoer. Als u bijvoorbeeld de volgende opdracht opgeeft, wordt er een bericht weer gegeven waarin wordt gemeld dat Windows Power shell ' is-NotACommand ' niet herkent:

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a>Gegevens afdrukken (niet-printer)

U kunt gegevens afdrukken met behulp van de **out-printer-** cmdlet. De **out-printer** cmdlet gebruikt uw standaard printer als u geen printer naam opgeeft. U kunt elke op Windows gebaseerde printer gebruiken door de bijbehorende weergave naam op te geven. Er is geen soort printer poort toewijzing nodig of zelfs een echte fysieke printer. Als u bijvoorbeeld de Microsoft Office document imaging-hulpprogram ma's hebt geïnstalleerd, kunt u de gegevens naar een afbeeldings bestand verzenden door het volgende te typen:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a>Gegevens opslaan (out-file)

U kunt uitvoer naar een bestand verzenden in plaats van via het console venster met de **out-file-** cmdlet. De volgende opdracht regel verzendt een lijst met processen naar het bestand **C:\\temp\\processlist. txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

De resultaten van het gebruik van de **out-file** cmdlet zijn mogelijk niet wat u verwacht als u gebruikt voor traditionele uitvoer omleiding. Om het gedrag ervan te begrijpen, moet u rekening houden met de context waarin de **out-file-** cmdlet werkt.

Standaard maakt de cmdlet **out-file** een Unicode-bestand. Dit is de beste standaard waarde in de lange uitvoering, maar dit betekent dat de hulpprogram ma's die ASCII-bestanden verwachten, niet goed werken met de standaard uitvoer indeling. U kunt de standaard uitvoer indeling wijzigen in ASCII met behulp van de para meter **Encoding** :

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-bestands** indelingen bestands inhoud die eruitziet als console-uitvoer. Dit zorgt ervoor dat de uitvoer wordt afgekapt net zoals deze in de meeste omstandigheden in een console venster wordt uitgevoerd. Als u bijvoorbeeld de volgende opdracht uitvoert:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

De uitvoer ziet er als volgt uit:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

U kunt de para meter **width** gebruiken om de lijn breedte op te geven om de uitvoer op te halen die niet voldoet aan de scherm breedte. Omdat **width** een 32-bits integer-para meter is, kan de maximum waarde zijn 2147483647. Typ het volgende om de lijn breedte in te stellen op deze maximum waarde:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

De **out-file** cmdlet is het handigst wanneer u de uitvoer wilt opslaan zoals deze zou worden weer gegeven op de-console. Voor een nauw keurige controle over de indeling van de uitvoer hebt u meer geavanceerde hulp middelen nodig. We kijken naar die in het volgende hoofd stuk, samen met enkele details over het bewerken van objecten.
