---
description: Hierin wordt beschreven hoe u kunt werken met opdracht parameters in Power shell.
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: c9d7ab62c13a7cafcf93103f9a70f6575d5dd7b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706230"
---
# <a name="about-parameters"></a><span data-ttu-id="fbe2a-103">Over para meters</span><span class="sxs-lookup"><span data-stu-id="fbe2a-103">About Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="fbe2a-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="fbe2a-104">Short description</span></span>
<span data-ttu-id="fbe2a-105">Hierin wordt beschreven hoe u kunt werken met opdracht parameters in Power shell.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-105">Describes how to work with command parameters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="fbe2a-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="fbe2a-106">Long description</span></span>

<span data-ttu-id="fbe2a-107">De meeste Power shell-opdrachten, zoals cmdlets, functies en scripts, zijn afhankelijk van para meters waarmee gebruikers opties kunnen selecteren of invoer kunnen opgeven.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-107">Most PowerShell commands, such as cmdlets, functions, and scripts, rely on parameters to allow users to select options or provide input.</span></span> <span data-ttu-id="fbe2a-108">De para meters volgen de naam van de opdracht en hebben de volgende vorm:</span><span class="sxs-lookup"><span data-stu-id="fbe2a-108">The parameters follow the command name and have the following form:</span></span>

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

<span data-ttu-id="fbe2a-109">De naam van de para meter wordt voorafgegaan door een koppel teken (-), waarmee wordt gesignaleerd naar Power shell dat het woord na het afbreek streepje een parameter naam is.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-109">The name of the parameter is preceded by a hyphen (-), which signals to PowerShell that the word following the hyphen is a parameter name.</span></span> <span data-ttu-id="fbe2a-110">De naam en waarde van de para meter kunnen worden gescheiden door een spatie of een punt komma.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-110">The parameter name and value can be separated by a space or a colon character.</span></span> <span data-ttu-id="fbe2a-111">Sommige para meters vereisen of accepteren geen parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-111">Some parameters do not require or accept a parameter value.</span></span> <span data-ttu-id="fbe2a-112">Andere para meters hebben een waarde nodig, maar de parameter naam is niet vereist in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-112">Other parameters require a value, but do not require the parameter name in the command.</span></span>

<span data-ttu-id="fbe2a-113">Het type para meters en de vereisten voor die para meters kunnen verschillen.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-113">The type of parameters and the requirements for those parameters vary.</span></span> <span data-ttu-id="fbe2a-114">Als u informatie wilt vinden over de para meters van een opdracht, gebruikt u de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-114">To find information about the parameters of a command, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="fbe2a-115">Als u bijvoorbeeld informatie zoekt over de para meters van de `Get-ChildItem` cmdlet, typt u:</span><span class="sxs-lookup"><span data-stu-id="fbe2a-115">For example, to find information about the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="fbe2a-116">Als u informatie wilt vinden over de para meters van een script, gebruikt u het volledige pad naar het script bestand.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-116">To find information about the parameters of a script, use the full path to the script file.</span></span> <span data-ttu-id="fbe2a-117">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="fbe2a-117">For example:</span></span>

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

<span data-ttu-id="fbe2a-118">De `Get-Help` cmdlet retourneert verschillende details over de opdracht, met inbegrip van een beschrijving, de syntaxis van de opdracht, informatie over de para meters en voor beelden die laten zien hoe u de para meters in een opdracht kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-118">The `Get-Help` cmdlet returns various details about the command, including a description, the command syntax, information about the parameters, and examples showing how to use the parameters in a command.</span></span>

