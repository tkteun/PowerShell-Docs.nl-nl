---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Referentieopties in de configuratiegegevens
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080149"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="690b9-103">Referentieopties in de configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="690b9-103">Credentials Options in Configuration Data</span></span>

><span data-ttu-id="690b9-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="690b9-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="690b9-105">Tekst zonder opmaak wachtwoorden en domeingebruikers</span><span class="sxs-lookup"><span data-stu-id="690b9-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="690b9-106">DSC-configuraties met een referentie zonder versleuteling wordt een foutbericht over ongecodeerde wachtwoorden worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="690b9-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="690b9-107">DSC wordt ook een waarschuwing gegenereerd wanneer met domeinreferenties.</span><span class="sxs-lookup"><span data-stu-id="690b9-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="690b9-108">Gebruik de trefwoorden DSC-configuratie gegevens als u wilt onderdrukken deze fout- en waarschuwingsberichten:</span><span class="sxs-lookup"><span data-stu-id="690b9-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="690b9-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="690b9-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="690b9-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="690b9-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="690b9-111">Opslag/verzending van niet-versleutelde wachtwoorden in platte tekst is in het algemeen niet beveiligd.</span><span class="sxs-lookup"><span data-stu-id="690b9-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="690b9-112">Referenties beveiligen met behulp van de technieken die verderop in dit onderwerp aan bod wordt aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="690b9-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="690b9-113">De service Azure Automation DSC kunt u om referenties op om te worden gecompileerd in configuraties en veilig opgeslagen centraal te beheren.</span><span class="sxs-lookup"><span data-stu-id="690b9-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="690b9-114">Zie voor informatie: [DSC-configuraties compileren / Referentieassets](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="690b9-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="690b9-115">Verwerken van de referenties in DSC</span><span class="sxs-lookup"><span data-stu-id="690b9-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="690b9-116">DSC-configuratieresources run as- `Local System` standaard.</span><span class="sxs-lookup"><span data-stu-id="690b9-116">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="690b9-117">Sommige resources moeten echter een referentie, bijvoorbeeld wanneer de `Package` resource nodig heeft voor het installeren van software die onder een bepaalde gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="690b9-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="690b9-118">Eerder gebruikte vastgelegde `Credential` eigenschapsnaam voor het afhandelen van dit.</span><span class="sxs-lookup"><span data-stu-id="690b9-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="690b9-119">WMF 5.0 toegevoegd automatisch `PsDscRunAsCredential` eigenschap voor alle resources.</span><span class="sxs-lookup"><span data-stu-id="690b9-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="690b9-120">Voor informatie over het gebruik van `PsDscRunAsCredential`, Zie [DSC uitvoeren met gebruikersreferenties](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="690b9-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="690b9-121">Nieuwere resources en aangepaste resources kunnen u deze automatische eigenschap gebruiken in plaats van het maken van hun eigen eigenschap voor referenties.</span><span class="sxs-lookup"><span data-stu-id="690b9-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="690b9-122">Het ontwerp van sommige resources zijn meerdere referenties gebruiken om een bepaalde reden en hebben ze hun eigen referentie-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="690b9-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="690b9-123">Eigenschappen van een resource gebruiken op de beschikbare referentie niet vinden een `Get-DscResource -Name ResourceName -Syntax` of de Intellisense in de ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="690b9-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="690b9-124">In dit voorbeeld wordt een [groep](../resources/resources.md) -resource in de `PSDesiredStateConfiguration` ingebouwde DSC-resource-module.</span><span class="sxs-lookup"><span data-stu-id="690b9-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="690b9-125">Het kan maken van lokale groepen en leden toevoegen of verwijderen.</span><span class="sxs-lookup"><span data-stu-id="690b9-125">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="690b9-126">Accepteert zowel de `Credential` eigenschap en de automatische `PsDscRunAsCredential` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="690b9-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="690b9-127">Echter, de resource maakt alleen gebruik van de `Credential` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="690b9-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="690b9-128">Voor meer informatie over de `PsDscRunAsCredential` eigenschap, Zie [DSC uitvoeren met gebruikersreferenties](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="690b9-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="690b9-129">Voorbeeld: De bron van gebruikersgroep referentie-eigenschap</span><span class="sxs-lookup"><span data-stu-id="690b9-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="690b9-130">DSC wordt uitgevoerd onder `Local System`, zodat deze heeft al machtigingen om lokale gebruikers en groepen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="690b9-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="690b9-131">Als het lid toegevoegd een lokaal account is, zijn er is geen referentie is nodig.</span><span class="sxs-lookup"><span data-stu-id="690b9-131">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="690b9-132">Als de `Group` resource wordt een domeinaccount toegevoegd aan de lokale groep en vervolgens een referentie nodig is.</span><span class="sxs-lookup"><span data-stu-id="690b9-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="690b9-133">Anonieme query's naar Active Directory zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="690b9-133">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="690b9-134">De `Credential` eigenschap van de `Group` resource is het domeinaccount dat wordt gebruikt om te zoeken in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="690b9-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="690b9-135">Voor de meeste doeleinden mogelijk een algemeen gebruikersaccount, standaard kunnen gebruikers *lezen* meeste van de objecten in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="690b9-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="690b9-136">Voorbeeld van een configuratie</span><span class="sxs-lookup"><span data-stu-id="690b9-136">Example Configuration</span></span>

<span data-ttu-id="690b9-137">De volgende voorbeeldcode maakt gebruik van DSC voor het vullen van een lokale groep met een domeingebruiker:</span><span class="sxs-lookup"><span data-stu-id="690b9-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="690b9-138">Deze code genereert een fout en de waarschuwing weergegeven:</span><span class="sxs-lookup"><span data-stu-id="690b9-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="690b9-139">In dit voorbeeld heeft twee problemen:</span><span class="sxs-lookup"><span data-stu-id="690b9-139">This example has two issues:</span></span>

1. <span data-ttu-id="690b9-140">Een fout wordt uitgelegd dat ongecodeerde wachtwoorden worden niet aanbevolen</span><span class="sxs-lookup"><span data-stu-id="690b9-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="690b9-141">Een waarschuwing wordt beschermd tegen het gebruik van een domeinreferentie</span><span class="sxs-lookup"><span data-stu-id="690b9-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="690b9-142">De vlaggen **PSDSCAllowPlainTextPassword** en **PSDSCAllowDomainUser** onderdrukken van de fout en waarschuwing waarin de gebruiker van het risico.</span><span class="sxs-lookup"><span data-stu-id="690b9-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="690b9-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="690b9-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="690b9-144">Het eerste foutbericht heeft een URL met de documentatie.</span><span class="sxs-lookup"><span data-stu-id="690b9-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="690b9-145">Deze koppeling wordt uitgelegd hoe u voor het versleutelen van wachtwoorden met een [ConfigurationData](./configData.md) structuur en een certificaat.</span><span class="sxs-lookup"><span data-stu-id="690b9-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="690b9-146">Voor meer informatie over certificaten en DSC [leest u dit bericht](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="690b9-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="690b9-147">Als u wilt afdwingen dat een wachtwoord als tekst zonder opmaak, de resource vereist de `PsDscAllowPlainTextPassword` sleutelwoord in de configuratiegegevens sectie als volgt:</span><span class="sxs-lookup"><span data-stu-id="690b9-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="690b9-148">localhost.MOF</span><span class="sxs-lookup"><span data-stu-id="690b9-148">localhost.mof</span></span>

<span data-ttu-id="690b9-149">De **PSDSCAllowPlainTextPassword** vlag vereist dat de gebruiker bevestigt de kans op tekst zonder opmaak wachtwoorden opslaan in een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="690b9-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="690b9-150">In de gegenereerde MOF-bestand, zelfs als een **PSCredential** object bevat een **SecureString** is gebruikt, wordt de wachtwoorden worden nog wel weergegeven als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="690b9-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="690b9-151">Dit is de enige keer dat de referenties worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="690b9-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="690b9-152">Toegang krijgen tot dit MOF-bestand biedt iedereen toegang tot het Administrator-account.</span><span class="sxs-lookup"><span data-stu-id="690b9-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="690b9-153">Referenties in-transit en inactieve</span><span class="sxs-lookup"><span data-stu-id="690b9-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="690b9-154">De **PSDscAllowPlainTextPassword** vlag kan de compilatie van MOF-bestanden die wachtwoorden in niet-versleutelde tekst bevatten.</span><span class="sxs-lookup"><span data-stu-id="690b9-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span>
  <span data-ttu-id="690b9-155">Voorzorgsmaatregelen nemen bij het opslaan van MOF-bestanden met niet-versleutelde tekst wachtwoorden.</span><span class="sxs-lookup"><span data-stu-id="690b9-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="690b9-156">Wanneer het MOF-bestand wordt geleverd aan een knooppunt in **Push** modus WinRM versleutelt de communicatie ter bescherming van het wachtwoord niet-versleutelde tekst, tenzij u de standaardwaarde van vervangen door de **AllowUnencrypted** parameter.</span><span class="sxs-lookup"><span data-stu-id="690b9-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="690b9-157">Het MOF-bestand in rust versleutelen van de MOF met een certificaat worden beveiligd voordat deze is toegepast op een knooppunt.</span><span class="sxs-lookup"><span data-stu-id="690b9-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="690b9-158">In **Pull** modus, u kunt Windows pull-server configureren om HTTPS te gebruiken voor het versleutelen van verkeer dat gebruikmaakt van het protocol is opgegeven in Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="690b9-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="690b9-159">Zie voor meer informatie de artikelen [instellen van een DSC-pull-client](../pull-server/pullclient.md) en [beveiligen MOF-bestanden met certificaten](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="690b9-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="690b9-160">In de [Statusconfiguratie van Azure Automation](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) -service, Pull-verkeer wordt altijd versleuteld.</span><span class="sxs-lookup"><span data-stu-id="690b9-160">In the [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="690b9-161">Klik op het knooppunt MOF-bestanden zijn versleuteld in rust vanaf PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="690b9-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="690b9-162">Bestanden zijn in PowerShell 4.0 MOF niet-versleuteld in rust, tenzij ze zijn versleuteld met een certificaat wanneer ze gepusht of naar het knooppunt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="690b9-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="690b9-163">**Microsoft adviseert om te voorkomen dat ongecodeerde wachtwoorden vanwege de aanzienlijke beveiligingsrisico's.**</span><span class="sxs-lookup"><span data-stu-id="690b9-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="690b9-164">Domeinreferenties</span><span class="sxs-lookup"><span data-stu-id="690b9-164">Domain Credentials</span></span>

<span data-ttu-id="690b9-165">Het voorbeeld van de configuratie-script opnieuw is uitgevoerd (met of zonder versleuteling), nog steeds worden gegenereerd voor de waarschuwing die met behulp van een domein-account voor een referentie wordt niet aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="690b9-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="690b9-166">Met behulp van een lokaal account wordt voorkomen dat potentiële blootstelling van domeinreferenties die kan worden gebruikt op andere servers.</span><span class="sxs-lookup"><span data-stu-id="690b9-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="690b9-167">**Als u referenties voor DSC-resources, moet u een lokaal account liever via een domeinaccount, indien mogelijk.**</span><span class="sxs-lookup"><span data-stu-id="690b9-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="690b9-168">Als er een '\\'of'\@' in de `Username` eigenschap van de referentie en vervolgens de DSC zal worden beschouwd als een domeinaccount.</span><span class="sxs-lookup"><span data-stu-id="690b9-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="690b9-169">Er is een uitzondering voor 'localhost', '127.0.0.1' en ':: 1" in het domeingedeelte van de naam van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="690b9-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="690b9-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="690b9-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="690b9-171">In de DSC `Group` resourcevoorbeeld hierboven, uitvoeren van query's een Active Directory-domein *vereist* een domeinaccount.</span><span class="sxs-lookup"><span data-stu-id="690b9-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="690b9-172">In dit geval voegen de `PSDscAllowDomainUser` eigenschap in op de `ConfigurationData` blokkeren als volgt:</span><span class="sxs-lookup"><span data-stu-id="690b9-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="690b9-173">Het configuratiescript wordt nu het MOF-bestand met geen fouten of waarschuwingen hebben gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="690b9-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
