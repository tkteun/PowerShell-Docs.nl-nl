---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: 2c82c898dd4043d55d708eb30929580a91389845
ms.sourcegitcommit: c91f79576bc54e162bcc7adf78026417b2776687
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274288"
---
# <span data-ttu-id="5f7fa-102">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="5f7fa-102">Set-Alias</span></span>

## <span data-ttu-id="5f7fa-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="5f7fa-103">Synopsis</span></span>
<span data-ttu-id="5f7fa-104">Hiermee maakt of wijzigt u een alias voor een cmdlet of een andere opdracht in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-104">Creates or changes an alias for a cmdlet or other command in the current PowerShell session.</span></span>

## <span data-ttu-id="5f7fa-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5f7fa-105">Syntax</span></span>

### <span data-ttu-id="5f7fa-106">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="5f7fa-106">Default (Default)</span></span>

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5f7fa-107">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5f7fa-107">Description</span></span>

<span data-ttu-id="5f7fa-108">De `Set-Alias` cmdlet maakt of wijzigt een alias voor een cmdlet of een opdracht, zoals een functie, script, bestand of ander uitvoerbaar bestand.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-108">The `Set-Alias` cmdlet creates or changes an alias for a cmdlet or a command, such as a function, script, file, or other executable.</span></span> <span data-ttu-id="5f7fa-109">Een alias is een alternatieve naam die verwijst naar een cmdlet of opdracht.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-109">An alias is an alternate name that refers to a cmdlet or command.</span></span>
<span data-ttu-id="5f7fa-110">`sal`Is bijvoorbeeld de alias voor de `Set-Alias` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-110">For example, `sal` is the alias for the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="5f7fa-111">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-111">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="5f7fa-112">Een cmdlet kan meerdere aliassen hebben, maar een alias kan slechts aan één cmdlet worden gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-112">A cmdlet can have multiple aliases, but an alias can only be associated with one cmdlet.</span></span> <span data-ttu-id="5f7fa-113">U kunt gebruiken `Set-Alias` om een bestaande alias opnieuw toe te wijzen aan een andere cmdlet of de eigenschappen van een alias te wijzigen, zoals de beschrijving.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-113">You can use `Set-Alias` to reassign an existing alias to another cmdlet, or change an alias's properties, such as the description.</span></span>

<span data-ttu-id="5f7fa-114">Een alias die is gemaakt of gewijzigd door `Set-Alias` is niet permanent en is alleen beschikbaar tijdens de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-114">An alias that is created or changed by `Set-Alias` is not permanent and is only available during the current PowerShell session.</span></span> <span data-ttu-id="5f7fa-115">Wanneer de Power shell-sessie is gesloten, wordt de alias verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-115">When the PowerShell session is closed, the alias is removed.</span></span>

## <span data-ttu-id="5f7fa-116">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="5f7fa-116">Examples</span></span>

### <span data-ttu-id="5f7fa-117">Voor beeld 1: een alias maken voor een cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f7fa-117">Example 1: Create an alias for a cmdlet</span></span>

<span data-ttu-id="5f7fa-118">Met deze opdracht maakt u een alias voor een cmdlet in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-118">This command creates an alias to a cmdlet in the current PowerShell session.</span></span>

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

<span data-ttu-id="5f7fa-119">`Set-Alias`Met de cmdlet maakt u een alias in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-119">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="5f7fa-120">Met de para meter **name** wordt de naam van de alias opgegeven, `list` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-120">The **Name** parameter specifies the alias's name, `list`.</span></span> <span data-ttu-id="5f7fa-121">De **waarde** para meter geeft u de cmdlet op die de alias uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-121">The **Value** parameter specifies the cmdlet that the alias runs.</span></span>

<span data-ttu-id="5f7fa-122">Als u de alias wilt uitvoeren, typt u `list` op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-122">To run the alias, type `list` on the PowerShell command line.</span></span>

### <span data-ttu-id="5f7fa-123">Voor beeld 2: een bestaande alias opnieuw toewijzen aan een andere cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f7fa-123">Example 2: Reassign an existing alias to a different cmdlet</span></span>

<span data-ttu-id="5f7fa-124">Met deze opdracht wordt een bestaande alias opnieuw toegewezen om een andere cmdlet uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-124">This command reassigns an existing alias to run a different cmdlet.</span></span>

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

