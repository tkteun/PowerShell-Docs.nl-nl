---
description: Hierin worden de syntaxis diagrammen beschreven die worden gebruikt in Power shell.
keywords: powershell,cmdlet
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: 33692eebab41e20bd85eb447cc66f1ff592977ef
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252370"
---
# <a name="about-command-syntax"></a><span data-ttu-id="0a665-104">Over opdracht syntaxis</span><span class="sxs-lookup"><span data-stu-id="0a665-104">About Command Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="0a665-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0a665-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="0a665-106">Hierin worden de syntaxis diagrammen beschreven die worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0a665-106">Describes the syntax diagrams that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0a665-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0a665-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="0a665-108">Met de cmdlets [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) en [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) worden syntaxis diagrammen weer gegeven om u te helpen opdrachten op de juiste manier te bouwen.</span><span class="sxs-lookup"><span data-stu-id="0a665-108">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlets display syntax diagrams to help you construct commands correctly.</span></span> <span data-ttu-id="0a665-109">In dit onderwerp wordt uitgelegd hoe u de syntaxis diagrammen kunt interpreteren.</span><span class="sxs-lookup"><span data-stu-id="0a665-109">This topic explains how to interpret the syntax diagrams.</span></span>

## <a name="syntax-diagrams"></a><span data-ttu-id="0a665-110">SYNTAXIS DIAGRAMMEN</span><span class="sxs-lookup"><span data-stu-id="0a665-110">SYNTAX DIAGRAMS</span></span>

<span data-ttu-id="0a665-111">Elke alinea in een opdracht syntaxis diagram vertegenwoordigt een geldige vorm van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0a665-111">Each paragraph in a command syntax diagram represents a valid form of the command.</span></span>

<span data-ttu-id="0a665-112">Als u een opdracht wilt maken, volgt u het syntaxis diagram van links naar rechts.</span><span class="sxs-lookup"><span data-stu-id="0a665-112">To construct a command, follow the syntax diagram from left to right.</span></span> <span data-ttu-id="0a665-113">Selecteer een van de optionele para meters en geef waarden op voor de tijdelijke aanduidingen.</span><span class="sxs-lookup"><span data-stu-id="0a665-113">Select from among the optional parameters and provide values for the placeholders.</span></span>

<span data-ttu-id="0a665-114">Power shell gebruikt de volgende notatie voor syntaxis diagrammen.</span><span class="sxs-lookup"><span data-stu-id="0a665-114">PowerShell uses the following notation for syntax diagrams.</span></span>

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

