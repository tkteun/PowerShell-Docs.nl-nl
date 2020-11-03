---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: f3230c247296d5fd907d580e719cbbbc560183a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250560"
---
# <span data-ttu-id="095c9-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="095c9-103">Set-Clipboard</span></span>

## <span data-ttu-id="095c9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="095c9-104">SYNOPSIS</span></span>
<span data-ttu-id="095c9-105">Hiermee stelt u de huidige vermelding van het Windows-klem bord.</span><span class="sxs-lookup"><span data-stu-id="095c9-105">Sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="095c9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="095c9-106">SYNTAX</span></span>

### <span data-ttu-id="095c9-107">Teken reeks (standaard)</span><span class="sxs-lookup"><span data-stu-id="095c9-107">String (Default)</span></span>

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="095c9-108">Waarde</span><span class="sxs-lookup"><span data-stu-id="095c9-108">Value</span></span>

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="095c9-109">Pad</span><span class="sxs-lookup"><span data-stu-id="095c9-109">Path</span></span>

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="095c9-110">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="095c9-110">LiteralPath</span></span>

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="095c9-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="095c9-111">DESCRIPTION</span></span>

<span data-ttu-id="095c9-112">Met de `Set-Clipboard` cmdlet wordt het huidige Windows klem bord-item ingesteld.</span><span class="sxs-lookup"><span data-stu-id="095c9-112">The `Set-Clipboard` cmdlet sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="095c9-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="095c9-113">EXAMPLES</span></span>

### <span data-ttu-id="095c9-114">Voor beeld 1: tekst naar het klem bord kopiëren</span><span class="sxs-lookup"><span data-stu-id="095c9-114">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="095c9-115">Voor beeld 2: de inhoud van een map naar het klem bord kopiëren</span><span class="sxs-lookup"><span data-stu-id="095c9-115">Example 2: Copy the contents of a directory to the clipboard</span></span>

<span data-ttu-id="095c9-116">Met deze opdracht wordt de inhoud van de opgegeven map naar het klem bord gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="095c9-116">This command copies the content of the specified folder to the clipboard.</span></span>

```powershell
Set-Clipboard -Path "C:\Staging\"
```

## <span data-ttu-id="095c9-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="095c9-117">PARAMETERS</span></span>

### <span data-ttu-id="095c9-118">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="095c9-118">-Append</span></span>

<span data-ttu-id="095c9-119">Geeft aan dat het klem bord niet wordt gewist door de cmdlet en er inhoud aan wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="095c9-119">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="095c9-120">-AsHtml</span><span class="sxs-lookup"><span data-stu-id="095c9-120">-AsHtml</span></span>

<span data-ttu-id="095c9-121">Geeft aan dat de cmdlet de inhoud weergeeft als HTML-bestand naar het klem bord.</span><span class="sxs-lookup"><span data-stu-id="095c9-121">Indicates that the cmdlet renders the content as HTML to the clipboard.</span></span>

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

### <span data-ttu-id="095c9-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="095c9-122">-LiteralPath</span></span>

<span data-ttu-id="095c9-123">Hiermee geeft u het pad op naar het item dat naar het klem bord wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="095c9-123">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="095c9-124">In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="095c9-124">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="095c9-125">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="095c9-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="095c9-126">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="095c9-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="095c9-127">Enkele aanhalings tekens geven aan dat Windows Power shell geen tekens interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="095c9-127">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="095c9-128">-Path</span><span class="sxs-lookup"><span data-stu-id="095c9-128">-Path</span></span>

<span data-ttu-id="095c9-129">Hiermee geeft u het pad op naar het item dat naar het klem bord wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="095c9-129">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="095c9-130">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="095c9-130">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="095c9-131">-Waarde</span><span class="sxs-lookup"><span data-stu-id="095c9-131">-Value</span></span>

<span data-ttu-id="095c9-132">Geeft als een teken reeks matrix de inhoud aan die naar het klem bord moet worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="095c9-132">Specifies, as a string array, the content to copy to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Value
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="095c9-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="095c9-133">-Confirm</span></span>

<span data-ttu-id="095c9-134">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="095c9-134">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="095c9-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="095c9-135">-WhatIf</span></span>

<span data-ttu-id="095c9-136">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="095c9-136">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="095c9-137">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="095c9-137">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="095c9-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="095c9-138">CommonParameters</span></span>

<span data-ttu-id="095c9-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="095c9-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="095c9-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="095c9-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="095c9-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="095c9-141">INPUTS</span></span>

### <span data-ttu-id="095c9-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="095c9-142">System.String[]</span></span>

## <span data-ttu-id="095c9-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="095c9-143">OUTPUTS</span></span>

## <span data-ttu-id="095c9-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="095c9-144">NOTES</span></span>

<span data-ttu-id="095c9-145">In zeldzame gevallen wanneer `Set-Clipboard` u met een groot aantal waarden snel achter elkaar gebruikt, bijvoorbeeld in een lus, kunt u sporadisch een lege waarde uit het klem bord halen.</span><span class="sxs-lookup"><span data-stu-id="095c9-145">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="095c9-146">Dit kan worden opgelost door `Start-Sleep -Milliseconds 1` in de lus te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="095c9-146">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="095c9-147">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="095c9-147">RELATED LINKS</span></span>

[<span data-ttu-id="095c9-148">Get-klem bord</span><span class="sxs-lookup"><span data-stu-id="095c9-148">Get-Clipboard</span></span>](Get-Clipboard.md)
