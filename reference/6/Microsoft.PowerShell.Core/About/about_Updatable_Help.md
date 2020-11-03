---
description: Beschrijft het Help-systeem dat kan worden bijgewerkt in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: 9f946fa1ef0f11efc3e0d964cf9ea8a55e01ff8f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252199"
---
# <a name="about-updatable-help"></a><span data-ttu-id="bb168-104">Informatie over bijwerk bare Help</span><span class="sxs-lookup"><span data-stu-id="bb168-104">About Updatable Help</span></span>

## <a name="short-description"></a><span data-ttu-id="bb168-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="bb168-105">Short description</span></span>
<span data-ttu-id="bb168-106">Beschrijft het Help-systeem dat kan worden bijgewerkt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="bb168-106">Describes the updatable help system in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="bb168-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="bb168-107">Long description</span></span>

<span data-ttu-id="bb168-108">Power shell biedt verschillende manieren om toegang te krijgen tot de meest recente Help-onderwerpen voor Power shell-cmdlets en-concepten.</span><span class="sxs-lookup"><span data-stu-id="bb168-108">PowerShell provides several different ways to access the most up-to-date help topics for PowerShell cmdlets and concepts.</span></span>

<span data-ttu-id="bb168-109">Het bij te werken Help-systeem, geïntroduceerd in Power Shell 3,0, is ontworpen om ervoor te zorgen dat u altijd over de nieuwste Help-onderwerpen op uw lokale computer beschikt zodat u ze op de opdracht regel kunt lezen.</span><span class="sxs-lookup"><span data-stu-id="bb168-109">The Updatable Help system, introduced in PowerShell 3.0, is designed to assure that you always have the newest help topics on your local computer so that you can read them at the command line.</span></span> <span data-ttu-id="bb168-110">Het is eenvoudig om Help-bestanden te downloaden en te installeren en ze bij te werken wanneer nieuwere Help-bestanden beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="bb168-110">It makes it easy to download and install help files and to update them whenever newer help files become available.</span></span>

<span data-ttu-id="bb168-111">Als u bijgewerkte hulp wilt bieden voor meerdere computers in een onderneming en voor computers die geen toegang tot internet hebben, kunt u met behulp van de Help-informatie Help-bestanden downloaden naar een bestandssysteem Directory of bestands share, en vervolgens de Help-bestanden installeren vanuit de bestands share.</span><span class="sxs-lookup"><span data-stu-id="bb168-111">To provide updated help for multiple computers in an enterprise and for computers that do not have access to the internet, Updatable Help lets you download help files to a filesystem directory or file share, and then install the help files from the file share.</span></span>

