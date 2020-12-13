---
ms.date: 06/09/2020
ms.topic: reference
title: Trefwoorden voor Help op basis van opmerkingen
description: Trefwoorden voor Help op basis van opmerkingen
ms.openlocfilehash: d87dde8700813767f6c09cfce70ed06c7964ebc7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645466"
---
# <a name="comment-based-help-keywords"></a><span data-ttu-id="1e902-103">Trefwoorden voor Help op basis van opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1e902-103">Comment-Based Help Keywords</span></span>

<span data-ttu-id="1e902-104">In dit onderwerp worden de tref woorden in Help op basis van opmerkingen vermeld en beschreven.</span><span class="sxs-lookup"><span data-stu-id="1e902-104">This topic lists and describes the keywords in comment-based help.</span></span>

## <a name="keywords-in-comment-based-help"></a><span data-ttu-id="1e902-105">Tref woorden in Comment-Based Help</span><span class="sxs-lookup"><span data-stu-id="1e902-105">Keywords in Comment-Based Help</span></span>

<span data-ttu-id="1e902-106">Hieronder vindt u geldige Help-tref woorden op basis van opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="1e902-106">The following are valid comment-based Help keywords.</span></span> <span data-ttu-id="1e902-107">Ze worden weer gegeven in de volg orde waarin ze doorgaans worden weer gegeven in een Help-onderwerp samen met het beoogde gebruik.</span><span class="sxs-lookup"><span data-stu-id="1e902-107">They are listed in the order in which they typically appear in a Help topic along with their intended use.</span></span> <span data-ttu-id="1e902-108">Deze tref woorden kunnen in een wille keurige volg orde in de op opmerkingen gebaseerde Help worden weer gegeven en zijn niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="1e902-108">These keywords can appear in any order in the comment-based Help, and they are not case-sensitive.</span></span>

