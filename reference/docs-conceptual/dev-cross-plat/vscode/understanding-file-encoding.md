---
title: Informatie over bestandscodering in VS Code en PowerShell
description: Bestands codering configureren in VS code en Power shell
ms.date: 02/28/2019
ms.openlocfilehash: afad189ff20a4e73d25f15c48d6c4982b18f29a3
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142545"
---
# <a name="understanding-file-encoding-in-vs-code-and-powershell"></a><span data-ttu-id="cb079-103">Informatie over bestandscodering in VS Code en PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb079-103">Understanding file encoding in VS Code and PowerShell</span></span>

<span data-ttu-id="cb079-104">Wanneer u VS code gebruikt om Power shell-scripts te maken en te bewerken, is het belang rijk dat uw bestanden worden opgeslagen met de juiste indeling voor teken versleuteling.</span><span class="sxs-lookup"><span data-stu-id="cb079-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="cb079-105">Wat is bestands codering en waarom is het belang rijk?</span><span class="sxs-lookup"><span data-stu-id="cb079-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="cb079-106">VS code beheert de interface tussen een menselijk invoer van teken reeksen in een buffer en lees-en schrijf blokken van bytes naar het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="cb079-106">VS Code manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="cb079-107">Als VS code een bestand opslaat, wordt een tekst codering gebruikt om te bepalen welke bytes elk teken wordt.</span><span class="sxs-lookup"><span data-stu-id="cb079-107">When VS Code saves a file, it uses a text encoding to decide what bytes each character becomes.</span></span> <span data-ttu-id="cb079-108">Zie [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cb079-108">For more information, see [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding).</span></span>

<span data-ttu-id="cb079-109">Op dezelfde manier moet, wanneer Power shell een script uitvoert, de bytes in een bestand converteren naar tekens om het bestand opnieuw te maken in een Power shell-programma.</span><span class="sxs-lookup"><span data-stu-id="cb079-109">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="cb079-110">Omdat VS code het bestand schrijft en Power shell het bestand leest, moeten ze hetzelfde coderings systeem gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cb079-110">Since VS Code writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="cb079-111">Dit proces voor het parseren van een Power shell-script gaat over: _bytes_  ->  _tekens_  ->  _tokens_ de  ->  _abstracte syntaxis_  ->  _van_ de syntax structuur</span><span class="sxs-lookup"><span data-stu-id="cb079-111">This process of parsing a PowerShell script goes: _bytes_ -> _characters_ -> _tokens_ -> _abstract syntax tree_ -> _execution_ .</span></span>

<span data-ttu-id="cb079-112">Zowel VS code als Power shell worden geïnstalleerd met een verstandig standaard coderings configuratie.</span><span class="sxs-lookup"><span data-stu-id="cb079-112">Both VS Code and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="cb079-113">De standaard codering die door Power shell wordt gebruikt, is echter gewijzigd met de release van Power shell core (v6. x).</span><span class="sxs-lookup"><span data-stu-id="cb079-113">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="cb079-114">Om ervoor te zorgen dat u geen problemen hebt met het gebruik van Power shell of de Power shell-extensie in VS code, moet u de VS code en Power shell-instellingen op de juiste wijze configureren.</span><span class="sxs-lookup"><span data-stu-id="cb079-114">To ensure you have no problems using PowerShell or the PowerShell extension in VS Code, you need to configure your VS Code and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="cb079-115">Veelvoorkomende oorzaken van het coderen van problemen</span><span class="sxs-lookup"><span data-stu-id="cb079-115">Common causes of encoding issues</span></span>

<span data-ttu-id="cb079-116">Coderings problemen treden op wanneer de code ring van VS code of uw script bestand niet overeenkomt met de verwachte code ring van Power shell.</span><span class="sxs-lookup"><span data-stu-id="cb079-116">Encoding problems occur when the encoding of VS Code or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="cb079-117">Het is niet mogelijk om in Power shell automatisch de bestands codering te bepalen.</span><span class="sxs-lookup"><span data-stu-id="cb079-117">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="cb079-118">Het is waarschijnlijker dat u problemen hebt met het coderen wanneer u tekens gebruikt die niet voor komt in de [7-bits ASCII-tekenset](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="cb079-118">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="cb079-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="cb079-119">For example:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="cb079-120">Uitgebreide niet-letter-tekens zoals em-streepje ( `—` ), non-Break Space ( ` ` ) of dubbele aanhalings teken `"` ()</span><span class="sxs-lookup"><span data-stu-id="cb079-120">Extended non-letter characters like em-dash (`—`), non-breaking space (` `) or left double quotation mark (`"`)</span></span>
- <span data-ttu-id="cb079-121">Latijnse tekens met accenten ( `É` , `ü` )</span><span class="sxs-lookup"><span data-stu-id="cb079-121">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="cb079-122">Niet-Latijnse tekens zoals Cyrillisch ( `Д` , `Ц` )</span><span class="sxs-lookup"><span data-stu-id="cb079-122">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="cb079-123">CJK-tekens ( `本` , `화` , `が` )</span><span class="sxs-lookup"><span data-stu-id="cb079-123">CJK characters (`本`, `화`, `が`)</span></span>

<span data-ttu-id="cb079-124">Veelvoorkomende redenen voor het coderen van problemen zijn:</span><span class="sxs-lookup"><span data-stu-id="cb079-124">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="cb079-125">De code ringen van VS code en Power shell zijn niet gewijzigd ten opzichte van hun standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="cb079-125">The encodings of VS Code and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="cb079-126">Voor Power shell 5,1 en lager is de standaard codering verschillend van VS code.</span><span class="sxs-lookup"><span data-stu-id="cb079-126">For PowerShell 5.1 and below, the default encoding is different from VS Code's.</span></span>
- <span data-ttu-id="cb079-127">Een andere editor heeft het bestand geopend en overschreven in een nieuwe code ring.</span><span class="sxs-lookup"><span data-stu-id="cb079-127">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="cb079-128">Dit gebeurt vaak met de ISE.</span><span class="sxs-lookup"><span data-stu-id="cb079-128">This often happens with the ISE.</span></span>
- <span data-ttu-id="cb079-129">Het bestand is in broncode beheer ingecheckt in een code ring die verschilt van wat VS code of Power shell verwacht.</span><span class="sxs-lookup"><span data-stu-id="cb079-129">The file is checked into source control in an encoding that is different from what VS Code or PowerShell expects.</span></span> <span data-ttu-id="cb079-130">Dit kan gebeuren wanneer samen werkers editors gebruiken met verschillende coderings configuraties.</span><span class="sxs-lookup"><span data-stu-id="cb079-130">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="cb079-131">Hoe weet ik wanneer u problemen met het coderen hebt</span><span class="sxs-lookup"><span data-stu-id="cb079-131">How to tell when you have encoding issues</span></span>

<span data-ttu-id="cb079-132">Codeer fouten worden vaak als fouten in scripts geparseerd.</span><span class="sxs-lookup"><span data-stu-id="cb079-132">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="cb079-133">Als u vreemde teken reeksen in uw script vindt, kan dit het probleem zijn.</span><span class="sxs-lookup"><span data-stu-id="cb079-133">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="cb079-134">In het onderstaande voor beeld wordt een en-streepje ( `–` ) weer gegeven als de tekens `â&euro;"` :</span><span class="sxs-lookup"><span data-stu-id="cb079-134">In the example below, an en-dash (`–`) appears as the characters `â&euro;"`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â&euro;"From $from â&euro;"To $recipient1 â&euro;"Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="cb079-135">Dit probleem treedt op omdat VS code het teken `–` in UTF-8 als de bytes codeert `0xE2 0x80 0x93` .</span><span class="sxs-lookup"><span data-stu-id="cb079-135">This problem occurs because VS Code encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span> <span data-ttu-id="cb079-136">Wanneer deze bytes worden gedecodeerd als Windows-1252, worden ze geïnterpreteerd als de tekens `â&euro;"` .</span><span class="sxs-lookup"><span data-stu-id="cb079-136">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â&euro;"`.</span></span>

<span data-ttu-id="cb079-137">U kunt onder andere de volgende vreemde teken reeksen zien:</span><span class="sxs-lookup"><span data-stu-id="cb079-137">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="cb079-138">`â&euro;"` In plaats van `–`</span><span class="sxs-lookup"><span data-stu-id="cb079-138">`â&euro;"` instead of `–`</span></span>
- <span data-ttu-id="cb079-139">`â&euro;"` In plaats van `—`</span><span class="sxs-lookup"><span data-stu-id="cb079-139">`â&euro;"` instead of `—`</span></span>
- <span data-ttu-id="cb079-140">`Ã„2` In plaats van `Ä`</span><span class="sxs-lookup"><span data-stu-id="cb079-140">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="cb079-141">`Â` in plaats van ` `  (een vaste spatie)</span><span class="sxs-lookup"><span data-stu-id="cb079-141">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="cb079-142">`Ã&copy;` In plaats van `é`</span><span class="sxs-lookup"><span data-stu-id="cb079-142">`Ã&copy;` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="cb079-143">Deze handige [Naslag informatie](https://www.i18nqa.com/debug/utf8-debug.html) bevat de algemene patronen die duiden op een UTF-8-of Windows-1252-coderings probleem.</span><span class="sxs-lookup"><span data-stu-id="cb079-143">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vs-code-interacts-with-encodings"></a><span data-ttu-id="cb079-144">Hoe de Power shell-uitbrei ding in VS code communiceert met code ringen</span><span class="sxs-lookup"><span data-stu-id="cb079-144">How the PowerShell extension in VS Code interacts with encodings</span></span>

<span data-ttu-id="cb079-145">De Power shell-extensie communiceert op een aantal manieren met scripts:</span><span class="sxs-lookup"><span data-stu-id="cb079-145">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="cb079-146">Wanneer scripts worden bewerkt in VS code, wordt de inhoud door VS-code naar de uitbrei ding verzonden.</span><span class="sxs-lookup"><span data-stu-id="cb079-146">When scripts are edited in VS Code, the contents are sent by VS Code to the extension.</span></span> <span data-ttu-id="cb079-147">Het [Language server-protocol][] verplichtt dat deze inhoud wordt overgedragen in UTF-8.</span><span class="sxs-lookup"><span data-stu-id="cb079-147">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="cb079-148">Daarom is het niet mogelijk om de uitbrei ding de verkeerde code ring te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="cb079-148">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
1. <span data-ttu-id="cb079-149">Wanneer scripts rechtstreeks worden uitgevoerd in de geïntegreerde console, worden ze rechtstreeks door Power shell gelezen uit het bestand.</span><span class="sxs-lookup"><span data-stu-id="cb079-149">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="cb079-150">Als de code ring van Power shell verschilt van VS code, kan er iets fout hier worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cb079-150">If PowerShell's encoding differs from VS Code's, something can go wrong here.</span></span>
1. <span data-ttu-id="cb079-151">Wanneer een script dat is geopend in VS code verwijst naar een ander script dat niet is geopend in VS code, valt de uitbrei ding terug om de inhoud van dat script uit het bestands systeem te laden.</span><span class="sxs-lookup"><span data-stu-id="cb079-151">When a script that is open in VS Code references another script that is not open in VS Code, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="cb079-152">De Power shell-extensie wordt standaard ingesteld op UTF-8-code ring, maar gebruikt een [byte-volgorde markering][]of stuk lijst, detectie om de juiste code ring te selecteren.</span><span class="sxs-lookup"><span data-stu-id="cb079-152">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="cb079-153">Het probleem treedt op bij het afnemen van de code ring van een stuk lijst-less-indeling (zoals [UTF-8][] zonder stuk lijst en [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="cb079-153">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span> <span data-ttu-id="cb079-154">De Power shell-extensie wordt standaard ingesteld op UTF-8.</span><span class="sxs-lookup"><span data-stu-id="cb079-154">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="cb079-155">De uitbrei ding kan de coderings instellingen van VS code niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="cb079-155">The extension cannot change VS Code's encoding settings.</span></span> <span data-ttu-id="cb079-156">Zie [issue #824](https://github.com/Microsoft/VSCode/issues/824)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cb079-156">For more information, see [issue #824](https://github.com/Microsoft/VSCode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="cb079-157">De juiste code ring kiezen</span><span class="sxs-lookup"><span data-stu-id="cb079-157">Choosing the right encoding</span></span>

<span data-ttu-id="cb079-158">Verschillende systemen en toepassingen kunnen gebruikmaken van verschillende code ringen:</span><span class="sxs-lookup"><span data-stu-id="cb079-158">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="cb079-159">In .NET Standard, op het web en in de Linux-wereld is UTF-8 nu de dominante code ring.</span><span class="sxs-lookup"><span data-stu-id="cb079-159">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="cb079-160">Veel .NET Framework toepassingen gebruiken [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="cb079-160">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="cb079-161">Voor historische redenen wordt dit ook wel ' Unicode ' genoemd, een term die nu verwijst naar een brede [norm](https://en.wikipedia.org/wiki/Unicode) die zowel UTF-8 als UTF-16 bevat.</span><span class="sxs-lookup"><span data-stu-id="cb079-161">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="cb079-162">In Windows zijn veel systeem eigen toepassingen die vooraf date Unicode blijven gebruiken standaard Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="cb079-162">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="cb079-163">Unicode-code ringen hebben ook het concept van een byte-volgorde markering (stuk lijst).</span><span class="sxs-lookup"><span data-stu-id="cb079-163">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="cb079-164">Stuk lijsten komen aan het begin van de tekst voor om een decoder te laten zien welke code wordt gebruikt voor het coderen van de tekst.</span><span class="sxs-lookup"><span data-stu-id="cb079-164">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="cb079-165">Voor multi byte-code ringen geeft de stuk lijst ook de [endian](https://en.wikipedia.org/wiki/Endianness) van de code ring aan.</span><span class="sxs-lookup"><span data-stu-id="cb079-165">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="cb079-166">Stuk lijsten zijn ontworpen om bytes te zijn die zelden voor komen in niet-Unicode-tekst, waardoor een redelijke schatting van de tekst Unicode wanneer een stuk lijst aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="cb079-166">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="cb079-167">Stuk lijsten zijn optioneel en hun acceptatie is niet hetzelfde als populair in de Linux-wereld omdat een betrouw bare Conventie van UTF-8 overal wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cb079-167">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="cb079-168">De meeste Linux-toepassingen gaan ervan uit dat tekst invoer is gecodeerd in UTF-8.</span><span class="sxs-lookup"><span data-stu-id="cb079-168">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="cb079-169">Hoewel veel Linux-toepassingen een stuk lijst herkennen en op de juiste wijze afhandelen, wordt een getal niet in rekening gebracht voor artefacten in tekst die is gemanipuleerd met deze toepassingen.</span><span class="sxs-lookup"><span data-stu-id="cb079-169">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="cb079-170">**Daarom** :</span><span class="sxs-lookup"><span data-stu-id="cb079-170">**Therefore** :</span></span>

- <span data-ttu-id="cb079-171">Als u voornamelijk met Windows-toepassingen en Windows Power shell werkt, moet u de voor keur geven aan een code ring zoals UTF-8 met stuk lijst of UTF-16.</span><span class="sxs-lookup"><span data-stu-id="cb079-171">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="cb079-172">Als u op verschillende platforms werkt, moet u de voor keur geven aan UTF-8 met stuk lijst.</span><span class="sxs-lookup"><span data-stu-id="cb079-172">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="cb079-173">Als u voornamelijk werkt in contexten die aan Linux zijn gekoppeld, moet u de voor keur geven aan UTF-8 zonder stuk lijst.</span><span class="sxs-lookup"><span data-stu-id="cb079-173">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="cb079-174">Windows-1252 en Latijns-1 zijn in wezen oudere code ringen die u zo mogelijk moet vermijden.</span><span class="sxs-lookup"><span data-stu-id="cb079-174">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="cb079-175">Sommige oudere Windows-toepassingen kunnen echter afhankelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="cb079-175">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="cb079-176">Het is ook belang rijk dat het ondertekenen van een script [coderings afhankelijke](https://github.com/PowerShell/PowerShell/issues/3466)is, wat betekent dat het wijzigen van de code ring van een ondertekend script opnieuw moet worden ondertekend.</span><span class="sxs-lookup"><span data-stu-id="cb079-176">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vs-code"></a><span data-ttu-id="cb079-177">VS-code configureren</span><span class="sxs-lookup"><span data-stu-id="cb079-177">Configuring VS Code</span></span>

<span data-ttu-id="cb079-178">De standaard codering van VS code is UTF-8 zonder stuk lijst.</span><span class="sxs-lookup"><span data-stu-id="cb079-178">VS Code's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="cb079-179">Als u de code [ring van VS code][]wilt instellen, gaat u naar de instellingen van VS code (<kbd>CTRL</kbd> + <kbd>,</kbd>) en stelt u de `"files.encoding"` instelling in:</span><span class="sxs-lookup"><span data-stu-id="cb079-179">To set [VS Code's encoding][], go to the VS Code settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="cb079-180">Enkele mogelijke waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="cb079-180">Some possible values are:</span></span>

- <span data-ttu-id="cb079-181">`utf8`: [UTF-8] zonder stuk lijst</span><span class="sxs-lookup"><span data-stu-id="cb079-181">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="cb079-182">`utf8bom`: [UTF-8] met stuk lijst</span><span class="sxs-lookup"><span data-stu-id="cb079-182">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="cb079-183">`utf16le`: Little Endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="cb079-183">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="cb079-184">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="cb079-184">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="cb079-185">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="cb079-185">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="cb079-186">U krijgt hiervoor een vervolg keuzelijst te zien in de weer gave GUI of in de JSON-weer gave.</span><span class="sxs-lookup"><span data-stu-id="cb079-186">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="cb079-187">U kunt indien mogelijk ook het volgende toevoegen voor het automatisch detecteren van code ring:</span><span class="sxs-lookup"><span data-stu-id="cb079-187">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="cb079-188">Als u niet wilt dat deze instellingen van invloed zijn op alle bestands typen, kunt u in VS code configuraties per taal instellen.</span><span class="sxs-lookup"><span data-stu-id="cb079-188">If you don't want these settings to affect all files types, VS Code also allows per-language configurations.</span></span> <span data-ttu-id="cb079-189">Maak een taalspecifieke instelling door instellingen in een veld in te voeren `[<language-name>]` .</span><span class="sxs-lookup"><span data-stu-id="cb079-189">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="cb079-190">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="cb079-190">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="cb079-191">U kunt ook overwegen om de [Gremlins tracker][] voor Visual Studio code te installeren.</span><span class="sxs-lookup"><span data-stu-id="cb079-191">You may also want to consider installing the [Gremlins tracker][] for Visual Studio Code.</span></span> <span data-ttu-id="cb079-192">Met deze uitbrei ding worden bepaalde Unicode-tekens die eenvoudig zijn beschadigd, weer geven, omdat deze onzichtbaar zijn of eruitzien als andere normale tekens.</span><span class="sxs-lookup"><span data-stu-id="cb079-192">This extension reveals certain Unicode characters that easily corrupted because they are invisible or look like other normal characters.</span></span>

## <a name="configuring-powershell"></a><span data-ttu-id="cb079-193">Power shell configureren</span><span class="sxs-lookup"><span data-stu-id="cb079-193">Configuring PowerShell</span></span>

<span data-ttu-id="cb079-194">De standaard codering van Power shell varieert afhankelijk van de versie:</span><span class="sxs-lookup"><span data-stu-id="cb079-194">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="cb079-195">In Power shell 6 + is de standaard codering UTF-8 zonder stuk lijst op alle platformen.</span><span class="sxs-lookup"><span data-stu-id="cb079-195">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="cb079-196">In Windows Power shell is de standaard codering doorgaans Windows-1252, een uitbrei ding van [Latijn-1][], ook wel ISO 8859-1 genoemd.</span><span class="sxs-lookup"><span data-stu-id="cb079-196">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="cb079-197">In Power shell 5 + vindt u de standaard codering met de volgende opties:</span><span class="sxs-lookup"><span data-stu-id="cb079-197">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="cb079-198">Het volgende [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kan worden gebruikt om te bepalen welke code ring uw Power shell-sessie afleidt voor een script zonder een stuk lijst.</span><span class="sxs-lookup"><span data-stu-id="cb079-198">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="cb079-199">Het is mogelijk om Power shell te configureren voor het gebruik van een bepaalde code ring, met behulp van profiel instellingen.</span><span class="sxs-lookup"><span data-stu-id="cb079-199">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span>
<span data-ttu-id="cb079-200">Zie de volgende artikelen:</span><span class="sxs-lookup"><span data-stu-id="cb079-200">See the following articles:</span></span>

- <span data-ttu-id="cb079-201">[@mklement0][antwoord over Power shell-code ring op stack overflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="cb079-201">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="cb079-202">[@rkeithhill]het [blog bericht over het afhandelen van een stuk lijst zonder UTF-8-invoer in Power shell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="cb079-202">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="cb079-203">Het is niet mogelijk om Power shell te dwingen een specifieke invoer codering te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cb079-203">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="cb079-204">In Power shell 5,1 en lager, dat wordt uitgevoerd op Windows met de land instelling ingesteld op en-US, wordt standaard Windows-1252-code ring weer gegeven wanneer er geen stuk lijst is.</span><span class="sxs-lookup"><span data-stu-id="cb079-204">PowerShell 5.1 and below, running on Windows with the locale set to en-US, defaults to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="cb079-205">Andere land instellingen kunnen gebruikmaken van een andere code ring.</span><span class="sxs-lookup"><span data-stu-id="cb079-205">Other locale settings may use a different encoding.</span></span> <span data-ttu-id="cb079-206">Om interoperabiliteit te garanderen, is het het beste om scripts in een Unicode-indeling met een stuk lijst op te slaan.</span><span class="sxs-lookup"><span data-stu-id="cb079-206">To ensure interoperability, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb079-207">Andere hulpprogram ma's waarmee u Power shell-scripts kunt aanraken, kunnen worden beïnvloed door uw coderings opties of uw scripts opnieuw versleutelen naar een andere code ring.</span><span class="sxs-lookup"><span data-stu-id="cb079-207">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="cb079-208">Bestaande scripts</span><span class="sxs-lookup"><span data-stu-id="cb079-208">Existing scripts</span></span>

<span data-ttu-id="cb079-209">Scripts die zich al op het bestands systeem bevinden, moeten mogelijk opnieuw worden gecodeerd met de nieuwe gekozen code ring.</span><span class="sxs-lookup"><span data-stu-id="cb079-209">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="cb079-210">In de onderste balk van VS code ziet u het label UTF-8.</span><span class="sxs-lookup"><span data-stu-id="cb079-210">In the bottom bar of VS Code, you'll see the label UTF-8.</span></span> <span data-ttu-id="cb079-211">Klik hierop om de actie balk te openen en selecteer **opslaan met code ring** .</span><span class="sxs-lookup"><span data-stu-id="cb079-211">Click it to open the action bar and select **Save with encoding** .</span></span> <span data-ttu-id="cb079-212">U kunt nu een nieuwe code ring voor dat bestand kiezen.</span><span class="sxs-lookup"><span data-stu-id="cb079-212">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="cb079-213">Bekijk [de code ring van VS codes][] voor volledige instructies.</span><span class="sxs-lookup"><span data-stu-id="cb079-213">See [VS Code's encoding][] for full instructions.</span></span>

<span data-ttu-id="cb079-214">Als u meerdere bestanden opnieuw moet versleutelen, kunt u het volgende script gebruiken:</span><span class="sxs-lookup"><span data-stu-id="cb079-214">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="cb079-215">De Power shell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="cb079-215">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="cb079-216">Als u ook scripts bewerkt met behulp van de Power shell-ISE, moet u de instellingen voor de code ring hier synchroniseren.</span><span class="sxs-lookup"><span data-stu-id="cb079-216">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="cb079-217">De ISE moet voldoen aan een stuk lijst, maar het is ook mogelijk om reflectie te gebruiken om [de code ring](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)in te stellen.</span><span class="sxs-lookup"><span data-stu-id="cb079-217">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="cb079-218">Houd er rekening mee dat dit niet kan worden gehandhaafd tussen opstart handelingen.</span><span class="sxs-lookup"><span data-stu-id="cb079-218">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="cb079-219">Broncode beheer software</span><span class="sxs-lookup"><span data-stu-id="cb079-219">Source control software</span></span>

<span data-ttu-id="cb079-220">Sommige hulpprogram ma's voor broncode beheer, zoals git, negeren code ringen. Git houdt alleen de bytes bij.</span><span class="sxs-lookup"><span data-stu-id="cb079-220">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span> <span data-ttu-id="cb079-221">Andere, zoals Azure DevOps of mercurial, is niet mogelijk.</span><span class="sxs-lookup"><span data-stu-id="cb079-221">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="cb079-222">Zelfs sommige Git-hulpprogram ma's zijn afhankelijk van het decoderen van tekst.</span><span class="sxs-lookup"><span data-stu-id="cb079-222">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="cb079-223">Als dit het geval is, moet u het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="cb079-223">When this is the case, make sure you:</span></span>

- <span data-ttu-id="cb079-224">Configureer de tekst codering in het bron beheer zodat deze overeenkomt met de configuratie van de VS code.</span><span class="sxs-lookup"><span data-stu-id="cb079-224">Configure the text encoding in your source control to match your VS Code configuration.</span></span>
- <span data-ttu-id="cb079-225">Zorg ervoor dat al uw bestanden in de juiste code ring zijn ingecheckt in broncode beheer.</span><span class="sxs-lookup"><span data-stu-id="cb079-225">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="cb079-226">Wees op de hoede van wijzigingen in de code ring die via broncode beheer wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="cb079-226">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="cb079-227">Een sleutel teken van dit is een verschil waarmee de wijzigingen worden aangegeven, maar waarbij niets lijkt te zijn gewijzigd (omdat het aantal bytes maar tekens bevat).</span><span class="sxs-lookup"><span data-stu-id="cb079-227">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="cb079-228">Omgevingen van deel nemers</span><span class="sxs-lookup"><span data-stu-id="cb079-228">Collaborators' environments</span></span>

<span data-ttu-id="cb079-229">Zorg ervoor dat uw samen werkers op bestanden die u deelt geen instellingen hebben die uw code ring overschrijven door Power Shell-bestanden opnieuw te coderen, boven op het configureren van broncode beheer.</span><span class="sxs-lookup"><span data-stu-id="cb079-229">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="cb079-230">Andere Program ma's</span><span class="sxs-lookup"><span data-stu-id="cb079-230">Other programs</span></span>

<span data-ttu-id="cb079-231">Elk ander programma dat een Power shell-script leest of schrijft, kan het opnieuw versleutelen.</span><span class="sxs-lookup"><span data-stu-id="cb079-231">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="cb079-232">Een aantal voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="cb079-232">Some examples are:</span></span>

- <span data-ttu-id="cb079-233">Het klem bord gebruiken om een script te kopiëren en te plakken.</span><span class="sxs-lookup"><span data-stu-id="cb079-233">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="cb079-234">Dit is gebruikelijk in scenario's zoals:</span><span class="sxs-lookup"><span data-stu-id="cb079-234">This is common in scenarios like:</span></span>
  - <span data-ttu-id="cb079-235">Een script naar een VM kopiëren</span><span class="sxs-lookup"><span data-stu-id="cb079-235">Copying a script into a VM</span></span>
  - <span data-ttu-id="cb079-236">Een script uit een e-mail bericht of webpagina kopiëren</span><span class="sxs-lookup"><span data-stu-id="cb079-236">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="cb079-237">Een script kopiëren naar of van een micro soft Word-of Power Point-document</span><span class="sxs-lookup"><span data-stu-id="cb079-237">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="cb079-238">Andere tekst editors, zoals:</span><span class="sxs-lookup"><span data-stu-id="cb079-238">Other text editors, such as:</span></span>
  - <span data-ttu-id="cb079-239">Kladblok</span><span class="sxs-lookup"><span data-stu-id="cb079-239">Notepad</span></span>
  - <span data-ttu-id="cb079-240">vim</span><span class="sxs-lookup"><span data-stu-id="cb079-240">vim</span></span>
  - <span data-ttu-id="cb079-241">Een andere Power shell-script editor</span><span class="sxs-lookup"><span data-stu-id="cb079-241">Any other PowerShell script editor</span></span>
- <span data-ttu-id="cb079-242">Hulpprogram ma's voor tekst bewerking, zoals:</span><span class="sxs-lookup"><span data-stu-id="cb079-242">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="cb079-243">Power shell-omleidings operatoren zoals `>` en `>>`</span><span class="sxs-lookup"><span data-stu-id="cb079-243">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="cb079-244">Program ma's voor bestands overdracht, zoals:</span><span class="sxs-lookup"><span data-stu-id="cb079-244">File transfer programs, like:</span></span>
  - <span data-ttu-id="cb079-245">Een webbrowser bij het downloaden van scripts</span><span class="sxs-lookup"><span data-stu-id="cb079-245">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="cb079-246">Een bestands share</span><span class="sxs-lookup"><span data-stu-id="cb079-246">A file share</span></span>

<span data-ttu-id="cb079-247">Sommige van deze hulpprogram ma's maken deel uit van bytes in plaats van tekst, maar andere bieden coderings configuraties.</span><span class="sxs-lookup"><span data-stu-id="cb079-247">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="cb079-248">In die gevallen waarin u een code ring moet configureren, moet u deze op dezelfde locatie instellen als uw editor codering om problemen te voor komen.</span><span class="sxs-lookup"><span data-stu-id="cb079-248">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="cb079-249">Andere bronnen voor code ring in Power shell</span><span class="sxs-lookup"><span data-stu-id="cb079-249">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="cb079-250">Er zijn enkele andere leuke berichten over code ring en het configureren van code ring in Power shell die een lees bewerking zijn:</span><span class="sxs-lookup"><span data-stu-id="cb079-250">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- [<span data-ttu-id="cb079-251">about_Character_Encoding</span><span class="sxs-lookup"><span data-stu-id="cb079-251">about_Character_Encoding</span></span>](/powershell/module/microsoft.powershell.core/about/about_character_encoding)
- <span data-ttu-id="cb079-252">[@mklement0][overzicht van Power shell-code ring op stack overflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="cb079-252">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="cb079-253">Eerdere problemen die zijn geopend op VS Code-PowerShell voor het coderen van problemen:</span><span class="sxs-lookup"><span data-stu-id="cb079-253">Previous issues opened on VS Code-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="cb079-254">#1308</span><span class="sxs-lookup"><span data-stu-id="cb079-254">#1308</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1308)
  - [<span data-ttu-id="cb079-255">#1628</span><span class="sxs-lookup"><span data-stu-id="cb079-255">#1628</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1628)
  - [<span data-ttu-id="cb079-256">#1680</span><span class="sxs-lookup"><span data-stu-id="cb079-256">#1680</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1680)
  - [<span data-ttu-id="cb079-257">#1744</span><span class="sxs-lookup"><span data-stu-id="cb079-257">#1744</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1744)
  - [<span data-ttu-id="cb079-258">#1751</span><span class="sxs-lookup"><span data-stu-id="cb079-258">#1751</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1751)
- [<span data-ttu-id="cb079-259">De klassieke _Joel op software_ schrijven over Unicode</span><span class="sxs-lookup"><span data-stu-id="cb079-259">The classic _Joel on Software_ write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="cb079-260">Coderen in .NET Standard</span><span class="sxs-lookup"><span data-stu-id="cb079-260">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)

[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[Latijns-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte-volgorde markering]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocol voor taal server]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Versleuteling van VS code]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VS Code's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[Gremlins tracering]: https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins
[Gremlins tracker]: https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins
