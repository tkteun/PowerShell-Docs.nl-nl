---
description: Hierin wordt beschreven hoe u opdrachten bewerkt in de Power shell-opdracht prompt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_line_editing?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Line_Editing
ms.openlocfilehash: d4b525e4c3f461b799c3bef157e04e0763a0b9c6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252480"
---
# <a name="about-line-editing"></a><span data-ttu-id="b8acd-104">Regels bewerken</span><span class="sxs-lookup"><span data-stu-id="b8acd-104">About Line Editing</span></span>

## <a name="short-description"></a><span data-ttu-id="b8acd-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="b8acd-105">Short description</span></span>

<span data-ttu-id="b8acd-106">Hierin wordt beschreven hoe u opdrachten bewerkt in de Power shell-opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="b8acd-106">Describes how to edit commands at the PowerShell command prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="b8acd-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="b8acd-107">Long description</span></span>

<span data-ttu-id="b8acd-108">De Power shell-console bevat enkele nuttige sneltoetsen die u helpen bij het bewerken van opdrachten bij de Power shell-opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="b8acd-108">The PowerShell console has some useful keyboard shortcuts to help you edit commands at the PowerShell command prompt.</span></span>

### <a name="add-a-line"></a><span data-ttu-id="b8acd-109">Een regel toevoegen</span><span class="sxs-lookup"><span data-stu-id="b8acd-109">Add a line</span></span>

<span data-ttu-id="b8acd-110">Als u een regel wilt toevoegen, drukt u op <kbd>SHIFT</kbd> + <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-110">To add a line, press <kbd>Shift</kbd>+<kbd>Enter</kbd>.</span></span>

<span data-ttu-id="b8acd-111">U kunt meerdere regels toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b8acd-111">You can add multiple lines.</span></span> <span data-ttu-id="b8acd-112">Elke extra regel begint met `>>` , de voortzettings prompt.</span><span class="sxs-lookup"><span data-stu-id="b8acd-112">Each additional line begins with `>>`, the continuation prompt.</span></span> <span data-ttu-id="b8acd-113">Druk op <kbd>Enter</kbd> om de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b8acd-113">Press <kbd>Enter</kbd> to execute the command.</span></span>

### <a name="move-left-and-right"></a><span data-ttu-id="b8acd-114">Naar links en rechts</span><span class="sxs-lookup"><span data-stu-id="b8acd-114">Move left and right</span></span>

<span data-ttu-id="b8acd-115">Als u de cursor één teken naar links wilt verplaatsen, drukt u op de <kbd>pijl naar links</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-115">To move the cursor one character to the left, press the <kbd>Left arrow</kbd>.</span></span>

<span data-ttu-id="b8acd-116">Als u de cursor één woord naar links wilt verplaatsen, drukt u op <kbd>CTRL</kbd>- + <kbd>pijl-links</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-116">To move the cursor one word to the left, press <kbd>Ctrl</kbd>+<kbd>Left arrow</kbd>.</span></span>

<span data-ttu-id="b8acd-117">Als u de cursor één teken naar rechts wilt verplaatsen, drukt u op de <kbd>pijl-rechts</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-117">To move the cursor one character to the right, press the <kbd>Right arrow</kbd>.</span></span>

<span data-ttu-id="b8acd-118">Als u de cursor één woord naar rechts wilt verplaatsen, drukt u op <kbd>CTRL</kbd>- + <kbd>pijl-rechts</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-118">To move the cursor one word to the right, press <kbd>Ctrl</kbd>+<kbd>Right arrow</kbd>.</span></span>

### <a name="move-to-a-lines-beginning-or-end"></a><span data-ttu-id="b8acd-119">Naar het begin of einde van een regel verplaatsen</span><span class="sxs-lookup"><span data-stu-id="b8acd-119">Move to a line's beginning or end</span></span>

<span data-ttu-id="b8acd-120">Als u naar het begin van een regel wilt gaan, drukt u op <kbd>Home</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-120">To move to the beginning of a line, press <kbd>Home</kbd>.</span></span>

<span data-ttu-id="b8acd-121">Als u naar het einde van een regel wilt gaan, drukt u op <kbd>End</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-121">To move to the end of a line, press <kbd>End</kbd>.</span></span>

