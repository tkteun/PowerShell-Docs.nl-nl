---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 4f5a5705c726aef7150b734a6265308a5915decb
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685593"
---
# <span data-ttu-id="d6d91-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="d6d91-103">Read-Host</span></span>

## <span data-ttu-id="d6d91-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d6d91-104">SYNOPSIS</span></span>
<span data-ttu-id="d6d91-105">Hiermee wordt een regel invoer uit de-console gelezen.</span><span class="sxs-lookup"><span data-stu-id="d6d91-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="d6d91-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d6d91-106">SYNTAX</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="d6d91-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d6d91-107">DESCRIPTION</span></span>

<span data-ttu-id="d6d91-108">De `Read-Host` cmdlet leest een regel invoer van de-console.</span><span class="sxs-lookup"><span data-stu-id="d6d91-108">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="d6d91-109">U kunt deze gebruiken om een gebruiker te vragen om invoer.</span><span class="sxs-lookup"><span data-stu-id="d6d91-109">You can use it to prompt a user for input.</span></span> <span data-ttu-id="d6d91-110">Omdat u de invoer kunt opslaan als een beveiligde teken reeks, kunt u deze cmdlet gebruiken om gebruikers te vragen voor beveiligde gegevens, zoals wacht woorden, en gedeelde gegevens.</span><span class="sxs-lookup"><span data-stu-id="d6d91-110">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

> [!NOTE]
> <span data-ttu-id="d6d91-111">`Read-Host` heeft een limiet van 1022 tekens die kan worden geaccepteerd als invoer van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d6d91-111">`Read-Host` has a limit of 1022 characters it can accept as input from a user.</span></span>

## <span data-ttu-id="d6d91-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d6d91-112">EXAMPLES</span></span>

### <span data-ttu-id="d6d91-113">Voor beeld 1: console-invoer opslaan in een variabele</span><span class="sxs-lookup"><span data-stu-id="d6d91-113">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="d6d91-114">In dit voor beeld wordt de teken reeks "Voer uw leeftijd:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d6d91-114">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="d6d91-115">Wanneer een waarde wordt ingevoerd en de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen in de `$Age` variabele.</span><span class="sxs-lookup"><span data-stu-id="d6d91-115">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="d6d91-116">Voor beeld 2: de console-invoer opslaan als een veilige teken reeks</span><span class="sxs-lookup"><span data-stu-id="d6d91-116">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="d6d91-117">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d6d91-117">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="d6d91-118">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="d6d91-118">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="d6d91-119">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **SecureString** -object in de `$pwd_secure_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="d6d91-119">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## <span data-ttu-id="d6d91-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d6d91-120">PARAMETERS</span></span>

### <span data-ttu-id="d6d91-121">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="d6d91-121">-AsSecureString</span></span>

<span data-ttu-id="d6d91-122">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="d6d91-122">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="d6d91-123">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **SecureString** -object (**System. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="d6d91-123">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="d6d91-124">-Prompt</span><span class="sxs-lookup"><span data-stu-id="d6d91-124">-Prompt</span></span>

<span data-ttu-id="d6d91-125">Hiermee geeft u de tekst van de prompt.</span><span class="sxs-lookup"><span data-stu-id="d6d91-125">Specifies the text of the prompt.</span></span> <span data-ttu-id="d6d91-126">Typ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="d6d91-126">Type a string.</span></span> <span data-ttu-id="d6d91-127">Als de teken reeks spaties bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d6d91-127">If the string includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="d6d91-128">Power shell voegt een dubbele punt ( `:` ) toe aan de tekst die u invoert.</span><span class="sxs-lookup"><span data-stu-id="d6d91-128">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="d6d91-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d6d91-129">CommonParameters</span></span>

<span data-ttu-id="d6d91-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d6d91-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d6d91-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d6d91-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d6d91-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="d6d91-132">INPUTS</span></span>

### <span data-ttu-id="d6d91-133">Geen</span><span class="sxs-lookup"><span data-stu-id="d6d91-133">None</span></span>

<span data-ttu-id="d6d91-134">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6d91-134">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d6d91-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d6d91-135">OUTPUTS</span></span>

### <span data-ttu-id="d6d91-136">System. String of System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="d6d91-136">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="d6d91-137">Als de para meter **AsSecureString** wordt gebruikt, `Read-Host` retourneert een **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="d6d91-137">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="d6d91-138">Anders wordt een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d6d91-138">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="d6d91-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d6d91-139">NOTES</span></span>

## <span data-ttu-id="d6d91-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d6d91-140">RELATED LINKS</span></span>

[<span data-ttu-id="d6d91-141">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="d6d91-141">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="d6d91-142">Get-host</span><span class="sxs-lookup"><span data-stu-id="d6d91-142">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="d6d91-143">Write-host</span><span class="sxs-lookup"><span data-stu-id="d6d91-143">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="d6d91-144">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="d6d91-144">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
