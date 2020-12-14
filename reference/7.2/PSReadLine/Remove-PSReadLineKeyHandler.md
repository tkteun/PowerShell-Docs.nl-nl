---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: d280eba2e717ccfb0b896d62f42079390d1db848
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705575"
---
# <span data-ttu-id="acb38-102">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="acb38-102">Remove-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="acb38-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="acb38-103">SYNOPSIS</span></span>
<span data-ttu-id="acb38-104">Hiermee verwijdert u een sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="acb38-104">Removes a key binding.</span></span>

## <span data-ttu-id="acb38-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="acb38-105">SYNTAX</span></span>

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## <span data-ttu-id="acb38-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="acb38-106">DESCRIPTION</span></span>

<span data-ttu-id="acb38-107">Met de `Remove-PSReadLineKeyHandler` cmdlet wordt een opgegeven toetsbinding verwijderd.</span><span class="sxs-lookup"><span data-stu-id="acb38-107">The `Remove-PSReadLineKeyHandler` cmdlet removes a specified key binding.</span></span>

## <span data-ttu-id="acb38-108">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="acb38-108">EXAMPLES</span></span>

### <span data-ttu-id="acb38-109">Voor beeld 1: een binding verwijderen</span><span class="sxs-lookup"><span data-stu-id="acb38-109">Example 1: Remove a binding</span></span>

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

<span data-ttu-id="acb38-110">Met deze opdracht wordt de binding van de toetscombinatie, of koorde, verwijderd `Ctrl+B` .</span><span class="sxs-lookup"><span data-stu-id="acb38-110">This command removes the binding from the key combination, or chord, `Ctrl+B`.</span></span> <span data-ttu-id="acb38-111">De `Ctrl+B` koorde wordt in het `Set-PSReadLineKeyHandler` artikel gemaakt.</span><span class="sxs-lookup"><span data-stu-id="acb38-111">The `Ctrl+B` chord is created in the `Set-PSReadLineKeyHandler` article.</span></span>

## <span data-ttu-id="acb38-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="acb38-112">PARAMETERS</span></span>

### <span data-ttu-id="acb38-113">-Koord</span><span class="sxs-lookup"><span data-stu-id="acb38-113">-Chord</span></span>

<span data-ttu-id="acb38-114">Hiermee geeft u een matrix op met sleutels of reeksen van sleutels die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="acb38-114">Specifies an array of keys or sequences of keys to be removed.</span></span> <span data-ttu-id="acb38-115">Er wordt één binding opgegeven met behulp van één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="acb38-115">A single binding is specified by using a single string.</span></span> <span data-ttu-id="acb38-116">Als de binding een reeks sleutels is, scheidt u de sleutels met een komma, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="acb38-116">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+x,Ctrl+l`

<span data-ttu-id="acb38-117">Deze para meter accepteert een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="acb38-117">This parameter accepts an array of strings.</span></span> <span data-ttu-id="acb38-118">Elke teken reeks is een afzonderlijke binding, geen reeks sleutels voor één binding.</span><span class="sxs-lookup"><span data-stu-id="acb38-118">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

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

### <span data-ttu-id="acb38-119">-ViMode</span><span class="sxs-lookup"><span data-stu-id="acb38-119">-ViMode</span></span>

<span data-ttu-id="acb38-120">Geef op op welke VI-modus de binding van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="acb38-120">Specify which vi mode the binding applies to.</span></span> <span data-ttu-id="acb38-121">Mogelijke waarden zijn: insert en Command.</span><span class="sxs-lookup"><span data-stu-id="acb38-121">Possible values are: Insert, Command.</span></span>

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

### <span data-ttu-id="acb38-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="acb38-122">CommonParameters</span></span>

<span data-ttu-id="acb38-123">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="acb38-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="acb38-124">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="acb38-124">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="acb38-125">INVOER</span><span class="sxs-lookup"><span data-stu-id="acb38-125">INPUTS</span></span>

### <span data-ttu-id="acb38-126">Geen</span><span class="sxs-lookup"><span data-stu-id="acb38-126">None</span></span>

<span data-ttu-id="acb38-127">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="acb38-127">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="acb38-128">UITVOER</span><span class="sxs-lookup"><span data-stu-id="acb38-128">OUTPUTS</span></span>

### <span data-ttu-id="acb38-129">Geen</span><span class="sxs-lookup"><span data-stu-id="acb38-129">None</span></span>

## <span data-ttu-id="acb38-130">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="acb38-130">NOTES</span></span>

## <span data-ttu-id="acb38-131">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="acb38-131">RELATED LINKS</span></span>

[<span data-ttu-id="acb38-132">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="acb38-132">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="acb38-133">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="acb38-133">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="acb38-134">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="acb38-134">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="acb38-135">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="acb38-135">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

