---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 2/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 2a84c08022689d53c3273f1b6f802cfeae67953d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249909"
---
# <span data-ttu-id="42b25-103">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="42b25-103">Set-Alias</span></span>

## <span data-ttu-id="42b25-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="42b25-104">SYNOPSIS</span></span>
<span data-ttu-id="42b25-105">Hiermee maakt of wijzigt u een alias voor een cmdlet of een andere opdracht in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="42b25-105">Creates or changes an alias for a cmdlet or other command in the current PowerShell session.</span></span>

## <span data-ttu-id="42b25-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="42b25-106">SYNTAX</span></span>

### <span data-ttu-id="42b25-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="42b25-107">Default (Default)</span></span>

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="42b25-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="42b25-108">DESCRIPTION</span></span>

<span data-ttu-id="42b25-109">De `Set-Alias` cmdlet maakt of wijzigt een alias voor een cmdlet of een opdracht, zoals een functie, script, bestand of ander uitvoerbaar bestand.</span><span class="sxs-lookup"><span data-stu-id="42b25-109">The `Set-Alias` cmdlet creates or changes an alias for a cmdlet or a command, such as a function, script, file, or other executable.</span></span> <span data-ttu-id="42b25-110">Een alias is een alternatieve naam die verwijst naar een cmdlet of opdracht.</span><span class="sxs-lookup"><span data-stu-id="42b25-110">An alias is an alternate name that refers to a cmdlet or command.</span></span>
<span data-ttu-id="42b25-111">`sal`Is bijvoorbeeld de alias voor de `Set-Alias` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42b25-111">For example, `sal` is the alias for the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="42b25-112">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="42b25-112">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="42b25-113">Een cmdlet kan meerdere aliassen hebben, maar een alias kan slechts aan één cmdlet worden gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="42b25-113">A cmdlet can have multiple aliases, but an alias can only be associated with one cmdlet.</span></span> <span data-ttu-id="42b25-114">U kunt gebruiken `Set-Alias` om een bestaande alias opnieuw toe te wijzen aan een andere cmdlet of de eigenschappen van een alias te wijzigen, zoals de beschrijving.</span><span class="sxs-lookup"><span data-stu-id="42b25-114">You can use `Set-Alias` to reassign an existing alias to another cmdlet, or change an alias's properties, such as the description.</span></span>

<span data-ttu-id="42b25-115">Een alias die is gemaakt of gewijzigd door `Set-Alias` is niet permanent en is alleen beschikbaar tijdens de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="42b25-115">An alias that is created or changed by `Set-Alias` is not permanent and is only available during the current PowerShell session.</span></span> <span data-ttu-id="42b25-116">Wanneer de Power shell-sessie is gesloten, wordt de alias verwijderd.</span><span class="sxs-lookup"><span data-stu-id="42b25-116">When the PowerShell session is closed, the alias is removed.</span></span>

## <span data-ttu-id="42b25-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="42b25-117">EXAMPLES</span></span>

### <span data-ttu-id="42b25-118">Voor beeld 1: een alias maken voor een cmdlet</span><span class="sxs-lookup"><span data-stu-id="42b25-118">Example 1: Create an alias for a cmdlet</span></span>

<span data-ttu-id="42b25-119">Met deze opdracht maakt u een alias voor een cmdlet in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="42b25-119">This command creates an alias to a cmdlet in the current PowerShell session.</span></span>

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

<span data-ttu-id="42b25-120">`Set-Alias`Met de cmdlet maakt u een alias in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="42b25-120">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="42b25-121">Met de para meter **name** wordt de naam van de alias opgegeven, `list` .</span><span class="sxs-lookup"><span data-stu-id="42b25-121">The **Name** parameter specifies the alias's name, `list`.</span></span> <span data-ttu-id="42b25-122">De **waarde** para meter geeft u de cmdlet op die de alias uitvoert.</span><span class="sxs-lookup"><span data-stu-id="42b25-122">The **Value** parameter specifies the cmdlet that the alias runs.</span></span>

