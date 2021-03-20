---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/18/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 6a5b698b06fef4a4e8f438e21f95692d44a516e8
ms.sourcegitcommit: 16a02ae47d1a85b01692101aa0aa6e91e1ba398e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104726686"
---
# <span data-ttu-id="38fc3-102">Read-Host</span><span class="sxs-lookup"><span data-stu-id="38fc3-102">Read-Host</span></span>

## <span data-ttu-id="38fc3-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="38fc3-103">SYNOPSIS</span></span>
<span data-ttu-id="38fc3-104">Hiermee wordt een regel invoer uit de-console gelezen.</span><span class="sxs-lookup"><span data-stu-id="38fc3-104">Reads a line of input from the console.</span></span>

## <span data-ttu-id="38fc3-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="38fc3-105">SYNTAX</span></span>

### <span data-ttu-id="38fc3-106">AsString (standaard)</span><span class="sxs-lookup"><span data-stu-id="38fc3-106">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="38fc3-107">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="38fc3-107">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="38fc3-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="38fc3-108">DESCRIPTION</span></span>

<span data-ttu-id="38fc3-109">De `Read-Host` cmdlet leest een regel invoer uit de-console (stdin).</span><span class="sxs-lookup"><span data-stu-id="38fc3-109">The `Read-Host` cmdlet reads a line of input from the console (stdin).</span></span> <span data-ttu-id="38fc3-110">U kunt deze gebruiken om een gebruiker te vragen om invoer.</span><span class="sxs-lookup"><span data-stu-id="38fc3-110">You can use it to prompt a user for input.</span></span> <span data-ttu-id="38fc3-111">Omdat u de invoer kunt opslaan als een beveiligde teken reeks, kunt u deze cmdlet gebruiken om gebruikers te vragen voor beveiligde gegevens, zoals wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="38fc3-111">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords.</span></span>

> [!NOTE]
> <span data-ttu-id="38fc3-112">`Read-Host` heeft een limiet van 1022 tekens die kan worden geaccepteerd als invoer van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="38fc3-112">`Read-Host` has a limit of 1022 characters it can accept as input from a user.</span></span>

## <span data-ttu-id="38fc3-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="38fc3-113">EXAMPLES</span></span>

### <span data-ttu-id="38fc3-114">Voor beeld 1: console-invoer opslaan in een variabele</span><span class="sxs-lookup"><span data-stu-id="38fc3-114">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="38fc3-115">In dit voor beeld wordt de teken reeks "Voer uw leeftijd:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="38fc3-115">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="38fc3-116">Wanneer een waarde wordt ingevoerd en de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen in de `$Age` variabele.</span><span class="sxs-lookup"><span data-stu-id="38fc3-116">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="38fc3-117">Voor beeld 2: de console-invoer opslaan als een veilige teken reeks</span><span class="sxs-lookup"><span data-stu-id="38fc3-117">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="38fc3-118">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="38fc3-118">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="38fc3-119">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="38fc3-119">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="38fc3-120">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **SecureString** -object in de `$pwd_secure_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="38fc3-120">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="38fc3-121">Voor beeld 3: masker invoer en als teken reeks zonder opmaak</span><span class="sxs-lookup"><span data-stu-id="38fc3-121">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="38fc3-122">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="38fc3-122">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="38fc3-123">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="38fc3-123">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="38fc3-124">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **teken reeks** object met tekst zonder opmaak in de `$pwd_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="38fc3-124">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="38fc3-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38fc3-125">PARAMETERS</span></span>

### <span data-ttu-id="38fc3-126">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="38fc3-126">-AsSecureString</span></span>

<span data-ttu-id="38fc3-127">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="38fc3-127">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="38fc3-128">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **SecureString** -object (**System. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="38fc3-128">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="38fc3-129">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="38fc3-129">-MaskInput</span></span>

<span data-ttu-id="38fc3-130">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="38fc3-130">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="38fc3-131">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="38fc3-131">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="38fc3-132">Zo kunt u veilig vragen om een wacht woord dat als tekst wordt geretourneerd in plaats van **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="38fc3-132">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

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

### <span data-ttu-id="38fc3-133">-Prompt</span><span class="sxs-lookup"><span data-stu-id="38fc3-133">-Prompt</span></span>

<span data-ttu-id="38fc3-134">Hiermee geeft u de tekst van de prompt.</span><span class="sxs-lookup"><span data-stu-id="38fc3-134">Specifies the text of the prompt.</span></span> <span data-ttu-id="38fc3-135">Typ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="38fc3-135">Type a string.</span></span> <span data-ttu-id="38fc3-136">Als de teken reeks spaties bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="38fc3-136">If the string includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="38fc3-137">Power shell voegt een dubbele punt ( `:` ) toe aan de tekst die u invoert.</span><span class="sxs-lookup"><span data-stu-id="38fc3-137">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="38fc3-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38fc3-138">CommonParameters</span></span>

<span data-ttu-id="38fc3-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38fc3-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38fc3-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="38fc3-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="38fc3-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="38fc3-141">INPUTS</span></span>

### <span data-ttu-id="38fc3-142">Geen</span><span class="sxs-lookup"><span data-stu-id="38fc3-142">None</span></span>

<span data-ttu-id="38fc3-143">Deze cmdlet accepteert geen invoer van de Power shell-pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="38fc3-143">This cmdlet does not accept input from the PowerShell pipeline.</span></span>

## <span data-ttu-id="38fc3-144">UITVOER</span><span class="sxs-lookup"><span data-stu-id="38fc3-144">OUTPUTS</span></span>

### <span data-ttu-id="38fc3-145">System. String of System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="38fc3-145">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="38fc3-146">Als de para meter **AsSecureString** wordt gebruikt, `Read-Host` retourneert een **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="38fc3-146">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="38fc3-147">Anders wordt een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="38fc3-147">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="38fc3-148">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="38fc3-148">NOTES</span></span>

<span data-ttu-id="38fc3-149">Met deze cmdlet wordt alleen de stdin-stroom van het hostproces gelezen.</span><span class="sxs-lookup"><span data-stu-id="38fc3-149">This cmdlet only reads from the stdin stream of the host process.</span></span> <span data-ttu-id="38fc3-150">Normaal gesp roken is de stdin-stroom verbonden met het toetsen bord van de host-console.</span><span class="sxs-lookup"><span data-stu-id="38fc3-150">Usually, the stdin stream is connected to the keyboard of the host console.</span></span>

## <span data-ttu-id="38fc3-151">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="38fc3-151">RELATED LINKS</span></span>

[<span data-ttu-id="38fc3-152">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="38fc3-152">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="38fc3-153">Get-host</span><span class="sxs-lookup"><span data-stu-id="38fc3-153">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="38fc3-154">Write-host</span><span class="sxs-lookup"><span data-stu-id="38fc3-154">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="38fc3-155">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="38fc3-155">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
