---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een PowerShell-tabblad maken in Windows PowerShell ISE
ms.openlocfilehash: 7baf9a4051a196045d53eebf8ce5260bdc1bc55a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030586"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="03f67-103">Een PowerShell-tabblad maken in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="03f67-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="03f67-104">Tabbladen in de Windows PowerShell Integrated Scripting Environment (ISE) kunnen u tegelijkertijd maken en gebruiken van verschillende omgevingen binnen dezelfde toepassing.</span><span class="sxs-lookup"><span data-stu-id="03f67-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="03f67-105">Elk tabblad PowerShell overeenkomt met een afzonderlijke uitvoeringsomgeving of -sessie.</span><span class="sxs-lookup"><span data-stu-id="03f67-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="03f67-106">Variabelen, functies en -aliassen die u op een tabblad maakt doen niet meegenomen naar een andere.</span><span class="sxs-lookup"><span data-stu-id="03f67-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="03f67-107">Ze zijn andere Windows PowerShell-sessies.</span><span class="sxs-lookup"><span data-stu-id="03f67-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="03f67-108">Gebruik de volgende stappen uit om te openen of sluiten van een tabblad in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03f67-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="03f67-109">Wijzig de naam van een tabblad, stel de [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) eigenschap op het Windows PowerShell-tabblad scripting-object.</span><span class="sxs-lookup"><span data-stu-id="03f67-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="03f67-110">Het maken en gebruiken van een nieuwe PowerShell-tabblad</span><span class="sxs-lookup"><span data-stu-id="03f67-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="03f67-111">Op de **bestand** menu, klikt u op **nieuwe PowerShell-tabblad**. De nieuwe PowerShell-tabblad is altijd wordt geopend als het actieve venster.</span><span class="sxs-lookup"><span data-stu-id="03f67-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="03f67-112">PowerShell-tabbladen zijn incrementeel genummerd in de volgorde waarin ze worden geopend.</span><span class="sxs-lookup"><span data-stu-id="03f67-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="03f67-113">Elk tabblad is gekoppeld aan een eigen Windows PowerShell-consolevenster.</span><span class="sxs-lookup"><span data-stu-id="03f67-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="03f67-114">Er kunnen maximaal 32 PowerShell tabbladen met hun eigen sessie openen op een tijdstip (dit is beperkt tot 8 in Windows PowerShell ISE 2.0).</span><span class="sxs-lookup"><span data-stu-id="03f67-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="03f67-115">Houd er rekening mee dat te klikken op de **nieuw** of **Open** pictogrammen op de werkbalk maakt geen een nieuw tabblad met een aparte-sessie.</span><span class="sxs-lookup"><span data-stu-id="03f67-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="03f67-116">Deze knoppen openen in plaats daarvan een nieuw of bestaand scriptbestand op het actieve tabblad met een sessie.</span><span class="sxs-lookup"><span data-stu-id="03f67-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="03f67-117">U kunt meerdere bestanden worden geopend met elk tabblad en sessie-script hebben.</span><span class="sxs-lookup"><span data-stu-id="03f67-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="03f67-118">De tabbladen van het script voor een sessie wordt alleen weergegeven onder de tabbladen sessie wanneer de bijbehorende sessie actief is.</span><span class="sxs-lookup"><span data-stu-id="03f67-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="03f67-119">Als u wilt een PowerShell-tabblad activeren, klikt u op het tabblad. Selecteren uit alle PowerShell-tabbladen die zijn geopend op de **weergave** menu, klikt u op de PowerShell-tabblad dat u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="03f67-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="03f67-120">Het maken en gebruiken van een nieuwe externe PowerShell-tabblad</span><span class="sxs-lookup"><span data-stu-id="03f67-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="03f67-121">Op de **bestand** menu, klikt u op **nieuwe externe PowerShell-tabblad** tot stand brengen van een sessie op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="03f67-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="03f67-122">Een dialoogvenster wordt weergegeven en vraagt u om in te voeren van gegevens die zijn vereist om de externe verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="03f67-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="03f67-123">De functies van het tabblad Extern net als bij een lokale PowerShell-tabblad, maar de opdrachten en scripts die worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="03f67-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="03f67-124">Om een PowerShell-tabblad te sluiten</span><span class="sxs-lookup"><span data-stu-id="03f67-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="03f67-125">Als u wilt een tabblad sluit, kunt u een van de volgende technieken gebruiken:</span><span class="sxs-lookup"><span data-stu-id="03f67-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="03f67-126">Klik op het tabblad dat u wilt sluiten.</span><span class="sxs-lookup"><span data-stu-id="03f67-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="03f67-127">Op de **bestand** menu, klikt u op **PowerShell-tabblad sluit**, of klik op de knop Sluiten (**X**) op een actieve tabblad om het tabblad te sluiten.</span><span class="sxs-lookup"><span data-stu-id="03f67-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="03f67-128">Als u hebt niet-opgeslagen bestanden worden geopend in de PowerShell-tabblad dat u wilt sluiten, wordt u gevraagd op te slaan of ze negeren.</span><span class="sxs-lookup"><span data-stu-id="03f67-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="03f67-129">Zie voor meer informatie over het opslaan van een script [hoe u een Script opslaan](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="03f67-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="03f67-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="03f67-130">See Also</span></span>

- [<span data-ttu-id="03f67-131">Maak kennis met de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="03f67-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="03f67-132">Het consolevenster gebruiken in de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="03f67-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
