---
description: Certificaat
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Certificaat provider
ms.openlocfilehash: 78536024e8e953a70485a7d950b187ba9a3fc405
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705863"
---
# <a name="certificate-provider"></a><span data-ttu-id="27b43-103">Certificaat provider</span><span class="sxs-lookup"><span data-stu-id="27b43-103">Certificate Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="27b43-104">Provider naam</span><span class="sxs-lookup"><span data-stu-id="27b43-104">Provider name</span></span>

<span data-ttu-id="27b43-105">Certificaat</span><span class="sxs-lookup"><span data-stu-id="27b43-105">Certificate</span></span>

## <a name="drives"></a><span data-ttu-id="27b43-106">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="27b43-106">Drives</span></span>

`Cert:`

## <a name="capabilities"></a><span data-ttu-id="27b43-107">Functies</span><span class="sxs-lookup"><span data-stu-id="27b43-107">Capabilities</span></span>

<span data-ttu-id="27b43-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="27b43-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="27b43-109">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="27b43-109">Short description</span></span>

<span data-ttu-id="27b43-110">Biedt toegang tot X. 509-certificaat archieven en-certificaten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="27b43-110">Provides access to X.509 certificate stores and certificates in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="27b43-111">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="27b43-111">Detailed description</span></span>

<span data-ttu-id="27b43-112">Met de Power shell- **certificaat** provider kunt u certificaten en certificaat archieven ophalen, toevoegen, wijzigen, wissen en verwijderen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="27b43-112">The PowerShell **Certificate** provider lets you get, add, change, clear, and delete certificates and certificate stores in PowerShell.</span></span>

<span data-ttu-id="27b43-113">Het **certificaat** station is een hiërarchische naam ruimte met de certificaat archieven en certificaten op uw computer.</span><span class="sxs-lookup"><span data-stu-id="27b43-113">The **Certificate** drive is a hierarchical namespace containing the certificate stores and certificates on your computer.</span></span>

<span data-ttu-id="27b43-114">De **certificaat** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="27b43-114">The **Certificate** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="27b43-115">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="27b43-115">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="27b43-116">Set-Location</span><span class="sxs-lookup"><span data-stu-id="27b43-116">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="27b43-117">Get-item</span><span class="sxs-lookup"><span data-stu-id="27b43-117">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="27b43-118">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="27b43-118">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="27b43-119">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="27b43-119">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="27b43-120">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="27b43-120">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="27b43-121">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="27b43-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="27b43-122">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="27b43-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="27b43-123">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="27b43-123">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="27b43-124">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="27b43-124">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="27b43-125">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="27b43-125">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="27b43-126">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="27b43-126">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="27b43-127">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="27b43-127">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="27b43-128">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="27b43-128">Types exposed by this provider</span></span>

<span data-ttu-id="27b43-129">Het certificaat station bevat de volgende typen.</span><span class="sxs-lookup"><span data-stu-id="27b43-129">The Certificate drive exposes the following types.</span></span>

- <span data-ttu-id="27b43-130">Opslag locaties (micro soft. Power shell. commands. X509StoreLocation), die bestaan uit containers met een hoog niveau waarmee de certificaten voor de huidige gebruiker en voor alle gebruikers worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="27b43-130">Store locations (Microsoft.PowerShell.Commands.X509StoreLocation), which are high-level containers that group the certificates for the current user and for all users.</span></span> <span data-ttu-id="27b43-131">Elk systeem heeft een opslag locatie van het object CurrentUser en LocalMachine (alle gebruikers).</span><span class="sxs-lookup"><span data-stu-id="27b43-131">Each system has a CurrentUser and LocalMachine (all users) store location.</span></span>

- <span data-ttu-id="27b43-132">Certificaat archieven (System. Security. Cryptography. X509Certificates. X509Store), die fysieke winkels zijn waarin certificaten worden opgeslagen en beheerd.</span><span class="sxs-lookup"><span data-stu-id="27b43-132">Certificates stores (System.Security.Cryptography.X509Certificates.X509Store), which are physical stores in which certificates are saved and managed.</span></span>

- <span data-ttu-id="27b43-133">X. 509 **System. Security. Cryptography. X509Certificates. X509Certificate2** -certificaten, die elk een X. 509-certificaat op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="27b43-133">X.509 **System.Security.Cryptography.X509Certificates.X509Certificate2** certificates, each of which represent an X.509 certificate on the computer.</span></span>
  <span data-ttu-id="27b43-134">Certificaten worden geïdentificeerd aan de hand van hun vinger afdrukken.</span><span class="sxs-lookup"><span data-stu-id="27b43-134">Certificates are identified by their thumbprints.</span></span>

## <a name="navigating-the-certificate-drive"></a><span data-ttu-id="27b43-135">Navigeren door het certificaat station</span><span class="sxs-lookup"><span data-stu-id="27b43-135">Navigating the Certificate drive</span></span>

