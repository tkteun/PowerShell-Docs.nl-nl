---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 52f060b0dd0364b1c930cd27a4bba280e467cff4
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253000"
---
# <span data-ttu-id="1c26c-103">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="1c26c-103">Write-Warning</span></span>

## <span data-ttu-id="1c26c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1c26c-104">SYNOPSIS</span></span>
<span data-ttu-id="1c26c-105">Hiermee schrijft u een waarschuwings bericht.</span><span class="sxs-lookup"><span data-stu-id="1c26c-105">Writes a warning message.</span></span>

## <span data-ttu-id="1c26c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1c26c-106">SYNTAX</span></span>

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="1c26c-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1c26c-107">DESCRIPTION</span></span>

<span data-ttu-id="1c26c-108">De `Write-Warning` cmdlet schrijft een waarschuwings bericht naar de Power shell-host.</span><span class="sxs-lookup"><span data-stu-id="1c26c-108">The `Write-Warning` cmdlet writes a warning message to the PowerShell host.</span></span> <span data-ttu-id="1c26c-109">De reactie op de waarschuwing is afhankelijk van de waarde van de gebruikers `$WarningPreference` variabele en het gebruik van de gemeen schappelijke para meter **WarningAction** .</span><span class="sxs-lookup"><span data-stu-id="1c26c-109">The response to the warning depends on the value of the user's `$WarningPreference` variable and the use of the **WarningAction** common parameter.</span></span>

## <span data-ttu-id="1c26c-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1c26c-110">EXAMPLES</span></span>

### <span data-ttu-id="1c26c-111">Voor beeld 1: een waarschuwings bericht schrijven</span><span class="sxs-lookup"><span data-stu-id="1c26c-111">Example 1: Write a warning message</span></span>

<span data-ttu-id="1c26c-112">Met deze opdracht wordt het bericht ' waarschuwing: dit is alleen een test waarschuwing ' weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1c26c-112">This command displays the message "WARNING: This is only a test warning."</span></span>

```powershell
Write-Warning "This is only a test warning."
```

### <span data-ttu-id="1c26c-113">Voor beeld 2: een teken reeks door geven Write-Warning</span><span class="sxs-lookup"><span data-stu-id="1c26c-113">Example 2: Pass a string to Write-Warning</span></span>

<span data-ttu-id="1c26c-114">Met deze opdracht wordt aangegeven dat u een pijplijn operator () kunt gebruiken `|` om een teken reeks naar te verzenden `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="1c26c-114">This command shows that you can use a pipeline operator (`|`) to send a string to `Write-Warning`.</span></span>
<span data-ttu-id="1c26c-115">U kunt de teken reeks in een variabele opslaan, zoals in deze opdracht wordt weer gegeven, of de teken reeks rechtstreeks naar `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="1c26c-115">You can save the string in a variable, as shown in this command, or pipe the string directly to `Write-Warning`.</span></span>

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### <span data-ttu-id="1c26c-116">Voor beeld 3: de $WarningPreference variabele instellen en een waarschuwing schrijven</span><span class="sxs-lookup"><span data-stu-id="1c26c-116">Example 3: Set the $WarningPreference variable and write a warning</span></span>

