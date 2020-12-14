---
description: WSMan
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan Provider
ms.openlocfilehash: 32baaaec3589fc9d6f4c2319f47d56bca777f738
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706007"
---
# <a name="wsman-provider"></a><span data-ttu-id="bf0cd-103">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="bf0cd-103">WSMan Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="bf0cd-104">Provider naam</span><span class="sxs-lookup"><span data-stu-id="bf0cd-104">Provider name</span></span>

<span data-ttu-id="bf0cd-105">WSMan</span><span class="sxs-lookup"><span data-stu-id="bf0cd-105">WSMan</span></span>

## <a name="drives"></a><span data-ttu-id="bf0cd-106">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="bf0cd-106">Drives</span></span>

`WSMan:`

## <a name="short-description"></a><span data-ttu-id="bf0cd-107">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="bf0cd-107">Short description</span></span>

<span data-ttu-id="bf0cd-108">Biedt toegang tot de configuratie gegevens van webservices voor beheer (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="bf0cd-108">Provides access to Web Services for Management (WS-Management) configuration information.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="bf0cd-109">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="bf0cd-109">Detailed description</span></span>

<span data-ttu-id="bf0cd-110">Met de **WSMan** -provider voor Power shell kunt u WS-Management configuratie gegevens op lokale of externe computers toevoegen, wijzigen, wissen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-110">The **WSMan** provider for PowerShell lets you add, change, clear, and delete WS-Management configuration data on local or remote computers.</span></span>

<span data-ttu-id="bf0cd-111">De **WSMan** -provider geeft een Power Shell-station met een mapstructuur die overeenkomt met een logische groepering van WS-Management configuratie-instellingen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-111">The **WSMan** provider exposes a PowerShell drive with a directory structure that corresponds to a logical grouping of WS-Management configuration settings.</span></span> <span data-ttu-id="bf0cd-112">Deze groeperingen worden containers genoemd.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-112">These groupings are known as containers.</span></span>

<span data-ttu-id="bf0cd-113">Vanaf Windows Power Shell 3,0 is de **WSMan** -provider bijgewerkt ter ondersteuning van nieuwe eigenschappen voor sessie configuraties, zoals **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-113">Beginning in Windows PowerShell 3.0, the **WSMan** provider has been updated to support new properties for session configurations, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="bf0cd-114">De sessie configuraties worden weer gegeven als items in de map voor de invoeg toepassing van het `WSMan:` station en de eigenschappen worden weer gegeven als items in elke sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-114">The session configurations appear as items in the Plugin directory of the `WSMan:` drive and the properties appear as items in each session configuration.</span></span>

<span data-ttu-id="bf0cd-115">De **WSMan** -provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-115">The **WSMan** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="bf0cd-116">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="bf0cd-116">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="bf0cd-117">Set-Location</span><span class="sxs-lookup"><span data-stu-id="bf0cd-117">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="bf0cd-118">Get-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-118">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="bf0cd-119">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-119">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="bf0cd-120">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-120">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="bf0cd-121">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-121">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> <span data-ttu-id="bf0cd-122">U kunt opdrachten in het `WSMan:` station gebruiken om de waarden van de nieuwe eigenschappen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-122">You can use commands in the `WSMan:` drive to change the values of the new properties.</span></span> <span data-ttu-id="bf0cd-123">U kunt het `WSMan:` station in Power shell 2,0 echter niet gebruiken voor het wijzigen van eigenschappen die zijn geïntroduceerd in Windows Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-123">However, you cannot use the `WSMan:` drive in PowerShell 2.0 to change properties that are introduced in Windows PowerShell 3.0.</span></span>
> <span data-ttu-id="bf0cd-124">Hoewel er geen fout wordt gegenereerd, zijn de opdrachten niet effectief om deze instellingen te wijzigen. gebruik het **WSMan** -station in Windows power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-124">Although no error is generated, the commands are not effective To change these settings, use the **WSMan** drive in Windows PowerShell 3.0.</span></span>

### <a name="organization-of-the-wsman-drive"></a><span data-ttu-id="bf0cd-125">Organisatie van het WSMan: station</span><span class="sxs-lookup"><span data-stu-id="bf0cd-125">Organization of the WSMan: Drive</span></span>

- <span data-ttu-id="bf0cd-126">**Client**: u kunt verschillende aspecten van de WS-Management-client configureren.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-126">**Client**: You can configure various aspects of the WS-Management client.</span></span> <span data-ttu-id="bf0cd-127">De configuratie-informatie wordt opgeslagen in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-127">The configuration information is stored in the registry.</span></span>

- <span data-ttu-id="bf0cd-128">**Service**: u kunt verschillende aspecten van de WS-Management-service configureren.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-128">**Service**: You can configure various aspects of the WS-Management service.</span></span>
  <span data-ttu-id="bf0cd-129">De configuratie-informatie wordt opgeslagen in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-129">The configuration information is stored in the registry.</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-130">Service configuratie wordt soms ook wel server configuratie genoemd.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-130">Service configuration is sometimes referred to as Server configuration.</span></span>

- <span data-ttu-id="bf0cd-131">**Shell**: u kunt verschillende aspecten van de WS-Management shell configureren, zoals de instelling voor het toestaan van externe shell toegang (**AllowRemoteShellAccess**) en het maximum aantal gelijktijdige gebruikers toegestaan (**MaxConcurrentUsers**).</span><span class="sxs-lookup"><span data-stu-id="bf0cd-131">**Shell**: You can configure various aspects of the WS-Management shell, such as the setting to allow remote shell access (**AllowRemoteShellAccess**) and the maximum number of concurrent users allowed (**MaxConcurrentUsers**).</span></span>

- <span data-ttu-id="bf0cd-132">**Listener**: u kunt een listener maken en configureren.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-132">**Listener**: You can create and configure a listener.</span></span> <span data-ttu-id="bf0cd-133">Een listener is een beheer service waarmee het WS-Management-protocol wordt geïmplementeerd om berichten te verzenden en te ontvangen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-133">A listener is a management service that implements the WS-Management protocol to send and to receive messages.</span></span>

- <span data-ttu-id="bf0cd-134">**Invoeg toepassing**: invoeg toepassingen worden geladen en gebruikt door de WS-Management-service om verschillende functies te bieden.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-134">**Plugin**: Plug-ins are loaded and used by the WS-Management service to provide various functions.</span></span> <span data-ttu-id="bf0cd-135">Power shell biedt standaard drie invoeg toepassingen:</span><span class="sxs-lookup"><span data-stu-id="bf0cd-135">By default, PowerShell provides three plug-ins:</span></span>
  - <span data-ttu-id="bf0cd-136">De invoeg toepassing voor het door sturen van gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-136">The Event Forwarding plug-in.</span></span>
  - <span data-ttu-id="bf0cd-137">De invoeg toepassing micro soft. Power shell.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-137">The Microsoft.PowerShell plug-in.</span></span>
  - <span data-ttu-id="bf0cd-138">De invoeg toepassing van de Windows Management Instrumentation provider (WMI).</span><span class="sxs-lookup"><span data-stu-id="bf0cd-138">The Windows Management Instrumentation (WMI) Provider plug-in.</span></span>
  <span data-ttu-id="bf0cd-139">Deze drie invoeg toepassingen ondersteunen gebeurtenis door sturen, configureren en WMI-toegang.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-139">These three plug-ins support event forwarding, configuration, and WMI access.</span></span>

- <span data-ttu-id="bf0cd-140">**ClientCertificate**: u kunt een client certificaat maken en configureren.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-140">**ClientCertificate**: You can create and configure a client certificate.</span></span>
  <span data-ttu-id="bf0cd-141">Er wordt een client certificaat gebruikt wanneer de WS-Management-client is geconfigureerd voor het gebruik van verificatie via een certificaat.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-141">A client certificate is used when the WS-Management client is configured to use certificate authentication.</span></span>

### <a name="directory-hierarchy-of-the-wsman-provider"></a><span data-ttu-id="bf0cd-142">Directory-hiërarchie van de WSMan-provider</span><span class="sxs-lookup"><span data-stu-id="bf0cd-142">Directory Hierarchy of the WSMan Provider</span></span>

<span data-ttu-id="bf0cd-143">De Directory-hiërarchie van de WSMan-provider voor de lokale computer is als volgt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-143">The directory hierarchy of the WSMan provider for the local computer is as follows.</span></span>

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

<span data-ttu-id="bf0cd-144">De Directory-hiërarchie van de WSMan-provider voor een externe computer is hetzelfde als een lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-144">The directory hierarchy of the WSMan provider for a remote computer is the same as a local computer.</span></span> <span data-ttu-id="bf0cd-145">Om toegang te krijgen tot de configuratie-instellingen van een externe computer, moet u echter verbinding maken met de externe computer via [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span><span class="sxs-lookup"><span data-stu-id="bf0cd-145">However, in order to access the configuration settings of a remote computer, you need to make a connection to the remote computer using [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).</span></span> <span data-ttu-id="bf0cd-146">Zodra een verbinding met een externe computer tot stand is gebracht, wordt de naam van de externe computer weer gegeven in de provider.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-146">Once a connection is made to a remote computer, the name of the remote computer shows up in the provider.</span></span>

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a><span data-ttu-id="bf0cd-147">Navigeren door het WSMan: station</span><span class="sxs-lookup"><span data-stu-id="bf0cd-147">Navigating the WSMan: Drive</span></span>

<span data-ttu-id="bf0cd-148">Met deze opdracht wordt de `Set-Location` cmdlet gebruikt om de huidige locatie te wijzigen in het `WSMan:` station.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-148">This command uses the `Set-Location` cmdlet to change the current location to the `WSMan:` drive.</span></span>

```powershell
Set-Location WSMan:
```

<span data-ttu-id="bf0cd-149">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-149">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="bf0cd-150">Typ bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-150">For example, type.</span></span>

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a><span data-ttu-id="bf0cd-151">Navigeren naar een externe systeem archief locatie</span><span class="sxs-lookup"><span data-stu-id="bf0cd-151">Navigating to a remote system store location</span></span>

<span data-ttu-id="bf0cd-152">Met deze opdracht wordt de `Set-Location` opdracht voor het wijzigen van de huidige locatie naar de hoofd locatie in de externe systeem opslag locatie.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-152">This command uses the `Set-Location` command to change the current location to the root location in the remote system store location.</span></span> <span data-ttu-id="bf0cd-153">Gebruik een back slash `\` of slash `/` om een niveau van het station aan te geven `WSMan:` .</span><span class="sxs-lookup"><span data-stu-id="bf0cd-153">Use a backslash `\` or forward slash `/` to indicate a level of the `WSMan:` drive.</span></span>

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="bf0cd-154">De bovenstaande opdracht gaat ervan uit dat er al een verbinding met het externe systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-154">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="displaying-the-contents-of-the-wsman-drive"></a><span data-ttu-id="bf0cd-155">De inhoud van het WSMan: station weer geven</span><span class="sxs-lookup"><span data-stu-id="bf0cd-155">Displaying the Contents of the WSMan: Drive</span></span>

<span data-ttu-id="bf0cd-156">Met deze opdracht wordt de `Get-Childitem` cmdlet gebruikt voor het weer geven van de WS-Management-archieven in de locatie van de localhost-opslag.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-156">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the Localhost store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\Localhost
```

<span data-ttu-id="bf0cd-157">Als u zich in het station bevindt `WSMan:` , kunt u de naam van het station weglaten.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-157">If you are in the `WSMan:` drive, you can omit the drive name.</span></span>

<span data-ttu-id="bf0cd-158">Met deze opdracht wordt de `Get-Childitem` cmdlet gebruikt om de WS-Management-archieven in de archief locatie ' SERVER01 ' van de externe computer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-158">This command uses the `Get-Childitem` cmdlet to display the WS-Management stores in the remote computer "SERVER01" store location.</span></span>

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> <span data-ttu-id="bf0cd-159">De bovenstaande opdracht gaat ervan uit dat er al een verbinding met het externe systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-159">The above command assume that a connection to the remote system already exists.</span></span>

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a><span data-ttu-id="bf0cd-160">De waarde van items instellen in WSMAN: station</span><span class="sxs-lookup"><span data-stu-id="bf0cd-160">Setting the value of items in the  WSMAN: drive</span></span>

<span data-ttu-id="bf0cd-161">U kunt de `Set-Item` cmdlet gebruiken om de configuratie-instellingen in het station te wijzigen `WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="bf0cd-161">You can use the `Set-Item` cmdlet to change configuration settings in the `WSMAN` drive.</span></span> <span data-ttu-id="bf0cd-162">In het volgende voor beeld wordt de **TrustedHosts** -waarde ingesteld om alle hosts met het achtervoegsel ' contoso.com ' te accepteren.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-162">The following example sets the **TrustedHosts** value to accept all hosts with the suffix "contoso.com".</span></span>

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

<span data-ttu-id="bf0cd-163">De `Set-Item` cmdlet biedt ondersteuning voor een extra para meter `-Concatenate` waarmee een waarde wordt toegevoegd in plaats van deze te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-163">The `Set-Item` cmdlet supports an additional parameter `-Concatenate` that appends a value instead of changing it.</span></span> <span data-ttu-id="bf0cd-164">In het volgende voor beeld wordt een nieuwe waarde ' \*. domain2.com ' toegevoegd aan de oude waarde die is opgeslagen in `TrustedHost:`</span><span class="sxs-lookup"><span data-stu-id="bf0cd-164">The following example will append a new value "\*.domain2.com" to the old value stored in `TrustedHost:`</span></span>

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a><span data-ttu-id="bf0cd-165">Items maken in het WSMAN: station</span><span class="sxs-lookup"><span data-stu-id="bf0cd-165">Creating items in the WSMAN: drive</span></span>

### <a name="creating-a-new-listener"></a><span data-ttu-id="bf0cd-166">Een nieuwe listener maken</span><span class="sxs-lookup"><span data-stu-id="bf0cd-166">Creating a new listener</span></span>

<span data-ttu-id="bf0cd-167">Met de `New-Item` cmdlet worden items in een provider station gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-167">The `New-Item` cmdlet creates items within a provider drive.</span></span> <span data-ttu-id="bf0cd-168">Elke provider heeft verschillende item typen die u kunt maken.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-168">Each provider has different item types that you can create.</span></span> <span data-ttu-id="bf0cd-169">In het `WSMAN:` station kunt u *listeners* maken die u configureert om externe aanvragen te ontvangen en erop te reageren.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-169">In the `WSMAN:` drive, you can create *Listeners* which you configure to receive and respond to remote requests.</span></span> <span data-ttu-id="bf0cd-170">Met de volgende opdracht maakt u een nieuwe HTTP-listener met behulp van de- `New-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-170">The following command creates a new HTTP listener using the `New-Item` cmdlet.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a><span data-ttu-id="bf0cd-171">Een nieuwe invoeg toepassing maken</span><span class="sxs-lookup"><span data-stu-id="bf0cd-171">Creating a new plug-in</span></span>

<span data-ttu-id="bf0cd-172">Met deze opdracht wordt een invoeg toepassing voor de WS-Management-service gemaakt (geregistreerd).</span><span class="sxs-lookup"><span data-stu-id="bf0cd-172">This command creates (registers) a plug-in for the WS-Management service.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a><span data-ttu-id="bf0cd-173">Nieuwe resource-invoer maken</span><span class="sxs-lookup"><span data-stu-id="bf0cd-173">Creating a new resource entry</span></span>

<span data-ttu-id="bf0cd-174">Met deze opdracht maakt u een bron vermelding in de map resources van een TestPlugin.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-174">This command creates a resource entry in the Resources directory of a TestPlugin.</span></span> <span data-ttu-id="bf0cd-175">Bij deze opdracht wordt ervan uitgegaan dat er een TestPlugin is gemaakt met behulp van een afzonderlijke opdracht.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-175">This command assumes that a TestPlugin has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a><span data-ttu-id="bf0cd-176">Een nieuwe beveiligings vermelding voor een resource maken</span><span class="sxs-lookup"><span data-stu-id="bf0cd-176">Creating a new security entry for a resource</span></span>

<span data-ttu-id="bf0cd-177">Met deze opdracht maakt u een beveiligings vermelding in de map Security van Resource_5967683 (een specifieke resource).</span><span class="sxs-lookup"><span data-stu-id="bf0cd-177">This command creates a security entry in the Security directory of Resource_5967683 (a specific resource).</span></span> <span data-ttu-id="bf0cd-178">Bij deze opdracht wordt ervan uitgegaan dat de bron vermelding is gemaakt met een afzonderlijke opdracht.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-178">This command assumes that the resource entry has been created using a separate command.</span></span>

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a><span data-ttu-id="bf0cd-179">Een nieuw client certificaat maken</span><span class="sxs-lookup"><span data-stu-id="bf0cd-179">Creating a new Client Certificate</span></span>

<span data-ttu-id="bf0cd-180">Met deze opdracht maakt u een item voor **ClientCertificate** dat kan worden gebruikt door de WS-Management-client.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-180">This command creates **ClientCertificate** entry that can be used by the WS-Management client.</span></span> <span data-ttu-id="bf0cd-181">De nieuwe **ClientCertificate** wordt weer gegeven in de map **ClientCertificate** als "ClientCertificate_1234567890".</span><span class="sxs-lookup"><span data-stu-id="bf0cd-181">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="bf0cd-182">Alle para meters zijn verplicht.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-182">All of the parameters are mandatory.</span></span> <span data-ttu-id="bf0cd-183">De **Uitgever** moet een vinger afdruk van het certificaat van de certificerings instantie zijn.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-183">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a><span data-ttu-id="bf0cd-184">Een nieuwe initialisatie parameter maken</span><span class="sxs-lookup"><span data-stu-id="bf0cd-184">Creating a new Initialization Parameter</span></span>

<span data-ttu-id="bf0cd-185">Met deze opdracht maakt u een initialisatie parameter met de naam ' testparametername ' in de map ' InitializationParameters '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-185">This command creates an Initialization parameter named "testparametername" in the "InitializationParameters" directory.</span></span> <span data-ttu-id="bf0cd-186">Bij deze opdracht wordt ervan uitgegaan dat de ' TestPlugin ' is gemaakt met behulp van een afzonderlijke opdracht.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-186">This command assumes that the "TestPlugin" has been created using a separate command.</span></span>

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a><span data-ttu-id="bf0cd-187">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="bf0cd-187">Dynamic parameters</span></span>

<span data-ttu-id="bf0cd-188">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-188">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="address-string"></a><span data-ttu-id="bf0cd-189">Help \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-189">Address \<String\></span></span>

<span data-ttu-id="bf0cd-190">Hiermee geeft u het adres op waarvoor deze listener is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-190">Specifies the address for which this listener was created.</span></span> <span data-ttu-id="bf0cd-191">De waarde kan één van de volgende zijn:</span><span class="sxs-lookup"><span data-stu-id="bf0cd-191">The value can be one of the following:</span></span>

- <span data-ttu-id="bf0cd-192">De letterlijke teken reeks "\*".</span><span class="sxs-lookup"><span data-stu-id="bf0cd-192">The literal string "\*".</span></span> <span data-ttu-id="bf0cd-193">(Met het Joker teken ( `*` ) wordt de opdracht alle IP-adressen op alle netwerk adapters gebonden.)</span><span class="sxs-lookup"><span data-stu-id="bf0cd-193">(The wildcard character (`*`) makes the command bind all the IP addresses on all the network adapters.)</span></span>
- <span data-ttu-id="bf0cd-194">De letterlijke teken reeks ' IP: ' gevolgd door een geldig IP-adres in IPv4-decimale notatie of in een IPv6-gekloonde hexadecimale indeling.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-194">The literal string "IP:" followed by a valid IP address in either IPv4 dotted-decimal format or in IPv6 cloned-hexadecimal format.</span></span>
- <span data-ttu-id="bf0cd-195">De letterlijke teken reeks ' MAC: ' gevolgd door het MAC-adres van een adapter.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-195">The literal string "MAC:" followed by the MAC address of an adapter.</span></span>
  <span data-ttu-id="bf0cd-196">Bijvoorbeeld: MAC: 32-a3-58 -90-CC.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-196">For example: MAC:32-a3-58-90-be-cc.</span></span>

> [!NOTE]
> <span data-ttu-id="bf0cd-197">De adres waarde wordt ingesteld bij het maken van een listener.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-197">The Address value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-198">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-198">Cmdlets supported</span></span>

- [<span data-ttu-id="bf0cd-199">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-199">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a><span data-ttu-id="bf0cd-200">Voorzieningen \<Enumeration\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-200">Capability \<Enumeration\></span></span>

<span data-ttu-id="bf0cd-201">Bij het werken met *invoeg toepassingen* geeft deze para meter een bewerking aan die wordt ondersteund voor deze URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="bf0cd-201">When working with *Plug-ins* this parameter specifies an operation that is supported on this Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="bf0cd-202">U moet één vermelding maken voor elk type bewerking dat door de URI wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-202">You have to create one entry for each type of operation that the URI supports.</span></span> <span data-ttu-id="bf0cd-203">U kunt geldige kenmerken voor een bepaalde bewerking opgeven als de bewerking deze ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-203">You can specify any valid attributes for a given operation, if the operation supports it.</span></span>

<span data-ttu-id="bf0cd-204">Deze kenmerken zijn onder andere **SupportsFiltering** en **SupportsFragment**.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-204">These attributes include **SupportsFiltering** and **SupportsFragment**.</span></span>

- <span data-ttu-id="bf0cd-205">**Maken**: Create-bewerkingen worden ondersteund op de URI.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-205">**Create**: Create operations are supported on the URI.</span></span>
  - <span data-ttu-id="bf0cd-206">Het kenmerk **SupportFragment**  wordt gebruikt als de bewerking Create het concept ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-206">The **SupportFragment**  attribute is used if the Create operation supports the concept.</span></span>
  - <span data-ttu-id="bf0cd-207">Het kenmerk **SupportFiltering** is niet geldig voor Create-bewerkingen en moet worden ingesteld op ' false '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-207">The **SupportFiltering** attribute is NOT valid for Create operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-208">Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-208">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="bf0cd-209">**Verwijderen**: Verwijder bewerkingen worden ondersteund op de URI.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-209">**Delete**: Delete operations are supported on the URI.</span></span>
  - <span data-ttu-id="bf0cd-210">Het kenmerk **SupportFragment** wordt gebruikt als de bewerking delete het concept ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-210">The **SupportFragment** attribute is used if the Delete operation supports the concept.</span></span>
  - <span data-ttu-id="bf0cd-211">Het kenmerk **SupportFiltering** is niet geldig voor Delete-bewerkingen en moet worden ingesteld op ' false '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-211">The **SupportFiltering** attribute is NOT valid for Delete operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-212">Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-212">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="bf0cd-213">**Opsommen**: opsommings bewerkingen worden ondersteund op de URI.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-213">**Enumerate**: Enumerate operations are supported on the URI.</span></span>
  - <span data-ttu-id="bf0cd-214">Het kenmerk **SupportFragment** wordt niet ondersteund voor opsommings bewerkingen en moet worden ingesteld op false.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-214">The **SupportFragment** attribute is NOT supported for Enumerate operations and should be set to False.</span></span>
  - <span data-ttu-id="bf0cd-215">Het kenmerk **SupportFiltering** is geldig en als de invoeg toepassing filteren ondersteunt, moet dit kenmerk worden ingesteld op ' True '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-215">The **SupportFiltering** attribute is valid, and if the plug-in supports filtering, this attribute should be set to "True".</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-216">Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-216">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="bf0cd-217">**Get**: Get-bewerkingen worden ondersteund op de URI.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-217">**Get**: Get operations are supported on the URI.</span></span>
  - <span data-ttu-id="bf0cd-218">Het kenmerk **SupportFragment** wordt gebruikt als de Get-bewerking het concept ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-218">The **SupportFragment** attribute is used if the Get operation supports the concept.</span></span>
  - <span data-ttu-id="bf0cd-219">Het kenmerk **SupportFiltering** is niet geldig voor Get-bewerkingen en moet worden ingesteld op false.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-219">The **SupportFiltering** attribute is NOT valid for Get operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-220">Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-220">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="bf0cd-221">**Invoke**: bewerkingen aanroepen worden ondersteund op de URI.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-221">**Invoke**: Invoke operations are supported on the URI.</span></span>
  - <span data-ttu-id="bf0cd-222">Het kenmerk **SupportFragment** wordt niet ondersteund voor invoke-bewerkingen en moet worden ingesteld op false.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-222">The **SupportFragment** attribute is not supported for Invoke operations and should be set to False.</span></span>
  - <span data-ttu-id="bf0cd-223">Het kenmerk **SupportFiltering** is ongeldig en moet worden ingesteld op ' false '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-223">The **SupportFiltering** attribute is not valid and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-224">Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-224">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="bf0cd-225">**Put**: put-bewerkingen worden ondersteund op de URI.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-225">**Put**: Put operations are supported on the URI.</span></span>
  - <span data-ttu-id="bf0cd-226">Het kenmerk **SupportFragment** wordt gebruikt als de put-bewerking het concept ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-226">The **SupportFragment** attribute is used if the Put operation supports the concept.</span></span>
  - <span data-ttu-id="bf0cd-227">Het kenmerk **SupportFiltering** is niet geldig voor put-bewerkingen en moet worden ingesteld op ' false '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-227">The **SupportFiltering** attribute is not valid for Put operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-228">Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-228">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="bf0cd-229">**Abonneren**: Abonneer bewerkingen worden ondersteund op de URI.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-229">**Subscribe**: Subscribe operations are supported on the URI.</span></span>
  - <span data-ttu-id="bf0cd-230">Het kenmerk **SupportFragment** wordt niet ondersteund voor Abonneer bewerkingen en moet worden ingesteld op false.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-230">The **SupportFragment** attribute is not supported for Subscribe operations and should be set to False.</span></span>
  - <span data-ttu-id="bf0cd-231">Het kenmerk **SupportFiltering** is niet geldig voor abonnements bewerkingen en moet worden ingesteld op ' false '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-231">The **SupportFiltering** attribute is not valid for Subscribe operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-232">Deze bewerking is niet geldig voor een URI als shell bewerkingen ook worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-232">This operation is not valid for a URI if Shell operations are also supported.</span></span>
- <span data-ttu-id="bf0cd-233">**Shell**: shell-bewerkingen worden ondersteund op de URI.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-233">**Shell**: Shell operations are supported on the URI.</span></span>
  - <span data-ttu-id="bf0cd-234">Het kenmerk **SupportFragment** wordt niet ondersteund voor shell-bewerkingen en moet worden ingesteld op ' false '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-234">The **SupportFragment** attribute is not supported for Shell operations and should be set to "False".</span></span>
  - <span data-ttu-id="bf0cd-235">Het kenmerk **SupportFiltering** is niet geldig voor shell-bewerkingen en moet worden ingesteld op ' false '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-235">The **SupportFiltering** attribute is not valid for Shell operations and should be set to "False".</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-236">Deze bewerking is niet geldig voor een URI als een andere bewerking ook wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-236">This operation is not valid for a URI if ANY other operation is also supported.</span></span>
  > [!NOTE]
  > <span data-ttu-id="bf0cd-237">Als een shell-bewerking is geconfigureerd voor een URI, worden Get-, put-, Create-, Delete-, Invoke-en Enumeratable-bewerkingen intern verwerkt in de WS-Management-service (WinRM) voor het beheren van shells.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-237">If a Shell operation is configured for a URI, Get, Put, Create, Delete, Invoke, and Enumerate operations are processed internally within the WS-Management (WinRM) service to manage shells.</span></span> <span data-ttu-id="bf0cd-238">Als gevolg hiervan kan de invoeg toepassing de bewerkingen niet afhandelen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-238">As a result, the plug-in cannot handle the operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-239">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-239">Cmdlets supported</span></span>

- [<span data-ttu-id="bf0cd-240">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-240">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a><span data-ttu-id="bf0cd-241">CertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-241">CertificateThumbprint \<String\></span></span>

<span data-ttu-id="bf0cd-242">Hiermee geeft u de vinger afdruk van het service certificaat.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-242">Specifies the thumbprint of the service certificate.</span></span>

<span data-ttu-id="bf0cd-243">Deze waarde vertegenwoordigt de reeks hexadecimale waarden van twee cijfers in het veld vinger afdruk van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-243">This value represents the string of two-digit hexadecimal values in the Thumbprint field of the certificate.</span></span> <span data-ttu-id="bf0cd-244">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-244">It specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="bf0cd-245">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-245">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="bf0cd-246">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts en ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-246">They can be mapped only to local user accounts, and they do not work with domain accounts.</span></span> <span data-ttu-id="bf0cd-247">Gebruik de `Get-Item` `Get-ChildItem` cmdlets in het Power Shell-station om een certificaat vingerafdruk te verkrijgen `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="bf0cd-247">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` cmdlets in the PowerShell `Cert:` drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-248">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-248">Cmdlets supported</span></span>

- [<span data-ttu-id="bf0cd-249">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-249">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a><span data-ttu-id="bf0cd-250">Ingeschakeld \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-250">Enabled \<Boolean\></span></span>

<span data-ttu-id="bf0cd-251">Hiermee geeft u op of de listener is in-of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-251">Specifies whether the listener is enabled or disabled.</span></span> <span data-ttu-id="bf0cd-252">De standaard waarde is True.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-252">The default is True.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-253">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-253">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-254">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-254">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a><span data-ttu-id="bf0cd-255">Bestands naam (invoeg toepassing) \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-255">FileName (Plugin) \<String\></span></span>

<span data-ttu-id="bf0cd-256">Hiermee geeft u de bestands naam van de invoeg toepassing voor bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-256">Specifies the file name of the operations plug-in.</span></span> <span data-ttu-id="bf0cd-257">Alle omgevings variabelen die in dit item worden geplaatst, worden uitgevouwen in de context van de gebruiker wanneer een aanvraag wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-257">Any environment variables that are put in this entry will be expanded in the users' context when a request is received.</span></span> <span data-ttu-id="bf0cd-258">Omdat elke gebruiker een andere versie van dezelfde omgevings variabele kan hebben, kan elke gebruiker een andere invoeg toepassing hebben.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-258">Because each user could have a different version of the same environment variable, each user could have a different plug-in.</span></span> <span data-ttu-id="bf0cd-259">Deze vermelding mag niet leeg zijn en moet verwijzen naar een geldige invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-259">This entry cannot be blank and must point to a valid plug-in.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-260">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-260">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-261">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-261">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a><span data-ttu-id="bf0cd-262">Hostnaam \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-262">HostName \<String\></span></span>

<span data-ttu-id="bf0cd-263">Hiermee geeft u de hostnaam op van de computer waarop de WS-Management-service (WinRM) wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-263">Specifies the host name of the computer on which the WS-Management (WinRM) service is running.</span></span>

<span data-ttu-id="bf0cd-264">De waarde moet een Fully Qualified Domain Name, een letterlijke IPv4-of een IPv6-teken reeks of een Joker teken zijn.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-264">The value must be a fully qualified domain name, an IPv4 or IPv6 literal string, or a wildcard character.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-265">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-265">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-266">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-266">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a><span data-ttu-id="bf0cd-267">Verlener \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-267">Issuer \<String\></span></span>

<span data-ttu-id="bf0cd-268">Hiermee geeft u de naam van de certificerings instantie die het certificaat heeft uitgegeven.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-268">Specifies the name of the certification authority that issued the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-269">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-269">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-270">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-270">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a><span data-ttu-id="bf0cd-271">Invoeg toepassing \<\> WS-Management-invoeg toepassingen zijn systeem eigen Dynamic Link Libraries (dll's)</span><span class="sxs-lookup"><span data-stu-id="bf0cd-271">Plugin \<\> WS-Management plug-ins are native dynamic link libraries (DLLs)</span></span>

<span data-ttu-id="bf0cd-272">waarmee u de functionaliteit van WS-Management insluit en uitbreidt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-272">that plug in to and extend the functionality of WS-Management .</span></span> <span data-ttu-id="bf0cd-273">De WSW-Management-invoeg toepassing biedt functionaliteit waarmee een gebruiker invoeg toepassingen kan schrijven door bepaalde Api's te implementeren voor ondersteunde bron-Uri's en bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-273">The WSW-Management Plug-in API provides functionality that enables a user to write plug-ins by implementing certain APIs for supported resource URIs and operations.</span></span> <span data-ttu-id="bf0cd-274">Nadat de invoeg toepassingen zijn geconfigureerd voor de WS-Management-service (WinRM) of voor Internet Information Services (IIS), worden de invoeg toepassingen respectievelijk geladen in de WS-Management host of in de IIS-host.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-274">After the plug-ins are configured for either the WS-Management (WinRM) service or for Internet Information Services (IIS), the plug-ins are loaded in the WS-Management host or in the IIS host, respectively.</span></span> <span data-ttu-id="bf0cd-275">Externe aanvragen worden doorgestuurd naar deze invoer punten om bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-275">Remote requests are routed to these plug-in entry points to perform operations.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-276">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-276">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-277">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-277">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a><span data-ttu-id="bf0cd-278">Importeer \<Unsigned Short Integer\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-278">Port \<Unsigned Short Integer\></span></span>

<span data-ttu-id="bf0cd-279">Hiermee geeft u de TCP-poort waarvoor deze listener is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-279">Specifies the TCP port for which this listener is created.</span></span> <span data-ttu-id="bf0cd-280">U kunt een waarde van 1 tot en met 65535 opgeven.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-280">You can specify any value from 1 through 65535.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-281">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-281">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-282">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-282">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="bf0cd-283">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-283">Resource \<String\></span></span>

<span data-ttu-id="bf0cd-284">Hiermee geeft u een eind punt op dat een afzonderlijk type beheer bewerking of-waarde vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-284">Specifies an endpoint that represents a distinct type of management operation or value.</span></span> <span data-ttu-id="bf0cd-285">Een service stelt een of meer resources beschikbaar en sommige resources kunnen meer dan één exemplaar hebben.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-285">A service exposes one or more resources, and some resources can have more than one instance.</span></span> <span data-ttu-id="bf0cd-286">Een beheer bron is vergelijkbaar met een WMI-klasse of een database tabel, en een exemplaar is vergelijkbaar met een instantie van de klasse of van een rij in de tabel.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-286">A management resource is similar to a WMI class or to a database table, and an instance is similar to an instance of the class or to a row in the table.</span></span> <span data-ttu-id="bf0cd-287">De klasse **Win32_LogicalDisk** vertegenwoordigt bijvoorbeeld een resource.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-287">For example, the **Win32_LogicalDisk** class represents a resource.</span></span> <span data-ttu-id="bf0cd-288">`Win32_LogicalDisk="C:\\"` is een specifiek exemplaar van de resource.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-288">`Win32_LogicalDisk="C:\\"` is a specific instance of the resource.</span></span>

<span data-ttu-id="bf0cd-289">Een URI (Uniform Resource Identifier) bevat een voor voegsel en een pad naar een resource.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-289">A Uniform Resource Identifier (URI) contains a prefix and a path to a resource.</span></span>
<span data-ttu-id="bf0cd-290">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bf0cd-290">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-291">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-291">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-292">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-292">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a><span data-ttu-id="bf0cd-293">Resource \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-293">Resource \<String\></span></span>

<span data-ttu-id="bf0cd-294">Hiermee geeft u de URI (Uniform Resource Identifier) op die een specifiek type resource identificeert, zoals een schijf of een proces, op een computer.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-294">Specifies the Uniform Resource Identifier (URI) that identifies a specific type of resource, such as a disk or a process, on a computer.</span></span>

<span data-ttu-id="bf0cd-295">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-295">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="bf0cd-296">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bf0cd-296">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-297">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-297">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-298">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-298">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a><span data-ttu-id="bf0cd-299">SDKVersion \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-299">SDKVersion \<String\></span></span>

<span data-ttu-id="bf0cd-300">Hiermee geeft u de versie van de SDK van de WS-Management-invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-300">Specifies the version of the WS-Management plug-in SDK.</span></span> <span data-ttu-id="bf0cd-301">De enige geldige waarde is</span><span class="sxs-lookup"><span data-stu-id="bf0cd-301">The only valid value is</span></span>
1.

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-302">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-302">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-303">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-303">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a><span data-ttu-id="bf0cd-304">Onderwerp \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-304">Subject \<String\></span></span>

<span data-ttu-id="bf0cd-305">Hiermee geeft u de entiteit op die wordt geïdentificeerd door het certificaat.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-305">Specifies the entity that is identified by the certificate.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-306">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-306">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-307">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-307">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a><span data-ttu-id="bf0cd-308">Portmap \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-308">Transport \<String\></span></span>

<span data-ttu-id="bf0cd-309">Hiermee geeft u het Trans Port op dat moet worden gebruikt voor het verzenden en ontvangen van WS-Management protocol aanvragen en-antwoorden.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-309">Specifies the transport to use to send and receive WS-Management protocol requests and responses.</span></span> <span data-ttu-id="bf0cd-310">De waarde moet HTTP of HTTPS zijn.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-310">The value must be either HTTP or HTTPS.</span></span>

<span data-ttu-id="bf0cd-311">Opmerking: de transport waarde is ingesteld bij het maken van een listener.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-311">Note: The Transport value is set when creating a Listener.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-312">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-312">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-313">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-313">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a><span data-ttu-id="bf0cd-314">URI \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-314">URI \<String\></span></span>

<span data-ttu-id="bf0cd-315">Hiermee wordt de URI aangegeven waarvoor toegang is toegestaan op basis van de waarde van de SDDL-para meter.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-315">Identifies the URI for which access is authorized based on the value of the Sddl parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-316">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-316">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-317">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-317">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a><span data-ttu-id="bf0cd-318">URLPrefix \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-318">URLPrefix \<String\></span></span>

<span data-ttu-id="bf0cd-319">Een URL-voor voegsel voor het accepteren van HTTP-of HTTPS-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-319">A URL prefix on which to accept HTTP or HTTPS requests.</span></span> <span data-ttu-id="bf0cd-320">Dit is een teken reeks met alleen de tekens `[a-z]` , `[A-Z]` ,, `[9-0]` onderstrepen ( `_` ) en back slash ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="bf0cd-320">This is a string containing only the characters `[a-z]`, `[A-Z]`, `[9-0]`, underscore (`_`) and backslash (`/`).</span></span> <span data-ttu-id="bf0cd-321">De teken reeks mag niet beginnen met of eindigen op een back slash ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="bf0cd-321">The string must not start with or end with a backslash (`/`).</span></span> <span data-ttu-id="bf0cd-322">Als de computer naam bijvoorbeeld ' SampleComputer ' is, geeft de WS-Management-client `http://SampleMachine/URLPrefix` op in het doel adres.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-322">For example, if the computer name is "SampleComputer", the WS-Management client would specify `http://SampleMachine/URLPrefix` in the destination address.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-323">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-323">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-324">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-324">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a><span data-ttu-id="bf0cd-325">Value \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-325">Value \<String\></span></span>

<span data-ttu-id="bf0cd-326">Hiermee geeft u de waarde van een initialisatie parameter op, een waarde die specifiek is voor een invoeg toepassing die wordt gebruikt om configuratie opties op te geven.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-326">Specifies the value of an initialization parameter, which is a plug-in-specific value that is used to specify configuration options.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-327">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-327">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-328">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-328">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a><span data-ttu-id="bf0cd-329">XMLRenderingType \<String\></span><span class="sxs-lookup"><span data-stu-id="bf0cd-329">XMLRenderingType \<String\></span></span>

<span data-ttu-id="bf0cd-330">Hiermee geeft u de indeling op waarin XML wordt door gegeven aan invoeg toepassingen via het **WSMAN_DATA** -object.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-330">Specifies the format in which XML is passed to plug-ins through the **WSMAN_DATA** object.</span></span> <span data-ttu-id="bf0cd-331">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="bf0cd-331">The following are valid values:</span></span>

- <span data-ttu-id="bf0cd-332">Tekst: inkomende XML-gegevens bevinden zich in een **WSMAN_DATA_TYPE_TEXT** structuur, die de XML vertegenwoordigt als een **PCWSTR** -geheugen buffer.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-332">Text: Incoming XML data is contained in a **WSMAN_DATA_TYPE_TEXT** structure, which represents the XML as a **PCWSTR** memory buffer.</span></span>
- <span data-ttu-id="bf0cd-333">XMLReader: inkomende XML-gegevens bevinden zich in een **WSMAN_DATA_TYPE_WS_XML_READER** -structuur, die de XML vertegenwoordigt als een **XmlReader** -object, dat is gedefinieerd in het header-bestand ' webservices. h '.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-333">XMLReader: Incoming XML data is contained in a **WSMAN_DATA_TYPE_WS_XML_READER** structure, which represents the XML as an **XmlReader** object, which is defined in the "WebServices.h" header file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="bf0cd-334">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="bf0cd-334">Cmdlets Supported</span></span>

- [<span data-ttu-id="bf0cd-335">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="bf0cd-335">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="bf0cd-336">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="bf0cd-336">Using the pipeline</span></span>

<span data-ttu-id="bf0cd-337">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-337">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="bf0cd-338">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-338">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="bf0cd-339">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-339">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="bf0cd-340">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="bf0cd-340">Getting help</span></span>

<span data-ttu-id="bf0cd-341">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-341">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="bf0cd-342">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="bf0cd-342">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a><span data-ttu-id="bf0cd-343">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bf0cd-343">See also</span></span>

[<span data-ttu-id="bf0cd-344">about_Providers</span><span class="sxs-lookup"><span data-stu-id="bf0cd-344">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