<span data-ttu-id="27b43-136">De **certificaat** provider geeft de naam ruimte van het certificaat weer als het `Cert:` station in Power shell.</span><span class="sxs-lookup"><span data-stu-id="27b43-136">The **Certificate** provider exposes the certificate namespace as the `Cert:` drive in PowerShell.</span></span> <span data-ttu-id="27b43-137">Met deze opdracht wordt de `Set-Location` opdracht voor het wijzigen van de huidige locatie naar het basis certificaat archief in de LocalMachine-opslag locatie.</span><span class="sxs-lookup"><span data-stu-id="27b43-137">This command uses the `Set-Location` command to change the current location to the Root certificate store in the LocalMachine store location.</span></span> <span data-ttu-id="27b43-138">Gebruik een back slash ( \\ ) of een slash (/) om een niveau van het station aan te geven `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="27b43-138">Use a backslash (\\) or a forward slash (/) to indicate a level of the `Cert:` drive.</span></span>

```powershell
Set-Location Cert:
```

<span data-ttu-id="27b43-139">U kunt ook met de certificaat provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="27b43-139">You can also work with the certificate provider from any other PowerShell drive.</span></span> <span data-ttu-id="27b43-140">Als u wilt verwijzen naar een alias vanuit een andere locatie, gebruikt u de `Cert:` naam van het station in het pad.</span><span class="sxs-lookup"><span data-stu-id="27b43-140">To reference an alias from another location, use the `Cert:` drive name in the path.</span></span>

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

<span data-ttu-id="27b43-141">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="27b43-141">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="27b43-142">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="27b43-142">For example, type:</span></span>

```powershell
Set-Location C:
```

> [!NOTE]
> <span data-ttu-id="27b43-143">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="27b43-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="27b43-144">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="27b43-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span>
> <span data-ttu-id="27b43-145">en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="27b43-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-contents-of-the-cert-drive"></a><span data-ttu-id="27b43-146">De inhoud van het certificaat wordt weer gegeven: station</span><span class="sxs-lookup"><span data-stu-id="27b43-146">Displaying the Contents of the Cert: drive</span></span>

<span data-ttu-id="27b43-147">Met deze opdracht wordt de `Get-ChildItem` cmdlet gebruikt voor het weer geven van de certificaat archieven in de locatie van het certificaat archief van het CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="27b43-147">This command uses the `Get-ChildItem` cmdlet to display the certificate stores in the CurrentUser certificate store location.</span></span>

<span data-ttu-id="27b43-148">Als u zich niet in het station bevindt `Cert:` , gebruikt u een absoluut pad.</span><span class="sxs-lookup"><span data-stu-id="27b43-148">If you are not in the `Cert:` drive, use an absolute path.</span></span>

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a><span data-ttu-id="27b43-149">Certificaat eigenschappen weer geven in het certificaat: station</span><span class="sxs-lookup"><span data-stu-id="27b43-149">Displaying certificate properties within the Cert: drive</span></span>

<span data-ttu-id="27b43-150">In dit voor beeld wordt een certificaat met opgehaald `Get-Item` en opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="27b43-150">This example gets a certificate with `Get-Item` and stores it in a variable.</span></span>
<span data-ttu-id="27b43-151">In het voor beeld worden de nieuwe eigenschappen van het certificaat script (**DnsNameList**, **EnhancedKeyUsageList**, **SendAsTrustedIssuer**) gebruikt `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="27b43-151">The example shows the new certificate script properties (**DnsNameList**, **EnhancedKeyUsageList**, **SendAsTrustedIssuer**) using `Select-Object`.</span></span>

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a><span data-ttu-id="27b43-152">Alle ontwerp certificaten zoeken</span><span class="sxs-lookup"><span data-stu-id="27b43-152">Find all CodeSigning certificates</span></span>

<span data-ttu-id="27b43-153">Deze opdracht maakt gebruik van de **CodeSigningCert** **en de** para meters van de `Get-ChildItem` cmdlet om alle certificaten op de computer te verkrijgen die dienst hebben voor de ondertekening van de programma code.</span><span class="sxs-lookup"><span data-stu-id="27b43-153">This command uses the **CodeSigningCert** and **Recurse** parameters of the `Get-ChildItem` cmdlet to get all of the certificates on the computer that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a><span data-ttu-id="27b43-154">Verlopen certificaten zoeken</span><span class="sxs-lookup"><span data-stu-id="27b43-154">Find expired certificates</span></span>

<span data-ttu-id="27b43-155">Met deze opdracht wordt de para meter **ExpiringInDays** van de `Get-ChildItem` cmdlet gebruikt om certificaten op te halen die binnen de komende 30 dagen verlopen.</span><span class="sxs-lookup"><span data-stu-id="27b43-155">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet to get certificates that will expire within the next 30 days.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a><span data-ttu-id="27b43-156">SSL-certificaten voor server zoeken</span><span class="sxs-lookup"><span data-stu-id="27b43-156">Find Server SSL Certificates</span></span>

<span data-ttu-id="27b43-157">Met deze opdracht wordt de para meter **SSLServerAuthentication** van de `Get-ChildItem` cmdlet gebruikt om alle SSL-certificaten van de server op te halen in de winkels van mijn en webhosting.</span><span class="sxs-lookup"><span data-stu-id="27b43-157">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get all Server SSL Certificates in the My and WebHosting stores.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a><span data-ttu-id="27b43-158">Verlopen certificaten zoeken op externe computers</span><span class="sxs-lookup"><span data-stu-id="27b43-158">Find expired certificates on remote computers</span></span>

<span data-ttu-id="27b43-159">Met deze opdracht wordt de `Invoke-Command` cmdlet gebruikt om een opdracht uit te voeren `Get-ChildItem` op de Srv01-en Srv02-computers.</span><span class="sxs-lookup"><span data-stu-id="27b43-159">This command uses the `Invoke-Command` cmdlet to run a `Get-ChildItem` command on the Srv01 and Srv02 computers.</span></span> <span data-ttu-id="27b43-160">Als de waarde nul (0) is in de para meter **ExpiringInDays** , worden certificaten opgehaald op de Srv01-en Srv02-computers die zijn verlopen.</span><span class="sxs-lookup"><span data-stu-id="27b43-160">A value of zero (0) in the **ExpiringInDays** parameter gets certificates on the Srv01 and Srv02 computers that have expired.</span></span>

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a><span data-ttu-id="27b43-161">Filters combi neren om een specifieke set certificaten te zoeken</span><span class="sxs-lookup"><span data-stu-id="27b43-161">Combining filters to find a specific set of certificates</span></span>

