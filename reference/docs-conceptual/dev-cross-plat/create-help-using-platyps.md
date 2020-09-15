---
title: Help maken op basis van XML met behulp van PlatyPS
description: Het gebruik van PlatyPS is de snelle en efficiënte manier om op XML gebaseerde Help te maken.
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972608"
---
# <a name="create-xml-based-help-using-platyps"></a><span data-ttu-id="4861d-103">Help maken op basis van XML met behulp van PlatyPS</span><span class="sxs-lookup"><span data-stu-id="4861d-103">Create XML-based help using PlatyPS</span></span>

<span data-ttu-id="4861d-104">Wanneer u een Power shell-module maakt, is het raadzaam om gedetailleerde hulp te bieden voor de cmdlets die u maakt.</span><span class="sxs-lookup"><span data-stu-id="4861d-104">When creating a PowerShell module, it is always recommended that you include detailed help for the cmdlets you create.</span></span> <span data-ttu-id="4861d-105">Als uw cmdlets in gecompileerde code worden geïmplementeerd, moet u de Help op XML gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4861d-105">If your cmdlets are implemented in compiled code, you must use the XML-based help.</span></span> <span data-ttu-id="4861d-106">Deze XML-indeling wordt ook wel bekend als micro soft Assistance Markup Language (MAML).</span><span class="sxs-lookup"><span data-stu-id="4861d-106">This XML format is known as the Microsoft Assistance Markup Language (MAML).</span></span>

<span data-ttu-id="4861d-107">De verouderde Power shell SDK-documentatie bevat informatie over het maken van Help voor Power shell-cmdlets, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="4861d-107">The legacy PowerShell SDK documentation covers the details of creating help for PowerShell cmdlets packaged into modules.</span></span> <span data-ttu-id="4861d-108">Power shell biedt echter geen hulp middelen voor het maken van XML-Help.</span><span class="sxs-lookup"><span data-stu-id="4861d-108">However, PowerShell does not provide any tools for creating the XML-based help.</span></span> <span data-ttu-id="4861d-109">In de SDK-documentatie wordt de structuur van de MAML-Help uitgelegd, maar u kunt de taak voor het maken van de complexe en diep geneste MAML-inhoud hand matig door bladeren.</span><span class="sxs-lookup"><span data-stu-id="4861d-109">The SDK documentation explains the structure of MAML help, but leaves you the task of creating the complex, and deeply nested, MAML content by hand.</span></span>

<span data-ttu-id="4861d-110">Hier kunt u de [PlatyPS][] -module helpen.</span><span class="sxs-lookup"><span data-stu-id="4861d-110">This is where the [PlatyPS][] module can help.</span></span>

## <a name="what-is-platyps"></a><span data-ttu-id="4861d-111">Wat is PlatyPS?</span><span class="sxs-lookup"><span data-stu-id="4861d-111">What is PlatyPS?</span></span>

<span data-ttu-id="4861d-112">PlatyPS is een [open source-][platyps-repo] hulp programma dat is gestart als een _hackathon_ -project om het maken en onderhouden van MAML eenvoudiger te maken.</span><span class="sxs-lookup"><span data-stu-id="4861d-112">PlatyPS is an [open-source][platyps-repo] tool that started as a _hackathon_ project to make the creation and maintenance of MAML easier.</span></span> <span data-ttu-id="4861d-113">PlatyPS documenten de syntaxis van parameter sets en de afzonderlijke para meters voor elke cmdlet in uw module.</span><span class="sxs-lookup"><span data-stu-id="4861d-113">PlatyPS documents the syntax of parameter sets and the individual parameters for each cmdlet in your module.</span></span> <span data-ttu-id="4861d-114">PlatyPS maakt gestructureerde bestanden met een [afkorting][] die de syntaxis informatie bevatten.</span><span class="sxs-lookup"><span data-stu-id="4861d-114">PlatyPS creates structured [Markdown][] files that contain the syntax information.</span></span> <span data-ttu-id="4861d-115">U kunt geen beschrijvingen maken of voor beelden opgeven.</span><span class="sxs-lookup"><span data-stu-id="4861d-115">It can't create descriptions or provide examples.</span></span>

