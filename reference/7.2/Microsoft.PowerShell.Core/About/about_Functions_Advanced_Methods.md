---
description: Hierin wordt beschreven hoe functies die het `CmdletBinding` kenmerk opgeven, de methoden en eigenschappen kunnen gebruiken die beschikbaar zijn voor gecompileerde cmdlets.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 13a9d7258f1a52d5fcbb2d8c55b91c8d6454452d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706237"
---
# <a name="about-functions-advanced-methods"></a><span data-ttu-id="2f38c-103">Over functies geavanceerde methoden</span><span class="sxs-lookup"><span data-stu-id="2f38c-103">About Functions Advanced Methods</span></span>

## <a name="short-description"></a><span data-ttu-id="2f38c-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="2f38c-104">Short description</span></span>

<span data-ttu-id="2f38c-105">Hierin wordt beschreven hoe functies die het `CmdletBinding` kenmerk opgeven, de methoden en eigenschappen kunnen gebruiken die beschikbaar zijn voor gecompileerde cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2f38c-105">Describes how functions that specify the `CmdletBinding` attribute can use the methods and properties that are available to compiled cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="2f38c-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="2f38c-106">Long description</span></span>

<span data-ttu-id="2f38c-107">Functies waarmee het `CmdletBinding` kenmerk wordt opgegeven, hebben toegang tot een aantal methoden en eigenschappen via de `$PSCmdlet` variabele.</span><span class="sxs-lookup"><span data-stu-id="2f38c-107">Functions that specify the `CmdletBinding` attribute can access a number of methods and properties through the `$PSCmdlet` variable.</span></span> <span data-ttu-id="2f38c-108">Deze methoden omvatten de volgende methoden:</span><span class="sxs-lookup"><span data-stu-id="2f38c-108">These methods include the following methods:</span></span>

- <span data-ttu-id="2f38c-109">Methoden voor het uitvoeren van invoer waarbij cmdlets worden gebruikt om hun werk uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2f38c-109">Input-processing methods that compiled cmdlets use to do their work.</span></span>
- <span data-ttu-id="2f38c-110">De `ShouldProcess` `ShouldContinue` methoden en die worden gebruikt om gebruikers feedback te krijgen voordat een actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2f38c-110">The `ShouldProcess` and `ShouldContinue` methods that are used to get user feedback before an action is performed.</span></span>
- <span data-ttu-id="2f38c-111">De `ThrowTerminatingError` methode voor het genereren van fout records.</span><span class="sxs-lookup"><span data-stu-id="2f38c-111">The `ThrowTerminatingError` method for generating error records.</span></span>
- <span data-ttu-id="2f38c-112">Verschillende `Write` methoden die verschillende soorten uitvoer retour neren.</span><span class="sxs-lookup"><span data-stu-id="2f38c-112">Several `Write` methods that return different types of output.</span></span>

