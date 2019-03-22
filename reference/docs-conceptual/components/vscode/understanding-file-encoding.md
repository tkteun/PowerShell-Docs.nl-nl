---
title: Informatie over bestandscodering in VSCode en PowerShell
description: Bestandscodering in VSCode en PowerShell configureren
ms.date: 02/28/2019
ms.openlocfilehash: ec06d8f5d446a92e6cd9d2d70b11260d1d0afda8
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320401"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="7c7a7-103">Informatie over bestandscodering in VSCode en PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c7a7-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="7c7a7-104">Wanneer u VS Code gebruikt om te maken en PowerShell-scripts bewerken, is het belangrijk dat uw bestanden worden opgeslagen met behulp van de juiste tekencodering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="7c7a7-105">Wat is bestandscodering en waarom is het belangrijk?</span><span class="sxs-lookup"><span data-stu-id="7c7a7-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="7c7a7-106">VSCode beheert de interface tussen een menselijke invoeren tekenreeksen in een buffer en lezen/schrijven-blokken van bytes voor het bestandssysteem.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="7c7a7-107">Wanneer VSCode een bestand slaat, gebruikt een tekstcodering om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="7c7a7-108">Wanneer u een script wordt uitgevoerd in PowerShell moet deze ook de bytes in een bestand converteren naar tekens te reconstrueren van het bestand in een PowerShell-programma.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="7c7a7-109">Aangezien VSCode schrijft u het bestand en PowerShell het bestand leest, moeten ze het systeem met dezelfde codering gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="7c7a7-110">Deze zijn van dit proces van het parseren van een PowerShell-script: *bytes* -> *tekens* -> *tokens*  ->   *abstracte syntaxisstructuur* -> *uitvoering*.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="7c7a7-111">Zowel VSCode en PowerShell zijn geïnstalleerd met een functionele codering standaardconfiguratie.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="7c7a7-112">Echter, de standaardversleuteling gebruikt PowerShell is gewijzigd met de versie van PowerShell Core (v6.x).</span><span class="sxs-lookup"><span data-stu-id="7c7a7-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="7c7a7-113">Om ervoor te zorgen er zich geen problemen met PowerShell of de PowerShell-extensie vscode, moet u uw VSCode en PowerShell-instellingen configureren naar behoren.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="7c7a7-114">Veelvoorkomende oorzaken van problemen met codering</span><span class="sxs-lookup"><span data-stu-id="7c7a7-114">Common causes of encoding issues</span></span>

