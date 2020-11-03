---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: f915a5741ed5c63206da3c35f5322508515bd566
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250191"
---
# <span data-ttu-id="d237d-103">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="d237d-103">Invoke-Expression</span></span>

## <span data-ttu-id="d237d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d237d-104">SYNOPSIS</span></span>
<span data-ttu-id="d237d-105">Voert opdrachten of expressies uit op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d237d-105">Runs commands or expressions on the local computer.</span></span>

## <span data-ttu-id="d237d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d237d-106">SYNTAX</span></span>

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## <span data-ttu-id="d237d-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d237d-107">DESCRIPTION</span></span>

<span data-ttu-id="d237d-108">De `Invoke-Expression` cmdlet evalueert of voert een opgegeven teken reeks als een opdracht en retourneert de resultaten van de expressie of opdracht.</span><span class="sxs-lookup"><span data-stu-id="d237d-108">The `Invoke-Expression` cmdlet evaluates or runs a specified string as a command and returns the results of the expression or command.</span></span> <span data-ttu-id="d237d-109">Zonder `Invoke-Expression` , wordt een teken reeks die is verzonden op de opdracht regel, ongewijzigd geretourneerd (geechod).</span><span class="sxs-lookup"><span data-stu-id="d237d-109">Without `Invoke-Expression`, a string submitted at the command line is returned (echoed) unchanged.</span></span>

<span data-ttu-id="d237d-110">Expressies worden geëvalueerd en uitgevoerd in de huidige scope.</span><span class="sxs-lookup"><span data-stu-id="d237d-110">Expressions are evaluated and run in the current scope.</span></span> <span data-ttu-id="d237d-111">Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d237d-111">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="d237d-112">Zorg voor redelijke voorzorgsmaatregelen bij het gebruik `Invoke-Expression` van de cmdlet in scripts.</span><span class="sxs-lookup"><span data-stu-id="d237d-112">Take reasonable precautions when using the `Invoke-Expression` cmdlet in scripts.</span></span> <span data-ttu-id="d237d-113">Wanneer u gebruikt `Invoke-Expression` om een opdracht uit te voeren die door de gebruiker wordt ingevoerd, controleert u of de opdracht veilig is om uit te voeren voordat deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d237d-113">When using `Invoke-Expression` to run a command that the user enters, verify that the command is safe to run before running it.</span></span> <span data-ttu-id="d237d-114">Over het algemeen kunt u het script het beste ontwerpen met vooraf gedefinieerde invoer opties, in plaats van vrije-vorm invoer toe te staan.</span><span class="sxs-lookup"><span data-stu-id="d237d-114">In general, it is best to design your script with predefined input options, rather than allowing freeform input.</span></span>

## <span data-ttu-id="d237d-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d237d-115">EXAMPLES</span></span>

### <span data-ttu-id="d237d-116">Voor beeld 1: een expressie evalueren</span><span class="sxs-lookup"><span data-stu-id="d237d-116">Example 1: Evaluate an expression</span></span>

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

<span data-ttu-id="d237d-117">In dit voor beeld ziet u hoe `Invoke-Expression` u een expressie kunt evalueren.</span><span class="sxs-lookup"><span data-stu-id="d237d-117">This example demonstrates the use of `Invoke-Expression` to evaluate an expression.</span></span> <span data-ttu-id="d237d-118">Zonder `Invoke-Expression` , de expressie wordt afgedrukt, maar niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="d237d-118">Without `Invoke-Expression`, the expression is printed, but not evaluated.</span></span>

<span data-ttu-id="d237d-119">Met de eerste opdracht wordt een waarde van `Get-Process` (een teken reeks) toegewezen aan de `$Command` variabele.</span><span class="sxs-lookup"><span data-stu-id="d237d-119">The first command assigns a value of `Get-Process` (a string) to the `$Command` variable.</span></span>

<span data-ttu-id="d237d-120">Met de tweede opdracht wordt het effect van het typen van de naam van de variabele op de opdracht regel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d237d-120">The second command shows the effect of typing the variable name at the command line.</span></span> <span data-ttu-id="d237d-121">Power shell Echos de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="d237d-121">PowerShell echoes the string.</span></span>

<span data-ttu-id="d237d-122">De derde opdracht wordt gebruikt `Invoke-Expression` om de teken reeks te evalueren.</span><span class="sxs-lookup"><span data-stu-id="d237d-122">The third command uses `Invoke-Expression` to evaluate the string.</span></span>

### <span data-ttu-id="d237d-123">Voor beeld 2: een script uitvoeren op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="d237d-123">Example 2: Run a script on the local computer</span></span>

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

<span data-ttu-id="d237d-124">Deze opdrachten gebruiken `Invoke-Expression` om een script, TestScript.ps1, uit te voeren op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d237d-124">These commands use `Invoke-Expression` to run a script, TestScript.ps1, on the local computer.</span></span> <span data-ttu-id="d237d-125">De twee opdrachten zijn gelijk.</span><span class="sxs-lookup"><span data-stu-id="d237d-125">The two commands are equivalent.</span></span> <span data-ttu-id="d237d-126">De eerste gebruikt de **opdracht** parameter om op te geven welke opdracht moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d237d-126">The first uses the **Command** parameter to specify the command to run.</span></span>
<span data-ttu-id="d237d-127">De tweede gebruikt een pijplijn operator ( `|` ) om de opdracht teken reeks naar te verzenden `Invoke-Expression` .</span><span class="sxs-lookup"><span data-stu-id="d237d-127">The second uses a pipeline operator (`|`) to send the command string to `Invoke-Expression`.</span></span>

