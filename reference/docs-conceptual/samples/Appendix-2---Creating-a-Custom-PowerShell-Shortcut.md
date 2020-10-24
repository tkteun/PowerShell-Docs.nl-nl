---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Bijlage 2 - Een aangepaste PowerShell-snelkoppeling maken
description: In de volgende procedure wordt beschreven hoe u een snelkoppeling maakt naar Windows Power shell waarin verschillende handige opties zijn aangepast.
ms.openlocfilehash: abdab517dec1357050bf431b6f2e35311ad49976
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500722"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="6b40a-104">Bijlage 2: een aangepaste Power shell-snelkoppeling maken</span><span class="sxs-lookup"><span data-stu-id="6b40a-104">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="6b40a-105">In de volgende procedure wordt beschreven hoe u een snelkoppeling maakt naar Windows Power shell waarin verschillende handige opties zijn aangepast.</span><span class="sxs-lookup"><span data-stu-id="6b40a-105">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="6b40a-106">Een snelkoppeling maken die verwijst naar Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="6b40a-106">Create a shortcut that points to Powershell.exe.</span></span>

1. <span data-ttu-id="6b40a-107">Klik met de rechter muisknop op de snelkoppeling en klik vervolgens op **Eigenschappen**.</span><span class="sxs-lookup"><span data-stu-id="6b40a-107">Right-click the shortcut, and then click **Properties**.</span></span>

1. <span data-ttu-id="6b40a-108">Klik op het tabblad **Options**.</span><span class="sxs-lookup"><span data-stu-id="6b40a-108">Click the **Options** tab.</span></span>

1. <span data-ttu-id="6b40a-109">Schakel in het gedeelte **bewerkings opties** het selectie vakje **snel** bewerken in.</span><span class="sxs-lookup"><span data-stu-id="6b40a-109">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="6b40a-110">Met deze instelling kunt u tekst in het venster van de Windows Power shell-console selecteren door de linkermuisknop te slepen. Hiermee kunt u tekst naar het klem bord kopiëren door op ENTER te drukken of door met de rechter muisknop op de muis te klikken.</span><span class="sxs-lookup"><span data-stu-id="6b40a-110">This setting lets you select text in the Windows PowerShell console window by dragging the left  mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking  the mouse.</span></span>

1. <span data-ttu-id="6b40a-111">Schakel in het gedeelte **bewerkings opties** het selectie vakje **invoeg modus** in.</span><span class="sxs-lookup"><span data-stu-id="6b40a-111">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="6b40a-112">Met deze instelling kunt u in het console venster met de rechter muisknop klikken om automatisch tekst van het klem bord te plakken.</span><span class="sxs-lookup"><span data-stu-id="6b40a-112">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

1. <span data-ttu-id="6b40a-113">Typ of Selecteer in het gedeelte **opdracht geschiedenis** een getal tussen 1 en 999 in het vak **buffer grootte** .</span><span class="sxs-lookup"><span data-stu-id="6b40a-113">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="6b40a-114">Hiermee stelt u het aantal getypte opdrachten in die in de console buffer worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="6b40a-114">This sets the number of typed commands that will be kept in the console buffer.</span></span>

1. <span data-ttu-id="6b40a-115">Schakel in de sectie **opdracht geschiedenis** het selectie vakje **oude dubbele items verwijderen** in om herhaalde opdrachten uit de console buffer te elimineren.</span><span class="sxs-lookup"><span data-stu-id="6b40a-115">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

1. <span data-ttu-id="6b40a-116">Klik op de **lay-out** tabblad.</span><span class="sxs-lookup"><span data-stu-id="6b40a-116">Click the **Layout** tab.</span></span>

1. <span data-ttu-id="6b40a-117">Typ in de sectie **scherm buffer** een getal tussen 1 en 9999 in het vak **hoogte** .</span><span class="sxs-lookup"><span data-stu-id="6b40a-117">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="6b40a-118">De hoogte vertegenwoordigt het aantal regels met uitvoer dat in de buffer wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="6b40a-118">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="6b40a-119">Dit is het maximum aantal regels dat kan worden weer gegeven wanneer u door het console venster bladert.</span><span class="sxs-lookup"><span data-stu-id="6b40a-119">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="6b40a-120">Als dit aantal lager is dan de hoogte die wordt weer gegeven in de sectie **venster grootte** , wordt de hoogte van de venster grootte automatisch beperkt tot dezelfde waarde.</span><span class="sxs-lookup"><span data-stu-id="6b40a-120">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

1. <span data-ttu-id="6b40a-121">Typ in de sectie **venster grootte** een getal tussen 1 en 9999 voor de breedte.</span><span class="sxs-lookup"><span data-stu-id="6b40a-121">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="6b40a-122">Hiermee wordt het aantal tekens aangegeven dat wordt weer gegeven in het console venster.</span><span class="sxs-lookup"><span data-stu-id="6b40a-122">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="6b40a-123">De standaard breedte is 80 en de uitvoer indeling van Windows Power shell is voor deze breedte ontworpen.</span><span class="sxs-lookup"><span data-stu-id="6b40a-123">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

1. <span data-ttu-id="6b40a-124">Als u de-console op een bepaald punt op het bureau blad wilt plaatsen wanneer deze wordt geopend, schakelt u het selectie vakje **systeem positie venster toestaan** in het gedeelte **venster positie** uit en wijzigt u de waarden in de vakken **links** en **boven** in de sectie **venster positie** .</span><span class="sxs-lookup"><span data-stu-id="6b40a-124">If you want to place the console at a particular point on the desktop when it is opened, clear  the **Let system position window** check box in the **Window position** section, and then change  the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

1. <span data-ttu-id="6b40a-125">Klik op **OK**.</span><span class="sxs-lookup"><span data-stu-id="6b40a-125">Click **OK**.</span></span>
