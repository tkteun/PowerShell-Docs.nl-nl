---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxGroup-Resource
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048326"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC voor Linux nxGroup-Resource

De **nxGroup** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Beschrijving |
|---|---|
| Groepsnaam| Hiermee geeft u de naam van de groep waarvan u wilt om te controleren of een specifieke status.|
| Zorg ervoor dat| Hiermee bepaalt u of om te controleren of de groep bestaat. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de groep bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat de groep bestaat niet. De standaardwaarde is 'Aanwezig'.|
| Leden| Hiermee geeft u de leden die de groep.|
| MembersToInclude| Hiermee geeft u de gebruikers die u wilt ervoor zorgen zijn leden van de groep.|
| MembersToExclude| Hiermee geeft u de gebruikers die u wilt ervoor zorgen geen lid van de groep zijn.|
| PreferredGroupID| Wordt indien mogelijk de groeps-id ingesteld op de opgegeven waarde. Als de groeps-id momenteel gebruikt wordt, worden de volgende beschikbare groeps-id wordt gebruikt.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld zorgt ervoor dat de gebruiker monuser bestaat en lid van de groep 'DBusers is'.

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```