---
description: Hierin wordt beschreven hoe u kunt werken met opdracht parameters in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: 7cc5c071116df8d3326a4ea13802227d350bfac3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252774"
---
# <a name="about-parameters"></a><span data-ttu-id="d51bb-104">Over para meters</span><span class="sxs-lookup"><span data-stu-id="d51bb-104">About Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="d51bb-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="d51bb-105">Short description</span></span>
<span data-ttu-id="d51bb-106">Hierin wordt beschreven hoe u kunt werken met opdracht parameters in Power shell.</span><span class="sxs-lookup"><span data-stu-id="d51bb-106">Describes how to work with command parameters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d51bb-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="d51bb-107">Long description</span></span>

<span data-ttu-id="d51bb-108">De meeste Power shell-opdrachten, zoals cmdlets, functies en scripts, zijn afhankelijk van para meters waarmee gebruikers opties kunnen selecteren of invoer kunnen opgeven.</span><span class="sxs-lookup"><span data-stu-id="d51bb-108">Most PowerShell commands, such as cmdlets, functions, and scripts, rely on parameters to allow users to select options or provide input.</span></span> <span data-ttu-id="d51bb-109">De para meters volgen de naam van de opdracht en hebben de volgende vorm:</span><span class="sxs-lookup"><span data-stu-id="d51bb-109">The parameters follow the command name and have the following form:</span></span>

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

<span data-ttu-id="d51bb-110">De naam van de para meter wordt voorafgegaan door een koppel teken (-), waarmee wordt gesignaleerd naar Power shell dat het woord na het afbreek streepje een parameter naam is.</span><span class="sxs-lookup"><span data-stu-id="d51bb-110">The name of the parameter is preceded by a hyphen (-), which signals to PowerShell that the word following the hyphen is a parameter name.</span></span> <span data-ttu-id="d51bb-111">De naam en waarde van de para meter kunnen worden gescheiden door een spatie of een punt komma.</span><span class="sxs-lookup"><span data-stu-id="d51bb-111">The parameter name and value can be separated by a space or a colon character.</span></span> <span data-ttu-id="d51bb-112">Sommige para meters vereisen of accepteren geen parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="d51bb-112">Some parameters do not require or accept a parameter value.</span></span> <span data-ttu-id="d51bb-113">Andere para meters hebben een waarde nodig, maar de parameter naam is niet vereist in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d51bb-113">Other parameters require a value, but do not require the parameter name in the command.</span></span>

<span data-ttu-id="d51bb-114">Het type para meters en de vereisten voor die para meters kunnen verschillen.</span><span class="sxs-lookup"><span data-stu-id="d51bb-114">The type of parameters and the requirements for those parameters vary.</span></span> <span data-ttu-id="d51bb-115">Als u informatie wilt vinden over de para meters van een opdracht, gebruikt u de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d51bb-115">To find information about the parameters of a command, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="d51bb-116">Als u bijvoorbeeld informatie zoekt over de para meters van de `Get-ChildItem` cmdlet, typt u:</span><span class="sxs-lookup"><span data-stu-id="d51bb-116">For example, to find information about the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="d51bb-117">Als u informatie wilt vinden over de para meters van een script, gebruikt u het volledige pad naar het script bestand.</span><span class="sxs-lookup"><span data-stu-id="d51bb-117">To find information about the parameters of a script, use the full path to the script file.</span></span> <span data-ttu-id="d51bb-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d51bb-118">For example:</span></span>

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

<span data-ttu-id="d51bb-119">De `Get-Help` cmdlet retourneert verschillende details over de opdracht, met inbegrip van een beschrijving, de syntaxis van de opdracht, informatie over de para meters en voor beelden die laten zien hoe u de para meters in een opdracht kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d51bb-119">The `Get-Help` cmdlet returns various details about the command, including a description, the command syntax, information about the parameters, and examples showing how to use the parameters in a command.</span></span>