<span data-ttu-id="5f7fa-125">De `Get-Alias` cmdlet gebruikt de para meter **name** om de alias weer te geven `list` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-125">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="5f7fa-126">De `list` alias is gekoppeld aan de `Get-ChildItem` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-126">The `list` alias is associated with the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="5f7fa-127">Wanneer de `list` alias wordt uitgevoerd, worden de items in de huidige map weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-127">When the `list` alias is run, the items in the current directory are displayed.</span></span>

<span data-ttu-id="5f7fa-128">De `Set-Alias` cmdlet gebruikt de para meter **name** om de alias op te geven `list` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-128">The `Set-Alias` cmdlet uses the **Name** parameter to specify the `list` alias.</span></span> <span data-ttu-id="5f7fa-129">De **waarde** para meter koppelt de alias aan de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-129">The **Value** parameter associates the alias to the `Get-Location` cmdlet.</span></span>

<span data-ttu-id="5f7fa-130">De `Get-Alias` cmdlet gebruikt de para meter **name** om de alias weer te geven `list` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-130">The `Get-Alias` cmdlet uses the **Name** parameter to display the `list` alias.</span></span> <span data-ttu-id="5f7fa-131">De `list` alias is gekoppeld aan de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-131">The `list` alias is associated with the `Get-Location` cmdlet.</span></span> <span data-ttu-id="5f7fa-132">Wanneer de `list` alias wordt uitgevoerd, wordt de locatie van de huidige map weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-132">When the `list` alias is run, the current directory's location is displayed.</span></span>

### <span data-ttu-id="5f7fa-133">Voor beeld 3: een alleen-lezen-alias maken en wijzigen</span><span class="sxs-lookup"><span data-stu-id="5f7fa-133">Example 3: Create and change a read-only alias</span></span>

<span data-ttu-id="5f7fa-134">Met deze opdracht maakt u een alias met het kenmerk alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-134">This command creates a read-only alias.</span></span> <span data-ttu-id="5f7fa-135">De alleen-lezen optie voor komt onbedoelde wijzigingen aan een alias.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-135">The read-only option prevents unintended changes to an alias.</span></span> <span data-ttu-id="5f7fa-136">Als u een alleen-lezen alias wilt wijzigen of verwijderen, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-136">To change or delete a read-only alias, use the **Force** parameter.</span></span>

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

<span data-ttu-id="5f7fa-137">`Set-Alias`Met de cmdlet maakt u een alias in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-137">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="5f7fa-138">Met de para meter **name** wordt de naam van de alias opgegeven, `loc` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-138">The **Name** parameter specifies the alias's name, `loc`.</span></span> <span data-ttu-id="5f7fa-139">De **waarde** para meter geeft u de `Get-Location` cmdlet op die de alias uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-139">The **Value** parameter specifies the `Get-Location` cmdlet that the alias runs.</span></span> <span data-ttu-id="5f7fa-140">Met de para meter **Option** wordt de waarde **ReadOnly** opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-140">The **Option** parameter specifies the **ReadOnly** value.</span></span> <span data-ttu-id="5f7fa-141">De para meter **PassThru** vertegenwoordigt het alias object en stuurt het object omlaag in de pijp lijn naar de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-141">The **PassThru** parameter represents the alias object and sends the object down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="5f7fa-142">`Format-List` gebruikt de **eigenschaps** parameter met een asterisk ( `*` ), zodat alle eigenschappen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-142">`Format-List` uses the **Property** parameter with an asterisk (`*`) so that all of the properties are displayed.</span></span> <span data-ttu-id="5f7fa-143">In de voorbeeld uitvoer ziet u een gedeeltelijke lijst met die eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-143">The example output shows a partial list of those properties.</span></span>

<span data-ttu-id="5f7fa-144">De `loc` alias wordt gewijzigd met de toevoeging van twee para meters.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-144">The `loc` alias is changed with the addition of two parameters.</span></span> <span data-ttu-id="5f7fa-145">**Beschrijving** voegt tekst toe om het doel van de alias te verklaren.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-145">**Description** adds text to explain the alias's purpose.</span></span> <span data-ttu-id="5f7fa-146">De para meter **Force** is vereist omdat de `loc` alias alleen-lezen is.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-146">The **Force** parameter is needed because the `loc` alias is read-only.</span></span> <span data-ttu-id="5f7fa-147">Als de para meter **Forces** niet wordt gebruikt, mislukt de wijziging.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-147">If the **Force** parameter is not used, the change fails.</span></span>

### <span data-ttu-id="5f7fa-148">Voor beeld 4: een alias maken voor een uitvoerbaar bestand</span><span class="sxs-lookup"><span data-stu-id="5f7fa-148">Example 4: Create an alias to an executable file</span></span>

