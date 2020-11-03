---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 9f53f137ecdd415e0185e380cba6ff817972b82e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251293"
---
# <span data-ttu-id="deb8d-103">Out-Host</span><span class="sxs-lookup"><span data-stu-id="deb8d-103">Out-Host</span></span>

## <span data-ttu-id="deb8d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="deb8d-104">SYNOPSIS</span></span>
<span data-ttu-id="deb8d-105">Verzendt uitvoer naar de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="deb8d-105">Sends output to the command line.</span></span>

## <span data-ttu-id="deb8d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="deb8d-106">SYNTAX</span></span>

### <span data-ttu-id="deb8d-107">Alles</span><span class="sxs-lookup"><span data-stu-id="deb8d-107">All</span></span>

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="deb8d-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="deb8d-108">DESCRIPTION</span></span>

<span data-ttu-id="deb8d-109">De `Out-Host` cmdlet verzendt uitvoer naar de Power shell-host om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-109">The `Out-Host` cmdlet sends output to the PowerShell host for display.</span></span> <span data-ttu-id="deb8d-110">Op de host wordt de uitvoer op de opdracht regel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-110">The host displays the output at the command line.</span></span> <span data-ttu-id="deb8d-111">Omdat `Out-Host` de standaard waarde is, hoeft u deze niet op te geven, tenzij u de para meters wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="deb8d-111">Because `Out-Host` is the default, you don't have to specify it unless you want to use its parameters.</span></span>

<span data-ttu-id="deb8d-112">`Out-Host` wordt automatisch toegevoegd aan elke opdracht die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="deb8d-112">`Out-Host` is automatically appended to every command that is executed.</span></span> <span data-ttu-id="deb8d-113">De uitvoer van de pijp lijn wordt door gegeven aan de host die de opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="deb8d-113">It passes the output of the pipeline to the host executing the command.</span></span> <span data-ttu-id="deb8d-114">`Out-Host` Hiermee worden ANSI-escape reeksen genegeerd.</span><span class="sxs-lookup"><span data-stu-id="deb8d-114">`Out-Host` ignores ANSI escape sequences.</span></span> <span data-ttu-id="deb8d-115">De escape-reeksen worden verwerkt door de host.</span><span class="sxs-lookup"><span data-stu-id="deb8d-115">The escape sequences are handled by the host.</span></span> <span data-ttu-id="deb8d-116">`Out-Host` Hiermee worden ANSI-escape reeksen aan de host door gegeven zonder te worden geïnterpreteerd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="deb8d-116">`Out-Host` passes ANSI escape sequences to the host without trying to interpret or change them.</span></span>

## <span data-ttu-id="deb8d-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="deb8d-117">EXAMPLES</span></span>

### <span data-ttu-id="deb8d-118">Voor beeld 1: uitvoer één pagina per keer weer geven</span><span class="sxs-lookup"><span data-stu-id="deb8d-118">Example 1: Display output one page at a time</span></span>

<span data-ttu-id="deb8d-119">In dit voor beeld wordt de systeem processen per pagina weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-119">This example displays the system processes one page at a time.</span></span>

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="deb8d-120">`Get-Process` Hiermee worden de systeem processen opgehaald en worden de objecten van de pijp lijn omlaag verzonden.</span><span class="sxs-lookup"><span data-stu-id="deb8d-120">`Get-Process` gets the system processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="deb8d-121">`Out-Host` maakt gebruik van de para meter **paging** om één pagina met gegevens per keer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-121">`Out-Host` uses the **Paging** parameter to display one page of data at a time.</span></span>

### <span data-ttu-id="deb8d-122">Voor beeld 2: een variabele als invoer gebruiken</span><span class="sxs-lookup"><span data-stu-id="deb8d-122">Example 2: Use a variable as input</span></span>

