---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een PowerShell-tabblad maken in Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 4d4388d889f2178b2cd24cb0f3350aee37327625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950043"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="16580-103">Een PowerShell-tabblad maken in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="16580-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="16580-104">Tabbladen in de Windows PowerShell Integrated Scripting Environment (ISE) kunt u tegelijkertijd maken en gebruiken van verschillende uitvoeringsomgevingen binnen dezelfde toepassing.</span><span class="sxs-lookup"><span data-stu-id="16580-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="16580-105">Elk tabblad PowerShell overeenkomt met een afzonderlijke uitvoeringsomgeving of de sessie.</span><span class="sxs-lookup"><span data-stu-id="16580-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="16580-106">**OPMERKING**:</span><span class="sxs-lookup"><span data-stu-id="16580-106">**NOTE**:</span></span>
>
> <span data-ttu-id="16580-107">Variabelen, functies en aliassen die u op een tabblad maakt uitvoeren niet via naar een andere.</span><span class="sxs-lookup"><span data-stu-id="16580-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="16580-108">Andere Windows PowerShell-sessies zijn.</span><span class="sxs-lookup"><span data-stu-id="16580-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="16580-109">Gebruik de volgende stappen uit om te openen of sluiten van een tabblad in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16580-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="16580-110">Wijzig de naam van een tabblad, stel de [DisplayName](The-PowerShellTab-Object.md#displayname) -eigenschap op het tabblad voor Windows PowerShell-scripting-object.</span><span class="sxs-lookup"><span data-stu-id="16580-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="16580-111">Maken en gebruiken van een nieuw PowerShell-tabblad</span><span class="sxs-lookup"><span data-stu-id="16580-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="16580-112">Op de **bestand** menu, klikt u op **nieuw PowerShell-tabblad**. Het nieuwe PowerShell-tabblad is altijd wordt geopend als het actieve venster.</span><span class="sxs-lookup"><span data-stu-id="16580-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="16580-113">PowerShell tabbladen worden stapsgewijs genummerd in de volgorde waarin ze worden geopend.</span><span class="sxs-lookup"><span data-stu-id="16580-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="16580-114">Elk tabblad is gekoppeld aan een eigen Windows PowerShell-consolevenster.</span><span class="sxs-lookup"><span data-stu-id="16580-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="16580-115">Er kunnen maximaal 32 PowerShell tabbladen met hun eigen sessie niet openen op een tijdstip (dit is beperkt tot 8 op Windows PowerShell ISE 2.0).</span><span class="sxs-lookup"><span data-stu-id="16580-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="16580-116">Houd er rekening mee dat te klikken op de **nieuw** of **Open** pictogrammen op de werkbalk maakt een nieuw tabblad niet met een afzonderlijke sessie.</span><span class="sxs-lookup"><span data-stu-id="16580-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="16580-117">Deze knoppen openen in plaats daarvan een nieuw of bestaand scriptbestand op het momenteel geselecteerde tabblad met een sessie.</span><span class="sxs-lookup"><span data-stu-id="16580-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="16580-118">U kunt meerdere script bestanden met elk tabblad en sessie openen hebben.</span><span class="sxs-lookup"><span data-stu-id="16580-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="16580-119">Het script voor een sessie alleen tabbladen onder de tabbladen sessie wanneer de bijbehorende sessie actief is.</span><span class="sxs-lookup"><span data-stu-id="16580-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="16580-120">Klik op het tabblad om een PowerShell-tabblad te activeren. Om te selecteren uit alle PowerShell tabbladen die zijn geopend op de **weergave** menu, klikt u op het PowerShell-tabblad dat u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="16580-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="16580-121">Maken en gebruiken van een nieuw tabblad van de externe PowerShell</span><span class="sxs-lookup"><span data-stu-id="16580-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="16580-122">Op de **bestand** menu, klikt u op **nieuwe externe PowerShell-tabblad** een sessie op een externe computer tot stand brengen.</span><span class="sxs-lookup"><span data-stu-id="16580-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="16580-123">Een dialoogvenster wordt weergegeven en u wordt gevraagd om de gegevens die zijn vereist voor het maken van de externe verbinding invoeren.</span><span class="sxs-lookup"><span data-stu-id="16580-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="16580-124">Het tabblad Extern functies net als bij een lokale PowerShell-tabblad, maar de opdrachten en scripts worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="16580-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="16580-125">Een PowerShell-tabblad sluiten</span><span class="sxs-lookup"><span data-stu-id="16580-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="16580-126">U kunt een van de volgende technieken gebruiken een tabblad om af te sluiten:</span><span class="sxs-lookup"><span data-stu-id="16580-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="16580-127">Klik op het tabblad dat u wilt sluiten.</span><span class="sxs-lookup"><span data-stu-id="16580-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="16580-128">Op de **bestand** menu, klikt u op **PowerShell tabblad sluiten**, of klik op de knop Sluiten (**X**) op een actieve tabblad te sluiten van het tabblad.</span><span class="sxs-lookup"><span data-stu-id="16580-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="16580-129">Als u hebt niet-opgeslagen openen bestanden op het tabblad PowerShell dat u wilt sluiten, wordt u gevraagd op te slaan of deze verwijderen.</span><span class="sxs-lookup"><span data-stu-id="16580-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="16580-130">Zie voor meer informatie over het opslaan van een script [hoe een Script opslaat](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="16580-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="16580-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="16580-131">See Also</span></span>

- [<span data-ttu-id="16580-132">Introducing the Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="16580-132">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="16580-133">Het gebruik van het consolevenster in de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="16580-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)