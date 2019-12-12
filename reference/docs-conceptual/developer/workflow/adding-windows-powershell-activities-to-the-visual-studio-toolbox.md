---
title: Windows Power shell-activiteiten toevoegen aan de Visual Studio-werkset | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352169"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="e9059-102">Windows PowerShell-activiteiten toevoegen aan de Visual Studio-werkset</span><span class="sxs-lookup"><span data-stu-id="e9059-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="e9059-103">Voordat u een Power shell-werk stroom met Workflow Designer maakt, moet u eerst de Power shell-activiteiten toevoegen aan de werkset in een toepassings project van een Visual Studio-werk stroom console.</span><span class="sxs-lookup"><span data-stu-id="e9059-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="e9059-104">De volgende procedure laat zien hoe u de activiteiten van de assembly micro soft. Power shell. core. activities kunt toevoegen aan de Visual Studio-werkset.</span><span class="sxs-lookup"><span data-stu-id="e9059-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="e9059-105">Windows Power shell-activiteiten toevoegen aan de werkset</span><span class="sxs-lookup"><span data-stu-id="e9059-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="e9059-106">Maak een nieuw werk stroom console toepassings project in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9059-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="e9059-107">Klik in het menu **beeld** op **werkset**.</span><span class="sxs-lookup"><span data-stu-id="e9059-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="e9059-108">Voeg een nieuw tabblad in de werkset toe door met de rechter muisknop te klikken in de werkset en op **tabblad toevoegen**te klikken en het nieuwe tabblad een naam te geven, zoals Power shell-activiteiten.</span><span class="sxs-lookup"><span data-stu-id="e9059-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="e9059-109">Door een tabblad toe te voegen, kunt u de Power shell-activiteiten groeperen, gescheiden van andere hulpprogram ma's in de werkset.</span><span class="sxs-lookup"><span data-stu-id="e9059-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="e9059-110">Klik op het tabblad nieuwe werkset op **items kiezen...** . Het dialoog venster **werkset-items kiezen** wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e9059-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="e9059-111">Klik in het dialoog venster **werkset-items kiezen** op het tabblad **System. activities** .</span><span class="sxs-lookup"><span data-stu-id="e9059-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="e9059-112">Klik op **Bladeren**.</span><span class="sxs-lookup"><span data-stu-id="e9059-112">Click **Browse**.</span></span>

7. <span data-ttu-id="e9059-113">Ga naar de map%WINDIR%\Microsoft.NET\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e en dubbel klik op micro soft. Power shell. core. activities. dll.</span><span class="sxs-lookup"><span data-stu-id="e9059-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="e9059-114">Klik op **OK**.</span><span class="sxs-lookup"><span data-stu-id="e9059-114">Click **OK**.</span></span> <span data-ttu-id="e9059-115">De activiteiten die zijn gedefinieerd door de assembly micro soft. Power shell. core. activities zijn nu beschikbaar in de werkset.</span><span class="sxs-lookup"><span data-stu-id="e9059-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9059-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e9059-116">See Also</span></span>

[<span data-ttu-id="e9059-117">Een Windows Power shell-werk stroom schrijven</span><span class="sxs-lookup"><span data-stu-id="e9059-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="e9059-118">Een werk stroom maken met Windows Power shell-activiteiten</span><span class="sxs-lookup"><span data-stu-id="e9059-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)