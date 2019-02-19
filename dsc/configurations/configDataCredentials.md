---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Referentieopties in configuratiegegevens
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/18/2019
ms.locfileid: "55686374"
---
# <a name="credentials-options-in-configuration-data"></a>Referentieopties in configuratiegegevens

>Van toepassing op: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Ongecodeerde wachtwoorden en domeingebruikers

DSC-configuraties met een referentie zonder versleuteling wordt een foutbericht over ongecodeerde wachtwoorden worden gegenereerd.
DSC wordt ook een waarschuwing gegenereerd wanneer met domeinreferenties.
Als u wilt onderdrukken deze fout- en waarschuwingsberichten de sleutelwoorden gebruiken om DSC configuration gegevens:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Opslaan van/overdragen ongecodeerde wachtwoorden ongecodeerd is doorgaans niet beveiligd. Referenties beveiligen met behulp van de technieken die verderop in dit onderwerp aan bod wordt aanbevolen.
> De service Azure Automation DSC kunt u om referenties in om te worden gecompileerd in configuraties en veilig opgeslagen centraal te beheren.
> Zie voor informatie: [Compileren van DSC-configuraties / Referentieassets](/azure/automation/automation-dsc-compile#credential-assets)

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

In dit voorbeeld wordt een [groep](../resources/resources.md) resource uit de `PSDesiredStateConfiguration` ingebouwde DSC-resource-module.
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

In dit voorbeeld heeft twee problemen:

1. Een fout wordt uitgelegd ongecodeerde wachtwoorden worden niet aanbevolen
2. Een waarschuwing adviseert tegen het gebruik van een domeinreferentie

De vlaggen **PSDSCAllowPlainTextPassword** en **PSDSCAllowDomainUser** onderdrukken van de fout en waarschuwing waarin de gebruiker van het risico.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Het eerste foutbericht heeft een URL met documentatie.
Deze koppeling wordt uitgelegd hoe u voor het versleutelen van wachtwoorden met een [ConfigurationData](./configData.md) structuur en een certificaat.
Voor meer informatie over certificaten en DSC [lezen van dit bericht](http://aka.ms/certs4dsc).

Als u een wachtwoord als tekst zonder opmaak, de bron is vereist de `PsDscAllowPlainTextPassword` -sleutelwoord in de configuratiegegevens sectie als volgt:

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

### <a name="localhostmof"></a>localhost.MOF

De **PSDSCAllowPlainTextPassword** vlag vereist dat de gebruiker bevestigt het risico van opslaan ongecodeerde wachtwoorden in een MOF-bestand. In de gegenereerde MOF-bestand, zelfs als een **PSCredential** object bevat een **SecureString** is gebruikt, wordt de wachtwoorden nog steeds wordt weergegeven als tekst zonder opmaak. Dit is de enige keer dat de referenties worden weergegeven. Toegang krijgen tot deze iedereen toegang tot de Administrator-account van MOF-bestand biedt.

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

### <a name="credentials-in-transit-and-at-rest"></a>Referenties die worden verzonden en in rust

- De **PSDscAllowPlainTextPassword** vlag kan het compileren van MOF-bestanden die wachtwoorden in ongecodeerde tekst bevatten.
  Voorzorgsmaatregelen nemen bij het opslaan van MOF-bestanden met wachtwoorden met leesbare tekst.
- Wanneer het MOF-bestand wordt geleverd aan een knooppunt in **Push** modus WinRM versleutelt de communicatie ter bescherming van het wachtwoord met ongecodeerde tekst, tenzij u de standaardwaarde vervangen door de **AllowUnencrypted** parameter.
  - Het MOF-bestand in rust versleutelen van de MOF met een certificaat worden beveiligd voordat deze is toegepast op een knooppunt.
- In **Pull** modus, kunt u Windows pull-server om HTTPS te gebruiken voor het versleutelen van verkeer dat gebruikmaakt van het protocol is opgegeven in Internet Information Server. Zie voor meer informatie de artikelen [instellen van een DSC-pull-client](../pull-server/pullclient.md) en [beveiligen MOF-bestanden met certificaten](../pull-server/secureMOF.md).
  - In de [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) -service, Pull-verkeer wordt altijd versleuteld.
- Klik op het knooppunt MOF-bestanden zijn versleuteld in rust vanaf PowerShell 5.0.
  - In PowerShell 4.0 MOF zijn bestanden niet-versleuteld in rust, tenzij ze zijn versleuteld met een certificaat wanneer ze ingedrukt of opgehaald naar het knooppunt.

**Microsoft adviseert om te voorkomen dat ongecodeerde wachtwoorden vanwege de aanzienlijke beveiligingsrisico met zich mee.**

## <a name="domain-credentials"></a>Domeinreferenties

De voorbeeld-configuratiescript opnieuw uitgevoerd (met of zonder versleuteling), nog steeds de waarschuwing die gebruik van een domein-account voor een referentie wordt niet aanbevolen genereert.
Met een lokale account elimineert mogelijke blootstelling van domeinreferenties die kan worden gebruikt op andere servers.

**Als u referenties met DSC-resources, liever dan een lokale account via een domeinaccount, indien mogelijk.**

Als er een '\\'of'\@' in de `Username` eigenschap van de referentie en vervolgens de DSC zal worden beschouwd als een domeinaccount.
Er is een uitzondering voor "localhost", "127.0.0.1" en ":: 1" in het domeingedeelte van de gebruikersnaam.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

In de DSC `Group` resource voorbeeld hierboven opvragen van een Active Directory-domein *vereist* een domeinaccount.
In dit geval toevoegen de `PSDscAllowDomainUser` eigenschap in op de `ConfigurationData` blokkeren als volgt:

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

Het configuratiescript wordt nu het MOF-bestand zonder fouten of waarschuwingen gegenereerd.
