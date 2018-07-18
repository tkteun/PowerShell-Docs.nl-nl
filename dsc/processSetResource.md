---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC ProcessSet-Resource
ms.openlocfilehash: d18d2c96239abd83cea735e0fbce198d0456cea6
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093987"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess-Resource

> Van toepassing op: Windows PowerShell 5.0

De **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het configureren van processen op een doelknooppunt. Deze resource is een [samengestelde resource](authoringResourceComposite.md) die roept de [WindowsProcess-resource](windowsProcessResource.md) voor elke groep die is opgegeven in de `GroupName` parameter.

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
| Argumenten| Een tekenreeks met argumenten worden doorgegeven aan de proces-is. Als u meerdere argumenten doorgeven wilt, plaatst u ze allemaal op deze tekenreeks.|
| Pad| De paden naar het proces uitvoerbare bestanden. Als dit zijn de namen van de uitvoerbare bestanden (geen volledig gekwalificeerde paden), de DSC-resource wordt zoeken in de omgeving **pad** variabele (`$env:Path`) om de bestanden te zoeken. Als de waarden van deze eigenschap volledig gekwalificeerde paden zijn, DSC niet gebruiken de **pad** omgevingsvariabele om de bestanden te zoeken en genereert een fout als een van de paden niet bestaan. Relatieve paden zijn niet toegestaan.|
| Referentie| Geeft aan dat de referenties voor het starten van het proces.|
| Zorg ervoor dat| Hiermee geeft u op of de processen bestaat. Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het proces bestaat. Anders wordt deze ingesteld op 'Ontbreekt'. De standaardwaarde is 'Aanwezig'.|
| StandardErrorPath| Het pad waarnaar de processen standaardfout schrijven. Er een bestaand bestand wordt overschreven.|
| StandardInputPath| De stroom van waaruit het proces standaard invoer ontvangt.|
| StandardOutputPath| Het pad van het bestand waarnaar de processen standaarduitvoer schrijven. Er een bestaand bestand wordt overschreven.|
| WorkingDirectory| De locatie die wordt gebruikt als de huidige werkmap voor de processen.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **_ResourceType**, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.|