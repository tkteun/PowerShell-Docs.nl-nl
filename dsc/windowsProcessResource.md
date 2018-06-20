---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsProcess Resource
ms.openlocfilehash: 72668136a3a51c17c52f762c6f94bec3ed4597b0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187024"
---
# <a name="dsc-windowsprocess-resource"></a>DSC-WindowsProcess Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het configureren van de processen in een doelknooppunt.

## <a name="syntax"></a>Syntaxis

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a>Eigenschappen
|  Eigenschap  |  Beschrijving   |
|---|---|
| Argumenten| Geeft een reeks van argumenten worden doorgegeven aan het proces als-is. Als u moet enkele argumenten doorgegeven, plaatst u deze allemaal in deze tekenreeks.|
| Pad| Het pad naar het uitvoerbare bestand van het proces. Als dit de bestandsnaam van het uitvoerbare bestand (niet de volledig gekwalificeerde pad), de DSC-resource zoekt de omgeving **pad** variabele (`$env:Path`) naar het uitvoerbare bestand niet vinden. Als de waarde van deze eigenschap een volledig gekwalificeerde pad is, DSC niet wordt gebruikt de **pad** omgevingsvariabele het bestand te vinden en genereert een fout als het pad niet bestaat. Relatieve paden zijn niet toegestaan.|
| referentie| Hiermee geeft u de referenties voor het starten van het proces.|
| Zorg ervoor dat| Hiermee wordt aangegeven of het proces bestaat. Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het proces bestaat. Anders wordt deze ingesteld op 'Afwezig'. De standaardwaarde is 'Aanwezig'.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = '[ ResourceType] ResourceName' ''.|
| StandardErrorPath| Geeft het pad de standaardfout worden geschreven. Er een bestaand bestand worden overschreven.|
| StandardInputPath| Hiermee wordt de locatie van de standaard invoer.|
| StandardOutputPath| Geeft de locatie voor het schrijven van de standaarduitvoer. Er een bestaand bestand worden overschreven.|
| WorkingDirectory| Geeft de locatie die wordt gebruikt als de huidige werkmap voor het proces.|