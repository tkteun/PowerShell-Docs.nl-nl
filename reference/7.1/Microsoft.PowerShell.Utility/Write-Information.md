---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: 2c6d9a66a7253af4621053a9006730dce856353c
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253020"
---
# <span data-ttu-id="c4343-103">Write-Information</span><span class="sxs-lookup"><span data-stu-id="c4343-103">Write-Information</span></span>

## <span data-ttu-id="c4343-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c4343-104">SYNOPSIS</span></span>

<span data-ttu-id="c4343-105">Hiermee geeft u op hoe Power shell gegevens streamen voor een opdracht verwerkt.</span><span class="sxs-lookup"><span data-stu-id="c4343-105">Specifies how PowerShell handles information stream data for a command.</span></span>

## <span data-ttu-id="c4343-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c4343-106">SYNTAX</span></span>

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="c4343-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c4343-107">DESCRIPTION</span></span>

<span data-ttu-id="c4343-108">Met de `Write-Information` cmdlet geeft u op hoe Power shell gegevens streamen voor een opdracht verwerkt.</span><span class="sxs-lookup"><span data-stu-id="c4343-108">The `Write-Information` cmdlet specifies how PowerShell handles information stream data for a command.</span></span>

<span data-ttu-id="c4343-109">Windows Power shell 5,0 introduceert een nieuwe, gestructureerde informatie stroom.</span><span class="sxs-lookup"><span data-stu-id="c4343-109">Windows PowerShell 5.0 introduces a new, structured information stream.</span></span> <span data-ttu-id="c4343-110">U kunt deze stroom gebruiken om gestructureerde gegevens te verzenden tussen een script en de aanroepers of de hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="c4343-110">You can use this stream to transmit structured data between a script and its callers or the host application.</span></span>
<span data-ttu-id="c4343-111">`Write-Information` Hiermee kunt u een informatief bericht toevoegen aan de stream en opgeven hoe Power shell gegevens streamen voor een opdracht verwerkt.</span><span class="sxs-lookup"><span data-stu-id="c4343-111">`Write-Information` lets you add an informational message to the stream, and specify how PowerShell handles information stream data for a command.</span></span> <span data-ttu-id="c4343-112">Informatie stromen werkt ook voor `PowerShell.Streams` , taken en geplande taken.</span><span class="sxs-lookup"><span data-stu-id="c4343-112">Information streams also work for `PowerShell.Streams`, jobs, and scheduled tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="c4343-113">De informatie stroom volgt niet de standaard Conventie voor het voor voegsel van de berichten met ' [Stream name]: '.</span><span class="sxs-lookup"><span data-stu-id="c4343-113">The information stream does not follow the standard convention of prefixing its messages with "[Stream Name]:".</span></span> <span data-ttu-id="c4343-114">Dit is bedoeld voor het gezichts boog en het visuele goed.</span><span class="sxs-lookup"><span data-stu-id="c4343-114">This was intended for brevity and visual cleanliness.</span></span>

