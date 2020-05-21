---
title: Een werk stroom maken met Windows Power shell-activiteiten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 12b0b246b78142f3811f9f566cd94e4dabd40cc9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557462"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="9c0ac-102">Een werkstroom maken met Windows PowerShell-activiteiten</span><span class="sxs-lookup"><span data-stu-id="9c0ac-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="9c0ac-103">U kunt een Windows Power shell-werk stroom maken door activiteiten in de Visual Studio-werkset te selecteren en deze naar het Workflow Designer venster te slepen.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="9c0ac-104">Zie [Windows Power shell-activiteiten toevoegen aan de werkset van Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)voor meer informatie over het toevoegen van Windows Power shell-activiteiten aan de Visual Studio-werkset.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="9c0ac-105">In de volgende procedures wordt beschreven hoe u een werk stroom maakt waarmee de domein status wordt gecontroleerd van een groep door de gebruiker opgegeven computers, wordt toegevoegd aan een domein als deze nog niet is gekoppeld en vervolgens de status opnieuw controleert.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="9c0ac-106">Het project instellen</span><span class="sxs-lookup"><span data-stu-id="9c0ac-106">Setting up the Project</span></span>

1. <span data-ttu-id="9c0ac-107">Volg de procedure in [Windows Power shell-activiteiten toevoegen aan de Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) om een werk stroom project te maken en voeg de activiteiten toe vanuit de [micro soft. Power shell. activities](/dotnet/api/Microsoft.PowerShell.Activities) en [micro soft. Power shell. Management. activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) -assembly's in de werkset.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="9c0ac-108">Voeg System. Management. Automation, micro soft. Power shell. activities, System. Management, micro soft. Power shell. Management. activities en micro soft. Power shell. commands. Management toe aan het project als referentie verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="9c0ac-109">Activiteiten toevoegen aan de werk stroom</span><span class="sxs-lookup"><span data-stu-id="9c0ac-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="9c0ac-110">Voeg een **reeks** activiteit toe aan de werk stroom.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="9c0ac-111">Maak een argument `ComputerName` met de naam met een argument type van `String[]` .</span><span class="sxs-lookup"><span data-stu-id="9c0ac-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="9c0ac-112">Dit argument vertegenwoordigt de namen van de computers die moeten worden gecontroleerd en toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="9c0ac-113">Maak een argument met de naam `DomainCred` van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="9c0ac-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="9c0ac-114">Dit argument vertegenwoordigt de domein referenties van een domein account dat is gemachtigd om een computer toe te voegen aan het domein.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="9c0ac-115">Maak een argument met de naam `MachineCred` van het type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="9c0ac-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="9c0ac-116">Dit argument vertegenwoordigt de referenties van een beheerder op de computers om te controleren en samen te voegen.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="9c0ac-117">Voeg een **ParallelForEach** -activiteit toe binnen de **reeks** activiteit.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="9c0ac-118">Typ `comp` en `ComputerName` in de tekst vakken zodat de lus door de elementen van de matrix doorloopt `ComputerName` .</span><span class="sxs-lookup"><span data-stu-id="9c0ac-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="9c0ac-119">Voeg een **sequentie** activiteit toe aan de hoofd tekst van de **ParallelForEach** -activiteit.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="9c0ac-120">Stel de eigenschap **DisplayName** van de reeks in op `JoinDomain` .</span><span class="sxs-lookup"><span data-stu-id="9c0ac-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="9c0ac-121">Voeg een **GetWmiObject** -activiteit toe aan de **JoinDomain** -reeks.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="9c0ac-122">Bewerk de eigenschappen van de **GetWmiObject** -activiteit als volgt.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="9c0ac-123">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="9c0ac-123">Property</span></span>|<span data-ttu-id="9c0ac-124">Waarde</span><span class="sxs-lookup"><span data-stu-id="9c0ac-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="9c0ac-125">**Klasse**</span><span class="sxs-lookup"><span data-stu-id="9c0ac-125">**Class**</span></span>|<span data-ttu-id="9c0ac-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="9c0ac-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="9c0ac-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="9c0ac-127">**PSComputerName**</span></span>|<span data-ttu-id="9c0ac-128">Comp</span><span class="sxs-lookup"><span data-stu-id="9c0ac-128">{comp}</span></span>|
   |<span data-ttu-id="9c0ac-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="9c0ac-129">**PSCredential**</span></span>|<span data-ttu-id="9c0ac-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="9c0ac-130">MachineCred</span></span>|

