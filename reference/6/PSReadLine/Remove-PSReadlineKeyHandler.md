---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: 6a15e829f589fbccf0da3479a22f24cdf3fc81ae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250668"
---
# <span data-ttu-id="7e14d-103">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7e14d-103">Remove-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="7e14d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7e14d-104">SYNOPSIS</span></span>
<span data-ttu-id="7e14d-105">Hiermee verwijdert u een sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="7e14d-105">Removes a key binding.</span></span>

## <span data-ttu-id="7e14d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7e14d-106">SYNTAX</span></span>

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## <span data-ttu-id="7e14d-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7e14d-107">DESCRIPTION</span></span>

<span data-ttu-id="7e14d-108">Met de `Remove-PSReadLineKeyHandler` cmdlet wordt een opgegeven toetsbinding verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e14d-108">The `Remove-PSReadLineKeyHandler` cmdlet removes a specified key binding.</span></span>

## <span data-ttu-id="7e14d-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7e14d-109">EXAMPLES</span></span>

### <span data-ttu-id="7e14d-110">Voor beeld 1: een binding verwijderen</span><span class="sxs-lookup"><span data-stu-id="7e14d-110">Example 1: Remove a binding</span></span>

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

<span data-ttu-id="7e14d-111">Met deze opdracht wordt de binding van de toetscombinatie, of koorde, verwijderd `Ctrl+B` .</span><span class="sxs-lookup"><span data-stu-id="7e14d-111">This command removes the binding from the key combination, or chord, `Ctrl+B`.</span></span> <span data-ttu-id="7e14d-112">De `Ctrl+B` koorde wordt in het `Set-PSReadLineKeyHandler` artikel gemaakt.</span><span class="sxs-lookup"><span data-stu-id="7e14d-112">The `Ctrl+B` chord is created in the `Set-PSReadLineKeyHandler` article.</span></span>

## <span data-ttu-id="7e14d-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7e14d-113">PARAMETERS</span></span>

### <span data-ttu-id="7e14d-114">-Koord</span><span class="sxs-lookup"><span data-stu-id="7e14d-114">-Chord</span></span>

<span data-ttu-id="7e14d-115">Hiermee geeft u een matrix op met sleutels of reeksen van sleutels die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7e14d-115">Specifies an array of keys or sequences of keys to be removed.</span></span> <span data-ttu-id="7e14d-116">Er wordt één binding opgegeven met behulp van één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="7e14d-116">A single binding is specified by using a single string.</span></span> <span data-ttu-id="7e14d-117">Als de binding een reeks sleutels is, scheidt u de sleutels met een komma, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="7e14d-117">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+x,Ctrl+l`

<span data-ttu-id="7e14d-118">Deze para meter accepteert een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="7e14d-118">This parameter accepts an array of strings.</span></span> <span data-ttu-id="7e14d-119">Elke teken reeks is een afzonderlijke binding, geen reeks sleutels voor één binding.</span><span class="sxs-lookup"><span data-stu-id="7e14d-119">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7e14d-120">-ViMode</span><span class="sxs-lookup"><span data-stu-id="7e14d-120">-ViMode</span></span>

<span data-ttu-id="7e14d-121">Geef op op welke VI-modus de binding van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="7e14d-121">Specify which vi mode the binding applies to.</span></span> <span data-ttu-id="7e14d-122">Mogelijke waarden zijn: insert en Command.</span><span class="sxs-lookup"><span data-stu-id="7e14d-122">Possible values are: Insert, Command.</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7e14d-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e14d-123">CommonParameters</span></span>

<span data-ttu-id="7e14d-124">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e14d-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e14d-125">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7e14d-125">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e14d-126">INVOER</span><span class="sxs-lookup"><span data-stu-id="7e14d-126">INPUTS</span></span>

### <span data-ttu-id="7e14d-127">Geen</span><span class="sxs-lookup"><span data-stu-id="7e14d-127">None</span></span>

<span data-ttu-id="7e14d-128">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="7e14d-128">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="7e14d-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7e14d-129">OUTPUTS</span></span>

### <span data-ttu-id="7e14d-130">Geen</span><span class="sxs-lookup"><span data-stu-id="7e14d-130">None</span></span>

## <span data-ttu-id="7e14d-131">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7e14d-131">NOTES</span></span>

## <span data-ttu-id="7e14d-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7e14d-132">RELATED LINKS</span></span>

[<span data-ttu-id="7e14d-133">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7e14d-133">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="7e14d-134">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="7e14d-134">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="7e14d-135">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="7e14d-135">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="7e14d-136">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7e14d-136">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
