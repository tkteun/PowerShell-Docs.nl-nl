---
title: Schrijven van een Windows PowerShell-werkstroom | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080319"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="cf97d-102">Een Windows PowerShell-werkstroom schrijven</span><span class="sxs-lookup"><span data-stu-id="cf97d-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="cf97d-103">U kunt een XAML-werkstroom maken door het toevoegen van activiteiten die worden weergegeven door de Windows PowerShell-assembly's naar de in Visual Studio-werkstroomontwerper.</span><span class="sxs-lookup"><span data-stu-id="cf97d-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="cf97d-104">De volgende Windows PowerShell-assembly's tonen activiteiten werkstroom ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="cf97d-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf97d-105">Een XAML-werkstroom moet worden geleverd als een module als u wilt biedt ondersteuning voor de werkstroom.</span><span class="sxs-lookup"><span data-stu-id="cf97d-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="cf97d-106">Zie voor meer informatie over modules [schrijven van een Windows PowerShell-Module](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="cf97d-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="cf97d-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="cf97d-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="cf97d-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="cf97d-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="cf97d-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="cf97d-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="cf97d-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="cf97d-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="cf97d-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="cf97d-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="cf97d-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="cf97d-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="cf97d-113">De volgende onderwerpen wordt beschreven hoe u een werkstroom maakt met behulp van Windows PowerShell-activiteiten.</span><span class="sxs-lookup"><span data-stu-id="cf97d-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="cf97d-114">Windows PowerShell-activiteiten toe te voegen aan de werkset van Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cf97d-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="cf97d-115">Het maken van een werkstroom met Windows PowerShell-activiteiten</span><span class="sxs-lookup"><span data-stu-id="cf97d-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="cf97d-116">Het maken van een werkstroom met behulp van een Windows PowerShell-Script</span><span class="sxs-lookup"><span data-stu-id="cf97d-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="cf97d-117">Importeren en het aanroepen van een Windows PowerShell-werkstroom</span><span class="sxs-lookup"><span data-stu-id="cf97d-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="cf97d-118">Het maken van een Workflow-activiteit vanuit een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cf97d-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)