<span data-ttu-id="0a665-115">Hier volgt de syntaxis van de cmdlet [New-alias](xref:Microsoft.PowerShell.Utility.New-Alias) .</span><span class="sxs-lookup"><span data-stu-id="0a665-115">The following is the syntax for the [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet.</span></span>

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="0a665-116">De syntaxis is in grote zin voor lees baarheid, maar Power shell is niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="0a665-116">The syntax is capitalized for readability, but PowerShell is case-insensitive.</span></span>

<span data-ttu-id="0a665-117">Het syntaxis diagram bevat de volgende elementen.</span><span class="sxs-lookup"><span data-stu-id="0a665-117">The syntax diagram has the following elements.</span></span>

## <a name="command-name"></a><span data-ttu-id="0a665-118">Opdracht naam</span><span class="sxs-lookup"><span data-stu-id="0a665-118">Command name</span></span>

<span data-ttu-id="0a665-119">Opdrachten beginnen altijd met een opdracht naam, zoals `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="0a665-119">Commands always begin with a command name, such as `New-Alias`.</span></span> <span data-ttu-id="0a665-120">Typ de naam van de opdracht of de alias, bijvoorbeeld ' GCM ' voor `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="0a665-120">Type the command name or its alias, such a "gcm" for `Get-Command`.</span></span>

## <a name="parameters"></a><span data-ttu-id="0a665-121">Parameters</span><span class="sxs-lookup"><span data-stu-id="0a665-121">Parameters</span></span>

<span data-ttu-id="0a665-122">De para meters van een opdracht zijn opties die bepalen wat de opdracht doet.</span><span class="sxs-lookup"><span data-stu-id="0a665-122">The parameters of a command are options that determine what the command does.</span></span>
<span data-ttu-id="0a665-123">Sommige para meters hebben een ' waarde ' die gebruikers invoer heeft naar de opdracht.</span><span class="sxs-lookup"><span data-stu-id="0a665-123">Some parameters take a "value" which is user input to the command.</span></span>

<span data-ttu-id="0a665-124">De `Get-Help` opdracht heeft bijvoorbeeld een para meter **name** waarmee u de naam van het onderwerp kunt opgeven waarvoor Help wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0a665-124">For example, the `Get-Help` command has a **Name** parameter that lets you specify the name of the topic for which help is displayed.</span></span> <span data-ttu-id="0a665-125">De naam van het onderwerp is de waarde van de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="0a665-125">The topic name is the value of the **Name** parameter.</span></span>

<span data-ttu-id="0a665-126">In een Power shell-opdracht beginnen parameter namen altijd met een koppel teken.</span><span class="sxs-lookup"><span data-stu-id="0a665-126">In a PowerShell command, parameter names always begin with a hyphen.</span></span>
<span data-ttu-id="0a665-127">Het afbreek streepje vertelt Power shell dat het item in de opdracht een parameter naam is.</span><span class="sxs-lookup"><span data-stu-id="0a665-127">The hyphen tells PowerShell that the item in the command is a parameter name.</span></span>

<span data-ttu-id="0a665-128">Als u bijvoorbeeld de para meter name van wilt gebruiken `New-Alias` , typt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="0a665-128">For example, to use the Name parameter of `New-Alias`, you type the following:</span></span>

```powershell
-Name
```

<span data-ttu-id="0a665-129">Para meters kunnen verplicht of optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="0a665-129">Parameters can be mandatory or optional.</span></span> <span data-ttu-id="0a665-130">In een syntaxis diagram bevinden optionele items zich tussen vier Kante haken `[ ]` .</span><span class="sxs-lookup"><span data-stu-id="0a665-130">In a syntax diagram, optional items are enclosed in brackets `[ ]`.</span></span>

<span data-ttu-id="0a665-131">Zie [about_Parameters](about_Parameters.md)voor meer informatie over para meters.</span><span class="sxs-lookup"><span data-stu-id="0a665-131">For more information about parameters, see [about_Parameters](about_Parameters.md).</span></span>

## <a name="parameter-values"></a><span data-ttu-id="0a665-132">Parameterwaarden</span><span class="sxs-lookup"><span data-stu-id="0a665-132">Parameter Values</span></span>

<span data-ttu-id="0a665-133">Een parameter waarde is de invoer die door de para meter wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0a665-133">A parameter value is the input that the parameter takes.</span></span> <span data-ttu-id="0a665-134">Omdat Windows Power shell is gebaseerd op het Microsoft .NET Framework, worden parameter waarden weer gegeven in het syntaxis diagram op basis van hun .NET-type.</span><span class="sxs-lookup"><span data-stu-id="0a665-134">Because Windows PowerShell is based on the Microsoft .NET Framework, parameter values are represented in the syntax diagram by their .NET type.</span></span>

<span data-ttu-id="0a665-135">De para meter name van neemt bijvoorbeeld een `Get-Help` teken reeks waarde, een teken reeks, zoals een enkel woord of meerdere woorden tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="0a665-135">For example, the Name parameter of `Get-Help` takes a "String" value, which is a text string, such as a single word or multiple words enclosed in quotation marks.</span></span>

```powershell
[-Name] <string>
```

<span data-ttu-id="0a665-136">Het .NET-type van een parameter waarde bevindt zich tussen punt haken `< >` om aan te geven dat het een tijdelijke aanduiding voor een waarde is en niet een letterlijke teken reeks die u in een opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="0a665-136">The .NET type of a parameter value is enclosed in angle brackets `< >` to indicate that it is placeholder for a value and not a literal that you type in a command.</span></span>

<span data-ttu-id="0a665-137">Als u de para meter wilt gebruiken, vervangt u de tijdelijke aanduiding .NET-type door een object dat het opgegeven .NET-type heeft.</span><span class="sxs-lookup"><span data-stu-id="0a665-137">To use the parameter, replace the .NET type placeholder with an object that has the specified .NET type.</span></span>

<span data-ttu-id="0a665-138">Als u bijvoorbeeld de para meter **name** wilt gebruiken, typt u '-name ', gevolgd door een teken reeks, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="0a665-138">For example, to use the **Name** parameter, type "-Name" followed by a string, such as the following:</span></span>

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a><span data-ttu-id="0a665-139">Para meters zonder waarden</span><span class="sxs-lookup"><span data-stu-id="0a665-139">Parameters with no values</span></span>

<span data-ttu-id="0a665-140">Sommige para meters accepteren geen invoer, dus ze hebben geen parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="0a665-140">Some parameters do not accept input, so they do not have a parameter value.</span></span>
<span data-ttu-id="0a665-141">Para meters zonder waarden worden "switch parameters" genoemd, omdat ze werken als aan/uit-switches.</span><span class="sxs-lookup"><span data-stu-id="0a665-141">Parameters without values are called "switch parameters" because they work like on/off switches.</span></span> <span data-ttu-id="0a665-142">U neemt ze op (aan) of u kunt deze weglaten (uit) van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="0a665-142">You include them (on) or you omit them (off) from a command.</span></span>

<span data-ttu-id="0a665-143">Als u een para meter switch wilt gebruiken, typt u de parameter naam, voorafgegaan door een koppel teken.</span><span class="sxs-lookup"><span data-stu-id="0a665-143">To use a switch parameter, just type the parameter name, preceded by a hyphen.</span></span>

<span data-ttu-id="0a665-144">Als u bijvoorbeeld de para meter **WhatIf** van de cmdlet wilt gebruiken `New-Alias` , typt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="0a665-144">For example, to use the **WhatIf** parameter of the `New-Alias` cmdlet, type the following:</span></span>

```powershell
-WhatIf
```

## <a name="parameter-sets"></a><span data-ttu-id="0a665-145">Parametersets</span><span class="sxs-lookup"><span data-stu-id="0a665-145">Parameter Sets</span></span>

<span data-ttu-id="0a665-146">De para meters van een opdracht worden weer gegeven in de parameter sets.</span><span class="sxs-lookup"><span data-stu-id="0a665-146">The parameters of a command are listed in parameter sets.</span></span> <span data-ttu-id="0a665-147">Parameter sets zien eruit als de alinea's van een syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="0a665-147">Parameter sets look like the paragraphs of a syntax diagram.</span></span>

<span data-ttu-id="0a665-148">De `New-Alias` cmdlet heeft één set para meters, maar veel cmdlets hebben meerdere parametersets.</span><span class="sxs-lookup"><span data-stu-id="0a665-148">The `New-Alias` cmdlet has one parameter set, but many cmdlets have multiple parameter sets.</span></span> <span data-ttu-id="0a665-149">Sommige cmdlet-para meters zijn uniek voor een parameterset en andere worden weer gegeven in meerdere parameter sets.</span><span class="sxs-lookup"><span data-stu-id="0a665-149">Some of the cmdlet parameters are unique to a parameter set, and others appear in multiple parameter sets.</span></span> <span data-ttu-id="0a665-150">Elke parameterset vertegenwoordigt de indeling van een geldige opdracht.</span><span class="sxs-lookup"><span data-stu-id="0a665-150">Each parameter set represents the format of a valid command.</span></span> <span data-ttu-id="0a665-151">Een parameterset bevat alleen para meters die samen in een opdracht kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0a665-151">A parameter set includes only parameters that can be used together in a command.</span></span> <span data-ttu-id="0a665-152">Als para meters niet kunnen worden gebruikt in dezelfde opdracht, worden ze weer gegeven in afzonderlijke parameter sets.</span><span class="sxs-lookup"><span data-stu-id="0a665-152">If parameters cannot be used in the same command, they appear in separate parameter sets.</span></span>

<span data-ttu-id="0a665-153">De [Get-wille](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet heeft bijvoorbeeld de volgende parameter sets:</span><span class="sxs-lookup"><span data-stu-id="0a665-153">For example, the [Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet has the following parameter sets:</span></span>

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

<span data-ttu-id="0a665-154">De eerste parameterset, die een wille keurig getal retourneert, heeft de **minimum** -en **maximum** waarden.</span><span class="sxs-lookup"><span data-stu-id="0a665-154">The first parameter set, which returns a random number, has the **Minimum** and **Maximum** parameters.</span></span> <span data-ttu-id="0a665-155">De tweede parameterset, die een wille keurig geselecteerd object uit een set objecten retourneert, omvat de para meters **input object** en **Count** .</span><span class="sxs-lookup"><span data-stu-id="0a665-155">The second parameter set, which returns a randomly selected object from a set of objects, includes the **InputObject** and **Count** parameters.</span></span> <span data-ttu-id="0a665-156">Beide parameter sets hebben de para meter **SetSeed** en de algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="0a665-156">Both parameter sets have the **SetSeed** parameter and the common parameters.</span></span>

<span data-ttu-id="0a665-157">Deze parameter sets geven aan dat u de para meters **input object** en **Count** kunt gebruiken in dezelfde opdracht, maar u kunt de para meters voor **maximum** en **aantal** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="0a665-157">These parameter sets indicate that you can use the **InputObject** and **Count** parameters in the same command, but you cannot use the **Maximum** and **Count** parameters in the same command.</span></span>

<span data-ttu-id="0a665-158">U geeft aan welke para meter die u wilt gebruiken met behulp van de para meters in die para meter zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="0a665-158">You indicate which parameter set you want to use by using the parameters in that parameter set.</span></span>

<span data-ttu-id="0a665-159">Voor elke cmdlet is echter ook een standaard parameterset ingesteld.</span><span class="sxs-lookup"><span data-stu-id="0a665-159">However, every cmdlet also has a default parameter set.</span></span> <span data-ttu-id="0a665-160">De standaard parameterset wordt gebruikt wanneer u geen para meters opgeeft die uniek zijn voor een parameterset.</span><span class="sxs-lookup"><span data-stu-id="0a665-160">The default parameter set is used when you do not specify parameters that are unique to a parameter set.</span></span> <span data-ttu-id="0a665-161">Als u bijvoorbeeld `Get-Random` zonder para meters gebruikt, veronderstelt Windows Power shell dat u de para **Number** meter set gebruikt en retourneert deze een wille keurig getal.</span><span class="sxs-lookup"><span data-stu-id="0a665-161">For example, if you use `Get-Random` without parameters, Windows PowerShell assumes that you are using the **Number** parameter set and it returns a random number.</span></span>

<span data-ttu-id="0a665-162">In elke parameterset worden de para meters in positie volgorde weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0a665-162">In each parameter set, the parameters appear in position order.</span></span> <span data-ttu-id="0a665-163">De volg orde van de para meters in een opdracht is alleen van belang wanneer u de optionele parameter namen weglaat.</span><span class="sxs-lookup"><span data-stu-id="0a665-163">The order of parameters in a command matters only when you omit the optional parameter names.</span></span> <span data-ttu-id="0a665-164">Wanneer parameter namen worden wegge laten, wijst Power shell waarden toe aan para meters op positie en type.</span><span class="sxs-lookup"><span data-stu-id="0a665-164">When parameter names are omitted, PowerShell assigns values to parameters by position and type.</span></span> <span data-ttu-id="0a665-165">Zie voor meer informatie over de positie van de para meter `about_Parameters` .</span><span class="sxs-lookup"><span data-stu-id="0a665-165">For more information about parameter position, see `about_Parameters`.</span></span>

## <a name="symbols-in-syntax-diagrams"></a><span data-ttu-id="0a665-166">Symbolen in syntaxis diagrammen</span><span class="sxs-lookup"><span data-stu-id="0a665-166">Symbols in Syntax Diagrams</span></span>

<span data-ttu-id="0a665-167">Het syntaxis diagram bevat een lijst met de naam van de opdracht, de opdracht parameters en de parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="0a665-167">The syntax diagram lists the command name, the command parameters, and the parameter values.</span></span> <span data-ttu-id="0a665-168">Er worden ook symbolen gebruikt om te laten zien hoe u een geldige opdracht kunt maken.</span><span class="sxs-lookup"><span data-stu-id="0a665-168">It also uses symbols to show how to construct a valid command.</span></span>

<span data-ttu-id="0a665-169">De syntaxis diagrammen gebruiken de volgende symbolen:</span><span class="sxs-lookup"><span data-stu-id="0a665-169">The syntax diagrams use the following symbols:</span></span>

- <span data-ttu-id="0a665-170">Een koppel teken `-` geeft de naam van een para meter aan.</span><span class="sxs-lookup"><span data-stu-id="0a665-170">A hyphen `-` indicates a parameter name.</span></span> <span data-ttu-id="0a665-171">Typ in een opdracht het afbreek streepje direct vóór de parameter naam zonder tussenliggende spaties, zoals wordt weer gegeven in het syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="0a665-171">In a command, type the hyphen immediately before the parameter name with no intervening spaces, as shown in the syntax diagram.</span></span>

  <span data-ttu-id="0a665-172">Als u bijvoorbeeld de para meter **name** van wilt gebruiken `New-Alias` , typt u:</span><span class="sxs-lookup"><span data-stu-id="0a665-172">For example, to use the **Name** parameter of `New-Alias`, type:</span></span>

  ```powershell
  -Name
  ```

- <span data-ttu-id="0a665-173">Met punt haken wordt de `<>` tijdelijke aanduiding voor tekst aangeduid.</span><span class="sxs-lookup"><span data-stu-id="0a665-173">Angle brackets `<>` indicate placeholder text.</span></span> <span data-ttu-id="0a665-174">U typt geen punt haken of de tekst van de tijdelijke aanduiding in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="0a665-174">You do not type the angle brackets or the placeholder text in a command.</span></span> <span data-ttu-id="0a665-175">In plaats daarvan vervangt u deze door het item dat hierin wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="0a665-175">Instead, you replace it with the item that it describes.</span></span>

  <span data-ttu-id="0a665-176">Punt haken worden gebruikt voor het identificeren van het .NET-type van de waarde die een para meter gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0a665-176">Angle brackets are used to identify the .NET type of the value that a parameter takes.</span></span> <span data-ttu-id="0a665-177">Als u bijvoorbeeld de para meter **name** van de cmdlet wilt gebruiken `New-Alias` , vervangt u de `<string>` door een teken reeks, een enkel woord of een groep woorden die tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="0a665-177">For example, to use the **Name** parameter of the `New-Alias` cmdlet, you replace the `<string>` with a string, which is a single word or a group of words that are enclosed in quotation marks.</span></span>

- <span data-ttu-id="0a665-178">Optionele items worden aangegeven door accolades `[ ]` .</span><span class="sxs-lookup"><span data-stu-id="0a665-178">Brackets `[ ]` indicate optional items.</span></span> <span data-ttu-id="0a665-179">Een para meter en de waarde ervan kunnen optioneel zijn, of de naam van een vereiste para meter kan optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="0a665-179">A parameter and its value can be optional, or the name of a required parameter can be optional.</span></span>

  <span data-ttu-id="0a665-180">De para meter **Description** van `New-Alias` en de waarde ervan bevindt zich bijvoorbeeld tussen vier Kante haken, omdat deze beide optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="0a665-180">For example, the **Description** parameter of `New-Alias` and its value are enclosed in brackets because they are both optional.</span></span>

  ```powershell
  [-Description <string>]
  ```

  <span data-ttu-id="0a665-181">De haakjes geven ook aan dat de waarde van de para meter name `<string>` vereist is, maar de parameter naam ' naam ' is optioneel.</span><span class="sxs-lookup"><span data-stu-id="0a665-181">The brackets also indicate that the Name parameter value `<string>` is required, but the parameter name, "Name", is optional.</span></span>

  ```powershell
  [-Name] <string>
  ```

- <span data-ttu-id="0a665-182">Een recht en haakje links `[]` toegevoegd aan een .net-type geeft aan dat de para meter een of meer waarden van dat type kan accepteren.</span><span class="sxs-lookup"><span data-stu-id="0a665-182">A right and left bracket `[]` appended to a .NET type indicates that the parameter can accept one or multiple values of that type.</span></span> <span data-ttu-id="0a665-183">Voer de waarden in een door komma's gescheiden lijst in.</span><span class="sxs-lookup"><span data-stu-id="0a665-183">Enter the values in a comma-separated list.</span></span>

  <span data-ttu-id="0a665-184">De para meter **name** van de `New-Alias` cmdlet gebruikt bijvoorbeeld slechts één teken reeks, maar de para meter **name** van [Get-process](xref:Microsoft.PowerShell.Management.Get-Process) kan een of meer teken reeksen aannemen.</span><span class="sxs-lookup"><span data-stu-id="0a665-184">For example, the **Name** parameter of the `New-Alias` cmdlet takes only one string, but the **Name** parameter of [Get-Process](xref:Microsoft.PowerShell.Management.Get-Process) can take one or many strings.</span></span>

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- <span data-ttu-id="0a665-185">Accolades `{}` geven een ' opsomming ' aan. Dit is een set geldige waarden voor een para meter.</span><span class="sxs-lookup"><span data-stu-id="0a665-185">Braces `{}` indicate an "enumeration," which is a set of valid values for a parameter.</span></span>

  <span data-ttu-id="0a665-186">De waarden in de accolades worden gescheiden door verticale balken `|` .</span><span class="sxs-lookup"><span data-stu-id="0a665-186">The values in the braces are separated by vertical bars `|`.</span></span> <span data-ttu-id="0a665-187">Deze balken geven een ' exclusieve of ' keuze aan, wat betekent dat u slechts één waarde kunt kiezen uit de set waarden die worden weer gegeven binnen de accolades.</span><span class="sxs-lookup"><span data-stu-id="0a665-187">These bars indicate an "exclusive OR" choice, meaning that you can choose only one value from the set of values that are listed inside the braces.</span></span>

  <span data-ttu-id="0a665-188">De syntaxis voor de `New-Alias` cmdlet bevat bijvoorbeeld de volgende waarde-inventarisatie voor de para meter **Option** :</span><span class="sxs-lookup"><span data-stu-id="0a665-188">For example, the syntax for the `New-Alias` cmdlet includes the following value enumeration for the **Option** parameter:</span></span>

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  <span data-ttu-id="0a665-189">De accolades en verticale balken geven aan dat u een van de vermelde waarden voor de para meter **Option** kunt kiezen, zoals "readonly" of "AllScope".</span><span class="sxs-lookup"><span data-stu-id="0a665-189">The braces and vertical bars indicate that you can choose any one of the listed values for the **Option** parameter, such as "ReadOnly" or "AllScope".</span></span>

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a><span data-ttu-id="0a665-190">Optionele items</span><span class="sxs-lookup"><span data-stu-id="0a665-190">Optional Items</span></span>

<span data-ttu-id="0a665-191">Vier Kante haken `[]` rond optionele items.</span><span class="sxs-lookup"><span data-stu-id="0a665-191">Brackets `[]` surround optional items.</span></span> <span data-ttu-id="0a665-192">In de beschrijving van de `New-Alias` syntaxis van de cmdlet is de **bereik** parameter bijvoorbeeld optioneel.</span><span class="sxs-lookup"><span data-stu-id="0a665-192">For example, in the `New-Alias` cmdlet syntax description, the **Scope** parameter is optional.</span></span> <span data-ttu-id="0a665-193">Dit wordt aangegeven in de syntaxis door de haken rond de naam van de para meter en het volgende type:</span><span class="sxs-lookup"><span data-stu-id="0a665-193">This is indicated in the syntax by the brackets around the parameter name and type:</span></span>

```powershell
[-Scope <string>]
```

<span data-ttu-id="0a665-194">In zowel de volgende voor beelden zijn het juiste gebruik van de `New-Alias` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="0a665-194">Both the following examples are correct uses of the `New-Alias` cmdlet:</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

<span data-ttu-id="0a665-195">Een parameter naam kan optioneel zijn, zelfs als de waarde voor die para meter is vereist.</span><span class="sxs-lookup"><span data-stu-id="0a665-195">A parameter name can be optional even if the value for that parameter is required.</span></span> <span data-ttu-id="0a665-196">Dit wordt aangegeven in de syntaxis van de haken rond de parameter naam, maar niet van het parameter type, zoals in dit voor beeld van de `New-Alias` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="0a665-196">This is indicated in the syntax by the brackets around the parameter name but not the parameter type, as in this example from the `New-Alias` cmdlet:</span></span>

```powershell
[-Name] <string> [-Value] <string>
```

<span data-ttu-id="0a665-197">Met de volgende opdrachten wordt de cmdlet op de juiste wijze gebruikt `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="0a665-197">The following commands correctly use the `New-Alias` cmdlet.</span></span> <span data-ttu-id="0a665-198">De opdrachten leveren hetzelfde resultaat op.</span><span class="sxs-lookup"><span data-stu-id="0a665-198">The commands produce the same result.</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

<span data-ttu-id="0a665-199">Als de parameter naam niet is opgenomen in de instructie als getypeerd, probeert Windows Power shell de positie van de argumenten te gebruiken om de waarden aan para meters toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="0a665-199">If the parameter name is not included in the statement as typed, Windows PowerShell tries to use the position of the arguments to assign the values to parameters.</span></span>

<span data-ttu-id="0a665-200">Het volgende voor beeld is niet voltooid:</span><span class="sxs-lookup"><span data-stu-id="0a665-200">The following example is not complete:</span></span>

```powershell
New-Alias utd
```

<span data-ttu-id="0a665-201">Voor deze cmdlet zijn waarden vereist voor de para meters **name** en **Value** .</span><span class="sxs-lookup"><span data-stu-id="0a665-201">This cmdlet requires values for both the **Name** and **Value** parameters.</span></span>

<span data-ttu-id="0a665-202">In syntaxis voorbeelden worden haakjes ook gebruikt bij het benoemen en casten naar .NET Framework typen.</span><span class="sxs-lookup"><span data-stu-id="0a665-202">In syntax examples, brackets are also used in naming and casting to .NET Framework types.</span></span> <span data-ttu-id="0a665-203">In deze context duiden haakjes niet aan dat een element optioneel is.</span><span class="sxs-lookup"><span data-stu-id="0a665-203">In this context, brackets do not indicate an element is optional.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a665-204">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="0a665-204">SEE ALSO</span></span>

- [<span data-ttu-id="0a665-205">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="0a665-205">about_Parameters</span></span>](about_Parameters.md)
- [<span data-ttu-id="0a665-206">Get-Command</span><span class="sxs-lookup"><span data-stu-id="0a665-206">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="0a665-207">Get-Help</span><span class="sxs-lookup"><span data-stu-id="0a665-207">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)
