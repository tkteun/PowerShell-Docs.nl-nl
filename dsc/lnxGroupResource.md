---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxGroup Resource
ms.openlocfilehash: bc01f6ae5ed61aff63958fe55f30d82f9b81b2b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC voor Linux nxGroup Resource

De **nxGroup** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van lokale groepen op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Beschrijving | 
|---|---|
| GroupName| Hiermee geeft u de naam van de groep waarvoor u om te controleren of een specifieke status.| 
| Zorg ervoor dat| Bepaalt of Controleer of de groep bestaat. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat de groep bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat de groep bestaat niet. De standaardwaarde is 'Aanwezig'.| 
| Leden| Hiermee geeft u de leden die vormen van de groep.| 
| MembersToInclude| Hiermee geeft u de gebruikers die u wilt zorgen lid zijn van de groep.| 
| MembersToExclude| Hiermee geeft u de gebruikers die u wilt zorgen zijn geen leden van de groep.| 
| PreferredGroupID| Wordt indien mogelijk de groeps-id ingesteld op de opgegeven waarde. Als de groeps-id momenteel in gebruik is, wordt de volgende beschikbare groeps-id wordt gebruikt.| 
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld zorgt ervoor dat de gebruiker "monuser" bestaat en lid van de groep 'DBusers is'.

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```