<span data-ttu-id="b8acd-122">Als er regels zijn toegevoegd, drukt u op <kbd>Home</kbd> of <kbd>eindigt</kbd> u twee maal om naar het begin of einde van de regels te gaan.</span><span class="sxs-lookup"><span data-stu-id="b8acd-122">If lines were added, press <kbd>Home</kbd> or <kbd>End</kbd> twice to move to the beginning or end of the lines.</span></span>

### <a name="delete-characters"></a><span data-ttu-id="b8acd-123">Tekens verwijderen</span><span class="sxs-lookup"><span data-stu-id="b8acd-123">Delete characters</span></span>

<span data-ttu-id="b8acd-124">Als u het teken achter de positie van de cursor wilt verwijderen, drukt u op <kbd>BACKSPACE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-124">To delete the character behind the cursor's position, press <kbd>Backspace</kbd>.</span></span>

<span data-ttu-id="b8acd-125">Als u het teken op de positie van de cursor wilt verwijderen, drukt u op <kbd>verwijderen</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-125">To delete the character at the cursor's position, press <kbd>Delete</kbd>.</span></span>

### <a name="delete-characters-from-a-line"></a><span data-ttu-id="b8acd-126">Tekens uit een regel verwijderen</span><span class="sxs-lookup"><span data-stu-id="b8acd-126">Delete characters from a line</span></span>

<span data-ttu-id="b8acd-127">Als u alle tekens van de cursor positie naar het einde van een regel wilt verwijderen, drukt u op <kbd>CTRL</kbd> + <kbd>End</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-127">To delete all the characters from the cursor's position to the end of a line, press <kbd>Ctrl</kbd>+<kbd>End</kbd>.</span></span>

<span data-ttu-id="b8acd-128">Als u alle tekens van de cursor positie naar het begin van een regel wilt verwijderen, drukt u op <kbd>CTRL</kbd> + <kbd>Home</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-128">To delete all the characters from the cursor's position to the beginning of a line, press <kbd>Ctrl</kbd>+<kbd>Home</kbd>.</span></span>

<span data-ttu-id="b8acd-129">Als er regels zijn toegevoegd, worden de tekens verwijderd uit de huidige regel en de regels die zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b8acd-129">If lines were added, characters are deleted from the current line and the lines that were added.</span></span>

### <a name="insert-and-overstrike-mode"></a><span data-ttu-id="b8acd-130">Invoeg-en overschrijf modus</span><span class="sxs-lookup"><span data-stu-id="b8acd-130">Insert and overstrike mode</span></span>

<span data-ttu-id="b8acd-131">Als u wilt overschakelen naar de Overschrijf modus, drukt u op <kbd>Insert</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b8acd-131">To change to overwrite mode, press <kbd>Insert</kbd>.</span></span> <span data-ttu-id="b8acd-132">Als u wilt terugkeren naar de Invoeg modus, drukt u nogmaals op <kbd>Invoegen</kbd> .</span><span class="sxs-lookup"><span data-stu-id="b8acd-132">To return to insert mode, press <kbd>Insert</kbd> again.</span></span>

### <a name="tab-completion"></a><span data-ttu-id="b8acd-133">Tabblad voltooiing</span><span class="sxs-lookup"><span data-stu-id="b8acd-133">Tab completion</span></span>

<span data-ttu-id="b8acd-134">Als u de naam van een cmdlet, een para meter of een pad wilt volt ooien, drukt u op de <kbd>Tab</kbd> -toets.</span><span class="sxs-lookup"><span data-stu-id="b8acd-134">To complete a cmdlet name, a parameter, or a path, press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="b8acd-135">Als u door een lijst met waarden wilt schuiven, drukt u nogmaals op de <kbd>Tab</kbd> -toets.</span><span class="sxs-lookup"><span data-stu-id="b8acd-135">To scroll through a list of values, press the <kbd>Tab</kbd> key again.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8acd-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b8acd-136">See also</span></span>

[<span data-ttu-id="b8acd-137">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="b8acd-137">about_Command_Syntax</span></span>](about_Command_Syntax.md)

[<span data-ttu-id="b8acd-138">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="b8acd-138">about_Path_Syntax</span></span>](about_Path_Syntax.md)

[<span data-ttu-id="b8acd-139">about_PSReadline</span><span class="sxs-lookup"><span data-stu-id="b8acd-139">about_PSReadline</span></span>](../../PSReadline/About/about_PSReadline.md)