<span data-ttu-id="27b43-162">Met deze opdracht worden alle certificaten in de LocalMachine-opslag locatie opgehaald met de volgende kenmerken:</span><span class="sxs-lookup"><span data-stu-id="27b43-162">This command gets all certificates in the LocalMachine store location that have the following attributes:</span></span>

- <span data-ttu-id="27b43-163">' fabrikam ' in de DNS-naam</span><span class="sxs-lookup"><span data-stu-id="27b43-163">"fabrikam" in their DNS name</span></span>
- <span data-ttu-id="27b43-164">' Client verificatie ' in hun EKU</span><span class="sxs-lookup"><span data-stu-id="27b43-164">"Client Authentication" in their EKU</span></span>
- <span data-ttu-id="27b43-165">een waarde van `$true` voor de eigenschap **SendAsTrustedIssuer**</span><span class="sxs-lookup"><span data-stu-id="27b43-165">a value of `$true` for the **SendAsTrustedIssuer** property</span></span>
- <span data-ttu-id="27b43-166">verloopt niet binnen de komende 30 dagen.</span><span class="sxs-lookup"><span data-stu-id="27b43-166">do not expire within the next 30 days.</span></span>

<span data-ttu-id="27b43-167">De eigenschap **NotAfter** slaat de verval datum van het certificaat op.</span><span class="sxs-lookup"><span data-stu-id="27b43-167">The **NotAfter** property stores the certificate expiration date.</span></span>

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a><span data-ttu-id="27b43-168">De MMC-module Certificaten openen</span><span class="sxs-lookup"><span data-stu-id="27b43-168">Opening the Certificates MMC Snap-in</span></span>

<span data-ttu-id="27b43-169">`Invoke-Item`Met de cmdlet wordt de standaard toepassing gebruikt voor het openen van een pad dat u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="27b43-169">The `Invoke-Item` cmdlet will use the default application to open a path you specify.</span></span> <span data-ttu-id="27b43-170">Voor certificaten is de standaard toepassing de MMC-module Certificaten.</span><span class="sxs-lookup"><span data-stu-id="27b43-170">For certificates, the default application is the Certificates MMC snap-in.</span></span>

<span data-ttu-id="27b43-171">Met deze opdracht wordt de MMC-module Certificaten geopend om het opgegeven certificaat te beheren.</span><span class="sxs-lookup"><span data-stu-id="27b43-171">This command opens the Certificates MMC snap-in to manage the specified certificate.</span></span>

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a><span data-ttu-id="27b43-172">Certificaten kopiëren</span><span class="sxs-lookup"><span data-stu-id="27b43-172">Copying Certificates</span></span>

<span data-ttu-id="27b43-173">Het kopiëren van certificaten wordt niet ondersteund door de **certificaat** provider.</span><span class="sxs-lookup"><span data-stu-id="27b43-173">Copying certificates is not supported by the **Certificate** provider.</span></span> <span data-ttu-id="27b43-174">Wanneer u een certificaat probeert te kopiëren, wordt deze fout weer geven.</span><span class="sxs-lookup"><span data-stu-id="27b43-174">When you attempt to copy a certificate, you see this error.</span></span>

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a><span data-ttu-id="27b43-175">Certificaten verplaatsen</span><span class="sxs-lookup"><span data-stu-id="27b43-175">Moving Certificates</span></span>

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a><span data-ttu-id="27b43-176">Alle SSL-server verificatie certificaten verplaatsen naar de webhosting-Store</span><span class="sxs-lookup"><span data-stu-id="27b43-176">Move all SSL Server authentication certs to the WebHosting store</span></span>

<span data-ttu-id="27b43-177">Met deze opdracht wordt de `Move-Item` cmdlet gebruikt om een certificaat uit de mijn Store te verplaatsen naar het webhosting-archief.</span><span class="sxs-lookup"><span data-stu-id="27b43-177">This command uses the `Move-Item` cmdlet to move a certificate from the My store to the WebHosting store.</span></span>

<span data-ttu-id="27b43-178">`Move-Item` certificaat archieven worden niet verplaatst en er worden geen certificaten naar een andere opslag locatie verplaatst, zoals het verplaatsen van een certificaat van LocalMachine naar CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="27b43-178">`Move-Item` will not move certificate stores and it will not move certificates to a different store location, such as moving a certificate from LocalMachine to CurrentUser.</span></span> <span data-ttu-id="27b43-179">Met de `Move-Item` cmdlet worden certificaten verplaatst, maar worden persoonlijke sleutels niet verplaatst.</span><span class="sxs-lookup"><span data-stu-id="27b43-179">The `Move-Item` cmdlet moves certificates, but it does not move private keys.</span></span>

<span data-ttu-id="27b43-180">Met deze opdracht wordt de para meter **SSLServerAuthentication** van de `Get-ChildItem` cmdlet gebruikt om certificaten voor SSL-server verificatie op te halen in het certificaat archief.</span><span class="sxs-lookup"><span data-stu-id="27b43-180">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get SSL server authentication certificates in the MY certificate store.</span></span>

<span data-ttu-id="27b43-181">De geretourneerde certificaten worden door gegeven aan de `Move-Item` cmdlet, waardoor de certificaten worden verplaatst naar het webhosting-archief.</span><span class="sxs-lookup"><span data-stu-id="27b43-181">The returned certificates are piped to the `Move-Item` cmdlet, which moves the certificates to the WebHosting store.</span></span>

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a><span data-ttu-id="27b43-182">Certificaten en persoonlijke sleutels verwijderen</span><span class="sxs-lookup"><span data-stu-id="27b43-182">Deleting Certificates and Private Keys</span></span>

