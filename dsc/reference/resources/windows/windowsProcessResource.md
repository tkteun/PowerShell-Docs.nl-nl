---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WindowsProcess-Resource
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076755"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess-Resource

_Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0_

De **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het configureren van processen op een doelknooppunt.

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

| Eigenschap | Description |
| --- | --- |
| Argumenten| Geeft een reeks van argumenten worden doorgegeven aan de proces-is. Als u meerdere argumenten doorgeven wilt, plaatst u ze allemaal op deze tekenreeks.|
| Pad| Het pad naar het uitvoerbare bestand. Als dit de naam van het uitvoerbare bestand (niet de volledig gekwalificeerde pad), de DSC-resource wordt zoeken in de omgeving **pad** variabele (`$env:Path`) naar het uitvoerbare bestand niet vinden. Als de waarde van deze eigenschap een volledig gekwalificeerde pad is, DSC niet gebruiken de **pad** omgevingsvariabele het bestand te vinden en genereert een fout als het pad niet bestaat. Relatieve paden zijn niet toegestaan.|
| Referentie| Geeft aan dat de referenties voor het starten van het proces.|
| Zorg ervoor dat| Geeft aan of het proces bestaat. Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het proces bestaat. Anders wordt deze ingesteld op 'Ontbreekt'. De standaardwaarde is 'Aanwezig'.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"` .|
| StandardErrorPath| Geeft het pad voor het schrijven van de standard-fout. Er een bestaand bestand wordt overschreven.|
| StandardInputPath| Geeft de locatie van de standaard invoer.|
| StandardOutputPath| Geeft de locatie voor het schrijven van de standaarduitvoer. Er een bestaand bestand wordt overschreven.|
| WorkingDirectory| Geeft de locatie die wordt gebruikt als de huidige werkmap voor het proces.|