<span data-ttu-id="5f7fa-149">In dit voor beeld wordt een alias gemaakt voor een uitvoerbaar bestand op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-149">This example creates an alias to an executable file on the local computer.</span></span>

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

<span data-ttu-id="5f7fa-150">`Set-Alias`Met de cmdlet maakt u een alias in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-150">The `Set-Alias` cmdlet creates an alias in the current PowerShell session.</span></span> <span data-ttu-id="5f7fa-151">Met de para meter **name** wordt de naam van de alias opgegeven, `np` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-151">The **Name** parameter specifies the alias's name, `np`.</span></span> <span data-ttu-id="5f7fa-152">De **waarde** para meter geeft u het pad en de naam van de toepassing op **C:\Windows\notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-152">The **Value** parameter specifies the path and application name **C:\Windows\notepad.exe**.</span></span> <span data-ttu-id="5f7fa-153">De `Get-Alias` cmdlet gebruikt de para meter **name** om aan te geven dat de `np` alias is gekoppeld aan **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-153">The `Get-Alias` cmdlet uses the **Name** parameter to show that the `np` alias is associated with **notepad.exe**.</span></span>

<span data-ttu-id="5f7fa-154">Als u de alias wilt uitvoeren, typt `np` u op de Power shell-opdracht regel om **notepad.exe** te openen.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-154">To run the alias, type `np` on the PowerShell command line to open **notepad.exe**.</span></span>

### <span data-ttu-id="5f7fa-155">Voor beeld 5: een alias maken voor een opdracht met para meters</span><span class="sxs-lookup"><span data-stu-id="5f7fa-155">Example 5: Create an alias for a command with parameters</span></span>

<span data-ttu-id="5f7fa-156">In dit voor beeld ziet u hoe u een alias toewijst aan een opdracht met para meters.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-156">This example shows how to assign an alias to a command with parameters.</span></span>

<span data-ttu-id="5f7fa-157">U kunt een alias voor een cmdlet maken, zoals `Set-Location` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-157">You can create an alias for a cmdlet, such as `Set-Location`.</span></span> <span data-ttu-id="5f7fa-158">U kunt geen alias maken voor een opdracht met para meters en waarden, zoals `Set-Location -Path C:\Windows\System32` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-158">You cannot create an alias for a command with parameters and values, such as `Set-Location -Path C:\Windows\System32`.</span></span> <span data-ttu-id="5f7fa-159">Als u een alias voor een opdracht wilt maken, maakt u een functie die de opdracht bevat en maakt u vervolgens een alias voor de functie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-159">To create an alias for a command, create a function that includes the command, and then create an alias to the function.</span></span> <span data-ttu-id="5f7fa-160">Zie [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-160">For more information, see [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).</span></span>

```
Function CD32 {Set-Location -Path C:\Windows\System32}

Set-Alias -Name Go -Value CD32
```

<span data-ttu-id="5f7fa-161">Er wordt een functie gemaakt met de naam `CD32` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-161">A function named `CD32` is created.</span></span> <span data-ttu-id="5f7fa-162">De functie gebruikt de `Set-Location` cmdlet met de para meter **Path** om de map op te geven `C:\Windows\System32` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-162">The function uses the `Set-Location` cmdlet with the **Path** parameter to specify the directory, `C:\Windows\System32`.</span></span>

<span data-ttu-id="5f7fa-163">De `Set-Alias` cmdlet maakt een alias voor de functie in de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-163">The `Set-Alias` cmdlet creates an alias to the function in the current PowerShell session.</span></span> <span data-ttu-id="5f7fa-164">Met de para meter **name** wordt de naam van de alias opgegeven, `Go` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-164">The **Name** parameter specifies the alias's name, `Go`.</span></span> <span data-ttu-id="5f7fa-165">De **waarde** para meter geeft u de naam van de functie op `CD32` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-165">The **Value** parameter specifies the function's name, `CD32`.</span></span>

<span data-ttu-id="5f7fa-166">Als u de alias wilt uitvoeren, typt u `Go` op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-166">To run the alias, type `Go` on the PowerShell command line.</span></span> <span data-ttu-id="5f7fa-167">De `CD32` functie wordt uitgevoerd en de map wordt gewijzigd `C:\Windows\System32` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-167">The `CD32` function runs and changes to the directory `C:\Windows\System32`.</span></span>

