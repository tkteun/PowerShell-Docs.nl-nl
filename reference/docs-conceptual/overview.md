---
ms.date: 03/22/2021
keywords: powershell,cmdlet
title: Wat is PowerShell?
description: Dit artikel bevat een inleiding tot de PowerShell-scriptomgeving en de functies ervan.
ms.openlocfilehash: ae2a5e311992e98045841a3992810e55390519ad
ms.sourcegitcommit: afbcc8675107ad9ec6afff91ef4a42b2953121cc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2021
ms.locfileid: "108121623"
---
# <a name="what-is-powershell"></a>Wat is PowerShell?

PowerShell is een platformoverschrijdende oplossing voor taakautomatisering die bestaat uit een opdrachtregelshell, een scripttaal en een framework voor configuratiebeheer. PowerShell wordt uitgevoerd op Windows, Linux en macOS.

## <a name="shell"></a>Shell

PowerShell is een moderne opdrachtshell met de beste functies van andere populaire shells. In tegenstelling tot de meeste shells die alleen tekst accepteren en retourneren, accepteert en retourneert PowerShell .NET-objecten. De shell bevat de volgende functies:

- Robuuste [opdrachtregelgeschiedenis][]
- Tab-voltooiing en opdrachtvoorspelling [(zie about_PSReadLine][])
- Ondersteunt opdracht- en [parameteraliassen][]
- [Pijplijn][] voor het aaneenketenen van opdrachten
- Help-systeem [][] in de console, vergelijkbaar met UNIX-pagina's `man`

## <a name="scripting-language"></a>Scripttaal

Als scripttaal wordt PowerShell vaak gebruikt voor het automatiseren van het beheer van systemen. Het wordt ook gebruikt voor het bouwen, testen en implementeren van oplossingen, vaak in CI/CD-omgevingen. PowerShell is gebouwd op de .NET Common Language Runtime (CLR). Alle invoer en uitvoer zijn .NET-objecten. Het is niet nodig om tekstuitvoer te parseren om informatie uit de uitvoer te extraheren. De PowerShell-scripttaal bevat de volgende functies:

- Uit te voeren via [functies,][] [klassen,][] [scripts][]en [modules][]
- Uitvouwbaar [opmaaksysteem voor][formatting] eenvoudige uitvoer
- Extensible [type system voor][types] het maken van dynamische typen
- Ingebouwde ondersteuning voor algemene gegevensindelingen zoals [CSV,][] [JSON][]en [XML][]

## <a name="configuration-management"></a>Configuratiebeheer

PowerShell Desired State Configuration[(DSC)][]is een beheerkader in PowerShell waarmee u uw bedrijfsinfrastructuur kunt beheren met configuratie als code. Met DSC kunt u het volgende doen:

- Declaratieve [configuraties en aangepaste][] scripts maken voor herhaalbare implementaties
- Configuratie-instellingen afdwingen en rapporteren over configuratiedrift
- Configuratie implementeren met [push- of pull-modellen][push-pull]

## <a name="next-steps"></a>Volgende stappen

### <a name="getting-started"></a>Aan de slag

Bent u niet bekend met PowerShell en weet u niet waar u moet beginnen? Bekijk deze resources.

- [PowerShell installeren][install]
- [PowerShell 101][PS101]
- [PowerShell Bits-zelfstudies][tutorials]
- [PowerShell Learn-modules][learn]

### <a name="powershell-in-action"></a>PowerShell in actie

Bekijk hoe PowerShell wordt gebruikt in verschillende scenario's en op verschillende platforms.

- [Externe communicatie van PowerShell via SSH][remoting]
- [Aan de slag met Azure PowerShell][azure]
- [Een CI/CD-pijplijn bouwen met DSC][devops]
- [Microsoft Exchange beheren][exchange]

<!-- link references -->

[Geschiedenis]: /powershell/module/microsoft.powershell.core/about/about_history
[about_PSReadLine]: /powershell/module/psreadline/about/about_psreadline
[Aliassen]: /powershell/module/microsoft.powershell.core/about/about_aliases
[Pijplijn]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[Help]: /powershell/module/microsoft.powershell.core/get-help
[Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[Functies]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[Klassen]: /powershell/module/microsoft.powershell.core/about/about_classes
[Scripts]: /powershell/module/microsoft.powershell.core/about/about_scripts
[formatting]: /powershell/module/microsoft.powershell.core/about/about_format.ps1xml
[types]: /powershell/module/microsoft.powershell.core/about/about_types.ps1xml
[CSV]: /powershell/module/microsoft.powershell.utility/convertfrom-csv
[JSON]: /powershell/module/microsoft.powershell.utility/convertfrom-json
[XML]: /powershell/module/microsoft.powershell.utility/convertto-xml
[Configuraties]: /powershell/scripting/dsc/configurations/configurations
[Dsc]: /powershell/scripting/dsc/overview/dscforengineers
[push-pull]: /powershell/scripting/dsc/pull-server/enactingconfigurations
[install]: /powershell/scripting/install/installing-powershell
[PS101]: /powershell/scripting/learn/ps101/00-introduction
[tutorials]: /powershell/scripting/learn/tutorials/00-introduction
[learn]: /learn/browse/?terms=PowerShell
[azure]: /powershell/azure/get-started-azureps
[devops]: /azure/devops/pipelines/release/dsc-cicd
[exchange]: /powershell/exchange/exchange-management-shell
[remoting]: /powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core
