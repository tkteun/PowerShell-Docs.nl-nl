---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 9da33bcf0bc1142859d547debedfb242819041aa
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2020
ms.locfileid: "93253265"
---
# <span data-ttu-id="1bd33-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="1bd33-103">Get-Clipboard</span></span>

## <span data-ttu-id="1bd33-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1bd33-104">SYNOPSIS</span></span>
<span data-ttu-id="1bd33-105">Hiermee haalt u de inhoud van het klem bord.</span><span class="sxs-lookup"><span data-stu-id="1bd33-105">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="1bd33-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1bd33-106">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="1bd33-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1bd33-107">DESCRIPTION</span></span>

<span data-ttu-id="1bd33-108">`Get-Clipboard`Met de cmdlet wordt de inhoud van het klem bord opgehaald als tekst.</span><span class="sxs-lookup"><span data-stu-id="1bd33-108">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="1bd33-109">Meerdere tekst regels worden geretourneerd als een matrix met teken reeksen die vergelijkbaar zijn met `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="1bd33-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="1bd33-110">Op Linux moet voor deze cmdlet het `xclip` hulp programma zich in het pad bevinden.</span><span class="sxs-lookup"><span data-stu-id="1bd33-110">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="1bd33-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1bd33-111">EXAMPLES</span></span>

### <span data-ttu-id="1bd33-112">Voor beeld 1: de inhoud van het klem bord ophalen en weer geven op de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="1bd33-112">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="1bd33-113">In dit voor beeld is de tekst ' Hello ' naar het klem bord gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="1bd33-113">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="1bd33-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1bd33-114">PARAMETERS</span></span>

### <span data-ttu-id="1bd33-115">-RAW</span><span class="sxs-lookup"><span data-stu-id="1bd33-115">-Raw</span></span>

<span data-ttu-id="1bd33-116">Hiermee haalt u de volledige inhoud van het klem bord.</span><span class="sxs-lookup"><span data-stu-id="1bd33-116">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="1bd33-117">Tekst met meerdere regels wordt geretourneerd als één teken reeks in plaats van een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1bd33-117">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="1bd33-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1bd33-118">CommonParameters</span></span>

<span data-ttu-id="1bd33-119">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1bd33-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1bd33-120">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1bd33-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1bd33-121">INVOER</span><span class="sxs-lookup"><span data-stu-id="1bd33-121">INPUTS</span></span>

## <span data-ttu-id="1bd33-122">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1bd33-122">OUTPUTS</span></span>

### <span data-ttu-id="1bd33-123">System. String</span><span class="sxs-lookup"><span data-stu-id="1bd33-123">System.String</span></span>

## <span data-ttu-id="1bd33-124">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1bd33-124">NOTES</span></span>

## <span data-ttu-id="1bd33-125">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1bd33-125">RELATED LINKS</span></span>

[<span data-ttu-id="1bd33-126">Set-klem bord</span><span class="sxs-lookup"><span data-stu-id="1bd33-126">Set-Clipboard</span></span>](Set-Clipboard.md)
