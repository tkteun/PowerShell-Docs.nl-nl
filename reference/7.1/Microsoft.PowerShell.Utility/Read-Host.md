---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: b76fc092046a29dcad52f755794fd55dd84ac675
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "93251414"
---
# <span data-ttu-id="41215-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="41215-103">Read-Host</span></span>

## <span data-ttu-id="41215-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="41215-104">SYNOPSIS</span></span>
<span data-ttu-id="41215-105">Hiermee wordt een regel invoer uit de-console gelezen.</span><span class="sxs-lookup"><span data-stu-id="41215-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="41215-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="41215-106">SYNTAX</span></span>

### <span data-ttu-id="41215-107">AsString (standaard)</span><span class="sxs-lookup"><span data-stu-id="41215-107">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="41215-108">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="41215-108">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="41215-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="41215-109">DESCRIPTION</span></span>

<span data-ttu-id="41215-110">De `Read-Host` cmdlet leest een regel invoer van de-console.</span><span class="sxs-lookup"><span data-stu-id="41215-110">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="41215-111">U kunt deze gebruiken om een gebruiker te vragen om invoer.</span><span class="sxs-lookup"><span data-stu-id="41215-111">You can use it to prompt a user for input.</span></span> <span data-ttu-id="41215-112">Omdat u de invoer kunt opslaan als een beveiligde teken reeks, kunt u deze cmdlet gebruiken om gebruikers te vragen voor beveiligde gegevens, zoals wacht woorden, en gedeelde gegevens.</span><span class="sxs-lookup"><span data-stu-id="41215-112">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="41215-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="41215-113">EXAMPLES</span></span>

### <span data-ttu-id="41215-114">Voor beeld 1: console-invoer opslaan in een variabele</span><span class="sxs-lookup"><span data-stu-id="41215-114">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="41215-115">In dit voor beeld wordt de teken reeks "Voer uw leeftijd:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="41215-115">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="41215-116">Wanneer een waarde wordt ingevoerd en de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen in de `$Age` variabele.</span><span class="sxs-lookup"><span data-stu-id="41215-116">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="41215-117">Voor beeld 2: de console-invoer opslaan als een veilige teken reeks</span><span class="sxs-lookup"><span data-stu-id="41215-117">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="41215-118">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="41215-118">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="41215-119">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="41215-119">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="41215-120">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **SecureString** -object in de `$pwd_secure_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="41215-120">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="41215-121">Voor beeld 3: masker invoer en als teken reeks zonder opmaak</span><span class="sxs-lookup"><span data-stu-id="41215-121">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="41215-122">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="41215-122">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="41215-123">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="41215-123">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="41215-124">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **teken reeks** object met tekst zonder opmaak in de `$pwd_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="41215-124">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="41215-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="41215-125">PARAMETERS</span></span>

### <span data-ttu-id="41215-126">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="41215-126">-AsSecureString</span></span>

<span data-ttu-id="41215-127">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="41215-127">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="41215-128">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **SecureString** -object ( **System. Security. SecureString** ).</span><span class="sxs-lookup"><span data-stu-id="41215-128">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object ( **System.Security.SecureString** ).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsSecureString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41215-129">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="41215-129">-MaskInput</span></span>

<span data-ttu-id="41215-130">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="41215-130">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="41215-131">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="41215-131">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="41215-132">Zo kunt u veilig vragen om een wacht woord dat als tekst wordt geretourneerd in plaats van **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="41215-132">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41215-133">-Prompt</span><span class="sxs-lookup"><span data-stu-id="41215-133">-Prompt</span></span>

<span data-ttu-id="41215-134">Hiermee geeft u de tekst van de prompt.</span><span class="sxs-lookup"><span data-stu-id="41215-134">Specifies the text of the prompt.</span></span>
<span data-ttu-id="41215-135">Typ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="41215-135">Type a string.</span></span>
<span data-ttu-id="41215-136">Als de teken reeks spaties bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="41215-136">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="41215-137">Power shell voegt een dubbele punt ( `:` ) toe aan de tekst die u invoert.</span><span class="sxs-lookup"><span data-stu-id="41215-137">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41215-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41215-138">CommonParameters</span></span>

<span data-ttu-id="41215-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41215-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41215-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="41215-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41215-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="41215-141">INPUTS</span></span>

### <span data-ttu-id="41215-142">Geen</span><span class="sxs-lookup"><span data-stu-id="41215-142">None</span></span>

<span data-ttu-id="41215-143">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41215-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="41215-144">UITVOER</span><span class="sxs-lookup"><span data-stu-id="41215-144">OUTPUTS</span></span>

### <span data-ttu-id="41215-145">System. String of System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="41215-145">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="41215-146">Als de para meter **AsSecureString** wordt gebruikt, `Read-Host` retourneert een **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="41215-146">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="41215-147">Anders wordt een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="41215-147">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="41215-148">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="41215-148">NOTES</span></span>

## <span data-ttu-id="41215-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="41215-149">RELATED LINKS</span></span>

[<span data-ttu-id="41215-150">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="41215-150">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="41215-151">Get-host</span><span class="sxs-lookup"><span data-stu-id="41215-151">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="41215-152">Write-host</span><span class="sxs-lookup"><span data-stu-id="41215-152">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="41215-153">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="41215-153">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
