---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: ccc72ac961adbcba542a7b8be55ad49df68a5ef6
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253003"
---
# <span data-ttu-id="e49c1-103">Write-Output</span><span class="sxs-lookup"><span data-stu-id="e49c1-103">Write-Output</span></span>

## <span data-ttu-id="e49c1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e49c1-104">SYNOPSIS</span></span>
<span data-ttu-id="e49c1-105">Hiermee worden de opgegeven objecten verzonden naar de volgende opdracht in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e49c1-105">Sends the specified objects to the next command in the pipeline.</span></span> <span data-ttu-id="e49c1-106">Als de opdracht de laatste opdracht in de pijp lijn is, worden de objecten weer gegeven in de-console.</span><span class="sxs-lookup"><span data-stu-id="e49c1-106">If the command is the last command in the pipeline, the objects are displayed in the console.</span></span>

## <span data-ttu-id="e49c1-107">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e49c1-107">SYNTAX</span></span>

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="e49c1-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e49c1-108">DESCRIPTION</span></span>

<span data-ttu-id="e49c1-109">De `Write-Output` cmdlet verzendt het opgegeven object in de pijp lijn naar de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="e49c1-109">The `Write-Output` cmdlet sends the specified object down the pipeline to the next command.</span></span>
<span data-ttu-id="e49c1-110">Als de opdracht de laatste opdracht in de pijp lijn is, wordt het object in de-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e49c1-110">If the command is the last command in the pipeline, the object is displayed in the console.</span></span>

<span data-ttu-id="e49c1-111">`Write-Output` Hiermee worden objecten verzonden naar de primaire pijp lijn, ook wel bekend als de "uitvoer stroom" of de "pijp lijn slagen".</span><span class="sxs-lookup"><span data-stu-id="e49c1-111">`Write-Output` sends objects down the primary pipeline, also known as the "output stream" or the "success pipeline."</span></span> <span data-ttu-id="e49c1-112">Als u fout objecten wilt verzenden naar de fout pijplijn, gebruikt u schrijf fout.</span><span class="sxs-lookup"><span data-stu-id="e49c1-112">To send error objects down the error pipeline, use Write-Error.</span></span>

<span data-ttu-id="e49c1-113">Deze cmdlet wordt doorgaans gebruikt in scripts om teken reeksen en andere objecten in de-console weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e49c1-113">This cmdlet is typically used in scripts to display strings and other objects on the console.</span></span> <span data-ttu-id="e49c1-114">Een van de ingebouwde aliassen voor `Write-Output` is `echo` en vergelijkbaar met andere shells die gebruikmaken van `echo` , het standaard gedrag is om de uitvoer aan het einde van een pijp lijn weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e49c1-114">One of the built-in aliases for `Write-Output` is `echo` and similar to other shells that use `echo`, the default behavior is to display the output at the end of a pipeline.</span></span> <span data-ttu-id="e49c1-115">In Power shell is het over het algemeen niet nodig om de cmdlet te gebruiken in gevallen waarin de uitvoer standaard wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e49c1-115">In PowerShell, it is generally not necessary to use the cmdlet in instances where the output is displayed by default.</span></span> <span data-ttu-id="e49c1-116">`Get-Process | Write-Output` is bijvoorbeeld gelijk aan `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="e49c1-116">For example, `Get-Process | Write-Output` is equivalent to `Get-Process`.</span></span> <span data-ttu-id="e49c1-117">Of `echo "Home directory: $HOME"` kan worden geschreven, `"Home directory: $HOME"` .</span><span class="sxs-lookup"><span data-stu-id="e49c1-117">Or, `echo "Home directory: $HOME"` can be written, `"Home directory: $HOME"`.</span></span>

<span data-ttu-id="e49c1-118">Standaard `Write-Output` inventariseert de verzamelingen die aan de cmdlet worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="e49c1-118">By default, `Write-Output` enumerates through collections provided to the cmdlet.</span></span> <span data-ttu-id="e49c1-119">Kan echter `Write-Output` ook worden gebruikt voor het door geven van verzamelingen in de pijp lijn als één object met de para meter ' **enumerate** '.</span><span class="sxs-lookup"><span data-stu-id="e49c1-119">However, `Write-Output` can also be used to pass collections down the pipeline as a single object with the **NoEnumerate** parameter.</span></span>

## <span data-ttu-id="e49c1-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e49c1-120">EXAMPLES</span></span>

### <span data-ttu-id="e49c1-121">Voor beeld 1: objecten ophalen en naar de console schrijven</span><span class="sxs-lookup"><span data-stu-id="e49c1-121">Example 1: Get objects and write them to the console</span></span>

```powershell
$P = Get-Process
Write-Output $P
```

<span data-ttu-id="e49c1-122">De eerste opdracht haalt processen op die worden uitgevoerd op de computer en slaat deze op in de `$P` variabele.</span><span class="sxs-lookup"><span data-stu-id="e49c1-122">The first command gets processes running on the computer and stores them in the `$P` variable.</span></span>

<span data-ttu-id="e49c1-123">Met de tweede en derde opdracht worden de proces objecten in de-console weer gegeven `$P` .</span><span class="sxs-lookup"><span data-stu-id="e49c1-123">The second and third commands display the process objects in `$P` on the console.</span></span>

### <span data-ttu-id="e49c1-124">Voor beeld 2: uitvoer door geven naar een andere cmdlet</span><span class="sxs-lookup"><span data-stu-id="e49c1-124">Example 2: Pass output to another cmdlet</span></span>

```powershell
Write-Output "test output" | Get-Member
```