<span data-ttu-id="27b43-183">`Remove-Item`Met de cmdlet worden de door u opgegeven certificaten verwijderd.</span><span class="sxs-lookup"><span data-stu-id="27b43-183">The `Remove-Item` cmdlet will remove certificates that you specify.</span></span> <span data-ttu-id="27b43-184">Met de `-DeleteKey` dynamische para meter wordt de persoonlijke sleutel verwijderd.</span><span class="sxs-lookup"><span data-stu-id="27b43-184">The `-DeleteKey` dynamic parameter deletes the private key.</span></span>

### <a name="delete-a-certificate-from-the-ca-store"></a><span data-ttu-id="27b43-185">Een certificaat verwijderen uit het CA-archief</span><span class="sxs-lookup"><span data-stu-id="27b43-185">Delete a Certificate from the CA store</span></span>

<span data-ttu-id="27b43-186">Met deze opdracht wordt een certificaat uit het CA-certificaat archief verwijderd, maar wordt de gekoppelde persoonlijke sleutel intact gelaten.</span><span class="sxs-lookup"><span data-stu-id="27b43-186">This command deletes a certificate from the CA certificate store, but leaves the associated private key intact.</span></span>

<span data-ttu-id="27b43-187">In het `Cert:` station ondersteunt de `Remove-Item` cmdlet alleen de para meters **DeleteKey**, **Path**, **WhatIf** en **confirm** .</span><span class="sxs-lookup"><span data-stu-id="27b43-187">In the `Cert:` drive, the `Remove-Item` cmdlet supports only the **DeleteKey**, **Path**, **WhatIf**, and **Confirm** parameters.</span></span> <span data-ttu-id="27b43-188">Alle andere para meters worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="27b43-188">All other parameters are ignored.</span></span>

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a><span data-ttu-id="27b43-189">Een certificaat verwijderen met een Joker teken in de DNS-naam</span><span class="sxs-lookup"><span data-stu-id="27b43-189">Delete a Certificate using a wildcards in the DNS name</span></span>

<span data-ttu-id="27b43-190">Met deze opdracht worden alle certificaten verwijderd die een DNS-naam hebben die ' fabrikam ' bevat.</span><span class="sxs-lookup"><span data-stu-id="27b43-190">This command deletes all certificates that have a DNS name that contains "Fabrikam".</span></span> <span data-ttu-id="27b43-191">De para meter **DNSName** van de cmdlet wordt gebruikt `Get-ChildItem` voor het ophalen van de certificaten en de `Remove-Item` cmdlet om deze te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="27b43-191">It uses the **DNSName** parameter of the `Get-ChildItem` cmdlet to get the certificates and the `Remove-Item` cmdlet to delete them.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a><span data-ttu-id="27b43-192">Persoonlijke sleutels van een externe computer verwijderen</span><span class="sxs-lookup"><span data-stu-id="27b43-192">Delete private keys from a remote computer</span></span>

<span data-ttu-id="27b43-193">Met deze reeks opdrachten wordt delegering ingeschakeld en wordt het certificaat en de bijbehorende persoonlijke sleutel op een externe computer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="27b43-193">This series of commands enables delegation and then deletes the certificate and associated private key on a remote computer.</span></span> <span data-ttu-id="27b43-194">Als u een persoonlijke sleutel op een externe computer wilt verwijderen, moet u gedelegeerde referenties gebruiken.</span><span class="sxs-lookup"><span data-stu-id="27b43-194">To delete a private key on a remote computer, you must use delegated credentials.</span></span>

<span data-ttu-id="27b43-195">Gebruik de- `Enable-WSManCredSSP` cmdlet om CredSSP-verificatie (Credential Security service provider) in te scha kelen op een client op de externe computer S1.</span><span class="sxs-lookup"><span data-stu-id="27b43-195">Use the `Enable-WSManCredSSP` cmdlet to enable Credential Security Service Provider (CredSSP) authentication on a client on the S1 remote computer.</span></span>
<span data-ttu-id="27b43-196">CredSSP staat gedelegeerde verificatie toe.</span><span class="sxs-lookup"><span data-stu-id="27b43-196">CredSSP permits delegated authentication.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

<span data-ttu-id="27b43-197">Gebruik de `Connect-WSMan` cmdlet om de computer S1 te verbinden met de WinRM-service op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="27b43-197">Use the `Connect-WSMan` cmdlet to connect the S1 computer to the WinRM service on the local computer.</span></span> <span data-ttu-id="27b43-198">Wanneer deze opdracht is voltooid, wordt de computer S1 weer gegeven in het lokale `WSMan:` station in Power shell.</span><span class="sxs-lookup"><span data-stu-id="27b43-198">When this command completes, the S1 computer appears in the local `WSMan:` drive in PowerShell.</span></span>

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

<span data-ttu-id="27b43-199">U kunt nu de cmdlet Set-Item gebruiken in het station WSMan: om het kenmerk CredSSP voor de WinRM-service in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="27b43-199">Now, you can use the Set-Item cmdlet in the WSMan: drive to enable the CredSSP attribute for the WinRM service.</span></span>

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

<span data-ttu-id="27b43-200">Start een externe sessie op de computer S1 met de `New-PSSession` cmdlet en geef CredSSP-verificatie op.</span><span class="sxs-lookup"><span data-stu-id="27b43-200">Start a remote session on the s1 computer using the `New-PSSession` cmdlet, and specify CredSSP authentication.</span></span> <span data-ttu-id="27b43-201">Hiermee wordt de sessie in de `$s` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="27b43-201">Saves the session in the `$s` variable.</span></span>

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

