---
title: Een Windows Power shell-werk stroom schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356628"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="70e90-102">Een Windows PowerShell-werkstroom schrijven</span><span class="sxs-lookup"><span data-stu-id="70e90-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="70e90-103">U kunt een XAML-werk stroom maken door activiteiten die worden weer gegeven door Windows Power shell-assembly's toe te voegen aan de werk stroom ontwerper in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70e90-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="70e90-104">De volgende Windows Power shell-assembly's tonen activiteiten die zijn ingeschakeld voor werk stromen.</span><span class="sxs-lookup"><span data-stu-id="70e90-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70e90-105">Een XAML-werk stroom moet worden verpakt als een module als u hulp voor de werk stroom wilt bieden.</span><span class="sxs-lookup"><span data-stu-id="70e90-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="70e90-106">Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="70e90-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="70e90-107">Micro soft. Power shell. activities</span><span class="sxs-lookup"><span data-stu-id="70e90-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="70e90-108">Micro soft. Power shell. core. activities</span><span class="sxs-lookup"><span data-stu-id="70e90-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="70e90-109">Micro soft. Power shell. Diagnostics. activities</span><span class="sxs-lookup"><span data-stu-id="70e90-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="70e90-110">Micro soft. Power shell. Management. activities</span><span class="sxs-lookup"><span data-stu-id="70e90-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="70e90-111">Micro soft. Power shell. Security. activities</span><span class="sxs-lookup"><span data-stu-id="70e90-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="70e90-112">Micro soft. Power shell. Utility. activities</span><span class="sxs-lookup"><span data-stu-id="70e90-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="70e90-113">In de volgende onderwerpen wordt beschreven hoe u een werk stroom maakt met behulp van Windows Power shell-activiteiten.</span><span class="sxs-lookup"><span data-stu-id="70e90-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="70e90-114">Windows Power shell-activiteiten toevoegen aan de Visual Studio-werkset</span><span class="sxs-lookup"><span data-stu-id="70e90-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="70e90-115">Een werk stroom maken met Windows Power shell-activiteiten</span><span class="sxs-lookup"><span data-stu-id="70e90-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="70e90-116">Een werk stroom maken met behulp van een Windows Power shell-script</span><span class="sxs-lookup"><span data-stu-id="70e90-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="70e90-117">Een Windows Power shell-werk stroom importeren en aanroepen</span><span class="sxs-lookup"><span data-stu-id="70e90-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="70e90-118">Een werk stroom activiteit maken op basis van een Windows Power shell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="70e90-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)