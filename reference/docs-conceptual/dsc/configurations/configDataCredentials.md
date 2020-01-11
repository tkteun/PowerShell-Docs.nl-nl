---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Referenties opties in configuratie gegevens
ms.openlocfilehash: aac27f1ff4b4287b53745fa3b946fb3de84771c2
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870554"
---
# <a name="credentials-options-in-configuration-data"></a>Referenties opties in configuratie gegevens

> Van toepassing op: Windows Power shell 5,0

## <a name="plain-text-passwords-and-domain-users"></a>Wacht woorden voor tekst zonder opmaak en domein gebruikers

DSC-configuraties met een referentie zonder versleuteling genereren een fout bericht over wacht woorden met tekst zonder opmaak. Daarnaast genereert DSC een waarschuwing wanneer domein referenties worden gebruikt. Als u deze fout-en waarschuwings berichten wilt onderdrukken, gebruikt u de sleutel woorden DSC-configuratie gegevens:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Het opslaan/verzenden van Lees bare wacht woorden die niet zijn versleuteld, is doorgaans niet veilig. Het is raadzaam om referenties te beveiligen met behulp van de technieken die verderop in dit onderwerp worden besproken. Met de Azure Automation DSC-service kunt u de referenties die in configuraties worden gecompileerd, centraal beheren en veilig opslaan. Zie voor meer informatie: [DSC-configuraties compileren/referentie-assets](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Referenties verwerken in DSC

DSC-configuratie resources worden standaard uitgevoerd als `Local System`. Sommige resources hebben echter een referentie nodig, bijvoorbeeld wanneer de `Package` resource software moet installeren onder een specifiek gebruikers account.

In eerdere bronnen is een hardcoded `Credential` eigenschaps naam gebruikt om dit te verwerken. WMF 5,0 heeft een automatische `PsDscRunAsCredential`-eigenschap toegevoegd voor alle resources. Zie [DSC uitvoeren met gebruikers referenties](runAsUser.md)voor meer informatie over het gebruik van `PsDscRunAsCredential`. Nieuwe resources en aangepaste resources kunnen deze automatische eigenschap gebruiken in plaats van een eigen eigenschap voor referenties te maken.

> [!NOTE]
> Het ontwerp van sommige resources is om een specifieke reden om meerdere referenties te gebruiken, en ze hebben hun eigen referentie-eigenschappen.

Als u de beschik bare referentie-eigenschappen voor een resource wilt zoeken, gebruikt u `Get-DscResource -Name ResourceName -Syntax` of IntelliSense in het ISE (`CTRL+SPACE`).

```powershell
Get-DscResource -Name Group -Syntax
```

```Output
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

In dit voor beeld wordt een [groeps](../resources/resources.md) resource uit de `PSDesiredStateConfiguration` ingebouwde DSC-resource module gebruikt. Hiermee kunnen lokale groepen worden gemaakt en leden worden toegevoegd of verwijderd. Zowel de eigenschap `Credential` als de eigenschap Automatic `PsDscRunAsCredential` wordt geaccepteerd. De resource maakt echter alleen gebruik van de eigenschap `Credential`.

Zie [DSC uitvoeren met gebruikers referenties](runAsUser.md)voor meer informatie over de eigenschap `PsDscRunAsCredential`.

## <a name="example-the-group-resource-credential-property"></a>Voor beeld: de eigenschap groeps bron referentie

DSC wordt uitgevoerd onder `Local System`, zodat het al machtigingen heeft voor het wijzigen van lokale gebruikers en groepen. Als het toegevoegde lid een lokaal account is, is er geen referentie nood zakelijk. Als de `Group` resource een domein account aan de lokale groep toevoegt, is een referentie vereist.

Anonieme query's voor Active Directory zijn niet toegestaan. De eigenschap `Credential` van de `Group` resource is het domein account dat wordt gebruikt voor het opvragen van Active Directory. In de meeste gevallen kan dit een Gene riek gebruikers account zijn, omdat standaard gebruikers de meeste objecten in Active Directory kunnen *lezen* .

## <a name="example-configuration"></a>Voorbeeld configuratie

De volgende voorbeeld code maakt gebruik van DSC om een lokale groep te vullen met een domein gebruiker:

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Deze code genereert een fout-en waarschuwings bericht:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

Dit voor beeld heeft twee problemen:

1. In een fout wordt uitgelegd dat wacht woorden voor tekst zonder opmaak niet worden aanbevolen
2. Er wordt een waarschuwing geadviseerd voor het gebruik van een domein referentie

De vlaggen **PSDSCAllowPlainTextPassword** en **PSDSCAllowDomainUser** onderdrukken de fout en waarschuwing die de gebruiker van het betrokken risico informeert.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Het eerste fout bericht heeft een URL met documentatie. In deze koppeling wordt uitgelegd hoe u wacht woorden versleutelt met behulp van een [ConfigurationData](./configData.md) -structuur en een certificaat. [Lees dit bericht](https://aka.ms/certs4dsc)voor meer informatie over certificaten en DSC.

Voor het afdwingen van een wacht woord voor tekst zonder opmaak vereist de resource het sleutel woord `PsDscAllowPlainTextPassword` in de sectie configuratie gegevens als volgt:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost. MOF

De **PSDSCAllowPlainTextPassword** -vlag vereist dat de gebruiker het risico erkent dat wacht woorden met tekst zonder opmaak in een MOF-bestand worden opgeslagen. Hoewel er in het gegenereerde MOF-bestand een **PSCredential** -object met een **SecureString** is gebruikt, worden de wacht woorden nog steeds weer gegeven als tekst zonder opmaak. Dit is de enige keer dat de referenties worden weer gegeven. Als u toegang krijgt tot dit MOF-bestand, krijgt iedereen toegang tot het beheerders account.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Referenties bij overdracht en in rust

- Met de vlag **PSDscAllowPlainTextPassword** wordt het compileren van MOF-bestanden met wacht woorden in Lees bare tekst toegestaan. Houd voorzorgsmaatregelen bij het opslaan van MOF-bestanden met wacht woorden met een lees bare tekst.
- Wanneer het MOF-bestand wordt geleverd aan een knoop punt in de **Push** -modus, versleutelt WinRM de communicatie om het wacht woord voor lees bare tekst te beveiligen tenzij u de standaard instelling overschrijft met de para meter **AllowUnencrypted** .
  - Het versleutelen van de MOF met een certificaat beschermt het MOF-bestand op rest voordat het op een knoop punt is toegepast.
- In de **pull** -modus kunt u Windows pull server configureren voor het gebruik van HTTPS voor het versleutelen van verkeer met het protocol dat is opgegeven in Internet Information Server. Zie de artikelen [een DSC-pull-client instellen](../pull-server/pullclient.md) en [MOF-bestanden beveiligen met certificaten](../pull-server/secureMOF.md)voor meer informatie.
  - Pull-verkeer in de [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) -service wordt altijd versleuteld.
- Op het knoop punt worden MOF-bestanden op rest versleuteld vanaf Power shell 5,0.
  - De MOF-bestanden van Power Shell 4,0 zijn niet-versleuteld in rust, tenzij ze zijn versleuteld met een certificaat wanneer ze naar het knoop punt zijn gepusht of worden opgehaald.

**Micro soft adviseert om wacht woorden voor onbewerkte tekst te voor komen vanwege het grote beveiligings risico.**

## <a name="domain-credentials"></a>Domein referenties

Wanneer het voorbeeld configuratie script opnieuw wordt uitgevoerd (met of zonder versleuteling), genereert nog steeds de waarschuwing dat het gebruik van een domein account voor een referentie wordt afgeraden. Door gebruik te maken van een lokaal account, elimineert u mogelijke bloot stelling van domein referenties die op andere servers kunnen worden gebruikt.

**Wanneer u referenties gebruikt met DSC-resources, moet u, indien mogelijk, een lokaal account via een domein account gebruiken.**

Als de eigenschap `Username` van de referentie een '\\' of '\@' bevat, wordt deze door DSC als een domein account behandeld. Er is een uitzonde ring voor ' localhost ', ' 127.0.0.1 ' en ':: 1 ' in het domein gedeelte van de gebruikers naam.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

In het bovenstaande voor beeld van DSC `Group`-resource is een domein account *vereist* voor het uitvoeren van een query op een Active Directory-domein. In dit geval voegt u de eigenschap `PSDscAllowDomainUser` als volgt toe aan het blok `ConfigurationData`:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Nu wordt het MOF-bestand met het configuratie script gegenereerd zonder fouten of waarschuwingen.