<span data-ttu-id="42b25-123">Als u de alias wilt uitvoeren, typt u `list` op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="42b25-123">To run the alias, type `list` on the PowerShell command line.</span></span>

### <span data-ttu-id="42b25-124">Voor beeld 2: een bestaande alias opnieuw toewijzen aan een andere cmdlet</span><span class="sxs-lookup"><span data-stu-id="42b25-124">Example 2: Reassign an existing alias to a different cmdlet</span></span>

<span data-ttu-id="42b25-125">Met deze opdracht wordt een bestaande alias opnieuw toegewezen om een andere cmdlet uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="42b25-125">This command reassigns an existing alias to run a different cmdlet.</span></span>

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

<span data-ttu-id="42b25-126">De `Get-Alias` cmdlet gebruikt de para meter **name** om de alias weer te geven `list` .</span><span class="sxs-lookup"><span data-stu-id="42b25-126">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="42b25-127">De `list` alias is gekoppeld aan de `Get-ChildItem` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42b25-127">The `list` alias is associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="42b25-128">Wanneer de `list` alias wordt uitgevoerd, worden de items in de huidige map weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="42b25-128">When the `list` alias is run, the items in the current directory are displayed.</span></span>

<span data-ttu-id="42b25-129">De `Set-Alias` cmdlet gebruikt de para meter **name** om de alias op te geven `list` .</span><span class="sxs-lookup"><span data-stu-id="42b25-129">The `Set-Alias` cmdlet uses the **Name** parameter to specify the `list` alias.</span></span> <span data-ttu-id="42b25-130">De **waarde** para meter koppelt de alias aan de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42b25-130">The **Value** parameter associates the alias to the `Get-Location` cmdlet.</span></span>

<span data-ttu-id="42b25-131">De `Get-Alias` cmdlet gebruikt de para meter **name** om de alias weer te geven `list` .</span><span class="sxs-lookup"><span data-stu-id="42b25-131">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="42b25-132">De `list` alias is gekoppeld aan de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42b25-132">The `list` alias is associated with the `Get-Location` cmdlet.</span></span> <span data-ttu-id="42b25-133">Wanneer de `list` alias wordt uitgevoerd, wordt de locatie van de huidige map weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="42b25-133">When the `list` alias is run, the current directory's location is displayed.</span></span>

### <span data-ttu-id="42b25-134">Voor beeld 3: een alleen-lezen-alias maken en wijzigen</span><span class="sxs-lookup"><span data-stu-id="42b25-134">Example 3: Create and change a read-only alias</span></span>

<span data-ttu-id="42b25-135">Met deze opdracht maakt u een alias met het kenmerk alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="42b25-135">This command creates a read-only alias.</span></span> <span data-ttu-id="42b25-136">De alleen-lezen optie voor komt onbedoelde wijzigingen aan een alias.</span><span class="sxs-lookup"><span data-stu-id="42b25-136">The read-only option prevents unintended changes to an alias.</span></span> <span data-ttu-id="42b25-137">Als u een alleen-lezen alias wilt wijzigen of verwijderen, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="42b25-137">To change or delete a read-only alias, use the **Force** parameter.</span></span>

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

