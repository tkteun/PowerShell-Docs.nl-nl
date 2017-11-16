---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
description: Biedt een mechanisme voor het beheren van lokale groepen in het doelknooppunt.
title: DSC-GroupSet Resource
ms.openlocfilehash: 0907a968bfc660adc873c28e8be6572d1d5cb993
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-groupset-resource"></a>DSC-GroupSet Resource

> Van toepassing op: Windows Windows PowerShell 5.0

De **GroupSet** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van lokale groepen in het doelknooppunt. Deze bron is een [samengestelde bron](authoringResourceComposite.md) die roept de [groep resource](groupResource.md) voor elke groep die is opgegeven in de `GroupName` parameter.

Gebruik deze bron als u wilt toevoegen en/of verwijderen van dezelfde lijst met leden aan meer dan één groep, meer dan één groep te verwijderen of toevoegen van meer dan één groep met dezelfde lijst met leden.

##<a name="syntax"></a>Syntaxis ##
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

|  Eigenschap  |  Beschrijving   | 
|---|---| 
| Groepsnaam| De namen van de groepen waarvoor u wilt om te controleren of een specifieke status.| 
| MembersToExclude| Gebruik deze eigenschap leden verwijderen uit het bestaande lidmaatschap van de groepen. De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*. Als u deze eigenschap in een configuratie instellen, gebruikt u niet de **leden** eigenschap. Hierdoor wordt een fout gegenereerd.| 
| referentie| De referenties die zijn vereist voor toegang tot externe bronnen. **Opmerking**: dit account de juiste Active Directory-machtigingen voor alle niet-lokale accounts toevoegen aan de groep moet hebben; anders wordt een fout optreedt.
| Zorg ervoor dat| Hiermee wordt aangegeven of de groepen bestaan. Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat de groepen bestaan niet. Instellen om "" (de standaardwaarde), zorgt u ervoor dat de groepen bestaan.| 
| Leden| Gebruik deze eigenschap het lidmaatschap van de huidige vervangt door de opgegeven leden. De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*. Als u deze eigenschap in een configuratie hebt ingesteld, geen gebruik van ofwel de **MembersToExclude** of **MembersToInclude** eigenschap. Hierdoor wordt een fout gegenereerd.| 
| MembersToInclude| Gebruik deze eigenschap leden toevoegen aan het bestaande lidmaatschap van de groep. De waarde van deze eigenschap is een matrix met tekenreeksen van het formulier *domein*\\*gebruikersnaam*. Als u deze eigenschap in een configuratie instellen, gebruikt u niet de **leden** eigenschap. Hierdoor wordt een fout gegenereerd.| 
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = '[ ResourceType] ResourceName' ''.| 

## <a name="example-1"></a>Voorbeeld 1

Het volgende voorbeeld laat zien hoe om ervoor te zorgen dat er twee groepen genaamd 'myGroup' en 'myOtherGroup' aanwezig zijn. 

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

>**Opmerking:** in dit voorbeeld gebruikt de referenties van de tekst zonder opmaak voor eenvoud. Zie voor meer informatie over het coderen van referenties in het MOF-bestand voor configuratie [beveiligen van het MOF-bestand](secureMOF.md).