### <span data-ttu-id="5f7fa-168">Voor beeld 6: opties voor een bestaande alias bijwerken</span><span class="sxs-lookup"><span data-stu-id="5f7fa-168">Example 6: Update options for an existing alias</span></span>

<span data-ttu-id="5f7fa-169">In dit voor beeld ziet u hoe u meerdere opties toewijst met behulp van de para meter **Option** .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-169">This example shows how to assign multiple options using the **Option** parameter.</span></span>

<span data-ttu-id="5f7fa-170">In het bovenstaande voor beeld wordt de alias ingesteld `Go` als `ReadOnly` en `Private` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-170">Using the example above we will set the alias `Go` as `ReadOnly` and `Private`.</span></span>

```powershell
Set-Alias -Name Go -Option ReadOnly, Private
```

<span data-ttu-id="5f7fa-171">De alias `Go` moet al bestaan.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-171">The alias `Go` should already exist.</span></span> <span data-ttu-id="5f7fa-172">Nadat u de bovenstaande opdracht hebt uitgevoerd, kan de alias niet worden gewijzigd zonder de para meter **Force** te gebruiken en alleen beschikbaar is in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-172">After running the command above, the alias is not be able to be changed without using the **Force** parameter and is only available in the current scope.</span></span>

## <span data-ttu-id="5f7fa-173">Parameters</span><span class="sxs-lookup"><span data-stu-id="5f7fa-173">Parameters</span></span>

### <span data-ttu-id="5f7fa-174">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5f7fa-174">-Description</span></span>

<span data-ttu-id="5f7fa-175">Hiermee geeft u een beschrijving van de alias.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-175">Specifies a description of the alias.</span></span> <span data-ttu-id="5f7fa-176">U kunt een wille keurige teken reeks typen.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-176">You can type any string.</span></span> <span data-ttu-id="5f7fa-177">Als de beschrijving spaties bevat, plaatst u deze enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-177">If the description includes spaces, enclose it single quotation marks.</span></span>

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

### <span data-ttu-id="5f7fa-178">-Force</span><span class="sxs-lookup"><span data-stu-id="5f7fa-178">-Force</span></span>

<span data-ttu-id="5f7fa-179">Gebruik de para meter **Force** om een alias te wijzigen of te verwijderen waarvoor de **optie** parameter is ingesteld op **ReadOnly**.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-179">Use the **Force** parameter to change or delete an alias that has the **Option** parameter set to **ReadOnly**.</span></span>

<span data-ttu-id="5f7fa-180">De para meter **Force** kan geen alias wijzigen of verwijderen met de para meter **Option** ingesteld op **constant**.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-180">The **Force** parameter cannot change or delete an alias with the **Option** parameter set to **Constant**.</span></span>

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

### <span data-ttu-id="5f7fa-181">-Name</span><span class="sxs-lookup"><span data-stu-id="5f7fa-181">-Name</span></span>

<span data-ttu-id="5f7fa-182">Hiermee geeft u de naam van een nieuwe alias.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-182">Specifies the name of a new alias.</span></span> <span data-ttu-id="5f7fa-183">Een alias naam mag alfanumerieke tekens en afbreek streepjes bevatten.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-183">An alias name can contain alphanumeric characters and hyphens.</span></span> <span data-ttu-id="5f7fa-184">Alias namen mogen niet numeriek zijn, zoals 123.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-184">Alias names cannot be numeric, such as 123.</span></span>

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

### <span data-ttu-id="5f7fa-185">-Optie</span><span class="sxs-lookup"><span data-stu-id="5f7fa-185">-Option</span></span>

<span data-ttu-id="5f7fa-186">Hiermee stelt u de waarde van de **optie** eigenschap van de alias.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-186">Sets the **Option** property value of the alias.</span></span> <span data-ttu-id="5f7fa-187">Waarden zoals `ReadOnly` en `Constant` beveiligen een alias tegen onbedoelde wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-187">Values such as `ReadOnly` and `Constant` protect an alias from unintended changes.</span></span> <span data-ttu-id="5f7fa-188">Als u de **optie** -eigenschap van alle aliassen in de sessie wilt weer geven, typt u `Get-Alias | Format-Table -Property Name, Options -Autosize` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-188">To see the **Option** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -Autosize`.</span></span>

