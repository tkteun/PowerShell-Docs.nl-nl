---
description: Hierin worden de syntaxis diagrammen beschreven die worden gebruikt in Power shell.
Locale: en-US
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: ff7a243a584ee336c0356200f5ba68fde55e0836
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194622"
---
# <a name="about-command-syntax"></a><span data-ttu-id="5d910-103">Over opdracht syntaxis</span><span class="sxs-lookup"><span data-stu-id="5d910-103">About Command Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="5d910-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5d910-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="5d910-105">Hierin worden de syntaxis diagrammen beschreven die worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="5d910-105">Describes the syntax diagrams that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="5d910-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5d910-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="5d910-107">Met de cmdlets [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) en [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) worden syntaxis diagrammen weer gegeven om u te helpen opdrachten op de juiste manier te bouwen.</span><span class="sxs-lookup"><span data-stu-id="5d910-107">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) and [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) cmdlets display syntax diagrams to help you construct commands correctly.</span></span> <span data-ttu-id="5d910-108">In dit onderwerp wordt uitgelegd hoe u de syntaxis diagrammen kunt interpreteren.</span><span class="sxs-lookup"><span data-stu-id="5d910-108">This topic explains how to interpret the syntax diagrams.</span></span>

## <a name="syntax-diagrams"></a><span data-ttu-id="5d910-109">SYNTAXIS DIAGRAMMEN</span><span class="sxs-lookup"><span data-stu-id="5d910-109">SYNTAX DIAGRAMS</span></span>

<span data-ttu-id="5d910-110">Elke alinea in een opdracht syntaxis diagram vertegenwoordigt een geldige vorm van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5d910-110">Each paragraph in a command syntax diagram represents a valid form of the command.</span></span>

<span data-ttu-id="5d910-111">Als u een opdracht wilt maken, volgt u het syntaxis diagram van links naar rechts.</span><span class="sxs-lookup"><span data-stu-id="5d910-111">To construct a command, follow the syntax diagram from left to right.</span></span> <span data-ttu-id="5d910-112">Selecteer een van de optionele para meters en geef waarden op voor de tijdelijke aanduidingen.</span><span class="sxs-lookup"><span data-stu-id="5d910-112">Select from among the optional parameters and provide values for the placeholders.</span></span>

<span data-ttu-id="5d910-113">Power shell gebruikt de volgende notatie voor syntaxis diagrammen.</span><span class="sxs-lookup"><span data-stu-id="5d910-113">PowerShell uses the following notation for syntax diagrams.</span></span>

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

<span data-ttu-id="5d910-114">Hier volgt de syntaxis van de cmdlet [New-alias](xref:Microsoft.PowerShell.Utility.New-Alias) .</span><span class="sxs-lookup"><span data-stu-id="5d910-114">The following is the syntax for the [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias) cmdlet.</span></span>

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="5d910-115">De syntaxis is in grote zin voor lees baarheid, maar Power shell is niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="5d910-115">The syntax is capitalized for readability, but PowerShell is case-insensitive.</span></span>

<span data-ttu-id="5d910-116">Het syntaxis diagram bevat de volgende elementen.</span><span class="sxs-lookup"><span data-stu-id="5d910-116">The syntax diagram has the following elements.</span></span>

## <a name="command-name"></a><span data-ttu-id="5d910-117">Opdracht naam</span><span class="sxs-lookup"><span data-stu-id="5d910-117">Command name</span></span>

<span data-ttu-id="5d910-118">Opdrachten beginnen altijd met een opdracht naam, zoals `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="5d910-118">Commands always begin with a command name, such as `New-Alias`.</span></span> <span data-ttu-id="5d910-119">Typ de naam van de opdracht of de alias, bijvoorbeeld ' GCM ' voor `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="5d910-119">Type the command name or its alias, such a "gcm" for `Get-Command`.</span></span>

## <a name="parameters"></a><span data-ttu-id="5d910-120">Parameters</span><span class="sxs-lookup"><span data-stu-id="5d910-120">Parameters</span></span>

