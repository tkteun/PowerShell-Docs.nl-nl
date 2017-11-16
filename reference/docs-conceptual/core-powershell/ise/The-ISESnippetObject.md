---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: De ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="090b8-103">De ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="090b8-103">The ISESnippetObject</span></span>
  <span data-ttu-id="090b8-104">Een **ISESnippet** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="090b8-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="090b8-105">De leden van de **$psISE.CurrentPowerShellTab.Snippets** verzameling zijn alle voorbeelden van **ISESnippet** objecten.</span><span class="sxs-lookup"><span data-stu-id="090b8-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="090b8-106">De eenvoudigste manier om een codefragment maken is met de [nieuw IseSnippet &#91; PSITPro5_ISE &#93; ](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="090b8-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="090b8-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="090b8-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="090b8-108">auteur</span><span class="sxs-lookup"><span data-stu-id="090b8-108">Author</span></span>
  <span data-ttu-id="090b8-109">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="090b8-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="090b8-110">De alleen-lezen eigenschap die de naam van de auteur van het fragment opgehaald.</span><span class="sxs-lookup"><span data-stu-id="090b8-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="090b8-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="090b8-111">CodeFragment</span></span>
  <span data-ttu-id="090b8-112">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="090b8-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="090b8-113">De alleen-lezen eigenschap die het codefragment moet worden ingevoegd in de editor opgehaald.</span><span class="sxs-lookup"><span data-stu-id="090b8-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="090b8-114">Snelkoppeling</span><span class="sxs-lookup"><span data-stu-id="090b8-114">Shortcut</span></span>
  <span data-ttu-id="090b8-115">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="090b8-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="090b8-116">De alleen-lezen eigenschap die opgehaald van de Windows-sneltoets voor de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="090b8-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="090b8-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="090b8-117">See Also</span></span>
- [<span data-ttu-id="090b8-118">Het Object ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="090b8-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="090b8-119">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="090b8-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="090b8-120">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="090b8-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="090b8-121">De hiërarchie ISE</span><span class="sxs-lookup"><span data-stu-id="090b8-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