<span data-ttu-id="c4343-115">De `$InformationPreference` waarde van de voorkeurs variabele bepaalt of het bericht dat u opgeeft `Write-Information` , wordt weer gegeven op het verwachte punt in de bewerking van een script.</span><span class="sxs-lookup"><span data-stu-id="c4343-115">The `$InformationPreference` preference variable value determines whether the message you provide to `Write-Information` is displayed at the expected point in a script's operation.</span></span> <span data-ttu-id="c4343-116">Omdat de standaard waarde van deze variabele `SilentlyContinue` standaard is, worden informatieve berichten niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c4343-116">Because the default value of this variable is `SilentlyContinue`, by default, informational messages are not shown.</span></span> <span data-ttu-id="c4343-117">Als u de waarde van niet wilt wijzigen `$InformationPreference` , kunt u de waarde ervan overschrijven door de `InformationAction` para meter common toe te voegen aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c4343-117">If you don't want to change the value of `$InformationPreference`, you can override its value by adding the `InformationAction` common parameter to your command.</span></span> <span data-ttu-id="c4343-118">Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) en [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c4343-118">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) and [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c4343-119">Met ingang van Windows Power shell 5,0 `Write-Host` is een wrapper waarmee `Write-Information` u `Write-Host` de uitvoer naar de informatie stroom kunt verzenden.</span><span class="sxs-lookup"><span data-stu-id="c4343-119">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="c4343-120">Hierdoor kan het **vastleggen** of **onderdrukken** van gegevens die zijn geschreven met behoud van `Write-Host` achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="c4343-120">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span> <span data-ttu-id="c4343-121">Zie [Write-host (Engelstalig)](Write-Host.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c4343-121">For more information see [Write-Host](Write-Host.md)</span></span>

<span data-ttu-id="c4343-122">`Write-Information` is ook een ondersteunde werk stroom activiteit in Power shell 5. x.</span><span class="sxs-lookup"><span data-stu-id="c4343-122">`Write-Information` is also a supported workflow activity in PowerShell 5.x.</span></span>

## <span data-ttu-id="c4343-123">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c4343-123">EXAMPLES</span></span>

### <span data-ttu-id="c4343-124">Voor beeld 1: informatie schrijven voor Get-Results</span><span class="sxs-lookup"><span data-stu-id="c4343-124">Example 1: Write information for Get- results</span></span>

<span data-ttu-id="c4343-125">In dit voor beeld ziet u een informatief bericht ' kreeg uw functies! ', na het uitvoeren `Get-WindowsFeature` van de opdracht om alle functies te vinden met een naam waarde die begint met ' p '.</span><span class="sxs-lookup"><span data-stu-id="c4343-125">In this example, you show an informational message, "Got your features!", after running the `Get-WindowsFeature` command to find all features that have a Name value that starts with 'p'.</span></span>
<span data-ttu-id="c4343-126">Omdat de `$InformationPreference` variabele nog steeds is ingesteld op de standaard instelling, `SilentlyContinue` voegt u de `InformationAction` para meter toe om de waarde te overschrijven `$InformationPreference` en wordt het bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c4343-126">Because the `$InformationPreference` variable is still set to its default, `SilentlyContinue`, you add the `InformationAction` parameter to override the `$InformationPreference` value, and show the message.</span></span> <span data-ttu-id="c4343-127">De `InformationAction` waarde wordt voortgezet, wat betekent dat uw bericht wordt weer gegeven, maar het script of de opdracht wordt voortgezet als dit nog niet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="c4343-127">The `InformationAction` value is Continue, which means that your message is shown, but the script or command continues, if it is not yet finished.</span></span>

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### <span data-ttu-id="c4343-128">Voor beeld 2: gegevens schrijven en deze labelen</span><span class="sxs-lookup"><span data-stu-id="c4343-128">Example 2: Write information and tag it</span></span>

<span data-ttu-id="c4343-129">In dit voor beeld gebruikt u `Write-Information` om gebruikers te laten weten dat ze een andere opdracht moeten uitvoeren nadat ze klaar zijn met het uitvoeren van de huidige opdracht.</span><span class="sxs-lookup"><span data-stu-id="c4343-129">In this example, you use `Write-Information` to let users know they'll need to run another command after they're done running the current command.</span></span> <span data-ttu-id="c4343-130">In het voor beeld worden de label instructies aan het informatie bericht toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="c4343-130">The example adds the tag Instructions to the informational message.</span></span> <span data-ttu-id="c4343-131">Als u na het uitvoeren van deze opdracht de informatie stroom doorzoekt naar berichten met instructies, is het bericht dat u hier hebt opgegeven, onder de resultaten.</span><span class="sxs-lookup"><span data-stu-id="c4343-131">After running this command, if you search the information stream for messages tagged Instructions, the message specified here would be among the results.</span></span>

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### <span data-ttu-id="c4343-132">Voor beeld 3: gegevens naar een bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="c4343-132">Example 3: Write information to a file</span></span>

<span data-ttu-id="c4343-133">In dit voor beeld leidt u de gegevens stroom in de functie om naar een `Info.txt` met behulp van de code `6>` .</span><span class="sxs-lookup"><span data-stu-id="c4343-133">In this example, you redirect the information stream in the function to a `Info.txt` using the code `6>`.</span></span> <span data-ttu-id="c4343-134">Wanneer u het `Info.txt` bestand opent, ziet u de tekst ' hier gaat u '.</span><span class="sxs-lookup"><span data-stu-id="c4343-134">When you open the `Info.txt` file, you see the text, "Here you go."</span></span>

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

### <span data-ttu-id="c4343-135">Voor beeld 4: object door geven om informatie te schrijven</span><span class="sxs-lookup"><span data-stu-id="c4343-135">Example 4: Pass object to write information</span></span>

<span data-ttu-id="c4343-136">In dit voor beeld kunt u gebruiken `Write-Information` om de tien beste processen voor CPU-gebruik te schrijven van de `Get-Process` object uitvoer die door meerdere pijp lijnen wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="c4343-136">In this example, you can use `Write-Information` to write the top 10 highest CPU utilization processes from the `Get-Process` object output that has passes through multiple pipelines.</span></span>

```powershell
Get-Process | Sort-Object CPU -Descending |
    Select-Object Id, ProcessName, CPU -First 10 |
        Write-Information -InformationAction Continue
```

```Output
@{Id=12692; ProcessName=chrome; CPU=39431.296875}
@{Id=21292; ProcessName=OUTLOOK; CPU=23991.875}
@{Id=10548; ProcessName=CefSharp.BrowserSubprocess; CPU=20546.203125}
@{Id=312848; ProcessName=Taskmgr; CPU=13173.1875}
@{Id=10848; ProcessName=SnapClient; CPU=7014.265625}
@{Id=9760; ProcessName=Receiver; CPU=6792.359375}
@{Id=12040; ProcessName=Teams; CPU=5605.578125}
@{Id=498388; ProcessName=chrome; CPU=3062.453125}
@{Id=6900; ProcessName=chrome; CPU=2546.9375}
@{Id=9044; ProcessName=explorer; CPU=2358.765625}
```

## <span data-ttu-id="c4343-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c4343-137">PARAMETERS</span></span>

### <span data-ttu-id="c4343-138">-MessageData</span><span class="sxs-lookup"><span data-stu-id="c4343-138">-MessageData</span></span>

<span data-ttu-id="c4343-139">Hiermee geeft u een informatief bericht op dat u wilt weer geven aan gebruikers wanneer ze een script of opdracht uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c4343-139">Specifies an informational message that you want to display to users as they run a script or command.</span></span> <span data-ttu-id="c4343-140">Voor de beste resultaten plaatst u het informatie bericht tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="c4343-140">For best results, enclose the informational message in quotation marks.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c4343-141">-Tags</span><span class="sxs-lookup"><span data-stu-id="c4343-141">-Tags</span></span>

<span data-ttu-id="c4343-142">Hiermee geeft u een eenvoudige teken reeks op die u kunt gebruiken om berichten die u aan de informatie stroom hebt toegevoegd, te sorteren en te filteren `Write-Information` .</span><span class="sxs-lookup"><span data-stu-id="c4343-142">Specifies a simple string that you can use to sort and filter messages that you have added to the information stream with `Write-Information`.</span></span> <span data-ttu-id="c4343-143">Deze para meter werkt op dezelfde manier als de **labels** -para meter in `New-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="c4343-143">This parameter works similarly to the **Tags** parameter in `New-ModuleManifest`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4343-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4343-144">CommonParameters</span></span>

<span data-ttu-id="c4343-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c4343-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4343-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c4343-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4343-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="c4343-147">INPUTS</span></span>

### <span data-ttu-id="c4343-148">System. object</span><span class="sxs-lookup"><span data-stu-id="c4343-148">System.Object</span></span>

<span data-ttu-id="c4343-149">`Write-Information` Hiermee worden objecten van het pipet geaccepteerd om aan de informatie stroom te worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="c4343-149">`Write-Information` accepts piped objects to pass to the information stream.</span></span>

## <span data-ttu-id="c4343-150">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c4343-150">OUTPUTS</span></span>

### <span data-ttu-id="c4343-151">System. Management. Automation. InformationRecord</span><span class="sxs-lookup"><span data-stu-id="c4343-151">System.Management.Automation.InformationRecord</span></span>

## <span data-ttu-id="c4343-152">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c4343-152">NOTES</span></span>

## <span data-ttu-id="c4343-153">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c4343-153">RELATED LINKS</span></span>

[<span data-ttu-id="c4343-154">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="c4343-154">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="c4343-155">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="c4343-155">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="c4343-156">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4343-156">about_CommonParameters</span></span>](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[<span data-ttu-id="c4343-157">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="c4343-157">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="c4343-158">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="c4343-158">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="c4343-159">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="c4343-159">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="c4343-160">Write-host</span><span class="sxs-lookup"><span data-stu-id="c4343-160">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="c4343-161">Write-Information</span><span class="sxs-lookup"><span data-stu-id="c4343-161">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="c4343-162">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="c4343-162">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="c4343-163">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="c4343-163">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="c4343-164">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="c4343-164">Write-Warning</span></span>](Write-Warning.md)

[<span data-ttu-id="c4343-165">Write-output</span><span class="sxs-lookup"><span data-stu-id="c4343-165">Write-Output</span></span>](Write-Output.md)
