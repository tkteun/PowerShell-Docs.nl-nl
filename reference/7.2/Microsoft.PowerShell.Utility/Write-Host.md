---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: 01d045a6254b40161462bf36976fdbf57f205705
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705687"
---
# <span data-ttu-id="e93e6-102">Write-Host</span><span class="sxs-lookup"><span data-stu-id="e93e6-102">Write-Host</span></span>

## <span data-ttu-id="e93e6-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e93e6-103">SYNOPSIS</span></span>

<span data-ttu-id="e93e6-104">Hiermee wordt de aangepaste uitvoer naar een host geschreven.</span><span class="sxs-lookup"><span data-stu-id="e93e6-104">Writes customized output to a host.</span></span>

## <span data-ttu-id="e93e6-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e93e6-105">SYNTAX</span></span>

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## <span data-ttu-id="e93e6-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e93e6-106">DESCRIPTION</span></span>

<span data-ttu-id="e93e6-107">Het `Write-Host` primaire doel van de cmdlet is het maken van een-op-(host)-alleen-weer gave-uitvoer, zoals het afdrukken van gekleurde tekst wanneer de gebruiker wordt gevraagd om in combi natie met [Read-host](Read-Host.md)te worden ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="e93e6-107">The `Write-Host` cmdlet's primary purpose is to produce for-(host)-display-only output, such as printing colored text like when prompting the user for input in conjunction with [Read-Host](Read-Host.md).</span></span>
<span data-ttu-id="e93e6-108">`Write-Host` maakt gebruik van de methode [toString ()](/dotnet/api/system.object.tostring) om de uitvoer te schrijven.</span><span class="sxs-lookup"><span data-stu-id="e93e6-108">`Write-Host` uses the [ToString()](/dotnet/api/system.object.tostring) method to write the output.</span></span> <span data-ttu-id="e93e6-109">Als u daarentegen gegevens naar de pijp lijn wilt uitvoeren, kunt u gebruikmaken van [Write-output](Write-Output.md) of impliciete uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e93e6-109">By contrast, to output data to the pipeline, use [Write-Output](Write-Output.md) or implicit output.</span></span>

