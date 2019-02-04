---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Referentieopties in de configuratiegegevens
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686374"
---
# <a name="credentials-options-in-configuration-data"></a>Referentieopties in de configuratiegegevens

>Van toepassing op: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Tekst zonder opmaak wachtwoorden en domeingebruikers

DSC-configuraties met een referentie zonder versleuteling wordt een foutbericht over ongecodeerde wachtwoorden worden gegenereerd.
DSC wordt ook een waarschuwing gegenereerd wanneer met domeinreferenties.
Gebruik de trefwoorden DSC-configuratie gegevens als u wilt onderdrukken deze fout- en waarschuwingsberichten:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Opslag/verzending van niet-versleutelde wachtwoorden in platte tekst is in het algemeen niet beveiligd. Referenties beveiligen met behulp van de technieken die verderop in dit onderwerp aan bod wordt aanbevolen.
> De service Azure Automation DSC kunt u om referenties op om te worden gecompileerd in configuraties en veilig opgeslagen centraal te beheren.
> Zie voor informatie: [DSC-configuraties compileren / Referentieassets](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Verwerken van de referenties in DSC

DSC-configuratieresources run as- `Local System` standaard.
Sommige resources moeten echter een referentie, bijvoorbeeld wanneer de `Package` resource nodig heeft voor het installeren van software die onder een bepaalde gebruikersaccount.

Eerder gebruikte vastgelegde `Credential` eigenschapsnaam voor het afhandelen van dit.
WMF 5.0 toegevoegd automatisch `PsDscRunAsCredential` eigenschap voor alle resources.
Voor informatie over het gebruik van `PsDscRunAsCredential`, Zie [DSC uitvoeren met gebruikersreferenties](runAsUser.md).
Nieuwere resources en aangepaste resources kunnen u deze automatische eigenschap gebruiken in plaats van het maken van hun eigen eigenschap voor referenties.

> [!NOTE]
> Het ontwerp van sommige resources zijn meerdere referenties gebruiken om een bepaalde reden en hebben ze hun eigen referentie-eigenschappen.

Eigenschappen van een resource gebruiken op de beschikbare referentie niet vinden een `Get-DscResource -Name ResourceName -Syntax` of de Intellisense in de ISE (`CTRL+SPACE`).

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

In dit voorbeeld wordt een [groep](../resources/resources.md) -resource in de `PSDesiredStateConfiguration` ingebouwde DSC-resource-module.
Het kan maken van lokale groepen en leden toevoegen of verwijderen.
Accepteert zowel de `Credential` eigenschap en de automatische `PsDscRunAsCredential` eigenschap.
Echter, de resource maakt alleen gebruik van de `Credential` eigenschap.

Voor meer informatie over de `PsDscRunAsCredential` eigenschap, Zie [DSC uitvoeren met gebruikersreferenties](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Voorbeeld: De bron van gebruikersgroep referentie-eigenschap

DSC wordt uitgevoerd onder `Local System`, zodat deze heeft al machtigingen om lokale gebruikers en groepen te wijzigen.
Als het lid toegevoegd een lokaal account is, zijn er is geen referentie is nodig.
Als de `Group` resource wordt een domeinaccount toegevoegd aan de lokale groep en vervolgens een referentie nodig is.

Anonieme query's naar Active Directory zijn niet toegestaan.
De `Credential` eigenschap van de `Group` resource is het domeinaccount dat wordt gebruikt om te zoeken in Active Directory.
Voor de meeste doeleinden mogelijk een algemeen gebruikersaccount, standaard kunnen gebruikers *lezen* meeste van de objecten in Active Directory.

## <a name="example-configuration"></a>Voorbeeld van een configuratie

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

1. Een fout wordt uitgelegd dat ongecodeerde wachtwoorden worden niet aanbevolen
2. Een waarschuwing wordt beschermd tegen het gebruik van een domeinreferentie

De vlaggen **PSDSCAllowPlainTextPassword** en **PSDSCAllowDomainUser** onderdrukken van de fout en waarschuwing waarin de gebruiker van het risico.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Het eerste foutbericht heeft een URL met de documentatie.
Deze koppeling wordt uitgelegd hoe u voor het versleutelen van wachtwoorden met een [ConfigurationData](./configData.md) structuur en een certificaat.
Voor meer informatie over certificaten en DSC [leest u dit bericht](http://aka.ms/certs4dsc).

Als u wilt afdwingen dat een wachtwoord als tekst zonder opmaak, de resource vereist de `PsDscAllowPlainTextPassword` sleutelwoord in de configuratiegegevens sectie als volgt:

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

De **PSDSCAllowPlainTextPassword** vlag vereist dat de gebruiker bevestigt de kans op tekst zonder opmaak wachtwoorden opslaan in een MOF-bestand. In de gegenereerde MOF-bestand, zelfs als een **PSCredential** object bevat een **SecureString** is gebruikt, wordt de wachtwoorden worden nog wel weergegeven als tekst zonder opmaak. Dit is de enige keer dat de referenties worden weergegeven. Toegang krijgen tot dit MOF-bestand biedt iedereen toegang tot het Administrator-account.

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

### <a name="credentials-in-transit-and-at-rest"></a>Referenties in-transit en inactieve

- De **PSDscAllowPlainTextPassword** vlag kan de compilatie van MOF-bestanden die wachtwoorden in niet-versleutelde tekst bevatten.
  Voorzorgsmaatregelen nemen bij het opslaan van MOF-bestanden met niet-versleutelde tekst wachtwoorden.
- Wanneer het MOF-bestand wordt geleverd aan een knooppunt in **Push** modus WinRM versleutelt de communicatie ter bescherming van het wachtwoord niet-versleutelde tekst, tenzij u de standaardwaarde van vervangen door de **AllowUnencrypted** parameter.
  - Het MOF-bestand in rust versleutelen van de MOF met een certificaat worden beveiligd voordat deze is toegepast op een knooppunt.
- In **Pull** modus, u kunt Windows pull-server configureren om HTTPS te gebruiken voor het versleutelen van verkeer dat gebruikmaakt van het protocol is opgegeven in Internet Information Server. Zie voor meer informatie de artikelen [instellen van een DSC-pull-client](../pull-server/pullclient.md) en [beveiligen MOF-bestanden met certificaten](../pull-server/secureMOF.md).
  - In de [Statusconfiguratie van Azure Automation](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) -service, Pull-verkeer wordt altijd versleuteld.
- Klik op het knooppunt MOF-bestanden zijn versleuteld in rust vanaf PowerShell 5.0.
  - Bestanden zijn in PowerShell 4.0 MOF niet-versleuteld in rust, tenzij ze zijn versleuteld met een certificaat wanneer ze gepusht of naar het knooppunt opgehaald.

**Microsoft adviseert om te voorkomen dat ongecodeerde wachtwoorden vanwege de aanzienlijke beveiligingsrisico's.**

## <a name="domain-credentials"></a>Domeinreferenties

Het voorbeeld van de configuratie-script opnieuw is uitgevoerd (met of zonder versleuteling), nog steeds worden gegenereerd voor de waarschuwing die met behulp van een domein-account voor een referentie wordt niet aanbevolen.
Met behulp van een lokaal account wordt voorkomen dat potentiële blootstelling van domeinreferenties die kan worden gebruikt op andere servers.

**Als u referenties voor DSC-resources, moet u een lokaal account liever via een domeinaccount, indien mogelijk.**

Als er een '\\'of'\@' in de `Username` eigenschap van de referentie en vervolgens de DSC zal worden beschouwd als een domeinaccount.
Er is een uitzondering voor 'localhost', '127.0.0.1' en ':: 1" in het domeingedeelte van de naam van de gebruiker.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

In de DSC `Group` resourcevoorbeeld hierboven, uitvoeren van query's een Active Directory-domein *vereist* een domeinaccount.
In dit geval voegen de `PSDscAllowDomainUser` eigenschap in op de `ConfigurationData` blokkeren als volgt:

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

Het configuratiescript wordt nu het MOF-bestand met geen fouten of waarschuwingen hebben gegenereerd.