<span data-ttu-id="42b25-138">`Set-Alias`Met de cmdlet maakt u een alias in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="42b25-138">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="42b25-139">Met de para meter **name** wordt de naam van de alias opgegeven, `loc` .</span><span class="sxs-lookup"><span data-stu-id="42b25-139">The **Name** parameter specifies the alias's name, `loc`.</span></span> <span data-ttu-id="42b25-140">De **waarde** para meter geeft u de `Get-Location` cmdlet op die de alias uitvoert.</span><span class="sxs-lookup"><span data-stu-id="42b25-140">The **Value** parameter specifies the `Get-Location` cmdlet that the alias runs.</span></span> <span data-ttu-id="42b25-141">Met de para meter **Option** wordt de waarde **ReadOnly** opgegeven.</span><span class="sxs-lookup"><span data-stu-id="42b25-141">The **Option** parameter specifies the **ReadOnly** value.</span></span> <span data-ttu-id="42b25-142">De para meter **PassThru** vertegenwoordigt het alias object en stuurt het object omlaag in de pijp lijn naar de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42b25-142">The **PassThru** parameter represents the alias object and sends the object down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="42b25-143">`Format-List` gebruikt de **eigenschaps** parameter met een asterisk ( `*` ), zodat alle eigenschappen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="42b25-143">`Format-List` uses the **Property** parameter with an asterisk (`*`) so that all of the properties are displayed.</span></span> <span data-ttu-id="42b25-144">In de voorbeeld uitvoer ziet u een gedeeltelijke lijst met die eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="42b25-144">The example output shows a partial list of those properties.</span></span>

<span data-ttu-id="42b25-145">De `loc` alias wordt gewijzigd met de toevoeging van twee para meters.</span><span class="sxs-lookup"><span data-stu-id="42b25-145">The `loc` alias is changed with the addition of two parameters.</span></span> <span data-ttu-id="42b25-146">**Beschrijving** voegt tekst toe om het doel van de alias te verklaren.</span><span class="sxs-lookup"><span data-stu-id="42b25-146">**Description** adds text to explain the alias's purpose.</span></span> <span data-ttu-id="42b25-147">De para meter **Force** is vereist omdat de `loc` alias alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="42b25-147">The **Force** parameter is needed because the `loc` alias is read-only.</span></span> <span data-ttu-id="42b25-148">Als de para meter **Forces** niet wordt gebruikt, mislukt de wijziging.</span><span class="sxs-lookup"><span data-stu-id="42b25-148">If the **Force** parameter is not used, the change fails.</span></span>

### <span data-ttu-id="42b25-149">Voor beeld 4: een alias maken voor een uitvoerbaar bestand</span><span class="sxs-lookup"><span data-stu-id="42b25-149">Example 4: Create an alias to an executable file</span></span>

<span data-ttu-id="42b25-150">In dit voor beeld wordt een alias gemaakt voor een uitvoerbaar bestand op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="42b25-150">This example creates an alias to an executable file on the local computer.</span></span>

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

<span data-ttu-id="42b25-151">`Set-Alias`Met de cmdlet maakt u een alias in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="42b25-151">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="42b25-152">Met de para meter **name** wordt de naam van de alias opgegeven, `np` .</span><span class="sxs-lookup"><span data-stu-id="42b25-152">The **Name** parameter specifies the alias's name, `np`.</span></span> <span data-ttu-id="42b25-153">De **waarde** para meter geeft u het pad en de naam van de toepassing op **C:\Windows\notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="42b25-153">The **Value** parameter specifies the path and application name **C:\Windows\notepad.exe**.</span></span> <span data-ttu-id="42b25-154">De `Get-Alias` cmdlet gebruikt de para meter **name** om aan te geven dat de `np` alias is gekoppeld aan **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="42b25-154">The `Get-Alias` cmdlet uses the **Name** parameter to show that the `np` alias is associated with **notepad.exe**.</span></span>

<span data-ttu-id="42b25-155">Als u de alias wilt uitvoeren, typt `np` u op de Power shell-opdracht regel om **notepad.exe** te openen.</span><span class="sxs-lookup"><span data-stu-id="42b25-155">To run the alias, type `np` on the PowerShell command line to open **notepad.exe**.</span></span>

### <span data-ttu-id="42b25-156">Voor beeld 5: een alias maken voor een opdracht met para meters</span><span class="sxs-lookup"><span data-stu-id="42b25-156">Example 5: Create an alias for a command with parameters</span></span>

