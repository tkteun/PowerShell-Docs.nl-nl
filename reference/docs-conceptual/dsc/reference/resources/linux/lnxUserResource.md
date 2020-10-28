---
ms.date: 07/17/2020
ms.topic: reference
title: DSC voor Linux nxUser-resource
description: DSC voor Linux nxUser-resource
ms.openlocfilehash: 298caa8f5ea6d4587f9782a02d0544147ee33e84
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667382"
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC voor Linux nxUser-resource

De **nxUser** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale gebruikers op een Linux-knoop punt.

## <a name="syntax"></a>Syntax

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Hiermee wordt de account naam aangegeven waarvoor u een specifieke status wilt waarborgen. |
|---|---|
|UserName |Hiermee geeft u de locatie op waar u de status van een bestand of map wilt controleren. |
|FullName |Een teken reeks die de volledige naam bevat die moet worden gebruikt voor het gebruikers account. |
|Beschrijving |De beschrijving voor het gebruikers account. |
|Wachtwoord |De hash van het wacht woord van de gebruiker in het juiste formulier voor de Linux-computer. Normaal gesp roken is dit een gezouten SHA-256-of SHA-512-hash. Op Debian en Ubuntu Linux kan deze waarde worden gegenereerd met de `mkpasswd` opdracht. Voor andere Linux-distributies kan de cryptografie methode van de cryptografie bibliotheek van python worden gebruikt voor het genereren van de hash. |
|Uitgeschakeld |Hiermee wordt aangegeven of het account is ingeschakeld. Stel deze eigenschap in op `$true` om ervoor te zorgen dat dit account is uitgeschakeld en stel dit in op `$false` om ervoor te zorgen dat deze is ingeschakeld. |
|PasswordChangeRequired |Hiermee wordt aangegeven of de gebruiker het wacht woord kan wijzigen. Stel deze eigenschap in op `$true` om ervoor te zorgen dat de gebruiker het wacht woord niet kan wijzigen en stel in om de gebruiker in staat te stellen `$false` het wacht woord te wijzigen. De standaardwaarde is `$false`. Deze eigenschap wordt alleen geëvalueerd als het gebruikers account niet eerder bestaat en wordt gemaakt. |
|HomeDirectory |De basismap voor de gebruiker. |
|Groep |De primaire groeps-ID voor de gebruiker. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee geeft u op of het account bestaat. Stel deze eigenschap in op aanwezig om er zeker van te **zijn** dat het account bestaat en stel het in op **afwezig** om ervoor te zorgen dat het account niet bestaat. |

## <a name="example"></a>Voorbeeld

In het volgende voor beeld wordt ervoor gezorgd dat de gebruiker ' monuser ' bestaat en lid is van de groep ' DBusers '.

```powershell
Import-DSCResource -Module nx

Node $node
{
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
