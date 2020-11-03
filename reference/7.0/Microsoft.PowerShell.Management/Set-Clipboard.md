---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/09/2019
online version: https://go.microsoft.com/fwlink/?linkid=526220
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 271d9191a0968b03b1e7ec3d283eacc36e633516
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2020
ms.locfileid: "93253268"
---
# <span data-ttu-id="1043b-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="1043b-103">Set-Clipboard</span></span>

## <span data-ttu-id="1043b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1043b-104">SYNOPSIS</span></span>
<span data-ttu-id="1043b-105">Hiermee stelt u de inhoud van het klem bord.</span><span class="sxs-lookup"><span data-stu-id="1043b-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="1043b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1043b-106">SYNTAX</span></span>

```
Set-Clipboard [-Value] <string[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="1043b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1043b-107">DESCRIPTION</span></span>

<span data-ttu-id="1043b-108">`Set-Clipboard`Met de cmdlet wordt de inhoud van het klem bord ingesteld.</span><span class="sxs-lookup"><span data-stu-id="1043b-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="1043b-109">Op Linux moet voor deze cmdlet het `xclip` hulp programma zich in het pad bevinden.</span><span class="sxs-lookup"><span data-stu-id="1043b-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="1043b-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1043b-110">EXAMPLES</span></span>

### <span data-ttu-id="1043b-111">Voor beeld 1: tekst naar het klem bord kopiëren</span><span class="sxs-lookup"><span data-stu-id="1043b-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

## <span data-ttu-id="1043b-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1043b-112">PARAMETERS</span></span>

### <span data-ttu-id="1043b-113">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="1043b-113">-Append</span></span>

<span data-ttu-id="1043b-114">Geeft aan dat het klem bord niet wordt gewist door de cmdlet en er inhoud aan wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="1043b-114">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="1043b-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1043b-115">-Confirm</span></span>

<span data-ttu-id="1043b-116">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1043b-116">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1043b-117">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1043b-117">-WhatIf</span></span>

<span data-ttu-id="1043b-118">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1043b-118">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="1043b-119">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1043b-119">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1043b-120">-Waarde</span><span class="sxs-lookup"><span data-stu-id="1043b-120">-Value</span></span>

<span data-ttu-id="1043b-121">De teken reeks waarden die moeten worden toegevoegd aan het klem bord.</span><span class="sxs-lookup"><span data-stu-id="1043b-121">The string values to be added to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1043b-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1043b-122">CommonParameters</span></span>

<span data-ttu-id="1043b-123">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1043b-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1043b-124">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1043b-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1043b-125">INVOER</span><span class="sxs-lookup"><span data-stu-id="1043b-125">INPUTS</span></span>

### <span data-ttu-id="1043b-126">System.String[]</span><span class="sxs-lookup"><span data-stu-id="1043b-126">System.String[]</span></span>

## <span data-ttu-id="1043b-127">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1043b-127">OUTPUTS</span></span>

## <span data-ttu-id="1043b-128">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1043b-128">NOTES</span></span>

<span data-ttu-id="1043b-129">In zeldzame gevallen wanneer `Set-Clipboard` u met een groot aantal waarden snel achter elkaar gebruikt, bijvoorbeeld in een lus, kunt u sporadisch een lege waarde uit het klem bord halen.</span><span class="sxs-lookup"><span data-stu-id="1043b-129">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="1043b-130">Dit kan worden opgelost door `Start-Sleep -Milliseconds 1` in de lus te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1043b-130">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="1043b-131">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1043b-131">RELATED LINKS</span></span>

[<span data-ttu-id="1043b-132">Get-klem bord</span><span class="sxs-lookup"><span data-stu-id="1043b-132">Get-Clipboard</span></span>](Get-Clipboard.md)