<span data-ttu-id="27b43-202">Ten slotte gebruikt `Invoke-Command` u de cmdlet om een opdracht uit te voeren `Remove-Item` in de sessie in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="27b43-202">Finally, use the `Invoke-Command` cmdlet to run a `Remove-Item` command in the session in the `$s` variable.</span></span> <span data-ttu-id="27b43-203">De `Remove-Item` opdracht gebruikt de para meter **DeleteKey** om de persoonlijke sleutel samen met het opgegeven certificaat te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="27b43-203">The `Remove-Item` command uses the **DeleteKey** parameter to remove the private key along with the specified certificate.</span></span>

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a><span data-ttu-id="27b43-204">Verlopen certificaten verwijderen</span><span class="sxs-lookup"><span data-stu-id="27b43-204">Delete expired Certificates</span></span>

<span data-ttu-id="27b43-205">Met deze opdracht wordt de para meter **ExpiringInDays** van de `Get-ChildItem` cmdlet met de waarde 0 gebruikt om certificaten in de webhosting Store te verkrijgen die zijn verlopen.</span><span class="sxs-lookup"><span data-stu-id="27b43-205">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet with a value of 0 to get certificates in the WebHosting store that have expired.</span></span>

<span data-ttu-id="27b43-206">De variabele met de geretourneerde certificaten wordt naar de cmdlet gesluisd `Remove-Item` , waardoor deze wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="27b43-206">The variable containing the returned certificates is piped to the `Remove-Item` cmdlet, which deletes them.</span></span> <span data-ttu-id="27b43-207">De opdracht maakt gebruik van de para meter **DeleteKey** voor het verwijderen van de persoonlijke sleutel en het certificaat.</span><span class="sxs-lookup"><span data-stu-id="27b43-207">The command uses the **DeleteKey** parameter to delete the private key along with the certificate.</span></span>

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a><span data-ttu-id="27b43-208">Certificaten maken</span><span class="sxs-lookup"><span data-stu-id="27b43-208">Creating Certificates</span></span>

<span data-ttu-id="27b43-209">De `New-Item` cmdlet maakt geen nieuwe certificaten in de **certificaat** provider.</span><span class="sxs-lookup"><span data-stu-id="27b43-209">The `New-Item` cmdlet does not create new certificates in the **Certificate** provider.</span></span> <span data-ttu-id="27b43-210">Gebruik de cmdlet [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) om een certificaat voor test doeleinden te maken.</span><span class="sxs-lookup"><span data-stu-id="27b43-210">Use the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet to create a certificate for testing purposes.</span></span>

## <a name="creating-certificate-stores"></a><span data-ttu-id="27b43-211">Certificaat archieven maken</span><span class="sxs-lookup"><span data-stu-id="27b43-211">Creating Certificate Stores</span></span>

<span data-ttu-id="27b43-212">In het certificaat: station maakt de `New-Item` cmdlet certificaat archieven op de opslag locatie van de LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="27b43-212">In the Cert: drive, the `New-Item` cmdlet creates certificate stores in the LocalMachine store location.</span></span> <span data-ttu-id="27b43-213">De para meters **name**, **Path**, **WhatIf** en **confirm** worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="27b43-213">It supports the **Name**, **Path**, **WhatIf**, and **Confirm** parameters.</span></span> <span data-ttu-id="27b43-214">Alle andere para meters worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="27b43-214">All other parameters are ignored.</span></span> <span data-ttu-id="27b43-215">De opdracht retourneert een **System. Security. Cryptography. X509Certificates. X509Store** dat het nieuwe certificaat archief vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="27b43-215">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

<span data-ttu-id="27b43-216">Met deze opdracht maakt u een nieuw certificaat archief met de naam ' CustomStore ' in de opslag locatie van LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="27b43-216">This command creates a new certificate store named "CustomStore" in the LocalMachine store location.</span></span>

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a><span data-ttu-id="27b43-217">Een nieuw certificaat archief maken op een externe computer</span><span class="sxs-lookup"><span data-stu-id="27b43-217">Create a new certificate store on a remote computer</span></span>

<span data-ttu-id="27b43-218">Met deze opdracht maakt u een nieuw certificaat archief met de naam ' HostingStore ' in de opslag locatie LocalMachine op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="27b43-218">This command creates a new certificate store named "HostingStore" in the LocalMachine store location on the Server01 computer.</span></span>

<span data-ttu-id="27b43-219">De opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `New-Item` op de computer Server01.</span><span class="sxs-lookup"><span data-stu-id="27b43-219">The command uses the `Invoke-Command` cmdlet to run a `New-Item` command on the Server01 computer.</span></span> <span data-ttu-id="27b43-220">De opdracht retourneert een **System. Security. Cryptography. X509Certificates. X509Store** dat het nieuwe certificaat archief vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="27b43-220">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a><span data-ttu-id="27b43-221">Client certificaten maken voor WS-Man</span><span class="sxs-lookup"><span data-stu-id="27b43-221">Creating Client Certificates for WS-Man</span></span>

<span data-ttu-id="27b43-222">Met deze opdracht maakt u een item voor **ClientCertificate** dat kan worden gebruikt door de **WS-Management** -client.</span><span class="sxs-lookup"><span data-stu-id="27b43-222">This command creates **ClientCertificate** entry that can be used by the **WS-Management** client.</span></span> <span data-ttu-id="27b43-223">De nieuwe **ClientCertificate** wordt weer gegeven in de map **ClientCertificate** als "ClientCertificate_1234567890".</span><span class="sxs-lookup"><span data-stu-id="27b43-223">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="27b43-224">Alle para meters zijn verplicht.</span><span class="sxs-lookup"><span data-stu-id="27b43-224">All of the parameters are mandatory.</span></span> <span data-ttu-id="27b43-225">De **Uitgever** moet een vinger afdruk van het certificaat van de certificerings instantie zijn.</span><span class="sxs-lookup"><span data-stu-id="27b43-225">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a><span data-ttu-id="27b43-226">Certificaat archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="27b43-226">Deleting Certificate Stores</span></span>

