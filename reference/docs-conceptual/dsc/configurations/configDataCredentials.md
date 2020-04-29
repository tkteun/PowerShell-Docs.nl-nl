---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Referenties opties in configuratie gegevens
ms.openlocfilehash: aac27f1ff4b4287b53745fa3b946fb3de84771c2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870554"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="40531-103">Referenties opties in configuratie gegevens</span><span class="sxs-lookup"><span data-stu-id="40531-103">Credentials Options in Configuration Data</span></span>

> <span data-ttu-id="40531-104">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="40531-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="40531-105">Wacht woorden voor tekst zonder opmaak en domein gebruikers</span><span class="sxs-lookup"><span data-stu-id="40531-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="40531-106">DSC-configuraties met een referentie zonder versleuteling genereren een fout bericht over wacht woorden met tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="40531-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span> <span data-ttu-id="40531-107">Daarnaast genereert DSC een waarschuwing wanneer domein referenties worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40531-107">Also, DSC will generate a warning when using domain credentials.</span></span> <span data-ttu-id="40531-108">Als u deze fout-en waarschuwings berichten wilt onderdrukken, gebruikt u de sleutel woorden DSC-configuratie gegevens:</span><span class="sxs-lookup"><span data-stu-id="40531-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="40531-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="40531-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="40531-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="40531-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="40531-111">Het opslaan/verzenden van Lees bare wacht woorden die niet zijn versleuteld, is doorgaans niet veilig.</span><span class="sxs-lookup"><span data-stu-id="40531-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="40531-112">Het is raadzaam om referenties te beveiligen met behulp van de technieken die verderop in dit onderwerp worden besproken.</span><span class="sxs-lookup"><span data-stu-id="40531-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span> <span data-ttu-id="40531-113">Met de Azure Automation DSC-service kunt u de referenties die in configuraties worden gecompileerd, centraal beheren en veilig opslaan.</span><span class="sxs-lookup"><span data-stu-id="40531-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span> <span data-ttu-id="40531-114">Zie voor meer informatie: [DSC-configuraties compileren/referentie-assets](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="40531-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="40531-115">Referenties verwerken in DSC</span><span class="sxs-lookup"><span data-stu-id="40531-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="40531-116">DSC-configuratie resources worden `Local System` standaard uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="40531-116">DSC configuration resources run as `Local System` by default.</span></span> <span data-ttu-id="40531-117">Sommige resources hebben echter een referentie nodig, bijvoorbeeld wanneer de `Package` bron software moet installeren onder een specifiek gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="40531-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="40531-118">In eerdere bronnen is een vastgelegde `Credential` eigenschaps naam gebruikt om dit te verwerken.</span><span class="sxs-lookup"><span data-stu-id="40531-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span> <span data-ttu-id="40531-119">WMF 5,0 heeft een automatische `PsDscRunAsCredential` eigenschap voor alle resources toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="40531-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="40531-120">Zie `PsDscRunAsCredential` [DSC uitvoeren met gebruikers referenties](runAsUser.md)voor meer informatie over het gebruik van.</span><span class="sxs-lookup"><span data-stu-id="40531-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span> <span data-ttu-id="40531-121">Nieuwe resources en aangepaste resources kunnen deze automatische eigenschap gebruiken in plaats van een eigen eigenschap voor referenties te maken.</span><span class="sxs-lookup"><span data-stu-id="40531-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="40531-122">Het ontwerp van sommige resources is om een specifieke reden om meerdere referenties te gebruiken, en ze hebben hun eigen referentie-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="40531-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="40531-123">Als u de beschik bare referentie-eigenschappen voor een `Get-DscResource -Name ResourceName -Syntax` resource wilt zoeken, gebruikt u ofwel`CTRL+SPACE`de IntelliSense in de ISE ().</span><span class="sxs-lookup"><span data-stu-id="40531-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="40531-124">In dit voor beeld wordt een [groeps](../resources/resources.md) resource uit de `PSDesiredStateConfiguration` ingebouwde DSC-resource module gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40531-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span> <span data-ttu-id="40531-125">Hiermee kunnen lokale groepen worden gemaakt en leden worden toegevoegd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="40531-125">It can create local groups and add or remove members.</span></span> <span data-ttu-id="40531-126">Deze accepteert zowel de `Credential` eigenschap als de automatische `PsDscRunAsCredential` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="40531-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span> <span data-ttu-id="40531-127">De resource maakt echter alleen gebruik van `Credential` de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="40531-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="40531-128">Zie `PsDscRunAsCredential` [DSC uitvoeren met gebruikers referenties](runAsUser.md)voor meer informatie over de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="40531-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="40531-129">Voor beeld: de eigenschap groeps bron referentie</span><span class="sxs-lookup"><span data-stu-id="40531-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="40531-130">DSC wordt uitgevoerd `Local System`onder, zodat het al machtigingen heeft voor het wijzigen van lokale gebruikers en groepen.</span><span class="sxs-lookup"><span data-stu-id="40531-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span> <span data-ttu-id="40531-131">Als het toegevoegde lid een lokaal account is, is er geen referentie nood zakelijk.</span><span class="sxs-lookup"><span data-stu-id="40531-131">If the member added is a local account, then no credential is necessary.</span></span> <span data-ttu-id="40531-132">Als de `Group` resource een domein account aan de lokale groep toevoegt, is een referentie vereist.</span><span class="sxs-lookup"><span data-stu-id="40531-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="40531-133">Anonieme query's voor Active Directory zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="40531-133">Anonymous queries to Active Directory are not allowed.</span></span> <span data-ttu-id="40531-134">De `Credential` eigenschap van de `Group` resource is het domein account dat wordt gebruikt om Active Directory op te vragen.</span><span class="sxs-lookup"><span data-stu-id="40531-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span> <span data-ttu-id="40531-135">In de meeste gevallen kan dit een Gene riek gebruikers account zijn, omdat standaard gebruikers de meeste objecten in Active Directory kunnen *lezen* .</span><span class="sxs-lookup"><span data-stu-id="40531-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="40531-136">Voorbeeld configuratie</span><span class="sxs-lookup"><span data-stu-id="40531-136">Example Configuration</span></span>

<span data-ttu-id="40531-137">De volgende voorbeeld code maakt gebruik van DSC om een lokale groep te vullen met een domein gebruiker:</span><span class="sxs-lookup"><span data-stu-id="40531-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="40531-138">Deze code genereert een fout-en waarschuwings bericht:</span><span class="sxs-lookup"><span data-stu-id="40531-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="40531-139">Dit voor beeld heeft twee problemen:</span><span class="sxs-lookup"><span data-stu-id="40531-139">This example has two issues:</span></span>

1. <span data-ttu-id="40531-140">In een fout wordt uitgelegd dat wacht woorden voor tekst zonder opmaak niet worden aanbevolen</span><span class="sxs-lookup"><span data-stu-id="40531-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="40531-141">Er wordt een waarschuwing geadviseerd voor het gebruik van een domein referentie</span><span class="sxs-lookup"><span data-stu-id="40531-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="40531-142">De vlaggen **PSDSCAllowPlainTextPassword** en **PSDSCAllowDomainUser** onderdrukken de fout en waarschuwing die de gebruiker van het betrokken risico informeert.</span><span class="sxs-lookup"><span data-stu-id="40531-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="40531-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="40531-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="40531-144">Het eerste fout bericht heeft een URL met documentatie.</span><span class="sxs-lookup"><span data-stu-id="40531-144">The first error message has a URL with documentation.</span></span> <span data-ttu-id="40531-145">In deze koppeling wordt uitgelegd hoe u wacht woorden versleutelt met behulp van een [ConfigurationData](./configData.md) -structuur en een certificaat.</span><span class="sxs-lookup"><span data-stu-id="40531-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span> <span data-ttu-id="40531-146">[Lees dit bericht](https://aka.ms/certs4dsc)voor meer informatie over certificaten en DSC.</span><span class="sxs-lookup"><span data-stu-id="40531-146">For more information on certificates and DSC [read this post](https://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="40531-147">Voor het afdwingen van een wacht woord voor tekst zonder `PsDscAllowPlainTextPassword` opmaak vereist de bron het sleutel woord in de sectie configuratie gegevens als volgt:</span><span class="sxs-lookup"><span data-stu-id="40531-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="40531-148">localhost. MOF</span><span class="sxs-lookup"><span data-stu-id="40531-148">localhost.mof</span></span>

<span data-ttu-id="40531-149">De **PSDSCAllowPlainTextPassword** -vlag vereist dat de gebruiker het risico erkent dat wacht woorden met tekst zonder opmaak in een MOF-bestand worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="40531-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="40531-150">Hoewel er in het gegenereerde MOF-bestand een **PSCredential** -object met een **SecureString** is gebruikt, worden de wacht woorden nog steeds weer gegeven als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="40531-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="40531-151">Dit is de enige keer dat de referenties worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="40531-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="40531-152">Als u toegang krijgt tot dit MOF-bestand, krijgt iedereen toegang tot het beheerders account.</span><span class="sxs-lookup"><span data-stu-id="40531-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="40531-153">Referenties bij overdracht en in rust</span><span class="sxs-lookup"><span data-stu-id="40531-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="40531-154">Met de vlag **PSDscAllowPlainTextPassword** wordt het compileren van MOF-bestanden met wacht woorden in Lees bare tekst toegestaan.</span><span class="sxs-lookup"><span data-stu-id="40531-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span> <span data-ttu-id="40531-155">Houd voorzorgsmaatregelen bij het opslaan van MOF-bestanden met wacht woorden met een lees bare tekst.</span><span class="sxs-lookup"><span data-stu-id="40531-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="40531-156">Wanneer het MOF-bestand wordt geleverd aan een knoop punt in de **Push** -modus, versleutelt WinRM de communicatie om het wacht woord voor lees bare tekst te beveiligen tenzij u de standaard instelling overschrijft met de para meter **AllowUnencrypted** .</span><span class="sxs-lookup"><span data-stu-id="40531-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="40531-157">Het versleutelen van de MOF met een certificaat beschermt het MOF-bestand op rest voordat het op een knoop punt is toegepast.</span><span class="sxs-lookup"><span data-stu-id="40531-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="40531-158">In de **pull** -modus kunt u Windows pull server configureren voor het gebruik van HTTPS voor het versleutelen van verkeer met het protocol dat is opgegeven in Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="40531-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="40531-159">Zie de artikelen [een DSC-pull-client instellen](../pull-server/pullclient.md) en [MOF-bestanden beveiligen met certificaten](../pull-server/secureMOF.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40531-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="40531-160">Pull-verkeer in de [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) -service wordt altijd versleuteld.</span><span class="sxs-lookup"><span data-stu-id="40531-160">In the [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="40531-161">Op het knoop punt worden MOF-bestanden op rest versleuteld vanaf Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="40531-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="40531-162">De MOF-bestanden van Power Shell 4,0 zijn niet-versleuteld in rust, tenzij ze zijn versleuteld met een certificaat wanneer ze naar het knoop punt zijn gepusht of worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="40531-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="40531-163">**Micro soft adviseert om wacht woorden voor onbewerkte tekst te voor komen vanwege het grote beveiligings risico.**</span><span class="sxs-lookup"><span data-stu-id="40531-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="40531-164">Domein referenties</span><span class="sxs-lookup"><span data-stu-id="40531-164">Domain Credentials</span></span>

<span data-ttu-id="40531-165">Wanneer het voorbeeld configuratie script opnieuw wordt uitgevoerd (met of zonder versleuteling), genereert nog steeds de waarschuwing dat het gebruik van een domein account voor een referentie wordt afgeraden.</span><span class="sxs-lookup"><span data-stu-id="40531-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span> <span data-ttu-id="40531-166">Door gebruik te maken van een lokaal account, elimineert u mogelijke bloot stelling van domein referenties die op andere servers kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40531-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="40531-167">**Wanneer u referenties gebruikt met DSC-resources, moet u, indien mogelijk, een lokaal account via een domein account gebruiken.**</span><span class="sxs-lookup"><span data-stu-id="40531-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="40531-168">Als de `Username` eigenschap van de\\referentie een '\@' of ' ' bevat, wordt deze door DSC als een domein account behandeld.</span><span class="sxs-lookup"><span data-stu-id="40531-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span> <span data-ttu-id="40531-169">Er is een uitzonde ring voor ' localhost ', ' 127.0.0.1 ' en ':: 1 ' in het domein gedeelte van de gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="40531-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="40531-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="40531-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="40531-171">In het bovenstaande `Group` voor beeld van DSC-resources *moet* u een domein account voor een query uitvoeren op een Active Directory domein.</span><span class="sxs-lookup"><span data-stu-id="40531-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span> <span data-ttu-id="40531-172">In dit geval voegt u `PSDscAllowDomainUser` de eigenschap als `ConfigurationData` volgt toe aan het blok:</span><span class="sxs-lookup"><span data-stu-id="40531-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="40531-173">Nu wordt het MOF-bestand met het configuratie script gegenereerd zonder fouten of waarschuwingen.</span><span class="sxs-lookup"><span data-stu-id="40531-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
