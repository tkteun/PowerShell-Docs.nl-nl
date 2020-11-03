---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: 75b046ea6b11be3e4d87ed9db3e011a1f00d6ef5
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93252984"
---
# <span data-ttu-id="6e643-103">Write-Output</span><span class="sxs-lookup"><span data-stu-id="6e643-103">Write-Output</span></span>

## <span data-ttu-id="6e643-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6e643-104">SYNOPSIS</span></span>
<span data-ttu-id="6e643-105">Hiermee worden de opgegeven objecten verzonden naar de volgende opdracht in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="6e643-105">Sends the specified objects to the next command in the pipeline.</span></span> <span data-ttu-id="6e643-106">Als de opdracht de laatste opdracht in de pijp lijn is, worden de objecten weer gegeven in de-console.</span><span class="sxs-lookup"><span data-stu-id="6e643-106">If the command is the last command in the pipeline, the objects are displayed in the console.</span></span>

## <span data-ttu-id="6e643-107">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6e643-107">SYNTAX</span></span>

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="6e643-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6e643-108">DESCRIPTION</span></span>

<span data-ttu-id="6e643-109">De `Write-Output` cmdlet verzendt het opgegeven object in de pijp lijn naar de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="6e643-109">The `Write-Output` cmdlet sends the specified object down the pipeline to the next command.</span></span>
<span data-ttu-id="6e643-110">Als de opdracht de laatste opdracht in de pijp lijn is, wordt het object in de-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6e643-110">If the command is the last command in the pipeline, the object is displayed in the console.</span></span>

<span data-ttu-id="6e643-111">`Write-Output` Hiermee worden objecten verzonden naar de primaire pijp lijn, ook wel bekend als de "uitvoer stroom" of de "pijp lijn slagen".</span><span class="sxs-lookup"><span data-stu-id="6e643-111">`Write-Output` sends objects down the primary pipeline, also known as the "output stream" or the "success pipeline."</span></span> <span data-ttu-id="6e643-112">Als u fout objecten wilt verzenden naar de fout pijplijn, gebruikt u schrijf fout.</span><span class="sxs-lookup"><span data-stu-id="6e643-112">To send error objects down the error pipeline, use Write-Error.</span></span>

<span data-ttu-id="6e643-113">Deze cmdlet wordt doorgaans gebruikt in scripts om teken reeksen en andere objecten in de-console weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6e643-113">This cmdlet is typically used in scripts to display strings and other objects on the console.</span></span> <span data-ttu-id="6e643-114">Een van de ingebouwde aliassen voor `Write-Output` is `echo` en vergelijkbaar met andere shells die gebruikmaken van `echo` , het standaard gedrag is om de uitvoer aan het einde van een pijp lijn weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6e643-114">One of the built-in aliases for `Write-Output` is `echo` and similar to other shells that use `echo`, the default behavior is to display the output at the end of a pipeline.</span></span> <span data-ttu-id="6e643-115">In Power shell is het over het algemeen niet nodig om de cmdlet te gebruiken in gevallen waarin de uitvoer standaard wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6e643-115">In PowerShell, it is generally not necessary to use the cmdlet in instances where the output is displayed by default.</span></span> <span data-ttu-id="6e643-116">`Get-Process | Write-Output` is bijvoorbeeld gelijk aan `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="6e643-116">For example, `Get-Process | Write-Output` is equivalent to `Get-Process`.</span></span> <span data-ttu-id="6e643-117">Of `echo "Home directory: $HOME"` kan worden geschreven, `"Home directory: $HOME"` .</span><span class="sxs-lookup"><span data-stu-id="6e643-117">Or, `echo "Home directory: $HOME"` can be written, `"Home directory: $HOME"`.</span></span>

<span data-ttu-id="6e643-118">Standaard `Write-Output` inventariseert de verzamelingen die aan de cmdlet worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="6e643-118">By default, `Write-Output` enumerates through collections provided to the cmdlet.</span></span> <span data-ttu-id="6e643-119">Kan echter `Write-Output` ook worden gebruikt voor het door geven van verzamelingen in de pijp lijn als één object met de para meter ' **enumerate** '.</span><span class="sxs-lookup"><span data-stu-id="6e643-119">However, `Write-Output` can also be used to pass collections down the pipeline as a single object with the **NoEnumerate** parameter.</span></span>

## <span data-ttu-id="6e643-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6e643-120">EXAMPLES</span></span>

### <span data-ttu-id="6e643-121">Voor beeld 1: objecten ophalen en naar de console schrijven</span><span class="sxs-lookup"><span data-stu-id="6e643-121">Example 1: Get objects and write them to the console</span></span>

```powershell
$P = Get-Process
Write-Output $P
```

<span data-ttu-id="6e643-122">De eerste opdracht haalt processen op die worden uitgevoerd op de computer en slaat deze op in de `$P` variabele.</span><span class="sxs-lookup"><span data-stu-id="6e643-122">The first command gets processes running on the computer and stores them in the `$P` variable.</span></span>

<span data-ttu-id="6e643-123">Met de tweede en derde opdracht worden de proces objecten in de-console weer gegeven `$P` .</span><span class="sxs-lookup"><span data-stu-id="6e643-123">The second and third commands display the process objects in `$P` on the console.</span></span>

### <span data-ttu-id="6e643-124">Voor beeld 2: uitvoer door geven naar een andere cmdlet</span><span class="sxs-lookup"><span data-stu-id="6e643-124">Example 2: Pass output to another cmdlet</span></span>

