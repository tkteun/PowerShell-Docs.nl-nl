---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Nieuwe en bijgewerkte cmdlets
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145024"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="dd7ab-103">Nieuwe en bijgewerkte cmdlets</span><span class="sxs-lookup"><span data-stu-id="dd7ab-103">New and updated cmdlets</span></span>

<span data-ttu-id="dd7ab-104">We hebben nieuwe en bijgewerkte bestaande cmdlets toegevoegd op basis van feedback van de community.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="dd7ab-105">Archief-cmdlets</span><span class="sxs-lookup"><span data-stu-id="dd7ab-105">Archive cmdlets</span></span>

<span data-ttu-id="dd7ab-106">`Compress-Archive` Met twee nieuwe cmdlets en `Expand-Archive`kunt u zip-bestanden comprimeren en uitvouwen.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="dd7ab-107">Zie de documentatie over de module [micro soft. Power shell. Archive](/powershell/module/microsoft.powershell.archive/) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="dd7ab-108">Catalogus-cmdlets</span><span class="sxs-lookup"><span data-stu-id="dd7ab-108">Catalog Cmdlets</span></span>

<span data-ttu-id="dd7ab-109">Er zijn twee nieuwe cmdlets toegevoegd in de module micro soft. Power shell. Security.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="dd7ab-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="dd7ab-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="dd7ab-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="dd7ab-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="dd7ab-112">Deze genereren en valideren Windows-catalogus bestanden.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="dd7ab-113">Klembord-cmdlets</span><span class="sxs-lookup"><span data-stu-id="dd7ab-113">Clipboard cmdlets</span></span>

<span data-ttu-id="dd7ab-114">`Get-Clipboard`en `Set-Clipboard` Maak het eenvoudiger voor u om inhoud over te dragen van en naar een Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="dd7ab-115">De Klembord-cmdlets ondersteunen installatie kopieën, audio bestanden, bestands lijsten en tekst.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="dd7ab-116">Zie voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="dd7ab-116">For more information, see:</span></span>