<span data-ttu-id="fbe2a-119">U kunt ook de para meter parameter van de `Get-Help` cmdlet gebruiken om informatie te zoeken over een bepaalde para meter.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-119">You can also use the Parameter parameter of the `Get-Help` cmdlet to find information about a particular parameter.</span></span> <span data-ttu-id="fbe2a-120">Of u kunt de para meter **parameter** met de waarde Joker teken ( `*` ) gebruiken om informatie te zoeken over alle para meters van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-120">Or, you can use the **Parameter** parameter with the wildcard character ( `*` ) value to find information about all parameters of the command.</span></span> <span data-ttu-id="fbe2a-121">Met de volgende opdracht wordt bijvoorbeeld informatie over alle para meters van de `Get-Member` cmdlet opgehaald:</span><span class="sxs-lookup"><span data-stu-id="fbe2a-121">For example, the following command gets information about all parameters of the `Get-Member` cmdlet:</span></span>

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a><span data-ttu-id="fbe2a-122">Standaard parameter waarden</span><span class="sxs-lookup"><span data-stu-id="fbe2a-122">Default parameter values</span></span>

<span data-ttu-id="fbe2a-123">Optionele para meters hebben een standaard waarde. Dit is de waarde die wordt gebruikt of wordt aangenomen wanneer de para meter niet is opgegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-123">Optional parameters have a default value, which is the value that is used or assumed when the parameter is not specified in the command.</span></span>

<span data-ttu-id="fbe2a-124">De standaard waarde van de para meter **ComputerName** van veel cmdlets is bijvoorbeeld de naam van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-124">For example, the default value of the **ComputerName** parameter of many cmdlets is the name of the local computer.</span></span> <span data-ttu-id="fbe2a-125">Als gevolg hiervan wordt de naam van de lokale computer in de opdracht gebruikt, tenzij u de para meter **ComputerName** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-125">As a result, the local computer name is used in the command unless the **ComputerName** parameter is specified.</span></span>

<span data-ttu-id="fbe2a-126">Zie het Help-onderwerp voor de cmdlet om de standaard parameter waarde te vinden.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-126">To find the default parameter value, see help topic for the cmdlet.</span></span> <span data-ttu-id="fbe2a-127">De parameter beschrijving moet de standaard waarde bevatten.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-127">The parameter description should include the default value.</span></span>

<span data-ttu-id="fbe2a-128">U kunt ook een aangepaste standaard waarde instellen voor elke para meter van een cmdlet of een geavanceerde functie.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-128">You can also set a custom default value for any parameter of a cmdlet or advanced function.</span></span> <span data-ttu-id="fbe2a-129">Zie [about_Parameters_Default_Values](about_Parameters_Default_Values.md)voor meer informatie over het instellen van aangepaste standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-129">For information about setting custom default values, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="fbe2a-130">Parameter kenmerk tabel</span><span class="sxs-lookup"><span data-stu-id="fbe2a-130">Parameter attribute table</span></span>

<span data-ttu-id="fbe2a-131">Wanneer u de para meters **Full**, **para meter** of **online** van de `Get-Help` cmdlet gebruikt, `Get-Help` wordt een tabel met parameter kenmerken weer gegeven met gedetailleerde informatie over de para meter.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-131">When you use the **Full**, **Parameter**, or **Online** parameters of the `Get-Help` cmdlet, `Get-Help` displays a parameter attribute table with detailed information about the parameter.</span></span>

<span data-ttu-id="fbe2a-132">Deze informatie bevat de details die u moet kennen om de para meter te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-132">This information includes the details you need to know to use the parameter.</span></span>
<span data-ttu-id="fbe2a-133">Het Help-onderwerp voor de `Get-ChildItem` cmdlet bevat bijvoorbeeld de volgende gegevens over de para meter Path:</span><span class="sxs-lookup"><span data-stu-id="fbe2a-133">For example, the help topic for the `Get-ChildItem` cmdlet includes the following details about its Path parameter:</span></span>

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

<span data-ttu-id="fbe2a-134">De parameter informatie bevat de syntaxis van de para meter, een beschrijving van de para meter en de parameter kenmerken.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-134">The parameter information includes the parameter syntax, a description of the parameter, and the parameter attributes.</span></span> <span data-ttu-id="fbe2a-135">In de volgende secties worden de parameter kenmerken beschreven.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-135">The following sections describe the parameter attributes.</span></span>