<span data-ttu-id="5d910-121">De para meters van een opdracht zijn opties die bepalen wat de opdracht doet.</span><span class="sxs-lookup"><span data-stu-id="5d910-121">The parameters of a command are options that determine what the command does.</span></span>
<span data-ttu-id="5d910-122">Sommige para meters hebben een ' waarde ' die gebruikers invoer heeft naar de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5d910-122">Some parameters take a "value" which is user input to the command.</span></span>

<span data-ttu-id="5d910-123">De `Get-Help` opdracht heeft bijvoorbeeld een para meter **name** waarmee u de naam van het onderwerp kunt opgeven waarvoor Help wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5d910-123">For example, the `Get-Help` command has a **Name** parameter that lets you specify the name of the topic for which help is displayed.</span></span> <span data-ttu-id="5d910-124">De naam van het onderwerp is de waarde van de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="5d910-124">The topic name is the value of the **Name** parameter.</span></span>

<span data-ttu-id="5d910-125">In een Power shell-opdracht beginnen parameter namen altijd met een koppel teken.</span><span class="sxs-lookup"><span data-stu-id="5d910-125">In a PowerShell command, parameter names always begin with a hyphen.</span></span>
<span data-ttu-id="5d910-126">Het afbreek streepje vertelt Power shell dat het item in de opdracht een parameter naam is.</span><span class="sxs-lookup"><span data-stu-id="5d910-126">The hyphen tells PowerShell that the item in the command is a parameter name.</span></span>

<span data-ttu-id="5d910-127">Als u bijvoorbeeld de para meter name van wilt gebruiken `New-Alias` , typt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="5d910-127">For example, to use the Name parameter of `New-Alias`, you type the following:</span></span>

```powershell
-Name
```

<span data-ttu-id="5d910-128">Para meters kunnen verplicht of optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="5d910-128">Parameters can be mandatory or optional.</span></span> <span data-ttu-id="5d910-129">In een syntaxis diagram bevinden optionele items zich tussen vier Kante haken `[ ]` .</span><span class="sxs-lookup"><span data-stu-id="5d910-129">In a syntax diagram, optional items are enclosed in brackets `[ ]`.</span></span>

<span data-ttu-id="5d910-130">Zie [about_Parameters](about_Parameters.md)voor meer informatie over para meters.</span><span class="sxs-lookup"><span data-stu-id="5d910-130">For more information about parameters, see [about_Parameters](about_Parameters.md).</span></span>

## <a name="parameter-values"></a><span data-ttu-id="5d910-131">Parameterwaarden</span><span class="sxs-lookup"><span data-stu-id="5d910-131">Parameter Values</span></span>

<span data-ttu-id="5d910-132">Een parameter waarde is de invoer die door de para meter wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5d910-132">A parameter value is the input that the parameter takes.</span></span> <span data-ttu-id="5d910-133">Omdat Windows Power shell is gebaseerd op het Microsoft .NET Framework, worden parameter waarden weer gegeven in het syntaxis diagram op basis van hun .NET-type.</span><span class="sxs-lookup"><span data-stu-id="5d910-133">Because Windows PowerShell is based on the Microsoft .NET Framework, parameter values are represented in the syntax diagram by their .NET type.</span></span>

<span data-ttu-id="5d910-134">De para meter name van neemt bijvoorbeeld een `Get-Help` teken reeks waarde, een teken reeks, zoals een enkel woord of meerdere woorden tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="5d910-134">For example, the Name parameter of `Get-Help` takes a "String" value, which is a text string, such as a single word or multiple words enclosed in quotation marks.</span></span>

```powershell
[-Name] <string>
```

<span data-ttu-id="5d910-135">Het .NET-type van een parameter waarde bevindt zich tussen punt haken `< >` om aan te geven dat het een tijdelijke aanduiding voor een waarde is en niet een letterlijke teken reeks die u in een opdracht typt.</span><span class="sxs-lookup"><span data-stu-id="5d910-135">The .NET type of a parameter value is enclosed in angle brackets `< >` to indicate that it is placeholder for a value and not a literal that you type in a command.</span></span>

