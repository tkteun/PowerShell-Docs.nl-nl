---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 1ee55dfaf4ecd3e46bedd8f356b1f677180c9c62
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564551"
---
# <span data-ttu-id="3a369-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="3a369-103">Set-Clipboard</span></span>

## <span data-ttu-id="3a369-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3a369-104">SYNOPSIS</span></span>
<span data-ttu-id="3a369-105">Hiermee stelt u de inhoud van het klem bord.</span><span class="sxs-lookup"><span data-stu-id="3a369-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="3a369-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3a369-106">SYNTAX</span></span>

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3a369-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3a369-107">DESCRIPTION</span></span>

<span data-ttu-id="3a369-108">`Set-Clipboard`Met de cmdlet wordt de inhoud van het klem bord ingesteld.</span><span class="sxs-lookup"><span data-stu-id="3a369-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="3a369-109">Op Linux moet voor deze cmdlet het `xclip` hulp programma zich in het pad bevinden.</span><span class="sxs-lookup"><span data-stu-id="3a369-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="3a369-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3a369-110">EXAMPLES</span></span>

### <span data-ttu-id="3a369-111">Voor beeld 1: tekst naar het klem bord kopiëren</span><span class="sxs-lookup"><span data-stu-id="3a369-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="3a369-112">Voor beeld 2: de inhoud van een bestand naar het klem bord kopiëren</span><span class="sxs-lookup"><span data-stu-id="3a369-112">Example 2: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="3a369-113">In dit voor beeld wordt de inhoud van een bestand naar het klem bord gesluizen.</span><span class="sxs-lookup"><span data-stu-id="3a369-113">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="3a369-114">In dit voor beeld krijgen we een open bare SSH-sleutel, zodat deze kan worden geplakt in een andere toepassing, zoals GitHub.</span><span class="sxs-lookup"><span data-stu-id="3a369-114">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="3a369-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3a369-115">PARAMETERS</span></span>

### <span data-ttu-id="3a369-116">-Toevoegen</span><span class="sxs-lookup"><span data-stu-id="3a369-116">-Append</span></span>

<span data-ttu-id="3a369-117">Geeft aan dat het klem bord niet wordt gewist door de cmdlet en er inhoud aan wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3a369-117">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="3a369-118">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3a369-118">-Confirm</span></span>

<span data-ttu-id="3a369-119">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3a369-119">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3a369-120">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3a369-120">-WhatIf</span></span>

<span data-ttu-id="3a369-121">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="3a369-121">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3a369-122">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3a369-122">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3a369-123">-Waarde</span><span class="sxs-lookup"><span data-stu-id="3a369-123">-Value</span></span>

<span data-ttu-id="3a369-124">De teken reeks waarden die moeten worden toegevoegd aan het klem bord.</span><span class="sxs-lookup"><span data-stu-id="3a369-124">The string values to be added to the clipboard.</span></span>

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

### <span data-ttu-id="3a369-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3a369-125">CommonParameters</span></span>

<span data-ttu-id="3a369-126">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3a369-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3a369-127">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3a369-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3a369-128">INVOER</span><span class="sxs-lookup"><span data-stu-id="3a369-128">INPUTS</span></span>

### <span data-ttu-id="3a369-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="3a369-129">System.String[]</span></span>

## <span data-ttu-id="3a369-130">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3a369-130">OUTPUTS</span></span>

## <span data-ttu-id="3a369-131">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3a369-131">NOTES</span></span>

<span data-ttu-id="3a369-132">In zeldzame gevallen wanneer `Set-Clipboard` u met een groot aantal waarden snel achter elkaar gebruikt, bijvoorbeeld in een lus, kunt u sporadisch een lege waarde uit het klem bord halen.</span><span class="sxs-lookup"><span data-stu-id="3a369-132">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="3a369-133">Dit kan worden opgelost door `Start-Sleep -Milliseconds 1` in de lus te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3a369-133">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="3a369-134">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3a369-134">RELATED LINKS</span></span>

[<span data-ttu-id="3a369-135">Get-klem bord</span><span class="sxs-lookup"><span data-stu-id="3a369-135">Get-Clipboard</span></span>](Get-Clipboard.md)
