---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Variabelen gebruiken om objecten op te slaan
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810685"
---
# <a name="using-variables-to-store-objects"></a>Variabelen gebruiken om objecten op te slaan

Power shell werkt met objecten. Met Power shell kunt u benoemde objecten maken die variabelen worden genoemd.
Namen van variabelen kunnen het onderstrepings teken en alfanumerieke tekens bevatten. Bij gebruik in Power shell wordt altijd een variabele opgegeven met behulp \$ van het teken gevolgd door de naam van de variabele.

## <a name="creating-a-variable"></a>Een variabele maken

U kunt een variabele maken door de naam van een geldige variabele te typen:

```
PS> $loc
PS>
```

Dit voor beeld retourneert geen resultaat omdat er geen `$loc` waarde is. U kunt een variabele maken en deze in dezelfde stap aan een waarde toewijzen. Power Shell maakt de variabele alleen als deze niet bestaat.
Anders wordt de opgegeven waarde toegewezen aan de bestaande variabele. In het volgende voor beeld wordt de huidige locatie in de variabele opgeslagen `$loc` :

```powershell
$loc = Get-Location
```

Power shell geeft geen uitvoer weer wanneer u deze opdracht typt. Power shell verzendt de uitvoer van ' Get-location ' naar `$loc` . In Power shell worden gegevens die niet zijn toegewezen of omgeleid naar het scherm verzonden. Als `$loc` u typt, wordt uw huidige locatie weer gegeven:

```
PS> $loc

Path
----
C:\temp
```

U kunt gebruiken `Get-Member` om informatie weer te geven over de inhoud van variabelen. `Get-Member`Hier ziet u dat `$loc` een **PathInfo** -object is, net als bij de uitvoer van `Get-Location` :

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>Variabelen bewerken

Power shell biedt verschillende opdrachten voor het bewerken van variabelen. U kunt een volledige lijst weer geven in een lees bare vorm door het volgende te typen:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

Power Shell maakt ook diverse door het systeem gedefinieerde variabelen. U kunt de `Remove-Variable` cmdlet gebruiken om variabelen te verwijderen die niet worden beheerd door Power shell, vanuit de huidige sessie. Typ de volgende opdracht om alle variabelen te wissen:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Nadat u de vorige opdracht hebt uitgevoerd, worden in de `Get-Variable` cmdlet de systeem variabelen van Power shell weer gegeven.

Power Shell maakt ook een variabele station. Gebruik het volgende voor beeld om alle Power shell-variabelen weer te geven met behulp van het variabele station:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Cmd. exe-variabelen gebruiken

Power shell kan gebruikmaken van dezelfde omgevings variabelen die beschikbaar zijn voor elk Windows-proces, inclusief **cmd. exe**. Deze variabelen worden weer gegeven via een station met de naam `env:` . U kunt deze variabelen weer geven door de volgende opdracht te typen:

```powershell
Get-ChildItem env:
```

De standaard- `*-Variable` cmdlets zijn niet ontworpen om te werken met omgevings variabelen. Omgevings variabelen worden geopend met behulp van het `env:` voor voegsel van de schijf. De variabele **% System root%** in **cmd. exe** bevat bijvoorbeeld de naam van de hoofdmap van het besturings systeem. In Power shell gebruikt u `$env:SystemRoot` om toegang te krijgen tot dezelfde waarde.

```
PS> $env:SystemRoot
C:\WINDOWS
```

U kunt ook omgevings variabelen maken en wijzigen in Power shell. Omgevings variabelen in Power shell volgen dezelfde regels voor omgevings variabelen die elders in het besturings systeem worden gebruikt. In het volgende voor beeld wordt een nieuwe omgevings variabele gemaakt:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Hoewel dit niet vereist is, is het gebruikelijk om alle hoofd letters te gebruiken voor de namen van omgevings variabelen.