<span data-ttu-id="1e902-109">Houd er rekening mee dat het `.EXTERNALHELP` sleutel woord voor rang krijgt op alle andere op opmerkingen gebaseerde Help-tref woorden.</span><span class="sxs-lookup"><span data-stu-id="1e902-109">Note that the `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span>
<span data-ttu-id="1e902-110">Wanneer `.EXTERNALHELP` aanwezig is, wordt in de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) geen Help op basis van opmerkingen weer gegeven, zelfs wanneer er geen Help-bestand wordt gevonden dat overeenkomt met de waarde van het sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="1e902-110">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1e902-111">. SAMEN VATTING</span><span class="sxs-lookup"><span data-stu-id="1e902-111">.SYNOPSIS</span></span>

<span data-ttu-id="1e902-112">Een korte beschrijving van de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="1e902-112">A brief description of the function or script.</span></span> <span data-ttu-id="1e902-113">Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1e902-113">This keyword can be used only once in each topic.</span></span>

## <a name="description"></a><span data-ttu-id="1e902-114">. BESCHRIJVINGEN</span><span class="sxs-lookup"><span data-stu-id="1e902-114">.DESCRIPTION</span></span>

<span data-ttu-id="1e902-115">Een gedetailleerde beschrijving van de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="1e902-115">A detailed description of the function or script.</span></span> <span data-ttu-id="1e902-116">Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1e902-116">This keyword can be used only once in each topic.</span></span>

## <a name="parameter-parameter-name"></a><span data-ttu-id="1e902-117">. BEPAALDE \<Parameter-Name></span><span class="sxs-lookup"><span data-stu-id="1e902-117">.PARAMETER \<Parameter-Name></span></span>

<span data-ttu-id="1e902-118">De beschrijving van een para meter.</span><span class="sxs-lookup"><span data-stu-id="1e902-118">The description of a parameter.</span></span> <span data-ttu-id="1e902-119">U kunt een `.PARAMETER` tref woord voor elke para meter toevoegen in de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="1e902-119">You can include a `.PARAMETER` keyword for each parameter in the function or script.</span></span>

<span data-ttu-id="1e902-120">De `.PARAMETER` tref woorden kunnen in een wille keurige volg orde in het blok met opmerkingen worden weer gegeven, maar de volg orde waarin de para meters worden weer gegeven in de declaratie van de `Param` instructie of functie, bepaalt de volg orde waarin de para meters in het Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="1e902-120">The `.PARAMETER` keywords can appear in any order in the comment block, but the order in which the parameters appear in the `Param` statement or function declaration determines the order in which the parameters appear in Help topic.</span></span> <span data-ttu-id="1e902-121">Als u de volg orde van de para meters in het Help-onderwerp wilt wijzigen, wijzigt u de volg orde van de para meters in de `Param` declaratie instructie of functie.</span><span class="sxs-lookup"><span data-stu-id="1e902-121">To change the order of parameters in the Help topic, change the order of the parameters in the `Param` statement or function declaration.</span></span>

<span data-ttu-id="1e902-122">U kunt ook een beschrijving van een para meter opgeven door een opmerking in de `Param` instructie direct vóór de naam van de parameter variabele in te stellen.</span><span class="sxs-lookup"><span data-stu-id="1e902-122">You can also specify a parameter description by placing a comment in the `Param` statement immediately before the parameter variable name.</span></span> <span data-ttu-id="1e902-123">Als u zowel een `Param` Opmerking Als een `.PARAMETER` tref woord gebruikt, wordt de beschrijving die is gekoppeld aan het `.PARAMETER` tref woord gebruikt en wordt de opmerking voor de `Param` instructie genegeerd.</span><span class="sxs-lookup"><span data-stu-id="1e902-123">If you use both a `Param` statement comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the `Param` statement comment is ignored.</span></span>

## <a name="example"></a><span data-ttu-id="1e902-124">. Hierbij</span><span class="sxs-lookup"><span data-stu-id="1e902-124">.EXAMPLE</span></span>

<span data-ttu-id="1e902-125">Een voor beeld van een opdracht die gebruikmaakt van de functie of het script, eventueel gevolgd door voorbeeld uitvoer en een beschrijving.</span><span class="sxs-lookup"><span data-stu-id="1e902-125">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="1e902-126">Herhaal dit tref woord voor elk voor beeld.</span><span class="sxs-lookup"><span data-stu-id="1e902-126">Repeat this keyword for each example.</span></span>

## <a name="inputs"></a><span data-ttu-id="1e902-127">. INVOER</span><span class="sxs-lookup"><span data-stu-id="1e902-127">.INPUTS</span></span>

<span data-ttu-id="1e902-128">De Microsoft .NET Framework typen objecten die kunnen worden gesluisd met de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="1e902-128">The Microsoft .NET Framework types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="1e902-129">U kunt ook een beschrijving van de invoer objecten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="1e902-129">You can also include a description of the input objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="1e902-130">. UITVOER</span><span class="sxs-lookup"><span data-stu-id="1e902-130">.OUTPUTS</span></span>

<span data-ttu-id="1e902-131">Het .NET Framework type van de objecten die door de cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e902-131">The .NET Framework type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="1e902-132">U kunt ook een beschrijving van de geretourneerde objecten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="1e902-132">You can also include a description of the returned objects.</span></span>

## <a name="notes"></a><span data-ttu-id="1e902-133">. NOTEN</span><span class="sxs-lookup"><span data-stu-id="1e902-133">.NOTES</span></span>

<span data-ttu-id="1e902-134">Aanvullende informatie over de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="1e902-134">Additional information about the function or script.</span></span>

## <a name="link"></a><span data-ttu-id="1e902-135">. GEKOPPELD</span><span class="sxs-lookup"><span data-stu-id="1e902-135">.LINK</span></span>

<span data-ttu-id="1e902-136">De naam van een verwant onderwerp.</span><span class="sxs-lookup"><span data-stu-id="1e902-136">The name of a related topic.</span></span> <span data-ttu-id="1e902-137">Herhaal dit tref woord voor elk verwant onderwerp.</span><span class="sxs-lookup"><span data-stu-id="1e902-137">Repeat this keyword for each related topic.</span></span> <span data-ttu-id="1e902-138">Deze inhoud wordt weer gegeven in de sectie verwante koppelingen van het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="1e902-138">This content appears in the Related Links section of the Help topic.</span></span>

<span data-ttu-id="1e902-139">De `.LINK` inhoud van het sleutel woord kan ook een URI (Uniform Resource Identifier) bevatten naar een online versie van hetzelfde Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="1e902-139">The `.LINK` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same Help topic.</span></span> <span data-ttu-id="1e902-140">De online versie wordt geopend wanneer u de `Online` para meter van gebruikt `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="1e902-140">The online version opens when you use the `Online` parameter of `Get-Help`.</span></span> <span data-ttu-id="1e902-141">De URI moet beginnen met http of https.</span><span class="sxs-lookup"><span data-stu-id="1e902-141">The URI must begin with "http" or "https".</span></span>

## <a name="component"></a><span data-ttu-id="1e902-142">. ONDERDEEL</span><span class="sxs-lookup"><span data-stu-id="1e902-142">.COMPONENT</span></span>

<span data-ttu-id="1e902-143">De naam van de technologie of functie die de functie of het script gebruikt of waaraan deze is gerelateerd.</span><span class="sxs-lookup"><span data-stu-id="1e902-143">The name of the technology or feature that the function or script uses, or to which it is related.</span></span>
<span data-ttu-id="1e902-144">De **onderdeel** parameter van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="1e902-144">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="role"></a><span data-ttu-id="1e902-145">. Rolvak</span><span class="sxs-lookup"><span data-stu-id="1e902-145">.Role</span></span>