<span data-ttu-id="deb8d-123">In dit voor beeld worden objecten gebruikt die zijn opgeslagen in een variabele als invoer voor `Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="deb8d-123">This example uses objects stored in a variable as the input for `Out-Host`.</span></span>

```powershell
$io = Get-History
Out-Host -InputObject $io
```

<span data-ttu-id="deb8d-124">`Get-History` Hiermee wordt de geschiedenis van de Power shell-sessie opgehaald en worden de objecten in de `$io` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="deb8d-124">`Get-History` gets the PowerShell session's history, and stores the objects in the `$io` variable.</span></span>
<span data-ttu-id="deb8d-125">`Out-Host` maakt gebruik van de para meter **input object** om de variabele op te geven `$io` en geeft de geschiedenis weer.</span><span class="sxs-lookup"><span data-stu-id="deb8d-125">`Out-Host` uses the **InputObject** parameter to specify the `$io` variable and displays the history.</span></span>

## <span data-ttu-id="deb8d-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="deb8d-126">PARAMETERS</span></span>

### <span data-ttu-id="deb8d-127">-Input object</span><span class="sxs-lookup"><span data-stu-id="deb8d-127">-InputObject</span></span>

<span data-ttu-id="deb8d-128">Hiermee geeft u de objecten die naar de-console worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-128">Specifies the objects that are written to the console.</span></span> <span data-ttu-id="deb8d-129">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="deb8d-129">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="deb8d-130">-Paging</span><span class="sxs-lookup"><span data-stu-id="deb8d-130">-Paging</span></span>

<span data-ttu-id="deb8d-131">Hiermee wordt aangegeven dat `Out-Host` één pagina met uitvoer per keer wordt weer gegeven en wacht op invoer van de gebruiker voordat de resterende pagina's worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-131">Indicates that `Out-Host` displays one page of output at a time, and waits for user input before the remaining pages are displayed.</span></span> <span data-ttu-id="deb8d-132">Standaard wordt alle uitvoer op één pagina weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-132">By default, all the output is displayed on a single page.</span></span> <span data-ttu-id="deb8d-133">De pagina grootte wordt bepaald door de kenmerken van de host.</span><span class="sxs-lookup"><span data-stu-id="deb8d-133">The page size is determined by the characteristics of the host.</span></span>

<span data-ttu-id="deb8d-134">Druk op de <kbd>spatie</kbd> balk om de volgende uitvoer pagina of de <kbd>Enter</kbd> -toets weer te geven om de volgende uitvoer regel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-134">Press the <kbd>Space</kbd> bar to display the next page of output or the <kbd>Enter</kbd> key to view the next line of output.</span></span> <span data-ttu-id="deb8d-135">Druk op <kbd>Q</kbd> om af te sluiten.</span><span class="sxs-lookup"><span data-stu-id="deb8d-135">Press <kbd>Q</kbd> to quit.</span></span>

<span data-ttu-id="deb8d-136">**Paginering** is vergelijkbaar met de **meer** opdracht.</span><span class="sxs-lookup"><span data-stu-id="deb8d-136">**Paging** is similar to the **more** command.</span></span>

> [!NOTE]
> <span data-ttu-id="deb8d-137">De **paginerings** parameter wordt niet ondersteund door de Power shell ISE-host.</span><span class="sxs-lookup"><span data-stu-id="deb8d-137">The **Paging** parameter isn't supported by the PowerShell ISE host.</span></span>

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

### <span data-ttu-id="deb8d-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="deb8d-138">CommonParameters</span></span>

<span data-ttu-id="deb8d-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="deb8d-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="deb8d-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="deb8d-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="deb8d-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="deb8d-141">INPUTS</span></span>

### <span data-ttu-id="deb8d-142">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="deb8d-142">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="deb8d-143">U kunt objecten naar beneden verplaatsen in de pijp lijn `Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="deb8d-143">You can send objects down the pipeline to `Out-Host`.</span></span>

## <span data-ttu-id="deb8d-144">UITVOER</span><span class="sxs-lookup"><span data-stu-id="deb8d-144">OUTPUTS</span></span>

### <span data-ttu-id="deb8d-145">Geen</span><span class="sxs-lookup"><span data-stu-id="deb8d-145">None</span></span>

<span data-ttu-id="deb8d-146">`Out-Host` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="deb8d-146">`Out-Host` doesn't generate any output.</span></span> <span data-ttu-id="deb8d-147">Er worden objecten naar de host verzonden om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-147">It sends objects to the host for display.</span></span>

## <span data-ttu-id="deb8d-148">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="deb8d-148">NOTES</span></span>

