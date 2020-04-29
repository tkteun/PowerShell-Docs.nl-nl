---
ms.date: 08/23/2018
keywords: Power shell, cmdlet
title: Informatie over Power shell-pijp lijnen
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030391"
---
# <a name="understanding-pipelines"></a>Pijp lijnen

Pijp lijnen fungeren als een reeks verbonden segmenten van pipes. Items die langs de pijp lijn worden verplaatst, passeren elk segment. Als u een pijp lijn in Power shell wilt maken, verbindt u opdrachten samen met de pipe-operator |. De uitvoer van elke opdracht wordt gebruikt als invoer voor de volgende opdracht.

De notatie die wordt gebruikt voor pijp lijnen, is vergelijkbaar met de notatie die wordt gebruikt in andere schalen. In eerste instantie is het mogelijk niet duidelijk hoe pijp lijnen anders zijn in Power shell. Hoewel er tekst op het scherm wordt weer gegeven, Power shell pipes-objecten, geen tekst, tussen opdrachten.

## <a name="the-powershell-pipeline"></a>De Power shell-pijp lijn

Pijp lijnen zijn weliswaar het meest waardevolle concept dat wordt gebruikt in opdracht regel interfaces. Wanneer u correct gebruikt, kunnen pijp lijnen de moeite van het gebruik van complexe opdrachten verminderen en is het eenvoudiger om de werk stroom voor de opdrachten te zien. Elke opdracht in een pijp lijn (een pijplijn element genoemd) geeft de uitvoer door aan de volgende opdracht in de pijp lijn, item-per-item. Opdrachten hoeven niet meer dan één item tegelijk te verwerken. Het resultaat is een gereduceerd Resource verbruik en de mogelijkheid om de uitvoer onmiddellijk te verkrijgen.

Als u bijvoorbeeld de `Out-Host` cmdlet gebruikt om een pagina-op-pagina weer te geven van uitvoer van een andere opdracht, ziet de uitvoer er net zo uit als de normale tekst die op het scherm wordt weer gegeven, onderverdeeld in pagina's:

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

Paginering vermindert ook het `Out-Host` CPU-gebruik omdat er een volledige pagina kan worden weer gegeven. De cmdlets die voorafgaan aan de pijp lijn worden uitgevoerd, totdat de volgende pagina van uitvoer beschikbaar is.

U kunt zien hoe pijpleidingen het CPU-en geheugen gebruik in Windows taak beheer beïnvloedt door de volgende opdrachten te vergelijken:

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> De **paginerings** parameter wordt niet ondersteund door alle Power shell-hosts. Wanneer u bijvoorbeeld probeert de para meter **paging** te gebruiken in Power shell ISE, ziet u de volgende fout:
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>Objecten in de pijp lijn

Wanneer u een cmdlet in Power shell uitvoert, wordt tekst uitvoer weer gegeven, omdat het nodig is om objecten als tekst in een console venster aan te duiden. In de tekst uitvoer worden mogelijk niet alle eigenschappen weer gegeven van het object dat wordt uitgevoerd.

Denk bijvoorbeeld aan de `Get-Location` cmdlet. Als u uitvoert `Get-Location` terwijl uw huidige locatie de hoofdmap van station C is, ziet u de volgende uitvoer:

```
PS> Get-Location

Path
----
C:\
```

De tekst uitvoer is een samen vatting van informatie, niet een volledige weer gave van het object `Get-Location`dat wordt geretourneerd door. De kop in de uitvoer wordt toegevoegd door het proces waarmee de gegevens voor het scherm worden opgemaakt.

Wanneer u de uitvoer naar de `Get-Member` cmdlet Pipet, krijgt u informatie over het object `Get-Location`dat wordt geretourneerd door.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location`retourneert een **PathInfo** -object dat het huidige pad en andere informatie bevat.
