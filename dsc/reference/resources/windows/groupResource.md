---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Groep van de DSC-Resource
ms.openlocfilehash: 123e09b54a923af942a15f80fa7291c555b4235f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077344"
---
# <a name="dsc-group-resource"></a>Groep van de DSC-Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De bron van gebruikersgroep in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doelknooppunt.

## <a name="syntax"></a>Syntaxis

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Description   |
|---|---|
| GroupName| De naam van de groep waarvan u wilt om te controleren of een specifieke status.|
| Referentie| De referenties die zijn vereist voor toegang tot externe bronnen. **Houd er rekening mee**: Dit account moet hebben tot de juiste Active Directory-machtigingen voor alle niet-lokale accounts toevoegen aan de groep. anders treedt een fout op wanneer de configuratie wordt uitgevoerd op het doelknooppunt.
| Description| De beschrijving van de groep.|
| Zorg ervoor dat| Geeft aan of de groep bestaat. Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat de groep niet bestaat. Instellen om "" (de standaardwaarde), zorgt u ervoor dat de groep bestaat.|
| Leden| Gebruik deze eigenschap om het lidmaatschap van de huidige vervangen door de opgegeven leden. De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*. Als u deze eigenschap in een configuratie hebt ingesteld, mag niet een gebruiken de **MembersToExclude** of **MembersToInclude** eigenschap. In dat geval wordt een fout gegenereerd.|
| MembersToExclude| Gebruik deze eigenschap leden verwijderen uit het bestaande lidmaatschap van de groep. De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*. Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap. In dat geval wordt een fout gegenereerd.|
| MembersToInclude| Gebruik deze eigenschap leden toevoegen aan het bestaande lidmaatschap van de groep. De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*. Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap. In dat geval wordt er een fout gegenereerd.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.|

## <a name="example-1"></a>Voorbeeld 1

Het volgende voorbeeld ziet hoe u om ervoor te zorgen dat een groep met de naam "Testgroep" afwezig is.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a>Voorbeeld 2

Het volgende voorbeeld laat zien hoe een Active Directory-gebruiker toevoegen aan de lokale groep administrators als onderdeel van een Machine met meerdere Lab-build waar u al een PSCredential worden gebruikt voor het lokale Administrator-account.
Als dit wordt ook gebruikt voor het beheeraccount van het domein (na de promotie van domein), moeten we vervolgens deze bestaande PSCredential omzetten in een domein beschrijvende referentie.
We kunnen vervolgens de gebruiker van een domein toevoegen aan de lokale groep Administrators op de lidserver.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>Voorbeeld 3

Het volgende voorbeeld laat zien hoe om te controleren of een lokale groep, TigerTeamAdmins, op de server TigerTeamSource.Contoso.Com bevat niet de account van een bepaald domein, Contoso\JerryG.

```powershell
Configuration SecureTigerTeamSource {
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

  Node TigerTeamSource.Contoso.Com {
    Group TigerTeamAdmins {
       GroupName        = 'TigerTeamAdmins'
       Ensure           = 'Present'
       MembersToExclude = "Contoso\JerryG"
    }
  }
}
```