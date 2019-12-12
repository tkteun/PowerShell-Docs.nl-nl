---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISESnippet-object
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028883"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="03fa9-103">Het ISESnippet-object</span><span class="sxs-lookup"><span data-stu-id="03fa9-103">The ISESnippetObject</span></span>

<span data-ttu-id="03fa9-104">Een **ISESnippet** -object is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="03fa9-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="03fa9-105">De leden van de verzameling **$psISE. CurrentPowerShellTab. fragmentes** zijn alle voor beelden van **ISESnippet** -objecten.</span><span class="sxs-lookup"><span data-stu-id="03fa9-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="03fa9-106">De eenvoudigste manier om een fragment te maken, is door de cmdlet [New&#91;-&#93; IseSnippet PSITPro5_ISE](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="03fa9-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="03fa9-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="03fa9-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="03fa9-108">Auteur</span><span class="sxs-lookup"><span data-stu-id="03fa9-108">Author</span></span>

<span data-ttu-id="03fa9-109">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="03fa9-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="03fa9-110">De alleen-lezen eigenschap waarmee de naam van de auteur van het fragment wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="03fa9-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="03fa9-111">Cofragmentatie</span><span class="sxs-lookup"><span data-stu-id="03fa9-111">CodeFragment</span></span>

<span data-ttu-id="03fa9-112">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="03fa9-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="03fa9-113">De alleen-lezen eigenschap waarmee het code fragment wordt opgehaald dat in de editor moet worden ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="03fa9-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="03fa9-114">Shortcutdimensie</span><span class="sxs-lookup"><span data-stu-id="03fa9-114">Shortcut</span></span>

<span data-ttu-id="03fa9-115">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="03fa9-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="03fa9-116">De alleen-lezen eigenschap waarmee de Windows-sneltoets wordt opgehaald voor de menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="03fa9-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="03fa9-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="03fa9-117">See Also</span></span>

- [<span data-ttu-id="03fa9-118">Het ISESnippetCollection-object</span><span class="sxs-lookup"><span data-stu-id="03fa9-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="03fa9-119">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="03fa9-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="03fa9-120">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="03fa9-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
