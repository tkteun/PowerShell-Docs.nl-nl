---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
description: Biedt een mechanisme voor het beheren van lokale groepen op het doel knooppunt.
title: DSC-groeps resource
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941402"
---
# <a name="dsc-groupset-resource"></a>DSC-groeps resource

> Van toepassing op: Windows Power shell 5. x

De **groeps** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doel knooppunt. Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die de [groeps bron](groupResource.md) aanroept voor elke groep die is opgegeven in de para meter `GroupName`.

Gebruik deze resource als u dezelfde lijst met leden wilt toevoegen aan of verwijderen uit meer dan één groep, als u meer dan één groep wilt verwijderen of meer dan één groep met dezelfde lijst met leden wilt toevoegen.

## <a name="syntax"></a>Syntaxis

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|groupName |De namen van de groepen waarvoor u een specifieke status wilt controleren. |
|Leden |Gebruik deze eigenschap om het huidige groepslid maatschap te vervangen door de opgegeven leden. De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName`. Als u deze eigenschap in een configuratie instelt, moet u de eigenschap **MembersToExclude** of **MembersToInclude** niet gebruiken. Als u dit doet, wordt er een fout gegenereerd. |
|Beschrijving |De beschrijving van de groep. |
|MembersToInclude |Gebruik deze eigenschap om leden toe te voegen aan het bestaande lidmaatschap van de groep. De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName`. Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken. Als u dit doet, wordt er een fout gegenereerd. |
|MembersToExclude |Gebruik deze eigenschap om leden te verwijderen uit het bestaande lidmaatschap van de groepen. De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName`. Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken. Als u dit doet, wordt er een fout gegenereerd. |
|Referentie |De referenties die nodig zijn voor toegang tot externe bronnen. Dit account moet over de juiste Active Directory machtigingen beschikken om alle niet-lokale accounts aan de groep toe te voegen. anders treedt er een fout op. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. Als de ID van het resource-configuratie script blok dat u eerst wilt uitvoeren bijvoorbeeld de naam ResourceName is, en het type van de bron resource is, is de syntaxis voor het gebruik van deze eigenschap `DependsOn = "[ResourceType]ResourceName"`. |
|Zo |Hiermee wordt aangegeven of de groepen bestaan. Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de groepen niet bestaan. **Als u** deze instelling inschakelt, zorgt u ervoor dat de groepen bestaan. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example-1-ensuring-groups-are-present"></a>Voor beeld 1: controleren of groepen aanwezig zijn

In het volgende voor beeld ziet u hoe u ervoor kunt zorgen dat twee groepen met de naam ' myGroup ' en ' myOtherGroup ' aanwezig zijn.

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
> In dit voor beeld worden Lees bare referenties gebruikt voor eenvoud. Zie [het MOF-bestand beveiligen](../../../pull-server/secureMOF.md)voor meer informatie over het versleutelen van referenties in het MOF-configuratie bestand.