<span data-ttu-id="e93e6-110">U kunt de kleur van tekst opgeven met behulp van de `ForegroundColor` para meter en u kunt de achtergrond kleur opgeven met behulp van de `BackgroundColor` para meter.</span><span class="sxs-lookup"><span data-stu-id="e93e6-110">You can specify the color of text by using the `ForegroundColor` parameter, and you can specify the background color by using the `BackgroundColor` parameter.</span></span> <span data-ttu-id="e93e6-111">Met de scheidings parameter kunt u een teken reeks opgeven die moet worden gebruikt voor het scheiden van weer gegeven objecten.</span><span class="sxs-lookup"><span data-stu-id="e93e6-111">The Separator parameter lets you specify a string to use to separate displayed objects.</span></span> <span data-ttu-id="e93e6-112">Het specifieke resultaat is afhankelijk van het programma dat Power shell host.</span><span class="sxs-lookup"><span data-stu-id="e93e6-112">The particular result depends on the program that is hosting PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="e93e6-113">Met ingang van Windows Power shell 5,0 `Write-Host` is een wrapper waarmee `Write-Information` u `Write-Host` de uitvoer naar de informatie stroom kunt verzenden.</span><span class="sxs-lookup"><span data-stu-id="e93e6-113">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="e93e6-114">Hierdoor kan het **vastleggen** of **onderdrukken** van gegevens die zijn geschreven met behoud van `Write-Host` achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="e93e6-114">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span>
>
> <span data-ttu-id="e93e6-115">De `$InformationPreference` Voorkeurs variabele en de `InformationAction` algemene para meter zijn niet van invloed op `Write-Host` berichten.</span><span class="sxs-lookup"><span data-stu-id="e93e6-115">The `$InformationPreference` preference variable and `InformationAction` common parameter do not affect `Write-Host` messages.</span></span> <span data-ttu-id="e93e6-116">De uitzonde ring op deze regel is `-InformationAction Ignore` , waarmee uitvoer effectief wordt onderdrukt `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="e93e6-116">The exception to this rule is `-InformationAction Ignore`, which effectively suppresses `Write-Host` output.</span></span> <span data-ttu-id="e93e6-117">(zie "voor beeld 5")</span><span class="sxs-lookup"><span data-stu-id="e93e6-117">(see "Example 5")</span></span>

## <span data-ttu-id="e93e6-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e93e6-118">EXAMPLES</span></span>

### <span data-ttu-id="e93e6-119">Voor beeld 1: naar de console schrijven zonder een nieuwe regel toe te voegen</span><span class="sxs-lookup"><span data-stu-id="e93e6-119">Example 1: Write to the console without adding a new line</span></span>

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

<span data-ttu-id="e93e6-120">Met deze opdracht wordt de teken reeks ' geen nieuwe regel test ' weer gegeven met de `NoNewline` para meter.</span><span class="sxs-lookup"><span data-stu-id="e93e6-120">This command displays the string 'no newline test' with the `NoNewline` parameter.</span></span>

<span data-ttu-id="e93e6-121">Er wordt een tweede teken reeks geschreven, maar deze eindigt op dezelfde lijn als de eerste omdat de teken reeksen niet worden gescheiden door een nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="e93e6-121">A second string is written, but it ends up on the same line as the first due to the absence of a newline separating the strings.</span></span>

### <span data-ttu-id="e93e6-122">Voor beeld 2: schrijven naar de-console en een scheidings teken toevoegen</span><span class="sxs-lookup"><span data-stu-id="e93e6-122">Example 2: Write to the console and include a separator</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

Met deze opdracht worden de even nummers van twee tot en met 12 weer gegeven. <span data-ttu-id="e93e6-124">De **scheidings** parameter wordt gebruikt om de teken reeks `, +2= ` (komma, spatie,, `+` `2` , `=` , spatie) toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="e93e6-124">The **Separator** parameter is used to add the string `, +2= ` (comma, space, `+`, `2`, `=`, space).</span></span>

### <span data-ttu-id="e93e6-125">Voor beeld 3: schrijven met andere tekst-en achtergrond kleuren</span><span class="sxs-lookup"><span data-stu-id="e93e6-125">Example 3: Write with different text and background colors</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

<span data-ttu-id="e93e6-126">Met deze opdracht worden de even nummers van twee tot en met 12 weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e93e6-126">This command displays the even numbers from two through twelve.</span></span> <span data-ttu-id="e93e6-127">De `ForegroundColor` para meter wordt gebruikt voor het uitvoeren van donker groene tekst en de `BackgroundColor` para meter om een witte achtergrond weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e93e6-127">It uses the `ForegroundColor` parameter to output dark green text and the `BackgroundColor` parameter to display a white background.</span></span>

### <span data-ttu-id="e93e6-128">Voor beeld 4: schrijven met andere tekst-en achtergrond kleuren</span><span class="sxs-lookup"><span data-stu-id="e93e6-128">Example 4: Write with different text and background colors</span></span>

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

<span data-ttu-id="e93e6-129">Met deze opdracht wordt de teken reeks "rood op witte tekst" weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e93e6-129">This command displays the string "Red on white text."</span></span> <span data-ttu-id="e93e6-130">De tekst is rood, zoals gedefinieerd door de `ForegroundColor` para meter.</span><span class="sxs-lookup"><span data-stu-id="e93e6-130">The text is red, as defined by the `ForegroundColor` parameter.</span></span> <span data-ttu-id="e93e6-131">De achtergrond is wit, zoals gedefinieerd door de `BackgroundColor` para meter.</span><span class="sxs-lookup"><span data-stu-id="e93e6-131">The background is white, as defined by the `BackgroundColor` parameter.</span></span>

### <span data-ttu-id="e93e6-132">Voor beeld 5: uitvoer van Write-Host onderdrukken</span><span class="sxs-lookup"><span data-stu-id="e93e6-132">Example 5: Suppress output from Write-Host</span></span>

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

<span data-ttu-id="e93e6-133">Met deze opdrachten wordt de uitvoer van de cmdlet in feite onderdrukt `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="e93e6-133">These commands effectively suppress output of the `Write-Host` cmdlet.</span></span> <span data-ttu-id="e93e6-134">De eerste gebruikt de `InformationAction` para meter met de `Ignore` waarde om de uitvoer naar de informatie stroom te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="e93e6-134">The first one uses the `InformationAction` parameter with the `Ignore` Value to suppress output to the information stream.</span></span>
<span data-ttu-id="e93e6-135">In het tweede voor beeld wordt de informatie stroom van de opdracht omgeleid naar de `$null` variabele, waardoor deze wordt onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="e93e6-135">The second example redirects the information stream of the command to the `$null` variable and thereby suppresses it.</span></span>

## <span data-ttu-id="e93e6-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e93e6-136">PARAMETERS</span></span>

### <span data-ttu-id="e93e6-137">-BackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e93e6-137">-BackgroundColor</span></span>

