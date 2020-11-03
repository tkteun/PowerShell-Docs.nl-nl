---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 1a4a3f7050c3da2a73ae0d5319938117284076b7
ms.sourcegitcommit: 05f578d3fca0d9663bb1e4f76e2f14604f5303ae
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/04/2020
ms.locfileid: "93251895"
---
# <span data-ttu-id="8d8f5-103">Get-Help</span><span class="sxs-lookup"><span data-stu-id="8d8f5-103">Get-Help</span></span>

## <span data-ttu-id="8d8f5-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8d8f5-104">SYNOPSIS</span></span>
<span data-ttu-id="8d8f5-105">Geeft informatie weer over Power shell-opdrachten en-concepten.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-105">Displays information about PowerShell commands and concepts.</span></span>

## <span data-ttu-id="8d8f5-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8d8f5-106">SYNTAX</span></span>

### <span data-ttu-id="8d8f5-107">AllUsersView (standaard)</span><span class="sxs-lookup"><span data-stu-id="8d8f5-107">AllUsersView (Default)</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8d8f5-108">DetailedView</span><span class="sxs-lookup"><span data-stu-id="8d8f5-108">DetailedView</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Detailed
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8d8f5-109">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="8d8f5-109">Examples</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Examples
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8d8f5-110">Parameters</span><span class="sxs-lookup"><span data-stu-id="8d8f5-110">Parameters</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="8d8f5-111">Online</span><span class="sxs-lookup"><span data-stu-id="8d8f5-111">Online</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### <span data-ttu-id="8d8f5-112">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="8d8f5-112">ShowWindow</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## <span data-ttu-id="8d8f5-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8d8f5-113">DESCRIPTION</span></span>

<span data-ttu-id="8d8f5-114">De `Get-Help` cmdlet geeft informatie weer over Power shell-concepten en-opdrachten, waaronder cmdlets, functies, Common Information Model (CIM)-opdrachten, werk stromen, providers, aliassen en scripts.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-114">The `Get-Help` cmdlet displays information about PowerShell concepts and commands, including cmdlets, functions, Common Information Model (CIM) commands, workflows, providers, aliases, and scripts.</span></span>

<span data-ttu-id="8d8f5-115">Voor hulp bij een Power shell-cmdlet typt u `Get-Help` gevolgd door de naam van de cmdlet, zoals: `Get-Help Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-115">To get help for a PowerShell cmdlet, type `Get-Help` followed by the cmdlet name, such as: `Get-Help Get-Process`.</span></span>

<span data-ttu-id="8d8f5-116">Conceptuele Help-artikelen in Power shell beginnen met **about_** , zoals **about_Comparison_Operators**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-116">Conceptual help articles in PowerShell begin with **about_** , such as **about_Comparison_Operators**.</span></span> <span data-ttu-id="8d8f5-117">Als u alle **about_** -artikelen wilt weer geven, typt u `Get-Help about_*` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-117">To see all **about_** articles, type `Get-Help about_*`.</span></span> <span data-ttu-id="8d8f5-118">Als u een bepaald artikel wilt bekijken, typt u bijvoorbeeld `Get-Help about_<article-name>` `Get-Help about_Comparison_Operators` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-118">To see a particular article, type `Get-Help about_<article-name>`, such as `Get-Help about_Comparison_Operators`.</span></span>

<span data-ttu-id="8d8f5-119">Als u hulp wilt krijgen voor een Power shell-provider, typt u `Get-Help` gevolgd door de naam van de provider.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-119">To get help for a PowerShell provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="8d8f5-120">Als u bijvoorbeeld hulp wilt krijgen voor de certificaat provider, typt u `Get-Help Certificate` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-120">For example, to get help for the Certificate provider, type `Get-Help Certificate`.</span></span>

<span data-ttu-id="8d8f5-121">U kunt ook typen `help` of `man` , waarin één scherm met tekst wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-121">You can also type `help` or `man`, which displays one screen of text at a time.</span></span> <span data-ttu-id="8d8f5-122">Of, `<cmdlet-name> -?` is gelijk aan `Get-Help` , maar werkt alleen voor cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-122">Or, `<cmdlet-name> -?`, that is identical to `Get-Help`, but only works for cmdlets.</span></span>

<span data-ttu-id="8d8f5-123">`Get-Help` Hiermee wordt de Help-inhoud opgehaald die wordt weer gegeven van Help-bestanden op uw computer.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-123">`Get-Help` gets the help content that it displays from help files on your computer.</span></span> <span data-ttu-id="8d8f5-124">Zonder de Help-bestanden `Get-Help` wordt alleen basis informatie over cmdlets weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-124">Without the help files, `Get-Help` displays only basic information about cmdlets.</span></span> <span data-ttu-id="8d8f5-125">Sommige Power shell-modules bevatten Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-125">Some PowerShell modules include help files.</span></span> <span data-ttu-id="8d8f5-126">Vanaf Power Shell 3,0 zijn de modules die deel uitmaakt van het Windows-besturings systeem geen Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-126">Beginning in PowerShell 3.0, the modules that come with the Windows operating system don't include help files.</span></span> <span data-ttu-id="8d8f5-127">Als u de Help-bestanden voor een module in Power Shell 3,0 wilt downloaden of bijwerken, gebruikt u de `Update-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-127">To download or update the help files for a module in PowerShell 3.0, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="8d8f5-128">U kunt de Power shell Help-documenten ook online bekijken in het Microsoft Docs. Als u de online versie van een Help-bestand wilt ophalen, gebruikt u de para meter **online** , zoals: `Get-Help Get-Process -Online` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-128">You can also view the PowerShell help documents online in the Microsoft Docs. To get the online version of a help file, use the **Online** parameter, such as: `Get-Help Get-Process -Online`.</span></span> <span data-ttu-id="8d8f5-129">Raadpleeg de Microsoft Docs [Power shell-documentatie](/powershell)voor meer informatie over de Power shell-documentatie.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-129">To read all the PowerShell documentation, see the Microsoft Docs [PowerShell Documentation](/powershell).</span></span>

<span data-ttu-id="8d8f5-130">Als u typt `Get-Help` gevolgd door de exacte naam van een Help-artikel of een woord dat uniek is voor een Help-artikel, `Get-Help` wordt de inhoud van het artikel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-130">If you type `Get-Help` followed by the exact name of a help article, or by a word unique to a help article, `Get-Help` displays the article's content.</span></span> <span data-ttu-id="8d8f5-131">Als u de exacte naam van een opdracht alias opgeeft, `Get-Help` wordt de Help voor de oorspronkelijke opdracht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-131">If you specify the exact name of a command alias, `Get-Help` displays the help for the original command.</span></span> <span data-ttu-id="8d8f5-132">Als u een woord-of woord patroon opgeeft dat wordt weer gegeven in verschillende Help-artikel titels, `Get-Help` wordt een lijst met de overeenkomende titels weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-132">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span> <span data-ttu-id="8d8f5-133">Als u tekst opgeeft die niet wordt weer gegeven in de titels van Help-artikelen, `Get-Help` wordt een lijst met artikelen weer gegeven die de tekst in de inhoud bevat.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-133">If you enter any text that doesn't appear in any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="8d8f5-134">`Get-Help` kan Help-artikelen voor alle ondersteunde talen en land instellingen ophalen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-134">`Get-Help` can get help articles for all supported languages and locales.</span></span> <span data-ttu-id="8d8f5-135">`Get-Help` eerst zoekt u naar Help-bestanden in de land instelling die voor Windows is ingesteld, vervolgens in de bovenliggende land instelling, bijvoorbeeld **PT** voor **pt-br** , en vervolgens in een terugval land instelling.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-135">`Get-Help` first looks for help files in the locale set for Windows, then in the parent locale, such as **pt** for **pt-BR** , and then in a fallback locale.</span></span> <span data-ttu-id="8d8f5-136">Als er vanaf Power Shell 3,0 `Get-Help` geen hulp wordt gevonden in de terugval land instelling, zoekt het naar Help-artikelen in het Engels, **en-US** voordat een fout bericht wordt geretourneerd of automatisch gegenereerde Help wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-136">Beginning in PowerShell 3.0, if `Get-Help` doesn't find help in the fallback locale, it looks for help articles in English, **en-US** , before it returns an error message or displaying autogenerated help.</span></span>

<span data-ttu-id="8d8f5-137">Zie about_Command_Syntax voor meer informatie over de symbolen die `Get-Help` worden weer gegeven in het [about_Command_Syntax](./About/about_Command_Syntax.md)opdracht syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-137">For information about the symbols that `Get-Help` displays in the command syntax diagram, see [about_Command_Syntax](./About/about_Command_Syntax.md).</span></span>
<span data-ttu-id="8d8f5-138">Zie [about_Parameters](./About/about_Parameters.md)voor meer informatie over parameter kenmerken, zoals **vereist** en **positie**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-138">For information about parameter attributes, such as **Required** and **Position** , see [about_Parameters](./About/about_Parameters.md).</span></span>

>[!NOTE]
> <span data-ttu-id="8d8f5-139">In Power Shell 3,0 en Power Shell 4,0 `Get-Help` kunt **About** u geen artikelen in modules vinden, tenzij de module in de huidige sessie is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-139">In PowerShell 3.0 and PowerShell 4.0, `Get-Help` can't find **About** articles in modules unless the module is imported into the current session.</span></span> <span data-ttu-id="8d8f5-140">Dit is een bekend probleem.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-140">This is a known issue.</span></span> <span data-ttu-id="8d8f5-141">Als u wilt **weten over** artikelen in een module, importeert u de module, hetzij met behulp van de cmdlet, hetzij `Import-Module` door een cmdlet uit te voeren die is opgenomen in de module.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-141">To get **About** articles in a module, import the module, either by using the `Import-Module` cmdlet or by running a cmdlet that's included in the module.</span></span>

## <span data-ttu-id="8d8f5-142">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8d8f5-142">EXAMPLES</span></span>

### <span data-ttu-id="8d8f5-143">Voor beeld 1: Basic Help-informatie over een cmdlet weer geven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-143">Example 1: Display basic help information about a cmdlet</span></span>

<span data-ttu-id="8d8f5-144">In deze voor beelden worden algemene Help-informatie over de cmdlet weer gegeven `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-144">These examples display basic help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

<span data-ttu-id="8d8f5-145">`Get-Help <cmdlet-name>` is de eenvoudigste en standaard syntaxis van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-145">`Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet.</span></span> <span data-ttu-id="8d8f5-146">U kunt de para meter **name** weglaten.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-146">You can omit the **Name** parameter.</span></span>

<span data-ttu-id="8d8f5-147">De syntaxis `<cmdlet-name> -?` werkt alleen voor cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-147">The syntax `<cmdlet-name> -?` works only for cmdlets.</span></span>

### <span data-ttu-id="8d8f5-148">Voor beeld 2: basis informatie één pagina tegelijk weer geven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-148">Example 2: Display basic information one page at a time</span></span>

<span data-ttu-id="8d8f5-149">In deze voor beelden worden algemene Help-informatie over de `Format-Table` cmdlet per pagina weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-149">These examples display basic help information about the `Format-Table` cmdlet one page at a time.</span></span>

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

<span data-ttu-id="8d8f5-150">`help` is een functie die `Get-Help` de cmdlet intern uitvoert en het resultaat één pagina per keer weergeeft.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-150">`help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.</span></span>

<span data-ttu-id="8d8f5-151">`man` is een alias voor de `help` functie.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-151">`man` is an alias for the `help` function.</span></span>

<span data-ttu-id="8d8f5-152">`Get-Help Format-Table` Hiermee wordt het object omlaag verzonden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-152">`Get-Help Format-Table` sends the object down the pipeline.</span></span> <span data-ttu-id="8d8f5-153">`Out-Host -Paging` Hiermee wordt de uitvoer van de pijp lijn ontvangen en één pagina tegelijk weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-153">`Out-Host -Paging` receives the output from the pipeline and displays it one page at a time.</span></span> <span data-ttu-id="8d8f5-154">Zie [out-host](Out-Host.md)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-154">For more information, see [Out-Host](Out-Host.md).</span></span>

### <span data-ttu-id="8d8f5-155">Voor beeld 3: meer informatie voor een cmdlet weer geven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-155">Example 3: Display more information for a cmdlet</span></span>

<span data-ttu-id="8d8f5-156">In deze voor beelden wordt gedetailleerdere Help-informatie over de cmdlet weer gegeven `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-156">These examples display more detailed help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

<span data-ttu-id="8d8f5-157">De **gedetailleerde** weer gave van het Help-artikel bevat para meters en voor beelden.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-157">The **Detailed** parameter displays the help article's detailed view that includes parameter descriptions and examples.</span></span>

<span data-ttu-id="8d8f5-158">Met de **volledige** para meter wordt de volledige weer gave van het Help-artikel weer gegeven, inclusief parameter beschrijvingen, voor beelden, invoer-en uitvoer object typen en aanvullende notities.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-158">The **Full** parameter displays the help article's full view that includes parameter descriptions, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="8d8f5-159">De **gedetailleerde** en **volledige** para meters zijn alleen effectief voor de opdrachten met Help-bestanden die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-159">The **Detailed** and **Full** parameters are effective only for the commands that have help files installed on the computer.</span></span> <span data-ttu-id="8d8f5-160">De para meters zijn niet effectief voor de conceptuele ( **about_** ) Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-160">The parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="8d8f5-161">Voor beeld 4: geselecteerde onderdelen van een cmdlet weer geven met behulp van para meters</span><span class="sxs-lookup"><span data-stu-id="8d8f5-161">Example 4: Display selected parts of a cmdlet by using parameters</span></span>

<span data-ttu-id="8d8f5-162">In deze voor beelden worden geselecteerde delen van de Help van de cmdlet weer gegeven `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-162">These examples display selected portions of the `Format-Table` cmdlet help.</span></span>

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

<span data-ttu-id="8d8f5-163">De **voor beelden** -para meters bevatten de secties **naam** en samen **vatting** van het Help-bestand en alle voor beelden.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-163">The **Examples** parameter displays the help file's **NAME** and **SYNOPSIS** sections, and all the Examples.</span></span> <span data-ttu-id="8d8f5-164">U kunt geen voorbeeld nummer opgeven, omdat de para meter **voor beelden** een switch parameter is.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-164">You can't specify an Example number because the **Examples** parameter is a switch parameter.</span></span>

<span data-ttu-id="8d8f5-165">Met de **parameter** parameter worden alleen de beschrijvingen van de opgegeven para meters weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-165">The **Parameter** parameter displays only the descriptions of the specified parameters.</span></span> <span data-ttu-id="8d8f5-166">Als u alleen het sterretje ( `*` )-Joker teken opgeeft, worden de beschrijvingen van alle para meters weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-166">If you specify only the asterisk (`*`) wildcard character, it displays the descriptions of all parameters.</span></span>
<span data-ttu-id="8d8f5-167">Als de **para meter** een parameter naam opgeeft, zoals **GroupBy** , wordt informatie over die para meter weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-167">When **Parameter** specifies a parameter name such as **GroupBy** , information about that parameter is shown.</span></span>

<span data-ttu-id="8d8f5-168">Deze para meters zijn niet effectief voor de conceptuele ( **about_** ) Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-168">These parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="8d8f5-169">Voor beeld 5: online versie van Help weer geven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-169">Example 5: Display online version of help</span></span>

<span data-ttu-id="8d8f5-170">In dit voor beeld wordt de online versie van het Help-artikel voor de `Format-Table` cmdlet in de standaard webbrowser weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-170">This example displays the online version of the help article for the `Format-Table` cmdlet in your default web browser.</span></span>

```powershell
Get-Help Format-Table -Online
```

### <span data-ttu-id="8d8f5-171">Voor beeld 6: Help over het Help-systeem weer geven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-171">Example 6: Display help about the help system</span></span>

<span data-ttu-id="8d8f5-172">De `Get-Help` cmdlet zonder para meters geeft informatie weer over het Help-systeem van Power shell.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-172">The `Get-Help` cmdlet without parameters displays information about the PowerShell help system.</span></span>

```powershell
Get-Help
```

### <span data-ttu-id="8d8f5-173">Voor beeld 7: beschik bare Help-artikelen weer geven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-173">Example 7: Display available help articles</span></span>

<span data-ttu-id="8d8f5-174">In dit voor beeld wordt een lijst weer gegeven met alle Help-artikelen die op uw computer beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-174">This example displays a list of all help articles available on your computer.</span></span>

```powershell
Get-Help *
```

### <span data-ttu-id="8d8f5-175">Voor beeld 8: een lijst met conceptuele artikelen weer geven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-175">Example 8: Display a list of conceptual articles</span></span>

<span data-ttu-id="8d8f5-176">In dit voor beeld wordt een lijst weer gegeven met de conceptuele artikelen die in de Help van Power shell zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-176">This example displays a list of the conceptual articles included in PowerShell help.</span></span> <span data-ttu-id="8d8f5-177">Al deze artikelen beginnen met de tekens **about_**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-177">All these articles begin with the characters **about_**.</span></span> <span data-ttu-id="8d8f5-178">Typ bijvoorbeeld om een bepaald Help-bestand weer te geven `Get-Help \<about_article-name\>` `Get-Help about_Signing` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-178">To display a particular help file, type `Get-Help \<about_article-name\>`, for example, `Get-Help about_Signing`.</span></span>

<span data-ttu-id="8d8f5-179">Alleen de conceptuele artikelen met Help-bestanden die op uw computer zijn geïnstalleerd, worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-179">Only the conceptual articles that have help files installed on your computer are displayed.</span></span> <span data-ttu-id="8d8f5-180">Zie [Update-Help](Update-Help.md)voor informatie over het downloaden en installeren van Help-bestanden in power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-180">For information about downloading and installing help files in PowerShell 3.0, see [Update-Help](Update-Help.md).</span></span>

```powershell
Get-Help about_*
```

### <span data-ttu-id="8d8f5-181">Voor beeld 9: zoeken naar een woord in cmdlet Help</span><span class="sxs-lookup"><span data-stu-id="8d8f5-181">Example 9: Search for a word in cmdlet help</span></span>

<span data-ttu-id="8d8f5-182">In dit voor beeld ziet u hoe u naar een woord zoekt in een Help-artikel over cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-182">This example shows how to search for a word in a cmdlet help article.</span></span>

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

<span data-ttu-id="8d8f5-183">`Get-Help` gebruikt de **volledige** para meter voor het verkrijgen van Help-informatie voor `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-183">`Get-Help` uses the **Full** parameter to get help information for `Add-Member`.</span></span> <span data-ttu-id="8d8f5-184">Het **MamlCommandHelpInfo** -object wordt verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-184">The **MamlCommandHelpInfo** object is sent down the pipeline.</span></span> <span data-ttu-id="8d8f5-185">`Out-String` maakt gebruik van de para meter **Stream** om het object te converteren naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-185">`Out-String` uses the **Stream** parameter to convert the object into a string.</span></span> <span data-ttu-id="8d8f5-186">`Select-String` maakt gebruik van de **patroon** parameter om te zoeken naar de teken reeks voor **Clixml**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-186">`Select-String` uses the **Pattern** parameter to search the string for **Clixml**.</span></span>

### <span data-ttu-id="8d8f5-187">Voor beeld 10: een lijst met artikelen weer geven die een woord bevatten</span><span class="sxs-lookup"><span data-stu-id="8d8f5-187">Example 10: Display a list of articles that include a word</span></span>

<span data-ttu-id="8d8f5-188">In dit voor beeld wordt een lijst weer gegeven met artikelen die het woord **externe toegang** bevatten.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-188">This example displays a list of articles that include the word **remoting**.</span></span>

<span data-ttu-id="8d8f5-189">Wanneer u een woord invoert dat niet wordt weer gegeven in een artikel titel, `Get-Help` wordt een lijst met artikelen weer gegeven waarin dat woord is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-189">When you enter a word that doesn't appear in any article title, `Get-Help` displays a list of articles that include that word.</span></span>

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### <span data-ttu-id="8d8f5-190">Voor beeld 11: specifieke Help voor de provider weer geven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-190">Example 11: Display provider-specific help</span></span>

<span data-ttu-id="8d8f5-191">In dit voor beeld ziet u twee manieren om de provider-specifieke Help voor te verkrijgen `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-191">This example shows two ways of getting the provider-specific help for `Get-Item`.</span></span> <span data-ttu-id="8d8f5-192">Met deze opdrachten krijgt u informatie over het gebruik van de `Get-Item` cmdlet in het **DataCollection** -knoop punt van de power shell-SQL server provider.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-192">These commands get help that explains how to use the `Get-Item` cmdlet in the PowerShell SQL Server provider's **DataCollection** node.</span></span>

<span data-ttu-id="8d8f5-193">In het eerste voor beeld wordt de `Get-Help` para meter **Path** gebruikt om het pad van de SQL server provider op te geven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-193">The first example uses the `Get-Help` **Path** parameter to specify the SQL Server provider's path.</span></span>
<span data-ttu-id="8d8f5-194">Omdat het pad van de provider is opgegeven, kunt u de opdracht vanaf een wille keurige pad-locatie uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-194">Because the provider's path is specified, you can run the command from any path location.</span></span>

<span data-ttu-id="8d8f5-195">In het tweede voor beeld wordt gebruikgemaakt `Set-Location` van om naar het pad van de SQL server provider te navigeren.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-195">The second example uses `Set-Location` to navigate to the SQL Server provider's path.</span></span> <span data-ttu-id="8d8f5-196">Vanaf die locatie is de para meter **Path** niet nodig `Get-Help` om de provider-specifieke hulp te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-196">From that location, the **Path** parameter isn't needed for `Get-Help` to get the provider-specific help.</span></span>

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### <span data-ttu-id="8d8f5-197">Voor beeld 12: Help voor een script weer geven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-197">Example 12: Display help for a script</span></span>

<span data-ttu-id="8d8f5-198">In dit voor beeld wordt Help voor de `MyScript.ps1 script` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-198">This example gets help for the `MyScript.ps1 script`.</span></span> <span data-ttu-id="8d8f5-199">Zie [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)voor meer informatie over het schrijven van Help voor uw functies en scripts.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-199">For information about how to write help for your functions and scripts, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span></span>

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## <span data-ttu-id="8d8f5-200">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8d8f5-200">PARAMETERS</span></span>

### <span data-ttu-id="8d8f5-201">-Categorie</span><span class="sxs-lookup"><span data-stu-id="8d8f5-201">-Category</span></span>

<span data-ttu-id="8d8f5-202">Geeft alleen Help-informatie weer voor items in de opgegeven categorie en de bijbehorende aliassen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-202">Displays help only for items in the specified category and their aliases.</span></span> <span data-ttu-id="8d8f5-203">Conceptuele artikelen vindt u in de categorie **Help file** .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-203">Conceptual articles are in the **HelpFile** category.</span></span>

<span data-ttu-id="8d8f5-204">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="8d8f5-204">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="8d8f5-205">Alias</span><span class="sxs-lookup"><span data-stu-id="8d8f5-205">Alias</span></span>
- <span data-ttu-id="8d8f5-206">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8d8f5-206">Cmdlet</span></span>
- <span data-ttu-id="8d8f5-207">Provider</span><span class="sxs-lookup"><span data-stu-id="8d8f5-207">Provider</span></span>
- <span data-ttu-id="8d8f5-208">Algemeen</span><span class="sxs-lookup"><span data-stu-id="8d8f5-208">General</span></span>
- <span data-ttu-id="8d8f5-209">Veelgestelde vragen</span><span class="sxs-lookup"><span data-stu-id="8d8f5-209">FAQ</span></span>
- <span data-ttu-id="8d8f5-210">Woordenlijst</span><span class="sxs-lookup"><span data-stu-id="8d8f5-210">Glossary</span></span>
- <span data-ttu-id="8d8f5-211">File</span><span class="sxs-lookup"><span data-stu-id="8d8f5-211">HelpFile</span></span>
- <span data-ttu-id="8d8f5-212">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="8d8f5-212">ScriptCommand</span></span>
- <span data-ttu-id="8d8f5-213">Functie</span><span class="sxs-lookup"><span data-stu-id="8d8f5-213">Function</span></span>
- <span data-ttu-id="8d8f5-214">Filteren</span><span class="sxs-lookup"><span data-stu-id="8d8f5-214">Filter</span></span>
- <span data-ttu-id="8d8f5-215">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="8d8f5-215">ExternalScript</span></span>
- <span data-ttu-id="8d8f5-216">Alles</span><span class="sxs-lookup"><span data-stu-id="8d8f5-216">All</span></span>
- <span data-ttu-id="8d8f5-217">DefaultHelp</span><span class="sxs-lookup"><span data-stu-id="8d8f5-217">DefaultHelp</span></span>
- <span data-ttu-id="8d8f5-218">Werkstroom</span><span class="sxs-lookup"><span data-stu-id="8d8f5-218">Workflow</span></span>
- <span data-ttu-id="8d8f5-219">Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="8d8f5-219">DscResource</span></span>
- <span data-ttu-id="8d8f5-220">Klasse</span><span class="sxs-lookup"><span data-stu-id="8d8f5-220">Class</span></span>
- <span data-ttu-id="8d8f5-221">Configuration</span><span class="sxs-lookup"><span data-stu-id="8d8f5-221">Configuration</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d8f5-222">-Onderdeel</span><span class="sxs-lookup"><span data-stu-id="8d8f5-222">-Component</span></span>

<span data-ttu-id="8d8f5-223">Geeft opdrachten weer met de opgegeven onderdeel waarde, zoals **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-223">Displays commands with the specified component value, such as **Exchange**.</span></span> <span data-ttu-id="8d8f5-224">Voer een onderdeel naam in.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-224">Enter a component name.</span></span>
<span data-ttu-id="8d8f5-225">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-225">Wildcard characters are permitted.</span></span> <span data-ttu-id="8d8f5-226">Deze para meter heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-226">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8d8f5-227">-Gedetailleerd</span><span class="sxs-lookup"><span data-stu-id="8d8f5-227">-Detailed</span></span>

<span data-ttu-id="8d8f5-228">Hiermee worden parameter beschrijvingen en voor beelden toegevoegd aan de Basic Help-weer gave.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-228">Adds parameter descriptions and examples to the basic help display.</span></span> <span data-ttu-id="8d8f5-229">Deze para meter is alleen effectief als de Help-bestanden op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-229">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="8d8f5-230">Dit heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-230">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d8f5-231">-Voor beelden</span><span class="sxs-lookup"><span data-stu-id="8d8f5-231">-Examples</span></span>

<span data-ttu-id="8d8f5-232">Alleen de naam, de samen vatting en de voor beelden worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-232">Displays only the name, synopsis, and examples.</span></span> <span data-ttu-id="8d8f5-233">Als u alleen de voor beelden wilt weer geven, typt u `(Get-Help \<cmdlet-name\>).Examples` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-233">To display only the examples, type `(Get-Help \<cmdlet-name\>).Examples`.</span></span>

<span data-ttu-id="8d8f5-234">Deze para meter is alleen effectief als de Help-bestanden op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-234">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="8d8f5-235">Dit heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-235">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d8f5-236">-Volledig</span><span class="sxs-lookup"><span data-stu-id="8d8f5-236">-Full</span></span>

<span data-ttu-id="8d8f5-237">Hiermee wordt het volledige Help-artikel voor een cmdlet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-237">Displays the entire help article for a cmdlet.</span></span> <span data-ttu-id="8d8f5-238">**Volledige** bevat parameter beschrijvingen en kenmerken, voor beelden, invoer-en uitvoer object typen en aanvullende notities.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-238">**Full** includes parameter descriptions and attributes, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="8d8f5-239">Deze para meter is alleen effectief als de Help-bestanden op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-239">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="8d8f5-240">Dit heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-240">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d8f5-241">-Functionaliteit</span><span class="sxs-lookup"><span data-stu-id="8d8f5-241">-Functionality</span></span>

<span data-ttu-id="8d8f5-242">Geeft Help weer voor items met de opgegeven functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-242">Displays help for items with the specified functionality.</span></span> <span data-ttu-id="8d8f5-243">Voer de functionaliteit in.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-243">Enter the functionality.</span></span> <span data-ttu-id="8d8f5-244">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-244">Wildcard characters are permitted.</span></span> <span data-ttu-id="8d8f5-245">Deze para meter heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-245">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8d8f5-246">-Name</span><span class="sxs-lookup"><span data-stu-id="8d8f5-246">-Name</span></span>

<span data-ttu-id="8d8f5-247">Hiermee krijgt u hulp bij de opgegeven opdracht of het concept.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-247">Gets help about the specified command or concept.</span></span> <span data-ttu-id="8d8f5-248">Voer de naam in van een cmdlet, functie, provider, script of werk stroom, zoals `Get-Member` een conceptuele artikel naam, zoals `about_Objects` of een alias, zoals `ls` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-248">Enter the name of a cmdlet, function, provider, script, or workflow, such as `Get-Member`, a conceptual article name, such as `about_Objects`, or an alias, such as `ls`.</span></span> <span data-ttu-id="8d8f5-249">Joker tekens zijn toegestaan in de namen van cmdlets en providers, maar u kunt geen joker tekens gebruiken om de namen te vinden van de Help-en Help-artikelen over functies.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-249">Wildcard characters are permitted in cmdlet and provider names, but you can't use wildcard characters to find the names of function help and script help articles.</span></span>