<span data-ttu-id="e49c1-125">Met deze opdracht pipet u de test uitvoer teken reeks naar de `Get-Member` cmdlet, waarmee de leden van de klasse **System. String** worden weer gegeven, waarbij wordt aangetoond dat de teken reeks is door gegeven aan de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e49c1-125">This command pipes the "test output" string to the `Get-Member` cmdlet, which displays the members of the **System.String** class, demonstrating that the string was passed along the pipeline.</span></span>

### <span data-ttu-id="e49c1-126">Voor beeld 3: inventarisatie in uitvoer onderdrukken</span><span class="sxs-lookup"><span data-stu-id="e49c1-126">Example 3: Suppress enumeration in output</span></span>

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

<span data-ttu-id="e49c1-127">Met deze opdracht wordt de para meter ' niet **opsommen** ' toegevoegd om een verzameling of matrix als één object te behandelen via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e49c1-127">This command adds the **NoEnumerate** parameter to treat a collection or array as a single object through the pipeline.</span></span>

## <span data-ttu-id="e49c1-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e49c1-128">PARAMETERS</span></span>

### <span data-ttu-id="e49c1-129">-Input object</span><span class="sxs-lookup"><span data-stu-id="e49c1-129">-InputObject</span></span>

<span data-ttu-id="e49c1-130">Hiermee geeft u de objecten op die de pijp lijn moeten verzenden.</span><span class="sxs-lookup"><span data-stu-id="e49c1-130">Specifies the objects to send down the pipeline.</span></span> <span data-ttu-id="e49c1-131">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e49c1-131">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="e49c1-132">-Opsomming</span><span class="sxs-lookup"><span data-stu-id="e49c1-132">-NoEnumerate</span></span>

<span data-ttu-id="e49c1-133">Standaard wordt de uitvoer van de `Write-Output` cmdlet altijd opgesomd.</span><span class="sxs-lookup"><span data-stu-id="e49c1-133">By default, the `Write-Output` cmdlet always enumerates its output.</span></span> <span data-ttu-id="e49c1-134">De para meter ' niet **opsommen** ' onderdrukt het standaard gedrag en voor komt het `Write-Output` opsommen van uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e49c1-134">The **NoEnumerate** parameter suppresses the default behavior, and prevents `Write-Output` from enumerating output.</span></span> <span data-ttu-id="e49c1-135">De para meter voor de **opsomming** heeft geen effect als de opdracht tussen haakjes wordt ingepakt, omdat de opsomming afdwingt.</span><span class="sxs-lookup"><span data-stu-id="e49c1-135">The **NoEnumerate** parameter has no effect if the command is wrapped in parentheses, because the parentheses force enumeration.</span></span> <span data-ttu-id="e49c1-136">`(Write-Output 1,2,3)`De matrix wordt bijvoorbeeld nog steeds opgesomd.</span><span class="sxs-lookup"><span data-stu-id="e49c1-136">For example, `(Write-Output 1,2,3)` still enumerates the array.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e49c1-137">Er is een probleem met deze switch in Windows Power shell die is opgelost in Power shell 6,2 en hoger.</span><span class="sxs-lookup"><span data-stu-id="e49c1-137">There is an issue with this switch in Windows PowerShell that is fixed in PowerShell 6.2 and above.</span></span> <span data-ttu-id="e49c1-138">Wanneer u **geen gebruik maakt** van de para meter **input object** , wordt de opdracht nog steeds opgesomd.</span><span class="sxs-lookup"><span data-stu-id="e49c1-138">When using **NoEnumerate** and explicitly using the **InputObject** parameter, the command still enumerates.</span></span> <span data-ttu-id="e49c1-139">U kunt dit probleem omzeilen door de **input object** -argument (en) positioneel door te geven.</span><span class="sxs-lookup"><span data-stu-id="e49c1-139">To work around this, pass the **InputObject** argument(s) positionally.</span></span>

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

### <span data-ttu-id="e49c1-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e49c1-140">CommonParameters</span></span>

<span data-ttu-id="e49c1-141">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e49c1-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e49c1-142">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e49c1-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e49c1-143">INVOER</span><span class="sxs-lookup"><span data-stu-id="e49c1-143">INPUTS</span></span>

### <span data-ttu-id="e49c1-144">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="e49c1-144">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e49c1-145">U kunt objecten door sluizen naar `Write-Output` .</span><span class="sxs-lookup"><span data-stu-id="e49c1-145">You can pipe objects to `Write-Output`.</span></span>

## <span data-ttu-id="e49c1-146">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e49c1-146">OUTPUTS</span></span>

### <span data-ttu-id="e49c1-147">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="e49c1-147">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e49c1-148">`Write-Output` retourneert de objecten die als invoer worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="e49c1-148">`Write-Output` returns the objects that are submitted as input.</span></span>

## <span data-ttu-id="e49c1-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e49c1-149">NOTES</span></span>

## <span data-ttu-id="e49c1-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e49c1-150">RELATED LINKS</span></span>

[<span data-ttu-id="e49c1-151">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="e49c1-151">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="e49c1-152">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="e49c1-152">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="e49c1-153">T-object</span><span class="sxs-lookup"><span data-stu-id="e49c1-153">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="e49c1-154">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="e49c1-154">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="e49c1-155">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="e49c1-155">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="e49c1-156">Write-host</span><span class="sxs-lookup"><span data-stu-id="e49c1-156">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="e49c1-157">Write-Information</span><span class="sxs-lookup"><span data-stu-id="e49c1-157">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="e49c1-158">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="e49c1-158">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="e49c1-159">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="e49c1-159">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="e49c1-160">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="e49c1-160">Write-Warning</span></span>](Write-Warning.md)
