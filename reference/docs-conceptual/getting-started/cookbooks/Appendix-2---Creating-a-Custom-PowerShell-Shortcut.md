---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Bijlage 2 maken van een aangepaste PowerShell-snelkoppeling
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: d5e554f6f062fc5bf1beddd2aca1acf0b93d2133
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="330c5-103">Bijlage 2: een aangepaste PowerShell-snelkoppeling maken</span><span class="sxs-lookup"><span data-stu-id="330c5-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>
<span data-ttu-id="330c5-104">De volgende procedure wordt beschreven hoe een snelkoppeling naar de Windows PowerShell die beschikt over verschillende handige opties aangepast.</span><span class="sxs-lookup"><span data-stu-id="330c5-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="330c5-105">Maak een snelkoppeling die naar Powershell.exe verwijst.</span><span class="sxs-lookup"><span data-stu-id="330c5-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="330c5-106">Met de rechtermuisknop op de snelkoppeling en klik vervolgens op **eigenschappen**.</span><span class="sxs-lookup"><span data-stu-id="330c5-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="330c5-107">Klik op de **opties** tabblad.</span><span class="sxs-lookup"><span data-stu-id="330c5-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="330c5-108">In de **opties bewerken** sectie, selecteer de **snel bewerken** selectievakje.</span><span class="sxs-lookup"><span data-stu-id="330c5-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="330c5-109">Deze instelling kunt u tekst in het venster Windows PowerShell-console selecteren door de linkermuisknop slepen en Hiermee kunt u tekst naar het Klembord kopiëren door ENTER te drukken of door met de rechtermuisknop op de muis.</span><span class="sxs-lookup"><span data-stu-id="330c5-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="330c5-110">In de **opties bewerken** sectie, selecteer de **invoegmodus** selectievakje.</span><span class="sxs-lookup"><span data-stu-id="330c5-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="330c5-111">Deze instelling kunt u met de rechtermuisknop in het consolevenster automatisch tekst van het Klembord te plakken.</span><span class="sxs-lookup"><span data-stu-id="330c5-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="330c5-112">In de **opdrachtgeschiedenis** sectie typt of selecteert u een getal tussen 1 en 999 in de **buffergrootte** vak.</span><span class="sxs-lookup"><span data-stu-id="330c5-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="330c5-113">Hiermee stelt u het aantal getypte opdrachten die in de console-buffer worden behouden.</span><span class="sxs-lookup"><span data-stu-id="330c5-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="330c5-114">In de **opdrachtgeschiedenis** sectie, selecteer de **oude duplicaten verwijderen** selectievakje herhaalde opdrachten uit de console-buffer elimineren.</span><span class="sxs-lookup"><span data-stu-id="330c5-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="330c5-115">Klik op de **lay-out** tabblad.</span><span class="sxs-lookup"><span data-stu-id="330c5-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="330c5-116">In de **schermbuffer** sectie, typ een getal tussen 1 en 9999 in de **hoogte** vak.</span><span class="sxs-lookup"><span data-stu-id="330c5-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="330c5-117">De hoogte geeft het aantal regels van de uitvoer die in de buffer worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="330c5-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="330c5-118">Dit is het maximale aantal regels weer te geven wanneer u in het consolevenster schuiven bewaard.</span><span class="sxs-lookup"><span data-stu-id="330c5-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="330c5-119">Als dit aantal lager dan de hoogte wordt weergegeven is in de **venstergrootte** sectie, wordt de hoogte van het venster Grootte automatisch verkleind tot dezelfde waarde.</span><span class="sxs-lookup"><span data-stu-id="330c5-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="330c5-120">In de **venstergrootte** sectie, typ een getal tussen 1 en 9999 voor de breedte.</span><span class="sxs-lookup"><span data-stu-id="330c5-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="330c5-121">Hiermee wordt het aantal tekens dat wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="330c5-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="330c5-122">De standaardbreedte is 80 en opmaak van Windows PowerShell-uitvoer is ontworpen voor deze breedte.</span><span class="sxs-lookup"><span data-stu-id="330c5-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="330c5-123">Als u plaatsen van de console op een bepaald moment op het bureaublad wilt wanneer deze wordt geopend, schakel de **systeem bepaalt vensterpositie** selectievakje in de **vensterpositie** sectie en wijzig vervolgens de waarden in de  **Links** en **boven** dialoogvensters in de **vensterpositie** sectie.</span><span class="sxs-lookup"><span data-stu-id="330c5-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="330c5-124">Klik op **OK**.</span><span class="sxs-lookup"><span data-stu-id="330c5-124">Click **OK**.</span></span>