```powershell
Write-Output "test output" | Get-Member
```

<span data-ttu-id="6e643-125">Met deze opdracht pipet u de test uitvoer teken reeks naar de `Get-Member` cmdlet, waarmee de leden van de klasse **System. String** worden weer gegeven, waarbij wordt aangetoond dat de teken reeks is door gegeven aan de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="6e643-125">This command pipes the "test output" string to the `Get-Member` cmdlet, which displays the members of the **System.String** class, demonstrating that the string was passed along the pipeline.</span></span>

### <span data-ttu-id="6e643-126">Voor beeld 3: inventarisatie in uitvoer onderdrukken</span><span class="sxs-lookup"><span data-stu-id="6e643-126">Example 3: Suppress enumeration in output</span></span>

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

<span data-ttu-id="6e643-127">Met deze opdracht wordt de para meter ' niet **opsommen** ' toegevoegd om een verzameling of matrix als één object te behandelen via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="6e643-127">This command adds the **NoEnumerate** parameter to treat a collection or array as a single object through the pipeline.</span></span>

## <span data-ttu-id="6e643-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e643-128">PARAMETERS</span></span>

### <span data-ttu-id="6e643-129">-Input object</span><span class="sxs-lookup"><span data-stu-id="6e643-129">-InputObject</span></span>

<span data-ttu-id="6e643-130">Hiermee geeft u de objecten op die de pijp lijn moeten verzenden.</span><span class="sxs-lookup"><span data-stu-id="6e643-130">Specifies the objects to send down the pipeline.</span></span> <span data-ttu-id="6e643-131">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6e643-131">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6e643-132">-Opsomming</span><span class="sxs-lookup"><span data-stu-id="6e643-132">-NoEnumerate</span></span>

<span data-ttu-id="6e643-133">Standaard wordt de uitvoer van de `Write-Output` cmdlet altijd opgesomd.</span><span class="sxs-lookup"><span data-stu-id="6e643-133">By default, the `Write-Output` cmdlet always enumerates its output.</span></span> <span data-ttu-id="6e643-134">De para meter ' niet **opsommen** ' onderdrukt het standaard gedrag en voor komt het `Write-Output` opsommen van uitvoer.</span><span class="sxs-lookup"><span data-stu-id="6e643-134">The **NoEnumerate** parameter suppresses the default behavior, and prevents `Write-Output` from enumerating output.</span></span> <span data-ttu-id="6e643-135">De para meter voor de **opsomming** heeft geen effect als de opdracht tussen haakjes wordt ingepakt, omdat de opsomming afdwingt.</span><span class="sxs-lookup"><span data-stu-id="6e643-135">The **NoEnumerate** parameter has no effect if the command is wrapped in parentheses, because the parentheses force enumeration.</span></span> <span data-ttu-id="6e643-136">`(Write-Output 1,2,3)`De matrix wordt bijvoorbeeld nog steeds opgesomd.</span><span class="sxs-lookup"><span data-stu-id="6e643-136">For example, `(Write-Output 1,2,3)` still enumerates the array.</span></span>

> [!NOTE]
> <span data-ttu-id="6e643-137">Deze switch werkt alleen goed met Power shell Core 6,2 en hoger.</span><span class="sxs-lookup"><span data-stu-id="6e643-137">This switch only works correctly with PowerShell Core 6.2 and newer.</span></span> <span data-ttu-id="6e643-138">In oudere versies van Power shell core wordt de verzameling nog steeds geïnventariseerd, zelfs met het gebruik van deze switch.</span><span class="sxs-lookup"><span data-stu-id="6e643-138">On older versions of PowerShell Core, the collection is still enumerated even with use of this switch.</span></span>

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

### <span data-ttu-id="6e643-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6e643-139">CommonParameters</span></span>

<span data-ttu-id="6e643-140">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6e643-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6e643-141">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6e643-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6e643-142">INVOER</span><span class="sxs-lookup"><span data-stu-id="6e643-142">INPUTS</span></span>

### <span data-ttu-id="6e643-143">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6e643-143">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6e643-144">U kunt objecten door sluizen naar `Write-Output` .</span><span class="sxs-lookup"><span data-stu-id="6e643-144">You can pipe objects to `Write-Output`.</span></span>

## <span data-ttu-id="6e643-145">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6e643-145">OUTPUTS</span></span>

### <span data-ttu-id="6e643-146">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6e643-146">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="6e643-147">`Write-Output` retourneert de objecten die als invoer worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="6e643-147">`Write-Output` returns the objects that are submitted as input.</span></span>

## <span data-ttu-id="6e643-148">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6e643-148">NOTES</span></span>

## <span data-ttu-id="6e643-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6e643-149">RELATED LINKS</span></span>

[<span data-ttu-id="6e643-150">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="6e643-150">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="6e643-151">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="6e643-151">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="6e643-152">T-object</span><span class="sxs-lookup"><span data-stu-id="6e643-152">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="6e643-153">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="6e643-153">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="6e643-154">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="6e643-154">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="6e643-155">Write-host</span><span class="sxs-lookup"><span data-stu-id="6e643-155">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="6e643-156">Write-Information</span><span class="sxs-lookup"><span data-stu-id="6e643-156">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="6e643-157">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="6e643-157">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="6e643-158">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="6e643-158">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="6e643-159">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="6e643-159">Write-Warning</span></span>](Write-Warning.md)
