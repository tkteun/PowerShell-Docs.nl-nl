---
title: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
description: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264025"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="e20df-103">Visual Studio Code gebruiken voor externe bewerking en foutopsporing</span><span class="sxs-lookup"><span data-stu-id="e20df-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="e20df-104">Bedoeld voor degenen die bekend met de ISE zijn misschien herinnert u zich dat u kunt uitvoeren `psedit file.ps1` rechtstreeks vanuit de geïntegreerde console bestanden - lokale of externe - te openen in de ISE.</span><span class="sxs-lookup"><span data-stu-id="e20df-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="e20df-105">Deze functie is ook beschikbaar in de PowerShell-extensie voor VSCode.</span><span class="sxs-lookup"><span data-stu-id="e20df-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="e20df-106">Deze handleiding wordt beschreven hoe u dit doet.</span><span class="sxs-lookup"><span data-stu-id="e20df-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e20df-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e20df-107">Prerequisites</span></span>

<span data-ttu-id="e20df-108">Deze handleiding wordt ervan uitgegaan dat u hebt:</span><span class="sxs-lookup"><span data-stu-id="e20df-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="e20df-109">een externe bron (bijvoorbeeld: een virtuele machine, een container) dat u toegang tot hebt</span><span class="sxs-lookup"><span data-stu-id="e20df-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="e20df-110">PowerShell die worden uitgevoerd op deze en de hostcomputer</span><span class="sxs-lookup"><span data-stu-id="e20df-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="e20df-111">VSCode en de PowerShell-extensie voor VSCode</span><span class="sxs-lookup"><span data-stu-id="e20df-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="e20df-112">Deze functie werkt op Windows PowerShell en PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e20df-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="e20df-113">Deze functie werkt ook bij het verbinden met een externe computer via WinRM, PowerShell Direct of SSH.</span><span class="sxs-lookup"><span data-stu-id="e20df-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="e20df-114">Als u wilt gebruiken van SSH, maar met behulp van Windows, bekijk dan de [Win32-versie van SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="e20df-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e20df-115">De `Open-EditorFile` en `psedit` opdrachten alleen werken in de **PowerShell geïntegreerde Console** gemaakt door de PowerShell-extensie voor VSCode.</span><span class="sxs-lookup"><span data-stu-id="e20df-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="e20df-116">Voorbeelden van het gebruik</span><span class="sxs-lookup"><span data-stu-id="e20df-116">Usage examples</span></span>

<span data-ttu-id="e20df-117">Deze voorbeelden tonen externe bewerken en foutopsporing via een MacBook Pro op een Ubuntu-VM die wordt uitgevoerd in Azure.</span><span class="sxs-lookup"><span data-stu-id="e20df-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="e20df-118">Het proces is vrijwel identiek in Windows.</span><span class="sxs-lookup"><span data-stu-id="e20df-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="e20df-119">Lokaal bestand bewerken met Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="e20df-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="e20df-120">Met de PowerShell-extensie voor VSCode gestart en de geïntegreerde PowerShell-Console hebt geopend, kunnen we typen `Open-EditorFile foo.ps1` of `psedit foo.ps1` lokale foo.ps1 bestand rechts in de editor te openen.</span><span class="sxs-lookup"><span data-stu-id="e20df-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 werkt lokaal](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="e20df-122">Het bestand `foo.ps1` moet al bestaan.</span><span class="sxs-lookup"><span data-stu-id="e20df-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="e20df-123">Van daaruit kunnen we:</span><span class="sxs-lookup"><span data-stu-id="e20df-123">From there, we can:</span></span>

- <span data-ttu-id="e20df-124">Onderbrekingspunten toevoegen aan de tussenruimte</span><span class="sxs-lookup"><span data-stu-id="e20df-124">Add breakpoints to the gutter</span></span>

  ![onderbrekingspunt naar rugmarge toevoegen](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="e20df-126">Druk op F5 om op te sporen in het PowerShell-script.</span><span class="sxs-lookup"><span data-stu-id="e20df-126">Hit F5 to debug the PowerShell script.</span></span>

  ![het lokale PowerShell-script-foutopsporing](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="e20df-128">Tijdens het opsporen van fouten, kunt u communiceren met de console voor foutopsporing, bekijk de variabelen in het bereik aan de linkerkant en alle andere standard hulpmiddelen voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e20df-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="e20df-129">Extern bestand bewerken met Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="e20df-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="e20df-130">Nu gaan we krijgen tot externe bestand bewerken en het opsporen van fouten.</span><span class="sxs-lookup"><span data-stu-id="e20df-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="e20df-131">De stappen zijn vrijwel hetzelfde, wordt er slechts één wat die we moeten eerst doen - opgeven van onze PowerShell-sessie met de externe server.</span><span class="sxs-lookup"><span data-stu-id="e20df-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="e20df-132">Er is een cmdlet voor om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="e20df-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="e20df-133">Dit heet `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="e20df-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="e20df-134">De watered omlaag uitleg van de cmdlet is:</span><span class="sxs-lookup"><span data-stu-id="e20df-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="e20df-135">`Enter-PSSession -ComputerName foo` Hiermee wordt een sessie via WinRM gestart</span><span class="sxs-lookup"><span data-stu-id="e20df-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="e20df-136">`Enter-PSSession -ContainerId foo` en `Enter-PSSession -VmId foo` een sessie via PowerShell Direct starten</span><span class="sxs-lookup"><span data-stu-id="e20df-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="e20df-137">`Enter-PSSession -HostName foo` Hiermee wordt een sessie via SSH gestart</span><span class="sxs-lookup"><span data-stu-id="e20df-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="e20df-138">Zie voor meer informatie de documentatie voor [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="e20df-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="e20df-139">Daar gaan we in Mac OS een Ubuntu-VM in Azure, we SSH gebruiken voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="e20df-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="e20df-140">Voer eerst in de geïntegreerde Console `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="e20df-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="e20df-141">U bent verbonden met de externe sessie wanneer `[<hostname>]` geeft tot aan de linkerkant van de opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="e20df-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![De aanroep naar de Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="e20df-143">We kunnen nu dezelfde stappen doen als we een lokale-script bewerkt.</span><span class="sxs-lookup"><span data-stu-id="e20df-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="e20df-144">Voer `Open-EditorFile test.ps1` of `psedit test.ps1` openen van de externe `test.ps1` bestand</span><span class="sxs-lookup"><span data-stu-id="e20df-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Het bestand test.ps1 Open-EditorFile](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="e20df-146">Het bestand/set-onderbrekingspunten bewerken</span><span class="sxs-lookup"><span data-stu-id="e20df-146">Edit the file/set breakpoints</span></span>

   ![bewerken en onderbrekingspunten instellen](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="e20df-148">Foutopsporing (F5) het externe bestand starten</span><span class="sxs-lookup"><span data-stu-id="e20df-148">Start debugging (F5) the remote file</span></span>

   ![foutopsporing van het externe bestand](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="e20df-150">Als u problemen hebt, kunt u problemen in openen de [GitHub-opslagplaats](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="e20df-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
