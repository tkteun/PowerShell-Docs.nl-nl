---
ms.date: 08/27/2018
keywords: Power shell, cmdlet
title: Variabelen gebruiken om objecten op te slaan
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030369"
---
# <a name="using-variables-to-store-objects"></a>Variabelen gebruiken om objecten op te slaan

Power shell werkt met objecten. Met Power shell kunt u benoemde objecten maken die variabelen worden genoemd.
Namen van variabelen kunnen het onderstrepings teken en alfanumerieke tekens bevatten. Bij gebruik in Power shell wordt altijd een variabele opgegeven met behulp van het \$ teken gevolgd door de naam van de variabele.

## <a name="creating-a-variable"></a>Een variabele maken

U kunt een variabele maken door de naam van een geldige variabele te typen:

```
PS> $loc
PS>
```

In dit voor beeld wordt geen resultaat weer gegeven omdat `$loc` geen waarde heeft. U kunt een variabele maken en deze in dezelfde stap aan een waarde toewijzen. Power Shell maakt de variabele alleen als deze niet bestaat.
Anders wordt de opgegeven waarde toegewezen aan de bestaande variabele. In het volgende voor beeld wordt de huidige locatie opgeslagen in de variabele `$loc`:

```powershell
$loc = Get-Location
```

Power shell geeft geen uitvoer weer wanneer u deze opdracht typt. Power shell verzendt de uitvoer van ' Get-location ' naar `$loc`. In Power shell worden gegevens die niet zijn toegewezen of omgeleid naar het scherm verzonden. Wanneer u `$loc` typt, wordt uw huidige locatie weer gegeven:

```
PS> $loc

Path
----
C:\temp
```

U kunt `Get-Member` gebruiken om informatie weer te geven over de inhoud van variabelen. `Get-Member` ziet u dat `$loc` een **PathInfo** -object is, net als bij de uitvoer van `Get-Location`:

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

Power Shell maakt ook diverse door het systeem gedefinieerde variabelen. U kunt de cmdlet `Remove-Variable` gebruiken om variabelen te verwijderen die niet worden beheerd door Power shell, vanuit de huidige sessie. Typ de volgende opdracht om alle variabelen te wissen:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Nadat u de vorige opdracht hebt uitgevoerd, worden in de cmdlet `Get-Variable` de systeem variabelen van Power shell weer gegeven.

Power Shell maakt ook een variabele station. Gebruik het volgende voor beeld om alle Power shell-variabelen weer te geven met behulp van het variabele station:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Cmd. exe-variabelen gebruiken

Power shell kan gebruikmaken van dezelfde omgevings variabelen die beschikbaar zijn voor elk Windows-proces, inclusief **cmd. exe**. Deze variabelen worden weer gegeven via een station met de naam `env:`. U kunt deze variabelen weer geven door de volgende opdracht te typen:

```powershell
Get-ChildItem env:
```

De standaard `*-Variable`-cmdlets zijn niet ontworpen om te werken met omgevings variabelen. U krijgt toegang tot omgevings variabelen met behulp van het voor voegsel `env:` station. De variabele **% System root%** in **cmd. exe** bevat bijvoorbeeld de naam van de hoofdmap van het besturings systeem. In Power shell gebruikt u `$env:SystemRoot` om toegang te krijgen tot dezelfde waarde.

```
PS> $env:SystemRoot
C:\WINDOWS
```

U kunt ook omgevings variabelen maken en wijzigen in Power shell. Omgevings variabelen in Power shell volgen dezelfde regels voor omgevings variabelen die elders in het besturings systeem worden gebruikt. In het volgende voor beeld wordt een nieuwe omgevings variabele gemaakt:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Hoewel dit niet vereist is, is het gebruikelijk om alle hoofd letters te gebruiken voor de namen van omgevings variabelen.
