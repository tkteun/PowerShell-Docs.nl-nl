---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: c1cf126e41a5e918afffbc41d30f957e650efdf5
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564499"
---
# <span data-ttu-id="34672-102">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="34672-102">Set-Clipboard</span></span>

## <span data-ttu-id="34672-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="34672-103">SYNOPSIS</span></span>
<span data-ttu-id="34672-104">Hiermee stelt u de huidige vermelding van het Windows-klem bord.</span><span class="sxs-lookup"><span data-stu-id="34672-104">Sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="34672-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="34672-105">SYNTAX</span></span>

### <span data-ttu-id="34672-106">Teken reeks (standaard)</span><span class="sxs-lookup"><span data-stu-id="34672-106">String (Default)</span></span>

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="34672-107">Waarde</span><span class="sxs-lookup"><span data-stu-id="34672-107">Value</span></span>

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="34672-108">Pad</span><span class="sxs-lookup"><span data-stu-id="34672-108">Path</span></span>

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="34672-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="34672-109">LiteralPath</span></span>

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="34672-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="34672-110">DESCRIPTION</span></span>

<span data-ttu-id="34672-111">Met de `Set-Clipboard` cmdlet wordt het huidige Windows klem bord-item ingesteld.</span><span class="sxs-lookup"><span data-stu-id="34672-111">The `Set-Clipboard` cmdlet sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="34672-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="34672-112">EXAMPLES</span></span>

### <span data-ttu-id="34672-113">Voor beeld 1: tekst naar het klem bord kopiëren</span><span class="sxs-lookup"><span data-stu-id="34672-113">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="34672-114">Voor beeld 2: de inhoud van een map naar het klem bord kopiëren</span><span class="sxs-lookup"><span data-stu-id="34672-114">Example 2: Copy the contents of a directory to the clipboard</span></span>

<span data-ttu-id="34672-115">In dit voor beeld wordt de inhoud van de opgegeven map naar het klem bord gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="34672-115">This example copies the content of the specified folder to the clipboard.</span></span>

```powershell
Set-Clipboard -Path "C:\Staging\"
```

### <span data-ttu-id="34672-116">Voor beeld 3: de inhoud van een bestand naar het klem bord kopiëren</span><span class="sxs-lookup"><span data-stu-id="34672-116">Example 3: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="34672-117">In dit voor beeld wordt de inhoud van een bestand naar het klem bord gesluizen.</span><span class="sxs-lookup"><span data-stu-id="34672-117">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="34672-118">In dit voor beeld krijgen we een open bare SSH-sleutel, zodat deze kan worden geplakt in een andere toepassing, zoals GitHub.</span><span class="sxs-lookup"><span data-stu-id="34672-118">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="34672-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34672-119">PARAMETERS</span></span>

### <span data-ttu-id="34672-120">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="34672-120">-Append</span></span>

<span data-ttu-id="34672-121">Geeft aan dat het klem bord niet wordt gewist door de cmdlet en er inhoud aan wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="34672-121">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="34672-122">-AsHtml</span><span class="sxs-lookup"><span data-stu-id="34672-122">-AsHtml</span></span>

<span data-ttu-id="34672-123">Geeft aan dat de cmdlet de inhoud weergeeft als HTML-bestand naar het klem bord.</span><span class="sxs-lookup"><span data-stu-id="34672-123">Indicates that the cmdlet renders the content as HTML to the clipboard.</span></span>

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

### <span data-ttu-id="34672-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="34672-124">-LiteralPath</span></span>

<span data-ttu-id="34672-125">Hiermee geeft u het pad op naar het item dat naar het klem bord wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="34672-125">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="34672-126">In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="34672-126">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="34672-127">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="34672-127">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="34672-128">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="34672-128">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="34672-129">Enkele aanhalings tekens geven aan dat Windows Power shell geen tekens interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="34672-129">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="34672-130">-Path</span><span class="sxs-lookup"><span data-stu-id="34672-130">-Path</span></span>

<span data-ttu-id="34672-131">Hiermee geeft u het pad op naar het item dat naar het klem bord wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="34672-131">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="34672-132">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="34672-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="34672-133">-Waarde</span><span class="sxs-lookup"><span data-stu-id="34672-133">-Value</span></span>

<span data-ttu-id="34672-134">Geeft als een teken reeks matrix de inhoud aan die naar het klem bord moet worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="34672-134">Specifies, as a string array, the content to copy to the clipboard.</span></span>

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

### <span data-ttu-id="34672-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="34672-135">-Confirm</span></span>

<span data-ttu-id="34672-136">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="34672-136">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="34672-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="34672-137">-WhatIf</span></span>

<span data-ttu-id="34672-138">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="34672-138">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="34672-139">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="34672-139">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="34672-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34672-140">CommonParameters</span></span>

<span data-ttu-id="34672-141">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="34672-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="34672-142">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="34672-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="34672-143">INVOER</span><span class="sxs-lookup"><span data-stu-id="34672-143">INPUTS</span></span>

### <span data-ttu-id="34672-144">System.String[]</span><span class="sxs-lookup"><span data-stu-id="34672-144">System.String[]</span></span>

## <span data-ttu-id="34672-145">UITVOER</span><span class="sxs-lookup"><span data-stu-id="34672-145">OUTPUTS</span></span>

## <span data-ttu-id="34672-146">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="34672-146">NOTES</span></span>

<span data-ttu-id="34672-147">In zeldzame gevallen wanneer `Set-Clipboard` u met een groot aantal waarden snel achter elkaar gebruikt, bijvoorbeeld in een lus, kunt u sporadisch een lege waarde uit het klem bord halen.</span><span class="sxs-lookup"><span data-stu-id="34672-147">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="34672-148">Dit kan worden opgelost door `Start-Sleep -Milliseconds 1` in de lus te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="34672-148">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="34672-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="34672-149">RELATED LINKS</span></span>

[<span data-ttu-id="34672-150">Get-klem bord</span><span class="sxs-lookup"><span data-stu-id="34672-150">Get-Clipboard</span></span>](Get-Clipboard.md)
