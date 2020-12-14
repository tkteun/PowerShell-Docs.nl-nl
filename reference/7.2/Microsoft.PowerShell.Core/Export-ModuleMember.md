---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: fcb9af654f9e95f44e49ea984294b80752aa3453
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705634"
---
# <span data-ttu-id="77e11-102">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="77e11-102">Export-ModuleMember</span></span>

## <span data-ttu-id="77e11-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="77e11-103">SYNOPSIS</span></span>
<span data-ttu-id="77e11-104">Hiermee geeft u de module leden op die worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-104">Specifies the module members that are exported.</span></span>

## <span data-ttu-id="77e11-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="77e11-105">SYNTAX</span></span>

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="77e11-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="77e11-106">DESCRIPTION</span></span>

<span data-ttu-id="77e11-107">De cmdlet **export-ModuleMember** geeft de module leden op die worden geëxporteerd uit een script module bestand (. psm1) of van een dynamische module die is gemaakt met behulp van de cmdlet New-Module.</span><span class="sxs-lookup"><span data-stu-id="77e11-107">The **Export-ModuleMember** cmdlet specifies the module members that are exported from a script module (.psm1) file, or from a dynamic module created by using the New-Module cmdlet.</span></span>
<span data-ttu-id="77e11-108">Module leden bevatten cmdlets, functies, variabelen en aliassen.</span><span class="sxs-lookup"><span data-stu-id="77e11-108">Module members include cmdlets, functions, variables, and aliases.</span></span>
<span data-ttu-id="77e11-109">Deze cmdlet kan alleen worden gebruikt in een script module bestand of een dynamische module.</span><span class="sxs-lookup"><span data-stu-id="77e11-109">This cmdlet can be used only in a script module file or a dynamic module.</span></span>

<span data-ttu-id="77e11-110">Als een script module geen opdracht **export-ModuleMember** bevat, worden de functies en aliassen in de script module geëxporteerd, maar de variabelen niet.</span><span class="sxs-lookup"><span data-stu-id="77e11-110">If a script module does not include an **Export-ModuleMember** command, the functions and aliases in the script module are exported, but the variables are not.</span></span>
<span data-ttu-id="77e11-111">Wanneer een script module **export-ModuleMember** opdrachten bevat, worden alleen de leden geëxporteerd die zijn opgegeven in de **export-ModuleMember-** opdrachten.</span><span class="sxs-lookup"><span data-stu-id="77e11-111">When a script module includes **Export-ModuleMember** commands, only the members specified in the **Export-ModuleMember** commands are exported.</span></span>
<span data-ttu-id="77e11-112">U kunt ook **exporteren-ModuleMember** gebruiken om leden te onderdrukken of te exporteren die de script module uit andere modules importeert.</span><span class="sxs-lookup"><span data-stu-id="77e11-112">You can also use **Export-ModuleMember** to suppress or export members that the script module imports from other modules.</span></span>

<span data-ttu-id="77e11-113">Een **export-ModuleMember-** opdracht is optioneel, maar het is een Best Practice.</span><span class="sxs-lookup"><span data-stu-id="77e11-113">An **Export-ModuleMember** command is optional, but it is a best practice.</span></span>
<span data-ttu-id="77e11-114">Zelfs als met de opdracht de standaard waarden worden bevestigd, wordt de bedoeling van de module Auteur gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-114">Even if the command confirms the default values, it demonstrates the intention of the module author.</span></span>

## <span data-ttu-id="77e11-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="77e11-115">EXAMPLES</span></span>

### <span data-ttu-id="77e11-116">Voor beeld 1: functies en aliassen exporteren in een script module</span><span class="sxs-lookup"><span data-stu-id="77e11-116">Example 1: Export functions and aliases in a script module</span></span>

```powershell
Export-ModuleMember -Function * -Alias *
```

<span data-ttu-id="77e11-117">Met deze opdracht worden alle functies en aliassen die in de script module zijn gedefinieerd, geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-117">This command exports all the functions and aliases defined in the script module.</span></span>