<span data-ttu-id="deb8d-149">De **paginerings** parameter wordt niet ondersteund door alle Power shell-hosts.</span><span class="sxs-lookup"><span data-stu-id="deb8d-149">The **Paging** parameter isn't supported by all PowerShell hosts.</span></span> <span data-ttu-id="deb8d-150">Als u bijvoorbeeld de para meter **paging** in het Power shell-ISE gebruikt, wordt de volgende fout weer gegeven: `out-lineoutput : The method or operation is not implemented.`</span><span class="sxs-lookup"><span data-stu-id="deb8d-150">For example, if you use the **Paging** parameter in the PowerShell ISE, the following error is displayed: `out-lineoutput : The method or operation is not implemented.`</span></span>

<span data-ttu-id="deb8d-151">De cmdlets die de **out** -verb bevatten, `Out-` en objecten niet opdelen.</span><span class="sxs-lookup"><span data-stu-id="deb8d-151">The cmdlets that contain the **Out** verb, `Out-`, don't format objects.</span></span> <span data-ttu-id="deb8d-152">Ze genereren objecten en verzenden ze naar het opgegeven weergave doel.</span><span class="sxs-lookup"><span data-stu-id="deb8d-152">They render objects and send them to the specified display destination.</span></span> <span data-ttu-id="deb8d-153">Als u een niet-opgemaakt object naar een `Out-` cmdlet verzendt, verzendt de cmdlet het naar een format-cmdlet voordat deze wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-153">If you send an unformatted object to an `Out-` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="deb8d-154">De `Out-` cmdlets hebben geen para meters voor namen of bestands paden.</span><span class="sxs-lookup"><span data-stu-id="deb8d-154">The `Out-` cmdlets don't have parameters for names or file paths.</span></span> <span data-ttu-id="deb8d-155">Als u gegevens naar een `Out-` cmdlet wilt verzenden, gebruikt u de pijp lijn om de uitvoer van een Power shell-opdracht naar de cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="deb8d-155">To send data to an `Out-` cmdlet, use the pipeline to send a PowerShell command's output to the cmdlet.</span></span> <span data-ttu-id="deb8d-156">Of u kunt gegevens opslaan in een variabele en de para meter **input object** gebruiken om de gegevens door te geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="deb8d-156">Or, you can store data in a variable and use the **InputObject** parameter to pass the data to the cmdlet.</span></span>

<span data-ttu-id="deb8d-157">`Out-Host` gegevens worden verzonden, maar er worden geen uitvoer objecten geproduceerd.</span><span class="sxs-lookup"><span data-stu-id="deb8d-157">`Out-Host` sends data, but it doesn't produce any output objects.</span></span> <span data-ttu-id="deb8d-158">Als u de uitvoer van `Out-Host` naar de cmdlet pijp lijnt `Get-Member` , `Get-Member` rapporten dat er geen objecten zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="deb8d-158">If you pipeline the output of `Out-Host` to the `Get-Member` cmdlet, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="deb8d-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="deb8d-159">RELATED LINKS</span></span>

[<span data-ttu-id="deb8d-160">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="deb8d-160">Clear-Host</span></span>](Clear-Host.md)

[<span data-ttu-id="deb8d-161">Out-standaard</span><span class="sxs-lookup"><span data-stu-id="deb8d-161">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="deb8d-162">Out-file</span><span class="sxs-lookup"><span data-stu-id="deb8d-162">Out-File</span></span>](../Microsoft.PowerShell.Utility/Out-File.md)

[<span data-ttu-id="deb8d-163">Out-Null</span><span class="sxs-lookup"><span data-stu-id="deb8d-163">Out-Null</span></span>](Out-Null.md)

[<span data-ttu-id="deb8d-164">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="deb8d-164">Out-Printer</span></span>](../Microsoft.PowerShell.Utility/Out-Printer.md)

[<span data-ttu-id="deb8d-165">Out-teken reeks</span><span class="sxs-lookup"><span data-stu-id="deb8d-165">Out-String</span></span>](../Microsoft.PowerShell.Utility/Out-String.md)

[<span data-ttu-id="deb8d-166">Write-host</span><span class="sxs-lookup"><span data-stu-id="deb8d-166">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)

