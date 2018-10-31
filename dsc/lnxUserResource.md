---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxUser-Resource
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226029"
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC voor Linux nxUser-Resource

De **nxUser** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale gebruikers op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Geeft de accountnaam waarvan u wilt om te controleren of een specifieke status. |
|---|---|
| UserName| Hiermee geeft u de locatie waar u om te controleren of de status van een bestand of map.|
| Zorg ervoor dat| Hiermee geeft u op of het account bestaat. Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het account bestaat en stel deze in op 'Ontbreekt' om ervoor te zorgen dat het account niet bestaat.|
| Volledige naam| Een tekenreeks zijn met de volledige naam moet worden gebruikt voor het gebruikersaccount.|
| Beschrijving| De beschrijving voor het gebruikersaccount.|
| Wachtwoord| De hash van het wachtwoord van de gebruiker in de juiste vorm voor de Linux-computer. Dit is meestal een gezouten SHA-256, of een hash van SHA-512. Op Debian en Ubuntu Linux, kan deze waarde worden gegenereerd met de opdracht mkpasswd. Voor andere Linux-distributies, kan de crypt-methode van de Python-Crypt-bibliotheek worden gebruikt voor het genereren van de hash.|
| Disabled| Geeft aan of het account is ingeschakeld. Deze eigenschap instellen op **$true** om ervoor te zorgen dat dit account is uitgeschakeld, en stel deze in op **$false** om ervoor te zorgen dat deze is ingeschakeld.|
| PasswordChangeRequired| Geeft aan of de gebruiker het wachtwoord kunt wijzigen. Deze eigenschap instellen op **$true** om ervoor te zorgen dat de gebruiker kan niet het wachtwoord wijzigen en stel deze in op **$false** zodat de gebruiker het wachtwoord te wijzigen. De standaardwaarde is **$false**. Deze eigenschap wordt alleen beoordeeld als het gebruikersaccount niet aanwezig waren en wordt gemaakt.|
| Basismap| De basismap voor de gebruiker.|
| Groeps-id| De primaire groeps-ID voor de gebruiker.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van het scriptblok voor resource-configuratie die u wilt uitvoeren 'ResourceName' voor het eerst is en het type is 'ResourceType', de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

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