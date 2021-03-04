---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 5563413400abd28ce376265970631ad1206ca518
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685259"
---
# <span data-ttu-id="aaa59-102">Read-Host</span><span class="sxs-lookup"><span data-stu-id="aaa59-102">Read-Host</span></span>

## <span data-ttu-id="aaa59-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="aaa59-103">SYNOPSIS</span></span>
<span data-ttu-id="aaa59-104">Hiermee wordt een regel invoer uit de-console gelezen.</span><span class="sxs-lookup"><span data-stu-id="aaa59-104">Reads a line of input from the console.</span></span>

## <span data-ttu-id="aaa59-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="aaa59-105">SYNTAX</span></span>

### <span data-ttu-id="aaa59-106">AsString (standaard)</span><span class="sxs-lookup"><span data-stu-id="aaa59-106">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="aaa59-107">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="aaa59-107">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="aaa59-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aaa59-108">DESCRIPTION</span></span>

<span data-ttu-id="aaa59-109">De `Read-Host` cmdlet leest een regel invoer van de-console.</span><span class="sxs-lookup"><span data-stu-id="aaa59-109">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="aaa59-110">U kunt deze gebruiken om een gebruiker te vragen om invoer.</span><span class="sxs-lookup"><span data-stu-id="aaa59-110">You can use it to prompt a user for input.</span></span> <span data-ttu-id="aaa59-111">Omdat u de invoer kunt opslaan als een beveiligde teken reeks, kunt u deze cmdlet gebruiken om gebruikers te vragen voor beveiligde gegevens, zoals wacht woorden, en gedeelde gegevens.</span><span class="sxs-lookup"><span data-stu-id="aaa59-111">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

> [!NOTE]
> <span data-ttu-id="aaa59-112">`Read-Host` heeft een limiet van 1022 tekens die kan worden geaccepteerd als invoer van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="aaa59-112">`Read-Host` has a limit of 1022 characters it can accept as input from a user.</span></span>

## <span data-ttu-id="aaa59-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="aaa59-113">EXAMPLES</span></span>

### <span data-ttu-id="aaa59-114">Voor beeld 1: console-invoer opslaan in een variabele</span><span class="sxs-lookup"><span data-stu-id="aaa59-114">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="aaa59-115">In dit voor beeld wordt de teken reeks "Voer uw leeftijd:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aaa59-115">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="aaa59-116">Wanneer een waarde wordt ingevoerd en de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen in de `$Age` variabele.</span><span class="sxs-lookup"><span data-stu-id="aaa59-116">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="aaa59-117">Voor beeld 2: de console-invoer opslaan als een veilige teken reeks</span><span class="sxs-lookup"><span data-stu-id="aaa59-117">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="aaa59-118">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aaa59-118">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="aaa59-119">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="aaa59-119">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="aaa59-120">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **SecureString** -object in de `$pwd_secure_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="aaa59-120">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="aaa59-121">Voor beeld 3: masker invoer en als teken reeks zonder opmaak</span><span class="sxs-lookup"><span data-stu-id="aaa59-121">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="aaa59-122">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aaa59-122">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="aaa59-123">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="aaa59-123">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="aaa59-124">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **teken reeks** object met tekst zonder opmaak in de `$pwd_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="aaa59-124">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="aaa59-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aaa59-125">PARAMETERS</span></span>

### <span data-ttu-id="aaa59-126">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="aaa59-126">-AsSecureString</span></span>

<span data-ttu-id="aaa59-127">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="aaa59-127">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="aaa59-128">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **SecureString** -object (**System. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="aaa59-128">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="aaa59-129">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="aaa59-129">-MaskInput</span></span>

<span data-ttu-id="aaa59-130">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="aaa59-130">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="aaa59-131">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="aaa59-131">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="aaa59-132">Zo kunt u veilig vragen om een wacht woord dat als tekst wordt geretourneerd in plaats van **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="aaa59-132">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

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

### <span data-ttu-id="aaa59-133">-Prompt</span><span class="sxs-lookup"><span data-stu-id="aaa59-133">-Prompt</span></span>

<span data-ttu-id="aaa59-134">Hiermee geeft u de tekst van de prompt.</span><span class="sxs-lookup"><span data-stu-id="aaa59-134">Specifies the text of the prompt.</span></span> <span data-ttu-id="aaa59-135">Typ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="aaa59-135">Type a string.</span></span> <span data-ttu-id="aaa59-136">Als de teken reeks spaties bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="aaa59-136">If the string includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="aaa59-137">Power shell voegt een dubbele punt ( `:` ) toe aan de tekst die u invoert.</span><span class="sxs-lookup"><span data-stu-id="aaa59-137">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="aaa59-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aaa59-138">CommonParameters</span></span>

<span data-ttu-id="aaa59-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aaa59-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aaa59-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aaa59-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aaa59-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="aaa59-141">INPUTS</span></span>

### <span data-ttu-id="aaa59-142">Geen</span><span class="sxs-lookup"><span data-stu-id="aaa59-142">None</span></span>

<span data-ttu-id="aaa59-143">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aaa59-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="aaa59-144">UITVOER</span><span class="sxs-lookup"><span data-stu-id="aaa59-144">OUTPUTS</span></span>

### <span data-ttu-id="aaa59-145">System. String of System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="aaa59-145">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="aaa59-146">Als de para meter **AsSecureString** wordt gebruikt, `Read-Host` retourneert een **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="aaa59-146">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="aaa59-147">Anders wordt een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="aaa59-147">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="aaa59-148">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="aaa59-148">NOTES</span></span>

## <span data-ttu-id="aaa59-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="aaa59-149">RELATED LINKS</span></span>

[<span data-ttu-id="aaa59-150">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="aaa59-150">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="aaa59-151">Get-host</span><span class="sxs-lookup"><span data-stu-id="aaa59-151">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="aaa59-152">Write-host</span><span class="sxs-lookup"><span data-stu-id="aaa59-152">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="aaa59-153">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="aaa59-153">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
