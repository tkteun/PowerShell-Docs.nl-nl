---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 3d23f76dbf8e1c9a21805a4914038c8c4f319852
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706011"
---
# <span data-ttu-id="42dad-102">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="42dad-102">Write-Debug</span></span>

## <span data-ttu-id="42dad-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="42dad-103">SYNOPSIS</span></span>
<span data-ttu-id="42dad-104">Schrijft een debug-bericht naar de-console.</span><span class="sxs-lookup"><span data-stu-id="42dad-104">Writes a debug message to the console.</span></span>

## <span data-ttu-id="42dad-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="42dad-105">SYNTAX</span></span>

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="42dad-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="42dad-106">DESCRIPTION</span></span>

<span data-ttu-id="42dad-107">De `Write-Debug` cmdlet schrijft fout opsporingsgegevens van berichten naar de host vanuit een script of opdracht.</span><span class="sxs-lookup"><span data-stu-id="42dad-107">The `Write-Debug` cmdlet writes debug messages to the host from a script or command.</span></span>

<span data-ttu-id="42dad-108">Standaard worden fout opsporings berichten niet weer gegeven in de-console, maar u kunt ze weer geven met de para meter **debug** of de `$DebugPreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="42dad-108">By default, debug messages are not displayed in the console, but you can display them by using the **Debug** parameter or the `$DebugPreference` variable.</span></span>

## <span data-ttu-id="42dad-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="42dad-109">EXAMPLES</span></span>

### <span data-ttu-id="42dad-110">Voor beeld 1: inzicht $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="42dad-110">Example 1: Understand $DebugPreference</span></span>

<span data-ttu-id="42dad-111">In dit voor beeld wordt een debug-bericht geschreven.</span><span class="sxs-lookup"><span data-stu-id="42dad-111">This example writes a debug message.</span></span>

```powershell
Write-Debug "Cannot open file."
```

<span data-ttu-id="42dad-112">De standaard waarde van `$DebugPreference` is **SilentlyContinue**.</span><span class="sxs-lookup"><span data-stu-id="42dad-112">The default value of `$DebugPreference` is **SilentlyContinue**.</span></span> <span data-ttu-id="42dad-113">Het bericht wordt daarom niet in de-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="42dad-113">Therefore, the message is not displayed in the console.</span></span>

### <span data-ttu-id="42dad-114">Voor beeld 2: de waarde van $DebugPreference wijzigen</span><span class="sxs-lookup"><span data-stu-id="42dad-114">Example 2: Change the value of $DebugPreference</span></span>

<span data-ttu-id="42dad-115">In dit voor beeld ziet u het effect van het wijzigen van de waarde van de `$DebugPreference` variabele.</span><span class="sxs-lookup"><span data-stu-id="42dad-115">This example shows the effect of changing the value of the `$DebugPreference` variable.</span></span> <span data-ttu-id="42dad-116">Eerst wordt de huidige waarde van `$DebugPreference` en poging tot het schrijven van een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="42dad-116">First, we display the current value of `$DebugPreference` and attempt to write a debug message.</span></span> <span data-ttu-id="42dad-117">Vervolgens wijzigen we de waarde van `$DebugPreference` om **door te gaan**, waardoor fout opsporingsgegevens kunnen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="42dad-117">Then we change the value of `$DebugPreference` to **Continue**, which allows debug messages to be displayed.</span></span>

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

<span data-ttu-id="42dad-118">Zie about_Preference_Variables voor meer informatie over `$DebugPreference` . [](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables)</span><span class="sxs-lookup"><span data-stu-id="42dad-118">For more information about `$DebugPreference`, see [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span></span>

### <span data-ttu-id="42dad-119">Voor beeld 3: de para meter debug gebruiken om $DebugPreference te negeren</span><span class="sxs-lookup"><span data-stu-id="42dad-119">Example 3: Use the Debug parameter to override $DebugPreference</span></span>

<span data-ttu-id="42dad-120">De `Test-Debug` functie schrijft de waarde van de `$DebugPreference` variabele naar de Power shell-host en naar de stroom voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="42dad-120">The `Test-Debug` function writes the value of the `$DebugPreference` variable to the PowerShell host and to the Debug stream.</span></span> <span data-ttu-id="42dad-121">In dit voor beeld gebruiken we de para meter **debug** om de `$DebugPreference` waarde te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="42dad-121">In this example, we use the **Debug** parameter to override the `$DebugPreference` value.</span></span>

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

<span data-ttu-id="42dad-122">U ziet dat de waarde van `$DebugPreference` wijzigingen wanneer u de para meter **debug** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="42dad-122">Notice that the value of `$DebugPreference` changes when you use the **Debug** parameter.</span></span> <span data-ttu-id="42dad-123">Deze wijziging is alleen van invloed op het bereik van de functie.</span><span class="sxs-lookup"><span data-stu-id="42dad-123">This change only affects the scope of the function.</span></span> <span data-ttu-id="42dad-124">De waarde wordt niet beïnvloed buiten de functie.</span><span class="sxs-lookup"><span data-stu-id="42dad-124">The value is not affected outside the function.</span></span>

<span data-ttu-id="42dad-125">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie over de para meter common **debug** .</span><span class="sxs-lookup"><span data-stu-id="42dad-125">For more information about the **Debug** common parameter, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="42dad-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="42dad-126">PARAMETERS</span></span>

### <span data-ttu-id="42dad-127">-Bericht</span><span class="sxs-lookup"><span data-stu-id="42dad-127">-Message</span></span>

<span data-ttu-id="42dad-128">Hiermee geeft u het debug-bericht op dat naar de-console moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="42dad-128">Specifies the debug message to send to the console.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="42dad-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="42dad-129">CommonParameters</span></span>

<span data-ttu-id="42dad-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="42dad-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="42dad-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="42dad-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="42dad-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="42dad-132">INPUTS</span></span>

### <span data-ttu-id="42dad-133">System. String</span><span class="sxs-lookup"><span data-stu-id="42dad-133">System.String</span></span>

<span data-ttu-id="42dad-134">U kunt een teken reeks die een debug-bericht bevat, door sluizen naar `Write-Debug` .</span><span class="sxs-lookup"><span data-stu-id="42dad-134">You can pipe a string that contains a debug message to `Write-Debug`.</span></span>

## <span data-ttu-id="42dad-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="42dad-135">OUTPUTS</span></span>

### <span data-ttu-id="42dad-136">Geen</span><span class="sxs-lookup"><span data-stu-id="42dad-136">None</span></span>

<span data-ttu-id="42dad-137">`Write-Debug` schrijft alleen naar de stroom voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="42dad-137">`Write-Debug` only writes to the debug stream.</span></span> <span data-ttu-id="42dad-138">Er worden geen objecten naar de pijp lijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="42dad-138">It does not write any objects to the pipeline.</span></span>

## <span data-ttu-id="42dad-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="42dad-139">NOTES</span></span>

## <span data-ttu-id="42dad-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="42dad-140">RELATED LINKS</span></span>

[<span data-ttu-id="42dad-141">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="42dad-141">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="42dad-142">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="42dad-142">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="42dad-143">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="42dad-143">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="42dad-144">Write-host</span><span class="sxs-lookup"><span data-stu-id="42dad-144">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="42dad-145">Write-output</span><span class="sxs-lookup"><span data-stu-id="42dad-145">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="42dad-146">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="42dad-146">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="42dad-147">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="42dad-147">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="42dad-148">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="42dad-148">Write-Warning</span></span>](Write-Warning.md)