<span data-ttu-id="5d910-136">Als u de para meter wilt gebruiken, vervangt u de tijdelijke aanduiding .NET-type door een object dat het opgegeven .NET-type heeft.</span><span class="sxs-lookup"><span data-stu-id="5d910-136">To use the parameter, replace the .NET type placeholder with an object that has the specified .NET type.</span></span>

<span data-ttu-id="5d910-137">Als u bijvoorbeeld de para meter **name** wilt gebruiken, typt u '-name ', gevolgd door een teken reeks, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="5d910-137">For example, to use the **Name** parameter, type "-Name" followed by a string, such as the following:</span></span>

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a><span data-ttu-id="5d910-138">Para meters zonder waarden</span><span class="sxs-lookup"><span data-stu-id="5d910-138">Parameters with no values</span></span>

<span data-ttu-id="5d910-139">Sommige para meters accepteren geen invoer, dus ze hebben geen parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="5d910-139">Some parameters do not accept input, so they do not have a parameter value.</span></span>
<span data-ttu-id="5d910-140">Para meters zonder waarden worden "switch parameters" genoemd, omdat ze werken als aan/uit-switches.</span><span class="sxs-lookup"><span data-stu-id="5d910-140">Parameters without values are called "switch parameters" because they work like on/off switches.</span></span> <span data-ttu-id="5d910-141">U neemt ze op (aan) of u kunt deze weglaten (uit) van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="5d910-141">You include them (on) or you omit them (off) from a command.</span></span>

<span data-ttu-id="5d910-142">Als u een para meter switch wilt gebruiken, typt u de parameter naam, voorafgegaan door een koppel teken.</span><span class="sxs-lookup"><span data-stu-id="5d910-142">To use a switch parameter, just type the parameter name, preceded by a hyphen.</span></span>

<span data-ttu-id="5d910-143">Als u bijvoorbeeld de para meter **WhatIf** van de cmdlet wilt gebruiken `New-Alias` , typt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="5d910-143">For example, to use the **WhatIf** parameter of the `New-Alias` cmdlet, type the following:</span></span>

```powershell
-WhatIf
```

## <a name="parameter-sets"></a><span data-ttu-id="5d910-144">Parametersets</span><span class="sxs-lookup"><span data-stu-id="5d910-144">Parameter Sets</span></span>

<span data-ttu-id="5d910-145">De para meters van een opdracht worden weer gegeven in de parameter sets.</span><span class="sxs-lookup"><span data-stu-id="5d910-145">The parameters of a command are listed in parameter sets.</span></span> <span data-ttu-id="5d910-146">Parameter sets zien eruit als de alinea's van een syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="5d910-146">Parameter sets look like the paragraphs of a syntax diagram.</span></span>

<span data-ttu-id="5d910-147">De `New-Alias` cmdlet heeft één set para meters, maar veel cmdlets hebben meerdere parametersets.</span><span class="sxs-lookup"><span data-stu-id="5d910-147">The `New-Alias` cmdlet has one parameter set, but many cmdlets have multiple parameter sets.</span></span> <span data-ttu-id="5d910-148">Sommige cmdlet-para meters zijn uniek voor een parameterset en andere worden weer gegeven in meerdere parameter sets.</span><span class="sxs-lookup"><span data-stu-id="5d910-148">Some of the cmdlet parameters are unique to a parameter set, and others appear in multiple parameter sets.</span></span> <span data-ttu-id="5d910-149">Elke parameterset vertegenwoordigt de indeling van een geldige opdracht.</span><span class="sxs-lookup"><span data-stu-id="5d910-149">Each parameter set represents the format of a valid command.</span></span> <span data-ttu-id="5d910-150">Een parameterset bevat alleen para meters die samen in een opdracht kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5d910-150">A parameter set includes only parameters that can be used together in a command.</span></span> <span data-ttu-id="5d910-151">Als para meters niet kunnen worden gebruikt in dezelfde opdracht, worden ze weer gegeven in afzonderlijke parameter sets.</span><span class="sxs-lookup"><span data-stu-id="5d910-151">If parameters cannot be used in the same command, they appear in separate parameter sets.</span></span>