<span data-ttu-id="1e902-146">De naam van de gebruikersrol voor het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="1e902-146">The name of the user role for the help topic.</span></span> <span data-ttu-id="1e902-147">De para meter **Role** van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="1e902-147">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="functionality"></a><span data-ttu-id="1e902-148">. VOORZIENING</span><span class="sxs-lookup"><span data-stu-id="1e902-148">.FUNCTIONALITY</span></span>

<span data-ttu-id="1e902-149">De tref woorden die het beoogde gebruik van de functie beschrijven.</span><span class="sxs-lookup"><span data-stu-id="1e902-149">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="1e902-150">De **functie** parameter van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="1e902-150">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="forwardhelptargetname-command-name"></a><span data-ttu-id="1e902-151">. FORWARDHELPTARGETNAME \<Command-Name></span><span class="sxs-lookup"><span data-stu-id="1e902-151">.FORWARDHELPTARGETNAME \<Command-Name></span></span>

<span data-ttu-id="1e902-152">Omleiding naar het Help-onderwerp voor de opgegeven opdracht.</span><span class="sxs-lookup"><span data-stu-id="1e902-152">Redirects to the Help topic for the specified command.</span></span> <span data-ttu-id="1e902-153">U kunt gebruikers omleiden naar een Help-onderwerp, inclusief Help-onderwerpen voor een functie, script, cmdlet of provider.</span><span class="sxs-lookup"><span data-stu-id="1e902-153">You can redirect users to any Help topic, including Help topics for a function, script, cmdlet, or provider.</span></span>

## <a name="forwardhelpcategory-category"></a><span data-ttu-id="1e902-154">. FORWARDHELPCATEGORY \<Category></span><span class="sxs-lookup"><span data-stu-id="1e902-154">.FORWARDHELPCATEGORY \<Category></span></span>

<span data-ttu-id="1e902-155">Hiermee geeft u de Help-categorie van het item in op `.FORWARDHELPTARGETNAME` .</span><span class="sxs-lookup"><span data-stu-id="1e902-155">Specifies the Help category of the item in `.FORWARDHELPTARGETNAME`.</span></span> <span data-ttu-id="1e902-156">Gebruik dit tref woord om conflicten te voor komen wanneer er opdrachten met dezelfde naam zijn.</span><span class="sxs-lookup"><span data-stu-id="1e902-156">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

<span data-ttu-id="1e902-157">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="1e902-157">Valid values are:</span></span>

- <span data-ttu-id="1e902-158">Alias</span><span class="sxs-lookup"><span data-stu-id="1e902-158">Alias</span></span>
- <span data-ttu-id="1e902-159">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1e902-159">Cmdlet</span></span>
- <span data-ttu-id="1e902-160">File</span><span class="sxs-lookup"><span data-stu-id="1e902-160">HelpFile</span></span>
- <span data-ttu-id="1e902-161">Functie</span><span class="sxs-lookup"><span data-stu-id="1e902-161">Function</span></span>
- <span data-ttu-id="1e902-162">Provider</span><span class="sxs-lookup"><span data-stu-id="1e902-162">Provider</span></span>
- <span data-ttu-id="1e902-163">Algemeen</span><span class="sxs-lookup"><span data-stu-id="1e902-163">General</span></span>
- <span data-ttu-id="1e902-164">Veelgestelde vragen</span><span class="sxs-lookup"><span data-stu-id="1e902-164">FAQ</span></span>
- <span data-ttu-id="1e902-165">Woordenlijst</span><span class="sxs-lookup"><span data-stu-id="1e902-165">Glossary</span></span>
- <span data-ttu-id="1e902-166">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="1e902-166">ScriptCommand</span></span>
- <span data-ttu-id="1e902-167">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="1e902-167">ExternalScript</span></span>
- <span data-ttu-id="1e902-168">Filter</span><span class="sxs-lookup"><span data-stu-id="1e902-168">Filter</span></span>
- <span data-ttu-id="1e902-169">Alles</span><span class="sxs-lookup"><span data-stu-id="1e902-169">All</span></span>

## <a name="remotehelprunspace-pssession-variable"></a><span data-ttu-id="1e902-170">. REMOTEHELPRUNSPACE \<PSSession-variable></span><span class="sxs-lookup"><span data-stu-id="1e902-170">.REMOTEHELPRUNSPACE \<PSSession-variable></span></span>

