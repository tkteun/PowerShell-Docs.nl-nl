---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Referenties opties in configuratie gegevens
description: Met DSC kunt u referenties opgeven zodat de configuratie-instellingen kunnen worden toegepast in de context van een specifiek gebruikers account in plaats van het lokale systeem account.
ms.openlocfilehash: 41478dc042ca59fb70aa033de81b589a4a8c09c7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658632"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="afe18-104">Referenties opties in configuratie gegevens</span><span class="sxs-lookup"><span data-stu-id="afe18-104">Credentials Options in Configuration Data</span></span>

> <span data-ttu-id="afe18-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="afe18-105">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="afe18-106">Wacht woorden voor tekst zonder opmaak en domein gebruikers</span><span class="sxs-lookup"><span data-stu-id="afe18-106">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="afe18-107">DSC-configuraties met een referentie zonder versleuteling genereren een fout bericht over wacht woorden met tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="afe18-107">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span> <span data-ttu-id="afe18-108">Daarnaast genereert DSC een waarschuwing wanneer domein referenties worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="afe18-108">Also, DSC will generate a warning when using domain credentials.</span></span> <span data-ttu-id="afe18-109">Als u deze fout-en waarschuwings berichten wilt onderdrukken, gebruikt u de sleutel woorden DSC-configuratie gegevens:</span><span class="sxs-lookup"><span data-stu-id="afe18-109">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="afe18-110">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="afe18-110">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="afe18-111">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="afe18-111">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="afe18-112">Het opslaan/verzenden van Lees bare wacht woorden die niet zijn versleuteld, is doorgaans niet veilig.</span><span class="sxs-lookup"><span data-stu-id="afe18-112">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="afe18-113">Het is raadzaam om referenties te beveiligen met behulp van de technieken die verderop in dit onderwerp worden besproken.</span><span class="sxs-lookup"><span data-stu-id="afe18-113">Securing credentials by using the techniques covered later in this topic is recommended.</span></span> <span data-ttu-id="afe18-114">Met de Azure Automation DSC-service kunt u de referenties die in configuraties worden gecompileerd, centraal beheren en veilig opslaan.</span><span class="sxs-lookup"><span data-stu-id="afe18-114">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span> <span data-ttu-id="afe18-115">Zie voor meer informatie: [DSC-configuraties compileren/referentie-assets](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="afe18-115">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="afe18-116">Referenties verwerken in DSC</span><span class="sxs-lookup"><span data-stu-id="afe18-116">Handling Credentials in DSC</span></span>

<span data-ttu-id="afe18-117">DSC-configuratie resources worden `Local System` standaard uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="afe18-117">DSC configuration resources run as `Local System` by default.</span></span> <span data-ttu-id="afe18-118">Sommige resources hebben echter een referentie nodig, bijvoorbeeld wanneer de `Package` bron software moet installeren onder een specifiek gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="afe18-118">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="afe18-119">In eerdere bronnen is een vastgelegde `Credential` eigenschaps naam gebruikt om dit te verwerken.</span><span class="sxs-lookup"><span data-stu-id="afe18-119">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span> <span data-ttu-id="afe18-120">WMF 5,0 heeft een automatische `PsDscRunAsCredential` eigenschap voor alle resources toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="afe18-120">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="afe18-121">`PsDscRunAsCredential`Zie [DSC uitvoeren met gebruikers referenties](runAsUser.md)voor meer informatie over het gebruik van.</span><span class="sxs-lookup"><span data-stu-id="afe18-121">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span> <span data-ttu-id="afe18-122">Nieuwe resources en aangepaste resources kunnen deze automatische eigenschap gebruiken in plaats van een eigen eigenschap voor referenties te maken.</span><span class="sxs-lookup"><span data-stu-id="afe18-122">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="afe18-123">Het ontwerp van sommige resources is om een specifieke reden om meerdere referenties te gebruiken, en ze hebben hun eigen referentie-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="afe18-123">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="afe18-124">Als u de beschik bare referentie-eigenschappen voor een resource wilt zoeken, gebruikt u ofwel `Get-DscResource -Name ResourceName -Syntax` de IntelliSense in de ISE ( `CTRL+SPACE` ).</span><span class="sxs-lookup"><span data-stu-id="afe18-124">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="afe18-125">In dit voor beeld wordt een [groeps](../resources/resources.md) resource uit de `PSDesiredStateConfiguration` ingebouwde DSC-resource module gebruikt.</span><span class="sxs-lookup"><span data-stu-id="afe18-125">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span> <span data-ttu-id="afe18-126">Hiermee kunnen lokale groepen worden gemaakt en leden worden toegevoegd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="afe18-126">It can create local groups and add or remove members.</span></span> <span data-ttu-id="afe18-127">Deze accepteert zowel de `Credential` eigenschap als de automatische `PsDscRunAsCredential` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="afe18-127">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span> <span data-ttu-id="afe18-128">De resource maakt echter alleen gebruik van de `Credential` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="afe18-128">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="afe18-129">`PsDscRunAsCredential`Zie [DSC uitvoeren met gebruikers referenties](runAsUser.md)voor meer informatie over de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="afe18-129">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="afe18-130">Voor beeld: de eigenschap groeps bron referentie</span><span class="sxs-lookup"><span data-stu-id="afe18-130">Example: The Group resource Credential property</span></span>

