---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 1c799a5b0f9041d285ce0e83a98582d6888c607e
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685304"
---
# <span data-ttu-id="4af11-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="4af11-103">Read-Host</span></span>

## <span data-ttu-id="4af11-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4af11-104">SYNOPSIS</span></span>
<span data-ttu-id="4af11-105">Hiermee wordt een regel invoer uit de-console gelezen.</span><span class="sxs-lookup"><span data-stu-id="4af11-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="4af11-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4af11-106">SYNTAX</span></span>

### <span data-ttu-id="4af11-107">AsString (standaard)</span><span class="sxs-lookup"><span data-stu-id="4af11-107">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="4af11-108">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="4af11-108">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="4af11-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4af11-109">DESCRIPTION</span></span>

<span data-ttu-id="4af11-110">De `Read-Host` cmdlet leest een regel invoer van de-console.</span><span class="sxs-lookup"><span data-stu-id="4af11-110">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="4af11-111">U kunt deze gebruiken om een gebruiker te vragen om invoer.</span><span class="sxs-lookup"><span data-stu-id="4af11-111">You can use it to prompt a user for input.</span></span> <span data-ttu-id="4af11-112">Omdat u de invoer kunt opslaan als een beveiligde teken reeks, kunt u deze cmdlet gebruiken om gebruikers te vragen voor beveiligde gegevens, zoals wacht woorden, en gedeelde gegevens.</span><span class="sxs-lookup"><span data-stu-id="4af11-112">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

> [!NOTE]
> <span data-ttu-id="4af11-113">`Read-Host` heeft een limiet van 1022 tekens die kan worden geaccepteerd als invoer van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="4af11-113">`Read-Host` has a limit of 1022 characters it can accept as input from a user.</span></span>

## <span data-ttu-id="4af11-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4af11-114">EXAMPLES</span></span>

### <span data-ttu-id="4af11-115">Voor beeld 1: console-invoer opslaan in een variabele</span><span class="sxs-lookup"><span data-stu-id="4af11-115">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="4af11-116">In dit voor beeld wordt de teken reeks "Voer uw leeftijd:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4af11-116">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="4af11-117">Wanneer een waarde wordt ingevoerd en de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen in de `$Age` variabele.</span><span class="sxs-lookup"><span data-stu-id="4af11-117">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="4af11-118">Voor beeld 2: de console-invoer opslaan als een veilige teken reeks</span><span class="sxs-lookup"><span data-stu-id="4af11-118">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="4af11-119">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4af11-119">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="4af11-120">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="4af11-120">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="4af11-121">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **SecureString** -object in de `$pwd_secure_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="4af11-121">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="4af11-122">Voor beeld 3: masker invoer en als teken reeks zonder opmaak</span><span class="sxs-lookup"><span data-stu-id="4af11-122">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="4af11-123">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4af11-123">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="4af11-124">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="4af11-124">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="4af11-125">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **teken reeks** object met tekst zonder opmaak in de `$pwd_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="4af11-125">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="4af11-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4af11-126">PARAMETERS</span></span>

### <span data-ttu-id="4af11-127">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="4af11-127">-AsSecureString</span></span>

<span data-ttu-id="4af11-128">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="4af11-128">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="4af11-129">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **SecureString** -object (**System. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="4af11-129">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="4af11-130">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="4af11-130">-MaskInput</span></span>

<span data-ttu-id="4af11-131">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="4af11-131">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="4af11-132">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="4af11-132">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="4af11-133">Zo kunt u veilig vragen om een wacht woord dat als tekst wordt geretourneerd in plaats van **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="4af11-133">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

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

### <span data-ttu-id="4af11-134">-Prompt</span><span class="sxs-lookup"><span data-stu-id="4af11-134">-Prompt</span></span>

<span data-ttu-id="4af11-135">Hiermee geeft u de tekst van de prompt.</span><span class="sxs-lookup"><span data-stu-id="4af11-135">Specifies the text of the prompt.</span></span> <span data-ttu-id="4af11-136">Typ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="4af11-136">Type a string.</span></span> <span data-ttu-id="4af11-137">Als de teken reeks spaties bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="4af11-137">If the string includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="4af11-138">Power shell voegt een dubbele punt ( `:` ) toe aan de tekst die u invoert.</span><span class="sxs-lookup"><span data-stu-id="4af11-138">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="4af11-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4af11-139">CommonParameters</span></span>

<span data-ttu-id="4af11-140">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4af11-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4af11-141">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4af11-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4af11-142">INVOER</span><span class="sxs-lookup"><span data-stu-id="4af11-142">INPUTS</span></span>

### <span data-ttu-id="4af11-143">Geen</span><span class="sxs-lookup"><span data-stu-id="4af11-143">None</span></span>

<span data-ttu-id="4af11-144">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4af11-144">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="4af11-145">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4af11-145">OUTPUTS</span></span>

### <span data-ttu-id="4af11-146">System. String of System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="4af11-146">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="4af11-147">Als de para meter **AsSecureString** wordt gebruikt, `Read-Host` retourneert een **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="4af11-147">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="4af11-148">Anders wordt een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4af11-148">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="4af11-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4af11-149">NOTES</span></span>

## <span data-ttu-id="4af11-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4af11-150">RELATED LINKS</span></span>

[<span data-ttu-id="4af11-151">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="4af11-151">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="4af11-152">Get-host</span><span class="sxs-lookup"><span data-stu-id="4af11-152">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="4af11-153">Write-host</span><span class="sxs-lookup"><span data-stu-id="4af11-153">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="4af11-154">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="4af11-154">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