<span data-ttu-id="8d8f5-250">Als u hulp nodig hebt voor een script dat zich niet in een pad bevindt dat wordt vermeld in de `$env:Path` omgevings variabele, typt u het pad en de bestands naam van het script.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-250">To get help for a script that isn't located in a path that's listed in the `$env:Path` environment variable, type the script's path and file name.</span></span>

<span data-ttu-id="8d8f5-251">Als u de exacte naam van een Help-artikel opgeeft, `Get-Help` wordt de inhoud van het artikel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-251">If you enter the exact name of a help article, `Get-Help` displays the article contents.</span></span>

<span data-ttu-id="8d8f5-252">Als u een woord-of woord patroon opgeeft dat wordt weer gegeven in verschillende Help-artikel titels, `Get-Help` wordt een lijst met de overeenkomende titels weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-252">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span>

<span data-ttu-id="8d8f5-253">Als u tekst invoert die niet overeenkomt met de titels van Help-artikelen, `Get-Help` wordt een lijst met artikelen weer gegeven die de tekst in de inhoud bevat.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-253">If you enter any text that doesn't match any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="8d8f5-254">De namen van conceptuele artikelen, zoals `about_Objects` , moeten worden ingevoerd in het Engels, zelfs in niet-Engelse versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-254">The names of conceptual articles, such as `about_Objects`, must be entered in English, even in non-English versions of PowerShell.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="8d8f5-255">-Online</span><span class="sxs-lookup"><span data-stu-id="8d8f5-255">-Online</span></span>

<span data-ttu-id="8d8f5-256">Hiermee wordt de online versie van een Help-artikel in de standaard browser weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-256">Displays the online version of a help article in the default browser.</span></span> <span data-ttu-id="8d8f5-257">Deze para meter is alleen geldig voor de Help-artikelen voor cmdlets, functies, werk stromen en scripts.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-257">This parameter is valid only for cmdlet, function, workflow, and script help articles.</span></span> <span data-ttu-id="8d8f5-258">U kunt de **online** para meter niet gebruiken `Get-Help` in een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-258">You can't use the **Online** parameter with `Get-Help` in a remote session.</span></span>

