---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlinekeyhandler?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineKeyHandler
ms.openlocfilehash: 09a34993df29ab06a9d25e6d66770e5774bd28b0
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253174"
---
# <span data-ttu-id="d1700-103">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d1700-103">Get-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="d1700-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d1700-104">SYNOPSIS</span></span>
<span data-ttu-id="d1700-105">Hiermee haalt u de gebonden-sleutel functies voor de PSReadLine-module op.</span><span class="sxs-lookup"><span data-stu-id="d1700-105">Gets the bound key functions for the PSReadLine module.</span></span>

## <span data-ttu-id="d1700-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d1700-106">SYNTAX</span></span>

### <span data-ttu-id="d1700-107">FullListing (standaard)</span><span class="sxs-lookup"><span data-stu-id="d1700-107">FullListing (default)</span></span>

```
Get-PSReadLineKeyHandler [-Bound] [-Unbound] [<CommonParameters>]
```

### <span data-ttu-id="d1700-108">SpecificBindings</span><span class="sxs-lookup"><span data-stu-id="d1700-108">SpecificBindings</span></span>

```
Get-PSReadLineKeyHandler [-Chord] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="d1700-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d1700-109">DESCRIPTION</span></span>

<span data-ttu-id="d1700-110">Als er geen para meter is opgegeven, worden de momenteel gebonden sleutel functies voor de PSReadLine-module geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d1700-110">If no parameter is specified, returns the currently bound key functions for the PSReadLine module.</span></span>

<span data-ttu-id="d1700-111">Als de para meter **koord** is opgegeven, retourneert de cmdlet de specifieke gebonden sleutels.</span><span class="sxs-lookup"><span data-stu-id="d1700-111">If **Chord** parameter is specified, the cmdlet returns the specific bound keys.</span></span>

## <span data-ttu-id="d1700-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d1700-112">EXAMPLES</span></span>

### <span data-ttu-id="d1700-113">Voor beeld 1: alle toetstoewijzingen ophalen</span><span class="sxs-lookup"><span data-stu-id="d1700-113">Example 1: Get all key mappings</span></span>

<span data-ttu-id="d1700-114">Met deze opdracht worden alle toetstoewijzingen, gebonden en niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d1700-114">This command returns all key mappings, bound and unbound.</span></span>

```powershell
Get-PSReadLineKeyHandler -Bound -Unbound
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
Shift+Tab             TabCompletePrevious     Complete the input using the previous completion
Ctrl+a                SelectAll               Select the entire line. Moves the cursor to the end of the line
Ctrl+c                CopyOrCancelLine        Either copy selected text to the clipboard, or if no text is selected, cancel editing the line with Cancel...
Ctrl+C                Copy                    Copy selected region to the system clipboard.  If no region is selected, copy the whole line
Ctrl+l                ClearScreen             Clear the screen and redraw the current line at the top of the screen
Ctrl+r                ReverseSearchHistory    Search history backwards interactively
...
```

### <span data-ttu-id="d1700-115">Voor beeld 2: gebonden sleutels ophalen</span><span class="sxs-lookup"><span data-stu-id="d1700-115">Example 2: Get bound keys</span></span>

<span data-ttu-id="d1700-116">Met deze opdracht worden alleen gebonden toetsen en toetscombinaties geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d1700-116">This command returns only bound keys and key combinations.</span></span>

```powershell
Get-PSReadLineKeyHandler
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
...
```

### <span data-ttu-id="d1700-117">Voor beeld 3: specifieke sleutel bindingen ophalen</span><span class="sxs-lookup"><span data-stu-id="d1700-117">Example 3: Get specific key bindings</span></span>

<span data-ttu-id="d1700-118">Met deze opdracht worden alleen de bindingen voor de opgegeven sleutels geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d1700-118">This command returns only the bindings for the specified keys.</span></span>

```powershell
Get-PSReadLineKeyHandler -Chord Enter, Shift+Enter
```

```Output
Key         Function   Description
---         --------   -----------
Enter       AcceptLine Accept the input or move to the next line if input is missing a closing token.
Shift+Enter AddLine    Move the cursor to the next line without attempting to execute the input
...
```

## <span data-ttu-id="d1700-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d1700-119">PARAMETERS</span></span>

### <span data-ttu-id="d1700-120">-Gebonden</span><span class="sxs-lookup"><span data-stu-id="d1700-120">-Bound</span></span>

<span data-ttu-id="d1700-121">Geeft aan dat deze cmdlet functies retourneert die gebonden zijn.</span><span class="sxs-lookup"><span data-stu-id="d1700-121">Indicates that this cmdlet returns functions that are bound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d1700-122">-Niet-afhankelijk</span><span class="sxs-lookup"><span data-stu-id="d1700-122">-Unbound</span></span>

<span data-ttu-id="d1700-123">Geeft aan dat met deze cmdlet functies worden geretourneerd die niet afhankelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="d1700-123">Indicates that this cmdlet returns functions that are unbound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d1700-124">-Koord</span><span class="sxs-lookup"><span data-stu-id="d1700-124">-Chord</span></span>

<span data-ttu-id="d1700-125">Alleen functies retour neren die zijn gebonden aan specifieke sleutels of reeksen.</span><span class="sxs-lookup"><span data-stu-id="d1700-125">Return only functions bound to specific keys or sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SpecificBindings
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d1700-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d1700-126">CommonParameters</span></span>

<span data-ttu-id="d1700-127">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d1700-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d1700-128">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d1700-128">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d1700-129">INVOER</span><span class="sxs-lookup"><span data-stu-id="d1700-129">INPUTS</span></span>

### <span data-ttu-id="d1700-130">Geen</span><span class="sxs-lookup"><span data-stu-id="d1700-130">None</span></span>

<span data-ttu-id="d1700-131">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="d1700-131">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="d1700-132">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d1700-132">OUTPUTS</span></span>

### <span data-ttu-id="d1700-133">Micro soft. Power shell.</span><span class="sxs-lookup"><span data-stu-id="d1700-133">Microsoft.PowerShell.KeyHandler</span></span>

## <span data-ttu-id="d1700-134">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d1700-134">NOTES</span></span>

## <span data-ttu-id="d1700-135">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d1700-135">RELATED LINKS</span></span>

[<span data-ttu-id="d1700-136">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d1700-136">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="d1700-137">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d1700-137">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="d1700-138">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d1700-138">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="d1700-139">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="d1700-139">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

