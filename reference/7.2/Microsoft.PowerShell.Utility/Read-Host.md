---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 2efe75730ef7d35618dc0d1fbf7a8d6f8a5db5ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705814"
---
# <span data-ttu-id="af49d-102">Read-Host</span><span class="sxs-lookup"><span data-stu-id="af49d-102">Read-Host</span></span>

## <span data-ttu-id="af49d-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="af49d-103">SYNOPSIS</span></span>
<span data-ttu-id="af49d-104">Hiermee wordt een regel invoer uit de-console gelezen.</span><span class="sxs-lookup"><span data-stu-id="af49d-104">Reads a line of input from the console.</span></span>

## <span data-ttu-id="af49d-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="af49d-105">SYNTAX</span></span>

### <span data-ttu-id="af49d-106">AsString (standaard)</span><span class="sxs-lookup"><span data-stu-id="af49d-106">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="af49d-107">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="af49d-107">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="af49d-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="af49d-108">DESCRIPTION</span></span>

<span data-ttu-id="af49d-109">De `Read-Host` cmdlet leest een regel invoer van de-console.</span><span class="sxs-lookup"><span data-stu-id="af49d-109">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="af49d-110">U kunt deze gebruiken om een gebruiker te vragen om invoer.</span><span class="sxs-lookup"><span data-stu-id="af49d-110">You can use it to prompt a user for input.</span></span> <span data-ttu-id="af49d-111">Omdat u de invoer kunt opslaan als een beveiligde teken reeks, kunt u deze cmdlet gebruiken om gebruikers te vragen voor beveiligde gegevens, zoals wacht woorden, en gedeelde gegevens.</span><span class="sxs-lookup"><span data-stu-id="af49d-111">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="af49d-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="af49d-112">EXAMPLES</span></span>

### <span data-ttu-id="af49d-113">Voor beeld 1: console-invoer opslaan in een variabele</span><span class="sxs-lookup"><span data-stu-id="af49d-113">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="af49d-114">In dit voor beeld wordt de teken reeks "Voer uw leeftijd:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="af49d-114">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="af49d-115">Wanneer een waarde wordt ingevoerd en de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen in de `$Age` variabele.</span><span class="sxs-lookup"><span data-stu-id="af49d-115">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="af49d-116">Voor beeld 2: de console-invoer opslaan als een veilige teken reeks</span><span class="sxs-lookup"><span data-stu-id="af49d-116">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="af49d-117">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="af49d-117">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="af49d-118">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="af49d-118">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="af49d-119">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **SecureString** -object in de `$pwd_secure_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="af49d-119">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="af49d-120">Voor beeld 3: masker invoer en als teken reeks zonder opmaak</span><span class="sxs-lookup"><span data-stu-id="af49d-120">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="af49d-121">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="af49d-121">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="af49d-122">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="af49d-122">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="af49d-123">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **teken reeks** object met tekst zonder opmaak in de `$pwd_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="af49d-123">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="af49d-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="af49d-124">PARAMETERS</span></span>

### <span data-ttu-id="af49d-125">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="af49d-125">-AsSecureString</span></span>

<span data-ttu-id="af49d-126">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="af49d-126">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="af49d-127">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **SecureString** -object (**System. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="af49d-127">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="af49d-128">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="af49d-128">-MaskInput</span></span>

<span data-ttu-id="af49d-129">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="af49d-129">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="af49d-130">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="af49d-130">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="af49d-131">Zo kunt u veilig vragen om een wacht woord dat als tekst wordt geretourneerd in plaats van **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="af49d-131">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

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

### <span data-ttu-id="af49d-132">-Prompt</span><span class="sxs-lookup"><span data-stu-id="af49d-132">-Prompt</span></span>

<span data-ttu-id="af49d-133">Hiermee geeft u de tekst van de prompt.</span><span class="sxs-lookup"><span data-stu-id="af49d-133">Specifies the text of the prompt.</span></span>
<span data-ttu-id="af49d-134">Typ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="af49d-134">Type a string.</span></span>
<span data-ttu-id="af49d-135">Als de teken reeks spaties bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="af49d-135">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="af49d-136">Power shell voegt een dubbele punt ( `:` ) toe aan de tekst die u invoert.</span><span class="sxs-lookup"><span data-stu-id="af49d-136">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="af49d-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="af49d-137">CommonParameters</span></span>

<span data-ttu-id="af49d-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="af49d-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="af49d-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="af49d-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="af49d-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="af49d-140">INPUTS</span></span>

### <span data-ttu-id="af49d-141">Geen</span><span class="sxs-lookup"><span data-stu-id="af49d-141">None</span></span>

<span data-ttu-id="af49d-142">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="af49d-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="af49d-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="af49d-143">OUTPUTS</span></span>

### <span data-ttu-id="af49d-144">System. String of System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="af49d-144">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="af49d-145">Als de para meter **AsSecureString** wordt gebruikt, `Read-Host` retourneert een **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="af49d-145">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="af49d-146">Anders wordt een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="af49d-146">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="af49d-147">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="af49d-147">NOTES</span></span>

## <span data-ttu-id="af49d-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="af49d-148">RELATED LINKS</span></span>

[<span data-ttu-id="af49d-149">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="af49d-149">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="af49d-150">Get-host</span><span class="sxs-lookup"><span data-stu-id="af49d-150">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="af49d-151">Write-host</span><span class="sxs-lookup"><span data-stu-id="af49d-151">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="af49d-152">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="af49d-152">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