<span data-ttu-id="bb168-112">In Power Shell 4,0 wordt de eigenschap **HelpInfoUri** overgenomen van Windows Power shell Remoting, waarmee `Save-Help` u kunt werken met modules die zijn geïnstalleerd op een externe computer, maar niet per se geïnstalleerd zijn op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb168-112">In PowerShell 4.0, the **HelpInfoUri** property is preserved over Windows PowerShell remoting, which allows `Save-Help` to work for modules that are installed on a remote computer, but are not necessarily installed on the local computer.</span></span> <span data-ttu-id="bb168-113">U kunt een **PSModuleInfo** -object opslaan op schijf of verwissel bare media (zoals een USB-station) door uit te voeren `Export-Clixml` op een computer die geen toegang heeft tot internet, het **PSModuleInfo** -object te importeren op een computer die toegang heeft tot internet en vervolgens wordt uitgevoerd `Save-Help` op het **PSModuleInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="bb168-113">You can save a **PSModuleInfo** object to disk or removable media (such as a USB drive) by running `Export-Clixml` on a computer that does not have internet access, importing the **PSModuleInfo** object on a computer that does have internet access, and then running `Save-Help` on the **PSModuleInfo** object.</span></span> <span data-ttu-id="bb168-114">De opgeslagen Help kan worden gekopieerd naar de externe, niet-verbonden computer met behulp van Verwissel bare media en vervolgens worden geïnstalleerd door te worden uitgevoerd `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-114">The saved help can be copied to the remote, disconnected computer by using removable media, and then installed by running `Update-Help`.</span></span> <span data-ttu-id="bb168-115">Met deze verbeteringen in `Save-Help` functionaliteit kunt u Help installeren op computers die geen netwerk toegang zijn.</span><span class="sxs-lookup"><span data-stu-id="bb168-115">These improvements in `Save-Help` functionality let you install help on computers that are without any kind of network access.</span></span> <span data-ttu-id="bb168-116">Voor een voor beeld van het gebruik van de nieuwe `Save-Help` functionaliteit raadpleegt [u Help bijwerken vanuit een bestands share](#how-to-update-help-from-a-file-share) in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="bb168-116">For an example of how to use the new `Save-Help` functionality, see [How to update help from a file share](#how-to-update-help-from-a-file-share) in this topic.</span></span>

<span data-ttu-id="bb168-117">Bij te werken Help kan ook online toegang worden geboden tot de nieuwste Help-onderwerpen en de Basic-Help voor cmdlets, zelfs wanneer er geen Help-bestanden op de computer staan.</span><span class="sxs-lookup"><span data-stu-id="bb168-117">Updatable Help also supports online access to the newest help topics and basic help for cmdlets, even when there are no help files on the computer.</span></span>

<span data-ttu-id="bb168-118">Power Shell 3,0 wordt niet geleverd met Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="bb168-118">PowerShell 3.0 does not come with Help files.</span></span> <span data-ttu-id="bb168-119">U kunt de Help-functie die kan worden bijgewerkt gebruiken om de Help-bestanden te installeren voor alle opdrachten die standaard zijn opgenomen in Power shell en voor alle Windows-modules.</span><span class="sxs-lookup"><span data-stu-id="bb168-119">You can use the Updatable Help feature to install the help files for all of the commands that are included by default in PowerShell and for all Windows modules.</span></span>

## <a name="updatable-help-cmdlets"></a><span data-ttu-id="bb168-120">Help-cmdlets die kunnen worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="bb168-120">Updatable help cmdlets</span></span>

- <span data-ttu-id="bb168-121">`Update-Help`: Downloadt de nieuwste Help-bestanden van Internet of een bestands share en installeert ze op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb168-121">`Update-Help`: Downloads the newest help files from the internet or a file share, and installs them on the local computer.</span></span>

- <span data-ttu-id="bb168-122">`Save-Help`: Downloadt de nieuwste Help-bestanden van Internet en slaat ze op in een bestandssysteem Directory of bestands share.</span><span class="sxs-lookup"><span data-stu-id="bb168-122">`Save-Help`: Downloads the newest help files from the internet and saves them in a filesystem directory or file share.</span></span> <span data-ttu-id="bb168-123">Als u de Help-bestanden op computers wilt installeren, gebruikt u `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-123">To install the help files on computers, use `Update-Help`.</span></span>

- <span data-ttu-id="bb168-124">`Get-Help`: De Help-onderwerpen worden weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="bb168-124">`Get-Help`: Displays help topics at the command line.</span></span> <span data-ttu-id="bb168-125">Hiermee krijgt u hulp van de Help-bestanden op de computer.</span><span class="sxs-lookup"><span data-stu-id="bb168-125">Gets help from the help files on the computer.</span></span> <span data-ttu-id="bb168-126">Hiermee wordt automatisch gegenereerde Help weer gegeven voor cmdlets en functies die geen Help-bestanden hebben.</span><span class="sxs-lookup"><span data-stu-id="bb168-126">Displays auto-generated help for cmdlets and functions that do not have help files.</span></span> <span data-ttu-id="bb168-127">Hiermee opent u online Help-onderwerpen voor cmdlets, functies, scripts en werk stromen in uw standaard Internet browser.</span><span class="sxs-lookup"><span data-stu-id="bb168-127">Opens online help topics for cmdlets, functions, scripts, and workflows in your default internet browser.</span></span>

## <a name="auto-generated-help-help-without-help-files"></a><span data-ttu-id="bb168-128">Automatisch gegenereerde Help: Help zonder Help-bestanden</span><span class="sxs-lookup"><span data-stu-id="bb168-128">Auto-generated help: help without help files</span></span>

<span data-ttu-id="bb168-129">Als u niet beschikt over het Help-bestand voor een cmdlet, functie of werk stroom op de computer, `Get-Help` wordt door de cmdlet automatisch gegenereerde Help weer gegeven en wordt u gevraagd om de Help-bestanden te downloaden of ze online te lezen.</span><span class="sxs-lookup"><span data-stu-id="bb168-129">If you do not have the help file for a cmdlet, function, or workflow on the computer, the `Get-Help` cmdlet displays auto-generated help and prompts you to download the help files or read them online.</span></span>

<span data-ttu-id="bb168-130">Automatisch gegenereerde Help omvat syntaxis en aliassen, en opmerkingen met uitleg over het gebruik van de Help-cmdlets die kunnen worden bijgewerkt en voor toegang tot de online Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="bb168-130">Auto-generated help includes syntax and aliases, and remarks that explain how to use the Updatable Help cmdlets and to access the online help topics.</span></span>

<span data-ttu-id="bb168-131">De volgende opdracht wordt bijvoorbeeld Basic-Help voor de `Get-Culture` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb168-131">For example, the following command gets basic help for the `Get-Culture` cmdlet.</span></span> <span data-ttu-id="bb168-132">De uitvoer toont de `Get-Help` weer gave wanneer er geen Help-bestanden op de computer staan.</span><span class="sxs-lookup"><span data-stu-id="bb168-132">The output shows the `Get-Help` display when there are no help files on the computer.</span></span>

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a><span data-ttu-id="bb168-133">Help-bestanden voor modules</span><span class="sxs-lookup"><span data-stu-id="bb168-133">Help files for modules</span></span>

<span data-ttu-id="bb168-134">De kleinste eenheid van de Help die kan worden bijgewerkt is een hulp voor een module.</span><span class="sxs-lookup"><span data-stu-id="bb168-134">The smallest unit of Updatable Help is help for a module.</span></span> <span data-ttu-id="bb168-135">De Help van module bevat hulp voor alle cmdlets, functies, werk stromen, providers, scripts en concepten in een module.</span><span class="sxs-lookup"><span data-stu-id="bb168-135">Module help includes help for all of the cmdlets, functions, workflows, providers, scripts, and concepts in a module.</span></span> <span data-ttu-id="bb168-136">U kunt de Help bijwerken voor alle modules die op de computer zijn geïnstalleerd, zelfs als deze niet in de huidige sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="bb168-136">You can update help for all modules that are installed on the computer, even if they are not imported into the current session.</span></span>

<span data-ttu-id="bb168-137">U kunt de Help-informatie voor de hele module bijwerken, maar u kunt geen Help bijwerken voor afzonderlijke cmdlets.</span><span class="sxs-lookup"><span data-stu-id="bb168-137">You can update help for the entire module, but you cannot update help for individual cmdlets.</span></span>

<span data-ttu-id="bb168-138">Als u de module wilt vinden die een bepaalde cmdlet bevat, gebruikt u de volgende opdracht indeling:</span><span class="sxs-lookup"><span data-stu-id="bb168-138">To find the module that contains a particular cmdlet, use the following command format:</span></span>

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

<span data-ttu-id="bb168-139">Als u bijvoorbeeld de module wilt vinden die de `Set-ExecutionPolicy` cmdlet bevat, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb168-139">For example, to find the module that contains the `Set-ExecutionPolicy` cmdlet, type:</span></span>

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

<span data-ttu-id="bb168-140">Als u de Help voor een bepaalde module wilt bijwerken, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb168-140">To update help for a particular module, type:</span></span>

```powershell
Update-Help -Module <ModuleName>
```

<span data-ttu-id="bb168-141">Als u bijvoorbeeld Help wilt bijwerken voor de module met de cmdlet Set-ExecutionPolicy, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb168-141">For example, to update help for the module that contains the Set-ExecutionPolicy cmdlet, type:</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a><span data-ttu-id="bb168-142">Machtigingen voor Help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="bb168-142">Permissions for updatable help</span></span>

<span data-ttu-id="bb168-143">Als u de Help voor de modules in de map wilt bijwerken `$pshome/Modules` , moet u lid zijn van de groep Administrators op de computer.</span><span class="sxs-lookup"><span data-stu-id="bb168-143">To update help for the modules in the directory `$pshome/Modules`, you must be member of the Administrators group on the computer.</span></span>

<span data-ttu-id="bb168-144">Als u geen lid bent van de groep Administrators, kunt u de Help voor deze modules niet bijwerken. maar als u toegang hebt tot internet, kunt u Help online bekijken.</span><span class="sxs-lookup"><span data-stu-id="bb168-144">If you are not a member of the Administrators group, you cannot update help for these modules; but if you have internet access, you can view help online.</span></span>

<span data-ttu-id="bb168-145">Bij het bijwerken van de Help voor modules in de Directory `$home/Documents/PowerShell/Modules` of modules in andere submappen van de `$home` Directory zijn geen speciale machtigingen vereist.</span><span class="sxs-lookup"><span data-stu-id="bb168-145">Updating help for modules in the directory `$home/Documents/PowerShell/Modules` or modules in other subdirectories of the `$home` directory does not require special permissions.</span></span>

<span data-ttu-id="bb168-146">De `Update-Help` `Save-Help` cmdlets en hebben een **UseDefaultCredentials** -para meter waarmee de expliciete referenties van de huidige gebruiker worden verstrekt.</span><span class="sxs-lookup"><span data-stu-id="bb168-146">The `Update-Help` and `Save-Help` cmdlets have a **UseDefaultCredentials** parameter that provides the explicit credentials of the current user.</span></span> <span data-ttu-id="bb168-147">Deze para meter is ontworpen voor toegang tot beveiligde Internet locaties.</span><span class="sxs-lookup"><span data-stu-id="bb168-147">This parameter is designed for accessing secure internet locations.</span></span>

<span data-ttu-id="bb168-148">De `Update-Help` `Save-Help` cmdlets en hebben ook de para meter **Credential** waarmee u de opdracht kunt uitvoeren op een externe computer en toegang hebt tot een bestands share op een derde computer.</span><span class="sxs-lookup"><span data-stu-id="bb168-148">The `Update-Help` and `Save-Help` cmdlets also have a **Credential** parameter that allows you to run the command on a remote computer and access a file share on a third computer.</span></span> <span data-ttu-id="bb168-149">De para meter **Credential** is alleen geldig als u de para meter SourcePath of **LiteralPath** van `Update-Help` en de **doelpad** -of **LiteralPath** -para meters van gebruikt `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-149">The **Credential** parameter is valid only when you use the SourcePath or **LiteralPath** parameters of `Update-Help` and the **DestinationPath** or **LiteralPath** parameters of `Save-Help`.</span></span>

## <a name="how-to-install-and-update-help-files"></a><span data-ttu-id="bb168-150">Help-bestanden installeren en bijwerken</span><span class="sxs-lookup"><span data-stu-id="bb168-150">How to install and update help files</span></span>

<span data-ttu-id="bb168-151">Gebruik de cmdlet om Help-bestanden voor de eerste keer te downloaden en te installeren, of om de Help-bestanden op uw computer bij te werken `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-151">To download and install help files for the first time, or to update the help files on your computer, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="bb168-152">`Update-Help`Met de cmdlet worden alle vaste werk voor u uitgevoerd, met inbegrip van de volgende taken.</span><span class="sxs-lookup"><span data-stu-id="bb168-152">The `Update-Help` cmdlet does all of the hard work for you, including the following tasks.</span></span>

- <span data-ttu-id="bb168-153">Hiermee wordt bepaald welke modules kunnen worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="bb168-153">Determines which modules support Updatable Help.</span></span>
- <span data-ttu-id="bb168-154">Hiermee wordt gezocht naar de Internet locatie waar elke module de bij te werken Help-bestanden opslaat.</span><span class="sxs-lookup"><span data-stu-id="bb168-154">Finds the internet location where each module stores its Updatable Help files.</span></span>
- <span data-ttu-id="bb168-155">Vergelijkt de Help-bestanden voor elke module op uw computer met de nieuwste Help-bestanden die voor elke module beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="bb168-155">Compares the help files for each module on your computer to the newest help files that are available for each module.</span></span>
- <span data-ttu-id="bb168-156">Downloadt de nieuwe bestanden van het internet.</span><span class="sxs-lookup"><span data-stu-id="bb168-156">Downloads the new files from the internet.</span></span>
- <span data-ttu-id="bb168-157">In wordt het pakket met de Help-bestanden uitgepakt.</span><span class="sxs-lookup"><span data-stu-id="bb168-157">Unwraps the help file package.</span></span>
- <span data-ttu-id="bb168-158">Verifieert of de bestanden geldige Help-bestanden zijn.</span><span class="sxs-lookup"><span data-stu-id="bb168-158">Verifies that the files are valid help files.</span></span>
- <span data-ttu-id="bb168-159">Installeert de Help-bestanden in de taalspecifieke submap van de module directory.</span><span class="sxs-lookup"><span data-stu-id="bb168-159">Installs the help files in the language-specific subdirectory of the module directory.</span></span>

<span data-ttu-id="bb168-160">Gebruik de cmdlet om toegang te krijgen tot de nieuwe Help-onderwerpen `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-160">To access the new help topics, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="bb168-161">U hoeft Power shell niet opnieuw op te starten.</span><span class="sxs-lookup"><span data-stu-id="bb168-161">You do not need to restart PowerShell.</span></span>

<span data-ttu-id="bb168-162">Als u de Help wilt installeren of bijwerken voor alle modules op de computer die de Help-informatie die kan worden bijgewerkt ondersteunt, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb168-162">To install or update help for all modules on the computer that supports Updatable Help, type:</span></span>

```powershell
Update-Help
```

<span data-ttu-id="bb168-163">Als u de Help voor bepaalde modules wilt bijwerken, voegt u de **module** parameter van toe `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-163">To update help for particular modules, add the **Module** parameter of `Update-Help`.</span></span> <span data-ttu-id="bb168-164">Joker tekens zijn toegestaan in de module naam.</span><span class="sxs-lookup"><span data-stu-id="bb168-164">Wildcard characters are permitted in the module name.</span></span>

<span data-ttu-id="bb168-165">Als u bijvoorbeeld de Help voor de module Server Manager wilt bijwerken, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb168-165">For example, to update help for the ServerManager module, type:</span></span>

```powershell
Update-Help -Module ServerManager
```

<span data-ttu-id="bb168-166">Zonder para meters `Update-Help` helpt updates voor alle modules in de sessie en voor alle geïnstalleerde modules die kunnen worden bijgewerkt met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="bb168-166">Without parameters, `Update-Help` updates help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="bb168-167">Om te worden opgenomen, moeten modules worden geïnstalleerd in mappen die worden vermeld in de waarde van de omgevings variabele PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="bb168-167">To be included, modules must be installed in directories that are listed in the value of the PSModulePath environment variable.</span></span> <span data-ttu-id="bb168-168">Dit zijn ook modules die worden geretourneerd door de opdracht Get-Help-ListAvailable.</span><span class="sxs-lookup"><span data-stu-id="bb168-168">These are also modules that are returned by a "Get-Help -ListAvailable" command.</span></span>

<span data-ttu-id="bb168-169">Als de waarde van de **module** parameter is `*` (alle), wordt `Update-Help` geprobeerd om de Help bij te werken voor alle geïnstalleerde modules, inclusief modules die geen ondersteuning bieden voor bijwerk bare Help.</span><span class="sxs-lookup"><span data-stu-id="bb168-169">If the value of the **Module** parameter is `*` (all), `Update-Help` attempts to update help for all installed modules, including modules that do not support Updatable Help.</span></span> <span data-ttu-id="bb168-170">Met deze opdracht worden doorgaans veel fouten gegenereerd, omdat de cmdlet modules detecteert die geen ondersteuning bieden voor Help.</span><span class="sxs-lookup"><span data-stu-id="bb168-170">This command typically generates many errors as the cmdlet encounters modules that do not support Updatable Help.</span></span>

## <a name="how-to-update-help-from-a-file-share"></a><span data-ttu-id="bb168-171">Help van een bestands share bijwerken</span><span class="sxs-lookup"><span data-stu-id="bb168-171">How to update help from a file share</span></span>

<span data-ttu-id="bb168-172">Gebruik de cmdlet om computers te ondersteunen die niet zijn verbonden met internet, of om het bijwerken van de Help in een onderneming te beheren of te stroom lijnen `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-172">To support computers that are not connected to the internet, or to control or streamline help updating in an enterprise, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="bb168-173">De `Save-Help` cmdlet downloadt Help-bestanden van Internet en slaat ze op in een bestandssysteem Directory die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="bb168-173">The `Save-Help` cmdlet downloads help files from the internet and saves them in a filesystem directory that you specify.</span></span>

<span data-ttu-id="bb168-174">`Save-Help` de Help-bestanden in de opgegeven map worden vergeleken met de nieuwste Help-bestanden die beschikbaar zijn voor elke module.</span><span class="sxs-lookup"><span data-stu-id="bb168-174">`Save-Help` compares the help files in the specified directory to the newest help files that are available for each module.</span></span> <span data-ttu-id="bb168-175">Als de Directory geen Help-bestanden of nieuwere Help-bestanden voor de module beschikbaar heeft, `Save-Help` downloadt de cmdlet de nieuwe bestanden van het internet.</span><span class="sxs-lookup"><span data-stu-id="bb168-175">If the directory has no help files or newer help files are available for the module, the `Save-Help` cmdlet downloads the new files from the internet.</span></span> <span data-ttu-id="bb168-176">De Help-bestanden worden echter niet uitgepakt of geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="bb168-176">However, it does not unwrap or install the help files.</span></span>

<span data-ttu-id="bb168-177">Als u de Help-bestanden op een computer wilt installeren of bijwerken vanuit Help-bestanden die zijn opgeslagen in een bestandssysteem Directory, gebruikt u de para meter **SourcePath** van de `Update-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb168-177">To install or update the help files on a computer from help files that were saved to a filesystem directory, use the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="bb168-178">Met de `Update-Help` cmdlet worden de nieuwste Help-bestanden geïdentificeerd, worden deze teruggestuurd en gevalideerd en worden deze in de taalspecifieke submappen van de module mappen geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="bb168-178">The `Update-Help` cmdlet identifies the newest help files, unwraps and validates them, and installs them in the language-specific subdirectories of the module directories.</span></span>

<span data-ttu-id="bb168-179">Als u bijvoorbeeld Help wilt opslaan voor alle geïnstalleerde modules in de `\\Server\Share` map, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb168-179">For example, to save help for all installed modules to the `\\Server\Share` directory, type:</span></span>

```powershell
Save-Help -DestinationPath \\Server\Share
```

<span data-ttu-id="bb168-180">Als u de Help vanuit de map wilt bijwerken `\\Server\Share` , typt u:</span><span class="sxs-lookup"><span data-stu-id="bb168-180">Then, to update help from the `\\Server\Share` directory, type:</span></span>

```powershell
Update-Help -SourcePath \\Server\Share
```

<span data-ttu-id="bb168-181">In de volgende voor beelden ziet u het gebruik van `Save-Help` om Help op te slaan voor modules die niet op de lokale computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="bb168-181">The following examples show the use of `Save-Help` to save help for modules that are not installed on the local computer.</span></span> <span data-ttu-id="bb168-182">In dit voor beeld wordt de-beheerder uitgevoerd `Save-Help` om de Help voor de DHCP-module op te slaan vanaf een client computer met Internet verbinding, zonder dat u de DHCP-module DHCP-server of de-serverrol op de lokale computer hoeft te installeren.</span><span class="sxs-lookup"><span data-stu-id="bb168-182">In this example, the administrator runs `Save-Help` to save the help for the DhcpServer module from an internet-connected client computer, without installing the DhcpServer module or DHCP Server role on the local computer.</span></span>

<span data-ttu-id="bb168-183">Optie 1: Voer uit `Invoke-Command` om het **PSModuleInfo** -object voor de externe module op te halen, op te slaan in een variabele, `$m` en voer vervolgens uit `Save-Help` op het **PSModuleInfo** -object door de variabele op te geven `$m` als de module naam.</span><span class="sxs-lookup"><span data-stu-id="bb168-183">Option 1: Run `Invoke-Command` to get the **PSModuleInfo** object for the remote module, save it in a variable, `$m`, and then run `Save-Help` on the **PSModuleInfo** object by specifying the variable `$m` as the module name.</span></span>

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="bb168-184">Optie 2: Open een PSSession die is gericht op de computer waarop de DHCP-server module wordt uitgevoerd, om het **PSModuleInfo** -object voor de module op te halen, op te slaan in een variabele `$m` en vervolgens uit te voeren `Save-Help` op het object dat is opgeslagen in de `$m` variabele.</span><span class="sxs-lookup"><span data-stu-id="bb168-184">Option 2: Open a PSSession targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="bb168-185">Optie 3: Open een CIM-sessie, gericht op de computer waarop de DHCP-server module wordt uitgevoerd, om het **PSModuleInfo** -object voor de module op te halen, op te slaan in een variabele `$m` en vervolgens uit te voeren `Save-Help` op het object dat is opgeslagen in de `$m` variabele.</span><span class="sxs-lookup"><span data-stu-id="bb168-185">Option 3: Open a CIM session, targeted at the computer that is running the DHCP Server module, to get the **PSModuleInfo** object for the module, save it in a variable `$m`, and then run `Save-Help` on the object that is saved in the `$m` variable.</span></span>

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

<span data-ttu-id="bb168-186">In het volgende voor beeld installeert de beheerder Help voor de module DHCP-server op een computer die geen netwerk toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="bb168-186">In the following example, the administrator installs help for the DHCP Server module on a computer that does not have network access.</span></span>

<span data-ttu-id="bb168-187">Voer eerst uit `Export-Clixml` om het **PSModuleInfo** -object te exporteren naar een gedeelde map of naar een verwisselbaar medium.</span><span class="sxs-lookup"><span data-stu-id="bb168-187">First, run `Export-Clixml` to export the **PSModuleInfo** object to a shared folder or to removable media.</span></span>

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

<span data-ttu-id="bb168-188">Transport vervolgens de Verwissel bare media naar een computer met Internet toegang en importeer vervolgens het **PSModuleInfo** -object met `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="bb168-188">Next, transport the removable media to a computer that has internet access, and then import the **PSModuleInfo** object with `Import-Clixml`.</span></span> <span data-ttu-id="bb168-189">Voer uit `Save-Help` om de Help voor het geïmporteerde DHCP-module **PSModuleInfo** -object op te slaan.</span><span class="sxs-lookup"><span data-stu-id="bb168-189">Run `Save-Help` to save the Help for the imported DhcpServer module **PSModuleInfo** object.</span></span>

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="bb168-190">Transport vervolgens de Verwissel bare media Terug naar de computer die geen netwerk toegang heeft en installeer vervolgens de Help door uit te voeren `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-190">Finally, transport the removable media back to the computer that does not have network access, and then install the help by running `Update-Help`.</span></span>

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

<span data-ttu-id="bb168-191">Zonder para meters, `Save-Help` down loads Help voor alle modules in de sessie en voor alle geïnstalleerde modules die kunnen worden bijgewerkt met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="bb168-191">Without parameters, `Save-Help` downloads help for all modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="bb168-192">Om te worden opgenomen, moeten modules worden geïnstalleerd in mappen die worden vermeld in de waarde van de `$env:PSModulePath` omgevings variabele, op de lokale computer of op een externe computer waarvoor u de Help wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="bb168-192">To be included, modules must be installed in directories that are listed in the value of the `$env:PSModulePath` environment variable, on either the local computer or on a remote computer for which you want to save help.</span></span> <span data-ttu-id="bb168-193">Dit zijn ook modules die worden geretourneerd door een opdracht uit te voeren `Get-Help -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="bb168-193">These are also modules that are returned by running a `Get-Help -ListAvailable` command.</span></span>

## <a name="how-to-update-help-files-in-different-languages"></a><span data-ttu-id="bb168-194">Help-bestanden in verschillende talen bijwerken</span><span class="sxs-lookup"><span data-stu-id="bb168-194">How to update help files in different languages</span></span>

<span data-ttu-id="bb168-195">Standaard `Update-Help` `Save-Help` downloaden de cmdlets en Help-informatie in de UI-cultuur en taal die is ingesteld voor Windows op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bb168-195">By default, the `Update-Help` and `Save-Help` cmdlets download help in the UI culture and language that is set for Windows on the local computer.</span></span> <span data-ttu-id="bb168-196">Als de Help-bestanden voor de opgegeven modules niet beschikbaar zijn in de lokale GEBRUIKERSINTERFACE cultuur `Update-Help` en `Save-Help` de Windows-taal terugval regels gebruiken om de best ondersteunde taal te vinden.</span><span class="sxs-lookup"><span data-stu-id="bb168-196">If help files for the specified modules are not available in the local UI culture, `Update-Help` and `Save-Help` use the Windows language fallback rules to find the best supported language.</span></span>

<span data-ttu-id="bb168-197">U kunt echter de **uiCulture** -para meters van de- `Update-Help` en- `Save-Help` cmdlets gebruiken om Help-bestanden te downloaden en te installeren in alle gebruikersinterface culturen waarin deze beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="bb168-197">However, you can use the **UICulture** parameters of the `Update-Help` and `Save-Help` cmdlets to download and install help files in any UI cultures in which they are available.</span></span>

<span data-ttu-id="bb168-198">Als u bijvoorbeeld de nieuwste Help-bestanden voor alle modules in de sessie in het Japans (ja-JP) en Frans (fr-FR) wilt opslaan, typt u:</span><span class="sxs-lookup"><span data-stu-id="bb168-198">For example, to save the newest help files for all modules on the session in Japanese (Ja-jp) and French (fr-FR), type:</span></span>

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

<span data-ttu-id="bb168-199">Als Help-bestanden voor de modules niet beschikbaar zijn in de talen die u hebt opgegeven, `Update-Help` retour neren de-en- `Save-Help` cmdlets een fout bericht met een lijst met de talen waarin de Help voor elke module beschikbaar is, zodat u het alternatief kunt kiezen dat het beste aan uw behoeften voldoet.</span><span class="sxs-lookup"><span data-stu-id="bb168-199">If help files for the modules are not available in the languages that you specified, the `Update-Help` and `Save-Help` cmdlets return an error message that lists the languages in which help for each module is available so you can choose the alternative that best meets your needs.</span></span>

> [!NOTE]
> <span data-ttu-id="bb168-200">Op dit moment wordt Help-inhoud die kan worden bijgewerkt, alleen in het Engels gepubliceerd (en-US).</span><span class="sxs-lookup"><span data-stu-id="bb168-200">Currently, Updateable Help content is only published in English (en-US).</span></span> <span data-ttu-id="bb168-201">Op sommige niet-Windows-systemen moet u de para meter **uiCulture** gebruiken om de inhoud expliciet aan te vragen `en-US` .</span><span class="sxs-lookup"><span data-stu-id="bb168-201">On some non-Windows systems you must use the **UICulture** parameter to explicitly request the `en-US` content.</span></span>

## <a name="how-to-use-online-help"></a><span data-ttu-id="bb168-202">Online-Help gebruiken</span><span class="sxs-lookup"><span data-stu-id="bb168-202">How to use online help</span></span>

<span data-ttu-id="bb168-203">Als u de Help-bestanden op uw lokale computer niet kunt of niet wilt bijwerken, kunt u nog steeds de nieuwste Help-bestanden online ophalen.</span><span class="sxs-lookup"><span data-stu-id="bb168-203">If you cannot or choose not to update the help files on your local computer, you can still get the newest help files online.</span></span>

<span data-ttu-id="bb168-204">Als u het online-Help-onderwerp voor een cmdlet of functie wilt openen, gebruikt u de para meter **online** van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb168-204">To open the online help topic for any cmdlet or function, use the **Online** parameter of the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="bb168-205">Met de volgende opdracht wordt bijvoorbeeld het online-Help-onderwerp voor de `Get-Job` cmdlet in de standaard browser van Internet geopend:</span><span class="sxs-lookup"><span data-stu-id="bb168-205">For example, the following command opens the online help topic for the `Get-Job` cmdlet in your default internet browser:</span></span>

```powershell
Get-Help Get-Job -Online
```

<span data-ttu-id="bb168-206">Als u online-Help voor een script wilt krijgen, gebruikt u de para meter **online** en het volledige pad naar het script.</span><span class="sxs-lookup"><span data-stu-id="bb168-206">To get online help for a script, use the **Online** parameter and the full path to the script.</span></span>

<span data-ttu-id="bb168-207">De para meter **online** werkt niet met informatie over onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="bb168-207">The **Online** parameter does not work with About topics.</span></span> <span data-ttu-id="bb168-208">Zie [Power shell about topics](about.md)(Engelstalig) voor een overzicht van de onderwerpen over Power shell, inclusief Help-onderwerpen over de Power shell-taal.</span><span class="sxs-lookup"><span data-stu-id="bb168-208">To see the about topics for PowerShell, including help topics about the PowerShell language, see [PowerShell About Topics](about.md).</span></span>

## <a name="how-to-minimize-or-prevent-internet-downloads"></a><span data-ttu-id="bb168-209">Internet downloads minimaliseren of voor komen</span><span class="sxs-lookup"><span data-stu-id="bb168-209">How to minimize or prevent internet downloads</span></span>

<span data-ttu-id="bb168-210">Gebruik de-cmdlet om Internet downloads te minimaliseren en Help-informatie te bieden voor gebruikers die niet zijn verbonden met internet `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-210">To minimize internet downloads and provide Updatable Help to users who are not connected to the internet, use the `Save-Help` cmdlet.</span></span> <span data-ttu-id="bb168-211">Down load de Help van Internet en sla deze op een netwerk share op.</span><span class="sxs-lookup"><span data-stu-id="bb168-211">Download help from the internet and save it to a network share.</span></span> <span data-ttu-id="bb168-212">Maak vervolgens een groepsbeleid-instelling of een geplande taak die een `Update-Help` opdracht op alle computers uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bb168-212">Then, create a Group Policy setting or scheduled job that runs an `Update-Help` command on all computers.</span></span> <span data-ttu-id="bb168-213">Stel de waarde van de para meter **SourcePath** van de `Update-Help` cmdlet in op de netwerk share.</span><span class="sxs-lookup"><span data-stu-id="bb168-213">Set the value of the **SourcePath** parameter of the `Update-Help` cmdlet to the network share.</span></span>

<span data-ttu-id="bb168-214">Als u wilt voor komen dat gebruikers met Internet toegang via internet kunnen worden gedownload, gebruikt u de instelling **het standaard bronpad instellen voor update-Help** Groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="bb168-214">To prevent users who have internet access from downloading Updatable Help from the internet, use the **Set the default source path for Update-Help** Group Policy setting.</span></span>

<span data-ttu-id="bb168-215">Met deze groepsbeleid instelling wordt impliciet de para meter **SourcePath** toegevoegd, met de locatie van het bestands systeem dat u opgeeft, voor elke `Update-Help` opdracht op elke betrokken computer.</span><span class="sxs-lookup"><span data-stu-id="bb168-215">This Group Policy setting implicitly adds the **SourcePath** parameter, with the filesystem location that you specify, to every `Update-Help` command on every affected computer.</span></span> <span data-ttu-id="bb168-216">Gebruikers kunnen de para meter **SourcePath** expliciet gebruiken om een andere bestandssysteem locatie op te geven, maar ze kunnen de para meter **SourcePath** niet uitsluiten en de Help van Internet niet downloaden.</span><span class="sxs-lookup"><span data-stu-id="bb168-216">Users can use the **SourcePath** parameter explicitly to specify a different filesystem location, but they cannot exclude the **SourcePath** parameter and download help from the internet.</span></span>

> [!NOTE]
> <span data-ttu-id="bb168-217">De instelling **het standaard bronpad instellen voor bijwerken-Help** groeps beleid wordt weer gegeven onder **computer configuratie** en **gebruikers configuratie**.</span><span class="sxs-lookup"><span data-stu-id="bb168-217">The **Set the default source path for Update-Help** group policy setting appears under **Computer Configuration** and **User Configuration**.</span></span> <span data-ttu-id="bb168-218">De beleids instelling onder **computer configuratie** is echter alleen effectief.</span><span class="sxs-lookup"><span data-stu-id="bb168-218">However, only the policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="bb168-219">De beleids instelling onder **gebruikers configuratie** wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="bb168-219">The policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="bb168-220">Zie [about_Group_Policy_Settings](about_Group_Policy_Settings.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bb168-220">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="how-to-update-help-for-non-standard-modules"></a><span data-ttu-id="bb168-221">Help voor niet-standaard modules bijwerken</span><span class="sxs-lookup"><span data-stu-id="bb168-221">How to update help for non-standard modules</span></span>

<span data-ttu-id="bb168-222">Als u Help wilt bijwerken of opslaan voor een module die niet wordt geretourneerd door de para meter **ListAvailable** van de `Get-Module` cmdlet, importeert u de module in de huidige sessie voordat u een `Update-Help` of-opdracht uitvoert `Save-Help` .</span><span class="sxs-lookup"><span data-stu-id="bb168-222">To update or save help for a module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, import the module into the current session before running an `Update-Help` or `Save-Help` command.</span></span> <span data-ttu-id="bb168-223">Importeer op een externe computer voordat u de `Save-Help` opdracht uitvoert de module in de huidige sessie, of het `Invoke-Command` script blok, dat is verbonden met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="bb168-223">On a remote computer, before running the `Save-Help` command, import the module into the current Session, or `Invoke-Command` script block, that is connected to the remote computer.</span></span>

<span data-ttu-id="bb168-224">Wanneer de module zich in de huidige sessie bevindt, voert `Update-Help` `Save-Help` u de cmdlets en zonder para meters uit of gebruikt u de **module** parameter om de module naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="bb168-224">When the module is in the current session, run the `Update-Help` or `Save-Help` cmdlets without parameters, or use the **Module** parameter to specify the module name.</span></span>

<span data-ttu-id="bb168-225">De **module** parameters van de `Update-Help` `Save-Help` cmdlets en accepteren alleen een module naam.</span><span class="sxs-lookup"><span data-stu-id="bb168-225">The **Module** parameters of the `Update-Help` and `Save-Help` cmdlets accept only a module name.</span></span> <span data-ttu-id="bb168-226">Het pad naar een module bestand wordt niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="bb168-226">They do not accept the path to a module file.</span></span>

<span data-ttu-id="bb168-227">Gebruik deze techniek om hulp bij te werken of bij te houden voor een module die niet wordt geretourneerd door de para meter **ListAvailable** van de `Get-Module` cmdlet, zoals een module die is geïnstalleerd op een locatie die niet wordt vermeld in de `$env:PSModulePath` omgevings variabele, of een module die niet juist is opgemaakt (de module directory bevat niet ten minste één bestand waarvan base naam gelijk is aan de mapnaam).</span><span class="sxs-lookup"><span data-stu-id="bb168-227">Use this technique to update or save help for any module that is not returned by the **ListAvailable** parameter of the `Get-Module` cmdlet, such as a module that is installed in a location that is not listed in the `$env:PSModulePath` environment variable, or a module that is not well-formed (the module directory does not contain at least one file whose basename is the same as the directory name).</span></span>

## <a name="how-to-support-updatable-help"></a><span data-ttu-id="bb168-228">Ondersteunende Help ondersteunen</span><span class="sxs-lookup"><span data-stu-id="bb168-228">How to support updatable help</span></span>

<span data-ttu-id="bb168-229">Als u een module ontwerpt, kunt u online-Help en Help-informatie voor uw modules ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="bb168-229">If you author a module, you can support online help and Updatable Help for your modules.</span></span> <span data-ttu-id="bb168-230">Zie [ondersteunende Help](/powershell/scripting/developer/help/supporting-updatable-help) en [ondersteunende online help](/powershell/scripting/developer/module/supporting-online-help) in de Microsoft docs voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bb168-230">For more information, see [Supporting Updatable Help](/powershell/scripting/developer/help/supporting-updatable-help) and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help) in the Microsoft Docs.</span></span>

<span data-ttu-id="bb168-231">Help-informatie die kan worden bijgewerkt, is niet beschikbaar voor Power shell-modules of Help op basis van opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="bb168-231">Updatable help not available for PowerShell snap-ins or comment-based help.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb168-232">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bb168-232">Remarks</span></span>

<span data-ttu-id="bb168-233">De `Update-Help` `Save-Help` cmdlets en worden niet ondersteund op Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="bb168-233">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb168-234">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bb168-234">See also</span></span>

[<span data-ttu-id="bb168-235">Get-Help</span><span class="sxs-lookup"><span data-stu-id="bb168-235">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)

[<span data-ttu-id="bb168-236">Opslaan-Help</span><span class="sxs-lookup"><span data-stu-id="bb168-236">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

[<span data-ttu-id="bb168-237">Update-Help</span><span class="sxs-lookup"><span data-stu-id="bb168-237">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)