### <span data-ttu-id="d237d-128">Voor beeld 3: een opdracht uitvoeren in een variabele</span><span class="sxs-lookup"><span data-stu-id="d237d-128">Example 3: Run a command in a variable</span></span>

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

<span data-ttu-id="d237d-129">In dit voor beeld wordt een opdracht reeks uitgevoerd die is opgeslagen in de `$Command` variabele.</span><span class="sxs-lookup"><span data-stu-id="d237d-129">This example runs a command string that is saved in the `$Command` variable.</span></span>

<span data-ttu-id="d237d-130">De opdracht teken reeks staat tussen enkele aanhalings tekens, omdat deze een variabele bevat, `$_` waarmee het huidige object wordt aangeduid.</span><span class="sxs-lookup"><span data-stu-id="d237d-130">The command string is enclosed in single quotation marks because it includes a variable, `$_`, which represents the current object.</span></span> <span data-ttu-id="d237d-131">Als deze tussen dubbele aanhalings tekens is geplaatst, wordt de `$_` variabele vervangen door de waarde voordat deze is opgeslagen in de `$Command` variabele.</span><span class="sxs-lookup"><span data-stu-id="d237d-131">If it were enclosed in double quotation marks, the `$_` variable would be replaced by its value before it was saved in the `$Command` variable.</span></span>

### <span data-ttu-id="d237d-132">Voor beeld 4: een Help-voor beeld van cmdlet ophalen en uitvoeren</span><span class="sxs-lookup"><span data-stu-id="d237d-132">Example 4: Get and run a cmdlet Help example</span></span>

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

<span data-ttu-id="d237d-133">Met deze opdracht wordt het eerste voor beeld in het Help-onderwerp van de cmdlet opgehaald en uitgevoerd `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="d237d-133">This command retrieves and runs the first example in the `Get-EventLog` cmdlet Help topic.</span></span>

<span data-ttu-id="d237d-134">Als u een voor beeld van een andere cmdlet wilt uitvoeren, wijzigt u de waarde van de `$Cmdlet_name` variabele in de naam van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d237d-134">To run an example of a different cmdlet, change the value of the `$Cmdlet_name` variable to the name of the cmdlet.</span></span> <span data-ttu-id="d237d-135">En wijzig de `$Example_number` variabele in het voorbeeld nummer dat u wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="d237d-135">And, change the `$Example_number` variable to the example number you want to run.</span></span> <span data-ttu-id="d237d-136">De opdracht mislukt als het voorbeeld nummer ongeldig is.</span><span class="sxs-lookup"><span data-stu-id="d237d-136">The command fails if the example number is not valid.</span></span>

## <span data-ttu-id="d237d-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d237d-137">PARAMETERS</span></span>

### <span data-ttu-id="d237d-138">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="d237d-138">-Command</span></span>

<span data-ttu-id="d237d-139">Hiermee geeft u de opdracht of expressie op die moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d237d-139">Specifies the command or expression to run.</span></span> <span data-ttu-id="d237d-140">Typ de opdracht of expressie of voer een variabele in die de opdracht of expressie bevat.</span><span class="sxs-lookup"><span data-stu-id="d237d-140">Type the command or expression or enter a variable that contains the command or expression.</span></span> <span data-ttu-id="d237d-141">De **opdracht** parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="d237d-141">The **Command** parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d237d-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d237d-142">CommonParameters</span></span>

<span data-ttu-id="d237d-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d237d-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d237d-144">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d237d-144">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d237d-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="d237d-145">INPUTS</span></span>

### <span data-ttu-id="d237d-146">System. String of PSObject</span><span class="sxs-lookup"><span data-stu-id="d237d-146">System.String or PSObject</span></span>

<span data-ttu-id="d237d-147">U kunt een object dat de opdracht vertegenwoordigt door sluizen naar `Invoke-Expression` .</span><span class="sxs-lookup"><span data-stu-id="d237d-147">You can pipe an object that represents the command to `Invoke-Expression`.</span></span>
<span data-ttu-id="d237d-148">Gebruik de `$Input` Automatische variabele om de invoer objecten in de opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d237d-148">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="d237d-149">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d237d-149">OUTPUTS</span></span>

### <span data-ttu-id="d237d-150">PSObject</span><span class="sxs-lookup"><span data-stu-id="d237d-150">PSObject</span></span>

<span data-ttu-id="d237d-151">Retourneert de uitvoer die wordt gegenereerd door de aangeroepen opdracht (de waarde van de **opdracht** parameter).</span><span class="sxs-lookup"><span data-stu-id="d237d-151">Returns the output that is generated by the invoked command (the value of the **Command** parameter).</span></span>

## <span data-ttu-id="d237d-152">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d237d-152">NOTES</span></span>

<span data-ttu-id="d237d-153">In de meeste gevallen roept u expressies aan met behulp van de aanroep operator van Power shell en haalt u dezelfde resultaten op.</span><span class="sxs-lookup"><span data-stu-id="d237d-153">In most cases, you invoke expressions using PowerShell's call operator and achieve the same results.</span></span>
<span data-ttu-id="d237d-154">De aanroep operator is een veiliger methode.</span><span class="sxs-lookup"><span data-stu-id="d237d-154">The call operator is a safer method.</span></span> <span data-ttu-id="d237d-155">Zie [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d237d-155">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-).</span></span>

## <span data-ttu-id="d237d-156">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d237d-156">RELATED LINKS</span></span>

[<span data-ttu-id="d237d-157">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="d237d-157">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="d237d-158">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="d237d-158">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)