9. <span data-ttu-id="9c0ac-131">Voeg een **AddComputer** -activiteit toe aan de **JoinDomain** -reeks na de activiteit **GetWmiObject** .</span><span class="sxs-lookup"><span data-stu-id="9c0ac-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="9c0ac-132">Bewerk de eigenschappen van de **AddComputer** -activiteit als volgt.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="9c0ac-133">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="9c0ac-133">Property</span></span>|<span data-ttu-id="9c0ac-134">Waarde</span><span class="sxs-lookup"><span data-stu-id="9c0ac-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="9c0ac-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="9c0ac-135">**ComputerName**</span></span>|<span data-ttu-id="9c0ac-136">Comp</span><span class="sxs-lookup"><span data-stu-id="9c0ac-136">{comp}</span></span>|
    |<span data-ttu-id="9c0ac-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="9c0ac-137">**DomainCredential**</span></span>|<span data-ttu-id="9c0ac-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="9c0ac-138">DomainCred</span></span>|

11. <span data-ttu-id="9c0ac-139">Voeg een **RestartComputer** -activiteit toe aan de **JoinDomain** -reeks na de activiteit **AddComputer** .</span><span class="sxs-lookup"><span data-stu-id="9c0ac-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="9c0ac-140">Bewerk de eigenschappen van de **RestartComputer** -activiteit als volgt.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="9c0ac-141">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="9c0ac-141">Property</span></span>|<span data-ttu-id="9c0ac-142">Waarde</span><span class="sxs-lookup"><span data-stu-id="9c0ac-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="9c0ac-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="9c0ac-143">**ComputerName**</span></span>|<span data-ttu-id="9c0ac-144">Comp</span><span class="sxs-lookup"><span data-stu-id="9c0ac-144">{comp}</span></span>|
    |<span data-ttu-id="9c0ac-145">**Referentie**</span><span class="sxs-lookup"><span data-stu-id="9c0ac-145">**Credential**</span></span>|<span data-ttu-id="9c0ac-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="9c0ac-146">MachineCred</span></span>|
    |<span data-ttu-id="9c0ac-147">**Zo**</span><span class="sxs-lookup"><span data-stu-id="9c0ac-147">**For**</span></span>|<span data-ttu-id="9c0ac-148">Micro soft. Power shell. commands. WaitForServiceTypes. Power shell</span><span class="sxs-lookup"><span data-stu-id="9c0ac-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="9c0ac-149">**Verkopers**</span><span class="sxs-lookup"><span data-stu-id="9c0ac-149">**Force**</span></span>|<span data-ttu-id="9c0ac-150">True</span><span class="sxs-lookup"><span data-stu-id="9c0ac-150">True</span></span>|
    |<span data-ttu-id="9c0ac-151">Wait</span><span class="sxs-lookup"><span data-stu-id="9c0ac-151">Wait</span></span>|<span data-ttu-id="9c0ac-152">True</span><span class="sxs-lookup"><span data-stu-id="9c0ac-152">True</span></span>|
    |<span data-ttu-id="9c0ac-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="9c0ac-153">PSComputerName</span></span>|<span data-ttu-id="9c0ac-154">{""}</span><span class="sxs-lookup"><span data-stu-id="9c0ac-154">{""}</span></span>|

13. <span data-ttu-id="9c0ac-155">Voeg een **GetWmiObject** -activiteit toe aan de **JoinDomain** -reeks na de activiteit **RestartComputer** .</span><span class="sxs-lookup"><span data-stu-id="9c0ac-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="9c0ac-156">Bewerk de eigenschappen zodanig dat deze hetzelfde zijn als de vorige **GetWmiObject** -activiteit.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="9c0ac-157">Wanneer u de procedures hebt voltooid, ziet het werk stroom ontwerp venster er als volgt uit.</span><span class="sxs-lookup"><span data-stu-id="9c0ac-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="9c0ac-158">![JoinDomain XAML in Workflow Designer ](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
     ![JoinDomain XAML in Workflow Designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="9c0ac-158">![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span></span>