<span data-ttu-id="8d8f5-259">Voor informatie over het ondersteunen van deze functie in Help-artikelen die u schrijft, raadpleegt u [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)en [ondersteunende online Help](/powershell/scripting/developer/module/supporting-online-help)en schrijft u de [Help voor Power shell-cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="8d8f5-259">For information about supporting this feature in help articles that you write, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md), and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help), and [Writing Help for PowerShell Cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d8f5-260">-Para meter</span><span class="sxs-lookup"><span data-stu-id="8d8f5-260">-Parameter</span></span>

<span data-ttu-id="8d8f5-261">Geeft alleen de gedetailleerde beschrijvingen van de opgegeven para meters weer.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-261">Displays only the detailed descriptions of the specified parameters.</span></span> <span data-ttu-id="8d8f5-262">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-262">Wildcards are permitted.</span></span> <span data-ttu-id="8d8f5-263">Deze para meter heeft geen invloed op de weer gave van conceptuele ( **About_** ) Help.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-263">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8d8f5-264">-Path</span><span class="sxs-lookup"><span data-stu-id="8d8f5-264">-Path</span></span>

<span data-ttu-id="8d8f5-265">Hiermee wordt informatie opgehaald over de werking van de cmdlet in het opgegeven pad van de provider.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-265">Gets help that explains how the cmdlet works in the specified provider path.</span></span> <span data-ttu-id="8d8f5-266">Voer een pad voor de Power shell-provider in.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-266">Enter a PowerShell provider path.</span></span>

<span data-ttu-id="8d8f5-267">Met deze para meter wordt een aangepaste versie van een Help-artikel van de cmdlet opgehaald waarin wordt uitgelegd hoe de cmdlet werkt in het opgegeven pad van de Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-267">This parameter gets a customized version of a cmdlet help article that explains how the cmdlet works in the specified PowerShell provider path.</span></span> <span data-ttu-id="8d8f5-268">Deze para meter is alleen effectief voor Help over een provider-cmdlet en alleen wanneer de provider een aangepaste versie van het Help-artikel van de provider-cmdlet in het Help-bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-268">This parameter is effective only for help about a provider cmdlet and only when the provider includes a custom version of the provider cmdlet help article in its help file.</span></span> <span data-ttu-id="8d8f5-269">Als u deze para meter wilt gebruiken, installeert u het Help-bestand voor de module die de provider bevat.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-269">To use this parameter, install the help file for the module that includes the provider.</span></span>

<span data-ttu-id="8d8f5-270">Als u de Help voor aangepaste cmdlets voor een pad naar een provider wilt bekijken, gaat u naar de locatie van het provider pad en voert u een `Get-Help` opdracht in, of u kunt vanuit elke locatie de para meter **Path** van `Get-Help` opgeven om het pad naar de provider op te geven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-270">To see the custom cmdlet help for a provider path, go to the provider path location and enter a `Get-Help` command or, from any path location, use the **Path** parameter of `Get-Help` to specify the provider path.</span></span> <span data-ttu-id="8d8f5-271">U kunt ook een aangepaste cmdlet Help online vinden in de Help-sectie van de provider van de Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-271">You can also find custom cmdlet help online in the provider help section of the help articles.</span></span>

<span data-ttu-id="8d8f5-272">Zie [about_Providers](./About/about_Providers.md)voor meer informatie over Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-272">For more information about PowerShell providers, see [about_Providers](./About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8d8f5-273">-Rol</span><span class="sxs-lookup"><span data-stu-id="8d8f5-273">-Role</span></span>

<span data-ttu-id="8d8f5-274">Geeft Help aangepast voor de opgegeven gebruikersrol.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-274">Displays help customized for the specified user role.</span></span> <span data-ttu-id="8d8f5-275">Voer een rol in.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-275">Enter a role.</span></span> <span data-ttu-id="8d8f5-276">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-276">Wildcard characters are permitted.</span></span>

<span data-ttu-id="8d8f5-277">Voer de rol in die de gebruiker in een organisatie speelt.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-277">Enter the role that the user plays in an organization.</span></span> <span data-ttu-id="8d8f5-278">Sommige cmdlets geven verschillende tekst in hun Help-bestanden weer op basis van de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-278">Some cmdlets display different text in their help files based on the value of this parameter.</span></span> <span data-ttu-id="8d8f5-279">Deze para meter heeft geen effect op de Help voor de kern-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-279">This parameter has no effect on help for the core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8d8f5-280">-ShowWindow</span><span class="sxs-lookup"><span data-stu-id="8d8f5-280">-ShowWindow</span></span>

<span data-ttu-id="8d8f5-281">Hiermee wordt het Help-onderwerp in een venster weer gegeven om gemakkelijker te kunnen lezen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-281">Displays the help topic in a window for easier reading.</span></span> <span data-ttu-id="8d8f5-282">Het venster bevat een zoek functie voor **zoeken** en een **instellingen** venster waarmee u opties voor de weer gave kunt instellen, inclusief opties voor het weer geven van alleen geselecteerde secties van een Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-282">The window includes a **Find** search feature and a **Settings** box that lets you set options for the display, including options to display only selected sections of a help topic.</span></span>

<span data-ttu-id="8d8f5-283">De **ShowWindow** -para meter ondersteunt Help-onderwerpen voor opdrachten (cmdlets, functies, CIM-opdrachten, scripts) en conceptuele **informatie over** artikelen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-283">The **ShowWindow** parameter supports help topics for commands (cmdlets, functions, CIM commands, scripts) and conceptual **About** articles.</span></span> <span data-ttu-id="8d8f5-284">De Help van de provider wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-284">It does not support provider help.</span></span>

<span data-ttu-id="8d8f5-285">Deze para meter is opnieuw geïntroduceerd in Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-285">This parameter was reintroduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8d8f5-286">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8d8f5-286">CommonParameters</span></span>

<span data-ttu-id="8d8f5-287">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-287">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8d8f5-288">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-288">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8d8f5-289">INVOER</span><span class="sxs-lookup"><span data-stu-id="8d8f5-289">INPUTS</span></span>

### <span data-ttu-id="8d8f5-290">Geen</span><span class="sxs-lookup"><span data-stu-id="8d8f5-290">None</span></span>

<span data-ttu-id="8d8f5-291">U kunt geen objecten naar beneden verplaatsen in de pijp lijn `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="8d8f5-291">You can't send objects down the pipeline to `Get-Help`.</span></span>

## <span data-ttu-id="8d8f5-292">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8d8f5-292">OUTPUTS</span></span>

### <span data-ttu-id="8d8f5-293">ExtendedCmdletHelpInfo</span><span class="sxs-lookup"><span data-stu-id="8d8f5-293">ExtendedCmdletHelpInfo</span></span>

<span data-ttu-id="8d8f5-294">Als u uitvoert `Get-Help` op een opdracht die geen Help-bestand heeft, `Get-Help` retourneert een **ExtendedCmdletHelpInfo** -object dat automatisch gegenereerde Help vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-294">If you run `Get-Help` on a command that doesn't have a help file, `Get-Help` returns an **ExtendedCmdletHelpInfo** object that represents autogenerated help.</span></span>

### <span data-ttu-id="8d8f5-295">System. String</span><span class="sxs-lookup"><span data-stu-id="8d8f5-295">System.String</span></span>

<span data-ttu-id="8d8f5-296">Als u een conceptueel Help-artikel krijgt, `Get-Help` retourneert dit als een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-296">If you get a conceptual help article, `Get-Help` returns it as a string.</span></span>

### <span data-ttu-id="8d8f5-297">MamlCommandHelpInfo</span><span class="sxs-lookup"><span data-stu-id="8d8f5-297">MamlCommandHelpInfo</span></span>

<span data-ttu-id="8d8f5-298">Als u een opdracht krijgt met een Help-bestand, `Get-Help` wordt een **MamlCommandHelpInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-298">If you get a command that has a help file, `Get-Help` returns a **MamlCommandHelpInfo** object.</span></span>

## <span data-ttu-id="8d8f5-299">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8d8f5-299">NOTES</span></span>

<span data-ttu-id="8d8f5-300">Power Shell 3,0 bevat geen Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-300">PowerShell 3.0 doesn't include help files.</span></span> <span data-ttu-id="8d8f5-301">Als u de Help-bestanden wilt downloaden en installeren die `Get-Help` worden gelezen, gebruikt u de `Update-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-301">To download and install the help files that `Get-Help` reads, use the `Update-Help` cmdlet.</span></span> <span data-ttu-id="8d8f5-302">U kunt de `Update-Help` cmdlet gebruiken om Help-bestanden te downloaden en te installeren voor de kern opdrachten die worden geleverd met Power shell en voor alle modules die u installeert.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-302">You can use the `Update-Help` cmdlet to download and install help files for the core commands that come with PowerShell and for any modules that you install.</span></span> <span data-ttu-id="8d8f5-303">U kunt dit ook gebruiken om de Help-bestanden bij te werken, zodat de Help op uw computer nooit verouderd is.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-303">You can also use it to update the help files so that the help on your computer is never outdated.</span></span>

<span data-ttu-id="8d8f5-304">U kunt ook de Help-artikelen lezen over de opdrachten die worden geleverd met Power shell online, vanaf aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8d8f5-304">You can also read the help articles about the commands that come with PowerShell online starting at [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

<span data-ttu-id="8d8f5-305">`Get-Help` geeft Help weer in de land instellingen die zijn ingesteld voor het Windows-besturings systeem of in de terugval taal voor die land instelling.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-305">`Get-Help` displays help in the locale set for the Windows operating system or in the fallback language for that locale.</span></span> <span data-ttu-id="8d8f5-306">Als u geen Help-bestanden hebt voor de primaire of terugval land instelling, `Get-Help` gedraagt zich alsof er geen Help-bestanden op de computer zijn.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-306">If you don't have help files for the primary or fallback locale, `Get-Help` behaves as if there are no help files on the computer.</span></span> <span data-ttu-id="8d8f5-307">Als u hulp nodig hebt bij een andere land instelling, gebruikt u **regio** en **taal** in het configuratie scherm om de instellingen te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-307">To get help for a different locale, use **Region** and **Language** in Control Panel to change the settings.</span></span> <span data-ttu-id="8d8f5-308">In Windows 10, **instellingen** , **tijd & taal**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-308">On Windows 10, **Settings** , **Time & Language**.</span></span>

<span data-ttu-id="8d8f5-309">De volledige weer gave van Help bevat een tabel met informatie over de para meters.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-309">The full view of help includes a table of information about the parameters.</span></span> <span data-ttu-id="8d8f5-310">De tabel bevat de volgende velden:</span><span class="sxs-lookup"><span data-stu-id="8d8f5-310">The table includes the following fields:</span></span>

- <span data-ttu-id="8d8f5-311">**Vereist**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-311">**Required**.</span></span> <span data-ttu-id="8d8f5-312">Hiermee wordt aangegeven of de para meter vereist is (true) of optioneel (false).</span><span class="sxs-lookup"><span data-stu-id="8d8f5-312">Indicates whether the parameter is required (true) or optional (false).</span></span>

- <span data-ttu-id="8d8f5-313">**Positie**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-313">**Position**.</span></span> <span data-ttu-id="8d8f5-314">Hiermee wordt aangegeven of de para meter een naam of positioneel (numeriek) is.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-314">Indicates whether the parameter is named or positional (numeric).</span></span> <span data-ttu-id="8d8f5-315">Positionele para meters moeten worden weer gegeven in een opgegeven plaats in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-315">Positional parameters must appear in a specified place in the command.</span></span>

- <span data-ttu-id="8d8f5-316">Met de **naam** geeft aan dat de parameter naam vereist is, maar dat de para meter overal in de opdracht kan worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-316">**Named** indicates that the parameter name is required, but that the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="8d8f5-317">Een **numerieke** waarde geeft aan dat de parameter naam optioneel is, maar wanneer de naam wordt wegge laten, moet de para meter zich in de plaats bevinden die is opgegeven door het getal.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-317">**Numeric** indicates that the parameter name is optional, but when the name is omitted, the parameter must be in the place specified by the number.</span></span> <span data-ttu-id="8d8f5-318">`2`Geeft bijvoorbeeld aan dat wanneer de parameter naam wordt wegge laten, de para meter de tweede of enige niet-genaamde para meter in de opdracht moet zijn.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-318">For example, `2` indicates that when the parameter name is omitted, the parameter must be the second or only unnamed parameter in the command.</span></span> <span data-ttu-id="8d8f5-319">Wanneer de parameter naam wordt gebruikt, kan de para meter in een wille keurige plaats in de opdracht worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-319">When the parameter name is used, the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="8d8f5-320">**Standaard waarde**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-320">**Default value**.</span></span> <span data-ttu-id="8d8f5-321">De parameter waarde of het standaard gedrag dat door Power shell wordt gebruikt als u de para meter niet in de opdracht opneemt.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-321">The parameter value or default behavior that PowerShell uses if you don't include the parameter in the command.</span></span>

- <span data-ttu-id="8d8f5-322">Accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-322">Accepts pipeline input.</span></span> <span data-ttu-id="8d8f5-323">Hiermee wordt aangegeven of u (true) of niet (false) objecten naar de para meter kunt verzenden via een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-323">Indicates whether you can (true) or can't (false) send objects to the parameter through a pipeline.</span></span> <span data-ttu-id="8d8f5-324">**Op naam van eigenschap** betekent dat het pipeline-object een eigenschap moet hebben die dezelfde naam heeft als de parameter naam.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-324">**By Property Name** means that the pipelined object must have a property that has the same name as the parameter name.</span></span>

- <span data-ttu-id="8d8f5-325">**Accepteert joker tekens**.</span><span class="sxs-lookup"><span data-stu-id="8d8f5-325">**Accepts wildcard characters**.</span></span> <span data-ttu-id="8d8f5-326">Hiermee wordt aangegeven of de waarde van een para meter joker tekens kan bevatten, zoals een asterisk ( `*` ) of een vraag teken ( `?` ).</span><span class="sxs-lookup"><span data-stu-id="8d8f5-326">Indicates whether the value of a parameter can include wildcard characters, such as an asterisk (`*`) or question mark (`?`).</span></span>

## <span data-ttu-id="8d8f5-327">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8d8f5-327">RELATED LINKS</span></span>

[<span data-ttu-id="8d8f5-328">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="8d8f5-328">about_Command_Syntax</span></span>](About/about_Command_Syntax.md)

[<span data-ttu-id="8d8f5-329">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="8d8f5-329">about_Comment_Based_Help</span></span>](./About/about_Comment_Based_Help.md)

[<span data-ttu-id="8d8f5-330">Get-Command</span><span class="sxs-lookup"><span data-stu-id="8d8f5-330">Get-Command</span></span>](Get-Command.md)

[<span data-ttu-id="8d8f5-331">Ondersteunende help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="8d8f5-331">Supporting Updatable Help</span></span>](/powershell/scripting/developer/module/supporting-updatable-help)

[<span data-ttu-id="8d8f5-332">Update-Help</span><span class="sxs-lookup"><span data-stu-id="8d8f5-332">Update-Help</span></span>](Update-Help.md)

[<span data-ttu-id="8d8f5-333">Help-onderwerpen op basis van opmerkingen schrijven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-333">Writing Comment-Based Help Topics</span></span>](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[<span data-ttu-id="8d8f5-334">Help voor PowerShell-cmdlets schrijven</span><span class="sxs-lookup"><span data-stu-id="8d8f5-334">Writing Help for PowerShell Cmdlets</span></span>](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)

