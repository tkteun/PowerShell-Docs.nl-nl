---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 4fefb133416b3db6c19c71a916d73fe00f86f3a4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705609"
---
# <span data-ttu-id="69c56-102">Out-Host</span><span class="sxs-lookup"><span data-stu-id="69c56-102">Out-Host</span></span>

## <span data-ttu-id="69c56-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="69c56-103">SYNOPSIS</span></span>
<span data-ttu-id="69c56-104">Verzendt uitvoer naar de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="69c56-104">Sends output to the command line.</span></span>

## <span data-ttu-id="69c56-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="69c56-105">SYNTAX</span></span>

### <span data-ttu-id="69c56-106">Alles</span><span class="sxs-lookup"><span data-stu-id="69c56-106">All</span></span>

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="69c56-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="69c56-107">DESCRIPTION</span></span>

<span data-ttu-id="69c56-108">De `Out-Host` cmdlet verzendt uitvoer naar de Power shell-host om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="69c56-108">The `Out-Host` cmdlet sends output to the PowerShell host for display.</span></span> <span data-ttu-id="69c56-109">Op de host wordt de uitvoer op de opdracht regel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="69c56-109">The host displays the output at the command line.</span></span> <span data-ttu-id="69c56-110">Omdat `Out-Host` de standaard waarde is, hoeft u deze niet op te geven, tenzij u de para meters wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="69c56-110">Because `Out-Host` is the default, you don't have to specify it unless you want to use its parameters.</span></span>

<span data-ttu-id="69c56-111">`Out-Host` wordt automatisch toegevoegd aan elke opdracht die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="69c56-111">`Out-Host` is automatically appended to every command that is executed.</span></span> <span data-ttu-id="69c56-112">De uitvoer van de pijp lijn wordt door gegeven aan de host die de opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="69c56-112">It passes the output of the pipeline to the host executing the command.</span></span> <span data-ttu-id="69c56-113">`Out-Host` Hiermee worden ANSI-escape reeksen genegeerd.</span><span class="sxs-lookup"><span data-stu-id="69c56-113">`Out-Host` ignores ANSI escape sequences.</span></span> <span data-ttu-id="69c56-114">De escape-reeksen worden verwerkt door de host.</span><span class="sxs-lookup"><span data-stu-id="69c56-114">The escape sequences are handled by the host.</span></span> <span data-ttu-id="69c56-115">`Out-Host` Hiermee worden ANSI-escape reeksen aan de host door gegeven zonder te worden geïnterpreteerd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="69c56-115">`Out-Host` passes ANSI escape sequences to the host without trying to interpret or change them.</span></span>

## <span data-ttu-id="69c56-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="69c56-116">EXAMPLES</span></span>

### <span data-ttu-id="69c56-117">Voor beeld 1: uitvoer één pagina per keer weer geven</span><span class="sxs-lookup"><span data-stu-id="69c56-117">Example 1: Display output one page at a time</span></span>

<span data-ttu-id="69c56-118">In dit voor beeld wordt de systeem processen per pagina weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="69c56-118">This example displays the system processes one page at a time.</span></span>

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

<span data-ttu-id="69c56-119">`Get-Process` Hiermee worden de systeem processen opgehaald en worden de objecten van de pijp lijn omlaag verzonden.</span><span class="sxs-lookup"><span data-stu-id="69c56-119">`Get-Process` gets the system processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="69c56-120">`Out-Host` maakt gebruik van de para meter **paging** om één pagina met gegevens per keer weer te geven.</span><span class="sxs-lookup"><span data-stu-id="69c56-120">`Out-Host` uses the **Paging** parameter to display one page of data at a time.</span></span>

### <span data-ttu-id="69c56-121">Voor beeld 2: een variabele als invoer gebruiken</span><span class="sxs-lookup"><span data-stu-id="69c56-121">Example 2: Use a variable as input</span></span>