<span data-ttu-id="e93e6-138">Hiermee geeft u de achtergrondkleur.</span><span class="sxs-lookup"><span data-stu-id="e93e6-138">Specifies the background color.</span></span> <span data-ttu-id="e93e6-139">Er is geen standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="e93e6-139">There is no default.</span></span> <span data-ttu-id="e93e6-140">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="e93e6-140">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e93e6-141">Zwart</span><span class="sxs-lookup"><span data-stu-id="e93e6-141">Black</span></span>
- <span data-ttu-id="e93e6-142">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="e93e6-142">DarkBlue</span></span>
- <span data-ttu-id="e93e6-143">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="e93e6-143">DarkGreen</span></span>
- <span data-ttu-id="e93e6-144">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="e93e6-144">DarkCyan</span></span>
- <span data-ttu-id="e93e6-145">DarkRed</span><span class="sxs-lookup"><span data-stu-id="e93e6-145">DarkRed</span></span>
- <span data-ttu-id="e93e6-146">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="e93e6-146">DarkMagenta</span></span>
- <span data-ttu-id="e93e6-147">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="e93e6-147">DarkYellow</span></span>
- <span data-ttu-id="e93e6-148">Grijs</span><span class="sxs-lookup"><span data-stu-id="e93e6-148">Gray</span></span>
- <span data-ttu-id="e93e6-149">DarkGray</span><span class="sxs-lookup"><span data-stu-id="e93e6-149">DarkGray</span></span>
- <span data-ttu-id="e93e6-150">Blauw</span><span class="sxs-lookup"><span data-stu-id="e93e6-150">Blue</span></span>
- <span data-ttu-id="e93e6-151">Green</span><span class="sxs-lookup"><span data-stu-id="e93e6-151">Green</span></span>
- <span data-ttu-id="e93e6-152">Hoeveelheid</span><span class="sxs-lookup"><span data-stu-id="e93e6-152">Cyan</span></span>
- <span data-ttu-id="e93e6-153">Rood</span><span class="sxs-lookup"><span data-stu-id="e93e6-153">Red</span></span>
- <span data-ttu-id="e93e6-154">Magenta</span><span class="sxs-lookup"><span data-stu-id="e93e6-154">Magenta</span></span>
- <span data-ttu-id="e93e6-155">Geel</span><span class="sxs-lookup"><span data-stu-id="e93e6-155">Yellow</span></span>
- <span data-ttu-id="e93e6-156">Wit</span><span class="sxs-lookup"><span data-stu-id="e93e6-156">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e93e6-157">-ForegroundColor</span><span class="sxs-lookup"><span data-stu-id="e93e6-157">-ForegroundColor</span></span>

<span data-ttu-id="e93e6-158">Geeft de tekst kleur aan.</span><span class="sxs-lookup"><span data-stu-id="e93e6-158">Specifies the text color.</span></span> <span data-ttu-id="e93e6-159">Er is geen standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="e93e6-159">There is no default.</span></span> <span data-ttu-id="e93e6-160">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="e93e6-160">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e93e6-161">Zwart</span><span class="sxs-lookup"><span data-stu-id="e93e6-161">Black</span></span>
- <span data-ttu-id="e93e6-162">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="e93e6-162">DarkBlue</span></span>
- <span data-ttu-id="e93e6-163">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="e93e6-163">DarkGreen</span></span>
- <span data-ttu-id="e93e6-164">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="e93e6-164">DarkCyan</span></span>
- <span data-ttu-id="e93e6-165">DarkRed</span><span class="sxs-lookup"><span data-stu-id="e93e6-165">DarkRed</span></span>
- <span data-ttu-id="e93e6-166">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="e93e6-166">DarkMagenta</span></span>
- <span data-ttu-id="e93e6-167">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="e93e6-167">DarkYellow</span></span>
- <span data-ttu-id="e93e6-168">Grijs</span><span class="sxs-lookup"><span data-stu-id="e93e6-168">Gray</span></span>
- <span data-ttu-id="e93e6-169">DarkGray</span><span class="sxs-lookup"><span data-stu-id="e93e6-169">DarkGray</span></span>
- <span data-ttu-id="e93e6-170">Blauw</span><span class="sxs-lookup"><span data-stu-id="e93e6-170">Blue</span></span>
- <span data-ttu-id="e93e6-171">Green</span><span class="sxs-lookup"><span data-stu-id="e93e6-171">Green</span></span>
- <span data-ttu-id="e93e6-172">Hoeveelheid</span><span class="sxs-lookup"><span data-stu-id="e93e6-172">Cyan</span></span>
- <span data-ttu-id="e93e6-173">Rood</span><span class="sxs-lookup"><span data-stu-id="e93e6-173">Red</span></span>
- <span data-ttu-id="e93e6-174">Magenta</span><span class="sxs-lookup"><span data-stu-id="e93e6-174">Magenta</span></span>
- <span data-ttu-id="e93e6-175">Geel</span><span class="sxs-lookup"><span data-stu-id="e93e6-175">Yellow</span></span>
- <span data-ttu-id="e93e6-176">Wit</span><span class="sxs-lookup"><span data-stu-id="e93e6-176">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e93e6-177">-Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="e93e6-177">-NoNewline</span></span>

