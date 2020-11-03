---
description: Hierin wordt beschreven hoe u Help-onderwerpen op basis van opmerkingen schrijft voor-functies en-scripts.
keywords: powershell,cmdlet
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: cb7ac6e7b4ec3afb95c9864665490633fdad6c5c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252711"
---
# <a name="about-comment-based-help"></a><span data-ttu-id="715ba-104">Informatie over op opmerkingen gebaseerde Help</span><span class="sxs-lookup"><span data-stu-id="715ba-104">About Comment-based Help</span></span>

## <a name="short-description"></a><span data-ttu-id="715ba-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="715ba-105">Short description</span></span>
<span data-ttu-id="715ba-106">Hierin wordt beschreven hoe u Help-onderwerpen op basis van opmerkingen schrijft voor-functies en-scripts.</span><span class="sxs-lookup"><span data-stu-id="715ba-106">Describes how to write comment-based help topics for functions and scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="715ba-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="715ba-107">Long description</span></span>

<span data-ttu-id="715ba-108">U kunt Help-onderwerpen op basis van opmerkingen schrijven voor functies en scripts door speciale tref woorden voor opmerkingen te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="715ba-108">You can write comment-based help topics for functions and scripts by using special help comment keywords.</span></span>

<span data-ttu-id="715ba-109">Met de cmdlet [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) wordt Help op basis van opmerkingen weer gegeven in dezelfde indeling waarin de Help-onderwerpen over cmdlets worden weer gegeven die zijn gegenereerd op basis van XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="715ba-109">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) cmdlet displays comment-based help in the same format in which it displays the cmdlet help topics that are generated from XML files.</span></span> <span data-ttu-id="715ba-110">Gebruikers kunnen alle para meters van `Get-Help` , zoals **gedetailleerde** , **volledige** , **voor beelden** en **online** , gebruiken om de inhoud van op opmerkingen gebaseerde Help weer te geven.</span><span class="sxs-lookup"><span data-stu-id="715ba-110">Users can use all of the parameters of `Get-Help`, such as **Detailed** , **Full** , **Examples** , and **Online** , to display the contents of comment-based help.</span></span>

<span data-ttu-id="715ba-111">U kunt ook op XML gebaseerde Help-bestanden voor functies en scripts schrijven.</span><span class="sxs-lookup"><span data-stu-id="715ba-111">You can also write XML-based help files for functions and scripts.</span></span> <span data-ttu-id="715ba-112">`Get-Help`Gebruik het sleutel woord om de cmdlet in te scha kelen om het op XML gebaseerde Help-bestand voor een functie of script te vinden `.ExternalHelp` .</span><span class="sxs-lookup"><span data-stu-id="715ba-112">To enable the `Get-Help` cmdlet to find the XML-based help file for a function or script, use the `.ExternalHelp` keyword.</span></span> <span data-ttu-id="715ba-113">Zonder dit sleutel woord `Get-Help` kunnen geen op XML gebaseerde Help-onderwerpen voor functies of scripts worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="715ba-113">Without this keyword, `Get-Help` cannot find XML-based help topics for functions or scripts.</span></span>

<span data-ttu-id="715ba-114">In dit onderwerp wordt uitgelegd hoe u Help-onderwerpen voor functies en scripts schrijft.</span><span class="sxs-lookup"><span data-stu-id="715ba-114">This topic explains how to write help topics for functions and scripts.</span></span> <span data-ttu-id="715ba-115">Zie [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)voor informatie over het weer geven van Help-onderwerpen voor functies en scripts.</span><span class="sxs-lookup"><span data-stu-id="715ba-115">For information about how to display help topics for functions and scripts, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help).</span></span>

<span data-ttu-id="715ba-116">De cmdlets [Update Help](xref:Microsoft.PowerShell.Core.Update-Help) en [Help voor opslaan](xref:Microsoft.PowerShell.Core.Save-Help) werken alleen op XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="715ba-116">The [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help) and [Save-Help](xref:Microsoft.PowerShell.Core.Save-Help) cmdlets work only on XML files.</span></span> <span data-ttu-id="715ba-117">Bij te werken Help biedt geen ondersteuning voor Help-onderwerpen op basis van opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="715ba-117">Updatable Help does not support comment-based help topics.</span></span>

## <a name="syntax-for-comment-based-help"></a><span data-ttu-id="715ba-118">Syntaxis voor op opmerkingen gebaseerde Help</span><span class="sxs-lookup"><span data-stu-id="715ba-118">Syntax for comment-based help</span></span>

<span data-ttu-id="715ba-119">De syntaxis voor op opmerkingen gebaseerde Help is als volgt:</span><span class="sxs-lookup"><span data-stu-id="715ba-119">The syntax for comment-based help is as follows:</span></span>

```
# .<help keyword>
# <help content>
```

<span data-ttu-id="715ba-120">of</span><span class="sxs-lookup"><span data-stu-id="715ba-120">or</span></span>

```
<#
.<help keyword>
<help content>
#>
```

<span data-ttu-id="715ba-121">Help op basis van opmerkingen wordt geschreven als een reeks opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="715ba-121">Comment-based help is written as a series of comments.</span></span> <span data-ttu-id="715ba-122">U kunt een opmerking toevoegen `#` vóór elke regel met opmerkingen, maar u kunt ook de `<#` symbolen en gebruiken `#>` om een opmerkingen blok te maken.</span><span class="sxs-lookup"><span data-stu-id="715ba-122">You can type a comment symbol `#` before each line of comments, or you can use the `<#` and `#>` symbols to create a comment block.</span></span> <span data-ttu-id="715ba-123">Alle regels in het opmerkingen blok worden geïnterpreteerd als opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="715ba-123">All the lines within the comment block are interpreted as comments.</span></span>

<span data-ttu-id="715ba-124">Alle regels in een Help-onderwerp op basis van opmerkingen moeten aaneengesloten zijn.</span><span class="sxs-lookup"><span data-stu-id="715ba-124">All of the lines in a comment-based help topic must be contiguous.</span></span> <span data-ttu-id="715ba-125">Als een Help-onderwerp op basis van opmerkingen een opmerking volgt die geen deel uitmaakt van het Help-onderwerp, moet er ten minste één lege regel tussen de laatste niet-Help opmerkings regel en het begin van de op opmerkingen gebaseerde Help zijn.</span><span class="sxs-lookup"><span data-stu-id="715ba-125">If a comment-based help topic follows a comment that is not part of the help topic, there must be at least one blank line between the last non-help comment line and the beginning of the comment-based help.</span></span>

<span data-ttu-id="715ba-126">Met tref woorden worden elke sectie van op opmerkingen gebaseerde Help gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="715ba-126">Keywords define each section of comment-based help.</span></span> <span data-ttu-id="715ba-127">Elk op opmerkingen gebaseerd Help-tref woord wordt voorafgegaan door een punt `.` .</span><span class="sxs-lookup"><span data-stu-id="715ba-127">Each comment-based help keyword is preceded by a dot `.`.</span></span> <span data-ttu-id="715ba-128">De tref woorden kunnen in elke wille keurige volg orde worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="715ba-128">The keywords can appear in any order.</span></span> <span data-ttu-id="715ba-129">De namen van tref woorden zijn niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="715ba-129">The keyword names are not case-sensitive.</span></span>

<span data-ttu-id="715ba-130">Het `.Description` sleutel woord gaat bijvoorbeeld vooraf op een beschrijving van een functie of script.</span><span class="sxs-lookup"><span data-stu-id="715ba-130">For example, the `.Description` keyword precedes a description of a function or script.</span></span>

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

<span data-ttu-id="715ba-131">Het commentaar blok moet ten minste één sleutel woord bevatten.</span><span class="sxs-lookup"><span data-stu-id="715ba-131">The comment block must contain at least one keyword.</span></span> <span data-ttu-id="715ba-132">Sommige tref woorden, zoals `.EXAMPLE` , kunnen vaak in hetzelfde commentaar blok worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="715ba-132">Some of the keywords, such as `.EXAMPLE`, can appear many times in the same comment block.</span></span> <span data-ttu-id="715ba-133">De Help-inhoud voor elk tref woord begint op de regel na het sleutel woord en kan meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="715ba-133">The help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

## <a name="syntax-for-comment-based-help-in-functions"></a><span data-ttu-id="715ba-134">Syntaxis voor op opmerkingen gebaseerde Help in functies</span><span class="sxs-lookup"><span data-stu-id="715ba-134">Syntax for comment-based help in functions</span></span>

<span data-ttu-id="715ba-135">Op opmerkingen gebaseerde Help voor een functie kan op een van de volgende drie locaties worden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="715ba-135">Comment-based help for a function can appear in one of three locations:</span></span>

- <span data-ttu-id="715ba-136">Aan het begin van de hoofd tekst van de functie.</span><span class="sxs-lookup"><span data-stu-id="715ba-136">At the beginning of the function body.</span></span>
- <span data-ttu-id="715ba-137">Aan het einde van de hoofd tekst van de functie.</span><span class="sxs-lookup"><span data-stu-id="715ba-137">At the end of the function body.</span></span>
- <span data-ttu-id="715ba-138">Vóór het `function` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="715ba-138">Before the `function` keyword.</span></span> <span data-ttu-id="715ba-139">Er mag niet meer dan één lege regel zijn tussen de laatste regel van de functie Help en het `function` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="715ba-139">There cannot be more than one blank line between the last line of the function help and the `function` keyword.</span></span>

<span data-ttu-id="715ba-140">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="715ba-140">For example:</span></span>

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

<span data-ttu-id="715ba-141">of</span><span class="sxs-lookup"><span data-stu-id="715ba-141">or</span></span>

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

<span data-ttu-id="715ba-142">of</span><span class="sxs-lookup"><span data-stu-id="715ba-142">or</span></span>

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a><span data-ttu-id="715ba-143">Syntaxis voor op opmerkingen gebaseerde Help in scripts</span><span class="sxs-lookup"><span data-stu-id="715ba-143">Syntax for comment-based help in scripts</span></span>

<span data-ttu-id="715ba-144">Op opmerkingen gebaseerde Help voor een script kan worden weer gegeven op een van de volgende twee locaties in het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-144">Comment-based help for a script can appear in one of the following two locations in the script.</span></span>

- <span data-ttu-id="715ba-145">Aan het begin van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="715ba-145">At the beginning of the script file.</span></span> <span data-ttu-id="715ba-146">De Help van het script kan alleen worden voorafgegaan door opmerkingen en lege regels in het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-146">Script help can be preceded in the script only by comments and blank lines.</span></span>

  <span data-ttu-id="715ba-147">Als het eerste item in de hoofd tekst van het script (na de Help) een functie declaratie is, moeten er ten minste twee lege regels tussen het einde van de script-Help en de functie declaratie zijn.</span><span class="sxs-lookup"><span data-stu-id="715ba-147">If the first item in the script body (after the help) is a function declaration, there must be at least two blank lines between the end of the script help and the function declaration.</span></span> <span data-ttu-id="715ba-148">Anders wordt de Help geïnterpreteerd als hulp voor de functie, en niet bij het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-148">Otherwise, the help is interpreted as being help for the function, not help for the script.</span></span>

- <span data-ttu-id="715ba-149">Aan het einde van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="715ba-149">At the end of the script file.</span></span> <span data-ttu-id="715ba-150">Als het script is ondertekend, plaatst u op opmerkingen gebaseerde Help aan het begin van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="715ba-150">However, if the script is signed, place Comment-based help at the beginning of the script file.</span></span> <span data-ttu-id="715ba-151">Het einde van het script wordt ingen Omen door het handtekening blok.</span><span class="sxs-lookup"><span data-stu-id="715ba-151">The end of the script is occupied by the signature block.</span></span>

<span data-ttu-id="715ba-152">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="715ba-152">For example:</span></span>

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

<span data-ttu-id="715ba-153">of</span><span class="sxs-lookup"><span data-stu-id="715ba-153">or</span></span>

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a><span data-ttu-id="715ba-154">Syntaxis voor op opmerkingen gebaseerde Help in script modules</span><span class="sxs-lookup"><span data-stu-id="715ba-154">Syntax for comment-based help in script modules</span></span>

<span data-ttu-id="715ba-155">In een script module `.psm1` gebruikt op opmerkingen gebaseerde Help de syntaxis voor-functies, niet de syntaxis voor scripts.</span><span class="sxs-lookup"><span data-stu-id="715ba-155">In a script module `.psm1`, comment-based help uses the syntax for functions, not the syntax for scripts.</span></span> <span data-ttu-id="715ba-156">U kunt de script syntaxis niet gebruiken om hulp te bieden voor alle functies die in een script module zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="715ba-156">You cannot use the script syntax to provide help for all functions defined in a script module.</span></span>

<span data-ttu-id="715ba-157">Als u bijvoorbeeld het `.ExternalHelp` tref woord gebruikt om de op XML gebaseerde Help-bestanden voor de functies in een script module te identificeren, moet u een `.ExternalHelp` Opmerking toevoegen aan elke functie.</span><span class="sxs-lookup"><span data-stu-id="715ba-157">For example, if you are using the `.ExternalHelp` keyword to identify the XML-based help files for the functions in a script module, you must add an `.ExternalHelp` comment to each function.</span></span>

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a><span data-ttu-id="715ba-158">Help-tref woorden op basis van opmerkingen</span><span class="sxs-lookup"><span data-stu-id="715ba-158">Comment-based help keywords</span></span>

<span data-ttu-id="715ba-159">Hieronder vindt u geldige Help-tref woorden op basis van opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="715ba-159">The following are valid comment-based help keywords.</span></span> <span data-ttu-id="715ba-160">Ze worden weer gegeven in de volg orde waarin ze doorgaans worden weer gegeven in een Help-onderwerp samen met het beoogde gebruik.</span><span class="sxs-lookup"><span data-stu-id="715ba-160">They are listed in the order in which they typically appear in a help topic along with their intended use.</span></span> <span data-ttu-id="715ba-161">Deze tref woorden kunnen in een wille keurige volg orde in de op opmerkingen gebaseerde Help worden weer gegeven en zijn niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="715ba-161">These keywords can appear in any order in the comment-based help, and they are not case-sensitive.</span></span>

### <a name="synopsis"></a><span data-ttu-id="715ba-162">. SAMEN VATTING</span><span class="sxs-lookup"><span data-stu-id="715ba-162">.SYNOPSIS</span></span>

<span data-ttu-id="715ba-163">Een korte beschrijving van de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-163">A brief description of the function or script.</span></span> <span data-ttu-id="715ba-164">Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="715ba-164">This keyword can be used only once in each topic.</span></span>

### <a name="description"></a><span data-ttu-id="715ba-165">. BESCHRIJVINGEN</span><span class="sxs-lookup"><span data-stu-id="715ba-165">.DESCRIPTION</span></span>

<span data-ttu-id="715ba-166">Een gedetailleerde beschrijving van de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-166">A detailed description of the function or script.</span></span> <span data-ttu-id="715ba-167">Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="715ba-167">This keyword can be used only once in each topic.</span></span>

### <a name="parameter"></a><span data-ttu-id="715ba-168">. BEPAALDE</span><span class="sxs-lookup"><span data-stu-id="715ba-168">.PARAMETER</span></span>

<span data-ttu-id="715ba-169">De beschrijving van een para meter.</span><span class="sxs-lookup"><span data-stu-id="715ba-169">The description of a parameter.</span></span> <span data-ttu-id="715ba-170">Voeg een `.PARAMETER` tref woord toe voor elke para meter in de syntaxis van de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-170">Add a `.PARAMETER` keyword for each parameter in the function or script syntax.</span></span>

<span data-ttu-id="715ba-171">Typ de parameter naam op dezelfde regel als het `.PARAMETER` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="715ba-171">Type the parameter name on the same line as the `.PARAMETER` keyword.</span></span> <span data-ttu-id="715ba-172">Typ de beschrijving van de para meter op de regels die volgen op het `.PARAMETER` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="715ba-172">Type the parameter description on the lines following the `.PARAMETER` keyword.</span></span> <span data-ttu-id="715ba-173">Windows Power shell interpreteert alle tekst tussen de `.PARAMETER` regel en het volgende tref woord of het einde van het commentaar blok als onderdeel van de parameter beschrijving.</span><span class="sxs-lookup"><span data-stu-id="715ba-173">Windows PowerShell interprets all text between the `.PARAMETER` line and the next keyword or the end of the comment block as part of the parameter description.</span></span>
<span data-ttu-id="715ba-174">De beschrijving kan alinea-einden bevatten.</span><span class="sxs-lookup"><span data-stu-id="715ba-174">The description can include paragraph breaks.</span></span>

```
.PARAMETER  <Parameter-Name>
```

<span data-ttu-id="715ba-175">De parameter trefwoorden kunnen in een wille keurige volg orde in het blok met opmerkingen worden weer gegeven, maar de functie-of script syntaxis bepaalt de volg orde waarin de para meters (en de bijbehorende beschrijvingen) in het Help-onderwerp worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="715ba-175">The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters (and their descriptions) appear in help topic.</span></span> <span data-ttu-id="715ba-176">Als u de volg orde wilt wijzigen, wijzigt u de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="715ba-176">To change the order, change the syntax.</span></span>

<span data-ttu-id="715ba-177">U kunt ook een parameter beschrijving opgeven door een opmerking in de functie-of script syntaxis direct vóór de naam van de parameter variabele in te stellen.</span><span class="sxs-lookup"><span data-stu-id="715ba-177">You can also specify a parameter description by placing a comment in the function or script syntax immediately before the parameter variable name.</span></span> <span data-ttu-id="715ba-178">Om dit te laten werken, moet u ook een opmerkingen blok met ten minste één sleutel woord hebben.</span><span class="sxs-lookup"><span data-stu-id="715ba-178">For this to work, you must also have a comment block with at least one keyword.</span></span>

<span data-ttu-id="715ba-179">Als u zowel een syntaxis Opmerking Als een `.PARAMETER` tref woord gebruikt, wordt de beschrijving die is gekoppeld aan het `.PARAMETER` tref woord gebruikt en wordt de syntaxis opmerking genegeerd.</span><span class="sxs-lookup"><span data-stu-id="715ba-179">If you use both a syntax comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the syntax comment is ignored.</span></span>

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a><span data-ttu-id="715ba-180">. Hierbij</span><span class="sxs-lookup"><span data-stu-id="715ba-180">.EXAMPLE</span></span>

<span data-ttu-id="715ba-181">Een voor beeld van een opdracht die gebruikmaakt van de functie of het script, eventueel gevolgd door voorbeeld uitvoer en een beschrijving.</span><span class="sxs-lookup"><span data-stu-id="715ba-181">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="715ba-182">Herhaal dit tref woord voor elk voor beeld.</span><span class="sxs-lookup"><span data-stu-id="715ba-182">Repeat this keyword for each example.</span></span>

### <a name="inputs"></a><span data-ttu-id="715ba-183">. INVOER</span><span class="sxs-lookup"><span data-stu-id="715ba-183">.INPUTS</span></span>

<span data-ttu-id="715ba-184">De .NET-typen objecten die kunnen worden gesluisd met de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-184">The .NET types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="715ba-185">U kunt ook een beschrijving van de invoer objecten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="715ba-185">You can also include a description of the input objects.</span></span>

### <a name="outputs"></a><span data-ttu-id="715ba-186">. UITVOER</span><span class="sxs-lookup"><span data-stu-id="715ba-186">.OUTPUTS</span></span>

<span data-ttu-id="715ba-187">Het .NET-type van de objecten die door de cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="715ba-187">The .NET type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="715ba-188">U kunt ook een beschrijving van de geretourneerde objecten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="715ba-188">You can also include a description of the returned objects.</span></span>

### <a name="notes"></a><span data-ttu-id="715ba-189">. NOTEN</span><span class="sxs-lookup"><span data-stu-id="715ba-189">.NOTES</span></span>

<span data-ttu-id="715ba-190">Aanvullende informatie over de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-190">Additional information about the function or script.</span></span>

### <a name="link"></a><span data-ttu-id="715ba-191">. GEKOPPELD</span><span class="sxs-lookup"><span data-stu-id="715ba-191">.LINK</span></span>

<span data-ttu-id="715ba-192">De naam van een verwant onderwerp.</span><span class="sxs-lookup"><span data-stu-id="715ba-192">The name of a related topic.</span></span> <span data-ttu-id="715ba-193">De waarde wordt weer gegeven op de regel onder de ". Het sleutel woord LINK en moet worden voorafgegaan door een opmerkings symbool `#` of opgenomen in het opmerkingen blok.</span><span class="sxs-lookup"><span data-stu-id="715ba-193">The value appears on the line below the ".LINK" keyword and must be preceded by a comment symbol `#` or included in the comment block.</span></span>

<span data-ttu-id="715ba-194">Herhaal het `.LINK` tref woord voor elk verwant onderwerp.</span><span class="sxs-lookup"><span data-stu-id="715ba-194">Repeat the `.LINK` keyword for each related topic.</span></span>

<span data-ttu-id="715ba-195">Deze inhoud wordt weer gegeven in de sectie verwante koppelingen van het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="715ba-195">This content appears in the Related Links section of the help topic.</span></span>

<span data-ttu-id="715ba-196">De `.Link` inhoud van het sleutel woord kan ook een URI (Uniform Resource Identifier) bevatten naar een online versie van hetzelfde Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="715ba-196">The `.Link` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same help topic.</span></span> <span data-ttu-id="715ba-197">De online versie wordt geopend wanneer u de **online** -para meter van gebruikt `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="715ba-197">The online version opens when you use the **Online** parameter of `Get-Help`.</span></span> <span data-ttu-id="715ba-198">De URI moet beginnen met http of https.</span><span class="sxs-lookup"><span data-stu-id="715ba-198">The URI must begin with "http" or "https".</span></span>

### <a name="component"></a><span data-ttu-id="715ba-199">. ONDERDEEL</span><span class="sxs-lookup"><span data-stu-id="715ba-199">.COMPONENT</span></span>

<span data-ttu-id="715ba-200">De naam van de technologie of functie die de functie of het script gebruikt of waaraan deze is gerelateerd.</span><span class="sxs-lookup"><span data-stu-id="715ba-200">The name of the technology or feature that the function or script uses, or to which it is related.</span></span> <span data-ttu-id="715ba-201">De **onderdeel** parameter van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="715ba-201">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="role"></a><span data-ttu-id="715ba-202">. ROLVAK</span><span class="sxs-lookup"><span data-stu-id="715ba-202">.ROLE</span></span>

<span data-ttu-id="715ba-203">De naam van de gebruikersrol voor het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="715ba-203">The name of the user role for the help topic.</span></span> <span data-ttu-id="715ba-204">De para meter **Role** van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="715ba-204">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="functionality"></a><span data-ttu-id="715ba-205">. VOORZIENING</span><span class="sxs-lookup"><span data-stu-id="715ba-205">.FUNCTIONALITY</span></span>

<span data-ttu-id="715ba-206">De tref woorden die het beoogde gebruik van de functie beschrijven.</span><span class="sxs-lookup"><span data-stu-id="715ba-206">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="715ba-207">De **functie** parameter van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="715ba-207">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="forwardhelptargetname"></a><span data-ttu-id="715ba-208">. FORWARDHELPTARGETNAME</span><span class="sxs-lookup"><span data-stu-id="715ba-208">.FORWARDHELPTARGETNAME</span></span>

<span data-ttu-id="715ba-209">Omleiding naar het Help-onderwerp voor de opgegeven opdracht.</span><span class="sxs-lookup"><span data-stu-id="715ba-209">Redirects to the help topic for the specified command.</span></span> <span data-ttu-id="715ba-210">U kunt gebruikers omleiden naar een Help-onderwerp, inclusief Help-onderwerpen voor een functie, script, cmdlet of provider.</span><span class="sxs-lookup"><span data-stu-id="715ba-210">You can redirect users to any help topic, including help topics for a function, script, cmdlet, or provider.</span></span>

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a><span data-ttu-id="715ba-211">. FORWARDHELPCATEGORY</span><span class="sxs-lookup"><span data-stu-id="715ba-211">.FORWARDHELPCATEGORY</span></span>

<span data-ttu-id="715ba-212">Hiermee geeft u de Help-categorie van het item in op `.ForwardHelpTargetName` .</span><span class="sxs-lookup"><span data-stu-id="715ba-212">Specifies the help category of the item in `.ForwardHelpTargetName`.</span></span> <span data-ttu-id="715ba-213">Geldige waarden zijn,,,,,,,,,, `Alias` `Cmdlet` `HelpFile` `Function` `Provider` `General` `FAQ` `Glossary` `ScriptCommand` `ExternalScript` `Filter` of `All` .</span><span class="sxs-lookup"><span data-stu-id="715ba-213">Valid values are `Alias`, `Cmdlet`, `HelpFile`, `Function`, `Provider`, `General`, `FAQ`, `Glossary`, `ScriptCommand`, `ExternalScript`, `Filter`, or `All`.</span></span> <span data-ttu-id="715ba-214">Gebruik dit tref woord om conflicten te voor komen wanneer er opdrachten met dezelfde naam zijn.</span><span class="sxs-lookup"><span data-stu-id="715ba-214">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a><span data-ttu-id="715ba-215">. REMOTEHELPRUNSPACE</span><span class="sxs-lookup"><span data-stu-id="715ba-215">.REMOTEHELPRUNSPACE</span></span>

<span data-ttu-id="715ba-216">Hiermee geeft u een sessie die het Help-onderwerp bevat.</span><span class="sxs-lookup"><span data-stu-id="715ba-216">Specifies a session that contains the help topic.</span></span> <span data-ttu-id="715ba-217">Voer een variabele in die een **PSSession** -object bevat.</span><span class="sxs-lookup"><span data-stu-id="715ba-217">Enter a variable that contains a **PSSession** object.</span></span> <span data-ttu-id="715ba-218">Dit sleutel woord wordt gebruikt door de cmdlet [export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) om de Help-onderwerpen voor de geëxporteerde opdrachten te vinden.</span><span class="sxs-lookup"><span data-stu-id="715ba-218">This keyword is used by the [Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) cmdlet to find the help topics for the exported commands.</span></span>

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a><span data-ttu-id="715ba-219">. EXTERNALHELP</span><span class="sxs-lookup"><span data-stu-id="715ba-219">.EXTERNALHELP</span></span>

<span data-ttu-id="715ba-220">Hiermee geeft u een XML-Help-bestand voor het script of de functie op.</span><span class="sxs-lookup"><span data-stu-id="715ba-220">Specifies an XML-based help file for the script or function.</span></span>

```powershell
# .EXTERNALHELP <XML Help File>
```

<span data-ttu-id="715ba-221">Het `.ExternalHelp` sleutel woord is vereist wanneer een functie of script wordt gedocumenteerd in XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="715ba-221">The `.ExternalHelp` keyword is required when a function or script is documented in XML files.</span></span> <span data-ttu-id="715ba-222">Zonder dit tref woord `Get-Help` kan het op XML gebaseerde Help-bestand niet vinden voor de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-222">Without this keyword, `Get-Help` cannot find the XML-based help file for the function or script.</span></span>

<span data-ttu-id="715ba-223">Het `.ExternalHelp` tref woord heeft voor rang op andere op opmerkingen gebaseerde Help-tref woorden.</span><span class="sxs-lookup"><span data-stu-id="715ba-223">The `.ExternalHelp` keyword takes precedence over other comment-based help keywords.</span></span> <span data-ttu-id="715ba-224">Als `.ExternalHelp` is aanwezig, wordt `Get-Help` Help op basis van opmerkingen niet weer gegeven, zelfs niet als er geen Help-onderwerp is gevonden dat overeenkomt met de waarde van het `.ExternalHelp` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="715ba-224">If `.ExternalHelp` is present, `Get-Help` does not display comment-based help, even if it cannot find a help topic that matches the value of the `.ExternalHelp` keyword.</span></span>

<span data-ttu-id="715ba-225">Als de functie wordt geëxporteerd door een module, stelt u de waarde van het `.ExternalHelp` sleutel woord in op een bestands naam zonder een pad.</span><span class="sxs-lookup"><span data-stu-id="715ba-225">If the function is exported by a module, set the value of the `.ExternalHelp` keyword to a filename without a path.</span></span> <span data-ttu-id="715ba-226">`Get-Help` zoekt naar de opgegeven bestands naam in een taalspecifieke submap van de module directory.</span><span class="sxs-lookup"><span data-stu-id="715ba-226">`Get-Help` looks for the specified file name in a language-specific subdirectory of the module directory.</span></span> <span data-ttu-id="715ba-227">Er zijn geen vereisten voor de naam van het op XML gebaseerde Help-bestand voor een functie, maar een best practice is het gebruik van de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="715ba-227">There are no requirements for the name of the XML-based help file for a function, but a best practice is to use the following format:</span></span>

```
<ScriptModule.psm1>-help.xml
```

<span data-ttu-id="715ba-228">Als de functie niet is opgenomen in een module, neemt u een pad op naar het op XML gebaseerde Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="715ba-228">If the function is not included in a module, include a path to the XML-based help file.</span></span> <span data-ttu-id="715ba-229">Als de waarde een pad bevat en het pad beschikt over taalspecifieke submappen voor de gebruikers interface, `Get-Help` doorzoekt de submappen recursief voor een XML-bestand met de naam van het script of de functie in overeenstemming met de taal vereisten die zijn ingesteld voor Windows, net zoals in een module directory.</span><span class="sxs-lookup"><span data-stu-id="715ba-229">If the value includes a path and the path contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does in a module directory.</span></span>

<span data-ttu-id="715ba-230">Zie [instructies voor het schrijven van cmdlets](https://go.microsoft.com/fwlink/?LinkID=123415) in de MSDN-bibliotheek voor meer informatie over de Help-indeling van de cmdlet-Help.</span><span class="sxs-lookup"><span data-stu-id="715ba-230">For more information about the cmdlet help XML-based help file format, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="autogenerated-content"></a><span data-ttu-id="715ba-231">Automatisch gegenereerde inhoud</span><span class="sxs-lookup"><span data-stu-id="715ba-231">Autogenerated content</span></span>

<span data-ttu-id="715ba-232">De naam, de syntaxis, de parameter lijst, de parameter kenmerk tabel, de algemene para meters en opmerkingen worden automatisch door de `Get-Help` cmdlet gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="715ba-232">The name, syntax, parameter list, parameter attribute table, common parameters, and remarks are automatically generated by the `Get-Help` cmdlet.</span></span>

### <a name="name"></a><span data-ttu-id="715ba-233">Naam</span><span class="sxs-lookup"><span data-stu-id="715ba-233">Name</span></span>

<span data-ttu-id="715ba-234">De sectie **naam** van het Help-onderwerp van een functie wordt opgehaald uit de functie naam in de syntaxis van de functie.</span><span class="sxs-lookup"><span data-stu-id="715ba-234">The **Name** section of a function help topic is taken from the function name in the function syntax.</span></span> <span data-ttu-id="715ba-235">De **naam** van een script Help-onderwerp wordt opgehaald uit de script bestandsnaam.</span><span class="sxs-lookup"><span data-stu-id="715ba-235">The **Name** of a script help topic is taken from the script filename.</span></span> <span data-ttu-id="715ba-236">Als u de naam of het hoofdletter gebruik wilt wijzigen, wijzigt u de syntaxis van de functie of de script bestands naam.</span><span class="sxs-lookup"><span data-stu-id="715ba-236">To change the name or its capitalization, change the function syntax or the script filename.</span></span>

### <a name="syntax"></a><span data-ttu-id="715ba-237">Syntax</span><span class="sxs-lookup"><span data-stu-id="715ba-237">Syntax</span></span>

<span data-ttu-id="715ba-238">De sectie **syntaxis** van het Help-onderwerp wordt gegenereerd met de syntaxis van de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-238">The **Syntax** section of the help topic is generated from the function or script syntax.</span></span> <span data-ttu-id="715ba-239">Als u details wilt toevoegen aan de syntaxis van het Help-onderwerp, zoals het .NET-type van een para meter, voegt u het detail toe aan de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="715ba-239">To add detail to the help topic syntax, such as the .NET type of a parameter, add the detail to the syntax.</span></span> <span data-ttu-id="715ba-240">Als u geen parameter type opgeeft, wordt het **object** type ingevoegd als de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="715ba-240">If you do not specify a parameter type, the **Object** type is inserted as the default value.</span></span>

### <a name="parameter-list"></a><span data-ttu-id="715ba-241">Parameter lijst</span><span class="sxs-lookup"><span data-stu-id="715ba-241">Parameter List</span></span>

<span data-ttu-id="715ba-242">De lijst met para meters in het Help-onderwerp wordt gegenereerd op basis van de functie-of script syntaxis en uit de beschrijvingen die u toevoegt met behulp van het `.Parameter` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="715ba-242">The parameter list in the help topic is generated from the function or script syntax and from the descriptions that you add by using the `.Parameter` keyword.</span></span> <span data-ttu-id="715ba-243">De functie parameters worden weer gegeven in de sectie **para meters** van het Help-onderwerp in dezelfde volg orde als waarin ze worden weer gegeven in de syntaxis van de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-243">The function parameters appear in the **Parameters** section of the help topic in the same order that they appear in the function or script syntax.</span></span> <span data-ttu-id="715ba-244">De spelling en het hoofdletter gebruik van parameter namen worden ook overgenomen uit de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="715ba-244">The spelling and capitalization of parameter names is also taken from the syntax.</span></span> <span data-ttu-id="715ba-245">Dit is niet van invloed op de parameter naam die is opgegeven door het `.Parameter` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="715ba-245">It is not affected by the parameter name specified by the `.Parameter` keyword.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="715ba-246">Algemene para meters</span><span class="sxs-lookup"><span data-stu-id="715ba-246">Common Parameters</span></span>

<span data-ttu-id="715ba-247">De **algemene para meters** worden toegevoegd aan de lijst syntaxis en para meters van het Help-onderwerp, zelfs als ze geen effect hebben.</span><span class="sxs-lookup"><span data-stu-id="715ba-247">The **Common parameters** are added to the syntax and parameter list of the help topic, even if they have no effect.</span></span> <span data-ttu-id="715ba-248">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie over de algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="715ba-248">For more information about the common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="715ba-249">Parameter kenmerk tabel</span><span class="sxs-lookup"><span data-stu-id="715ba-249">Parameter Attribute Table</span></span>

<span data-ttu-id="715ba-250">`Get-Help` Hiermee wordt de tabel met parameter kenmerken gegenereerd die wordt weer gegeven wanneer u de para meter **Full** of **para meter** van gebruikt `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="715ba-250">`Get-Help` generates the table of parameter attributes that appears when you use the **Full** or **Parameter** parameter of `Get-Help`.</span></span> <span data-ttu-id="715ba-251">De waarde van de kenmerken **vereist** , **positie** en **standaard** waarde wordt opgehaald uit de syntaxis van de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-251">The value of the **Required** , **Position** , and **Default** value attributes is taken from the function or script syntax.</span></span>

<span data-ttu-id="715ba-252">Standaard waarden en een waarde voor **joker tekens accepteren** worden niet weer gegeven in de parameter kenmerk tabel, zelfs niet wanneer ze zijn gedefinieerd in de functie of het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-252">Default values and a value for **Accept Wildcard characters** do not appear in the parameter attribute table even when they are defined in the function or script.</span></span> <span data-ttu-id="715ba-253">Geef deze informatie op in de parameter beschrijving om gebruikers te helpen.</span><span class="sxs-lookup"><span data-stu-id="715ba-253">To help users, provide this information in the parameter description.</span></span>

### <a name="remarks"></a><span data-ttu-id="715ba-254">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="715ba-254">Remarks</span></span>

<span data-ttu-id="715ba-255">De sectie **opmerkingen** van het Help-onderwerp wordt automatisch gegenereerd op basis van de functie of script naam.</span><span class="sxs-lookup"><span data-stu-id="715ba-255">The **Remarks** section of the help topic is automatically generated from the function or script name.</span></span> <span data-ttu-id="715ba-256">U kunt de inhoud niet wijzigen of beïnvloeden.</span><span class="sxs-lookup"><span data-stu-id="715ba-256">You cannot change or affect its content.</span></span>

## <a name="examples"></a><span data-ttu-id="715ba-257">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="715ba-257">Examples</span></span>

### <a name="comment-based-help-for-a-function"></a><span data-ttu-id="715ba-258">Op opmerkingen gebaseerde Help voor een functie</span><span class="sxs-lookup"><span data-stu-id="715ba-258">Comment-based Help for a Function</span></span>

<span data-ttu-id="715ba-259">De volgende voorbeeld functie bevat Help op basis van opmerkingen:</span><span class="sxs-lookup"><span data-stu-id="715ba-259">The following sample function includes comment-based help:</span></span>

```powershell
function Add-Extension
{
param ([string]$Name,[string]$Extension = "txt")
$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name.
Takes any strings for the file name or extension.

.PARAMETER Name
Specifies the file name.

.PARAMETER Extension
Specifies the extension. "Txt" is the default.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

<span data-ttu-id="715ba-260">De resultaten zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="715ba-260">The results are as follows:</span></span>

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

PARAMETERS

-Name
Specifies the file name.

Required?                    false
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-Extension
Specifies the extension. "Txt" is the default.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type
"get-help about_commonparameters".

INPUTS
None. You cannot pipe objects to Add-Extension.

OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a><span data-ttu-id="715ba-261">Parameter beschrijvingen in functie syntaxis</span><span class="sxs-lookup"><span data-stu-id="715ba-261">Parameter Descriptions in Function Syntax</span></span>

<span data-ttu-id="715ba-262">Dit voor beeld is hetzelfde als het vorige, behalve dat de parameter beschrijvingen worden ingevoegd in de syntaxis van de functie.</span><span class="sxs-lookup"><span data-stu-id="715ba-262">This example is the same as the previous one, except that the parameter descriptions are inserted in the function syntax.</span></span> <span data-ttu-id="715ba-263">Deze indeling is het handigst wanneer de beschrijvingen korter zijn.</span><span class="sxs-lookup"><span data-stu-id="715ba-263">This format is most useful when the descriptions are brief.</span></span>

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a><span data-ttu-id="715ba-264">Help op basis van opmerkingen voor een script</span><span class="sxs-lookup"><span data-stu-id="715ba-264">Comment-based Help for a Script</span></span>

<span data-ttu-id="715ba-265">Het volgende voorbeeld script bevat Help op basis van opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="715ba-265">The following sample script includes comment-based help.</span></span> <span data-ttu-id="715ba-266">Let op de lege regels tussen de afsluitende `#>` en de `Param` instructie.</span><span class="sxs-lookup"><span data-stu-id="715ba-266">Notice the blank lines between the closing `#>` and the `Param` statement.</span></span> <span data-ttu-id="715ba-267">In een script zonder `Param` instructie moeten er ten minste twee lege regels tussen de laatste opmerking in het Help-onderwerp en de eerste functie declaratie zijn.</span><span class="sxs-lookup"><span data-stu-id="715ba-267">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the help topic and the first function declaration.</span></span> <span data-ttu-id="715ba-268">Zonder deze lege regels `Get-Help` koppelt het Help-onderwerp aan de functie en niet aan het script.</span><span class="sxs-lookup"><span data-stu-id="715ba-268">Without these blank lines, `Get-Help` associates the help topic with the function, not the script.</span></span>

```powershell
<#
.SYNOPSIS

Performs monthly data updates.

.DESCRIPTION

The Update-Month.ps1 script updates the registry with new data generated
during the past month and generates a report.

.PARAMETER InputPath
Specifies the path to the CSV-based input file.

.PARAMETER OutputPath
Specifies the name and path for the CSV-based output file. By default,
MonthlyUpdates.ps1 generates a name from the date and time it runs, and
saves the output in the local directory.

.INPUTS

None. You cannot pipe objects to Update-Month.ps1.

.OUTPUTS

None. Update-Month.ps1 does not generate any output.

.EXAMPLE

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

<span data-ttu-id="715ba-269">Met de volgende opdracht wordt de Help van het script opgehaald.</span><span class="sxs-lookup"><span data-stu-id="715ba-269">The following command gets the script help.</span></span> <span data-ttu-id="715ba-270">Omdat het script zich niet in een map bevindt die wordt weer gegeven in de `$env:Path` omgevings variabele, `Get-Help` moet de opdracht die het script ophaalt het pad naar het script opgeven.</span><span class="sxs-lookup"><span data-stu-id="715ba-270">Because the script is not in a directory that is listed in the `$env:Path` environment variable, the `Get-Help` command that gets the script help must specify the script path.</span></span>

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

-InputPath
Specifies the path to the CSV-based input file.

Required?                    true
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-OutputPath
Specifies the name and path for the CSV-based output file. By
default, MonthlyUpdates.ps1 generates a name from the date
and time it runs, and saves the output in the local directory.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type,
"get-help about_commonparameters".

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a><span data-ttu-id="715ba-271">Omleiden naar een XML-bestand</span><span class="sxs-lookup"><span data-stu-id="715ba-271">Redirecting to an XML File</span></span>

<span data-ttu-id="715ba-272">U kunt op XML gebaseerde Help-onderwerpen voor functies en scripts schrijven.</span><span class="sxs-lookup"><span data-stu-id="715ba-272">You can write XML-based help topics for functions and scripts.</span></span> <span data-ttu-id="715ba-273">Hoewel Help op basis van opmerkingen eenvoudiger kan worden geïmplementeerd, is Help op basis van XML vereist voor bijwerk bare Help en om Help-onderwerpen te bieden in meerdere talen.</span><span class="sxs-lookup"><span data-stu-id="715ba-273">Although comment-based help is easier to implement, XML-based help is required for Updatable Help and to provide help topics in multiple languages.</span></span>

<span data-ttu-id="715ba-274">In het volgende voor beeld worden de eerste regels van het Update-Month.ps1 script weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="715ba-274">The following example shows the first few lines of the Update-Month.ps1 script.</span></span>
<span data-ttu-id="715ba-275">Het script maakt gebruik `.ExternalHelp` van het sleutel woord om het pad naar een op XML gebaseerd Help-onderwerp voor het script op te geven.</span><span class="sxs-lookup"><span data-stu-id="715ba-275">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based help topic for the script.</span></span>

<span data-ttu-id="715ba-276">Houd er rekening mee dat de waarde van het `.ExternalHelp` tref woord op dezelfde regel als het tref woord wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="715ba-276">Note that the value of the `.ExternalHelp` keyword appears on the same line as the keyword.</span></span> <span data-ttu-id="715ba-277">Andere plaatsen zijn niet effectief.</span><span class="sxs-lookup"><span data-stu-id="715ba-277">Any other placement is ineffective.</span></span>

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

<span data-ttu-id="715ba-278">In de volgende voor beelden worden drie geldige plaatsingen van het `.ExternalHelp` tref woord in een functie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="715ba-278">The following examples show three valid placements of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a><span data-ttu-id="715ba-279">Omleiden naar een ander Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="715ba-279">Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="715ba-280">De volgende code is een fragment van het begin van de ingebouwde Help-functie in Power shell, waarmee een scherm met Help-tekst per keer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="715ba-280">The following code is an excerpt from the beginning of the built-in help function in PowerShell, which displays one screen of help text at a time.</span></span>
<span data-ttu-id="715ba-281">Omdat in het Help-onderwerp voor de `Get-Help` cmdlet de Help-functie wordt beschreven, gebruikt de Help-functie de `.ForwardHelpTargetName` tref woorden en wordt de `.ForwardHelpCategory` gebruiker omgeleid naar het Help-onderwerp van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="715ba-281">Because the help topic for the `Get-Help` cmdlet describes the help function, the help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the `Get-Help` cmdlet help topic.</span></span>

```powershell
function help
{

<#
.FORWARDHELPTARGETNAME Get-Help
.FORWARDHELPCATEGORY Cmdlet
#>
[CmdletBinding(DefaultParameterSetName='AllUsersView')]
param(
[Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
[System.String]
${Name},
...
```

<span data-ttu-id="715ba-282">De volgende opdracht maakt gebruik van deze functie:</span><span class="sxs-lookup"><span data-stu-id="715ba-282">The following command uses this feature:</span></span>

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a><span data-ttu-id="715ba-283">Zie ook</span><span class="sxs-lookup"><span data-stu-id="715ba-283">See also</span></span>

[<span data-ttu-id="715ba-284">about_Functions</span><span class="sxs-lookup"><span data-stu-id="715ba-284">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="715ba-285">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="715ba-285">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="715ba-286">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="715ba-286">about_Scripts</span></span>](about_Scripts.md)

[<span data-ttu-id="715ba-287">Instructies voor het schrijven van cmdlets</span><span class="sxs-lookup"><span data-stu-id="715ba-287">How to Write Cmdlet Help</span></span>](https://go.microsoft.com/fwlink/?LinkID=123415)