### <a name="delete-a-certificate-store-from-a-remote-computer"></a><span data-ttu-id="27b43-227">Een certificaat archief verwijderen van een externe computer</span><span class="sxs-lookup"><span data-stu-id="27b43-227">Delete a certificate store from a remote computer</span></span>

<span data-ttu-id="27b43-228">Met deze opdracht wordt de `Invoke-Command` cmdlet gebruikt om een opdracht uit te voeren `Remove-Item` op de computers S1 en S2.</span><span class="sxs-lookup"><span data-stu-id="27b43-228">This command uses the `Invoke-Command` cmdlet to run a `Remove-Item` command on the S1 and S2 computers.</span></span> <span data-ttu-id="27b43-229">De `Remove-Item` opdracht bevat de **recursieve** para meter, waarmee de certificaten in de Store worden verwijderd voordat het archief wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="27b43-229">The `Remove-Item` command includes the **Recurse** parameter, which deletes the certificates in the store before it deletes the store.</span></span>

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a><span data-ttu-id="27b43-230">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="27b43-230">Dynamic parameters</span></span>

<span data-ttu-id="27b43-231">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="27b43-231">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span> <span data-ttu-id="27b43-232">Deze para meters zijn geldig in alle submappen van de certificaat provider, maar zijn alleen effectief op certificaten.</span><span class="sxs-lookup"><span data-stu-id="27b43-232">These parameters are valid in all subdirectories of the Certificate provider, but are effective only on certificates.</span></span>

> [!NOTE]
> <span data-ttu-id="27b43-233">Para meters die filteren op de `EnhancedKeyUsageList` eigenschap, retour neren ook items met een lege `EnhancedKeyUsageList` eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="27b43-233">Parameters that perform filtering against the `EnhancedKeyUsageList` property also return items with an empty `EnhancedKeyUsageList` property value.</span></span>
> <span data-ttu-id="27b43-234">Certificaten met een lege **EnhancedKeyUsageList** kunnen voor alle doel einden worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="27b43-234">Certificates that have an empty **EnhancedKeyUsageList** can be used for all purposes.</span></span>

<span data-ttu-id="27b43-235">De volgende certificaat Provider parameters zijn opnieuw geïntroduceerd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="27b43-235">The following Certificate provider parameters were reintroduced in PowerShell 7.1.</span></span>

- <span data-ttu-id="27b43-236">DNSName</span><span class="sxs-lookup"><span data-stu-id="27b43-236">DNSName</span></span>
- <span data-ttu-id="27b43-237">DocumentEncryptionCert</span><span class="sxs-lookup"><span data-stu-id="27b43-237">DocumentEncryptionCert</span></span>
- <span data-ttu-id="27b43-238">SLEUTEL</span><span class="sxs-lookup"><span data-stu-id="27b43-238">EKU</span></span>
- <span data-ttu-id="27b43-239">ExpiringInDays</span><span class="sxs-lookup"><span data-stu-id="27b43-239">ExpiringInDays</span></span>
- <span data-ttu-id="27b43-240">SSLServerAuthentication</span><span class="sxs-lookup"><span data-stu-id="27b43-240">SSLServerAuthentication</span></span>

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="27b43-241">CodeSigningCert <System. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="27b43-241">CodeSigningCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="27b43-242">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="27b43-242">Cmdlets supported</span></span>

