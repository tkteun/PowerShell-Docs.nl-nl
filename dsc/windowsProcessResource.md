---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsProcess Resource
ms.openlocfilehash: 236a48fd4449a96f2297c152bce65253dd2fd08d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
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