<span data-ttu-id="2f38c-113">Alle methoden en eigenschappen van de klasse **PSCmdlet** zijn beschikbaar voor geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="2f38c-113">All the methods and properties of the **PSCmdlet** class are available to advanced functions.</span></span> <span data-ttu-id="2f38c-114">Zie [System. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-114">For more information, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="2f38c-115">Zie about_Functions_CmdletBindingAttribute voor meer informatie over het `CmdletBinding` kenmerk [](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="2f38c-115">For more information about the `CmdletBinding` attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>
<span data-ttu-id="2f38c-116">Zie [System. Management. Automation. cmdlet. CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute)voor de **CmdletBindingAttribute** -klasse.</span><span class="sxs-lookup"><span data-stu-id="2f38c-116">For the **CmdletBindingAttribute** class, see [System.Management.Automation.Cmdlet.CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute).</span></span>

### <a name="input-processing-methods"></a><span data-ttu-id="2f38c-117">Invoer verwerkings methoden</span><span class="sxs-lookup"><span data-stu-id="2f38c-117">Input processing methods</span></span>

<span data-ttu-id="2f38c-118">De methoden die in deze sectie worden beschreven, worden de invoer verwerkings methoden genoemd.</span><span class="sxs-lookup"><span data-stu-id="2f38c-118">The methods described in this section are referred to as the input processing methods.</span></span> <span data-ttu-id="2f38c-119">Voor-functies worden deze drie methoden vertegenwoordigd door de `Begin` , `Process` en, en `End` de blokken van de functie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-119">For functions, these three methods are represented by the `Begin`, `Process`, and `End` blocks of the function.</span></span> <span data-ttu-id="2f38c-120">U hoeft geen van deze blokken in uw functies te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2f38c-120">You aren't required to use any of these blocks in your functions.</span></span>

> [!NOTE]
> <span data-ttu-id="2f38c-121">Deze blokken zijn ook beschikbaar voor functies die niet gebruikmaken van het- `CmdletBinding` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="2f38c-121">These blocks are also available to functions that don't use the `CmdletBinding` attribute.</span></span>

#### <a name="begin"></a><span data-ttu-id="2f38c-122">Beginnen</span><span class="sxs-lookup"><span data-stu-id="2f38c-122">Begin</span></span>

<span data-ttu-id="2f38c-123">Dit blok wordt gebruikt om de functie optioneel een eenmalige voor verwerking te bieden.</span><span class="sxs-lookup"><span data-stu-id="2f38c-123">This block is used to provide optional one-time preprocessing for the function.</span></span>
<span data-ttu-id="2f38c-124">De Power shell-runtime gebruikt de code in dit blok keer voor elk exemplaar van de functie in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="2f38c-124">The PowerShell runtime uses the code in this block once for each instance of the function in the pipeline.</span></span>

#### <a name="process"></a><span data-ttu-id="2f38c-125">Proces</span><span class="sxs-lookup"><span data-stu-id="2f38c-125">Process</span></span>

<span data-ttu-id="2f38c-126">Dit blok wordt gebruikt om de verwerking van records per record te bieden voor de functie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-126">This block is used to provide record-by-record processing for the function.</span></span> <span data-ttu-id="2f38c-127">U kunt een `Process` blok gebruiken zonder de andere blokken te definiëren.</span><span class="sxs-lookup"><span data-stu-id="2f38c-127">You can use a `Process` block without defining the other blocks.</span></span> <span data-ttu-id="2f38c-128">Het aantal `Process` blok uitvoeringen is afhankelijk van hoe u de functie gebruikt en wat invoer van de functie ontvangt.</span><span class="sxs-lookup"><span data-stu-id="2f38c-128">The number of `Process` block executions depends on how you use the function and what input the function receives.</span></span>

<span data-ttu-id="2f38c-129">De automatische variabele `$_` of `$PSItem` bevat het huidige object in de pijp lijn voor gebruik in het `Process` blok.</span><span class="sxs-lookup"><span data-stu-id="2f38c-129">The automatic variable `$_` or `$PSItem` contains the current object in the pipeline for use in the `Process` block.</span></span> <span data-ttu-id="2f38c-130">De `$input` Automatische variabele bevat een enumerator die alleen beschikbaar is voor functies en script blokken.</span><span class="sxs-lookup"><span data-stu-id="2f38c-130">The `$input` automatic variable contains an enumerator that's only available to functions and script blocks.</span></span>
<span data-ttu-id="2f38c-131">Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-131">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="2f38c-132">Als u de functie aan het begin of buiten een pijp lijn aanroept, wordt het `Process` blok eenmaal uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2f38c-132">Calling the function at the beginning, or outside of a pipeline, executes the `Process` block once.</span></span>
- <span data-ttu-id="2f38c-133">Binnen een pijp lijn wordt het `Process` blok eenmaal uitgevoerd voor elk invoer object dat de functie bereikt.</span><span class="sxs-lookup"><span data-stu-id="2f38c-133">Within a pipeline, the `Process` block executes once for each input object that reaches the function.</span></span>
- <span data-ttu-id="2f38c-134">Als de pijplijn invoer die de functie bereikt, leeg is, wordt het `Process` blok **niet** uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2f38c-134">If the pipeline input that reaches the function is empty, the `Process` block **does not** execute.</span></span>
  - <span data-ttu-id="2f38c-135">De `Begin` blokken en worden `End` nog steeds uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2f38c-135">The `Begin` and `End` blocks still execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f38c-136">Als een functie parameter is ingesteld om pijplijn invoer te accepteren en er geen `Process` blok is gedefinieerd, mislukt record-voor-record verwerking.</span><span class="sxs-lookup"><span data-stu-id="2f38c-136">If a function parameter is set to accept pipeline input, and a `Process` block isn't defined, record-by-record processing will fail.</span></span> <span data-ttu-id="2f38c-137">In dit geval wordt de functie slechts één keer uitgevoerd, ongeacht de invoer.</span><span class="sxs-lookup"><span data-stu-id="2f38c-137">In this case, your function will only execute once, regardless of the input.</span></span>

#### <a name="end"></a><span data-ttu-id="2f38c-138">Beëindigen</span><span class="sxs-lookup"><span data-stu-id="2f38c-138">End</span></span>

<span data-ttu-id="2f38c-139">Dit blok wordt gebruikt om een eenmalige naverwerking te bieden voor de functie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-139">This block is used to provide optional one-time post-processing for the function.</span></span>

<span data-ttu-id="2f38c-140">In het volgende voor beeld ziet u het overzicht van een functie die een `Begin` blok bevat voor eenmalige voor verwerking, een `Process` blok voor het verwerken van meerdere records en een `End` blok keren voor eenmalige verwerking.</span><span class="sxs-lookup"><span data-stu-id="2f38c-140">The following example shows the outline of a function that contains a `Begin` block for one-time preprocessing, a `Process` block for multiple record processing, and an `End` block for one-time post-processing.</span></span>

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> <span data-ttu-id="2f38c-141">Voor het gebruik van een `Begin` of- `End` blok is vereist dat u alle drie de blokken definieert.</span><span class="sxs-lookup"><span data-stu-id="2f38c-141">Using either a `Begin` or `End` block requires that you define all three blocks.</span></span> <span data-ttu-id="2f38c-142">Wanneer u alle drie de blokken gebruikt, moet alle Power shell-code zich in een van de blokken bevinden.</span><span class="sxs-lookup"><span data-stu-id="2f38c-142">When using all three blocks, all PowerShell code must be inside one of the blocks.</span></span>

### <a name="confirmation-methods"></a><span data-ttu-id="2f38c-143">Bevestigings methoden</span><span class="sxs-lookup"><span data-stu-id="2f38c-143">Confirmation methods</span></span>

#### <a name="shouldprocess"></a><span data-ttu-id="2f38c-144">ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="2f38c-144">ShouldProcess</span></span>

<span data-ttu-id="2f38c-145">Deze methode wordt aangeroepen om bevestiging van de gebruiker aan te vragen voordat de functie een actie uitvoert waardoor het systeem wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2f38c-145">This method is called to request confirmation from the user before the function performs an action that would change the system.</span></span> <span data-ttu-id="2f38c-146">De functie kan worden voortgezet op basis van de Booleaanse waarde die door de methode wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2f38c-146">The function can continue based on the Boolean value returned by the method.</span></span> <span data-ttu-id="2f38c-147">Deze methode kan alleen worden aangeroepen vanuit het `Process{}` blok van de functie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-147">This method can only be called only from within the `Process{}` block of the function.</span></span> <span data-ttu-id="2f38c-148">Het `CmdletBinding` kenmerk moet ook declareren dat de functie ondersteunt `ShouldProcess` (zoals weer gegeven in het vorige voor beeld).</span><span class="sxs-lookup"><span data-stu-id="2f38c-148">The `CmdletBinding` attribute must also declare that the function supports `ShouldProcess` (as shown in the previous example).</span></span>

<span data-ttu-id="2f38c-149">Zie [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess)voor meer informatie over deze methode.</span><span class="sxs-lookup"><span data-stu-id="2f38c-149">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess).</span></span>