- [<span data-ttu-id="27b43-243">Get-item</span><span class="sxs-lookup"><span data-stu-id="27b43-243">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="27b43-244">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="27b43-244">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="27b43-245">Met deze para meter worden certificaten opgehaald waarvoor ' hand tekening bij programma code ' is in de waarde van de eigenschap **EnhancedKeyUsageList** .</span><span class="sxs-lookup"><span data-stu-id="27b43-245">This parameter gets certificates that have "Code Signing" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="deletekey-systemmanagementautomationswitchparameter"></a><span data-ttu-id="27b43-246">DeleteKey <System. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="27b43-246">DeleteKey <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="27b43-247">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="27b43-247">Cmdlets supported</span></span>

- [<span data-ttu-id="27b43-248">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="27b43-248">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

<span data-ttu-id="27b43-249">Met deze para meter wordt de bijbehorende persoonlijke sleutel verwijderd wanneer het certificaat wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="27b43-249">This parameter deletes the associated private key when it deletes the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27b43-250">Als u een persoonlijke sleutel die is gekoppeld aan een gebruikers certificaat in het `Cert:\CurrentUser` Archief op een externe computer wilt verwijderen, moet u gedelegeerde referenties gebruiken.</span><span class="sxs-lookup"><span data-stu-id="27b43-250">To delete a private key that is associated with a user certificate in the `Cert:\CurrentUser` store on a remote computer, you must use delegated credentials.</span></span> <span data-ttu-id="27b43-251">De `Invoke-Command` cmdlet ondersteunt het overdragen van referenties met behulp van de **CredSSP** -para meter.</span><span class="sxs-lookup"><span data-stu-id="27b43-251">The `Invoke-Command` cmdlet supports credential delegation using the **CredSSP** parameter.</span></span> <span data-ttu-id="27b43-252">U moet rekening houden met eventuele beveiligings Risico's voordat u `Remove-Item` met `Invoke-Command` en de overdracht van referenties.</span><span class="sxs-lookup"><span data-stu-id="27b43-252">You should consider any security risks before using `Remove-Item` with `Invoke-Command` and credential delegation.</span></span>

<span data-ttu-id="27b43-253">Deze para meter is opnieuw geïntroduceerd in Power shell 7,1</span><span class="sxs-lookup"><span data-stu-id="27b43-253">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a><span data-ttu-id="27b43-254">DnsName <Microsoft. Power shell. commands. DnsNameRepresentation></span><span class="sxs-lookup"><span data-stu-id="27b43-254">DnsName <Microsoft.PowerShell.Commands.DnsNameRepresentation></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="27b43-255">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="27b43-255">Cmdlets supported</span></span>

- [<span data-ttu-id="27b43-256">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="27b43-256">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="27b43-257">Met deze para meter worden certificaten opgehaald die het opgegeven domein naam of naam patroon hebben in de eigenschap **DNSNameList** van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="27b43-257">This parameter gets certificates that have the specified domain name or name pattern in the **DNSNameList** property of the certificate.</span></span> <span data-ttu-id="27b43-258">De waarde van deze para meter kan ' Unicode ' of ' ASCII ' zijn.</span><span class="sxs-lookup"><span data-stu-id="27b43-258">The value of this parameter can either be "Unicode" or "ASCII".</span></span> <span data-ttu-id="27b43-259">Punycode waarden worden geconverteerd naar Unicode.</span><span class="sxs-lookup"><span data-stu-id="27b43-259">Punycode values are converted to Unicode.</span></span> <span data-ttu-id="27b43-260">Joker tekens ( `*` ) zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="27b43-260">Wildcard characters (`*`) are permitted.</span></span>

<span data-ttu-id="27b43-261">Deze para meter is opnieuw geïntroduceerd in Power shell 7,1</span><span class="sxs-lookup"><span data-stu-id="27b43-261">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="27b43-262">DocumentEncryptionCert <System. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="27b43-262">DocumentEncryptionCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="27b43-263">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="27b43-263">Cmdlets supported</span></span>

- [<span data-ttu-id="27b43-264">Get-item</span><span class="sxs-lookup"><span data-stu-id="27b43-264">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="27b43-265">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="27b43-265">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="27b43-266">Met deze para meter worden certificaten opgehaald die ' document Encryption ' hebben in de waarde van de eigenschap **EnhancedKeyUsageList** .</span><span class="sxs-lookup"><span data-stu-id="27b43-266">This parameter gets certificates that have "Document Encryption" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="eku-systemstring"></a><span data-ttu-id="27b43-267">EKU <System. String></span><span class="sxs-lookup"><span data-stu-id="27b43-267">EKU <System.String></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="27b43-268">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="27b43-268">Cmdlets supported</span></span>

- [<span data-ttu-id="27b43-269">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="27b43-269">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="27b43-270">Met deze para meter worden certificaten opgehaald die het opgegeven tekst-of tekst patroon hebben in de `EnhancedKeyUsageList` eigenschap van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="27b43-270">This parameter gets certificates that have the specified text or text pattern in the `EnhancedKeyUsageList` property of the certificate.</span></span> <span data-ttu-id="27b43-271">Joker tekens ( `*` ) zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="27b43-271">Wildcard characters (`*`) are permitted.</span></span> <span data-ttu-id="27b43-272">De `EnhancedKeyUsageList` eigenschap bevat de beschrijvende naam en de OID-velden van de EKU.</span><span class="sxs-lookup"><span data-stu-id="27b43-272">The `EnhancedKeyUsageList` property contains the friendly name and the OID fields of the EKU.</span></span>

<span data-ttu-id="27b43-273">Deze para meter is opnieuw geïntroduceerd in Power shell 7,1</span><span class="sxs-lookup"><span data-stu-id="27b43-273">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="expiringindays-systemint32"></a><span data-ttu-id="27b43-274">ExpiringInDays <System. Int32></span><span class="sxs-lookup"><span data-stu-id="27b43-274">ExpiringInDays <System.Int32></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="27b43-275">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="27b43-275">Cmdlets supported</span></span>

- [<span data-ttu-id="27b43-276">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="27b43-276">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="27b43-277">Met deze para meter worden certificaten opgehaald die in of vóór het opgegeven aantal dagen verlopen.</span><span class="sxs-lookup"><span data-stu-id="27b43-277">This parameter gets certificates that are expiring in or before the specified number of days.</span></span> <span data-ttu-id="27b43-278">Met de waarde 0 (nul) worden certificaten opgehaald die zijn verlopen.</span><span class="sxs-lookup"><span data-stu-id="27b43-278">A value of 0 (zero) gets certificates that have expired.</span></span>

<span data-ttu-id="27b43-279">Deze para meter is opnieuw geïntroduceerd in Power shell 7,1</span><span class="sxs-lookup"><span data-stu-id="27b43-279">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="itemtype-string"></a><span data-ttu-id="27b43-280">Item type \<String\></span><span class="sxs-lookup"><span data-stu-id="27b43-280">ItemType \<String\></span></span>

<span data-ttu-id="27b43-281">Met deze para meter kunt u het type item opgeven dat wordt gemaakt door `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="27b43-281">This parameter allows you to specify the type of item created by `New-Item`.</span></span>

<span data-ttu-id="27b43-282">In een `Certificate` station zijn de volgende waarden toegestaan:</span><span class="sxs-lookup"><span data-stu-id="27b43-282">In a `Certificate` drive, the following values are allowed:</span></span>

- <span data-ttu-id="27b43-283">Certificaat provider</span><span class="sxs-lookup"><span data-stu-id="27b43-283">Certificate Provider</span></span>
- <span data-ttu-id="27b43-284">Certificaat</span><span class="sxs-lookup"><span data-stu-id="27b43-284">Certificate</span></span>
- <span data-ttu-id="27b43-285">Opslaan</span><span class="sxs-lookup"><span data-stu-id="27b43-285">Store</span></span>
- <span data-ttu-id="27b43-286">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="27b43-286">StoreLocation</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="27b43-287">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="27b43-287">Cmdlets Supported</span></span>

- [<span data-ttu-id="27b43-288">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="27b43-288">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a><span data-ttu-id="27b43-289">SSLServerAuthentication <System. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="27b43-289">SSLServerAuthentication <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="27b43-290">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="27b43-290">Cmdlets supported</span></span>

- [<span data-ttu-id="27b43-291">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="27b43-291">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="27b43-292">Hiermee worden alleen server certificaten voor SSL-webhosting opgehaald.</span><span class="sxs-lookup"><span data-stu-id="27b43-292">Gets only server certificates for SSL web hosting.</span></span> <span data-ttu-id="27b43-293">Met deze para meter worden certificaten opgehaald die "server authenticatie" hebben in de `EnhancedKeyUsageList` eigenschaps waarde.</span><span class="sxs-lookup"><span data-stu-id="27b43-293">This parameter gets certificates that have "Server Authentication" in their `EnhancedKeyUsageList` property value.</span></span>

<span data-ttu-id="27b43-294">Deze para meter is opnieuw geïntroduceerd in Power shell 7,1</span><span class="sxs-lookup"><span data-stu-id="27b43-294">This parameter was reintroduced in PowerShell 7.1</span></span>

## <a name="script-properties"></a><span data-ttu-id="27b43-295">Script eigenschappen</span><span class="sxs-lookup"><span data-stu-id="27b43-295">Script properties</span></span>

<span data-ttu-id="27b43-296">Er zijn nieuwe script eigenschappen toegevoegd aan het **x509Certificate2** -object dat de certificaten vertegenwoordigt, zodat u de certificaten eenvoudig kunt zoeken en beheren.</span><span class="sxs-lookup"><span data-stu-id="27b43-296">New script properties have been added to the **x509Certificate2** object that represents the certificates to make it easy to search and manage the certificates.</span></span>

- <span data-ttu-id="27b43-297">`DnsNameList`: Als u de `DnsNameList` eigenschap wilt vullen, kopieert de certificaat provider de inhoud van de DNSName-vermelding in de SubjectAlternativeName-extensie (San).</span><span class="sxs-lookup"><span data-stu-id="27b43-297">`DnsNameList`: To populate the `DnsNameList` property, the Certificate provider copies the content from the DNSName entry in the SubjectAlternativeName (SAN) extension.</span></span> <span data-ttu-id="27b43-298">Als de SAN-extensie leeg is, wordt de eigenschap gevuld met inhoud uit het veld onderwerp van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="27b43-298">If the SAN extension is empty, the property is populated with content from the Subject field of the certificate.</span></span>

- <span data-ttu-id="27b43-299">`EnhancedKeyUsageList`: Als u de `EnhancedKeyUsageList` eigenschap wilt vullen, kopieert de certificaat provider de OID-eigenschappen van het veld EnhancedKeyUsage (EKU) in het certificaat en wordt er een beschrijvende naam voor gemaakt.</span><span class="sxs-lookup"><span data-stu-id="27b43-299">`EnhancedKeyUsageList`: To populate the `EnhancedKeyUsageList` property, the Certificate provider copies the OID properties of the EnhancedKeyUsage (EKU) field in the certificate and creates a friendly name for it.</span></span>

- <span data-ttu-id="27b43-300">`SendAsTrustedIssuer`: Als u de `SendAsTrustedIssuer` eigenschap wilt vullen, kopieert de certificaat provider de `SendAsTrustedIssuer` eigenschap van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="27b43-300">`SendAsTrustedIssuer`: To populate the `SendAsTrustedIssuer` property, the Certificate provider copies the `SendAsTrustedIssuer` property from the certificate.</span></span>  <span data-ttu-id="27b43-301">Zie [beheer van vertrouwde verleners voor client verificatie](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="27b43-301">For more information see [Management of trusted issuers for client authentication](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span></span>

<span data-ttu-id="27b43-302">Met deze nieuwe functies kunt u zoeken naar certificaten op basis van de DNS-namen en verval datums en certificaten voor client-en Server verificatie onderscheiden door de waarde van de eigenschappen van de Enhanced Key Usage (EKU).</span><span class="sxs-lookup"><span data-stu-id="27b43-302">These new features let you search for certificates based on their DNS names and expiration dates, and distinguish client and server authentication certificates by the value of their Enhanced Key Usage (EKU) properties.</span></span>

## <a name="using-the-pipeline"></a><span data-ttu-id="27b43-303">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="27b43-303">Using the pipeline</span></span>

<span data-ttu-id="27b43-304">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="27b43-304">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="27b43-305">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="27b43-305">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="27b43-306">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="27b43-306">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="27b43-307">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="27b43-307">Getting help</span></span>

<span data-ttu-id="27b43-308">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="27b43-308">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="27b43-309">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter van `Get-Help` om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="27b43-309">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of `Get-Help` to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a><span data-ttu-id="27b43-310">Zie ook</span><span class="sxs-lookup"><span data-stu-id="27b43-310">See also</span></span>

[<span data-ttu-id="27b43-311">about_Providers</span><span class="sxs-lookup"><span data-stu-id="27b43-311">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="27b43-312">about_Signing</span><span class="sxs-lookup"><span data-stu-id="27b43-312">about_Signing</span></span>](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[<span data-ttu-id="27b43-313">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="27b43-313">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[<span data-ttu-id="27b43-314">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="27b43-314">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[<span data-ttu-id="27b43-315">Get-pfx</span><span class="sxs-lookup"><span data-stu-id="27b43-315">Get-PfxCertificate</span></span>](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