<span data-ttu-id="e93e6-178">De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen.</span><span class="sxs-lookup"><span data-stu-id="e93e6-178">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="e93e6-179">Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="e93e6-179">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="e93e6-180">Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e93e6-180">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="e93e6-181">-Object</span><span class="sxs-lookup"><span data-stu-id="e93e6-181">-Object</span></span>

<span data-ttu-id="e93e6-182">Objecten die moeten worden weer gegeven op de host.</span><span class="sxs-lookup"><span data-stu-id="e93e6-182">Objects to display in the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e93e6-183">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="e93e6-183">-Separator</span></span>

<span data-ttu-id="e93e6-184">Hiermee geeft u een scheidings teken reeks moet worden ingevoegd tussen objecten die worden weer gegeven door de host.</span><span class="sxs-lookup"><span data-stu-id="e93e6-184">Specifies a separator string to insert between objects displayed by the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e93e6-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e93e6-185">CommonParameters</span></span>
<span data-ttu-id="e93e6-186">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e93e6-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e93e6-187">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e93e6-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e93e6-188">INVOER</span><span class="sxs-lookup"><span data-stu-id="e93e6-188">INPUTS</span></span>

### <span data-ttu-id="e93e6-189">System. object</span><span class="sxs-lookup"><span data-stu-id="e93e6-189">System.Object</span></span>

<span data-ttu-id="e93e6-190">U kunt objecten pipeen die naar de host moeten worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="e93e6-190">You can pipe objects to be written to the host.</span></span>

## <span data-ttu-id="e93e6-191">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e93e6-191">OUTPUTS</span></span>

### <span data-ttu-id="e93e6-192">Geen</span><span class="sxs-lookup"><span data-stu-id="e93e6-192">None</span></span>

<span data-ttu-id="e93e6-193">`Write-Host` Hiermee worden de objecten naar de host verzonden.</span><span class="sxs-lookup"><span data-stu-id="e93e6-193">`Write-Host` sends the objects to the host.</span></span> <span data-ttu-id="e93e6-194">Er worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e93e6-194">It does not return any objects.</span></span> <span data-ttu-id="e93e6-195">De host geeft echter de objecten weer die `Write-Host` ernaar worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="e93e6-195">However, the host displays the objects that `Write-Host` sends to it.</span></span>

## <span data-ttu-id="e93e6-196">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e93e6-196">NOTES</span></span>

- <span data-ttu-id="e93e6-197">Wanneer u een verzameling naar de host schrijft, worden elementen van de verzameling op dezelfde regel afgedrukt, gescheiden door één spatie.</span><span class="sxs-lookup"><span data-stu-id="e93e6-197">When writing a collection to the host, elements of the collection are printed on the same line separated by a single space.</span></span> <span data-ttu-id="e93e6-198">Dit kan worden overschreven met de **scheidings** parameter.</span><span class="sxs-lookup"><span data-stu-id="e93e6-198">This can be overridden with the **Separator** parameter.</span></span>

- <span data-ttu-id="e93e6-199">Niet-primitieve gegevens typen zoals objecten met eigenschappen kunnen leiden tot onverwachte resultaten en bieden geen zinvolle uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e93e6-199">Non-primitive data types such as objects with properties can cause unexpected results and not provide meaningful output.</span></span> <span data-ttu-id="e93e6-200">Bijvoorbeeld, `Write-Host @{a = 1; b = 2}` wordt afgedrukt `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` op de host.</span><span class="sxs-lookup"><span data-stu-id="e93e6-200">For example, `Write-Host @{a = 1; b = 2}` will print `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` to the host.</span></span>

## <span data-ttu-id="e93e6-201">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e93e6-201">RELATED LINKS</span></span>

[<span data-ttu-id="e93e6-202">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="e93e6-202">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="e93e6-203">Out-host</span><span class="sxs-lookup"><span data-stu-id="e93e6-203">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="e93e6-204">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="e93e6-204">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="e93e6-205">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="e93e6-205">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="e93e6-206">Write-output</span><span class="sxs-lookup"><span data-stu-id="e93e6-206">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="e93e6-207">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="e93e6-207">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="e93e6-208">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="e93e6-208">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="e93e6-209">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="e93e6-209">Write-Warning</span></span>](Write-Warning.md)