<span data-ttu-id="d51bb-120">U kunt ook de para meter parameter van de `Get-Help` cmdlet gebruiken om informatie te zoeken over een bepaalde para meter.</span><span class="sxs-lookup"><span data-stu-id="d51bb-120">You can also use the Parameter parameter of the `Get-Help` cmdlet to find information about a particular parameter.</span></span> <span data-ttu-id="d51bb-121">Of u kunt de para meter **parameter** met de waarde Joker teken ( `*` ) gebruiken om informatie te zoeken over alle para meters van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d51bb-121">Or, you can use the **Parameter** parameter with the wildcard character ( `*` ) value to find information about all parameters of the command.</span></span> <span data-ttu-id="d51bb-122">Met de volgende opdracht wordt bijvoorbeeld informatie over alle para meters van de `Get-Member` cmdlet opgehaald:</span><span class="sxs-lookup"><span data-stu-id="d51bb-122">For example, the following command gets information about all parameters of the `Get-Member` cmdlet:</span></span>

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a><span data-ttu-id="d51bb-123">Standaard parameter waarden</span><span class="sxs-lookup"><span data-stu-id="d51bb-123">Default parameter values</span></span>

<span data-ttu-id="d51bb-124">Optionele para meters hebben een standaard waarde. Dit is de waarde die wordt gebruikt of wordt aangenomen wanneer de para meter niet is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d51bb-124">Optional parameters have a default value, which is the value that is used or assumed when the parameter is not specified in the command.</span></span>

<span data-ttu-id="d51bb-125">De standaard waarde van de para meter **ComputerName** van veel cmdlets is bijvoorbeeld de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d51bb-125">For example, the default value of the **ComputerName** parameter of many cmdlets is the name of the local computer.</span></span> <span data-ttu-id="d51bb-126">Als gevolg hiervan wordt de naam van de lokale computer in de opdracht gebruikt, tenzij u de para meter **ComputerName** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="d51bb-126">As a result, the local computer name is used in the command unless the **ComputerName** parameter is specified.</span></span>

<span data-ttu-id="d51bb-127">Zie het Help-onderwerp voor de cmdlet om de standaard parameter waarde te vinden.</span><span class="sxs-lookup"><span data-stu-id="d51bb-127">To find the default parameter value, see help topic for the cmdlet.</span></span> <span data-ttu-id="d51bb-128">De parameter beschrijving moet de standaard waarde bevatten.</span><span class="sxs-lookup"><span data-stu-id="d51bb-128">The parameter description should include the default value.</span></span>

<span data-ttu-id="d51bb-129">U kunt ook een aangepaste standaard waarde instellen voor elke para meter van een cmdlet of een geavanceerde functie.</span><span class="sxs-lookup"><span data-stu-id="d51bb-129">You can also set a custom default value for any parameter of a cmdlet or advanced function.</span></span> <span data-ttu-id="d51bb-130">Zie [about_Parameters_Default_Values](about_Parameters_Default_Values.md)voor meer informatie over het instellen van aangepaste standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="d51bb-130">For information about setting custom default values, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="d51bb-131">Parameter kenmerk tabel</span><span class="sxs-lookup"><span data-stu-id="d51bb-131">Parameter attribute table</span></span>

<span data-ttu-id="d51bb-132">Wanneer u de para meters **Full** , **para meter** of **online** van de `Get-Help` cmdlet gebruikt, `Get-Help` wordt een tabel met parameter kenmerken weer gegeven met gedetailleerde informatie over de para meter.</span><span class="sxs-lookup"><span data-stu-id="d51bb-132">When you use the **Full** , **Parameter** , or **Online** parameters of the `Get-Help` cmdlet, `Get-Help` displays a parameter attribute table with detailed information about the parameter.</span></span>

<span data-ttu-id="d51bb-133">Deze informatie bevat de details die u moet kennen om de para meter te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d51bb-133">This information includes the details you need to know to use the parameter.</span></span>
<span data-ttu-id="d51bb-134">Het Help-onderwerp voor de `Get-ChildItem` cmdlet bevat bijvoorbeeld de volgende gegevens over de para meter Path:</span><span class="sxs-lookup"><span data-stu-id="d51bb-134">For example, the help topic for the `Get-ChildItem` cmdlet includes the following details about its Path parameter:</span></span>

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

<span data-ttu-id="d51bb-135">De parameter informatie bevat de syntaxis van de para meter, een beschrijving van de para meter en de parameter kenmerken.</span><span class="sxs-lookup"><span data-stu-id="d51bb-135">The parameter information includes the parameter syntax, a description of the parameter, and the parameter attributes.</span></span> <span data-ttu-id="d51bb-136">In de volgende secties worden de parameter kenmerken beschreven.</span><span class="sxs-lookup"><span data-stu-id="d51bb-136">The following sections describe the parameter attributes.</span></span>