<span data-ttu-id="5f7fa-189">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="5f7fa-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="5f7fa-190">`AllScope` -De alias wordt gekopieerd naar een nieuwe scope die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-190">`AllScope` - The alias is copied to any new scopes that are created.</span></span>
- <span data-ttu-id="5f7fa-191">`Constant` -Kan niet worden gewijzigd of verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-191">`Constant` - Cannot be changed or deleted.</span></span>
- <span data-ttu-id="5f7fa-192">`None` -Geen opties instellen en is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-192">`None` - Sets no options and is the default.</span></span>
- <span data-ttu-id="5f7fa-193">`Private` -De alias is alleen beschikbaar in de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-193">`Private` - The alias is available only in the current scope.</span></span>
- <span data-ttu-id="5f7fa-194">`ReadOnly` -Kan alleen worden gewijzigd of verwijderd als de para meter **Forces** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-194">`ReadOnly` - Cannot be changed or deleted unless the **Force** parameter is used.</span></span>
- `Unspecified`

<span data-ttu-id="5f7fa-195">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-195">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="5f7fa-196">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-196">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="5f7fa-197">De waarden kunnen worden door gegeven aan de para meter **Option** als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-197">The values can be passed to the **Option** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="5f7fa-198">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-198">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="5f7fa-199">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-199">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span>

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

### <span data-ttu-id="5f7fa-200">-PassThru</span><span class="sxs-lookup"><span data-stu-id="5f7fa-200">-PassThru</span></span>

<span data-ttu-id="5f7fa-201">Retourneert een object dat de alias vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-201">Returns an object that represents the alias.</span></span> <span data-ttu-id="5f7fa-202">Gebruik een indelings-cmdlet, zoals `Format-List` om het object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-202">Use a format cmdlet such as `Format-List` to display the object.</span></span> <span data-ttu-id="5f7fa-203">`Set-Alias`Er wordt standaard geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-203">By default, `Set-Alias` does not generate any output.</span></span>

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

### <span data-ttu-id="5f7fa-204">-Bereik</span><span class="sxs-lookup"><span data-stu-id="5f7fa-204">-Scope</span></span>

<span data-ttu-id="5f7fa-205">Hiermee geeft u het bereik op waarin deze alias geldig is.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-205">Specifies the scope in which this alias is valid.</span></span> <span data-ttu-id="5f7fa-206">De standaard waarde is **lokaal**.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-206">The default value is **Local**.</span></span> <span data-ttu-id="5f7fa-207">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-207">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

<span data-ttu-id="5f7fa-208">De acceptabele waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="5f7fa-208">The acceptable values are as follows:</span></span>

- <span data-ttu-id="5f7fa-209">Globaal</span><span class="sxs-lookup"><span data-stu-id="5f7fa-209">Global</span></span>
- <span data-ttu-id="5f7fa-210">Lokaal</span><span class="sxs-lookup"><span data-stu-id="5f7fa-210">Local</span></span>
- <span data-ttu-id="5f7fa-211">Persoonlijk</span><span class="sxs-lookup"><span data-stu-id="5f7fa-211">Private</span></span>
- <span data-ttu-id="5f7fa-212">Genummerde bereiken</span><span class="sxs-lookup"><span data-stu-id="5f7fa-212">Numbered scopes</span></span>
- <span data-ttu-id="5f7fa-213">Script</span><span class="sxs-lookup"><span data-stu-id="5f7fa-213">Script</span></span>

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

### <span data-ttu-id="5f7fa-214">-Waarde</span><span class="sxs-lookup"><span data-stu-id="5f7fa-214">-Value</span></span>

<span data-ttu-id="5f7fa-215">Hiermee geeft u de naam op van de cmdlet of opdracht die de alias uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-215">Specifies the name of the cmdlet or command that the alias runs.</span></span> <span data-ttu-id="5f7fa-216">De **waarde** para meter is de eigenschap **definitie** van de alias.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-216">The **Value** parameter is the alias's **Definition** property.</span></span>

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

### <span data-ttu-id="5f7fa-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5f7fa-217">-Confirm</span></span>

<span data-ttu-id="5f7fa-218">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5f7fa-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5f7fa-219">-WhatIf</span></span>

<span data-ttu-id="5f7fa-220">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-220">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5f7fa-221">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5f7fa-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f7fa-222">CommonParameters</span></span>

<span data-ttu-id="5f7fa-223">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f7fa-224">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f7fa-225">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="5f7fa-225">Inputs</span></span>

### <span data-ttu-id="5f7fa-226">Geen</span><span class="sxs-lookup"><span data-stu-id="5f7fa-226">None</span></span>