<span data-ttu-id="42b25-157">In dit voor beeld ziet u hoe u een alias toewijst aan een opdracht met para meters.</span><span class="sxs-lookup"><span data-stu-id="42b25-157">This example shows how to assign an alias to a command with parameters.</span></span>

<span data-ttu-id="42b25-158">U kunt een alias voor een cmdlet maken, zoals `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="42b25-158">You can create an alias for a cmdlet, such as `Set-Location`.</span></span> <span data-ttu-id="42b25-159">U kunt geen alias maken voor een opdracht met para meters en waarden, zoals `Set-Location -Path C:\Windows\System32` .</span><span class="sxs-lookup"><span data-stu-id="42b25-159">You cannot create an alias for a command with parameters and values, such as `Set-Location -Path C:\Windows\System32`.</span></span> <span data-ttu-id="42b25-160">Als u een alias voor een opdracht wilt maken, maakt u een functie die de opdracht bevat en maakt u vervolgens een alias voor de functie.</span><span class="sxs-lookup"><span data-stu-id="42b25-160">To create an alias for a command, create a function that includes the command, and then create an alias to the function.</span></span> <span data-ttu-id="42b25-161">Zie [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="42b25-161">For more information, see [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).</span></span>

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

<span data-ttu-id="42b25-162">Er wordt een functie gemaakt met de naam `CD32` .</span><span class="sxs-lookup"><span data-stu-id="42b25-162">A function named `CD32` is created.</span></span> <span data-ttu-id="42b25-163">De functie gebruikt de- `Set-Location` cmdlet met de para meter **Path** om de map, **C:\Windows\System32** op te geven.</span><span class="sxs-lookup"><span data-stu-id="42b25-163">The function uses the `Set-Location` cmdlet with the **Path** parameter to specify the directory, **C:\Windows\System32**.</span></span>

<span data-ttu-id="42b25-164">De `Set-Alias` cmdlet maakt een alias voor de functie in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="42b25-164">The `Set-Alias` cmdlet creates an alias to the function in the current PowerShell session.</span></span> <span data-ttu-id="42b25-165">Met de para meter **name** wordt de naam van de alias opgegeven, `Go` .</span><span class="sxs-lookup"><span data-stu-id="42b25-165">The **Name** parameter specifies the alias's name, `Go`.</span></span> <span data-ttu-id="42b25-166">De **waarde** para meter geeft u de naam van de functie op `CD32` .</span><span class="sxs-lookup"><span data-stu-id="42b25-166">The **Value** parameter specifies the function's name, `CD32`.</span></span>

<span data-ttu-id="42b25-167">Als u de alias wilt uitvoeren, typt u `Go` op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="42b25-167">To run the alias, type `Go` on the PowerShell command line.</span></span> <span data-ttu-id="42b25-168">De `CD32` functie wordt uitgevoerd en wijzigingen worden aangebracht in de Directory **C:\Windows\System32**.</span><span class="sxs-lookup"><span data-stu-id="42b25-168">The `CD32` function runs and changes to the directory **C:\Windows\System32**.</span></span>

## <span data-ttu-id="42b25-169">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="42b25-169">PARAMETERS</span></span>

### <span data-ttu-id="42b25-170">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="42b25-170">-Description</span></span>

<span data-ttu-id="42b25-171">Hiermee geeft u een beschrijving van de alias.</span><span class="sxs-lookup"><span data-stu-id="42b25-171">Specifies a description of the alias.</span></span> <span data-ttu-id="42b25-172">U kunt een wille keurige teken reeks typen.</span><span class="sxs-lookup"><span data-stu-id="42b25-172">You can type any string.</span></span> <span data-ttu-id="42b25-173">Als de beschrijving spaties bevat, plaatst u deze enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="42b25-173">If the description includes spaces, enclose it single quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42b25-174">-Force</span><span class="sxs-lookup"><span data-stu-id="42b25-174">-Force</span></span>

<span data-ttu-id="42b25-175">Gebruik de para meter **Force** om een alias te wijzigen of te verwijderen waarvoor de **optie** parameter is ingesteld op **ReadOnly**.</span><span class="sxs-lookup"><span data-stu-id="42b25-175">Use the **Force** parameter to change or delete an alias that has the **Option** parameter set to **ReadOnly**.</span></span>

<span data-ttu-id="42b25-176">De para meter **Force** kan geen alias wijzigen of verwijderen met de para meter **Option** ingesteld op **constant**.</span><span class="sxs-lookup"><span data-stu-id="42b25-176">The **Force** parameter cannot change or delete an alias with the **Option** parameter set to **Constant**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42b25-177">-Name</span><span class="sxs-lookup"><span data-stu-id="42b25-177">-Name</span></span>

<span data-ttu-id="42b25-178">Hiermee geeft u de naam van een nieuwe alias.</span><span class="sxs-lookup"><span data-stu-id="42b25-178">Specifies the name of a new alias.</span></span> <span data-ttu-id="42b25-179">Een alias naam mag alfanumerieke tekens en afbreek streepjes bevatten.</span><span class="sxs-lookup"><span data-stu-id="42b25-179">An alias name can contain alphanumeric characters and hyphens.</span></span> <span data-ttu-id="42b25-180">Alias namen mogen niet numeriek zijn, zoals 123.</span><span class="sxs-lookup"><span data-stu-id="42b25-180">Alias names cannot be numeric, such as 123.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="42b25-181">-Optie</span><span class="sxs-lookup"><span data-stu-id="42b25-181">-Option</span></span>

<span data-ttu-id="42b25-182">Hiermee stelt u de waarde van de **optie** eigenschap van de alias.</span><span class="sxs-lookup"><span data-stu-id="42b25-182">Sets the **Option** property value of the alias.</span></span> <span data-ttu-id="42b25-183">Waarden zoals **alleen-lezen** en **constant** een alias beveiligen tegen onbedoelde wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="42b25-183">Values such as **ReadOnly** and **Constant** protect an alias from unintended changes.</span></span> <span data-ttu-id="42b25-184">Als u de **optie** -eigenschap van alle aliassen in de sessie wilt weer geven, typt u `Get-Alias | Format-Table -Property Name, Options -Autosize` .</span><span class="sxs-lookup"><span data-stu-id="42b25-184">To see the **Option** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -Autosize`.</span></span>

