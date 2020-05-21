---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxGroup-resource
ms.openlocfilehash: 3682cb728d314d00b4a64a93b93018e8a6d12a21
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560845"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC voor Linux nxGroup-resource

De **nxGroup** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op een Linux-knoop punt.

## <a name="syntax"></a>Syntaxis

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|GroupName |Hiermee geeft u de naam van de groep waarvoor u een specifieke status wilt waarborgen. |
|Leden |Hiermee geeft u de leden op die de groep vormen. |
|MembersToInclude |Hiermee geeft u de gebruikers die u wilt controleren, lid zijn van de groep. |
|MembersToExclude |Hiermee geeft u de gebruikers die u wilt controleren, geen lid zijn van de groep. |
|PreferredGroupID |Hiermee stelt u de groeps-id in op de gegeven waarde, indien mogelijk. Als de groeps-id momenteel in gebruik is, wordt de volgende beschik bare groeps-id gebruikt. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt bepaald of er wordt gecontroleerd of de groep bestaat. Stel deze eigenschap in op **presen teren** om te controleren of de groep bestaat. Stel deze in op **afwezig** om te controleren of de groep niet bestaat. De standaard waarde is **aanwezig**. |

## <a name="example"></a>Voorbeeld

In het volgende voor beeld wordt ervoor gezorgd dat de gebruiker ' monuser ' bestaat en lid is van de groep ' DBusers '.

```powershell
Import-DSCResource -Module nx

Node $node
{
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