<span data-ttu-id="69c56-122">In dit voor beeld worden objecten gebruikt die zijn opgeslagen in een variabele als invoer voor `Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="69c56-122">This example uses objects stored in a variable as the input for `Out-Host`.</span></span>

```powershell
$io = Get-History
Out-Host -InputObject $io
```

<span data-ttu-id="69c56-123">`Get-History` Hiermee wordt de geschiedenis van de Power shell-sessie opgehaald en worden de objecten in de `$io` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="69c56-123">`Get-History` gets the PowerShell session's history, and stores the objects in the `$io` variable.</span></span>
<span data-ttu-id="69c56-124">`Out-Host` maakt gebruik van de para meter **input object** om de variabele op te geven `$io` en geeft de geschiedenis weer.</span><span class="sxs-lookup"><span data-stu-id="69c56-124">`Out-Host` uses the **InputObject** parameter to specify the `$io` variable and displays the history.</span></span>

## <span data-ttu-id="69c56-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="69c56-125">PARAMETERS</span></span>

### <span data-ttu-id="69c56-126">-Input object</span><span class="sxs-lookup"><span data-stu-id="69c56-126">-InputObject</span></span>

<span data-ttu-id="69c56-127">Hiermee geeft u de objecten die naar de-console worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="69c56-127">Specifies the objects that are written to the console.</span></span> <span data-ttu-id="69c56-128">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="69c56-128">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="69c56-129">-Paging</span><span class="sxs-lookup"><span data-stu-id="69c56-129">-Paging</span></span>

<span data-ttu-id="69c56-130">Hiermee wordt aangegeven dat `Out-Host` één pagina met uitvoer per keer wordt weer gegeven en wacht op invoer van de gebruiker voordat de resterende pagina's worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="69c56-130">Indicates that `Out-Host` displays one page of output at a time, and waits for user input before the remaining pages are displayed.</span></span> <span data-ttu-id="69c56-131">Standaard wordt alle uitvoer op één pagina weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="69c56-131">By default, all the output is displayed on a single page.</span></span> <span data-ttu-id="69c56-132">De pagina grootte wordt bepaald door de kenmerken van de host.</span><span class="sxs-lookup"><span data-stu-id="69c56-132">The page size is determined by the characteristics of the host.</span></span>

<span data-ttu-id="69c56-133">Druk op de <kbd>spatie</kbd> balk om de volgende uitvoer pagina of de <kbd>Enter</kbd> -toets weer te geven om de volgende uitvoer regel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="69c56-133">Press the <kbd>Space</kbd> bar to display the next page of output or the <kbd>Enter</kbd> key to view the next line of output.</span></span> <span data-ttu-id="69c56-134">Druk op <kbd>Q</kbd> om af te sluiten.</span><span class="sxs-lookup"><span data-stu-id="69c56-134">Press <kbd>Q</kbd> to quit.</span></span>

<span data-ttu-id="69c56-135">**Paginering** is vergelijkbaar met de **meer** opdracht.</span><span class="sxs-lookup"><span data-stu-id="69c56-135">**Paging** is similar to the **more** command.</span></span>

> [!NOTE]
> <span data-ttu-id="69c56-136">De **paginerings** parameter wordt niet ondersteund door de Power shell ISE-host.</span><span class="sxs-lookup"><span data-stu-id="69c56-136">The **Paging** parameter isn't supported by the PowerShell ISE host.</span></span>

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

### <span data-ttu-id="69c56-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="69c56-137">CommonParameters</span></span>

<span data-ttu-id="69c56-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="69c56-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="69c56-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="69c56-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="69c56-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="69c56-140">INPUTS</span></span>

### <span data-ttu-id="69c56-141">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="69c56-141">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="69c56-142">U kunt objecten naar beneden verplaatsen in de pijp lijn `Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="69c56-142">You can send objects down the pipeline to `Out-Host`.</span></span>

## <span data-ttu-id="69c56-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="69c56-143">OUTPUTS</span></span>

### <span data-ttu-id="69c56-144">Geen</span><span class="sxs-lookup"><span data-stu-id="69c56-144">None</span></span>

<span data-ttu-id="69c56-145">`Out-Host` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="69c56-145">`Out-Host` doesn't generate any output.</span></span> <span data-ttu-id="69c56-146">Er worden objecten naar de host verzonden om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="69c56-146">It sends objects to the host for display.</span></span>

## <span data-ttu-id="69c56-147">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="69c56-147">NOTES</span></span>

