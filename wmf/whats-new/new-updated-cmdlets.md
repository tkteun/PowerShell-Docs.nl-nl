---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Nieuwe en bijgewerkte cmdlets
ms.openlocfilehash: 9ec31c89c0bc4b111b40e2d4725fa0782a573204
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856243"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="ea948-103">Nieuwe en bijgewerkte cmdlets</span><span class="sxs-lookup"><span data-stu-id="ea948-103">New and updated cmdlets</span></span>

<span data-ttu-id="ea948-104">We hebben nieuwe en bijgewerkte bestaande cmdlets op basis van feedback van de community toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="ea948-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="ea948-105">Archief-cmdlets</span><span class="sxs-lookup"><span data-stu-id="ea948-105">Archive cmdlets</span></span>

<span data-ttu-id="ea948-106">Twee nieuwe cmdlets `Compress-Archive` en `Expand-Archive`laat u comprimeren en vouw ZIP-bestanden.</span><span class="sxs-lookup"><span data-stu-id="ea948-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="ea948-107">Zie voor meer informatie de [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module-documentatie.</span><span class="sxs-lookup"><span data-stu-id="ea948-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="ea948-108">Catalogus-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="ea948-108">Catalog Cmdlets</span></span>

<span data-ttu-id="ea948-109">Twee nieuwe cmdlets toegevoegd in de module Microsoft.PowerShell.Security.</span><span class="sxs-lookup"><span data-stu-id="ea948-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="ea948-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="ea948-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="ea948-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="ea948-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="ea948-112">Deze genereren en bestanden van Windows-catalogus te valideren.</span><span class="sxs-lookup"><span data-stu-id="ea948-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="ea948-113">Klembord-cmdlets</span><span class="sxs-lookup"><span data-stu-id="ea948-113">Clipboard cmdlets</span></span>

<span data-ttu-id="ea948-114">`Get-Clipboard` en `Set-Clipboard` maken het gemakkelijker voor u om inhoud naar en van een Windows PowerShell-sessie te brengen.</span><span class="sxs-lookup"><span data-stu-id="ea948-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="ea948-115">De Klembord-cmdlets bieden ondersteuning voor afbeeldingen, audio-bestanden, bestandslijsten en tekst.</span><span class="sxs-lookup"><span data-stu-id="ea948-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="ea948-116">Zie voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="ea948-116">For more information, see:</span></span>

