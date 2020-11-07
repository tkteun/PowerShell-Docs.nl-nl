---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: ed56dc5655f640dae1d80c66850581ff12dbb7ee
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347598"
---
# <span data-ttu-id="ea017-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="ea017-103">Get-Clipboard</span></span>

## <span data-ttu-id="ea017-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ea017-104">SYNOPSIS</span></span>
<span data-ttu-id="ea017-105">Hiermee haalt u de inhoud van het klem bord.</span><span class="sxs-lookup"><span data-stu-id="ea017-105">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="ea017-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ea017-106">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="ea017-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ea017-107">DESCRIPTION</span></span>

<span data-ttu-id="ea017-108">`Get-Clipboard`Met de cmdlet wordt de inhoud van het klem bord opgehaald als tekst.</span><span class="sxs-lookup"><span data-stu-id="ea017-108">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="ea017-109">Meerdere tekst regels worden geretourneerd als een matrix met teken reeksen die vergelijkbaar zijn met `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="ea017-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="ea017-110">Op Linux moet voor deze cmdlet het `xclip` hulp programma zich in het pad bevinden.</span><span class="sxs-lookup"><span data-stu-id="ea017-110">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span> <span data-ttu-id="ea017-111">Deze cmdlet wordt niet ondersteund in macOS.</span><span class="sxs-lookup"><span data-stu-id="ea017-111">This cmdlet is not supported on macOS.</span></span>

## <span data-ttu-id="ea017-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ea017-112">EXAMPLES</span></span>

### <span data-ttu-id="ea017-113">Voor beeld 1: de inhoud van het klem bord ophalen en weer geven op de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="ea017-113">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="ea017-114">In dit voor beeld is de tekst ' Hello ' naar het klem bord gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="ea017-114">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="ea017-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ea017-115">PARAMETERS</span></span>

### <span data-ttu-id="ea017-116">-RAW</span><span class="sxs-lookup"><span data-stu-id="ea017-116">-Raw</span></span>

<span data-ttu-id="ea017-117">Hiermee haalt u de volledige inhoud van het klem bord.</span><span class="sxs-lookup"><span data-stu-id="ea017-117">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="ea017-118">Tekst met meerdere regels wordt geretourneerd als één teken reeks in plaats van een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="ea017-118">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="ea017-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ea017-119">CommonParameters</span></span>

<span data-ttu-id="ea017-120">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ea017-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ea017-121">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ea017-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ea017-122">INVOER</span><span class="sxs-lookup"><span data-stu-id="ea017-122">INPUTS</span></span>

## <span data-ttu-id="ea017-123">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ea017-123">OUTPUTS</span></span>

### <span data-ttu-id="ea017-124">System. String</span><span class="sxs-lookup"><span data-stu-id="ea017-124">System.String</span></span>

## <span data-ttu-id="ea017-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ea017-125">NOTES</span></span>

## <span data-ttu-id="ea017-126">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ea017-126">RELATED LINKS</span></span>

[<span data-ttu-id="ea017-127">Set-klem bord</span><span class="sxs-lookup"><span data-stu-id="ea017-127">Set-Clipboard</span></span>](Set-Clipboard.md)
