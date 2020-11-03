---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 8e0c1057a4117eb60cdc8ec494470dacaca78699
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "93251416"
---
# <span data-ttu-id="c0336-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="c0336-103">Read-Host</span></span>

## <span data-ttu-id="c0336-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c0336-104">SYNOPSIS</span></span>
<span data-ttu-id="c0336-105">Hiermee wordt een regel invoer uit de-console gelezen.</span><span class="sxs-lookup"><span data-stu-id="c0336-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="c0336-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c0336-106">SYNTAX</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="c0336-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c0336-107">DESCRIPTION</span></span>

<span data-ttu-id="c0336-108">De `Read-Host` cmdlet leest een regel invoer van de-console.</span><span class="sxs-lookup"><span data-stu-id="c0336-108">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="c0336-109">U kunt deze gebruiken om een gebruiker te vragen om invoer.</span><span class="sxs-lookup"><span data-stu-id="c0336-109">You can use it to prompt a user for input.</span></span> <span data-ttu-id="c0336-110">Omdat u de invoer kunt opslaan als een beveiligde teken reeks, kunt u deze cmdlet gebruiken om gebruikers te vragen voor beveiligde gegevens, zoals wacht woorden, en gedeelde gegevens.</span><span class="sxs-lookup"><span data-stu-id="c0336-110">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="c0336-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c0336-111">EXAMPLES</span></span>

### <span data-ttu-id="c0336-112">Voor beeld 1: console-invoer opslaan in een variabele</span><span class="sxs-lookup"><span data-stu-id="c0336-112">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="c0336-113">In dit voor beeld wordt de teken reeks "Voer uw leeftijd:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0336-113">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="c0336-114">Wanneer een waarde wordt ingevoerd en de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen in de `$Age` variabele.</span><span class="sxs-lookup"><span data-stu-id="c0336-114">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="c0336-115">Voor beeld 2: de console-invoer opslaan als een veilige teken reeks</span><span class="sxs-lookup"><span data-stu-id="c0336-115">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="c0336-116">In dit voor beeld wordt de teken reeks "Voer een wacht woord:" als prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c0336-116">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="c0336-117">Als er een waarde wordt ingevoerd, worden sterretjes ( `*` ) op de console weer gegeven in plaats van de invoer.</span><span class="sxs-lookup"><span data-stu-id="c0336-117">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="c0336-118">Wanneer de Enter-toets wordt ingedrukt, wordt de waarde opgeslagen als een **SecureString** -object in de `$pwd_secure_string` variabele.</span><span class="sxs-lookup"><span data-stu-id="c0336-118">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## <span data-ttu-id="c0336-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c0336-119">PARAMETERS</span></span>

### <span data-ttu-id="c0336-120">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="c0336-120">-AsSecureString</span></span>

<span data-ttu-id="c0336-121">Geeft aan dat de cmdlet sterretjes ( `*` ) weergeeft in plaats van de tekens die de gebruiker typt als invoer.</span><span class="sxs-lookup"><span data-stu-id="c0336-121">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="c0336-122">Wanneer u deze para meter gebruikt, is de uitvoer van de `Read-Host` cmdlet een **SecureString** -object ( **System. Security. SecureString** ).</span><span class="sxs-lookup"><span data-stu-id="c0336-122">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object ( **System.Security.SecureString** ).</span></span>

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

### <span data-ttu-id="c0336-123">-Prompt</span><span class="sxs-lookup"><span data-stu-id="c0336-123">-Prompt</span></span>

<span data-ttu-id="c0336-124">Hiermee geeft u de tekst van de prompt.</span><span class="sxs-lookup"><span data-stu-id="c0336-124">Specifies the text of the prompt.</span></span>
<span data-ttu-id="c0336-125">Typ een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c0336-125">Type a string.</span></span>
<span data-ttu-id="c0336-126">Als de teken reeks spaties bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="c0336-126">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="c0336-127">Power shell voegt een dubbele punt ( `:` ) toe aan de tekst die u invoert.</span><span class="sxs-lookup"><span data-stu-id="c0336-127">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="c0336-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0336-128">CommonParameters</span></span>

<span data-ttu-id="c0336-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c0336-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0336-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c0336-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0336-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="c0336-131">INPUTS</span></span>

### <span data-ttu-id="c0336-132">Geen</span><span class="sxs-lookup"><span data-stu-id="c0336-132">None</span></span>

<span data-ttu-id="c0336-133">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0336-133">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c0336-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c0336-134">OUTPUTS</span></span>

### <span data-ttu-id="c0336-135">System. String of System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="c0336-135">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="c0336-136">Als de para meter **AsSecureString** wordt gebruikt, `Read-Host` retourneert een **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="c0336-136">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="c0336-137">Anders wordt een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c0336-137">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="c0336-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c0336-138">NOTES</span></span>

## <span data-ttu-id="c0336-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c0336-139">RELATED LINKS</span></span>

[<span data-ttu-id="c0336-140">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="c0336-140">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="c0336-141">Get-host</span><span class="sxs-lookup"><span data-stu-id="c0336-141">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="c0336-142">Write-host</span><span class="sxs-lookup"><span data-stu-id="c0336-142">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="c0336-143">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="c0336-143">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