<span data-ttu-id="4861d-116">PlatyPS maakt tijdelijke aanduidingen zodat u beschrijvingen en voor beelden kunt invullen.</span><span class="sxs-lookup"><span data-stu-id="4861d-116">PlatyPS creates placeholders for you to fill in descriptions and examples.</span></span> <span data-ttu-id="4861d-117">Nadat de vereiste informatie is toegevoegd, compileert PlatyPS de bestanden van de verlaging in MAML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="4861d-117">After adding the required information, PlatyPS compiles the Markdown files into MAML files.</span></span> <span data-ttu-id="4861d-118">In het Help-systeem van Power shell kunt u ook Help-bestanden met tekst zonder opmaak (informatie over onderwerpen).</span><span class="sxs-lookup"><span data-stu-id="4861d-118">PowerShell's help system also allows for plain-text conceptual help files (about topics).</span></span> <span data-ttu-id="4861d-119">PlatyPS heeft een cmdlet voor het maken van een gestructureerde prijsverlagings sjabloon voor een nieuw _info_ bestand, maar deze `about_*.help.txt` bestanden moeten hand matig worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="4861d-119">PlatyPS has a cmdlet to create a structured Markdown template for a new _about_ file, but these `about_*.help.txt` files must be maintained manually.</span></span>

<span data-ttu-id="4861d-120">U kunt de Help-bestanden voor MAML en tekst toevoegen aan uw module.</span><span class="sxs-lookup"><span data-stu-id="4861d-120">You can include the MAML and Text help files with your module.</span></span> <span data-ttu-id="4861d-121">U kunt PlatyPS ook gebruiken om de Help-bestanden te compileren in een CAB-pakket dat kan worden gehost op de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="4861d-121">You can also use PlatyPS to compile the help files into a CAB package that can be hosted for updateable help.</span></span>

## <a name="get-started-using-platyps"></a><span data-ttu-id="4861d-122">Aan de slag met PlatyPS</span><span class="sxs-lookup"><span data-stu-id="4861d-122">Get started using PlatyPS</span></span>

<span data-ttu-id="4861d-123">Eerst moet u PlatyPS installeren vanaf de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="4861d-123">First you must install PlatyPS from the PowerShell Gallery.</span></span>

```powershell
Install-Module platyps -Force
Import-Module platyps
```

<span data-ttu-id="4861d-124">Het volgende stroom diagram geeft een overzicht van het proces voor het maken of bijwerken van Power shell-referentie-inhoud.</span><span class="sxs-lookup"><span data-stu-id="4861d-124">The following flowchart outlines the process for creating or updating PowerShell reference content.</span></span>

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="De werk stroom voor het maken van XML-Help-informatie met behulp van PlatyPS":::

##  <a name="create-markdown-content-for-a-powershell-module"></a><span data-ttu-id="4861d-126">Inhoud voor afprijsing maken voor een Power shell-module</span><span class="sxs-lookup"><span data-stu-id="4861d-126">Create Markdown content for a PowerShell module</span></span>