<span data-ttu-id="69c56-148">De **paginerings** parameter wordt niet ondersteund door alle Power shell-hosts.</span><span class="sxs-lookup"><span data-stu-id="69c56-148">The **Paging** parameter isn't supported by all PowerShell hosts.</span></span> <span data-ttu-id="69c56-149">Als u bijvoorbeeld de para meter **paging** in het Power shell-ISE gebruikt, wordt de volgende fout weer gegeven: `out-lineoutput : The method or operation is not implemented.`</span><span class="sxs-lookup"><span data-stu-id="69c56-149">For example, if you use the **Paging** parameter in the PowerShell ISE, the following error is displayed: `out-lineoutput : The method or operation is not implemented.`</span></span>

<span data-ttu-id="69c56-150">De cmdlets die de **out** -verb bevatten, `Out-` en objecten niet opdelen.</span><span class="sxs-lookup"><span data-stu-id="69c56-150">The cmdlets that contain the **Out** verb, `Out-`, don't format objects.</span></span> <span data-ttu-id="69c56-151">Ze genereren objecten en verzenden ze naar het opgegeven weergave doel.</span><span class="sxs-lookup"><span data-stu-id="69c56-151">They render objects and send them to the specified display destination.</span></span> <span data-ttu-id="69c56-152">Als u een niet-opgemaakt object naar een `Out-` cmdlet verzendt, verzendt de cmdlet het naar een format-cmdlet voordat deze wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="69c56-152">If you send an unformatted object to an `Out-` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="69c56-153">De `Out-` cmdlets hebben geen para meters voor namen of bestands paden.</span><span class="sxs-lookup"><span data-stu-id="69c56-153">The `Out-` cmdlets don't have parameters for names or file paths.</span></span> <span data-ttu-id="69c56-154">Als u gegevens naar een `Out-` cmdlet wilt verzenden, gebruikt u de pijp lijn om de uitvoer van een Power shell-opdracht naar de cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="69c56-154">To send data to an `Out-` cmdlet, use the pipeline to send a PowerShell command's output to the cmdlet.</span></span> <span data-ttu-id="69c56-155">Of u kunt gegevens opslaan in een variabele en de para meter **input object** gebruiken om de gegevens door te geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="69c56-155">Or, you can store data in a variable and use the **InputObject** parameter to pass the data to the cmdlet.</span></span>

<span data-ttu-id="69c56-156">`Out-Host` gegevens worden verzonden, maar er worden geen uitvoer objecten geproduceerd.</span><span class="sxs-lookup"><span data-stu-id="69c56-156">`Out-Host` sends data, but it doesn't produce any output objects.</span></span> <span data-ttu-id="69c56-157">Als u de uitvoer van `Out-Host` naar de cmdlet pijp lijnt `Get-Member` , `Get-Member` rapporten dat er geen objecten zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="69c56-157">If you pipeline the output of `Out-Host` to the `Get-Member` cmdlet, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="69c56-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="69c56-158">RELATED LINKS</span></span>

[<span data-ttu-id="69c56-159">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="69c56-159">Clear-Host</span></span>](Clear-Host.md)

[<span data-ttu-id="69c56-160">Out-standaard</span><span class="sxs-lookup"><span data-stu-id="69c56-160">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="69c56-161">Out-file</span><span class="sxs-lookup"><span data-stu-id="69c56-161">Out-File</span></span>](../Microsoft.PowerShell.Utility/Out-File.md)

[<span data-ttu-id="69c56-162">Out-Null</span><span class="sxs-lookup"><span data-stu-id="69c56-162">Out-Null</span></span>](Out-Null.md)

[<span data-ttu-id="69c56-163">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="69c56-163">Out-Printer</span></span>](../Microsoft.PowerShell.Utility/Out-Printer.md)

[<span data-ttu-id="69c56-164">Out-teken reeks</span><span class="sxs-lookup"><span data-stu-id="69c56-164">Out-String</span></span>](../Microsoft.PowerShell.Utility/Out-String.md)

[<span data-ttu-id="69c56-165">Write-host</span><span class="sxs-lookup"><span data-stu-id="69c56-165">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)