<span data-ttu-id="1c26c-117">In dit voor beeld wordt het effect van de waarde van de `$WarningPreference` variabele op een opdracht weer gegeven `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="1c26c-117">This example shows the effect of the value of the `$WarningPreference` variable on a `Write-Warning` command.</span></span>

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

<span data-ttu-id="1c26c-118">Met de eerste opdracht wordt de standaard waarde van de `$WarningPreference` variabele weer gegeven `Continue` .</span><span class="sxs-lookup"><span data-stu-id="1c26c-118">The first command displays the default value of the `$WarningPreference` variable, which is `Continue`.</span></span> <span data-ttu-id="1c26c-119">Als u een waarschuwing schrijft, wordt het waarschuwings bericht weer gegeven en wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="1c26c-119">As a result, when you write a warning, the warning message is displayed and execution continues.</span></span>

<span data-ttu-id="1c26c-120">Wanneer u de waarde van de `$WarningPreference` variabele wijzigt, wordt het effect van de `Write-Warning` opdracht opnieuw gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="1c26c-120">When you change the value of the `$WarningPreference` variable, the effect of the `Write-Warning` command changes again.</span></span> <span data-ttu-id="1c26c-121">Een waarde van `SilentlyContinue` onderdrukt de waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="1c26c-121">A value of `SilentlyContinue` suppresses the warning.</span></span> <span data-ttu-id="1c26c-122">Met de waarde `Stop` wordt de waarschuwing weer gegeven en wordt de uitvoering van de opdracht gestopt.</span><span class="sxs-lookup"><span data-stu-id="1c26c-122">A value of `Stop` displays the warning and then stops execution of the command.</span></span>

<span data-ttu-id="1c26c-123">Zie about_Preference_Variables voor meer informatie over de `$WarningPreference` variabele [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1c26c-123">For more information about the `$WarningPreference` variable, see [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="1c26c-124">Voor beeld 4: de para meter WarningAction instellen en een waarschuwing schrijven</span><span class="sxs-lookup"><span data-stu-id="1c26c-124">Example 4: Set the WarningAction parameter and write a warning</span></span>

<span data-ttu-id="1c26c-125">In dit voor beeld ziet u het effect van de algemene para meter **WarningAction** voor een `Write-Warning` opdracht.</span><span class="sxs-lookup"><span data-stu-id="1c26c-125">This example shows the effect of the **WarningAction** common parameter on a `Write-Warning` command.</span></span> <span data-ttu-id="1c26c-126">U kunt de algemene para meter **WarningAction** gebruiken met elke cmdlet om te bepalen hoe Power shell reageert op waarschuwingen die voortkomen uit die opdracht.</span><span class="sxs-lookup"><span data-stu-id="1c26c-126">You can use the **WarningAction** common parameter with any cmdlet to determine how PowerShell responds to warnings resulting from that command.</span></span> <span data-ttu-id="1c26c-127">De algemene para meter **WarningAction** overschrijft de waarde van de `$WarningPreference` enige voor die specifieke opdracht.</span><span class="sxs-lookup"><span data-stu-id="1c26c-127">The **WarningAction** common parameter overrides the value of the `$WarningPreference` only for that particular command.</span></span>

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="1c26c-128">Met deze opdracht wordt de `Write-Warning` cmdlet gebruikt om een waarschuwing weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1c26c-128">This command uses the `Write-Warning` cmdlet to display a warning.</span></span> <span data-ttu-id="1c26c-129">De gemeen schappelijke para meter **WarningAction** met de waarde query stuurt het systeem om de gebruiker te vragen wanneer de opdracht een waarschuwing weergeeft.</span><span class="sxs-lookup"><span data-stu-id="1c26c-129">The **WarningAction** common parameter with a value of Inquire directs the system to prompt the user when the command displays a warning.</span></span>

<span data-ttu-id="1c26c-130">Zie [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md)voor meer informatie over de algemene para meter **WarningAction** .</span><span class="sxs-lookup"><span data-stu-id="1c26c-130">For more information about the **WarningAction** common parameter, see [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="1c26c-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1c26c-131">PARAMETERS</span></span>

### <span data-ttu-id="1c26c-132">-Bericht</span><span class="sxs-lookup"><span data-stu-id="1c26c-132">-Message</span></span>
<span data-ttu-id="1c26c-133">Hiermee geeft u het waarschuwings bericht.</span><span class="sxs-lookup"><span data-stu-id="1c26c-133">Specifies the warning message.</span></span>

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

### <span data-ttu-id="1c26c-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1c26c-134">CommonParameters</span></span>

<span data-ttu-id="1c26c-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1c26c-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1c26c-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1c26c-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1c26c-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="1c26c-137">INPUTS</span></span>

### <span data-ttu-id="1c26c-138">System. String</span><span class="sxs-lookup"><span data-stu-id="1c26c-138">System.String</span></span>

<span data-ttu-id="1c26c-139">U kunt een teken reeks die de waarschuwing bevat, door sluizen naar `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="1c26c-139">You can pipe a string that contains the warning to `Write-Warning`.</span></span>

## <span data-ttu-id="1c26c-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1c26c-140">OUTPUTS</span></span>

### <span data-ttu-id="1c26c-141">Geen</span><span class="sxs-lookup"><span data-stu-id="1c26c-141">None</span></span>

<span data-ttu-id="1c26c-142">`Write-Warning` schrijft alleen naar de waarschuwings stroom.</span><span class="sxs-lookup"><span data-stu-id="1c26c-142">`Write-Warning` writes only to the warning stream.</span></span> <span data-ttu-id="1c26c-143">Er wordt geen andere uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1c26c-143">It does not generate any other output.</span></span>

## <span data-ttu-id="1c26c-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1c26c-144">NOTES</span></span>

<span data-ttu-id="1c26c-145">De standaard waarde voor de `$WarningPreference` variabele is `Continue` , waarbij de waarschuwing wordt weer gegeven en de opdracht vervolgens blijft uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="1c26c-145">The default value for the `$WarningPreference` variable is `Continue`, which displays the warning and then continues executing the command.</span></span> <span data-ttu-id="1c26c-146">Als u geldige waarden voor een voorkeurs variabele wilt bepalen, zoals `$WarningPreference` , stelt u deze in op een teken reeks van wille keurige tekens, zoals "ABC".</span><span class="sxs-lookup"><span data-stu-id="1c26c-146">To determine valid values for a preference variable such as `$WarningPreference`, set it to a string of random characters, such as "abc".</span></span> <span data-ttu-id="1c26c-147">Het gegenereerde fout bericht bevat een lijst met de geldige waarden.</span><span class="sxs-lookup"><span data-stu-id="1c26c-147">The resulting error message lists the valid values.</span></span>

## <span data-ttu-id="1c26c-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1c26c-148">RELATED LINKS</span></span>

[<span data-ttu-id="1c26c-149">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="1c26c-149">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="1c26c-150">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="1c26c-150">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="1c26c-151">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="1c26c-151">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="1c26c-152">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="1c26c-152">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="1c26c-153">Write-host</span><span class="sxs-lookup"><span data-stu-id="1c26c-153">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="1c26c-154">Write-Information</span><span class="sxs-lookup"><span data-stu-id="1c26c-154">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="1c26c-155">Write-output</span><span class="sxs-lookup"><span data-stu-id="1c26c-155">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="1c26c-156">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="1c26c-156">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="1c26c-157">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="1c26c-157">Write-Verbose</span></span>](Write-Verbose.md)