1. <span data-ttu-id="4861d-127">Importeer uw nieuwe module in de sessie.</span><span class="sxs-lookup"><span data-stu-id="4861d-127">Import your new module into the session.</span></span> <span data-ttu-id="4861d-128">Herhaal deze stap voor elke module die u wilt documenteren.</span><span class="sxs-lookup"><span data-stu-id="4861d-128">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="4861d-129">Voer de volgende opdracht uit om de modules te importeren:</span><span class="sxs-lookup"><span data-stu-id="4861d-129">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="4861d-130">Gebruik PlatyPS om kortings bestanden te genereren voor uw module pagina en alle bijbehorende cmdlets in de module.</span><span class="sxs-lookup"><span data-stu-id="4861d-130">Use PlatyPS to generate Markdown files for your module page and all associated cmdlets within the module.</span></span> <span data-ttu-id="4861d-131">Herhaal deze stap voor elke module die u wilt documenteren.</span><span class="sxs-lookup"><span data-stu-id="4861d-131">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   <span data-ttu-id="4861d-132">Als de uitvoermap niet bestaat, `New-MarkdownHelp` maakt u deze.</span><span class="sxs-lookup"><span data-stu-id="4861d-132">If the output folder does not exist, `New-MarkdownHelp` creates it.</span></span> <span data-ttu-id="4861d-133">In dit voor beeld `New-MarkdownHelp` maakt u een bestand voor korting voor elke cmdlet in de module.</span><span class="sxs-lookup"><span data-stu-id="4861d-133">In this example, `New-MarkdownHelp` creates a Markdown file for each cmdlet in the module.</span></span> <span data-ttu-id="4861d-134">Ook wordt de _module pagina_ gemaakt in een bestand met de naam `<ModuleName>.md` .</span><span class="sxs-lookup"><span data-stu-id="4861d-134">It also creates the _module page_ in a file named `<ModuleName>.md`.</span></span> <span data-ttu-id="4861d-135">Deze module pagina bevat een lijst met de cmdlets in de module en de tijdelijke aanduidingen voor de beschrijving van de samen **vatting** .</span><span class="sxs-lookup"><span data-stu-id="4861d-135">This module page contains a list of the cmdlets contained in the module and placeholders for the **Synopsis** description.</span></span> <span data-ttu-id="4861d-136">De meta gegevens in de module pagina zijn afkomstig uit het module manifest en worden door PlatyPS gebruikt om het XML-bestand HelpInfo te maken (zoals [hieronder](#creating-an-updateable-help-package)wordt uitgelegd).</span><span class="sxs-lookup"><span data-stu-id="4861d-136">The metadata in the module page comes from the module manifest and is used by PlatyPS to create the HelpInfo XML file (as explained [below](#creating-an-updateable-help-package)).</span></span>

   <span data-ttu-id="4861d-137">`New-MarkdownAboutHelp` Hiermee maakt u _een nieuw bestand_ met de naam `about_topic_name.md` .</span><span class="sxs-lookup"><span data-stu-id="4861d-137">`New-MarkdownAboutHelp` creates a new _about_ file named `about_topic_name.md`.</span></span>

   <span data-ttu-id="4861d-138">Zie [New-MarkdownHelp][] en [New-MarkdownAboutHelp][]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4861d-138">For more information, see [New-MarkdownHelp][] and [New-MarkdownAboutHelp][].</span></span>

### <a name="update-existing-markdown-content-when-the-module-changes"></a><span data-ttu-id="4861d-139">Bestaande inhoud voor prijs verlaging bijwerken wanneer de module wordt gewijzigd</span><span class="sxs-lookup"><span data-stu-id="4861d-139">Update existing Markdown content when the module changes</span></span>

<span data-ttu-id="4861d-140">PlatyPS kan ook bestaande prijsverlagings bestanden voor een module bijwerken.</span><span class="sxs-lookup"><span data-stu-id="4861d-140">PlatyPS can also update existing Markdown files for a module.</span></span> <span data-ttu-id="4861d-141">Gebruik deze stap om bestaande modules bij te werken met nieuwe cmdlets, nieuwe para meters of para meters die zijn gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4861d-141">Use this step to update existing modules that have new cmdlets, new parameters, or parameters that have changed.</span></span>

1. <span data-ttu-id="4861d-142">Importeer uw nieuwe module in de sessie.</span><span class="sxs-lookup"><span data-stu-id="4861d-142">Import your new module into the session.</span></span> <span data-ttu-id="4861d-143">Herhaal deze stap voor elke module die u wilt documenteren.</span><span class="sxs-lookup"><span data-stu-id="4861d-143">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="4861d-144">Voer de volgende opdracht uit om de modules te importeren:</span><span class="sxs-lookup"><span data-stu-id="4861d-144">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="4861d-145">Gebruik PlatyPS om de prijsverlagings bestanden voor de module landings pagina en alle bijbehorende cmdlets in de module bij te werken.</span><span class="sxs-lookup"><span data-stu-id="4861d-145">Use PlatyPS to update Markdown files for your module landing page and all associated cmdlets within the module.</span></span> <span data-ttu-id="4861d-146">Herhaal deze stap voor elke module die u wilt documenteren.</span><span class="sxs-lookup"><span data-stu-id="4861d-146">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   <span data-ttu-id="4861d-147">`Update-MarkdownHelpModule` Hiermee worden de bestanden van de cmdlet en module bijgewerkt in de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="4861d-147">`Update-MarkdownHelpModule` updates the cmdlet and module Markdown files in the specified folder.</span></span>
   <span data-ttu-id="4861d-148">De bestanden worden niet bijgewerkt `about_*.md` .</span><span class="sxs-lookup"><span data-stu-id="4861d-148">It does not update the `about_*.md` files.</span></span> <span data-ttu-id="4861d-149">Het module bestand ( `ModuleName.md` ) ontvangt nieuwe samen **vattingen** die zijn toegevoegd aan de cmdlet-bestanden.</span><span class="sxs-lookup"><span data-stu-id="4861d-149">The module file (`ModuleName.md`) receives any new **Synopsis** text that has been added to the cmdlet files.</span></span> <span data-ttu-id="4861d-150">Updates voor cmdlet-bestanden bevatten de volgende wijziging:</span><span class="sxs-lookup"><span data-stu-id="4861d-150">Updates to cmdlet files include the following change:</span></span>

   - <span data-ttu-id="4861d-151">Nieuwe parameter sets</span><span class="sxs-lookup"><span data-stu-id="4861d-151">New parameter sets</span></span>
   - <span data-ttu-id="4861d-152">Nieuwe parameters</span><span class="sxs-lookup"><span data-stu-id="4861d-152">New parameters</span></span>
   - <span data-ttu-id="4861d-153">Meta gegevens van de para meter bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="4861d-153">Updated parameter metadata</span></span>
   - <span data-ttu-id="4861d-154">Informatie over invoer en uitvoer type bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="4861d-154">Updated input and output type information</span></span>

   <span data-ttu-id="4861d-155">Zie [Update-MarkdownHelpModule][]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4861d-155">For more information, see [Update-MarkdownHelpModule][].</span></span>

## <a name="edit-the-new-or-updated-markdown-files"></a><span data-ttu-id="4861d-156">De nieuwe of bijgewerkte verkortings bestanden bewerken</span><span class="sxs-lookup"><span data-stu-id="4861d-156">Edit the new or updated Markdown files</span></span>

<span data-ttu-id="4861d-157">PlatyPS documenten de syntaxis van de parameter sets en de afzonderlijke para meters.</span><span class="sxs-lookup"><span data-stu-id="4861d-157">PlatyPS documents the syntax of the parameter sets and the individual parameters.</span></span> <span data-ttu-id="4861d-158">U kunt geen beschrijvingen maken of voor beelden opgeven.</span><span class="sxs-lookup"><span data-stu-id="4861d-158">It can't create descriptions or provide examples.</span></span> <span data-ttu-id="4861d-159">De specifieke gebieden waar inhoud nodig is, zijn opgenomen in accolades.</span><span class="sxs-lookup"><span data-stu-id="4861d-159">The specific areas where content is needed are contained in curly braces.</span></span> <span data-ttu-id="4861d-160">Bijvoorbeeld: `{{ Fill in the Description }}`</span><span class="sxs-lookup"><span data-stu-id="4861d-160">For example: `{{ Fill in the Description }}`</span></span>

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="Sjabloon voor korting met de tijdelijke aanduidingen in VS code":::

<span data-ttu-id="4861d-162">U moet een samen vatting toevoegen, een beschrijving van de cmdlet, beschrijvingen voor elke para meter en ten minste één voor beeld.</span><span class="sxs-lookup"><span data-stu-id="4861d-162">You need to add a synopsis, a description of the cmdlet, descriptions for each parameter, and at least one example.</span></span>

<span data-ttu-id="4861d-163">Voor gedetailleerde informatie over het schrijven van Power shell-inhoud raadpleegt u de volgende artikelen:</span><span class="sxs-lookup"><span data-stu-id="4861d-163">For detailed information about writing PowerShell content, see the following articles:</span></span>

- [<span data-ttu-id="4861d-164">Power shell-stijl gids</span><span class="sxs-lookup"><span data-stu-id="4861d-164">PowerShell style guide</span></span>](/powershell/scripting/community/contributing/powershell-style-guide)
- [<span data-ttu-id="4861d-165">Verwijzings artikelen bewerken</span><span class="sxs-lookup"><span data-stu-id="4861d-165">Editing reference articles</span></span>](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> <span data-ttu-id="4861d-166">PlatyPS heeft een specifiek schema dat wordt gebruikt voor cmdlet-referentie.</span><span class="sxs-lookup"><span data-stu-id="4861d-166">PlatyPS has a specific schema that is uses for cmdlet reference.</span></span> <span data-ttu-id="4861d-167">Dit schema staat alleen bepaalde blokken met prijs verlagingen in specifieke secties van het document toe.</span><span class="sxs-lookup"><span data-stu-id="4861d-167">That schema only allows certain Markdown blocks in specific sections of the document.</span></span> <span data-ttu-id="4861d-168">Als u inhoud op de verkeerde locatie plaatst, mislukt de PlatyPS-build-stap.</span><span class="sxs-lookup"><span data-stu-id="4861d-168">If you put content in the wrong location, the PlatyPS build step fails.</span></span> <span data-ttu-id="4861d-169">Zie de [schema][] documentatie in de PlatyPS-opslag plaats voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4861d-169">For more information, see the [schema][] documentation in the PlatyPS repository.</span></span> <span data-ttu-id="4861d-170">Zie [Get-item][]voor een volledig voor beeld van een juist opgemaakte cmdlet-verwijzing.</span><span class="sxs-lookup"><span data-stu-id="4861d-170">For a complete example of well-formed cmdlet reference, see [Get-Item][].</span></span>

<span data-ttu-id="4861d-171">Nadat u de vereiste inhoud voor elk van de cmdlets hebt opgegeven, moet u ervoor zorgen dat u de landings pagina van de module bijwerkt.</span><span class="sxs-lookup"><span data-stu-id="4861d-171">After providing the required content for each of your cmdlets, you need to make sure that you update the module landing page.</span></span> <span data-ttu-id="4861d-172">Controleer of uw module de juiste `Module Guid` en `Download Help Link` waarden in de yaml-meta gegevens van het `<module-name>.md` bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="4861d-172">Verify your module has the correct `Module Guid` and `Download Help Link` values in the YAML metadata of the `<module-name>.md` file.</span></span> <span data-ttu-id="4861d-173">Voeg ontbrekende meta gegevens toe.</span><span class="sxs-lookup"><span data-stu-id="4861d-173">Add any missing metadata.</span></span>

<span data-ttu-id="4861d-174">Het is ook mogelijk dat er voor sommige cmdlets een samen **vatting** (_korte beschrijving_) ontbreekt.</span><span class="sxs-lookup"><span data-stu-id="4861d-174">Also, you may notice that some cmdlets may be missing a **Synopsis** (_short description_).</span></span> <span data-ttu-id="4861d-175">Met de volgende opdracht wordt de module landings pagina bijgewerkt met de beschrijvende tekst van de samen **vatting** .</span><span class="sxs-lookup"><span data-stu-id="4861d-175">The following command updates the module landing page with your **Synopsis** description text.</span></span> <span data-ttu-id="4861d-176">Open de pagina module overloop om de beschrijvingen te controleren.</span><span class="sxs-lookup"><span data-stu-id="4861d-176">Open the module landing page to verify the descriptions.</span></span>

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

<span data-ttu-id="4861d-177">Nu u alle inhoud hebt ingevoerd, kunt u de MAML-Help-bestanden maken die worden weer gegeven `Get-Help` in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="4861d-177">Now that you have entered all the content, you can create the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

## <a name="create-the-external-help-files"></a><span data-ttu-id="4861d-178">De externe Help-bestanden maken</span><span class="sxs-lookup"><span data-stu-id="4861d-178">Create the external help files</span></span>

<span data-ttu-id="4861d-179">Met deze stap maakt u de MAML Help-bestanden die worden weer gegeven `Get-Help` in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="4861d-179">This step creates the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

<span data-ttu-id="4861d-180">Voer de volgende opdracht uit om de MAML-bestanden te bouwen:</span><span class="sxs-lookup"><span data-stu-id="4861d-180">To build the MAML files, run the following command:</span></span>

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

<span data-ttu-id="4861d-181">`New-ExternalHelp` Hiermee converteert u alle bestanden van de cmdlet voor het afprijsen van een (of meer) MAML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="4861d-181">`New-ExternalHelp` converts all of the cmdlet Markdown files into one (or more) MAML files.</span></span> <span data-ttu-id="4861d-182">Over bestanden worden geconverteerd naar onbewerkte-tekst bestanden met de volgende naam indeling: `about_topic_name.help.txt` .</span><span class="sxs-lookup"><span data-stu-id="4861d-182">About files are converted to plain-text files with the following name format: `about_topic_name.help.txt`.</span></span>
<span data-ttu-id="4861d-183">De inhoud van de prijs opgave moet voldoen aan de vereiste van het PlatyPS-schema.</span><span class="sxs-lookup"><span data-stu-id="4861d-183">The Markdown content must meet the requirement of the PlatyPS schema.</span></span> <span data-ttu-id="4861d-184">`New-ExternalHelp` wordt afgesloten met fouten wanneer de inhoud niet voldoet aan het schema.</span><span class="sxs-lookup"><span data-stu-id="4861d-184">`New-ExternalHelp` will exits with errors when the content does not follow the schema.</span></span> <span data-ttu-id="4861d-185">U moet de bestanden bewerken om de schendingen van het schema op te lossen.</span><span class="sxs-lookup"><span data-stu-id="4861d-185">You must edit the files to fix the schema violations.</span></span>

> [!CAUTION]
> <span data-ttu-id="4861d-186">PlatyPS voert een slechte taak om de `about_*.md` bestanden om te zetten in tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="4861d-186">PlatyPS does a poor job converting the `about_*.md` files to plain text.</span></span> <span data-ttu-id="4861d-187">U moet een zeer eenvoudige prijs verlaging gebruiken om aanvaard bare resultaten te krijgen.</span><span class="sxs-lookup"><span data-stu-id="4861d-187">You must use very simple Markdown to get acceptable results.</span></span> <span data-ttu-id="4861d-188">Mogelijk wilt u de bestanden in de indeling tekst zonder opmaak behouden `about_topic_name.help.txt` , in plaats van PlatyPS toe te staan om ze te converteren.</span><span class="sxs-lookup"><span data-stu-id="4861d-188">You may want to maintain the files in plain-text `about_topic_name.help.txt` format, rather than allowing PlatyPS to convert them.</span></span>

<span data-ttu-id="4861d-189">Zodra deze stap is voltooid, ziet u `*-help.xml` `about_*.help.txt` de bestanden in de doelmap.</span><span class="sxs-lookup"><span data-stu-id="4861d-189">Once this step is complete, you will see `*-help.xml` and `about_*.help.txt` files in the target output folder.</span></span>

<span data-ttu-id="4861d-190">Zie [New-ExternalHelp][] voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4861d-190">For more information, see [New-ExternalHelp][]</span></span>

### <a name="test-the-compiled-help-files"></a><span data-ttu-id="4861d-191">De gecompileerde Help-bestanden testen</span><span class="sxs-lookup"><span data-stu-id="4861d-191">Test the compiled help files</span></span>

<span data-ttu-id="4861d-192">U kunt de inhoud controleren met de cmdlet [Get-HelpPreview][] :</span><span class="sxs-lookup"><span data-stu-id="4861d-192">You can verify the content with the [Get-HelpPreview][] cmdlet:</span></span>

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

<span data-ttu-id="4861d-193">De cmdlet leest het gecompileerde MAML-bestand en voert de inhoud uit met dezelfde indeling als waaruit u zou ontvangen `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="4861d-193">The cmdlet reads the compiled MAML file and outputs the content in the same format you would receive from `Get-Help`.</span></span> <span data-ttu-id="4861d-194">Hierdoor kunt u de resultaten controleren om te verifiëren of de verkortings bestanden correct zijn gecompileerd en de gewenste resultaten opleveren.</span><span class="sxs-lookup"><span data-stu-id="4861d-194">This allows you to inspect the results to verify that the Markdown files compiled correctly and produce the desired results.</span></span> <span data-ttu-id="4861d-195">Als er een fout optreedt, wijzigt u de bestanden voor de prijs verlaging opnieuw en compileert u de MAML opnieuw.</span><span class="sxs-lookup"><span data-stu-id="4861d-195">If you find an error, re-edit the Markdown files and recompile the MAML.</span></span>

<span data-ttu-id="4861d-196">U bent nu klaar om uw Help-bestanden te publiceren.</span><span class="sxs-lookup"><span data-stu-id="4861d-196">Now you are ready to publish your help files.</span></span>

## <a name="publishing-your-help"></a><span data-ttu-id="4861d-197">Uw Help publiceren</span><span class="sxs-lookup"><span data-stu-id="4861d-197">Publishing your help</span></span>

<span data-ttu-id="4861d-198">Nu u de bestanden voor de prijs verlaging hebt gecompileerd in Power shell Help-bestanden, kunt u de bestanden beschikbaar maken voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="4861d-198">Now that you have compiled the Markdown files into PowerShell help files, you are ready to make the files available to users.</span></span> <span data-ttu-id="4861d-199">Er zijn twee opties om hulp te bieden in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="4861d-199">There are two options for providing help in the PowerShell console.</span></span>

- <span data-ttu-id="4861d-200">De Help-bestanden inpakken met de module</span><span class="sxs-lookup"><span data-stu-id="4861d-200">Package the help files with the module</span></span>
- <span data-ttu-id="4861d-201">Een Help-pakket maken dat door gebruikers kan worden geïnstalleerd met de `Update-Help` cmdlet</span><span class="sxs-lookup"><span data-stu-id="4861d-201">Create an updateable help package that users install with the `Update-Help` cmdlet</span></span>

### <a name="packaging-help-with-the-module"></a><span data-ttu-id="4861d-202">Help bij de module inpakken</span><span class="sxs-lookup"><span data-stu-id="4861d-202">Packaging help with the module</span></span>

<span data-ttu-id="4861d-203">De Help-bestanden kunnen worden verpakt met uw module.</span><span class="sxs-lookup"><span data-stu-id="4861d-203">The help files can be packaged with your module.</span></span> <span data-ttu-id="4861d-204">Zie [hulp bij het schrijven van Help voor modules][] voor meer informatie over de mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="4861d-204">See [Writing Help for Modules][] for details of the folder structure.</span></span> <span data-ttu-id="4861d-205">U moet de lijst met Help-bestanden opnemen in de waarde van de sleutel **File List** in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="4861d-205">You should include the list of Help files in the value of the **FileList** key in the module manifest.</span></span>

### <a name="creating-an-updateable-help-package"></a><span data-ttu-id="4861d-206">Een Help-pakket maken dat kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="4861d-206">Creating an updateable help package</span></span>

<span data-ttu-id="4861d-207">Op hoog niveau zijn de stappen voor het maken van de updateable de volgende informatie:</span><span class="sxs-lookup"><span data-stu-id="4861d-207">At a high level, the steps to create updateable help include:</span></span>

1. <span data-ttu-id="4861d-208">Een Internet site zoeken om uw Help-bestanden te hosten</span><span class="sxs-lookup"><span data-stu-id="4861d-208">Find an internet site to host your help files</span></span>
1. <span data-ttu-id="4861d-209">Een **HelpInfoURI** -sleutel toevoegen aan het module manifest</span><span class="sxs-lookup"><span data-stu-id="4861d-209">Add a **HelpInfoURI** key to your module manifest</span></span>
1. <span data-ttu-id="4861d-210">Een HelpInfo XML-bestand maken</span><span class="sxs-lookup"><span data-stu-id="4861d-210">Create a HelpInfo XML file</span></span>
1. <span data-ttu-id="4861d-211">CAB-bestanden maken</span><span class="sxs-lookup"><span data-stu-id="4861d-211">Create CAB files</span></span>
1. <span data-ttu-id="4861d-212">Uw bestanden uploaden</span><span class="sxs-lookup"><span data-stu-id="4861d-212">Upload your files</span></span>

<span data-ttu-id="4861d-213">Zie voor meer informatie [ondersteunende Help-informatie: stapsgewijze instructies][step-by-step].</span><span class="sxs-lookup"><span data-stu-id="4861d-213">For more information, see [Supporting Updateable Help: Step-by-step][step-by-step].</span></span>

<span data-ttu-id="4861d-214">PlatyPS helpt u bij het uitvoeren van een aantal van deze stappen.</span><span class="sxs-lookup"><span data-stu-id="4861d-214">PlatyPS assists you with  some of these steps.</span></span>

<span data-ttu-id="4861d-215">De **HelpInfoURI** is een URL die verwijst naar de locatie waar uw Help-bestanden worden gehost op internet.</span><span class="sxs-lookup"><span data-stu-id="4861d-215">The **HelpInfoURI** is a URL that points to location where your help files are hosted on the internet.</span></span> <span data-ttu-id="4861d-216">Deze waarde wordt geconfigureerd in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="4861d-216">This value is configured in the module manifest.</span></span> <span data-ttu-id="4861d-217">`Update-Help` Hiermee wordt het module manifest gelezen om deze URL op te halen en de Help-inhoud te downloaden die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="4861d-217">`Update-Help` reads the module manifest to get this URL and download the updateable help content.</span></span> <span data-ttu-id="4861d-218">Deze URL mag alleen verwijzen naar de maplocatie en niet naar afzonderlijke bestanden.</span><span class="sxs-lookup"><span data-stu-id="4861d-218">This URL should only point to the folder location and not to individual files.</span></span> <span data-ttu-id="4861d-219">`Update-Help` maakt de bestands namen die moeten worden gedownload op basis van andere informatie uit het module manifest en het HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="4861d-219">`Update-Help` constructs the filenames to download based on other information from the module manifest and the HelpInfo XML file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4861d-220">De **HelpInfoURI** moet eindigen met een slash ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="4861d-220">The **HelpInfoURI** must end with a forward-slash character (`/`).</span></span> <span data-ttu-id="4861d-221">Zonder dat teken `Update-Help` kunt u niet de juiste bestands paden maken om de inhoud te downloaden.</span><span class="sxs-lookup"><span data-stu-id="4861d-221">Without that character, `Update-Help` cannot construct the correct file paths to download the content.</span></span> <span data-ttu-id="4861d-222">Daarnaast zijn de meeste op HTTP gebaseerde bestands Services hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="4861d-222">Also, most HTTP-based file services are case-sensitive.</span></span> <span data-ttu-id="4861d-223">Het is belang rijk dat de meta gegevens van de module in het XML-bestand van de HelpInfo de juiste letters bevatten.</span><span class="sxs-lookup"><span data-stu-id="4861d-223">It is important that the module metadata in the HelpInfo XML file contains the proper letter case.</span></span>

<span data-ttu-id="4861d-224">`New-ExternalHelp`Met de cmdlet maakt u het HelpInfo XML-bestand in de uitvoermap.</span><span class="sxs-lookup"><span data-stu-id="4861d-224">The `New-ExternalHelp` cmdlet creates the HelpInfo XML file in the output folder.</span></span> <span data-ttu-id="4861d-225">Het HelpInfo XML-bestand wordt gemaakt met behulp van YAML-meta gegevens die zijn opgenomen in de module reprijsing files ( `ModuleName.md` ).</span><span class="sxs-lookup"><span data-stu-id="4861d-225">The HelpInfo XML file is built using YAML metadata contained in the module Markdown files (`ModuleName.md`).</span></span>

<span data-ttu-id="4861d-226">De `New-ExternalHelpCab` cmdlet maakt zip-en cab-bestanden met de MAML en `about_*.help.txt` bestanden die u hebt opgesteld.</span><span class="sxs-lookup"><span data-stu-id="4861d-226">The `New-ExternalHelpCab` cmdlet creates ZIP and CAB files containing the MAML and `about_*.help.txt` files you compiled.</span></span> <span data-ttu-id="4861d-227">CAB-bestanden zijn compatibel met alle versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="4861d-227">CAB files are compatible with all versions of PowerShell.</span></span>
<span data-ttu-id="4861d-228">Power shell 6 en hoger kunnen ZIP-bestanden gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4861d-228">PowerShell 6 and higher can use ZIP files.</span></span>

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

<span data-ttu-id="4861d-229">Nadat u de ZIP-en CAB-bestanden hebt gemaakt, uploadt u de ZIP-, CAB-en HelpInfo-XML-bestanden naar de HTTP-Bestands server.</span><span class="sxs-lookup"><span data-stu-id="4861d-229">After creating the ZIP and CAB files, upload the ZIP, CAB, and HelpInfo XML files to your HTTP file server.</span></span> <span data-ttu-id="4861d-230">Plaats de bestanden op de locatie die wordt aangegeven door de **HelpInfoURI**.</span><span class="sxs-lookup"><span data-stu-id="4861d-230">Put the files in the location indicated by the **HelpInfoURI**.</span></span>

<span data-ttu-id="4861d-231">Zie [New-ExternalHelpCab][]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4861d-231">For more information, see [New-ExternalHelpCab][].</span></span>

### <a name="other-publishing-options"></a><span data-ttu-id="4861d-232">Andere publicatie opties</span><span class="sxs-lookup"><span data-stu-id="4861d-232">Other publishing options</span></span>

<span data-ttu-id="4861d-233">De prijs verlaging is een veelzijdige indeling die eenvoudig kan worden omgezet naar andere indelingen voor publicatie.</span><span class="sxs-lookup"><span data-stu-id="4861d-233">Markdown is a versatile format that is easy to transform to other formats for publishing.</span></span> <span data-ttu-id="4861d-234">Met een hulp programma, zoals [pandoc][], kunt u uw Help-bestanden voor prijs verlaging omzetten in veel verschillende document indelingen, waaronder tekst zonder opmaak, HTML, PDF en Office-document.</span><span class="sxs-lookup"><span data-stu-id="4861d-234">Using a tool like [Pandoc][], you can convert your Markdown help files to many different document formats, including plain text, HTML, PDF, and Office document formats.</span></span>

<span data-ttu-id="4861d-235">Daarnaast kunnen de cmdlets [ConvertFrom-][] prijs verlaging en [weer geven][] in Power shell 6 en hoger worden gebruikt om de prijs verlaging naar HTML te converteren of een kleur rijke weer gave in de Power shell-console te maken.</span><span class="sxs-lookup"><span data-stu-id="4861d-235">Also, the cmdlets [ConvertFrom-Markdown][] and [Show-Markdown][] in PowerShell 6 and higher can be used to convert Markdown to HTML or create a colorful display in the PowerShell console.</span></span>

## <a name="known-issues"></a><span data-ttu-id="4861d-236">Bekende problemen</span><span class="sxs-lookup"><span data-stu-id="4861d-236">Known issues</span></span>

<span data-ttu-id="4861d-237">PlatyPS is zeer gevoelig voor het [schema][] voor de structuur van de geprijsde bestanden die het maakt en compileert.</span><span class="sxs-lookup"><span data-stu-id="4861d-237">PlatyPS is very sensitive to the [schema][] for the structure of the Markdown files it creates and compiles.</span></span> <span data-ttu-id="4861d-238">Het is heel eenvoudig om een geldige prijs verlaging te schrijven die in strijd is met dit schema.</span><span class="sxs-lookup"><span data-stu-id="4861d-238">It is very easy write valid Markdown that violates this schema.</span></span> <span data-ttu-id="4861d-239">Raadpleeg de [Power shell-stijl gids][] en [Bewerk referentie artikelen][]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4861d-239">For more information, consult the [PowerShell style guide][] and [Editing reference articles][].</span></span>

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Get-item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[Get-Item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Update-MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[Power shell-stijl gids]: /powershell/scripting/community/contributing/powershell-style-guide
[PowerShell style guide]: /powershell/scripting/community/contributing/powershell-style-guide
[Verwijzings artikelen bewerken]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Editing reference articles]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Help-informatie over modules schrijven]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[Writing Help for Modules]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom-prijs verlaging]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[ConvertFrom-Markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Weer geven-prijs verlaging]: /powershell/module/microsoft.powershell.utility/show-markdown
[Show-Markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