- [<span data-ttu-id="dd7ab-117">Get-klem bord</span><span class="sxs-lookup"><span data-stu-id="dd7ab-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="dd7ab-118">Set-klem bord</span><span class="sxs-lookup"><span data-stu-id="dd7ab-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="dd7ab-119">Cmdlets voor cryptografische bericht syntaxis (CMS)</span><span class="sxs-lookup"><span data-stu-id="dd7ab-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="dd7ab-120">De syntaxis cmdlets van cryptografische berichten ondersteunen de versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor het cryptografisch beveiligen van berichten zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="dd7ab-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="dd7ab-121">De CMS Encryption Standard implementeert open bare-sleutel cryptografie, waarbij de sleutel die wordt gebruikt voor het versleutelen van inhoud (de *open bare sleutel*) en de sleutel die wordt gebruikt voor het ontsleutelen van inhoud (de *persoonlijke sleutel*), gescheiden zijn.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="dd7ab-122">Uw open bare sleutel kan algemeen worden gedeeld en bevat geen gevoelige gegevens.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="dd7ab-123">Alle inhoud die is versleuteld met de open bare sleutel kan alleen worden ontsleuteld met de persoonlijke sleutel.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="dd7ab-124">Zie voor meer informatie [open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="dd7ab-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="dd7ab-125">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-125">For more information see:</span></span>

- [<span data-ttu-id="dd7ab-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="dd7ab-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="dd7ab-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="dd7ab-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="dd7ab-128">Beveiliging opheffen-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="dd7ab-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="dd7ab-129">Certificaten vereisen een unieke sleutel gebruiks-id (EKU), zoals ' hand tekening bij programma code ' of ' versleutelde E-mail ', om ze te identificeren als certificaten voor gegevens versleuteling in Power shell.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="dd7ab-130">Als u certificaten voor document versleuteling in de certificaat provider wilt weer geven, kunt u de para `Get-ChildItem`meter DocumentEncryptionCert Dynamic gebruiken van:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="dd7ab-131">Gestructureerde objecten uit teken reeks inhoud extra heren en parseren</span><span class="sxs-lookup"><span data-stu-id="dd7ab-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="dd7ab-132">ConvertFrom-teken reeks</span><span class="sxs-lookup"><span data-stu-id="dd7ab-132">ConvertFrom-String</span></span>

<span data-ttu-id="dd7ab-133">De nieuwe `ConvertFrom-String` cmdlet ondersteunt twee modi:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="dd7ab-134">Basis delimite parsering</span><span class="sxs-lookup"><span data-stu-id="dd7ab-134">Basic delimited parsing</span></span>
- <span data-ttu-id="dd7ab-135">Automatisch gegenereerd voor beeld-aangedreven parsering</span><span class="sxs-lookup"><span data-stu-id="dd7ab-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="dd7ab-136">Met een scheidings teken voor het parseren wordt standaard de invoer gesplitst in witruimte en worden eigenschapnamen toegewezen aan de resulterende groepen.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="dd7ab-137">De **UpdateTemplate** para meter slaat de resultaten van het leer algoritme op in een opmerking in het sjabloon bestand.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="dd7ab-138">Dit maakt het leer proces (het langzaamste stadium) één eenmalige kosten.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="dd7ab-139">Het `ConvertFrom-String` uitvoeren van een sjabloon die het algoritme voor gecodeerde lessen bevat, is nu bijna direct.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="dd7ab-140">Zie [ConvertFrom-string (](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String)Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="dd7ab-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="dd7ab-141">Convert-String</span></span>

<span data-ttu-id="dd7ab-142">`Convert-String`Hiermee kunt u vóór en na voor beelden opgeven hoe tekst eruit moet zien.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="dd7ab-143">De cmdlet formatteert uw tekst automatisch.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="dd7ab-144">Zie [Convert-string](/powershell/module/Microsoft.PowerShell.Utility/Convert-String)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="dd7ab-145">Updates voor FileInfo-object</span><span class="sxs-lookup"><span data-stu-id="dd7ab-145">Updates to FileInfo object</span></span>

<span data-ttu-id="dd7ab-146">Informatie over de bestands versie kan misleidend zijn, met name in gevallen waarin het bestand is gerepareerd.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="dd7ab-147">WMF 5,0 voegt nieuwe **FileVersionRaw** -en **ProductVersionRaw** -script eigenschappen toe aan **file info** -objecten.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="dd7ab-148">Dit zijn de eigenschappen die worden weer gegeven voor Power shell. exe (ervan uitgaande dat $pid de ID is van het Power Shell-proces):</span><span class="sxs-lookup"><span data-stu-id="dd7ab-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="dd7ab-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="dd7ab-149">Format-Hex</span></span>

<span data-ttu-id="dd7ab-150">`Format-Hex`Hiermee kunt u tekst of binaire gegevens in hexadecimale indeling weer geven.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="dd7ab-151">Zie [Format-hex](/powershell/module/microsoft.powershell.utility/format-hex)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="dd7ab-152">Get-Child item heeft para meter-Depth</span><span class="sxs-lookup"><span data-stu-id="dd7ab-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="dd7ab-153">`Get-ChildItem`heeft nu een **diepte** parameter voor gebruik met **recursie** om de recursie te beperken:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="dd7ab-154">Modules ondersteunen voor het declareren van versie bereiken (1. \*, etc.)</span><span class="sxs-lookup"><span data-stu-id="dd7ab-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="dd7ab-155">U kunt nu **MinimumVersion** en **MaximumVersion** combi neren om module te importeren binnen een bepaald bereik.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="dd7ab-156">De para meters ondersteunen ook joker tekens.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-156">The parameters also support wildcards.</span></span>

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

## <a name="new-guid"></a><span data-ttu-id="dd7ab-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="dd7ab-157">New-Guid</span></span>

<span data-ttu-id="dd7ab-158">Er zijn veel scenario's waarbij youneed voor een unieke id.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="dd7ab-159">De `New-GUID` cmdlet biedt een eenvoudige manier om een nieuwe GUID te maken.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="dd7ab-160">De para meter voor een nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="dd7ab-160">NoNewLine parameter</span></span>

<span data-ttu-id="dd7ab-161">`Out-File`, `Add-Content`en `Set-Content` nu een nieuwe optie voor het wijzigen van een nieuwe **nieuwe** regel, waardoor er na de uitvoer niet meer wordt gelaat.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="dd7ab-162">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="dd7ab-163">Zonder dat de **nieuwe** regel wordt opgegeven, zou elk fragment op een afzonderlijke regel staan:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

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

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="dd7ab-164">Communiceren met symbolische koppelingen met verbeterde item-cmdlets</span><span class="sxs-lookup"><span data-stu-id="dd7ab-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="dd7ab-165">De cmdlet item en enkele verwante cmdlets zijn uitgebreid ter ondersteuning van symbolische koppelingen.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="dd7ab-166">Symbolische koppelings bestanden</span><span class="sxs-lookup"><span data-stu-id="dd7ab-166">Symbolic link files</span></span>

<span data-ttu-id="dd7ab-167">In dit voor beeld maken we een nieuw symbolische koppelings bestand met de naam MySymLinkFile. txt in C:\Temp dat is gekoppeld aan $pshome \profile.ps1.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="dd7ab-168">Alle drie de voor beelden produceren hetzelfde resultaat.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="dd7ab-169">Symbolische koppelings mappen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-169">Symbolic link directories</span></span>

<span data-ttu-id="dd7ab-170">In dit voor beeld maken we een nieuwe symbolische koppeling map met de naam MySymLinkDir in C:\Temp die aan de $pshome map is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="dd7ab-171">Alle drie de voor beelden produceren hetzelfde resultaat.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="dd7ab-172">Vaste koppelingen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-172">Hard links</span></span>

<span data-ttu-id="dd7ab-173">Dezelfde combi Naties van **pad** en **naam** zijn toegestaan zoals hierboven is beschreven.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="dd7ab-174">Adreslijst koppelingen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-174">Directory junctions</span></span>

<span data-ttu-id="dd7ab-175">Dezelfde combi Naties van **pad** en **naam** zijn toegestaan zoals hierboven is beschreven.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="dd7ab-176">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="dd7ab-176">Get-ChildItem</span></span>

<span data-ttu-id="dd7ab-177">`Get-ChildItem`in wordt nu een ' l ' weer gegeven in de eigenschap **mode** om een symbolische koppelings bestand of-map aan te geven.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

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

### <a name="remove-item"></a><span data-ttu-id="dd7ab-178">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="dd7ab-178">Remove-Item</span></span>

<span data-ttu-id="dd7ab-179">Het verwijderen van symbolische koppelingen werkt zoals bij het verwijderen van een ander item type.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="dd7ab-180">Gebruik de para meter **Force** om de bestanden in de doel directory en de symbolische koppeling te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="dd7ab-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="dd7ab-181">New-TemporaryFile</span></span>

<span data-ttu-id="dd7ab-182">Soms moet u in uw scripts een tijdelijk bestand maken.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="dd7ab-183">U kunt dit nu doen met de `New-TemporaryFile` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="dd7ab-184">Beheer van netwerkswitch met PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd7ab-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="dd7ab-185">Met de netwerk switch-cmdlets, die zijn geïntroduceerd in WMF 5,0, kunt u switch, virtuele LAN (VLAN) en elementaire laag 2-netwerk switch poort configuratie Toep assen op Windows Server 2012 R2 logo-gecertificeerde netwerk switches.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="dd7ab-186">Met deze cmdlets kunt u het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="dd7ab-187">Algemene switch configuratie, zoals:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="dd7ab-188">Hostnaam instellen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-188">Set host name</span></span>
  - <span data-ttu-id="dd7ab-189">Banner voor switch instellen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-189">Set switch banner</span></span>
  - <span data-ttu-id="dd7ab-190">Configuratie behouden</span><span class="sxs-lookup"><span data-stu-id="dd7ab-190">Persist configuration</span></span>
  - <span data-ttu-id="dd7ab-191">Functie in-of uitschakelen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-191">Enable or disable feature</span></span>

- <span data-ttu-id="dd7ab-192">VLAN-configuratie:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-192">VLAN configuration:</span></span>
  - <span data-ttu-id="dd7ab-193">VLAN maken of verwijderen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="dd7ab-194">VLAN in-of uitschakelen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="dd7ab-195">VLAN opsommen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="dd7ab-196">Beschrijvende naam voor een VLAN instellen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="dd7ab-197">Configuratie van laag 2-poort:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="dd7ab-198">Poorten opsommen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-198">Enumerate ports</span></span>
  - <span data-ttu-id="dd7ab-199">Poorten in-of uitschakelen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-199">Enable or disable ports</span></span>
  - <span data-ttu-id="dd7ab-200">Poort modi en eigenschappen instellen</span><span class="sxs-lookup"><span data-stu-id="dd7ab-200">Set port modes and properties</span></span>
  - <span data-ttu-id="dd7ab-201">VLAN toevoegen aan of koppelen aan de trunk of toegang op de poort</span><span class="sxs-lookup"><span data-stu-id="dd7ab-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="dd7ab-202">Zie de [NetworkSwitchManager](/powershell/module/networkswitchmanager/) -documentatie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="dd7ab-203">Power shell-cmdlets genereren op basis van een OData-eind punt met ODataUtils</span><span class="sxs-lookup"><span data-stu-id="dd7ab-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="dd7ab-204">Met de ODataUtils-module kunnen Power shell-cmdlets van REST-eind punten worden gegenereerd die OData ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="dd7ab-205">De module micro soft. Power shell. ODataUtils bevat de volgende functies:</span><span class="sxs-lookup"><span data-stu-id="dd7ab-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="dd7ab-206">Meer informatie over het kanaal aan aan de client zijde van het eind punt van de server.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="dd7ab-207">Ondersteuning voor paginering aan client zijde</span><span class="sxs-lookup"><span data-stu-id="dd7ab-207">Client-side paging support</span></span>
- <span data-ttu-id="dd7ab-208">Filters aan de server zijde met behulp van de para meter-Select</span><span class="sxs-lookup"><span data-stu-id="dd7ab-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="dd7ab-209">Ondersteuning voor webaanvraag headers</span><span class="sxs-lookup"><span data-stu-id="dd7ab-209">Support for web request headers</span></span>

<span data-ttu-id="dd7ab-210">De proxy-cmdlets die door `Export-ODataEndPointProxy` de cmdlet worden gegenereerd, bieden aanvullende informatie van het OData-eind punt aan de server zijde in de **informatie** stroom.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="dd7ab-211">In het volgende voor beeld wordt het beste product opgehaald en wordt de uitvoer in de `$infoStream` variabele vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="dd7ab-212">Door de para meter **IncludeTotalResponseCount** op te geven, wordt het totale aantal beschik bare **product** records op de server opgehaald.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="dd7ab-213">U kunt de records ophalen van de server in batches met de ondersteuning voor paginering aan client zijde.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="dd7ab-214">Dit is handig wanneer u een grote hoeveelheid gegevens van de server via het netwerk moet verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="dd7ab-215">De gegenereerde proxy-cmdlets ondersteunen de **Select** -para meter die wordt gebruikt als filter om alleen de record eigenschappen te ontvangen die de client nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="dd7ab-216">Het filter vindt plaats op de server, waardoor de hoeveelheid gegevens die via het netwerk wordt overgedragen, kleiner wordt.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="dd7ab-217">De `Export-ODataEndpointProxy` cmdlet en de proxy-cmdlets die door worden gegenereerd, ondersteunen nu de para meter **headers** .</span><span class="sxs-lookup"><span data-stu-id="dd7ab-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="dd7ab-218">De header kan worden gebruikt om aanvullende informatie die wordt verwacht door het OData-eind punt te kanaal te kanalen.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="dd7ab-219">In het volgende voor beeld wordt een hash-tabel met een abonnements sleutel aan de para meter **headers** door gegeven.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="dd7ab-220">Dit is een typisch voor beeld van services waarvoor een abonnements sleutel voor verificatie wordt verwacht.</span><span class="sxs-lookup"><span data-stu-id="dd7ab-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
