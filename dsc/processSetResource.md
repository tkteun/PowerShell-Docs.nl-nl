---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-ProcessSet Resource
ms.openlocfilehash: d3c7383da5fd10580612527465ab621004ee7269
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsprocess-resource"></a>DSC-WindowsProcess Resource

> Van toepassing op: Windows PowerShell 5.0

De **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het configureren van de processen in een doelknooppunt. Deze bron is een [samengestelde bron](authoringResourceComposite.md) die roept de [WindowsProcess resource](windowsProcessResource.md) voor elke groep die is opgegeven in de `GroupName` parameter.

## <a name="syntax"></a>Syntaxis

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Eigenschappen
|  Eigenschap  |  Beschrijving   |
|---|---|
| Argumenten| Een tekenreeks met argumenten worden doorgegeven aan het proces als-is. Als u moet enkele argumenten doorgegeven, plaatst u deze allemaal in deze tekenreeks.|
| Pad| De paden naar het proces uitvoerbare bestanden. Als dit zijn de namen van de uitvoerbare bestanden (niet de volledig gekwalificeerde paden), zoekt de DSC-resource de omgeving **pad** variabele (`$env:Path`) om de bestanden te zoeken. Als de waarden van deze eigenschap volledig gekwalificeerde paden zijn, DSC niet wordt gebruikt de **pad** omgevingsvariabele om de bestanden te zoeken en genereert een fout als de paden niet bestaan. Relatieve paden zijn niet toegestaan.|
| referentie| Hiermee geeft u de referenties voor het starten van het proces.|
| Zorg ervoor dat| Geeft aan of de processen bestaat. Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het proces bestaat. Anders wordt deze ingesteld op 'Afwezig'. De standaardwaarde is 'Aanwezig'.|
| StandardErrorPath| Het pad waaraan de processen standaardfout schrijven. Er een bestaand bestand worden overschreven.|
| StandardInputPath| De stroom van waaruit het proces standaardinvoer ontvangt.|
| StandardOutputPath| Het pad van het bestand waarvoor de processen standaarduitvoer schrijven. Er een bestaand bestand worden overschreven.|
| WorkingDirectory| De locatie die wordt gebruikt als de huidige werkmap voor de processen.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **_ResourceType**, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = '[ ResourceType] ResourceName' ''.|