<span data-ttu-id="2f38c-150">Zie [bevestiging aanvragen](/powershell/scripting/developer/cmdlet/requesting-confirmation)voor meer informatie over het aanvragen van een bevestiging.</span><span class="sxs-lookup"><span data-stu-id="2f38c-150">For more information about how to request confirmation, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

#### <a name="shouldcontinue"></a><span data-ttu-id="2f38c-151">ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="2f38c-151">ShouldContinue</span></span>

<span data-ttu-id="2f38c-152">Deze methode wordt aangeroepen om een tweede bevestigings bericht aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="2f38c-152">This method is called to request a second confirmation message.</span></span> <span data-ttu-id="2f38c-153">Deze moet worden aangeroepen wanneer de `ShouldProcess` methode wordt geretourneerd `$true` .</span><span class="sxs-lookup"><span data-stu-id="2f38c-153">It should be called when the `ShouldProcess` method returns `$true`.</span></span> <span data-ttu-id="2f38c-154">Zie [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)voor meer informatie over deze methode.</span><span class="sxs-lookup"><span data-stu-id="2f38c-154">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).</span></span>

### <a name="error-methods"></a><span data-ttu-id="2f38c-155">Fout methoden</span><span class="sxs-lookup"><span data-stu-id="2f38c-155">Error methods</span></span>