#### <a name="parameter-required"></a><span data-ttu-id="fbe2a-136">Para meter vereist</span><span class="sxs-lookup"><span data-stu-id="fbe2a-136">Parameter Required</span></span>

<span data-ttu-id="fbe2a-137">Met deze instelling geeft u aan of de para meter verplicht is, dat wil zeggen of alle opdrachten die gebruikmaken van deze cmdlet deze para meter moeten bevatten.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-137">This setting indicates whether the parameter is mandatory, that is, whether all commands that use this cmdlet must include this parameter.</span></span> <span data-ttu-id="fbe2a-138">Als de waarde **True** is en de para meter in de opdracht ontbreekt, vraagt Power shell u om een waarde voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-138">When the value is **True** and the parameter is missing from the command, PowerShell prompts you for a value for the parameter.</span></span>

#### <a name="parameter-position"></a><span data-ttu-id="fbe2a-139">Parameter positie</span><span class="sxs-lookup"><span data-stu-id="fbe2a-139">Parameter Position</span></span>

<span data-ttu-id="fbe2a-140">Als de `Position` instelling is ingesteld op een positief geheel getal, is de parameter naam niet vereist.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-140">If the `Position` setting is set to a positive integer, the parameter name is not required.</span></span> <span data-ttu-id="fbe2a-141">Dit type para meter wordt aangeduid als positionele para meter en het nummer geeft de positie aan waarin de para meter moet worden weer gegeven in verhouding tot andere positie parameters.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-141">This type of parameter is referred to as a positional parameter, and the number indicates the position in which the parameter must appear in relation to other positional parameters.</span></span> <span data-ttu-id="fbe2a-142">Een benoemde para meter kan worden weer gegeven op elke positie na de naam van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-142">A named parameter can be listed in any position after the cmdlet name.</span></span> <span data-ttu-id="fbe2a-143">Als u de parameter naam voor een positionele para meter toevoegt, kan de para meter op elke positie na de naam van de cmdlet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-143">If you include the parameter name for a positional parameter, the parameter can be listed in any position after the cmdlet name.</span></span>

<span data-ttu-id="fbe2a-144">De `Get-ChildItem` cmdlet heeft bijvoorbeeld Path-en exclude-para meters.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-144">For example, the `Get-ChildItem` cmdlet has Path and Exclude parameters.</span></span> <span data-ttu-id="fbe2a-145">De `Position` instelling voor het **pad** is **0**, wat betekent dat het een positionele para meter is.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-145">The `Position` setting for **Path** is **0**, which means that it is a positional parameter.</span></span> <span data-ttu-id="fbe2a-146">De `Position` instelling voor **uitsluiten** heet .</span><span class="sxs-lookup"><span data-stu-id="fbe2a-146">The `Position` setting for **Exclude** is **named**.</span></span>

<span data-ttu-id="fbe2a-147">Dit betekent dat voor het **pad** geen parameter naam is vereist, maar de parameter waarde moet de eerste of enige niet-genaamde parameter waarde in de opdracht zijn.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-147">This means that **Path** does not require the parameter name, but its parameter value must be the first or only unnamed parameter value in the command.</span></span>
<span data-ttu-id="fbe2a-148">Omdat de exclude-para meter echter een benoemde para meter is, kunt u deze op een wille keurige positie in de opdracht plaatsen.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-148">However, because the Exclude parameter is a named parameter, you can place it in any position in the command.</span></span>

<span data-ttu-id="fbe2a-149">Als gevolg van de `Position` instellingen voor deze twee para meters, kunt u een van de volgende opdrachten gebruiken:</span><span class="sxs-lookup"><span data-stu-id="fbe2a-149">As a result of the `Position` settings for these two parameters, you can use any of the following commands:</span></span>

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

<span data-ttu-id="fbe2a-150">Als u een andere positionele para meter zou gebruiken zonder de parameter naam op te nemen, moet deze para meter worden geplaatst in de volg orde die is opgegeven door de `Position` instelling.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-150">If you were to include another positional parameter without including the parameter name, that parameter must be placed in the order specified by the `Position` setting.</span></span>