<span data-ttu-id="1e902-171">Hiermee geeft u een sessie die het Help-onderwerp bevat.</span><span class="sxs-lookup"><span data-stu-id="1e902-171">Specifies a session that contains the Help topic.</span></span> <span data-ttu-id="1e902-172">Voer een variabele in die een PSSession bevat.</span><span class="sxs-lookup"><span data-stu-id="1e902-172">Enter a variable that contains a PSSession.</span></span> <span data-ttu-id="1e902-173">Dit sleutel woord wordt door de `Export-PSSession` cmdlet gebruikt om de Help-onderwerpen voor de geëxporteerde opdrachten te vinden.</span><span class="sxs-lookup"><span data-stu-id="1e902-173">This keyword is used by the `Export-PSSession` cmdlet to find the Help topics for the exported commands.</span></span>

## <a name="externalhelp-xml-help-file"></a><span data-ttu-id="1e902-174">. EXTERNALHELP \<XML Help File></span><span class="sxs-lookup"><span data-stu-id="1e902-174">.EXTERNALHELP \<XML Help File></span></span>

<span data-ttu-id="1e902-175">Hiermee geeft u het pad en/of de naam op van een XML-Help-bestand voor het script of de functie.</span><span class="sxs-lookup"><span data-stu-id="1e902-175">Specifies the path and/or name of an XML-based Help file for the script or function.</span></span>

<span data-ttu-id="1e902-176">Het `.EXTERNALHELP` sleutel woord vertelt de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) om hulp te krijgen voor het script of de functie in een XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="1e902-176">The `.EXTERNALHELP` keyword tells the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet to get help for the script or function in an XML-based file.</span></span> <span data-ttu-id="1e902-177">Het `.EXTERNALHELP` sleutel woord is vereist wanneer u een XML-Help-bestand gebruikt voor een script of functie.</span><span class="sxs-lookup"><span data-stu-id="1e902-177">The `.EXTERNALHELP` keyword is required when using an XML-based help file for a script or function.</span></span> <span data-ttu-id="1e902-178">Geen Help- `Get-Help` bestand voor de functie of het script wordt niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="1e902-178">Without it, `Get-Help` will not find a help file for the function or script.</span></span>

<span data-ttu-id="1e902-179">Het `.EXTERNALHELP` tref woord heeft voor rang op alle andere op opmerkingen gebaseerde Help-tref woorden.</span><span class="sxs-lookup"><span data-stu-id="1e902-179">The `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span> <span data-ttu-id="1e902-180">Wanneer `.EXTERNALHELP` aanwezig is, wordt in de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) geen Help op basis van opmerkingen weer gegeven, zelfs wanneer er geen Help-bestand wordt gevonden dat overeenkomt met de waarde van het sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="1e902-180">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

<span data-ttu-id="1e902-181">Wanneer de functie wordt geëxporteerd door een script module, moet de waarde van `.EXTERNALHELP` een bestands naam zonder pad zijn.</span><span class="sxs-lookup"><span data-stu-id="1e902-181">When the function is exported by a script module, the value of `.EXTERNALHELP` should be a filename without a path.</span></span> <span data-ttu-id="1e902-182">`Get-Help` zoekt naar het bestand in een landspecifieke submap van de module directory.</span><span class="sxs-lookup"><span data-stu-id="1e902-182">`Get-Help` looks for the file in a locale-specific subdirectory of the module directory.</span></span> <span data-ttu-id="1e902-183">Er zijn geen vereisten voor de bestands naam, maar een best practice is het gebruik van de volgende bestands indeling: `<ScriptModule>.psm1-help.xml` .</span><span class="sxs-lookup"><span data-stu-id="1e902-183">There are no requirements for the filename, but a best practice is to use the following filename format: `<ScriptModule>.psm1-help.xml`.</span></span>

<span data-ttu-id="1e902-184">Als de functie niet is gekoppeld aan een module, neemt u een pad en een bestands naam op in de waarde van het `.EXTERNALHELP` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="1e902-184">When the function is not associated with a module, include a path and filename in the value of the `.EXTERNALHELP` keyword.</span></span> <span data-ttu-id="1e902-185">Als het opgegeven pad naar het XML-bestand de submappen met de gebruikers interface-cultuur bevat, `Get-Help` doorzoekt de submappen recursief voor een XML-bestand met de naam van het script of de functie in overeenstemming met de taal vereisten die voor Windows zijn vastgesteld, net zoals voor alle Help-onderwerpen over XML.</span><span class="sxs-lookup"><span data-stu-id="1e902-185">If the specified path to the XML file contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does for all XML-based Help topics.</span></span>

<span data-ttu-id="1e902-186">Zie de [Help van Windows Power shell-cmdlets schrijven](./writing-help-for-windows-powershell-cmdlets.md)voor meer informatie over de XML-indeling van de Help-functie voor cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1e902-186">For more information about the cmdlet Help XML-based Help file format, see [Writing Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).</span></span>
