---
description: Hierin wordt beschreven hoe teken codering in Power shell wordt gebruikt voor invoer en uitvoer van teken reeks gegevens.
Locale: en-US
ms.date: 10/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Character_Encoding
ms.openlocfilehash: 48a33903bd44db68a3c581183f83ec23ea97161a
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96349802"
---
# <a name="about_character_encoding"></a><span data-ttu-id="dc3e3-103">about_Character_Encoding</span><span class="sxs-lookup"><span data-stu-id="dc3e3-103">about_Character_Encoding</span></span>

## <a name="short-description"></a><span data-ttu-id="dc3e3-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="dc3e3-104">Short description</span></span>
<span data-ttu-id="dc3e3-105">Hierin wordt beschreven hoe teken codering in Power shell wordt gebruikt voor invoer en uitvoer van teken reeks gegevens.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-105">Describes how PowerShell uses character encoding for input and output of string data.</span></span>

## <a name="long-description"></a><span data-ttu-id="dc3e3-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="dc3e3-106">Long description</span></span>

<span data-ttu-id="dc3e3-107">Unicode is een wereld wijde teken coderings standaard.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-107">Unicode is a worldwide character-encoding standard.</span></span> <span data-ttu-id="dc3e3-108">Het systeem gebruikt Unicode uitsluitend voor teken-en teken reeks manipulatie.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-108">The system uses Unicode exclusively for character and string manipulation.</span></span> <span data-ttu-id="dc3e3-109">Raadpleeg [de Unicode-standaard](https://www.unicode.org/standard/standard.html)voor een gedetailleerde beschrijving van alle aspecten van Unicode.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-109">For a detailed description of all aspects of Unicode, refer to [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>

<span data-ttu-id="dc3e3-110">Windows ondersteunt Unicode-en traditionele teken sets.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-110">Windows supports Unicode and traditional character sets.</span></span> <span data-ttu-id="dc3e3-111">Traditionele teken sets, zoals Windows-code pagina's, gebruiken 8-bits waarden of combi Naties van 8-bits waarden om de tekens weer te geven die worden gebruikt in een specifieke taal of instellingen voor geografische regio's.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-111">Traditional character sets, such as Windows code pages, use 8-bit values or combinations of 8-bit values to represent the characters used in a specific language or geographical region settings.</span></span>

<span data-ttu-id="dc3e3-112">Power Shell maakt standaard gebruik van een Unicode-tekenset.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-112">PowerShell uses a Unicode character set by default.</span></span> <span data-ttu-id="dc3e3-113">Meerdere cmdlets hebben echter een **Encoding** -para meter waarmee u code ring kunt opgeven voor een andere tekenset.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-113">However, several cmdlets have an **Encoding** parameter that can specify encoding for a different character set.</span></span> <span data-ttu-id="dc3e3-114">Met deze para meter kunt u de specifieke teken codering kiezen die u nodig hebt voor interoperabiliteit met andere systemen en toepassingen.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-114">This parameter allows you to choose the specific the character encoding you need for interoperability with other systems and applications.</span></span>

<span data-ttu-id="dc3e3-115">De volgende cmdlets hebben de para meter **Encoding** :</span><span class="sxs-lookup"><span data-stu-id="dc3e3-115">The following cmdlets have the **Encoding** parameter:</span></span>

- <span data-ttu-id="dc3e3-116">Micro soft. Power shell. Management</span><span class="sxs-lookup"><span data-stu-id="dc3e3-116">Microsoft.PowerShell.Management</span></span>
  - <span data-ttu-id="dc3e3-117">Add-Content</span><span class="sxs-lookup"><span data-stu-id="dc3e3-117">Add-Content</span></span>
  - <span data-ttu-id="dc3e3-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="dc3e3-118">Get-Content</span></span>
  - <span data-ttu-id="dc3e3-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="dc3e3-119">Set-Content</span></span>
- <span data-ttu-id="dc3e3-120">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="dc3e3-120">Microsoft.PowerShell.Utility</span></span>
  - <span data-ttu-id="dc3e3-121">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="dc3e3-121">Export-Clixml</span></span>
  - <span data-ttu-id="dc3e3-122">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="dc3e3-122">Export-Csv</span></span>
  - <span data-ttu-id="dc3e3-123">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="dc3e3-123">Export-PSSession</span></span>
  - <span data-ttu-id="dc3e3-124">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="dc3e3-124">Format-Hex</span></span>
  - <span data-ttu-id="dc3e3-125">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="dc3e3-125">Import-Csv</span></span>
  - <span data-ttu-id="dc3e3-126">Out-File</span><span class="sxs-lookup"><span data-stu-id="dc3e3-126">Out-File</span></span>
  - <span data-ttu-id="dc3e3-127">Select-String</span><span class="sxs-lookup"><span data-stu-id="dc3e3-127">Select-String</span></span>
  - <span data-ttu-id="dc3e3-128">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="dc3e3-128">Send-MailMessage</span></span>

## <a name="the-byte-order-mark"></a><span data-ttu-id="dc3e3-129">De byte volgorde markering</span><span class="sxs-lookup"><span data-stu-id="dc3e3-129">The byte-order-mark</span></span>

<span data-ttu-id="dc3e3-130">De byte-order-Mark (BOM) is een _Unicode-hand tekening_ in de eerste paar bytes van een bestand of tekst stroom die aangeeft welke Unicode-code ring voor de gegevens wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-130">The byte-order-mark (BOM) is a _Unicode signature_ in the first few bytes of a file or text stream that indicate which Unicode encoding used for the data.</span></span> <span data-ttu-id="dc3e3-131">Zie de documentatie over de [Byte Order Mark](/globalization/encoding/byte-order-mark) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-131">For more information, see the [Byte order mark](/globalization/encoding/byte-order-mark) documentation.</span></span>

<span data-ttu-id="dc3e3-132">In Windows Power Shell maakt Unicode-code ring, behalve `UTF7` , altijd een stuk lijst.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-132">In Windows PowerShell, any Unicode encoding, except `UTF7`, always creates a BOM.</span></span> <span data-ttu-id="dc3e3-133">Power shell core wordt standaard ingesteld op `utf8NoBOM` alle tekst uitvoer.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-133">PowerShell Core defaults to `utf8NoBOM` for all text output.</span></span>

<span data-ttu-id="dc3e3-134">Voor de beste algemene compatibiliteit kunt u geen stuk lijsten gebruiken in UTF-8-bestanden.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-134">For best overall compatibility, avoid using BOMs in UTF-8 files.</span></span> <span data-ttu-id="dc3e3-135">UNIX-platforms en UNIX-erfgoed-hulpprogram ma's die ook worden gebruikt op Windows-platforms ondersteunen geen stuk lijsten.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-135">Unix platforms and Unix-heritage utilities also used on Windows Platforms don't support BOMs.</span></span>

<span data-ttu-id="dc3e3-136">Op dezelfde manier `UTF7` moet de code ring worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-136">Similarly, `UTF7` encoding should be avoided.</span></span> <span data-ttu-id="dc3e3-137">UTF-7 is geen standaard Unicode-code ring en wordt zonder een stuk lijst in alle versies van Power shell geschreven.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-137">UTF-7 is not a standard Unicode encoding and is written without a BOM in all versions of PowerShell.</span></span>

<span data-ttu-id="dc3e3-138">Het maken van Power shell-scripts op een UNIX-soortgelijk platform of het gebruik van een platformoverschrijdende editor in Windows, zoals Visual Studio code, resulteert in een bestand dat is gecodeerd met `UTF8NoBOM` .</span><span class="sxs-lookup"><span data-stu-id="dc3e3-138">Creating PowerShell scripts on a Unix-like platform or using a cross-platform editor on Windows, such as Visual Studio Code, results in a file encoded using `UTF8NoBOM`.</span></span> <span data-ttu-id="dc3e3-139">Deze bestanden werken prima op Power shell core, maar kunnen in Windows Power shell worden verbroken als het bestand niet-ASCII-tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-139">These files work fine on PowerShell Core, but may break in Windows PowerShell if the file contains non-Ascii characters.</span></span>

<span data-ttu-id="dc3e3-140">Als u niet-ASCII-tekens in uw scripts moet gebruiken, slaat u ze op als UTF-8 met een stuk lijst.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-140">If you need to use non-Ascii characters in your scripts, save them as UTF-8 with BOM.</span></span> <span data-ttu-id="dc3e3-141">Zonder de stuk lijst interpreteert Windows Power shell uw script niet op dezelfde manier als in de verouderde code ring ' ANSI '.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-141">Without the BOM, Windows PowerShell misinterprets your script as being encoded in the legacy "ANSI" codepage.</span></span> <span data-ttu-id="dc3e3-142">Daarentegen kunnen bestanden met de UTF-8-stuk lijst problemen ondervinden op UNIX-achtige platformen.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-142">Conversely, files that do have the UTF-8 BOM can be problematic on Unix-like platforms.</span></span> <span data-ttu-id="dc3e3-143">Veel Unix-hulpprogram ma's zoals `cat` ,, `sed` `awk` en sommige editors, zoals `gedit` weet niet hoe de stuk lijst moet worden behandeld.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-143">Many Unix tools such as `cat`, `sed`, `awk`, and some editors such as `gedit` don't know how to treat the BOM.</span></span>

## <a name="character-encoding-in-windows-powershell"></a><span data-ttu-id="dc3e3-144">Teken codering in Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="dc3e3-144">Character encoding in Windows PowerShell</span></span>

<span data-ttu-id="dc3e3-145">In Power shell 5,1 ondersteunt de para meter **Encoding** de volgende waarden:</span><span class="sxs-lookup"><span data-stu-id="dc3e3-145">In PowerShell 5.1, the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="dc3e3-146">`Ascii` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="dc3e3-146">`Ascii` Uses Ascii (7-bit) character set.</span></span>
- <span data-ttu-id="dc3e3-147">`BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-147">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="dc3e3-148">`BigEndianUTF32` Maakt gebruik van UTF-32 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-148">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="dc3e3-149">`Byte` Codeert een reeks tekens in een reeks bytes.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-149">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="dc3e3-150">`Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).</span><span class="sxs-lookup"><span data-stu-id="dc3e3-150">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="dc3e3-151">`Oem` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-151">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="dc3e3-152">`String` Hetzelfde als `Unicode` .</span><span class="sxs-lookup"><span data-stu-id="dc3e3-152">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="dc3e3-153">`Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-153">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="dc3e3-154">`Unknown` Hetzelfde als `Unicode` .</span><span class="sxs-lookup"><span data-stu-id="dc3e3-154">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="dc3e3-155">`UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-155">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>
- <span data-ttu-id="dc3e3-156">`UTF7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-156">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="dc3e3-157">`UTF8` Maakt gebruik van UTF-8 (met stuk lijst).</span><span class="sxs-lookup"><span data-stu-id="dc3e3-157">`UTF8` Uses UTF-8 (with BOM).</span></span>

<span data-ttu-id="dc3e3-158">In het algemeen maakt Windows Power Shell standaard gebruik van de Unicode [UTF-16LE-](https://wikipedia.org/wiki/UTF-16) code ring.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-158">In general, Windows PowerShell uses the Unicode [UTF-16LE](https://wikipedia.org/wiki/UTF-16) encoding by default.</span></span> <span data-ttu-id="dc3e3-159">De standaard codering die door cmdlets in Windows Power shell wordt gebruikt, is echter niet consistent.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-159">However, the default encoding used by cmdlets in Windows PowerShell is not consistent.</span></span>

> [!NOTE]
> <span data-ttu-id="dc3e3-160">Het gebruik van Unicode-code ring, behalve `UTF7` , maakt altijd een stuk lijst.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-160">Using any Unicode encoding, except `UTF7`, always creates a BOM.</span></span>

<span data-ttu-id="dc3e3-161">Voor cmdlets die uitvoer naar bestanden schrijven:</span><span class="sxs-lookup"><span data-stu-id="dc3e3-161">For cmdlets that write output to files:</span></span>

- <span data-ttu-id="dc3e3-162">`Out-File` en de omleidings operatoren `>` en `>>` maken UTF-16LE, die met name afwijken van `Set-Content` en `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="dc3e3-162">`Out-File` and the redirection operators `>` and `>>` create UTF-16LE, which notably differs from `Set-Content` and `Add-Content`.</span></span>

- <span data-ttu-id="dc3e3-163">`New-ModuleManifest` en `Export-CliXml` maken ook UTF-16LE-bestanden.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-163">`New-ModuleManifest` and `Export-CliXml` also create UTF-16LE files.</span></span>

- <span data-ttu-id="dc3e3-164">Wanneer het doel bestand leeg is of niet bestaat, `Set-Content` en `Add-Content` gebruikmaakt van `Default` code ring.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-164">When the target file is empty or doesn't exist, `Set-Content` and `Add-Content` use `Default` encoding.</span></span> <span data-ttu-id="dc3e3-165">`Default` is de code ring die is opgegeven door de ANSI legacy-code tabel van het actieve systeem.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-165">`Default` is the encoding specified by the active system locale's ANSI legacy code page.</span></span>

- <span data-ttu-id="dc3e3-166">`Export-Csv` Hiermee maakt `Ascii` u bestanden, maar gebruikt u een andere code ring wanneer u **Append** para meter gebruikt (zie hieronder).</span><span class="sxs-lookup"><span data-stu-id="dc3e3-166">`Export-Csv` creates `Ascii` files but uses different encoding when using **Append** parameter (see below).</span></span>

- <span data-ttu-id="dc3e3-167">`Export-PSSession` maakt standaard UTF-8-bestanden met een stuk lijst.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-167">`Export-PSSession` creates UTF-8 files with BOM by default.</span></span>

- <span data-ttu-id="dc3e3-168">`New-Item -Type File -Value` Hiermee maakt u een stuk lijst zonder UTF-8-bestand.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-168">`New-Item -Type File -Value` creates a BOM-less UTF-8 file.</span></span>

- <span data-ttu-id="dc3e3-169">`Send-MailMessage` maakt gebruik `Default` van code ring standaard.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-169">`Send-MailMessage` uses `Default` encoding by default.</span></span>

- <span data-ttu-id="dc3e3-170">`Start-Transcript` Hiermee maakt u `Utf8` bestanden met een stuk lijst.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-170">`Start-Transcript` creates `Utf8` files with a BOM.</span></span> <span data-ttu-id="dc3e3-171">Wanneer de para meter **Append** wordt gebruikt, kan de code ring verschillen (zie hieronder).</span><span class="sxs-lookup"><span data-stu-id="dc3e3-171">When the **Append** parameter is used, the encoding can be different (see below).</span></span>

<span data-ttu-id="dc3e3-172">Voor opdrachten die worden toegevoegd aan een bestaand bestand:</span><span class="sxs-lookup"><span data-stu-id="dc3e3-172">For commands that append to an existing file:</span></span>

- <span data-ttu-id="dc3e3-173">`Out-File -Append` de `>>` omleidings operator maakt geen poging om de code ring van de bestaande inhoud van het doel bestand te vergelijken.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-173">`Out-File -Append` and the `>>` redirection operator make no attempt to match the encoding of the existing target file's content.</span></span> <span data-ttu-id="dc3e3-174">In plaats daarvan gebruiken ze de standaard codering tenzij de para meter **Encoding** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-174">Instead, they use the default encoding unless the **Encoding** parameter is used.</span></span> <span data-ttu-id="dc3e3-175">U moet de bestanden originele code ring gebruiken bij het toevoegen van inhoud.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-175">You must use the files original encoding when appending content.</span></span>

- <span data-ttu-id="dc3e3-176">Als er geen expliciete **Encoding** -para meter is, `Add-Content` detecteert de bestaande code ring en past deze automatisch toe op de nieuwe inhoud.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-176">In the absence of an explicit **Encoding** parameter, `Add-Content` detects the existing encoding and automatically applies it to the new content.</span></span> <span data-ttu-id="dc3e3-177">Als de bestaande inhoud geen stuk lijst heeft, `Default` wordt ANSI-code ring gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-177">If the existing content has no BOM, `Default` ANSI encoding is used.</span></span> <span data-ttu-id="dc3e3-178">Het gedrag van `Add-Content` is hetzelfde in Power shell core (V6 en hoger), met uitzonde ring van de standaard codering `Utf8` .</span><span class="sxs-lookup"><span data-stu-id="dc3e3-178">The behavior of `Add-Content` is the same in PowerShell Core (v6 and higher) except the default encoding is `Utf8`.</span></span>

- <span data-ttu-id="dc3e3-179">`Export-Csv -Append` komt overeen met de bestaande code ring wanneer het doel bestand een stuk lijst bevat.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-179">`Export-Csv -Append` matches the existing encoding when the target file contains a BOM.</span></span> <span data-ttu-id="dc3e3-180">Als er geen stuk lijst is, wordt `Utf8` code ring gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-180">In the absence of a BOM, it uses `Utf8` encoding.</span></span>

- <span data-ttu-id="dc3e3-181">`Start-Transcript -Append` komt overeen met de bestaande code ring van bestanden die een stuk lijst bevatten.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-181">`Start-Transcript -Append` matches the existing encoding of files that include a BOM.</span></span> <span data-ttu-id="dc3e3-182">Als er geen stuk lijst wordt gebruikt, wordt de standaard waarde `Ascii` gecodeerd.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-182">In the absence of a BOM, it defaults to `Ascii` encoding.</span></span> <span data-ttu-id="dc3e3-183">Deze code ring kan leiden tot gegevens verlies of beschadiging van het teken als de gegevens in de transcripten multi byte-tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-183">This encoding can result in data loss or character corruption when the data in the transcript contains multibyte characters.</span></span>

<span data-ttu-id="dc3e3-184">Voor cmdlets die teken reeks gegevens lezen in afwezigheid van een stuk lijst:</span><span class="sxs-lookup"><span data-stu-id="dc3e3-184">For cmdlets that read string data in the absence of a BOM:</span></span>

- <span data-ttu-id="dc3e3-185">`Get-Content` en `Import-PowerShellDataFile` maakt gebruik van de `Default` ANSI-code ring.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-185">`Get-Content` and `Import-PowerShellDataFile` uses the `Default` ANSI encoding.</span></span> <span data-ttu-id="dc3e3-186">ANSI is ook wat de Power shell-engine gebruikt bij het lezen van de bron code van bestanden.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-186">ANSI is also what the PowerShell engine uses when it reads source code from files.</span></span>

- <span data-ttu-id="dc3e3-187">`Import-Csv`, `Import-CliXml` en `Select-String` ervan uitgaan dat `Utf8` er geen stuk lijst is.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-187">`Import-Csv`, `Import-CliXml`, and `Select-String` assume `Utf8` in the absence of a BOM.</span></span>

## <a name="character-encoding-in-powershell-core"></a><span data-ttu-id="dc3e3-188">Teken codering in Power shell core</span><span class="sxs-lookup"><span data-stu-id="dc3e3-188">Character encoding in PowerShell Core</span></span>

<span data-ttu-id="dc3e3-189">In Power shell core (V6 en hoger) ondersteunt de para meter **Encoding** de volgende waarden:</span><span class="sxs-lookup"><span data-stu-id="dc3e3-189">In PowerShell Core (v6 and higher), the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="dc3e3-190">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="dc3e3-190">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="dc3e3-191">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-191">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="dc3e3-192">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-192">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="dc3e3-193">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-193">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="dc3e3-194">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-194">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="dc3e3-195">`utf8`: Wordt gecodeerd in UTF-8-indeling (geen stuk lijst).</span><span class="sxs-lookup"><span data-stu-id="dc3e3-195">`utf8`: Encodes in UTF-8 format (no BOM).</span></span>
- <span data-ttu-id="dc3e3-196">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="dc3e3-196">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="dc3e3-197">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="dc3e3-197">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="dc3e3-198">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-198">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="dc3e3-199">Power shell Core is standaard ingesteld op `utf8NoBOM` alle uitvoer.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-199">PowerShell Core defaults to `utf8NoBOM` for all output.</span></span>

<span data-ttu-id="dc3e3-200">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="dc3e3-200">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="dc3e3-201">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-201">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage).</span></span>

## <a name="changing-the-default-encoding"></a><span data-ttu-id="dc3e3-202">De standaard codering wijzigen</span><span class="sxs-lookup"><span data-stu-id="dc3e3-202">Changing the default encoding</span></span>

<span data-ttu-id="dc3e3-203">Power Shell heeft twee standaard variabelen die kunnen worden gebruikt om het standaard coderings gedrag te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-203">PowerShell has two default variables that can be used to change the default encoding behavior.</span></span>

- `$PSDefaultParameterValues`
- `$OutputEncoding`

<span data-ttu-id="dc3e3-204">Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-204">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="dc3e3-205">Vanaf Power shell 5,1 roept de omleidings operator ( `>` en `>>` ) de `Out-File` cmdlet aan.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-205">Beginning in PowerShell 5.1, the redirection operators (`>` and `>>`) call the `Out-File` cmdlet.</span></span> <span data-ttu-id="dc3e3-206">Daarom kunt u de standaard codering instellen met behulp van de `$PSDefaultParameterValues` Voorkeurs variabele, zoals wordt weer gegeven in dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="dc3e3-206">Therefore, you can set the default encoding of them using the `$PSDefaultParameterValues` preference variable as shown in this example:</span></span>

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

<span data-ttu-id="dc3e3-207">Gebruik de volgende instructie om de standaard codering te wijzigen voor alle cmdlets die de para meter **Encoding** hebben.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-207">Use the following statement to change the default encoding for all cmdlets that have the **Encoding** parameter.</span></span>

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> <span data-ttu-id="dc3e3-208">Als u deze opdracht in uw Power shell-profiel plaatst, wordt de voor keur een sessie-algemene instelling die van invloed is op alle opdrachten en scripts die geen expliciete code ring opgeven.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-208">Putting this command in your PowerShell profile makes the preference a session-global setting that affects all commands and scripts that do not explicitly specify an encoding.</span></span>
>
> <span data-ttu-id="dc3e3-209">Daarnaast moet u dergelijke opdrachten in uw scripts of modules insluiten die op dezelfde manier werken.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-209">Similarly, you should include such commands in your scripts or modules that you want to behave the same way.</span></span> <span data-ttu-id="dc3e3-210">Met deze opdrachten zorgt u ervoor dat cmdlets op dezelfde manier werken, zelfs wanneer ze worden uitgevoerd door een andere gebruiker, op een andere computer of in een andere versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-210">Using these commands ensure that cmdlets behave the same way even when run by another user, on a different computer, or in a different version of PowerShell.</span></span>

<span data-ttu-id="dc3e3-211">De automatische variabele `$OutputEncoding` is van invloed op de code ring Power shell die wordt gebruikt om te communiceren met externe Program ma's.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-211">The automatic variable `$OutputEncoding` affects the encoding PowerShell uses to communicate with external programs.</span></span> <span data-ttu-id="dc3e3-212">Dit heeft geen invloed op de code ring die door de Opera tors voor uitvoer omleiding en Power shell-cmdlets wordt gebruikt om bestanden op te slaan.</span><span class="sxs-lookup"><span data-stu-id="dc3e3-212">It has no effect on the encoding that the output redirection operators and PowerShell cmdlets use to save to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc3e3-213">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dc3e3-213">See also</span></span>

- [<span data-ttu-id="dc3e3-214">Inleiding tot teken codering in .NET</span><span class="sxs-lookup"><span data-stu-id="dc3e3-214">Introduction to character encoding in .NET</span></span>](/dotnet/standard/base-types/character-encoding-introduction)
- [<span data-ttu-id="dc3e3-215">Code pagina's-Win32-apps</span><span class="sxs-lookup"><span data-stu-id="dc3e3-215">Code Pages - Win32 apps</span></span>](/windows/win32/intl/code-pages)
- [<span data-ttu-id="dc3e3-216">De Unicode-standaard</span><span class="sxs-lookup"><span data-stu-id="dc3e3-216">The Unicode Standard</span></span>](https://www.unicode.org/standard/standard.html)
- [<span data-ttu-id="dc3e3-217">Encoding. code tabel</span><span class="sxs-lookup"><span data-stu-id="dc3e3-217">Encoding.CodePage</span></span>](/dotnet/api/system.text.encoding.codepage)
- [<span data-ttu-id="dc3e3-218">UTF-16LE</span><span class="sxs-lookup"><span data-stu-id="dc3e3-218">UTF-16LE</span></span>](https://wikipedia.org/wiki/UTF-16)
- [<span data-ttu-id="dc3e3-219">Byte order markering</span><span class="sxs-lookup"><span data-stu-id="dc3e3-219">Byte order mark</span></span>](https://wikipedia.org/wiki/Byte_order_mark)
- [<span data-ttu-id="dc3e3-220">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="dc3e3-220">about_Preference_Variables</span></span>](about_Preference_Variables.md)