#### <a name="parameter-type"></a><span data-ttu-id="fbe2a-151">Parameter type</span><span class="sxs-lookup"><span data-stu-id="fbe2a-151">Parameter Type</span></span>

<span data-ttu-id="fbe2a-152">Met deze instelling geeft u het type Microsoft .NET Framework van de parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-152">This setting specifies the Microsoft .NET Framework type of the parameter value.</span></span> <span data-ttu-id="fbe2a-153">Als het type bijvoorbeeld **Int32** is, moet de waarde van de para meter een geheel getal zijn.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-153">For example, if the type is **Int32**, the parameter value must be an integer.</span></span> <span data-ttu-id="fbe2a-154">Als het type een teken reeks is, moet de waarde van de para meter een teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-154">If the type is string, the parameter value must be a character string.</span></span> <span data-ttu-id="fbe2a-155">Als de teken reeks spaties bevat, moet de waarde tussen aanhalings tekens worden geplaatst of moeten de spaties worden voorafgegaan door het escape teken (').</span><span class="sxs-lookup"><span data-stu-id="fbe2a-155">If the string contains spaces, the value must be enclosed in quotation marks, or the spaces must be preceded by the escape character ( \` ).</span></span>

#### <a name="default-value"></a><span data-ttu-id="fbe2a-156">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="fbe2a-156">Default Value</span></span>

<span data-ttu-id="fbe2a-157">Met deze instelling geeft u de waarde op die door de para meter wordt aangenomen als er geen andere waarde is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-157">This setting specifies the value that the parameter will assume if no other value is provided.</span></span> <span data-ttu-id="fbe2a-158">Zo is de standaard waarde van de para meter Path vaak de huidige map.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-158">For example, the default value of the Path parameter is often the current directory.</span></span> <span data-ttu-id="fbe2a-159">De vereiste para meters hebben nooit een standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-159">Required parameters never have a default value.</span></span>
<span data-ttu-id="fbe2a-160">Voor veel optionele para meters is er geen standaard waarde omdat de para meter geen effect heeft als deze niet wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-160">For many optional parameters, there is no default because the parameter has no effect if it is not used.</span></span>

#### <a name="accepts-multiple-values"></a><span data-ttu-id="fbe2a-161">Accepteert meerdere waarden</span><span class="sxs-lookup"><span data-stu-id="fbe2a-161">Accepts Multiple Values</span></span>

<span data-ttu-id="fbe2a-162">Met deze instelling geeft u aan of een para meter meerdere parameter waarden accepteert.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-162">This setting indicates whether a parameter accepts multiple parameter values.</span></span>
<span data-ttu-id="fbe2a-163">Als een para meter meerdere waarden accepteert, kunt u een door komma's gescheiden lijst als waarde van de para meter in de opdracht typen of een door komma's gescheiden lijst (een matrix) in een variabele opslaan en vervolgens de variabele als parameter waarde opgeven.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-163">When a parameter accepts multiple values, you can type a comma-separated list as the value of the parameter in the command, or save a comma-separated list (an array) in a variable, and then specify the variable as the parameter value.</span></span>

<span data-ttu-id="fbe2a-164">De para meter ServiceName van de `Get-Service` cmdlet accepteert bijvoorbeeld meerdere waarden.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-164">For example, the ServiceName parameter of the `Get-Service` cmdlet accepts multiple values.</span></span> <span data-ttu-id="fbe2a-165">De volgende opdrachten zijn beide geldig:</span><span class="sxs-lookup"><span data-stu-id="fbe2a-165">The following commands are both valid:</span></span>

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a><span data-ttu-id="fbe2a-166">Invoer van pijp lijn accepteren</span><span class="sxs-lookup"><span data-stu-id="fbe2a-166">Accepts Pipeline Input</span></span>

