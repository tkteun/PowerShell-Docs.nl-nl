---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
description: Biedt een mechanisme voor het beheren van lokale groepen op het doelknooppunt.
title: DSC GroupSet-Resource
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077174"
---
# <a name="dsc-groupset-resource"></a>DSC GroupSet-Resource

> Van toepassing op: Windows PowerShell 5.0

De **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doelknooppunt. Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die roept de [groep resource](groupResource.md) voor elke groep die is opgegeven in de `GroupName` parameter.

Gebruik deze resource als u wilt toevoegen en/of verwijderen van de dezelfde lijst met leden aan meer dan één groep, meer dan één groep te verwijderen of toevoegen van meer dan één groep met dezelfde lijst met leden.

## <a name="syntax"></a>Syntaxis

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Description   |
|---|---|
| GroupName| De namen van de groepen waarvoor u wilt om te controleren of een specifieke status.|
| MembersToExclude| Gebruik deze eigenschap leden verwijderen uit het bestaande lidmaatschap van de groepen. De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*. Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap. In dat geval wordt er een fout gegenereerd.|
| Referentie| De referenties die zijn vereist voor toegang tot externe bronnen. **Houd er rekening mee**: Dit account moet hebben tot de juiste Active Directory-machtigingen voor alle niet-lokale accounts toevoegen aan de groep. anders wordt er een fout op.
| Zorg ervoor dat| Geeft aan of de groepen zijn. Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat de groepen niet bestaan. Instellen om "" (de standaardwaarde), zorgt u ervoor dat de groepen bestaan.|
| Leden| Gebruik deze eigenschap om het lidmaatschap van de huidige vervangen door de opgegeven leden. De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*. Als u deze eigenschap in een configuratie hebt ingesteld, mag niet een gebruiken de **MembersToExclude** of **MembersToInclude** eigenschap. In dat geval wordt er een fout gegenereerd.|
| MembersToInclude| Gebruik deze eigenschap leden toevoegen aan het bestaande lidmaatschap van de groep. De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*. Als u deze eigenschap in een configuratie hebt ingesteld, gebruik niet de **leden** eigenschap. In dat geval wordt er een fout gegenereerd.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = "[ ResourceType] ResourceName"''.|

## <a name="example-1-ensuring-groups-are-present"></a>Voorbeeld 1: Ervoor zorgen dat groepen zijn aanwezig

Het volgende voorbeeld ziet hoe u om ervoor te zorgen dat er twee groepen met de naam "myGroup" en "myOtherGroup" aanwezig zijn.

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> In dit voorbeeld maakt gebruik van referenties zonder gecodeerde tekst voor het gemak. Zie voor meer informatie over het versleutelen van de referenties in het MOF-configuratiebestand [beveiligen van het MOF-bestand](../../../pull-server/secureMOF.md).