<span data-ttu-id="42b25-185">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="42b25-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="42b25-186">**AllScope** De alias wordt gekopieerd naar nieuwe bereiken die worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="42b25-186">**AllScope** The alias is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="42b25-187">**Constante** Kan niet worden gewijzigd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="42b25-187">**Constant** Cannot be changed or deleted.</span></span>
- <span data-ttu-id="42b25-188">**Geen** Stelt geen opties in en is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="42b25-188">**None** Sets no options and is the default.</span></span>
- <span data-ttu-id="42b25-189">**Privé** De alias is alleen beschikbaar in de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="42b25-189">**Private** The alias is available only in the current scope.</span></span>
- <span data-ttu-id="42b25-190">**Alleen-lezen** Kan alleen worden gewijzigd of verwijderd als de para meter **Forces** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="42b25-190">**ReadOnly** Cannot be changed or deleted unless the **Force** parameter is used.</span></span>
- <span data-ttu-id="42b25-191">**Niet opgegeven**</span><span class="sxs-lookup"><span data-stu-id="42b25-191">**Unspecified**</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42b25-192">-PassThru</span><span class="sxs-lookup"><span data-stu-id="42b25-192">-PassThru</span></span>

<span data-ttu-id="42b25-193">Retourneert een object dat de alias vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="42b25-193">Returns an object that represents the alias.</span></span> <span data-ttu-id="42b25-194">Gebruik een indelings-cmdlet, zoals `Format-List` om het object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="42b25-194">Use a format cmdlet such as `Format-List` to display the object.</span></span> <span data-ttu-id="42b25-195">`Set-Alias`Er wordt standaard geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="42b25-195">By default, `Set-Alias` does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42b25-196">-Bereik</span><span class="sxs-lookup"><span data-stu-id="42b25-196">-Scope</span></span>