### <span data-ttu-id="77e11-118">Voor beeld 2: specifieke aliassen en functies exporteren</span><span class="sxs-lookup"><span data-stu-id="77e11-118">Example 2: Export specific aliases and functions</span></span>

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

<span data-ttu-id="77e11-119">Met deze opdracht worden drie aliassen en drie functies die in de script module zijn gedefinieerd, geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-119">This command exports three aliases and three functions defined in the script module.</span></span>

<span data-ttu-id="77e11-120">U kunt deze opdracht indeling gebruiken om de namen van module leden op te geven.</span><span class="sxs-lookup"><span data-stu-id="77e11-120">You can use this command format to specify the names of module members.</span></span>

### <span data-ttu-id="77e11-121">Voor beeld 3: geen leden exporteren</span><span class="sxs-lookup"><span data-stu-id="77e11-121">Example 3: Export no members</span></span>

```powershell
Export-ModuleMember
```

<span data-ttu-id="77e11-122">Met deze opdracht geeft u op dat er geen leden die zijn gedefinieerd in de script module, worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-122">This command specifies that no members defined in the script module are exported.</span></span>

<span data-ttu-id="77e11-123">Met deze opdracht voor komt u dat de module leden worden geëxporteerd, maar niet de leden verbergen.</span><span class="sxs-lookup"><span data-stu-id="77e11-123">This command prevents the module members from being exported, but it does not hide the members.</span></span>
<span data-ttu-id="77e11-124">Gebruikers kunnen module leden lezen en kopiëren of de aanroep operator (&) gebruiken om module leden aan te roepen die niet worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-124">Users can read and copy module members or use the call operator (&) to invoke module members that are not exported.</span></span>

### <span data-ttu-id="77e11-125">Voor beeld 4: een specifieke variabele exporteren</span><span class="sxs-lookup"><span data-stu-id="77e11-125">Example 4: Export a specific variable</span></span>

```powershell
Export-ModuleMember -Variable increment
```

<span data-ttu-id="77e11-126">Met deze opdracht wordt alleen de variabele $increment van de script module geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-126">This command exports only the $increment variable from the script module.</span></span>
<span data-ttu-id="77e11-127">Er zijn geen andere leden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-127">No other members are exported.</span></span>

<span data-ttu-id="77e11-128">Als u een variabele wilt exporteren, naast het exporteren van de functies in een module, moet de opdracht **export-ModuleMember** de namen bevatten van alle functies en de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="77e11-128">If you want to export a variable, in addition to exporting the functions in a module, the **Export-ModuleMember** command must include the names of all of the functions and the name of the variable.</span></span>

### <span data-ttu-id="77e11-129">Voor beeld 5: meerdere opdrachten voor exporteren</span><span class="sxs-lookup"><span data-stu-id="77e11-129">Example 5: Multiple export commands</span></span>

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

<span data-ttu-id="77e11-130">Deze opdrachten laten zien hoe meerdere opdrachten voor **exporteren ModuleMember** worden geïnterpreteerd in een script module bestand (. psm1).</span><span class="sxs-lookup"><span data-stu-id="77e11-130">These commands show how multiple **Export-ModuleMember** commands are interpreted in a script module (.psm1) file.</span></span>

<span data-ttu-id="77e11-131">Met deze opdrachten worden drie functies en één alias gemaakt en vervolgens worden twee van de functies en de alias geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-131">These commands create three functions and one alias, and then they export two of the functions and the alias.</span></span>

<span data-ttu-id="77e11-132">Zonder de **export-ModuleMember-** opdrachten, worden alle drie de functies en de alias geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-132">Without the **Export-ModuleMember** commands, all three of the functions and the alias would be exported.</span></span>
<span data-ttu-id="77e11-133">Met de opdracht **export-ModuleMember** worden alleen de functies **New-test** en **Start-test** en de STT-alias geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-133">With the **Export-ModuleMember** commands, only the **New-Test** and **Start-Test** functions and the STT alias are exported.</span></span>