<span data-ttu-id="afe18-131">DSC wordt uitgevoerd onder `Local System` , zodat het al machtigingen heeft voor het wijzigen van lokale gebruikers en groepen.</span><span class="sxs-lookup"><span data-stu-id="afe18-131">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span> <span data-ttu-id="afe18-132">Als het toegevoegde lid een lokaal account is, is er geen referentie nood zakelijk.</span><span class="sxs-lookup"><span data-stu-id="afe18-132">If the member added is a local account, then no credential is necessary.</span></span> <span data-ttu-id="afe18-133">Als de `Group` resource een domein account aan de lokale groep toevoegt, is een referentie vereist.</span><span class="sxs-lookup"><span data-stu-id="afe18-133">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="afe18-134">Anonieme query's voor Active Directory zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="afe18-134">Anonymous queries to Active Directory are not allowed.</span></span> <span data-ttu-id="afe18-135">De `Credential` eigenschap van de `Group` resource is het domein account dat wordt gebruikt om Active Directory op te vragen.</span><span class="sxs-lookup"><span data-stu-id="afe18-135">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span> <span data-ttu-id="afe18-136">In de meeste gevallen kan dit een Gene riek gebruikers account zijn, omdat standaard gebruikers de meeste objecten in Active Directory kunnen *lezen* .</span><span class="sxs-lookup"><span data-stu-id="afe18-136">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="afe18-137">Voorbeeld configuratie</span><span class="sxs-lookup"><span data-stu-id="afe18-137">Example Configuration</span></span>

<span data-ttu-id="afe18-138">De volgende voorbeeld code maakt gebruik van DSC om een lokale groep te vullen met een domein gebruiker:</span><span class="sxs-lookup"><span data-stu-id="afe18-138">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="afe18-139">Deze code genereert een fout-en waarschuwings bericht:</span><span class="sxs-lookup"><span data-stu-id="afe18-139">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="afe18-140">Dit voor beeld heeft twee problemen:</span><span class="sxs-lookup"><span data-stu-id="afe18-140">This example has two issues:</span></span>

1. <span data-ttu-id="afe18-141">In een fout wordt uitgelegd dat wacht woorden voor tekst zonder opmaak niet worden aanbevolen</span><span class="sxs-lookup"><span data-stu-id="afe18-141">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="afe18-142">Er wordt een waarschuwing geadviseerd voor het gebruik van een domein referentie</span><span class="sxs-lookup"><span data-stu-id="afe18-142">A warning advises against using a domain credential</span></span>