- [<span data-ttu-id="ea948-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="ea948-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="ea948-118">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="ea948-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="ea948-119">Cmdlets voor Cryptographic Message-syntaxis (CMS)</span><span class="sxs-lookup"><span data-stu-id="ea948-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="ea948-120">De cmdlets voor Cryptographic Message-syntaxis ondersteunt versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor het beveiligen van berichten cryptografisch zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="ea948-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="ea948-121">De standaard CMS-versleuteling implementeert openbare-sleutelcryptografie, waarbij de sleutel wordt gebruikt voor het versleutelen van inhoud (de *openbare sleutel*) en de sleutel die wordt gebruikt om inhoud te ontsleutelen (de *privésleutel*) zijn gescheiden.</span><span class="sxs-lookup"><span data-stu-id="ea948-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="ea948-122">Uw openbare-sleutelcertificaat grote schaal kan worden gedeeld en is geen gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="ea948-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="ea948-123">Alle inhoud die is versleuteld met de openbare sleutel kan alleen worden ontsleuteld met behulp van de persoonlijke sleutel.</span><span class="sxs-lookup"><span data-stu-id="ea948-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="ea948-124">Zie voor meer informatie, [openbare-sleutelcryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="ea948-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="ea948-125">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="ea948-125">For more information see:</span></span>

- [<span data-ttu-id="ea948-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="ea948-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage.md)
- [<span data-ttu-id="ea948-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="ea948-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage.md)
- [<span data-ttu-id="ea948-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="ea948-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/rotect-CmsMessage.md)

<span data-ttu-id="ea948-129">Certificaten vereist de id van een unieke sleutelgebruik (EKU), zoals 'Handtekening bij programmacode' of 'Versleuteld Mail', om te bepalen of deze gegevens versleutelingscertificaten in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea948-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="ea948-130">Als u wilt weergeven versleutelingscertificaten document in de certificaatprovider, kunt u de **DocumentEncryptionCert** dynamische parameter van `Get-ChildItem`:</span><span class="sxs-lookup"><span data-stu-id="ea948-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="ea948-131">Gestructureerd objecten uit de inhoud van de tekenreeks uitpakken en parseren</span><span class="sxs-lookup"><span data-stu-id="ea948-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="ea948-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="ea948-132">ConvertFrom-String</span></span>

<span data-ttu-id="ea948-133">De nieuwe `ConvertFrom-String` cmdlet ondersteunt twee modi:</span><span class="sxs-lookup"><span data-stu-id="ea948-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="ea948-134">Basic gescheiden parseren</span><span class="sxs-lookup"><span data-stu-id="ea948-134">Basic delimited parsing</span></span>
- <span data-ttu-id="ea948-135">Automatisch gegenereerde voorbeeld gebaseerde parseren</span><span class="sxs-lookup"><span data-stu-id="ea948-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="ea948-136">Gescheiden parseren, standaard, splitst de invoer op witruimte en namen van eigenschappen aan de resulterende groepen toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ea948-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="ea948-137">De **UpdateTemplate** parameter slaat de resultaten van het learning-algoritme in een opmerking in het sjabloonbestand.</span><span class="sxs-lookup"><span data-stu-id="ea948-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="ea948-138">Dit maakt het learning verwerken (de traagste fase) een eenmalige kosten.</span><span class="sxs-lookup"><span data-stu-id="ea948-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="ea948-139">Met `ConvertFrom-String` met een sjabloon met het gecodeerde learning-algoritme is nu bijna onmiddellijk.</span><span class="sxs-lookup"><span data-stu-id="ea948-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="ea948-140">Zie voor meer informatie, [ConvertFrom-tekenreeks](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="ea948-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="ea948-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="ea948-141">Convert-String</span></span>

<span data-ttu-id="ea948-142">`Convert-String` kunt u bieden voor en na voorbeelden van hoe u tekst om te zoeken.</span><span class="sxs-lookup"><span data-stu-id="ea948-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="ea948-143">De cmdlet wordt de tekst automatisch opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="ea948-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="ea948-144">Zie voor meer informatie, [Convert-tekenreeks](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="ea948-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="ea948-145">Updates voor FileInfo-object</span><span class="sxs-lookup"><span data-stu-id="ea948-145">Updates to FileInfo object</span></span>

<span data-ttu-id="ea948-146">Informatie over de bestandsversie kan misleidend zijn, met name in gevallen waar het bestand is hersteld.</span><span class="sxs-lookup"><span data-stu-id="ea948-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="ea948-147">WMF 5.0 voegt nieuwe **FileVersionRaw** en **ProductVersionRaw** eigenschappen gewijzigd in een script **FileInfo** objecten.</span><span class="sxs-lookup"><span data-stu-id="ea948-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="ea948-148">Hier zijn de eigenschappen als worden weergegeven voor de powershell.exe (ervan uitgaande dat $pid is de ID van de PowerShell-proces):</span><span class="sxs-lookup"><span data-stu-id="ea948-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="ea948-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="ea948-149">Format-Hex</span></span>

<span data-ttu-id="ea948-150">`Format-Hex` kunt u tekst of binaire gegevens weergeven in hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="ea948-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="ea948-151">Zie voor meer informatie, [indeling hexadecimaal](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="ea948-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="ea948-152">Get-ChildItem heeft parameter - Depth</span><span class="sxs-lookup"><span data-stu-id="ea948-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="ea948-153">`Get-ChildItem` heeft nu een **diepte** parameter voor gebruik met **Recurse** de recursie beperken:</span><span class="sxs-lookup"><span data-stu-id="ea948-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="ea948-154">Module-ondersteuning voor declareren versiebereiken (1.\*, enzovoort)</span><span class="sxs-lookup"><span data-stu-id="ea948-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="ea948-155">U kunt nu gecombineerd **MinimumVersion** en **MaximumVersion** module binnen een bepaald bereik te importeren.</span><span class="sxs-lookup"><span data-stu-id="ea948-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="ea948-156">De parameters bieden ook ondersteuning voor jokertekens.</span><span class="sxs-lookup"><span data-stu-id="ea948-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="ea948-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="ea948-157">New-Guid</span></span>

<span data-ttu-id="ea948-158">Er zijn veel scenario's waarbij youneed voor de unieke id.</span><span class="sxs-lookup"><span data-stu-id="ea948-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="ea948-159">De `New-GUID` cmdlet biedt een eenvoudige manier om te maken van een nieuwe GUID.</span><span class="sxs-lookup"><span data-stu-id="ea948-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="ea948-160">Parameter NoNewLine</span><span class="sxs-lookup"><span data-stu-id="ea948-160">NoNewLine parameter</span></span>

<span data-ttu-id="ea948-161">`Out-File`, `Add-Content`, en `Set-Content` hebben nu een nieuwe **NoNewline** switch die een nieuwe regel na de uitvoer wordt weggelaten.</span><span class="sxs-lookup"><span data-stu-id="ea948-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="ea948-162">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ea948-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt

```Output
This is a single sentence.
```

<span data-ttu-id="ea948-163">Zonder **NoNewline** opgegeven, wordt elk fragment zou worden op een afzonderlijke regel:</span><span class="sxs-lookup"><span data-stu-id="ea948-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="ea948-164">Interactie met symbolische koppelingen met verbeterde Item-cmdlets</span><span class="sxs-lookup"><span data-stu-id="ea948-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="ea948-165">De cmdlet Item en een aantal verwante cmdlets zijn uitgebreid ter ondersteuning van symbolische koppelingen.</span><span class="sxs-lookup"><span data-stu-id="ea948-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="ea948-166">Bestanden van de symbolische koppeling</span><span class="sxs-lookup"><span data-stu-id="ea948-166">Symbolic link files</span></span>

<span data-ttu-id="ea948-167">In dit voorbeeld maken we een nieuwe symbolische koppeling-bestand met de naam MySymLinkFile.txt in C:\Temp die is gekoppeld aan $pshome\profile.ps1.</span><span class="sxs-lookup"><span data-stu-id="ea948-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="ea948-168">Alle drie de voorbeelden opleveren hetzelfde resultaat.</span><span class="sxs-lookup"><span data-stu-id="ea948-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="ea948-169">Symbolische koppelingsmappen</span><span class="sxs-lookup"><span data-stu-id="ea948-169">Symbolic link directories</span></span>

<span data-ttu-id="ea948-170">In dit voorbeeld maken we een nieuwe symbolische koppeling-map met de naam MySymLinkDir in C:\Temp die is gekoppeld aan de map $pshome.</span><span class="sxs-lookup"><span data-stu-id="ea948-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="ea948-171">Alle drie de voorbeelden opleveren hetzelfde resultaat.</span><span class="sxs-lookup"><span data-stu-id="ea948-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="ea948-172">Vaste koppelingen</span><span class="sxs-lookup"><span data-stu-id="ea948-172">Hard links</span></span>

<span data-ttu-id="ea948-173">De dezelfde combinaties van **pad** en **naam** toegestaan, zoals hierboven beschreven.</span><span class="sxs-lookup"><span data-stu-id="ea948-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="ea948-174">Directory-koppelingen</span><span class="sxs-lookup"><span data-stu-id="ea948-174">Directory junctions</span></span>

<span data-ttu-id="ea948-175">De dezelfde combinaties van **pad** en **naam** toegestaan, zoals hierboven beschreven.</span><span class="sxs-lookup"><span data-stu-id="ea948-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="ea948-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="ea948-176">Get-ChildItem</span></span>

<span data-ttu-id="ea948-177">`Get-ChildItem` een 'l' wordt nu weergegeven de **modus** eigenschap om aan te geven van een symbolische koppelingsbestand of map.</span><span class="sxs-lookup"><span data-stu-id="ea948-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="ea948-178">Item verwijderen</span><span class="sxs-lookup"><span data-stu-id="ea948-178">Remove-Item</span></span>

<span data-ttu-id="ea948-179">Symbolische koppelingen verwijderen werkt net als elk ander itemtype verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ea948-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="ea948-180">Gebruik de **Force** parameter voor het verwijderen van de bestanden in de doelmap en de symbolische koppeling.</span><span class="sxs-lookup"><span data-stu-id="ea948-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="ea948-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="ea948-181">New-TemporaryFile</span></span>

<span data-ttu-id="ea948-182">Soms moet u een tijdelijk bestand maken in uw scripts.</span><span class="sxs-lookup"><span data-stu-id="ea948-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="ea948-183">U kunt nu doet dit met de `New-TemporaryFile` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="ea948-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="ea948-184">Beheer van netwerkswitch met PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea948-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="ea948-185">De netwerkswitch-cmdlets die zijn geïntroduceerd in WMF 5.0, kunt u switch, virtuele LAN (VLAN) en basic Layer 2-switch-poort netwerkconfiguratie toepassen op Windows Server 2012 R2-logo gecertificeerde netwerkswitches.</span><span class="sxs-lookup"><span data-stu-id="ea948-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="ea948-186">Met deze cmdlets die u kunt uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="ea948-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="ea948-187">Globale switch configuratie, zoals:</span><span class="sxs-lookup"><span data-stu-id="ea948-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="ea948-188">Set-hostnaam</span><span class="sxs-lookup"><span data-stu-id="ea948-188">Set host name</span></span>
  - <span data-ttu-id="ea948-189">Set-switch banner</span><span class="sxs-lookup"><span data-stu-id="ea948-189">Set switch banner</span></span>
  - <span data-ttu-id="ea948-190">Configuratie blijven behouden</span><span class="sxs-lookup"><span data-stu-id="ea948-190">Persist configuration</span></span>
  - <span data-ttu-id="ea948-191">Functie- of uitschakelen</span><span class="sxs-lookup"><span data-stu-id="ea948-191">Enable or disable feature</span></span>

- <span data-ttu-id="ea948-192">VLAN-configuratie:</span><span class="sxs-lookup"><span data-stu-id="ea948-192">VLAN configuration:</span></span>
  - <span data-ttu-id="ea948-193">Maken of verwijderen van VLAN</span><span class="sxs-lookup"><span data-stu-id="ea948-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="ea948-194">In- of uitschakelen van VLAN</span><span class="sxs-lookup"><span data-stu-id="ea948-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="ea948-195">VLAN opsommen</span><span class="sxs-lookup"><span data-stu-id="ea948-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="ea948-196">Beschrijvende naam van de set met een VLAN</span><span class="sxs-lookup"><span data-stu-id="ea948-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="ea948-197">Configuratie van de laag-2-poort:</span><span class="sxs-lookup"><span data-stu-id="ea948-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="ea948-198">Poorten inventariseren</span><span class="sxs-lookup"><span data-stu-id="ea948-198">Enumerate ports</span></span>
  - <span data-ttu-id="ea948-199">In- of uitschakelen van poorten</span><span class="sxs-lookup"><span data-stu-id="ea948-199">Enable or disable ports</span></span>
  - <span data-ttu-id="ea948-200">Set-poort-modi en eigenschappen</span><span class="sxs-lookup"><span data-stu-id="ea948-200">Set port modes and properties</span></span>
  - <span data-ttu-id="ea948-201">Toevoegen of koppelen van de VLAN Trunk of toegang op de poort</span><span class="sxs-lookup"><span data-stu-id="ea948-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="ea948-202">Zie voor meer informatie de [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentatie.</span><span class="sxs-lookup"><span data-stu-id="ea948-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="ea948-203">PowerShell-cmdlets op basis van een OData-eindpunt met ODataUtils genereren</span><span class="sxs-lookup"><span data-stu-id="ea948-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="ea948-204">De module ODataUtils kunt genereren van PowerShell-cmdlets van REST-eindpunten die ondersteuning bieden voor OData.</span><span class="sxs-lookup"><span data-stu-id="ea948-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="ea948-205">De module Microsoft.PowerShell.ODataUtils bevat de volgende functies:</span><span class="sxs-lookup"><span data-stu-id="ea948-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="ea948-206">Aanvullende informatie van server-side-eindpunt voor client-side-Channel.</span><span class="sxs-lookup"><span data-stu-id="ea948-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="ea948-207">Client-side-ondersteuning voor paginering</span><span class="sxs-lookup"><span data-stu-id="ea948-207">Client-side paging support</span></span>
- <span data-ttu-id="ea948-208">Serverzijde filteren met behulp van de - Select-parameters</span><span class="sxs-lookup"><span data-stu-id="ea948-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="ea948-209">Ondersteuning voor web-aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ea948-209">Support for web request headers</span></span>

<span data-ttu-id="ea948-210">De proxy-cmdlets die worden gegenereerd door de `Export-ODataEndPointProxy` cmdlet bevatten aanvullende informatie van het eindpunt van de OData-serverzijde op de **informatie** stream.</span><span class="sxs-lookup"><span data-stu-id="ea948-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="ea948-211">In het volgende voorbeeld zijn we bij het ophalen van de beste product en het vastleggen van de uitvoer in de `$infoStream` variabele.</span><span class="sxs-lookup"><span data-stu-id="ea948-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="ea948-212">Door op te geven **IncludeTotalResponseCount** parameter, krijgen we het totale aantal van alle de **Product** records beschikbaar op de server.</span><span class="sxs-lookup"><span data-stu-id="ea948-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="ea948-213">U kunt de records van de server in batches met behulp van de client-side-ondersteuning voor paginering ophalen.</span><span class="sxs-lookup"><span data-stu-id="ea948-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="ea948-214">Dit is handig als u een grote hoeveelheid gegevens uit de server via het netwerk ophalen moet.</span><span class="sxs-lookup"><span data-stu-id="ea948-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="ea948-215">De gegenereerde proxy-cmdlets bieden ondersteuning voor de **Selecteer** parameter die wordt gebruikt als een filter voor het ontvangen van de recordeigenschappen die de client nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="ea948-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="ea948-216">Het filter vindt plaats op de server, waardoor de hoeveelheid gegevens die via het netwerk wordt overgedragen.</span><span class="sxs-lookup"><span data-stu-id="ea948-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="ea948-217">De `Export-ODataEndpointProxy` -cmdlet en de webtoepassingsproxy-cmdlets die worden gegenereerd door, bieden nu ondersteuning voor de **Headers** parameter.</span><span class="sxs-lookup"><span data-stu-id="ea948-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="ea948-218">De header kan worden gebruikt om aanvullende informatie die wordt verwacht door het OData-eindpunt-channel.</span><span class="sxs-lookup"><span data-stu-id="ea948-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="ea948-219">In het volgende voorbeeld wordt een hash-tabel met de abonnementssleutel van een wordt geleverd aan de **Headers** parameter.</span><span class="sxs-lookup"><span data-stu-id="ea948-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="ea948-220">Dit is een typisch voorbeeld voor services die een abonnementssleutel voor verificatie verwacht.</span><span class="sxs-lookup"><span data-stu-id="ea948-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
