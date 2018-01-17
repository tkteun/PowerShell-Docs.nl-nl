---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Referentieopties in configuratiegegevens
ms.openlocfilehash: 15cdb29127d9774c58e1d6518bbba56273e7defd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="dc1d9-103">Referentieopties in configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="dc1d9-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="dc1d9-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dc1d9-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="dc1d9-105">Ongecodeerde wachtwoorden en domeingebruikers</span><span class="sxs-lookup"><span data-stu-id="dc1d9-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="dc1d9-106">DSC-configuraties met een referentie zonder versleuteling wordt een foutbericht over ongecodeerde wachtwoorden worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="dc1d9-107">DSC wordt ook een waarschuwing gegenereerd wanneer met domeinreferenties.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="dc1d9-108">Als u wilt onderdrukken deze fout- en waarschuwingsberichten de sleutelwoorden gebruiken om DSC configuration gegevens:</span><span class="sxs-lookup"><span data-stu-id="dc1d9-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="dc1d9-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="dc1d9-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="dc1d9-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="dc1d9-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="dc1d9-111">Opslaan van/overdragen ongecodeerde wachtwoorden ongecodeerd is doorgaans niet beveiligd.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="dc1d9-112">Referenties beveiligen met behulp van de technieken die verderop in dit onderwerp aan bod wordt aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="dc1d9-113">De service Azure Automation DSC kunt u om referenties in om te worden gecompileerd in configuraties en veilig opgeslagen centraal te beheren.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="dc1d9-114">Zie voor informatie: [DSC-configuraties compileren / Referentieassets](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="dc1d9-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="dc1d9-115">Hier volgt een voorbeeld van het doorgeven van referenties voor tekst zonder opmaak:</span><span class="sxs-lookup"><span data-stu-id="dc1d9-115">The following is an example of passing plain text credentials:</span></span>

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

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="dc1d9-116">Afhandeling van referenties in DSC</span><span class="sxs-lookup"><span data-stu-id="dc1d9-116">Handling Credentials in DSC</span></span>

<span data-ttu-id="dc1d9-117">Run as-configuratie-DSC-resources `Local System` standaard.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-117">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="dc1d9-118">Sommige resources moeten echter een referentie, bijvoorbeeld wanneer de `Package` resource nodig heeft voor het installeren van software met een specifiek gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-118">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="dc1d9-119">Eerdere bronnen gebruikt een vastgelegde `Credential` naam voor het afhandelen van deze eigenschap.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-119">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="dc1d9-120">WMF 5.0 toegevoegd automatisch `PsDscRunAsCredential` eigenschap voor alle resources.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-120">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="dc1d9-121">Voor informatie over het gebruik van `PsDscRunAsCredential`, Zie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="dc1d9-121">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="dc1d9-122">Nieuwere resources en aangepaste resources kunnen u deze automatische eigenschap gebruiken in plaats van hun eigen eigenschap voor referenties maken.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-122">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="dc1d9-123">Het ontwerp van sommige resources zijn meerdere referenties gebruiken om een bepaalde reden en hebben hun eigen referentie-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-123">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="dc1d9-124">De beschikbare referentie vinden gebruiken eigenschappen van een resource `Get-DscResource -Name ResourceName -Syntax` of de Intellisense in de ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="dc1d9-124">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="dc1d9-125">In dit voorbeeld wordt een [groep](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resource uit de `PSDesiredStateConfiguration` ingebouwde DSC-resource-module.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-125">This example uses a [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="dc1d9-126">Deze kan lokale groepen maken en leden toevoegen of verwijderen.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-126">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="dc1d9-127">De cmdlet accepteert zowel de `Credential` eigenschap en de automatische `PsDscRunAsCredential` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-127">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="dc1d9-128">De resource alleen gebruikt echter de `Credential` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-128">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="dc1d9-129">Voor meer informatie over de `PsDscRunAsCredential` eigenschap, Zie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="dc1d9-129">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="dc1d9-130">Voorbeeld: De bron van referentie-eigenschap</span><span class="sxs-lookup"><span data-stu-id="dc1d9-130">Example: The Group resource Credential property</span></span>

<span data-ttu-id="dc1d9-131">DSC wordt uitgevoerd onder `Local System`, zodat het al machtigingen heeft voor lokale gebruikers en groepen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-131">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="dc1d9-132">Als het lid dat wordt toegevoegd een lokaal account is, zijn er is geen referentie is nodig.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-132">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="dc1d9-133">Als de `Group` resource wordt een domeinaccount toegevoegd aan de lokale groep en vervolgens een referentie op die nodig is.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-133">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="dc1d9-134">Anonieme query's naar Active Directory zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-134">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="dc1d9-135">De `Credential` eigenschap van de `Group` resource wordt het domeinaccount dat wordt gebruikt om te zoeken in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-135">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="dc1d9-136">Voor de meeste doeleinden mogelijk een algemene gebruikersaccount standaard gebruikers kunnen *lezen* de meeste van de objecten in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-136">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="dc1d9-137">Voorbeeldconfiguratie</span><span class="sxs-lookup"><span data-stu-id="dc1d9-137">Example Configuration</span></span>

<span data-ttu-id="dc1d9-138">De volgende voorbeeldcode maakt gebruik van DSC voor het vullen van een lokale groep met een domeingebruiker:</span><span class="sxs-lookup"><span data-stu-id="dc1d9-138">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="dc1d9-139">Deze code genereert een fout en de waarschuwing weergegeven:</span><span class="sxs-lookup"><span data-stu-id="dc1d9-139">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="dc1d9-140">In dit voorbeeld heeft twee problemen:</span><span class="sxs-lookup"><span data-stu-id="dc1d9-140">This example has two issues:</span></span>
1. <span data-ttu-id="dc1d9-141">Een fout wordt uitgelegd ongecodeerde wachtwoorden worden niet aanbevolen</span><span class="sxs-lookup"><span data-stu-id="dc1d9-141">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="dc1d9-142">Een waarschuwing adviseert tegen het gebruik van een domeinreferentie</span><span class="sxs-lookup"><span data-stu-id="dc1d9-142">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="dc1d9-143">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="dc1d9-143">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="dc1d9-144">Het eerste foutbericht heeft een URL met documentatie.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="dc1d9-145">Deze koppeling wordt uitgelegd hoe u voor het versleutelen van wachtwoorden met een [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) structuur en een certificaat.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-145">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="dc1d9-146">Voor meer informatie over certificaten en DSC [lezen van dit bericht](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="dc1d9-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="dc1d9-147">Als u een wachtwoord als tekst zonder opmaak, de bron is vereist de `PsDscAllowPlainTextPassword` -sleutelwoord in de configuratiegegevens sectie als volgt:</span><span class="sxs-lookup"><span data-stu-id="dc1d9-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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
> <span data-ttu-id="dc1d9-148">`NodeName`kan niet gelijk zijn aan sterretje, de naam van een specifiek knooppunt is verplicht.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-148">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="dc1d9-149">**Microsoft adviseert om te voorkomen dat ongecodeerde wachtwoorden vanwege de aanzienlijke beveiligingsrisico met zich mee.**</span><span class="sxs-lookup"><span data-stu-id="dc1d9-149">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

<span data-ttu-id="dc1d9-150">Een uitzondering hierop is wanneer u de service Azure Automation DSC lezen omdat de gegevens wordt altijd versleuteld (in doorvoer in rust in de service en in rust in het knooppunt) opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-150">An exception would be when using the Azure Automation DSC service, only because the data is always stored encrypted (in transit, at rest in the service, and at rest on the node).</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="dc1d9-151">Domeinreferenties</span><span class="sxs-lookup"><span data-stu-id="dc1d9-151">Domain Credentials</span></span>

<span data-ttu-id="dc1d9-152">De voorbeeld-configuratiescript opnieuw uitgevoerd (met of zonder versleuteling), nog steeds de waarschuwing die gebruik van een domein-account voor een referentie wordt niet aanbevolen genereert.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-152">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="dc1d9-153">Met een lokale account elimineert mogelijke blootstelling van domeinreferenties die kan worden gebruikt op andere servers.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-153">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="dc1d9-154">**Als u referenties met DSC-resources, liever dan een lokale account via een domeinaccount, indien mogelijk.**</span><span class="sxs-lookup"><span data-stu-id="dc1d9-154">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="dc1d9-155">Als er een '\' of ' @' in de `Username` eigenschap van de referentie en vervolgens de DSC zal worden beschouwd als een domeinaccount.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-155">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="dc1d9-156">Er is een uitzondering voor "localhost", "127.0.0.1" en ":: 1" in het domeingedeelte van de gebruikersnaam.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-156">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="dc1d9-157">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="dc1d9-157">PSDscAllowDomainUser</span></span>

<span data-ttu-id="dc1d9-158">In de DSC `Group` resource voorbeeld hierboven opvragen van een Active Directory-domein *vereist* een domeinaccount.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-158">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="dc1d9-159">In dit geval toevoegen de `PSDscAllowDomainUser` eigenschap in op de `ConfigurationData` blokkeren als volgt:</span><span class="sxs-lookup"><span data-stu-id="dc1d9-159">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="dc1d9-160">Het configuratiescript wordt nu het MOF-bestand zonder fouten of waarschuwingen gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="dc1d9-160">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
