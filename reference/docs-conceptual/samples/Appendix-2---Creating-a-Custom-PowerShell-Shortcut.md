---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Bijlage 2 - Een aangepaste PowerShell-snelkoppeling maken
ms.openlocfilehash: 6f1a6a8187b1797103e3620b2cf9155978807ea5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030297"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="8de35-103">Bijlage 2: een aangepaste Power shell-snelkoppeling maken</span><span class="sxs-lookup"><span data-stu-id="8de35-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="8de35-104">In de volgende procedure wordt beschreven hoe u een snelkoppeling maakt naar Windows Power shell waarin verschillende handige opties zijn aangepast.</span><span class="sxs-lookup"><span data-stu-id="8de35-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="8de35-105">Een snelkoppeling maken die verwijst naar Power shell. exe.</span><span class="sxs-lookup"><span data-stu-id="8de35-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="8de35-106">Klik met de rechter muisknop op de snelkoppeling en klik vervolgens op **Eigenschappen**.</span><span class="sxs-lookup"><span data-stu-id="8de35-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="8de35-107">Klik op de **opties** tabblad.</span><span class="sxs-lookup"><span data-stu-id="8de35-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="8de35-108">Schakel in het gedeelte **bewerkings opties** het selectie vakje **snel** bewerken in.</span><span class="sxs-lookup"><span data-stu-id="8de35-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="8de35-109">Met deze instelling kunt u tekst in het venster van de Windows Power shell-console selecteren door de linkermuisknop te slepen. Hiermee kunt u tekst naar het klem bord kopiëren door op ENTER te drukken of door met de rechter muisknop op de muis te klikken.</span><span class="sxs-lookup"><span data-stu-id="8de35-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="8de35-110">Schakel in het gedeelte **bewerkings opties** het selectie vakje **invoeg modus** in.</span><span class="sxs-lookup"><span data-stu-id="8de35-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="8de35-111">Met deze instelling kunt u in het console venster met de rechter muisknop klikken om automatisch tekst van het klem bord te plakken.</span><span class="sxs-lookup"><span data-stu-id="8de35-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="8de35-112">Typ of Selecteer in het gedeelte **opdracht geschiedenis** een getal tussen 1 en 999 in het vak **buffer grootte** .</span><span class="sxs-lookup"><span data-stu-id="8de35-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="8de35-113">Hiermee stelt u het aantal getypte opdrachten in die in de console buffer worden bewaard.</span><span class="sxs-lookup"><span data-stu-id="8de35-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="8de35-114">Schakel in de sectie **opdracht geschiedenis** het selectie vakje **oude dubbele items verwijderen** in om herhaalde opdrachten uit de console buffer te elimineren.</span><span class="sxs-lookup"><span data-stu-id="8de35-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="8de35-115">Klik op de **lay-out** tabblad.</span><span class="sxs-lookup"><span data-stu-id="8de35-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="8de35-116">Typ in de sectie **scherm buffer** een getal tussen 1 en 9999 in het vak **hoogte** .</span><span class="sxs-lookup"><span data-stu-id="8de35-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="8de35-117">De hoogte vertegenwoordigt het aantal regels met uitvoer dat in de buffer wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8de35-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="8de35-118">Dit is het maximum aantal regels dat kan worden weer gegeven wanneer u door het console venster bladert.</span><span class="sxs-lookup"><span data-stu-id="8de35-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="8de35-119">Als dit aantal lager is dan de hoogte die wordt weer gegeven in de sectie **venster grootte** , wordt de hoogte van de venster grootte automatisch beperkt tot dezelfde waarde.</span><span class="sxs-lookup"><span data-stu-id="8de35-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="8de35-120">Typ in de sectie **venster grootte** een getal tussen 1 en 9999 voor de breedte.</span><span class="sxs-lookup"><span data-stu-id="8de35-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="8de35-121">Hiermee wordt het aantal tekens aangegeven dat wordt weer gegeven in het console venster.</span><span class="sxs-lookup"><span data-stu-id="8de35-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="8de35-122">De standaard breedte is 80 en de uitvoer indeling van Windows Power shell is voor deze breedte ontworpen.</span><span class="sxs-lookup"><span data-stu-id="8de35-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="8de35-123">Als u de-console op een bepaald punt op het bureau blad wilt plaatsen wanneer deze wordt geopend, schakelt u het selectie vakje **systeem positie venster toestaan** in het gedeelte **venster positie** uit en wijzigt u de waarden in de vakken **links** en **boven** in de sectie **venster positie** .</span><span class="sxs-lookup"><span data-stu-id="8de35-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="8de35-124">Klik op **OK**.</span><span class="sxs-lookup"><span data-stu-id="8de35-124">Click **OK**.</span></span>