### <span data-ttu-id="77e11-134">Voor beeld 6: leden exporteren in een dynamische module</span><span class="sxs-lookup"><span data-stu-id="77e11-134">Example 6: Export members in a dynamic module</span></span>

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

<span data-ttu-id="77e11-135">Met deze opdracht wordt uitgelegd hoe u Export-ModuleMember gebruikt in een dynamische module die is gemaakt met behulp van de cmdlet **New-module** .</span><span class="sxs-lookup"><span data-stu-id="77e11-135">This command shows how to use Export-ModuleMember in a dynamic module that is created by using the **New-Module** cmdlet.</span></span>

<span data-ttu-id="77e11-136">In dit voor beeld wordt **export-ModuleMember** gebruikt om zowel de Hi-alias als de functie **SayHello** in de dynamische module te exporteren.</span><span class="sxs-lookup"><span data-stu-id="77e11-136">In this example, **Export-ModuleMember** is used to export both the Hi alias and the **SayHello** function in the dynamic module.</span></span>

### <span data-ttu-id="77e11-137">Voor beeld 7: een functie declareren en exporteren in één opdracht</span><span class="sxs-lookup"><span data-stu-id="77e11-137">Example 7: Declare and export a function in a single command</span></span>

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

<span data-ttu-id="77e11-138">Dit voor beeld bevat een functie met de naam **export** die een functie declareert of een variabele maakt, en schrijft vervolgens een `Export-ModuleMember` opdracht voor de functie of variabele.</span><span class="sxs-lookup"><span data-stu-id="77e11-138">This example includes a function named **Export** that declares a function or creates a variable, and then writes an `Export-ModuleMember` command for the function or variable.</span></span>
<span data-ttu-id="77e11-139">Hiermee kunt u een functie of variabele declareren en exporteren in één opdracht.</span><span class="sxs-lookup"><span data-stu-id="77e11-139">This lets you declare and export a function or variable in a single command.</span></span>

<span data-ttu-id="77e11-140">Als u de functie **exporteren** wilt gebruiken, neemt u deze op in de script module.</span><span class="sxs-lookup"><span data-stu-id="77e11-140">To use the **Export** function, include it in your script module.</span></span>
<span data-ttu-id="77e11-141">Als u een functie wilt exporteren, typt u `Export` voor het gereserveerde woord **Function** .</span><span class="sxs-lookup"><span data-stu-id="77e11-141">To export a function, type `Export` before the **Function** keyword.</span></span>

<span data-ttu-id="77e11-142">Als u een variabele wilt exporteren, gebruikt u de volgende indeling om de variabele te declareren en de waarde ervan in te stellen:</span><span class="sxs-lookup"><span data-stu-id="77e11-142">To export a variable, use the following format to declare the variable and set its value:</span></span>

`Export variable <variable-name> <value>`

<span data-ttu-id="77e11-143">Met de opdrachten in het voor beeld wordt de juiste indeling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="77e11-143">The commands in the example show the correct format.</span></span>
<span data-ttu-id="77e11-144">In dit voor beeld worden alleen de functie **New-test** en de variabele $interval geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-144">In this example, only the **New-Test** function and the $Interval variable are exported.</span></span>

## <span data-ttu-id="77e11-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="77e11-145">PARAMETERS</span></span>

### <span data-ttu-id="77e11-146">-Alias</span><span class="sxs-lookup"><span data-stu-id="77e11-146">-Alias</span></span>

<span data-ttu-id="77e11-147">Hiermee geeft u de aliassen op die uit het script module bestand worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-147">Specifies the aliases that are exported from the script module file.</span></span>
<span data-ttu-id="77e11-148">Voer de alias namen in.</span><span class="sxs-lookup"><span data-stu-id="77e11-148">Enter the alias names.</span></span>
<span data-ttu-id="77e11-149">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="77e11-149">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="77e11-150">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="77e11-150">-Cmdlet</span></span>