<span data-ttu-id="5f7fa-227">`Set-Alias` accepteert geen invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-227">`Set-Alias` does not accept input from the pipeline.</span></span>

## <span data-ttu-id="5f7fa-228">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="5f7fa-228">Outputs</span></span>

### <span data-ttu-id="5f7fa-229">Geen of System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="5f7fa-229">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="5f7fa-230">Wanneer u de para meter **PassThru** gebruikt, `Set-Alias` genereert een **System. Management. Automation. AliasInfo** -object dat de alias vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-230">When you use the **PassThru** parameter, `Set-Alias` generates a **System.Management.Automation.AliasInfo** object representing the alias.</span></span> <span data-ttu-id="5f7fa-231">Anders `Set-Alias` wordt er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-231">Otherwise, `Set-Alias` does not generate any output.</span></span>

## <span data-ttu-id="5f7fa-232">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5f7fa-232">NOTES</span></span>

<span data-ttu-id="5f7fa-233">Power shell bevat ingebouwde aliassen die beschikbaar zijn in elke Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-233">PowerShell includes built-in aliases that are available in each PowerShell session.</span></span> <span data-ttu-id="5f7fa-234">`Get-Alias`Met de cmdlet worden de aliassen weer gegeven die beschikbaar zijn in een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-234">The `Get-Alias` cmdlet displays the aliases available in a PowerShell session.</span></span>

<span data-ttu-id="5f7fa-235">Als u een alias wilt maken, gebruikt u de-cmdlets `Set-Alias` of `New-Alias` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-235">To create an alias, use the cmdlets `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="5f7fa-236">In Power shell 6 kunt u een alias verwijderen met de `Remove-Alias` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-236">In PowerShell 6, to delete an alias, use the `Remove-Alias` cmdlet.</span></span> <span data-ttu-id="5f7fa-237">`Remove-Item` wordt geaccepteerd voor achterwaartse compatibiliteit, zoals voor scripts die zijn gemaakt met eerdere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-237">`Remove-Item` is accepted for backwards compatibility such as for scripts created with prior versions of PowerShell.</span></span> <span data-ttu-id="5f7fa-238">Gebruik een opdracht zoals `Remove-Item -Path Alias:aliasname` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-238">Use a command such as `Remove-Item -Path Alias:aliasname`.</span></span>

<span data-ttu-id="5f7fa-239">Als u een alias wilt maken die beschikbaar is in elke Power shell-sessie, voegt u deze toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-239">To create an alias that is available in each PowerShell session, add it to your PowerShell profile.</span></span>
<span data-ttu-id="5f7fa-240">Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-240">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="5f7fa-241">Een alias kan worden opgeslagen en opnieuw worden gebruikt in een andere Power shell-sessie door een export-en import bewerking uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5f7fa-241">An alias can be saved and reused in another PowerShell session by doing an export and import.</span></span> <span data-ttu-id="5f7fa-242">Als u een alias wilt opslaan in een bestand, gebruikt u `Export-Alias` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-242">To save an alias to a file, use `Export-Alias`.</span></span> <span data-ttu-id="5f7fa-243">Gebruik om een opgeslagen alias toe te voegen aan een nieuwe Power shell-sessie `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="5f7fa-243">To add a saved alias to a new PowerShell session, use `Import-Alias`.</span></span>

## <span data-ttu-id="5f7fa-244">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5f7fa-244">RELATED LINKS</span></span>

[<span data-ttu-id="5f7fa-245">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="5f7fa-245">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="5f7fa-246">about_Functions</span><span class="sxs-lookup"><span data-stu-id="5f7fa-246">about_Functions</span></span>](../Microsoft.PowerShell.Core/about/about_Functions.md)

[<span data-ttu-id="5f7fa-247">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="5f7fa-247">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[<span data-ttu-id="5f7fa-248">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="5f7fa-248">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[<span data-ttu-id="5f7fa-249">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="5f7fa-249">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="5f7fa-250">Get-alias</span><span class="sxs-lookup"><span data-stu-id="5f7fa-250">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="5f7fa-251">Import-alias</span><span class="sxs-lookup"><span data-stu-id="5f7fa-251">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="5f7fa-252">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="5f7fa-252">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="5f7fa-253">Alias verwijderen</span><span class="sxs-lookup"><span data-stu-id="5f7fa-253">Remove-Alias</span></span>](Remove-Alias.md)

[<span data-ttu-id="5f7fa-254">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="5f7fa-254">Remove-Item</span></span>](../Microsoft.PowerShell.Management/Remove-Item.md)

