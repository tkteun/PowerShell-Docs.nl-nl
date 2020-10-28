---
ms.date: 06/05/2017
title: Het ISESnippet-object
description: Een ISESnippet-object is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISESnippet.
ms.openlocfilehash: 602b344686cbcfb1e994914d4e26438ff7e4b1de
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663406"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="f6098-103">Het ISESnippet-object</span><span class="sxs-lookup"><span data-stu-id="f6098-103">The ISESnippetObject</span></span>

<span data-ttu-id="f6098-104">Een **ISESnippet** -object is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="f6098-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="f6098-105">De leden van de `$psISE.CurrentPowerShellTab.Snippets` verzameling zijn alle voor beelden van **ISESnippet** -objecten.</span><span class="sxs-lookup"><span data-stu-id="f6098-105">The members of the `$psISE.CurrentPowerShellTab.Snippets` collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="f6098-106">De eenvoudigste manier om een fragment te maken, is door de cmdlet [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f6098-106">The easiest way to create a snippet is to use the [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="f6098-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="f6098-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="f6098-108">Auteur</span><span class="sxs-lookup"><span data-stu-id="f6098-108">Author</span></span>

<span data-ttu-id="f6098-109">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="f6098-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f6098-110">De alleen-lezen eigenschap waarmee de naam van de auteur van het fragment wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f6098-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="f6098-111">Cofragmentatie</span><span class="sxs-lookup"><span data-stu-id="f6098-111">CodeFragment</span></span>

<span data-ttu-id="f6098-112">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="f6098-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f6098-113">De alleen-lezen eigenschap waarmee het code fragment wordt opgehaald dat in de editor moet worden ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="f6098-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="f6098-114">Shortcutdimensie</span><span class="sxs-lookup"><span data-stu-id="f6098-114">Shortcut</span></span>

<span data-ttu-id="f6098-115">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="f6098-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f6098-116">De alleen-lezen eigenschap waarmee de Windows-sneltoets wordt opgehaald voor de menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="f6098-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="f6098-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f6098-117">See Also</span></span>

- [<span data-ttu-id="f6098-118">Het ISESnippetCollection-object</span><span class="sxs-lookup"><span data-stu-id="f6098-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="f6098-119">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f6098-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="f6098-120">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="f6098-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