<span data-ttu-id="2f38c-156">Functies kunnen twee verschillende methoden aanroepen wanneer er fouten optreden.</span><span class="sxs-lookup"><span data-stu-id="2f38c-156">Functions can call two different methods when errors occur.</span></span> <span data-ttu-id="2f38c-157">Wanneer er een niet-afsluit fout optreedt, moet de functie de methode aanroepen `WriteError` , die wordt beschreven in de `Write` sectie methoden.</span><span class="sxs-lookup"><span data-stu-id="2f38c-157">When a non-terminating error occurs, the function should call the `WriteError` method, which is described in the `Write` methods section.</span></span> <span data-ttu-id="2f38c-158">Als er een afsluit fout optreedt en de functie kan niet worden voortgezet, moet de `ThrowTerminatingError` methode worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="2f38c-158">When a terminating error occurs and the function can't continue, it should call the `ThrowTerminatingError` method.</span></span> <span data-ttu-id="2f38c-159">U kunt ook de- `Throw` instructie voor het beëindigen van fouten en de cmdlet [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) gebruiken voor niet-afsluit fouten.</span><span class="sxs-lookup"><span data-stu-id="2f38c-159">You can also use the `Throw` statement for terminating errors and the [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) cmdlet for non-terminating errors.</span></span>