#### <a name="parameter-required"></a><span data-ttu-id="d51bb-137">Para meter vereist</span><span class="sxs-lookup"><span data-stu-id="d51bb-137">Parameter Required</span></span>

<span data-ttu-id="d51bb-138">Met deze instelling geeft u aan of de para meter verplicht is, dat wil zeggen of alle opdrachten die gebruikmaken van deze cmdlet deze para meter moeten bevatten.</span><span class="sxs-lookup"><span data-stu-id="d51bb-138">This setting indicates whether the parameter is mandatory, that is, whether all commands that use this cmdlet must include this parameter.</span></span> <span data-ttu-id="d51bb-139">Als de waarde **True** is en de para meter in de opdracht ontbreekt, vraagt Power shell u om een waarde voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="d51bb-139">When the value is **True** and the parameter is missing from the command, PowerShell prompts you for a value for the parameter.</span></span>

#### <a name="parameter-position"></a><span data-ttu-id="d51bb-140">Parameter positie</span><span class="sxs-lookup"><span data-stu-id="d51bb-140">Parameter Position</span></span>

<span data-ttu-id="d51bb-141">Als de `Position` instelling is ingesteld op een positief geheel getal, is de parameter naam niet vereist.</span><span class="sxs-lookup"><span data-stu-id="d51bb-141">If the `Position` setting is set to a positive integer, the parameter name is not required.</span></span> <span data-ttu-id="d51bb-142">Dit type para meter wordt aangeduid als positionele para meter en het nummer geeft de positie aan waarin de para meter moet worden weer gegeven in verhouding tot andere positie parameters.</span><span class="sxs-lookup"><span data-stu-id="d51bb-142">This type of parameter is referred to as a positional parameter, and the number indicates the position in which the parameter must appear in relation to other positional parameters.</span></span> <span data-ttu-id="d51bb-143">Een benoemde para meter kan worden weer gegeven op elke positie na de naam van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d51bb-143">A named parameter can be listed in any position after the cmdlet name.</span></span> <span data-ttu-id="d51bb-144">Als u de parameter naam voor een positionele para meter toevoegt, kan de para meter op elke positie na de naam van de cmdlet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d51bb-144">If you include the parameter name for a positional parameter, the parameter can be listed in any position after the cmdlet name.</span></span>

<span data-ttu-id="d51bb-145">De `Get-ChildItem` cmdlet heeft bijvoorbeeld Path-en exclude-para meters.</span><span class="sxs-lookup"><span data-stu-id="d51bb-145">For example, the `Get-ChildItem` cmdlet has Path and Exclude parameters.</span></span> <span data-ttu-id="d51bb-146">De `Position` instelling voor het **pad** is **0** , wat betekent dat het een positionele para meter is.</span><span class="sxs-lookup"><span data-stu-id="d51bb-146">The `Position` setting for **Path** is **0** , which means that it is a positional parameter.</span></span> <span data-ttu-id="d51bb-147">De `Position` instelling voor **uitsluiten** heet **named**.</span><span class="sxs-lookup"><span data-stu-id="d51bb-147">The `Position` setting for **Exclude** is **named**.</span></span>

<span data-ttu-id="d51bb-148">Dit betekent dat voor het **pad** geen parameter naam is vereist, maar de parameter waarde moet de eerste of enige niet-genaamde parameter waarde in de opdracht zijn.</span><span class="sxs-lookup"><span data-stu-id="d51bb-148">This means that **Path** does not require the parameter name, but its parameter value must be the first or only unnamed parameter value in the command.</span></span>
<span data-ttu-id="d51bb-149">Omdat de exclude-para meter echter een benoemde para meter is, kunt u deze op een wille keurige positie in de opdracht plaatsen.</span><span class="sxs-lookup"><span data-stu-id="d51bb-149">However, because the Exclude parameter is a named parameter, you can place it in any position in the command.</span></span>

<span data-ttu-id="d51bb-150">Als gevolg van de `Position` instellingen voor deze twee para meters, kunt u een van de volgende opdrachten gebruiken:</span><span class="sxs-lookup"><span data-stu-id="d51bb-150">As a result of the `Position` settings for these two parameters, you can use any of the following commands:</span></span>

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

