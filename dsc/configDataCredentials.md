---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Referentieopties in configuratiegegevens
ms.openlocfilehash: 3f1c75c65b357220856dd8e50694eb77808dee41
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="credentials-options-in-configuration-data"></a>Referentieopties in configuratiegegevens
>Van toepassing op: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Ongecodeerde wachtwoorden en domeingebruikers

DSC-configuraties met een referentie zonder versleuteling wordt een foutbericht over ongecodeerde wachtwoorden worden gegenereerd.
DSC wordt ook een waarschuwing gegenereerd wanneer met domeinreferenties.
Als u wilt onderdrukken deze fout- en waarschuwingsberichten de sleutelwoorden gebruiken om DSC configuration gegevens:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> Opslaan van/overdragen ongecodeerde wachtwoorden ongecodeerd is doorgaans niet beveiligd. Referenties beveiligen met behulp van de technieken die verderop in dit onderwerp aan bod wordt aanbevolen.
> De service Azure Automation DSC kunt u om referenties in om te worden gecompileerd in configuraties en veilig opgeslagen centraal te beheren.
> Zie voor informatie: [DSC-configuraties compileren / Referentieassets](/azure/automation/automation-dsc-compile#credential-assets)

Hier volgt een voorbeeld van het doorgeven van referenties voor tekst zonder opmaak:

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a>Afhandeling van referenties in DSC

Run as-configuratie-DSC-resources `Local System` standaard.
Sommige resources moeten echter een referentie, bijvoorbeeld wanneer de `Package` resource nodig heeft voor het installeren van software met een specifiek gebruikersaccount.

Eerdere bronnen gebruikt een vastgelegde `Credential` naam voor het afhandelen van deze eigenschap.
WMF 5.0 toegevoegd automatisch `PsDscRunAsCredential` eigenschap voor alle resources.
Voor informatie over het gebruik van `PsDscRunAsCredential`, Zie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md).
Nieuwere resources en aangepaste resources kunnen u deze automatische eigenschap gebruiken in plaats van hun eigen eigenschap voor referenties maken.

> [!NOTE]
> Het ontwerp van sommige resources zijn meerdere referenties gebruiken om een bepaalde reden en hebben hun eigen referentie-eigenschappen.

De beschikbare referentie vinden gebruiken eigenschappen van een resource `Get-DscResource -Name ResourceName -Syntax` of de Intellisense in de ISE (`CTRL+SPACE`).

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
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

In dit voorbeeld wordt een [groep](https://msdn.microsoft.com/powershell/dsc/groupresource) resource uit de `PSDesiredStateConfiguration` ingebouwde DSC-resource-module.
Deze kan lokale groepen maken en leden toevoegen of verwijderen.
De cmdlet accepteert zowel de `Credential` eigenschap en de automatische `PsDscRunAsCredential` eigenschap.
De resource alleen gebruikt echter de `Credential` eigenschap.

Voor meer informatie over de `PsDscRunAsCredential` eigenschap, Zie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Voorbeeld: De bron van referentie-eigenschap

DSC wordt uitgevoerd onder `Local System`, zodat het al machtigingen heeft voor lokale gebruikers en groepen te wijzigen.
Als het lid dat wordt toegevoegd een lokaal account is, zijn er is geen referentie is nodig.
Als de `Group` resource wordt een domeinaccount toegevoegd aan de lokale groep en vervolgens een referentie op die nodig is.

Anonieme query's naar Active Directory zijn niet toegestaan.
De `Credential` eigenschap van de `Group` resource wordt het domeinaccount dat wordt gebruikt om te zoeken in Active Directory.
Voor de meeste doeleinden mogelijk een algemene gebruikersaccount standaard gebruikers kunnen *lezen* de meeste van de objecten in Active Directory.

## <a name="example-configuration"></a>Voorbeeldconfiguratie

De volgende voorbeeldcode maakt gebruik van DSC voor het vullen van een lokale groep met een domeingebruiker:

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

Deze code genereert een fout en de waarschuwing weergegeven:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

In dit voorbeeld heeft twee problemen:
1. Een fout wordt uitgelegd ongecodeerde wachtwoorden worden niet aanbevolen
2. Een waarschuwing adviseert tegen het gebruik van een domeinreferentie

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

Het eerste foutbericht heeft een URL met documentatie.
Deze koppeling wordt uitgelegd hoe u voor het versleutelen van wachtwoorden met een [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) structuur en een certificaat.
Voor meer informatie over certificaten en DSC [lezen van dit bericht](http://aka.ms/certs4dsc).

Als u een wachtwoord als tekst zonder opmaak, de bron is vereist de `PsDscAllowPlainTextPassword` -sleutelwoord in de configuratiegegevens sectie als volgt:

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

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> `NodeName` kan niet gelijk zijn aan sterretje, de naam van een specifiek knooppunt is verplicht.

**Microsoft adviseert om te voorkomen dat ongecodeerde wachtwoorden vanwege de aanzienlijke beveiligingsrisico met zich mee.**

Een uitzondering hierop is wanneer u de service Azure Automation DSC lezen omdat de gegevens wordt altijd versleuteld (in doorvoer in rust in de service en in rust in het knooppunt) opgeslagen.

## <a name="domain-credentials"></a>Domeinreferenties

De voorbeeld-configuratiescript opnieuw uitgevoerd (met of zonder versleuteling), nog steeds de waarschuwing die gebruik van een domein-account voor een referentie wordt niet aanbevolen genereert.
Met een lokale account elimineert mogelijke blootstelling van domeinreferenties die kan worden gebruikt op andere servers.

**Als u referenties met DSC-resources, liever dan een lokale account via een domeinaccount, indien mogelijk.**

Als er een '\' of '\@' in de `Username` eigenschap van de referentie en vervolgens de DSC zal worden beschouwd als een domeinaccount.
Er is een uitzondering voor "localhost", "127.0.0.1" en ":: 1" in het domeingedeelte van de gebruikersnaam.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

In de DSC `Group` resource voorbeeld hierboven opvragen van een Active Directory-domein *vereist* een domeinaccount.
In dit geval toevoegen de `PSDscAllowDomainUser` eigenschap in op de `ConfigurationData` blokkeren als volgt:

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

Het configuratiescript wordt nu het MOF-bestand zonder fouten of waarschuwingen gegenereerd.