---
ms.date: 08/23/2018
keywords: PowerShell-cmdlet
title: Understanding PowerShell-pijplijnen
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030391"
---
# <a name="understanding-pipelines"></a>Inzicht in pijplijnen

Pijplijnen fungeert als een reeks verbonden segmenten van de pipe. Items verplaatsen langs de pijplijn doorgegeven via elk segment. Voor het maken van een pijplijn in PowerShell, u opdrachten, samen met de operator pipe verbinding maken ' | '. De uitvoer van elke opdracht wordt gebruikt als invoer voor de volgende opdracht.

De notatie die wordt gebruikt voor pijplijnen is vergelijkbaar met de notatie die wordt gebruikt in andere shells. Op het eerste gezicht deze mogelijk niet duidelijk hoe pijplijnen verschillen in PowerShell. Hoewel u tekst op het scherm ziet, geeft de PowerShell-objecten, geen tekst tussen opdrachten.

## <a name="the-powershell-pipeline"></a>De PowerShell-pijplijn

Pijplijnen zijn weliswaar de meest waardevolle concept gebruikt in opdrachtregelinterfaces. Wanneer u goed gebruikt, wordt pijplijnen minder moeite van het gebruik van complexe opdrachten en maken het gemakkelijker om te zien van de werkstroom voor de opdrachten. Elke opdracht in een pijplijn (ook wel een pipeline-element genoemd) wordt de uitvoer doorgegeven aan de volgende opdracht in de pijplijn per item. Opdrachten hebben voor het afhandelen van meer dan één item per keer niet. Het resultaat is verlaagd resourceverbruik en de mogelijkheid om te beginnen met de uitvoer onmiddellijk aan.

Als u bijvoorbeeld de `Out-Host` cmdlet om af te dwingen van per pagina weergegeven in een uitvoer van een andere opdracht, de uitvoer er ongeveer zo uitziet net zoals de normale tekst die wordt weergegeven op het scherm, opgedeeld in pagina's:

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

Ook het wisselbestand minder CPU-gebruik omdat verwerking naar overgebracht de `Out-Host` cmdlet wanneer er een volledige pagina Gereed om weer te geven. De cmdlets die worden voorafgegaan door het in de pijplijn onderbreken worden uitgevoerd totdat de volgende pagina van de uitvoer beschikbaar is.

U kunt zien hoe doorsluizen heeft gevolgen voor CPU- en geheugengebruik in Windows Taakbeheer door het vergelijken van de volgende opdrachten:

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> De **Paging** parameter wordt niet ondersteund door alle PowerShell-hosts. Bijvoorbeeld, wanneer u probeert te gebruiken de **Paging** parameter in de PowerShell ISE, ziet u de volgende fout:
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>Objecten in de pijplijn

Wanneer u een cmdlet in PowerShell uitvoert, ziet u tekstuitvoer omdat het is nodig om objecten te vertegenwoordigen als tekst in een consolevenster weergegeven. De tekstuitvoer kan niet alle van de eigenschappen van het object uitvoer wordt weergegeven.

Neem bijvoorbeeld de `Get-Location` cmdlet. Als u `Get-Location` terwijl uw huidige locatie, de hoofdmap van station C is, ziet u de volgende uitvoer:

```
PS> Get-Location

Path
----
C:\
```

De tekstuitvoer is een samenvatting van gegevens, niet een volledige weergave van het object dat wordt geretourneerd door `Get-Location`. De kop in de uitvoer is toegevoegd door het proces dat de gegevens voor weergave op het scherm wordt opgemaakt.

Wanneer u de uitvoer doorsluizen naar de `Get-Member` cmdlet krijgt u informatie over het object dat wordt geretourneerd door `Get-Location`.

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

`Get-Location` retourneert een **PathInfo** -object dat het huidige pad en andere informatie bevat.