<span data-ttu-id="fbe2a-167">Met deze instelling geeft u aan of u de pijplijn operator ( `|` ) kunt gebruiken om een waarde te verzenden naar de para meter.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-167">This setting indicates whether you can use the pipeline operator ( `|` ) to send a value to the parameter.</span></span>

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

<span data-ttu-id="fbe2a-168">Als een para meter ' True (per waarde) ' is, probeert Power shell alle sluis waarden met die para meter te koppelen voordat andere methoden proberen de opdracht te interpreteren.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-168">When a parameter is "True (by Value)", PowerShell tries to associate any piped values with that parameter before it tries other methods to interpret the command.</span></span>

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

<span data-ttu-id="fbe2a-169">U kunt bijvoorbeeld een waarde alleen door sluizen naar een **naam** parameter wanneer de waarde een eigenschap genaamd **name** heeft.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-169">For example, you can pipe a value to a **Name** parameter only when the value has a property called **Name**.</span></span>

> [!NOTE]
> <span data-ttu-id="fbe2a-170">Een getypeerde para meter die pijplijn invoer ( `by Value` ) of () accepteert, `by PropertyName` maakt het gebruik van script blokken met **vertragings bindingen** mogelijk voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-170">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
>
> <span data-ttu-id="fbe2a-171">Het script blok voor de **vertragings binding** wordt automatisch uitgevoerd tijdens **ParameterBinding**.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-171">The **delay-bind** script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="fbe2a-172">Het resultaat is gebonden aan de para meter.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-172">The result is bound to the parameter.</span></span> <span data-ttu-id="fbe2a-173">De vertraagde binding werkt **niet** voor para meters die zijn gedefinieerd als type `ScriptBlock` of `System.Object` , het script blok wordt door gegeven **zonder** dat dit wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-173">Delay binding does **not** work for parameters defined as type `ScriptBlock` or `System.Object`, the script block is passed through **without** being invoked.</span></span>
>
> <span data-ttu-id="fbe2a-174">U kunt hier meer lezen over de script blokken **met vertragings bindingen** [about_Script_Blocks. MD](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="fbe2a-174">You can read about **delay-bind** script blocks here [about_Script_Blocks.md](about_Script_Blocks.md)</span></span>

#### <a name="accepts-wildcard-characters"></a><span data-ttu-id="fbe2a-175">Joker tekens accepteren</span><span class="sxs-lookup"><span data-stu-id="fbe2a-175">Accepts Wildcard Characters</span></span>

<span data-ttu-id="fbe2a-176">Deze instelling geeft aan of de waarde van de para meter joker tekens kan bevatten zodat de parameter waarde kan worden gekoppeld aan meer dan één bestaand item in de doel container.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-176">This setting indicates whether the parameter's value can contain wildcard characters so that the parameter value can be matched to more than one existing item in the target container.</span></span>

#### <a name="common-parameters"></a><span data-ttu-id="fbe2a-177">Algemene para meters</span><span class="sxs-lookup"><span data-stu-id="fbe2a-177">Common Parameters</span></span>

<span data-ttu-id="fbe2a-178">Algemene para meters zijn para meters die u met een wille keurige cmdlet kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-178">Common parameters are parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="fbe2a-179">Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie over algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="fbe2a-179">For more information about common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbe2a-180">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fbe2a-180">See also</span></span>

[<span data-ttu-id="fbe2a-181">about_Command_syntax</span><span class="sxs-lookup"><span data-stu-id="fbe2a-181">about_Command_syntax</span></span>](about_Command_syntax.md)

[<span data-ttu-id="fbe2a-182">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="fbe2a-182">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="fbe2a-183">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="fbe2a-183">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="fbe2a-184">about_Parameters_Default_Values</span><span class="sxs-lookup"><span data-stu-id="fbe2a-184">about_Parameters_Default_Values</span></span>](about_Parameters_Default_Values.md)

[<span data-ttu-id="fbe2a-185">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="fbe2a-185">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="fbe2a-186">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="fbe2a-186">about_Wildcards</span></span>](about_Wildcards.md)