<span data-ttu-id="42b25-197">Hiermee geeft u het bereik op waarin deze alias geldig is.</span><span class="sxs-lookup"><span data-stu-id="42b25-197">Specifies the scope in which this alias is valid.</span></span> <span data-ttu-id="42b25-198">De standaard waarde is **lokaal**.</span><span class="sxs-lookup"><span data-stu-id="42b25-198">The default value is **Local**.</span></span> <span data-ttu-id="42b25-199">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="42b25-199">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

<span data-ttu-id="42b25-200">De acceptabele waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="42b25-200">The acceptable values are as follows:</span></span>

- <span data-ttu-id="42b25-201">Globaal</span><span class="sxs-lookup"><span data-stu-id="42b25-201">Global</span></span>
- <span data-ttu-id="42b25-202">Lokaal</span><span class="sxs-lookup"><span data-stu-id="42b25-202">Local</span></span>
- <span data-ttu-id="42b25-203">Privé</span><span class="sxs-lookup"><span data-stu-id="42b25-203">Private</span></span>
- <span data-ttu-id="42b25-204">Genummerde bereiken</span><span class="sxs-lookup"><span data-stu-id="42b25-204">Numbered scopes</span></span>
- <span data-ttu-id="42b25-205">Script</span><span class="sxs-lookup"><span data-stu-id="42b25-205">Script</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42b25-206">-Waarde</span><span class="sxs-lookup"><span data-stu-id="42b25-206">-Value</span></span>

<span data-ttu-id="42b25-207">Hiermee geeft u de naam op van de cmdlet of opdracht die de alias uitvoert.</span><span class="sxs-lookup"><span data-stu-id="42b25-207">Specifies the name of the cmdlet or command that the alias runs.</span></span> <span data-ttu-id="42b25-208">De **waarde** para meter is de eigenschap **definitie** van de alias.</span><span class="sxs-lookup"><span data-stu-id="42b25-208">The **Value** parameter is the alias's **Definition** property.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="42b25-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="42b25-209">-Confirm</span></span>

<span data-ttu-id="42b25-210">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="42b25-210">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42b25-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="42b25-211">-WhatIf</span></span>

<span data-ttu-id="42b25-212">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="42b25-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="42b25-213">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="42b25-213">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="42b25-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="42b25-214">CommonParameters</span></span>

<span data-ttu-id="42b25-215">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="42b25-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="42b25-216">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="42b25-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="42b25-217">INVOER</span><span class="sxs-lookup"><span data-stu-id="42b25-217">INPUTS</span></span>

### <span data-ttu-id="42b25-218">Geen</span><span class="sxs-lookup"><span data-stu-id="42b25-218">None</span></span>

<span data-ttu-id="42b25-219">`Set-Alias` accepteert geen invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="42b25-219">`Set-Alias` does not accept input from the pipeline.</span></span>

## <span data-ttu-id="42b25-220">UITVOER</span><span class="sxs-lookup"><span data-stu-id="42b25-220">OUTPUTS</span></span>

### <span data-ttu-id="42b25-221">Geen of System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="42b25-221">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="42b25-222">Wanneer u de para meter **PassThru** gebruikt, `Set-Alias` genereert een **System. Management. Automation. AliasInfo** -object dat de alias vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="42b25-222">When you use the **PassThru** parameter, `Set-Alias` generates a **System.Management.Automation.AliasInfo** object representing the alias.</span></span> <span data-ttu-id="42b25-223">Anders `Set-Alias` wordt er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="42b25-223">Otherwise, `Set-Alias` does not generate any output.</span></span>

## <span data-ttu-id="42b25-224">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="42b25-224">NOTES</span></span>

<span data-ttu-id="42b25-225">Power shell bevat ingebouwde aliassen die beschikbaar zijn in elke Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="42b25-225">PowerShell includes built-in aliases that are available in each PowerShell session.</span></span> <span data-ttu-id="42b25-226">`Get-Alias`Met de cmdlet worden de aliassen weer gegeven die beschikbaar zijn in een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="42b25-226">The `Get-Alias` cmdlet displays the aliases available in a PowerShell session.</span></span>

<span data-ttu-id="42b25-227">Als u een alias wilt maken, gebruikt u de-cmdlets `Set-Alias` of `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="42b25-227">To create an alias, use the cmdlets `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="42b25-228">In Power shell 6 kunt u een alias verwijderen met de `Remove-Alias` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42b25-228">In PowerShell 6, to delete an alias, use the `Remove-Alias` cmdlet.</span></span> <span data-ttu-id="42b25-229">`Remove-Item` wordt geaccepteerd voor achterwaartse compatibiliteit, zoals voor scripts die zijn gemaakt met eerdere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="42b25-229">`Remove-Item` is accepted for backwards compatibility such as for scripts created with prior versions of PowerShell.</span></span> <span data-ttu-id="42b25-230">Gebruik een opdracht zoals `Remove-Item -Path Alias:aliasname` .</span><span class="sxs-lookup"><span data-stu-id="42b25-230">Use a command such as `Remove-Item -Path Alias:aliasname`.</span></span>

<span data-ttu-id="42b25-231">Als u een alias wilt maken die beschikbaar is in elke Power shell-sessie, voegt u deze toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="42b25-231">To create an alias that is available in each PowerShell session, add it to your PowerShell profile.</span></span>
<span data-ttu-id="42b25-232">Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="42b25-232">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="42b25-233">Een alias kan worden opgeslagen en opnieuw worden gebruikt in een andere Power shell-sessie door een export-en import bewerking uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="42b25-233">An alias can be saved and reused in another PowerShell session by doing an export and import.</span></span> <span data-ttu-id="42b25-234">Als u een alias wilt opslaan in een bestand, gebruikt u `Export-Alias` .</span><span class="sxs-lookup"><span data-stu-id="42b25-234">To save an alias to a file, use `Export-Alias`.</span></span> <span data-ttu-id="42b25-235">Gebruik om een opgeslagen alias toe te voegen aan een nieuwe Power shell-sessie `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="42b25-235">To add a saved alias to a new PowerShell session, use `Import-Alias`.</span></span>

## <span data-ttu-id="42b25-236">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="42b25-236">RELATED LINKS</span></span>

[<span data-ttu-id="42b25-237">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="42b25-237">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="42b25-238">about_Functions</span><span class="sxs-lookup"><span data-stu-id="42b25-238">about_Functions</span></span>](../Microsoft.PowerShell.Core/about/about_Functions.md)

[<span data-ttu-id="42b25-239">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="42b25-239">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[<span data-ttu-id="42b25-240">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="42b25-240">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[<span data-ttu-id="42b25-241">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="42b25-241">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="42b25-242">Get-alias</span><span class="sxs-lookup"><span data-stu-id="42b25-242">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="42b25-243">Import-alias</span><span class="sxs-lookup"><span data-stu-id="42b25-243">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="42b25-244">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="42b25-244">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="42b25-245">Alias verwijderen</span><span class="sxs-lookup"><span data-stu-id="42b25-245">Remove-Alias</span></span>](Remove-Alias.md)

[<span data-ttu-id="42b25-246">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="42b25-246">Remove-Item</span></span>](../Microsoft.PowerShell.Management/Remove-Item.md)

