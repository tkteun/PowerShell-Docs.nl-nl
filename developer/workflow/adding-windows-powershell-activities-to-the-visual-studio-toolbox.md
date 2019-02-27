---
title: Windows PowerShell-activiteiten toe te voegen aan de werkset van Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56852106"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="2e67a-102">Windows PowerShell-activiteiten toevoegen aan de Visual Studio-werkset</span><span class="sxs-lookup"><span data-stu-id="2e67a-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="2e67a-103">Voordat u een PowerShell-werkstroom met Workflow Designer ontwerpt, moet u eerst de PowerShell-activiteiten toevoegen aan de werkset in een werkstroom met Visual Studio-consoletoepassingsproject.</span><span class="sxs-lookup"><span data-stu-id="2e67a-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="2e67a-104">De volgende procedure beschrijft hoe de activiteiten van de assembly Microsoft.PowerShell.Core.Activities toevoegen aan de werkset van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2e67a-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="2e67a-105">Windows PowerShell-activiteiten toe te voegen aan de werkset</span><span class="sxs-lookup"><span data-stu-id="2e67a-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="2e67a-106">Maak een nieuwe werkstroom consoletoepassingsproject in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2e67a-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="2e67a-107">Op de **weergave** menu, klikt u op **werkset**.</span><span class="sxs-lookup"><span data-stu-id="2e67a-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="2e67a-108">Een nieuw tabblad in de werkset toevoegen door te klikken en met de rechtermuisknop op in de werkset **tabblad toevoegen**, en geef een naam, zoals "Activiteiten PowerShell" op het nieuwe tabblad.</span><span class="sxs-lookup"><span data-stu-id="2e67a-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="2e67a-109">Een tabblad toe te voegen, kunt u de PowerShell-activiteiten gescheiden van andere hulpprogramma's in de werkset van de groep.</span><span class="sxs-lookup"><span data-stu-id="2e67a-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="2e67a-110">Klik op het nieuwe tabblad van de werkset **Items kiezen...** . De **Items in de werkset Kies** dialoogvenster wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="2e67a-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="2e67a-111">In de **Items in de werkset Kies** dialoogvenster, klikt u op de **System.Activities** tabblad.</span><span class="sxs-lookup"><span data-stu-id="2e67a-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="2e67a-112">Klik op **Bladeren**.</span><span class="sxs-lookup"><span data-stu-id="2e67a-112">Click **Browse**.</span></span>

7. <span data-ttu-id="2e67a-113">Navigeer naar de map %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e en dubbelklikt u op Microsoft.PowerShell.Core.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="2e67a-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="2e67a-114">Klik op **OK**.</span><span class="sxs-lookup"><span data-stu-id="2e67a-114">Click **OK**.</span></span> <span data-ttu-id="2e67a-115">De activiteiten die zijn gedefinieerd door de assembly Microsoft.PowerShell.Core.Activities zijn nu beschikbaar in de werkset.</span><span class="sxs-lookup"><span data-stu-id="2e67a-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e67a-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2e67a-116">See Also</span></span>

[<span data-ttu-id="2e67a-117">Schrijven van een Windows PowerShell-werkstroom</span><span class="sxs-lookup"><span data-stu-id="2e67a-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="2e67a-118">Het maken van een werkstroom met Windows PowerShell-activiteiten</span><span class="sxs-lookup"><span data-stu-id="2e67a-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)