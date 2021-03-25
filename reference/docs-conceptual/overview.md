---
ms.date: 03/22/2021
keywords: powershell,cmdlet
title: Wat is PowerShell?
description: Dit artikel is een inleiding tot de Power shell-script omgeving en de bijbehorende functies.
ms.openlocfilehash: 3e1c2cae4b8d6507057ee8136265710a8dfe74f3
ms.sourcegitcommit: 719debaed3cc32ba463b1d4cc56a491d8ecbce26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/24/2021
ms.locfileid: "105029686"
---
# <a name="what-is-powershell"></a>Wat is PowerShell?

Power shell is een oplossing voor het automatiseren van meerdere platforms die bestaat uit een opdracht regel shell, een script taal en een configuratie beheer raamwerk. Power shell wordt uitgevoerd op Windows, Linux en macOS.

## <a name="shell"></a>Shell

Power shell is een moderne opdracht shell die de beste functies van andere populaire shells bevat. In tegens telling tot de meeste shells die alleen tekst accepteren en retour neren, accepteert en retourneert Power shell .NET-objecten. De shell bevat de volgende functies:

- Robuuste opdracht regel [geschiedenis][]
- Tabblad voltooiing en de voor spelling van opdrachten (Zie [about_PSReadLine][])
- Ondersteunt opdracht-en parameter [aliassen][]
- [Pijp lijn][] voor het koppelen van opdrachten
- [Help][] -systeem in de console, vergelijkbaar met Unix- `man` pagina's

## <a name="scripting-language"></a>Script taal

Als script taal wordt Power shell doorgaans gebruikt voor het automatiseren van het beheer van systemen. Het wordt ook gebruikt om oplossingen te bouwen, te testen en te implementeren, vaak in CI/CD-omgevingen. Power shell is gebaseerd op de .NET common language runtime (CLR). Alle invoer en uitvoer zijn .NET-objecten. Het is niet nodig om tekst uitvoer te parseren om informatie uit de uitvoer op te halen. De Power shell-script taal bevat de volgende functies:

- Uitbreidbaar tot [functies][], [klassen][], [scripts][]en [modules][]
- Uitbreidbaar [systeem][formatting] voor eenvoudige uitvoer
- Uitbreidbaar [type systeem][types] voor het maken van dynamische typen
- Ingebouwde ondersteuning voor algemene gegevens indelingen, zoals [CSV][], [JSON][]en [XML][]

## <a name="configuration-management"></a>Configuratiebeheer

Power shell desired state Configuration ([DSC][]) is een beheer raamwerk in Power shell waarmee u uw bedrijfs infrastructuur met configuratie als code kunt beheren. Met DSC kunt u het volgende doen:

- Declaratieve [configuraties][] en aangepaste scripts maken voor Herhaal bare implementaties
- Configuratie-instellingen en rapport op configuratie-drift afdwingen
- Configuratie implementeren met [push-of pull][push-pull] -modellen

## <a name="next-steps"></a>Volgende stappen

### <a name="getting-started"></a>Aan de slag

Bent u nieuw in Power shell en weet u niet waar u moet beginnen? Bekijk deze bronnen.

- [PowerShell installeren][install]
- [PowerShell 101][PS101]
- [Zelf studies voor Power shell-bits][tutorials]
- [Power shell-modules voor leren][learn]

### <a name="powershell-in-action"></a>Power shell in actie

Bekijk hoe Power shell wordt gebruikt in verschillende scenario's en op verschillende platforms.

- [Externe communicatie van PowerShell via SSH][remoting]
- [Aan de slag met Azure PowerShell][azure]
- [Een CI/CD-pijp lijn bouwen met DSC][devops]
- [Micro soft Exchange beheren][exchange]

<!-- link references -->

[transactie]: /powershell/module/microsoft.powershell.core/about/about_history
[about_PSReadLine]: /powershell/module/psreadline/about/about_psreadline
[aliassen]: /powershell/module/microsoft.powershell.core/about/about_aliases
[Pijplijn]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[Help]: /powershell/module/microsoft.powershell.core/get-help
[modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[vervullen]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[instructeur]: /powershell/module/microsoft.powershell.core/about/about_classes
[scriptmap]: /powershell/module/microsoft.powershell.core/about/about_scripts
[formatting]: /powershell/module/microsoft.powershell.core/about/about_format.ps1xml
[types]: /powershell/module/microsoft.powershell.core/about/about_types.ps1xml
[CSV]: /powershell/module/microsoft.powershell.utility/convertfrom-csv
[JSON]: /powershell/module/microsoft.powershell.utility/convertfrom-json
[XML]: /powershell/module/microsoft.powershell.utility/convertto-xml
[configuraties]: /powershell/scripting/dsc/configurations/configurations
[DSC]: /powershell/scripting/dsc/overview/dscforengineers
[push-pull]: /powershell/scripting/dsc/pull-server/enactingconfigurations
[install]: /powershell/scripting/install/installing-powershell
[PS101]: /powershell/scripting/learn/ps101/00-introduction
[tutorials]: /powershell/scripting/learn/tutorials/00-introduction
[learn]: /learn/browse/?terms=PowerShell
[azure]: /powershell/azure/get-started-azureps
[devops]: /azure/devops/pipelines/release/dsc-cicd
[exchange]: /powershell/exchange/exchange-management-shell
[remoting]: /powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core