<span data-ttu-id="5d910-152">De [Get-wille](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet heeft bijvoorbeeld de volgende parameter sets:</span><span class="sxs-lookup"><span data-stu-id="5d910-152">For example, the [Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random) cmdlet has the following parameter sets:</span></span>

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

<span data-ttu-id="5d910-153">De eerste parameterset, die een wille keurig getal retourneert, heeft de **minimum** -en **maximum** waarden.</span><span class="sxs-lookup"><span data-stu-id="5d910-153">The first parameter set, which returns a random number, has the **Minimum** and **Maximum** parameters.</span></span> <span data-ttu-id="5d910-154">De tweede parameterset, die een wille keurig geselecteerd object uit een set objecten retourneert, omvat de para meters **input object** en **Count** .</span><span class="sxs-lookup"><span data-stu-id="5d910-154">The second parameter set, which returns a randomly selected object from a set of objects, includes the **InputObject** and **Count** parameters.</span></span> <span data-ttu-id="5d910-155">Beide parameter sets hebben de para meter **SetSeed** en de algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="5d910-155">Both parameter sets have the **SetSeed** parameter and the common parameters.</span></span>

<span data-ttu-id="5d910-156">Deze parameter sets geven aan dat u de para meters **input object** en **Count** kunt gebruiken in dezelfde opdracht, maar u kunt de para meters voor **maximum** en **aantal** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="5d910-156">These parameter sets indicate that you can use the **InputObject** and **Count** parameters in the same command, but you cannot use the **Maximum** and **Count** parameters in the same command.</span></span>

<span data-ttu-id="5d910-157">U geeft aan welke para meter die u wilt gebruiken met behulp van de para meters in die para meter zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="5d910-157">You indicate which parameter set you want to use by using the parameters in that parameter set.</span></span>

<span data-ttu-id="5d910-158">Voor elke cmdlet is echter ook een standaard parameterset ingesteld.</span><span class="sxs-lookup"><span data-stu-id="5d910-158">However, every cmdlet also has a default parameter set.</span></span> <span data-ttu-id="5d910-159">De standaard parameterset wordt gebruikt wanneer u geen para meters opgeeft die uniek zijn voor een parameterset.</span><span class="sxs-lookup"><span data-stu-id="5d910-159">The default parameter set is used when you do not specify parameters that are unique to a parameter set.</span></span> <span data-ttu-id="5d910-160">Als u bijvoorbeeld `Get-Random` zonder para meters gebruikt, veronderstelt Windows Power shell dat u de para  meter set gebruikt en retourneert deze een wille keurig getal.</span><span class="sxs-lookup"><span data-stu-id="5d910-160">For example, if you use `Get-Random` without parameters, Windows PowerShell assumes that you are using the **Number** parameter set and it returns a random number.</span></span>

<span data-ttu-id="5d910-161">In elke parameterset worden de para meters in positie volgorde weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5d910-161">In each parameter set, the parameters appear in position order.</span></span> <span data-ttu-id="5d910-162">De volg orde van de para meters in een opdracht is alleen van belang wanneer u de optionele parameter namen weglaat.</span><span class="sxs-lookup"><span data-stu-id="5d910-162">The order of parameters in a command matters only when you omit the optional parameter names.</span></span> <span data-ttu-id="5d910-163">Wanneer parameter namen worden wegge laten, wijst Power shell waarden toe aan para meters op positie en type.</span><span class="sxs-lookup"><span data-stu-id="5d910-163">When parameter names are omitted, PowerShell assigns values to parameters by position and type.</span></span> <span data-ttu-id="5d910-164">Zie voor meer informatie over de positie van de para meter `about_Parameters` .</span><span class="sxs-lookup"><span data-stu-id="5d910-164">For more information about parameter position, see `about_Parameters`.</span></span>

## <a name="symbols-in-syntax-diagrams"></a><span data-ttu-id="5d910-165">Symbolen in syntaxis diagrammen</span><span class="sxs-lookup"><span data-stu-id="5d910-165">Symbols in Syntax Diagrams</span></span>

<span data-ttu-id="5d910-166">Het syntaxis diagram bevat een lijst met de naam van de opdracht, de opdracht parameters en de parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="5d910-166">The syntax diagram lists the command name, the command parameters, and the parameter values.</span></span> <span data-ttu-id="5d910-167">Er worden ook symbolen gebruikt om te laten zien hoe u een geldige opdracht kunt maken.</span><span class="sxs-lookup"><span data-stu-id="5d910-167">It also uses symbols to show how to construct a valid command.</span></span>

<span data-ttu-id="5d910-168">De syntaxis diagrammen gebruiken de volgende symbolen:</span><span class="sxs-lookup"><span data-stu-id="5d910-168">The syntax diagrams use the following symbols:</span></span>

- <span data-ttu-id="5d910-169">Een koppel teken `-` geeft de naam van een para meter aan.</span><span class="sxs-lookup"><span data-stu-id="5d910-169">A hyphen `-` indicates a parameter name.</span></span> <span data-ttu-id="5d910-170">Typ in een opdracht het afbreek streepje direct vóór de parameter naam zonder tussenliggende spaties, zoals wordt weer gegeven in het syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="5d910-170">In a command, type the hyphen immediately before the parameter name with no intervening spaces, as shown in the syntax diagram.</span></span>

  <span data-ttu-id="5d910-171">Als u bijvoorbeeld de para meter **name** van wilt gebruiken `New-Alias` , typt u:</span><span class="sxs-lookup"><span data-stu-id="5d910-171">For example, to use the **Name** parameter of `New-Alias`, type:</span></span>

  ```powershell
  -Name
  ```

- <span data-ttu-id="5d910-172">Met punt haken wordt de `<>` tijdelijke aanduiding voor tekst aangeduid.</span><span class="sxs-lookup"><span data-stu-id="5d910-172">Angle brackets `<>` indicate placeholder text.</span></span> <span data-ttu-id="5d910-173">U typt geen punt haken of de tekst van de tijdelijke aanduiding in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="5d910-173">You do not type the angle brackets or the placeholder text in a command.</span></span> <span data-ttu-id="5d910-174">In plaats daarvan vervangt u deze door het item dat hierin wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="5d910-174">Instead, you replace it with the item that it describes.</span></span>

  <span data-ttu-id="5d910-175">Punt haken worden gebruikt voor het identificeren van het .NET-type van de waarde die een para meter gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5d910-175">Angle brackets are used to identify the .NET type of the value that a parameter takes.</span></span> <span data-ttu-id="5d910-176">Als u bijvoorbeeld de para meter **name** van de cmdlet wilt gebruiken `New-Alias` , vervangt u de `<string>` door een teken reeks, een enkel woord of een groep woorden die tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="5d910-176">For example, to use the **Name** parameter of the `New-Alias` cmdlet, you replace the `<string>` with a string, which is a single word or a group of words that are enclosed in quotation marks.</span></span>

- <span data-ttu-id="5d910-177">Optionele items worden aangegeven door accolades `[ ]` .</span><span class="sxs-lookup"><span data-stu-id="5d910-177">Brackets `[ ]` indicate optional items.</span></span> <span data-ttu-id="5d910-178">Een para meter en de waarde ervan kunnen optioneel zijn, of de naam van een vereiste para meter kan optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="5d910-178">A parameter and its value can be optional, or the name of a required parameter can be optional.</span></span>

  <span data-ttu-id="5d910-179">De para meter **Description** van `New-Alias` en de waarde ervan bevindt zich bijvoorbeeld tussen vier Kante haken, omdat deze beide optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="5d910-179">For example, the **Description** parameter of `New-Alias` and its value are enclosed in brackets because they are both optional.</span></span>

  ```powershell
  [-Description <string>]
  ```

  <span data-ttu-id="5d910-180">De haakjes geven ook aan dat de waarde van de para meter name `<string>` vereist is, maar de parameter naam ' naam ' is optioneel.</span><span class="sxs-lookup"><span data-stu-id="5d910-180">The brackets also indicate that the Name parameter value `<string>` is required, but the parameter name, "Name", is optional.</span></span>

  ```powershell
  [-Name] <string>
  ```

- <span data-ttu-id="5d910-181">Een recht en haakje links `[]` toegevoegd aan een .net-type geeft aan dat de para meter een of meer waarden van dat type kan accepteren.</span><span class="sxs-lookup"><span data-stu-id="5d910-181">A right and left bracket `[]` appended to a .NET type indicates that the parameter can accept one or multiple values of that type.</span></span> <span data-ttu-id="5d910-182">Voer de waarden in een door komma's gescheiden lijst in.</span><span class="sxs-lookup"><span data-stu-id="5d910-182">Enter the values in a comma-separated list.</span></span>

  <span data-ttu-id="5d910-183">De para meter **name** van de `New-Alias` cmdlet gebruikt bijvoorbeeld slechts één teken reeks, maar de para meter **name** van [Get-process](xref:Microsoft.PowerShell.Management.Get-Process) kan een of meer teken reeksen aannemen.</span><span class="sxs-lookup"><span data-stu-id="5d910-183">For example, the **Name** parameter of the `New-Alias` cmdlet takes only one string, but the **Name** parameter of [Get-Process](xref:Microsoft.PowerShell.Management.Get-Process) can take one or many strings.</span></span>

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- <span data-ttu-id="5d910-184">Accolades `{}` geven een ' opsomming ' aan. Dit is een set geldige waarden voor een para meter.</span><span class="sxs-lookup"><span data-stu-id="5d910-184">Braces `{}` indicate an "enumeration," which is a set of valid values for a parameter.</span></span>

  <span data-ttu-id="5d910-185">De waarden in de accolades worden gescheiden door verticale balken `|` .</span><span class="sxs-lookup"><span data-stu-id="5d910-185">The values in the braces are separated by vertical bars `|`.</span></span> <span data-ttu-id="5d910-186">Deze balken geven een ' exclusieve of ' keuze aan, wat betekent dat u slechts één waarde kunt kiezen uit de set waarden die worden weer gegeven binnen de accolades.</span><span class="sxs-lookup"><span data-stu-id="5d910-186">These bars indicate an "exclusive OR" choice, meaning that you can choose only one value from the set of values that are listed inside the braces.</span></span>

  <span data-ttu-id="5d910-187">De syntaxis voor de `New-Alias` cmdlet bevat bijvoorbeeld de volgende waarde-inventarisatie voor de para meter **Option** :</span><span class="sxs-lookup"><span data-stu-id="5d910-187">For example, the syntax for the `New-Alias` cmdlet includes the following value enumeration for the **Option** parameter:</span></span>

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  <span data-ttu-id="5d910-188">De accolades en verticale balken geven aan dat u een van de vermelde waarden voor de para meter **Option** kunt kiezen, zoals "readonly" of "AllScope".</span><span class="sxs-lookup"><span data-stu-id="5d910-188">The braces and vertical bars indicate that you can choose any one of the listed values for the **Option** parameter, such as "ReadOnly" or "AllScope".</span></span>

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a><span data-ttu-id="5d910-189">Optionele items</span><span class="sxs-lookup"><span data-stu-id="5d910-189">Optional Items</span></span>

<span data-ttu-id="5d910-190">Vier Kante haken `[]` rond optionele items.</span><span class="sxs-lookup"><span data-stu-id="5d910-190">Brackets `[]` surround optional items.</span></span> <span data-ttu-id="5d910-191">In de beschrijving van de `New-Alias` syntaxis van de cmdlet is de **bereik** parameter bijvoorbeeld optioneel.</span><span class="sxs-lookup"><span data-stu-id="5d910-191">For example, in the `New-Alias` cmdlet syntax description, the **Scope** parameter is optional.</span></span> <span data-ttu-id="5d910-192">Dit wordt aangegeven in de syntaxis door de haken rond de naam van de para meter en het volgende type:</span><span class="sxs-lookup"><span data-stu-id="5d910-192">This is indicated in the syntax by the brackets around the parameter name and type:</span></span>

```powershell
[-Scope <string>]
```

<span data-ttu-id="5d910-193">In zowel de volgende voor beelden zijn het juiste gebruik van de `New-Alias` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5d910-193">Both the following examples are correct uses of the `New-Alias` cmdlet:</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

<span data-ttu-id="5d910-194">Een parameter naam kan optioneel zijn, zelfs als de waarde voor die para meter is vereist.</span><span class="sxs-lookup"><span data-stu-id="5d910-194">A parameter name can be optional even if the value for that parameter is required.</span></span> <span data-ttu-id="5d910-195">Dit wordt aangegeven in de syntaxis van de haken rond de parameter naam, maar niet van het parameter type, zoals in dit voor beeld van de `New-Alias` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5d910-195">This is indicated in the syntax by the brackets around the parameter name but not the parameter type, as in this example from the `New-Alias` cmdlet:</span></span>

```powershell
[-Name] <string> [-Value] <string>
```

<span data-ttu-id="5d910-196">Met de volgende opdrachten wordt de cmdlet op de juiste wijze gebruikt `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="5d910-196">The following commands correctly use the `New-Alias` cmdlet.</span></span> <span data-ttu-id="5d910-197">De opdrachten leveren hetzelfde resultaat op.</span><span class="sxs-lookup"><span data-stu-id="5d910-197">The commands produce the same result.</span></span>

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

<span data-ttu-id="5d910-198">Als de parameter naam niet is opgenomen in de instructie als getypeerd, probeert Windows Power shell de positie van de argumenten te gebruiken om de waarden aan para meters toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="5d910-198">If the parameter name is not included in the statement as typed, Windows PowerShell tries to use the position of the arguments to assign the values to parameters.</span></span>

<span data-ttu-id="5d910-199">Het volgende voor beeld is niet voltooid:</span><span class="sxs-lookup"><span data-stu-id="5d910-199">The following example is not complete:</span></span>

```powershell
New-Alias utd
```

<span data-ttu-id="5d910-200">Voor deze cmdlet zijn waarden vereist voor de para meters **name** en **Value** .</span><span class="sxs-lookup"><span data-stu-id="5d910-200">This cmdlet requires values for both the **Name** and **Value** parameters.</span></span>

<span data-ttu-id="5d910-201">In syntaxis voorbeelden worden haakjes ook gebruikt bij het benoemen en casten naar .NET Framework typen.</span><span class="sxs-lookup"><span data-stu-id="5d910-201">In syntax examples, brackets are also used in naming and casting to .NET Framework types.</span></span> <span data-ttu-id="5d910-202">In deze context duiden haakjes niet aan dat een element optioneel is.</span><span class="sxs-lookup"><span data-stu-id="5d910-202">In this context, brackets do not indicate an element is optional.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d910-203">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="5d910-203">SEE ALSO</span></span>

- [<span data-ttu-id="5d910-204">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="5d910-204">about_Parameters</span></span>](about_Parameters.md)
- [<span data-ttu-id="5d910-205">Get-Command</span><span class="sxs-lookup"><span data-stu-id="5d910-205">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="5d910-206">Get-Help</span><span class="sxs-lookup"><span data-stu-id="5d910-206">Get-Help</span></span>](xref:Microsoft.PowerShell.Core.Get-Help)
