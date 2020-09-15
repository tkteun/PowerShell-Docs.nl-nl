---
ms.date: 07/16/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC-groeps resource
ms.openlocfilehash: 5570d46d872e205917eef49bfa869419b20a77b0
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464210"
---
# <a name="dsc-group-resource"></a>DSC-groeps resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **groeps** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale groepen op het doel knooppunt.

## <a name="syntax"></a>Syntax

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|GroupName |De naam van de groep waarvoor u een specifieke status wilt controleren. |
|Referentie |De referenties die nodig zijn voor toegang tot externe bronnen. Dit account moet over de juiste Active Directory machtigingen beschikken om alle niet-lokale accounts aan de groep toe te voegen. anders treedt er een fout op wanneer de configuratie wordt uitgevoerd op het doel knooppunt.
|Beschrijving |De beschrijving van de groep. |
|Leden |Gebruik deze eigenschap om het huidige groepslid maatschap te vervangen door de opgegeven leden. De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName` . Als u deze eigenschap in een configuratie instelt, moet u de eigenschap **MembersToExclude** of **MembersToInclude** niet gebruiken. Hierdoor wordt er een fout gegenereerd. |
|MembersToExclude |Gebruik deze eigenschap om leden te verwijderen uit het bestaande lidmaatschap van de groep. De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName` . Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken. Hierdoor wordt er een fout gegenereerd. |
|MembersToInclude |Gebruik deze eigenschap om leden toe te voegen aan het bestaande lidmaatschap van de groep. De waarde van deze eigenschap is een matrix met teken reeksen van het formulier `Domain\UserName` . Als u deze eigenschap in een configuratie instelt, mag u de eigenschap **Members** niet gebruiken. Als u dit doet, wordt er een fout gegenereerd. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt aangegeven of de groep bestaat. Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de groep niet bestaat. **Als u** deze instelling inschakelt, zorgt u ervoor dat de groep bestaat. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example-1-ensure-group-is-not-present"></a>Voor beeld 1: ervoor zorgen dat groep niet aanwezig is

In het volgende voor beeld ziet u hoe u ervoor kunt zorgen dat een groep met de naam ' TestGroup ' ontbreekt.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a>Voor beeld 2: domein gebruiker toevoegen aan lokale groep

In het volgende voor beeld ziet u hoe u een Active Directory gebruiker toevoegt aan de lokale groep Administrators als onderdeel van een test omgeving voor meerdere machines waar u al een PSCredential gebruikt voor het lokale beheerders account. Aangezien dit ook wordt gebruikt voor het domein beheerders account (na domein promotie), moeten we deze bestaande PSCredential converteren naar een gebruiks vriendelijke domein referentie. Vervolgens kunnen we een domein gebruiker toevoegen aan de lokale groep Administrators op de lidserver.

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

In het volgende voor beeld ziet u hoe u ervoor zorgt dat een lokale groep TigerTeamAdmins op de server TigerTeamSource.Contoso.Com geen bepaald domein account bevat Contoso\JerryG.

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