<span data-ttu-id="2f38c-160">Zie [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-160">For more information, see [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror).</span></span>

### <a name="write-methods"></a><span data-ttu-id="2f38c-161">Schrijf methoden</span><span class="sxs-lookup"><span data-stu-id="2f38c-161">Write methods</span></span>

<span data-ttu-id="2f38c-162">Een functie kan de volgende methoden aanroepen om verschillende typen uitvoer te retour neren.</span><span class="sxs-lookup"><span data-stu-id="2f38c-162">A function can call the following methods to return different types of output.</span></span>
<span data-ttu-id="2f38c-163">U ziet dat niet alle uitvoer naar de volgende opdracht in de pijp lijn wordt verplaatst.</span><span class="sxs-lookup"><span data-stu-id="2f38c-163">Notice that not all the output goes to the next command in the pipeline.</span></span> <span data-ttu-id="2f38c-164">U kunt ook de verschillende `Write` cmdlets gebruiken, zoals `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="2f38c-164">You can also use the various `Write` cmdlets, such as `Write-Error`.</span></span>

#### <a name="writecommanddetail"></a><span data-ttu-id="2f38c-165">WriteCommandDetail</span><span class="sxs-lookup"><span data-stu-id="2f38c-165">WriteCommandDetail</span></span>

<span data-ttu-id="2f38c-166">`WriteCommandDetails`Zie [System. Management. Automation. cmdlet. WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)voor meer informatie over de-methode.</span><span class="sxs-lookup"><span data-stu-id="2f38c-166">For information about the `WriteCommandDetails` method, see [System.Management.Automation.Cmdlet.WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail).</span></span>

#### <a name="writedebug"></a><span data-ttu-id="2f38c-167">WriteDebug</span><span class="sxs-lookup"><span data-stu-id="2f38c-167">WriteDebug</span></span>

<span data-ttu-id="2f38c-168">Als u informatie wilt opgeven die kan worden gebruikt om problemen met een functie op te lossen, moet u de functie aanroepen met de `WriteDebug` methode.</span><span class="sxs-lookup"><span data-stu-id="2f38c-168">To provide information that can be used to troubleshoot a function, make the function call the `WriteDebug` method.</span></span> <span data-ttu-id="2f38c-169">De `WriteDebug` methode geeft fout opsporingsberichten weer voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2f38c-169">The `WriteDebug` method displays debug messages to the user.</span></span> <span data-ttu-id="2f38c-170">Zie [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-170">For more information, see [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug).</span></span>

#### <a name="writeerror"></a><span data-ttu-id="2f38c-171">WriteError</span><span class="sxs-lookup"><span data-stu-id="2f38c-171">WriteError</span></span>

<span data-ttu-id="2f38c-172">Functies moeten deze methode aanroepen wanneer er niet-afsluit fouten optreden en de functie is ontworpen om de verwerking van records voort te zetten.</span><span class="sxs-lookup"><span data-stu-id="2f38c-172">Functions should call this method when non-terminating errors occur and the function is designed to continue processing records.</span></span> <span data-ttu-id="2f38c-173">Zie [System. Management. Automation. cmdlet. WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-173">For more information, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror).</span></span>

> [!NOTE]
> <span data-ttu-id="2f38c-174">Als er een afsluit fout optreedt, moet de functie de methode [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) aanroepen.</span><span class="sxs-lookup"><span data-stu-id="2f38c-174">If a terminating error occurs, the function should call the [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) method.</span></span>

#### <a name="writeobject"></a><span data-ttu-id="2f38c-175">WriteObject</span><span class="sxs-lookup"><span data-stu-id="2f38c-175">WriteObject</span></span>

<span data-ttu-id="2f38c-176">Met de- `WriteObject` methode kan de functie een object verzenden naar de volgende opdracht in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="2f38c-176">The `WriteObject` method allows the function to send an object to the next command in the pipeline.</span></span> <span data-ttu-id="2f38c-177">In de meeste gevallen `WriteObject` is de methode die moet worden gebruikt wanneer de functie gegevens retourneert.</span><span class="sxs-lookup"><span data-stu-id="2f38c-177">In most cases, `WriteObject` is the method to use when the function returns data.</span></span> <span data-ttu-id="2f38c-178">Zie [System. Management. Automation. PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-178">For more information, see [System.Management.Automation.PSCmdlet.WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).</span></span>

#### <a name="writeprogress"></a><span data-ttu-id="2f38c-179">WriteProgress</span><span class="sxs-lookup"><span data-stu-id="2f38c-179">WriteProgress</span></span>

<span data-ttu-id="2f38c-180">Voor functies met acties die veel tijd in beslag nemen, kan met deze methode de methode worden aangeroepen, `WriteProgress` zodat de voortgangs gegevens worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2f38c-180">For functions with actions that take a long time to complete, this method allows the function to call the `WriteProgress` method so that progress information is displayed.</span></span> <span data-ttu-id="2f38c-181">U kunt bijvoorbeeld het percentage voltooid weer geven.</span><span class="sxs-lookup"><span data-stu-id="2f38c-181">For example, you can display the percent completed.</span></span>
<span data-ttu-id="2f38c-182">Zie [System. Management. Automation. PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-182">For more information, see [System.Management.Automation.PSCmdlet.WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).</span></span>

#### <a name="writeverbose"></a><span data-ttu-id="2f38c-183">WriteVerbose</span><span class="sxs-lookup"><span data-stu-id="2f38c-183">WriteVerbose</span></span>

<span data-ttu-id="2f38c-184">Als u gedetailleerde informatie over de werking van de functie wilt opgeven, moet u de functie aanroepen `WriteVerbose` om uitgebreide berichten weer te geven aan de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2f38c-184">To provide detailed information about what the function is doing, make the function call the `WriteVerbose` method to display verbose messages to the user.</span></span> <span data-ttu-id="2f38c-185">Standaard worden uitgebreide berichten niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2f38c-185">By default, verbose messages aren't displayed.</span></span> <span data-ttu-id="2f38c-186">Zie [System. Management. Automation. PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-186">For more information, see [System.Management.Automation.PSCmdlet.WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).</span></span>

#### <a name="writewarning"></a><span data-ttu-id="2f38c-187">WriteWarning</span><span class="sxs-lookup"><span data-stu-id="2f38c-187">WriteWarning</span></span>

<span data-ttu-id="2f38c-188">Als u informatie wilt geven over voor waarden die onverwachte resultaten kunnen veroorzaken, moet u de functie aanroepen met de methode WriteWarning om waarschuwings berichten voor de gebruiker weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2f38c-188">To provide information about conditions that may cause unexpected results, make the function call the WriteWarning method to display warning messages to the user.</span></span> <span data-ttu-id="2f38c-189">Standaard worden waarschuwings berichten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2f38c-189">By default, warning messages are displayed.</span></span> <span data-ttu-id="2f38c-190">Zie [System. Management. Automation. PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2f38c-190">For more information, see [System.Management.Automation.PSCmdlet.WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).</span></span>

> [!NOTE]
> <span data-ttu-id="2f38c-191">U kunt ook waarschuwings berichten weer geven door de `$WarningPreference` variabele te configureren of door `Verbose` de `Debug` opdracht regel opties te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2f38c-191">You can also display warning messages by configuring the `$WarningPreference` variable or by using the `Verbose` and `Debug` command-line options.</span></span> <span data-ttu-id="2f38c-192">Zie about_Preference_Variables voor meer informatie over de `$WarningPreference` variabele [](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="2f38c-192">for more information about the `$WarningPreference` variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="other-methods-and-properties"></a><span data-ttu-id="2f38c-193">Andere methoden en eigenschappen</span><span class="sxs-lookup"><span data-stu-id="2f38c-193">Other methods and properties</span></span>

<span data-ttu-id="2f38c-194">`$PSCmdlet`Zie [System. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)voor meer informatie over de andere methoden en eigenschappen die kunnen worden gebruikt via de variabele.</span><span class="sxs-lookup"><span data-stu-id="2f38c-194">For information about the other methods and properties that can be accessed through the `$PSCmdlet` variable, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="2f38c-195">Met de eigenschap [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) kunt u bijvoorbeeld de ingestelde para meter weer geven die wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2f38c-195">For example, the [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) property allows you to see the parameter set that is being used.</span></span> <span data-ttu-id="2f38c-196">Met parameter sets kunt u een functie maken waarmee verschillende taken worden uitgevoerd op basis van de para meters die worden opgegeven wanneer de functie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2f38c-196">Parameter sets allow you to create a function that performs different tasks based on the parameters that are specified when the function is run.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f38c-197">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2f38c-197">See also</span></span>

[<span data-ttu-id="2f38c-198">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="2f38c-198">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="2f38c-199">about_Functions</span><span class="sxs-lookup"><span data-stu-id="2f38c-199">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="2f38c-200">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="2f38c-200">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="2f38c-201">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="2f38c-201">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="2f38c-202">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="2f38c-202">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="2f38c-203">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="2f38c-203">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="2f38c-204">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="2f38c-204">about_Preference_Variables</span></span>](about_Preference_Variables.md)