<span data-ttu-id="7c7a7-115">Codering problemen optreden wanneer de codering van VSCode of het scriptbestand komt niet overeen met de verwachte codering van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="7c7a7-116">Er is geen manier voor PowerShell om automatisch te bepalen de bestandscodering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="7c7a7-117">Hebt u waarschijnlijk meer hebben problemen-codering als u tekens die niet in de [-7-bits ASCII-tekenset](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="7c7a7-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="7c7a7-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-118">For example:</span></span>

- <span data-ttu-id="7c7a7-119">Accenten Latijnse tekens (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="7c7a7-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="7c7a7-120">Niet-Latijnse tekens zoals Cyrillisch (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="7c7a7-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="7c7a7-121">Han Chinees (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="7c7a7-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="7c7a7-122">Veelvoorkomende redenen voor het coderen van problemen zijn:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="7c7a7-123">De coderingen van VSCode en PowerShell zijn niet uit de standaardwaarden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="7c7a7-124">Voor PowerShell 5.1 en onder de standaard wijkt codering af van de VSCode zijn.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="7c7a7-125">Een andere editor is geopend en het bestand in een nieuwe codering overschreven.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="7c7a7-126">Dit gebeurt vaak met de ISE.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="7c7a7-127">Het bestand is ingeschakeld in broncodebeheer in een codering die verschilt van welke VSCode of PowerShell verwacht.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="7c7a7-128">Dit kan gebeuren wanneer de medewerkers editors met verschillende codering configuraties.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="7c7a7-129">Hoe kunt u zien wanneer u hebt coderingsproblemen</span><span class="sxs-lookup"><span data-stu-id="7c7a7-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="7c7a7-130">Vaak coderingsfouten zich presenteren als fouten in scripts parseren.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="7c7a7-131">Als u vreemd tekenreeksen in uw script kunt vinden, kan dit het probleem zijn.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="7c7a7-132">In het voorbeeld hieronder een en-streepje (`–`) wordt weergegeven als de tekens `â€“`:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="7c7a7-133">Dit probleem treedt op omdat VSCode het teken codeert `–` in UTF-8 als het aantal bytes `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="7c7a7-134">Wanneer deze bytes worden gedecodeerd als Windows-1252, worden geïnterpreteerd als de tekens `â€“`.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="7c7a7-135">Sommige vreemd tekenreeksen die u kunt tegenkomen zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-135">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="7c7a7-136">`â€“` In plaats van `–`</span><span class="sxs-lookup"><span data-stu-id="7c7a7-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="7c7a7-137">`â€”` In plaats van `—`</span><span class="sxs-lookup"><span data-stu-id="7c7a7-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="7c7a7-138">`Ã„2` In plaats van `Ä`</span><span class="sxs-lookup"><span data-stu-id="7c7a7-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="7c7a7-139">`Â` in plaats van ` ` (een vaste spatie)</span><span class="sxs-lookup"><span data-stu-id="7c7a7-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="7c7a7-140">`Ã©` In plaats van `é`</span><span class="sxs-lookup"><span data-stu-id="7c7a7-140">`Ã©` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="7c7a7-141">Binnen handbereik [verwijzing](https://www.i18nqa.com/debug/utf8-debug.html) geeft een lijst van de algemene patronen die wijzen op een probleem opgetreden bij codering UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="7c7a7-142">De interactie van de PowerShell-extensie in VSCode met coderingen</span><span class="sxs-lookup"><span data-stu-id="7c7a7-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="7c7a7-143">De extensie van PowerShell communiceert met behulp van scripts in een aantal manieren:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="7c7a7-144">Als scripts worden bewerkt in VSCode, worden de inhoud door VSCode verzonden naar de extensie.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="7c7a7-145">De [Language Server Protocol][] mandaten dat deze inhoud wordt verzonden in UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="7c7a7-146">Het is daarom niet mogelijk om de extensie te krijgen van de verkeerde codering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="7c7a7-147">Tijdens de uitvoering van scripts rechtstreeks in de geïntegreerde Console bent ze gelezen uit het bestand door PowerShell direct.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="7c7a7-148">Als de PowerShell-codering van de VSCode verschilt, kan iets fout gaan hier.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="7c7a7-149">Wanneer u een script dat is geopend in VSCode verwijst naar een ander script dat niet is geopend in VSCode, valt de extensie terug op het laden van de inhoud van het script van het bestandssysteem.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="7c7a7-150">De standaardinstelling UTF-8-codering van de PowerShell-extensie, maar maakt gebruik van [byte-volgordemarkering][], of stuklijst, detectie selecteert u de juiste codering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="7c7a7-151">Het probleem treedt op wanneer ervan uitgaande dat de codering van stuklijst zonder indelingen (zoals [UTF-8][] met geen stuklijst en [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="7c7a7-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="7c7a7-152">De extensie van PowerShell standaardwaarde is UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="7c7a7-153">De extensie wijzigen niet encoding van VSCode-instellingen.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="7c7a7-154">Zie voor meer informatie, [uitgeven #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="7c7a7-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="7c7a7-155">Kies de juiste codering</span><span class="sxs-lookup"><span data-stu-id="7c7a7-155">Choosing the right encoding</span></span>

<span data-ttu-id="7c7a7-156">Verschillende systemen en toepassingen kunnen verschillende coderingen gebruiken:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="7c7a7-157">In .NET Standard, op het web en in de wereld Linux is UTF-8 nu bij de dominante codering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="7c7a7-158">Veel .NET Framework-toepassingen gebruiken [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="7c7a7-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="7c7a7-159">Voor historische doeleinden, dit wordt soms 'Unicode' genoemd, een term die nu verwijst naar een brede [standard](https://en.wikipedia.org/wiki/Unicode) die zowel UTF-8- en UTF-16 bevat.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="7c7a7-160">Op Windows, worden veel systeemeigen toepassingen die zijn gemaakt vóór publicatie Unicode nog maken standaard gebruik van Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="7c7a7-161">Unicode-coderingen hebben ook het concept van een bytevolgorde markeren (BOM).</span><span class="sxs-lookup"><span data-stu-id="7c7a7-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="7c7a7-162">Stuklijsten optreden aan het begin van de tekst een decoder zien waarvan de codering de tekst die wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="7c7a7-163">Voor meerdere byte coderingen, geeft de stuklijst ook [endianness](https://en.wikipedia.org/wiki/Endianness) van de codering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="7c7a7-164">Stuklijsten zijn ontworpen om te worden van bytes die in niet-Unicode-tekst, zodat een redelijke schatting tekst is Unicode wanneer een stuklijst aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="7c7a7-165">Stuklijsten zijn optioneel en hun goedkeuring is zo populair zijn in de wereld Linux niet omdat het een betrouwbare conventie UTF-8 overal wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="7c7a7-166">De meeste Linux-toepassingen wordt ervan uitgegaan dat de tekstinvoer in UTF-8 wordt gecodeerd.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="7c7a7-167">Hoewel veel Linux-toepassingen wordt herkend en verwerkt goed een stuklijst, een getal geldt dit niet, waardoor er artefacten in tekst met deze toepassingen zijn gemanipuleerd.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="7c7a7-168">**Daarom**:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-168">**Therefore**:</span></span>

- <span data-ttu-id="7c7a7-169">Als u met toepassingen voor Windows en Windows PowerShell werkt, moet u liever een codering, zoals UTF-8 met stuklijst- of UTF-16.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="7c7a7-170">Als u verschillende platforms werkt, moet u UTF-8 met stuklijst liever.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="7c7a7-171">Als u voornamelijk in de context van Linux-die zijn gekoppeld werkt, moet u UTF-8 zonder stuklijst liever.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="7c7a7-172">Windows-1252 en Latijns-1 zijn in feite oudere coderingen die Vermijd indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="7c7a7-173">Sommige oudere Windows-toepassingen kunnen echter afhankelijk is van deze.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="7c7a7-174">Het is ook het vermelden waard dat ondertekening van het script is [encoding-afhankelijke](https://github.com/PowerShell/PowerShell/issues/3466), wat betekent dat een wijziging van de codering op een ondertekende script moet opgeven.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="7c7a7-175">VSCode configureren</span><span class="sxs-lookup"><span data-stu-id="7c7a7-175">Configuring VSCode</span></span>

<span data-ttu-id="7c7a7-176">VSCode de standaardcodering is UTF-8 zonder stuklijst.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="7c7a7-177">Om in te stellen [VSCode codering van][], gaat u naar de VSCode-instellingen (<kbd>Ctrl<kbd>+</kbd>,</kbd>) en stel de `"files.encoding"` instelling:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="7c7a7-178">Enkele mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-178">Some possible values are:</span></span>

- <span data-ttu-id="7c7a7-179">`utf8`: [UTF-8] zonder stuklijst</span><span class="sxs-lookup"><span data-stu-id="7c7a7-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="7c7a7-180">`utf8bom`: [UTF-8] met stuklijst</span><span class="sxs-lookup"><span data-stu-id="7c7a7-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="7c7a7-181">`utf16le`: Weinig endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="7c7a7-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="7c7a7-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="7c7a7-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="7c7a7-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="7c7a7-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="7c7a7-184">U krijgt een vervolgkeuzelijst voor deze in de GUI-weergave of voltooiingen voor het in de JSON weergeven.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="7c7a7-185">U kunt ook het volgende toevoegen aan autodetectie codering indien mogelijk:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="7c7a7-186">Als u niet dat deze instellingen wilt beïnvloeden alle bestandstypen, kan VSCode per taal configuraties.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="7c7a7-187">Een instelling taalspecifieke maken door instellingen een `[<language-name>]` veld.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="7c7a7-188">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="7c7a7-189">PowerShell configureren</span><span class="sxs-lookup"><span data-stu-id="7c7a7-189">Configuring PowerShell</span></span>

<span data-ttu-id="7c7a7-190">PowerShell de standaardcodering is afhankelijk van versie:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="7c7a7-191">In PowerShell 6 + is de standaardcodering UTF-8 zonder stuklijst op alle platforms.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="7c7a7-192">In Windows PowerShell, de standaardcodering is meestal Windows-1252, een uitbreiding van [latin 1][], ook wel aangeduid als ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="7c7a7-193">In PowerShell 5 + vindt u de standaardversleuteling aan:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="7c7a7-194">De volgende [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kan worden gebruikt om te bepalen wat de PowerShell-sessie-codering afleidt voor een script zonder een stuklijst.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="7c7a7-195">Het is mogelijk PowerShell voor het gebruik van een bepaalde codering meer in het algemeen gebruik-profielinstellingen te configureren.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="7c7a7-196">Zie de volgende artikelen:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-196">See the following articles:</span></span>

- <span data-ttu-id="7c7a7-197">[@mklement0]de [antwoord over PowerShell-codering op StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="7c7a7-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="7c7a7-198">[@rkeithhill]de [blogbericht over het afhandelen van stuklijst zonder UTF-8-invoer in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="7c7a7-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="7c7a7-199">Het is niet mogelijk om af te dwingen PowerShell gebruik van een specifieke invoer codering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="7c7a7-200">PowerShell 5.1 en onder de standaard Windows-1252-codering als er geen stuklijst is.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="7c7a7-201">Omwille van de interoperabiliteit is het raadzaam om op te slaan van scripts in een Unicode-indeling met een stuklijst.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c7a7-202">Andere hulpprogramma's hebt die touch PowerShell-scripts kunnen worden beïnvloed door uw keuzes codering of een andere codering van uw scripts opnieuw te coderen.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="7c7a7-203">Bestaande scripts</span><span class="sxs-lookup"><span data-stu-id="7c7a7-203">Existing scripts</span></span>

<span data-ttu-id="7c7a7-204">Scripts al op het bestandssysteem moet mogelijk opnieuw worden gecodeerd naar uw nieuw gekozen codering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="7c7a7-205">In de onderste balk van VSCode ziet u het label UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="7c7a7-206">Klik hierop om de actiebalk te openen en selecteer **opslaan met codering**.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="7c7a7-207">U kunt nu kiezen om een nieuwe codering voor dat bestand.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="7c7a7-208">Zie [VSCode codering van][] voor volledige instructies.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="7c7a7-209">Als u wilt dat meerdere bestanden opnieuw te coderen, kunt u het volgende script gebruiken:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="7c7a7-210">De PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="7c7a7-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="7c7a7-211">Als u ook scripts die met behulp van de PowerShell ISE hebt bewerkt, moet u uw encoding-instellingen er synchroniseren.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="7c7a7-212">Het ISE moet voldoen aan een stuklijst, maar het is ook mogelijk om reflectie te te gebruiken [stelt de](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="7c7a7-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="7c7a7-213">Houd er rekening mee dat dit worden gehandhaafd tussen startende ondernemingen blijft wouldn't.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="7c7a7-214">Software voor bronbeheer</span><span class="sxs-lookup"><span data-stu-id="7c7a7-214">Source control software</span></span>

<span data-ttu-id="7c7a7-215">Sommige source control hulpprogramma's, zoals git, negeren coderingen; GIT traceert alleen de bytes.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="7c7a7-216">Andere resources, zoals Azure DevOps- of Mercurial, mogelijk niet.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-216">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="7c7a7-217">Zelfs enkele git-hulpprogramma's zijn, is afhankelijk van de tekst te decoderen.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="7c7a7-218">Als dit het geval is, zorg ervoor dat u:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="7c7a7-219">Configureer de tekst die in uw broncodebeheer zodat deze overeenkomen met de configuratie van uw VSCode-codering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="7c7a7-220">Zorg ervoor dat alle bestanden worden gecontroleerd in broncodebeheer in de relevante codering.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="7c7a7-221">Let van wijzigingen in de codering ontvangen via broncodebeheer.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="7c7a7-222">Een sleutel teken van dit is een diff die wijzen op wijzigingen, maar waar niets lijkt te zijn gewijzigd (omdat bytes hebben, maar niet hebt gedaan tekens).</span><span class="sxs-lookup"><span data-stu-id="7c7a7-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="7c7a7-223">De deelnemers omgevingen</span><span class="sxs-lookup"><span data-stu-id="7c7a7-223">Collaborators' environments</span></span>

<span data-ttu-id="7c7a7-224">Naast het configureren van broncodebeheer, ervoor te zorgen dat uw medewerkers op alle bestanden die u deelt geen instellingen de codering uitvoeren overschrijven door het PowerShell-bestanden opnieuw te coderen.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="7c7a7-225">Andere programma 's</span><span class="sxs-lookup"><span data-stu-id="7c7a7-225">Other programs</span></span>

<span data-ttu-id="7c7a7-226">Andere programma's die leest of schrijft een PowerShell-script kan deze opnieuw coderen.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="7c7a7-227">Enkele voorbeelden zijn:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-227">Some examples are:</span></span>

- <span data-ttu-id="7c7a7-228">Met behulp van het Klembord kopiëren en plakken van een script.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="7c7a7-229">Dit is gebruikelijk in scenario's zoals:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="7c7a7-230">Een script kopieert naar een virtuele machine</span><span class="sxs-lookup"><span data-stu-id="7c7a7-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="7c7a7-231">Een script uit een e-mailadres of webpagina kopiëren</span><span class="sxs-lookup"><span data-stu-id="7c7a7-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="7c7a7-232">Een script kopiëren naar of uit een Microsoft Word- of PowerPoint-document</span><span class="sxs-lookup"><span data-stu-id="7c7a7-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="7c7a7-233">Andere teksteditors, zoals:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="7c7a7-234">Kladblok</span><span class="sxs-lookup"><span data-stu-id="7c7a7-234">Notepad</span></span>
  - <span data-ttu-id="7c7a7-235">vim</span><span class="sxs-lookup"><span data-stu-id="7c7a7-235">vim</span></span>
  - <span data-ttu-id="7c7a7-236">Een andere PowerShell-script-editor</span><span class="sxs-lookup"><span data-stu-id="7c7a7-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="7c7a7-237">Tekst met hulpprogramma's, zoals:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="7c7a7-238">PowerShell-omleiding operators zoals `>` en `>>`</span><span class="sxs-lookup"><span data-stu-id="7c7a7-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="7c7a7-239">File transfer-programma's, zoals:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="7c7a7-240">Een webbrowser, bij het downloaden van scripts</span><span class="sxs-lookup"><span data-stu-id="7c7a7-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="7c7a7-241">Een bestandsshare</span><span class="sxs-lookup"><span data-stu-id="7c7a7-241">A file share</span></span>

<span data-ttu-id="7c7a7-242">Sommige van deze hulpprogramma's bieden in bytes in plaats van tekst, maar andere codering configuraties bieden.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="7c7a7-243">In gevallen waarin u wilt configureren een codering, moet u zodat deze gelijk zijn aan de editor codering om problemen te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="7c7a7-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="7c7a7-244">Andere bronnen op codering in PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c7a7-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="7c7a7-245">Er zijn een paar andere mooie berichten op codering en codering in PowerShell configureren die het noemen waard lezen zijn:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="7c7a7-246">[@mklement0]de [samenvatting van de PowerShell-codering op StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="7c7a7-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="7c7a7-247">Problemen met vorige geopend op vscode-PowerShell voor het coderen van problemen:</span><span class="sxs-lookup"><span data-stu-id="7c7a7-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="7c7a7-248">#1308</span><span class="sxs-lookup"><span data-stu-id="7c7a7-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="7c7a7-249">#1628</span><span class="sxs-lookup"><span data-stu-id="7c7a7-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="7c7a7-250">#1680</span><span class="sxs-lookup"><span data-stu-id="7c7a7-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="7c7a7-251">#1744</span><span class="sxs-lookup"><span data-stu-id="7c7a7-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="7c7a7-252">#1751</span><span class="sxs-lookup"><span data-stu-id="7c7a7-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="7c7a7-253">Het klassieke *Joel op Software* up over Unicode schrijven</span><span class="sxs-lookup"><span data-stu-id="7c7a7-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="7c7a7-254">Encoding in .NET Standard</span><span class="sxs-lookup"><span data-stu-id="7c7a7-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte-volgordemarkering]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode codering van]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