<span data-ttu-id="77e11-151">Hiermee geeft u de cmdlets op die uit het script module bestand worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-151">Specifies the cmdlets that are exported from the script module file.</span></span>
<span data-ttu-id="77e11-152">Voer de namen van de cmdlets in.</span><span class="sxs-lookup"><span data-stu-id="77e11-152">Enter the cmdlet names.</span></span>
<span data-ttu-id="77e11-153">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="77e11-153">Wildcard characters are permitted.</span></span>

<span data-ttu-id="77e11-154">U kunt geen cmdlets maken in een script module-bestand, maar met cmdlets van een binaire module naar een script module, en deze opnieuw exporteren vanuit de script module.</span><span class="sxs-lookup"><span data-stu-id="77e11-154">You cannot create cmdlets in a script module file, but you can import cmdlets from a binary module into a script module and re-export them from the script module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="77e11-155">-Functie</span><span class="sxs-lookup"><span data-stu-id="77e11-155">-Function</span></span>

<span data-ttu-id="77e11-156">Hiermee geeft u de functies op die uit het script module bestand worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-156">Specifies the functions that are exported from the script module file.</span></span>
<span data-ttu-id="77e11-157">Voer de namen van de functies in.</span><span class="sxs-lookup"><span data-stu-id="77e11-157">Enter the function names.</span></span>
<span data-ttu-id="77e11-158">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="77e11-158">Wildcard characters are permitted.</span></span>
<span data-ttu-id="77e11-159">U kunt ook de functie naam teken reeksen van de sluis naar **export-ModuleMember**.</span><span class="sxs-lookup"><span data-stu-id="77e11-159">You can also pipe function name strings to **Export-ModuleMember**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="77e11-160">-Variabele</span><span class="sxs-lookup"><span data-stu-id="77e11-160">-Variable</span></span>

<span data-ttu-id="77e11-161">Hiermee geeft u de variabelen op die uit het script module bestand worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-161">Specifies the variables that are exported from the script module file.</span></span>
<span data-ttu-id="77e11-162">Voer de namen van de variabelen in, zonder een dollar teken.</span><span class="sxs-lookup"><span data-stu-id="77e11-162">Enter the variable names, without a dollar sign.</span></span>
<span data-ttu-id="77e11-163">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="77e11-163">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="77e11-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="77e11-164">CommonParameters</span></span>

<span data-ttu-id="77e11-165">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="77e11-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="77e11-166">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="77e11-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="77e11-167">INVOER</span><span class="sxs-lookup"><span data-stu-id="77e11-167">INPUTS</span></span>

### <span data-ttu-id="77e11-168">System. String</span><span class="sxs-lookup"><span data-stu-id="77e11-168">System.String</span></span>

<span data-ttu-id="77e11-169">U kunt de functie naam reeksen naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="77e11-169">You can pipe function name strings to this cmdlet.</span></span>

## <span data-ttu-id="77e11-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="77e11-170">OUTPUTS</span></span>

### <span data-ttu-id="77e11-171">Geen</span><span class="sxs-lookup"><span data-stu-id="77e11-171">None</span></span>

<span data-ttu-id="77e11-172">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="77e11-172">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="77e11-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="77e11-173">NOTES</span></span>

* <span data-ttu-id="77e11-174">Als u een lid wilt uitsluiten van de lijst met geëxporteerde leden, voegt u een opdracht **export-ModuleMember** toe met een lijst met alle andere leden, maar laat u het lid dat u wilt uitsluiten.</span><span class="sxs-lookup"><span data-stu-id="77e11-174">To exclude a member from the list of exported members, add an **Export-ModuleMember** command that lists all other members but omits the member that you want to exclude.</span></span>

## <span data-ttu-id="77e11-175">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="77e11-175">RELATED LINKS</span></span>

[<span data-ttu-id="77e11-176">Get-module</span><span class="sxs-lookup"><span data-stu-id="77e11-176">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="77e11-177">Import-module</span><span class="sxs-lookup"><span data-stu-id="77e11-177">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="77e11-178">Remove-module</span><span class="sxs-lookup"><span data-stu-id="77e11-178">Remove-Module</span></span>](Remove-Module.md)