<span data-ttu-id="afe18-143">De vlaggen **PSDSCAllowPlainTextPassword** en **PSDSCAllowDomainUser** onderdrukken de fout en waarschuwing die de gebruiker van het betrokken risico informeert.</span><span class="sxs-lookup"><span data-stu-id="afe18-143">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="afe18-144">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="afe18-144">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="afe18-145">Het eerste fout bericht heeft een URL met documentatie.</span><span class="sxs-lookup"><span data-stu-id="afe18-145">The first error message has a URL with documentation.</span></span> <span data-ttu-id="afe18-146">In deze koppeling wordt uitgelegd hoe u wacht woorden versleutelt met behulp van een [ConfigurationData](./configData.md) -structuur en een certificaat.</span><span class="sxs-lookup"><span data-stu-id="afe18-146">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span> <span data-ttu-id="afe18-147">[Lees dit bericht](https://aka.ms/certs4dsc)voor meer informatie over certificaten en DSC.</span><span class="sxs-lookup"><span data-stu-id="afe18-147">For more information on certificates and DSC [read this post](https://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="afe18-148">Voor het afdwingen van een wacht woord voor tekst zonder opmaak vereist de bron het `PsDscAllowPlainTextPassword` sleutel woord in de sectie configuratie gegevens als volgt:</span><span class="sxs-lookup"><span data-stu-id="afe18-148">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="afe18-149">localhost. MOF</span><span class="sxs-lookup"><span data-stu-id="afe18-149">localhost.mof</span></span>

<span data-ttu-id="afe18-150">De **PSDSCAllowPlainTextPassword** -vlag vereist dat de gebruiker het risico erkent dat wacht woorden met tekst zonder opmaak in een MOF-bestand worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="afe18-150">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="afe18-151">Hoewel er in het gegenereerde MOF-bestand een **PSCredential** -object met een **SecureString** is gebruikt, worden de wacht woorden nog steeds weer gegeven als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="afe18-151">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="afe18-152">Dit is de enige keer dat de referenties worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="afe18-152">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="afe18-153">Als u toegang krijgt tot dit MOF-bestand, krijgt iedereen toegang tot het beheerders account.</span><span class="sxs-lookup"><span data-stu-id="afe18-153">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="afe18-154">Referenties bij overdracht en in rust</span><span class="sxs-lookup"><span data-stu-id="afe18-154">Credentials in transit and at rest</span></span>

- <span data-ttu-id="afe18-155">Met de vlag **PSDscAllowPlainTextPassword** wordt het compileren van MOF-bestanden met wacht woorden in Lees bare tekst toegestaan.</span><span class="sxs-lookup"><span data-stu-id="afe18-155">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span> <span data-ttu-id="afe18-156">Houd voorzorgsmaatregelen bij het opslaan van MOF-bestanden met wacht woorden met een lees bare tekst.</span><span class="sxs-lookup"><span data-stu-id="afe18-156">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="afe18-157">Wanneer het MOF-bestand wordt geleverd aan een knoop punt in de **Push** -modus, versleutelt WinRM de communicatie om het wacht woord voor lees bare tekst te beveiligen tenzij u de standaard instelling overschrijft met de para meter **AllowUnencrypted** .</span><span class="sxs-lookup"><span data-stu-id="afe18-157">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="afe18-158">Het versleutelen van de MOF met een certificaat beschermt het MOF-bestand op rest voordat het op een knoop punt is toegepast.</span><span class="sxs-lookup"><span data-stu-id="afe18-158">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="afe18-159">In de **pull** -modus kunt u Windows pull server configureren voor het gebruik van HTTPS voor het versleutelen van verkeer met het protocol dat is opgegeven in Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="afe18-159">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="afe18-160">Zie de artikelen [een DSC-pull-client instellen](../pull-server/pullclient.md) en [MOF-bestanden beveiligen met certificaten](../pull-server/secureMOF.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="afe18-160">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="afe18-161">Pull-verkeer in de [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) -service wordt altijd versleuteld.</span><span class="sxs-lookup"><span data-stu-id="afe18-161">In the [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="afe18-162">Op het knoop punt worden MOF-bestanden op rest versleuteld vanaf Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="afe18-162">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="afe18-163">De MOF-bestanden van Power Shell 4,0 zijn niet-versleuteld in rust, tenzij ze zijn versleuteld met een certificaat wanneer ze naar het knoop punt zijn gepusht of worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="afe18-163">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="afe18-164">**Micro soft adviseert om wacht woorden voor onbewerkte tekst te voor komen vanwege het grote beveiligings risico.**</span><span class="sxs-lookup"><span data-stu-id="afe18-164">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="afe18-165">Domein referenties</span><span class="sxs-lookup"><span data-stu-id="afe18-165">Domain Credentials</span></span>

<span data-ttu-id="afe18-166">Wanneer het voorbeeld configuratie script opnieuw wordt uitgevoerd (met of zonder versleuteling), genereert nog steeds de waarschuwing dat het gebruik van een domein account voor een referentie wordt afgeraden.</span><span class="sxs-lookup"><span data-stu-id="afe18-166">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span> <span data-ttu-id="afe18-167">Door gebruik te maken van een lokaal account, elimineert u mogelijke bloot stelling van domein referenties die op andere servers kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="afe18-167">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="afe18-168">**Wanneer u referenties gebruikt met DSC-resources, moet u, indien mogelijk, een lokaal account via een domein account gebruiken.**</span><span class="sxs-lookup"><span data-stu-id="afe18-168">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="afe18-169">Als \\ \@ de eigenschap van de referentie een ' ' of ' ' bevat `Username` , wordt deze door DSC als een domein account behandeld.</span><span class="sxs-lookup"><span data-stu-id="afe18-169">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span> <span data-ttu-id="afe18-170">Er is een uitzonde ring voor ' localhost ', ' 127.0.0.1 ' en ':: 1 ' in het domein gedeelte van de gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="afe18-170">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="afe18-171">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="afe18-171">PSDscAllowDomainUser</span></span>

<span data-ttu-id="afe18-172">In het `Group` bovenstaande voor beeld van DSC-resources *moet* u een domein account voor een query uitvoeren op een Active Directory domein.</span><span class="sxs-lookup"><span data-stu-id="afe18-172">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span> <span data-ttu-id="afe18-173">In dit geval voegt `PSDscAllowDomainUser` u de eigenschap als volgt toe aan het `ConfigurationData` blok:</span><span class="sxs-lookup"><span data-stu-id="afe18-173">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="afe18-174">Nu wordt het MOF-bestand met het configuratie script gegenereerd zonder fouten of waarschuwingen.</span><span class="sxs-lookup"><span data-stu-id="afe18-174">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