<span data-ttu-id="d51bb-151">Als u een andere positionele para meter zou gebruiken zonder de parameter naam op te nemen, moet deze para meter worden geplaatst in de volg orde die is opgegeven door de `Position` instelling.</span><span class="sxs-lookup"><span data-stu-id="d51bb-151">If you were to include another positional parameter without including the parameter name, that parameter must be placed in the order specified by the `Position` setting.</span></span>

#### <a name="parameter-type"></a><span data-ttu-id="d51bb-152">Parameter type</span><span class="sxs-lookup"><span data-stu-id="d51bb-152">Parameter Type</span></span>

<span data-ttu-id="d51bb-153">Met deze instelling geeft u het type Microsoft .NET Framework van de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="d51bb-153">This setting specifies the Microsoft .NET Framework type of the parameter value.</span></span> <span data-ttu-id="d51bb-154">Als het type bijvoorbeeld **Int32** is, moet de waarde van de para meter een geheel getal zijn.</span><span class="sxs-lookup"><span data-stu-id="d51bb-154">For example, if the type is **Int32** , the parameter value must be an integer.</span></span> <span data-ttu-id="d51bb-155">Als het type een teken reeks is, moet de waarde van de para meter een teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="d51bb-155">If the type is string, the parameter value must be a character string.</span></span> <span data-ttu-id="d51bb-156">Als de teken reeks spaties bevat, moet de waarde tussen aanhalings tekens worden geplaatst of moeten de spaties worden voorafgegaan door het escape teken (').</span><span class="sxs-lookup"><span data-stu-id="d51bb-156">If the string contains spaces, the value must be enclosed in quotation marks, or the spaces must be preceded by the escape character ( \` ).</span></span>

#### <a name="default-value"></a><span data-ttu-id="d51bb-157">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="d51bb-157">Default Value</span></span>

<span data-ttu-id="d51bb-158">Met deze instelling geeft u de waarde op die door de para meter wordt aangenomen als er geen andere waarde is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d51bb-158">This setting specifies the value that the parameter will assume if no other value is provided.</span></span> <span data-ttu-id="d51bb-159">Zo is de standaard waarde van de para meter Path vaak de huidige map.</span><span class="sxs-lookup"><span data-stu-id="d51bb-159">For example, the default value of the Path parameter is often the current directory.</span></span> <span data-ttu-id="d51bb-160">De vereiste para meters hebben nooit een standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="d51bb-160">Required parameters never have a default value.</span></span>
<span data-ttu-id="d51bb-161">Voor veel optionele para meters is er geen standaard waarde omdat de para meter geen effect heeft als deze niet wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d51bb-161">For many optional parameters, there is no default because the parameter has no effect if it is not used.</span></span>

#### <a name="accepts-multiple-values"></a><span data-ttu-id="d51bb-162">Accepteert meerdere waarden</span><span class="sxs-lookup"><span data-stu-id="d51bb-162">Accepts Multiple Values</span></span>

<span data-ttu-id="d51bb-163">Met deze instelling geeft u aan of een para meter meerdere parameter waarden accepteert.</span><span class="sxs-lookup"><span data-stu-id="d51bb-163">This setting indicates whether a parameter accepts multiple parameter values.</span></span>
<span data-ttu-id="d51bb-164">Als een para meter meerdere waarden accepteert, kunt u een door komma's gescheiden lijst als waarde van de para meter in de opdracht typen of een door komma's gescheiden lijst (een matrix) in een variabele opslaan en vervolgens de variabele als parameter waarde opgeven.</span><span class="sxs-lookup"><span data-stu-id="d51bb-164">When a parameter accepts multiple values, you can type a comma-separated list as the value of the parameter in the command, or save a comma-separated list (an array) in a variable, and then specify the variable as the parameter value.</span></span>

<span data-ttu-id="d51bb-165">De para meter ServiceName van de `Get-Service` cmdlet accepteert bijvoorbeeld meerdere waarden.</span><span class="sxs-lookup"><span data-stu-id="d51bb-165">For example, the ServiceName parameter of the `Get-Service` cmdlet accepts multiple values.</span></span> <span data-ttu-id="d51bb-166">De volgende opdrachten zijn beide geldig:</span><span class="sxs-lookup"><span data-stu-id="d51bb-166">The following commands are both valid:</span></span>

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a><span data-ttu-id="d51bb-167">Invoer van pijp lijn accepteren</span><span class="sxs-lookup"><span data-stu-id="d51bb-167">Accepts Pipeline Input</span></span>

<span data-ttu-id="d51bb-168">Met deze instelling geeft u aan of u de pijplijn operator ( `|` ) kunt gebruiken om een waarde te verzenden naar de para meter.</span><span class="sxs-lookup"><span data-stu-id="d51bb-168">This setting indicates whether you can use the pipeline operator ( `|` ) to send a value to the parameter.</span></span>

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

<span data-ttu-id="d51bb-169">Als een para meter ' True (per waarde) ' is, probeert Power shell alle sluis waarden met die para meter te koppelen voordat andere methoden proberen de opdracht te interpreteren.</span><span class="sxs-lookup"><span data-stu-id="d51bb-169">When a parameter is "True (by Value)", PowerShell tries to associate any piped values with that parameter before it tries other methods to interpret the command.</span></span>

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

<span data-ttu-id="d51bb-170">U kunt bijvoorbeeld een waarde alleen door sluizen naar een **naam** parameter wanneer de waarde een eigenschap genaamd **name** heeft.</span><span class="sxs-lookup"><span data-stu-id="d51bb-170">For example, you can pipe a value to a **Name** parameter only when the value has a property called **Name**.</span></span>

> [!NOTE]
> <span data-ttu-id="d51bb-171">Een getypeerde para meter die pijplijn invoer ( `by Value` ) of () accepteert, `by PropertyName` maakt het gebruik van script blokken met **vertragings bindingen** mogelijk voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="d51bb-171">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
>
> <span data-ttu-id="d51bb-172">Het script blok voor de **vertragings binding** wordt automatisch uitgevoerd tijdens **ParameterBinding**.</span><span class="sxs-lookup"><span data-stu-id="d51bb-172">The **delay-bind** script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="d51bb-173">Het resultaat is gebonden aan de para meter.</span><span class="sxs-lookup"><span data-stu-id="d51bb-173">The result is bound to the parameter.</span></span> <span data-ttu-id="d51bb-174">De vertraagde binding werkt **niet** voor para meters die zijn gedefinieerd als type `ScriptBlock` of `System.Object` , het script blok wordt door gegeven **zonder** dat dit wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="d51bb-174">Delay binding does **not** work for parameters defined as type `ScriptBlock` or `System.Object`, the script block is passed through **without** being invoked.</span></span>
>
> <span data-ttu-id="d51bb-175">U kunt hier meer lezen over de script blokken **met vertragings bindingen** [about_Script_Blocks. MD](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="d51bb-175">You can read about **delay-bind** script blocks here [about_Script_Blocks.md](about_Script_Blocks.md)</span></span>

#### <a name="accepts-wildcard-characters"></a><span data-ttu-id="d51bb-176">Joker tekens accepteren</span><span class="sxs-lookup"><span data-stu-id="d51bb-176">Accepts Wildcard Characters</span></span>

<span data-ttu-id="d51bb-177">Deze instelling geeft aan of de waarde van de para meter joker tekens kan bevatten zodat de parameter waarde kan worden gekoppeld aan meer dan één bestaand item in de doel container.</span><span class="sxs-lookup"><span data-stu-id="d51bb-177">This setting indicates whether the parameter's value can contain wildcard characters so that the parameter value can be matched to more than one existing item in the target container.</span></span>

#### <a name="common-parameters"></a><span data-ttu-id="d51bb-178">Algemene para meters</span><span class="sxs-lookup"><span data-stu-id="d51bb-178">Common Parameters</span></span>

<span data-ttu-id="d51bb-179">Algemene para meters zijn para meters die u met een wille keurige cmdlet kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d51bb-179">Common parameters are parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="d51bb-180">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie over algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="d51bb-180">For more information about common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d51bb-181">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d51bb-181">See also</span></span>

[<span data-ttu-id="d51bb-182">about_Command_syntax</span><span class="sxs-lookup"><span data-stu-id="d51bb-182">about_Command_syntax</span></span>](about_Command_syntax.md)

[<span data-ttu-id="d51bb-183">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="d51bb-183">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="d51bb-184">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="d51bb-184">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="d51bb-185">about_Parameters_Default_Values</span><span class="sxs-lookup"><span data-stu-id="d51bb-185">about_Parameters_Default_Values</span></span>](about_Parameters_Default_Values.md)

[<span data-ttu-id="d51bb-186">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="d51bb-186">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="d51bb-187">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="d51bb-187">about_Wildcards</span></span>](about_Wildcards.md)
