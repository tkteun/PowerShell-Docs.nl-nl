---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISESnippet-object
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057975"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="dc070-103">Het ISESnippet-object</span><span class="sxs-lookup"><span data-stu-id="dc070-103">The ISESnippetObject</span></span>

<span data-ttu-id="dc070-104">Een **ISESnippet** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="dc070-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="dc070-105">De leden van de **$psISE.CurrentPowerShellTab.Snippets** verzameling zijn alle voorbeelden van **ISESnippet** objecten.</span><span class="sxs-lookup"><span data-stu-id="dc070-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="dc070-106">De eenvoudigste manier om het maken van een codefragment is met de [New-IseSnippet&#91;PSITPro5_ISE&#93; ](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dc070-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="dc070-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="dc070-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="dc070-108">Auteur</span><span class="sxs-lookup"><span data-stu-id="dc070-108">Author</span></span>

<span data-ttu-id="dc070-109">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="dc070-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="dc070-110">De alleen-lezen eigenschap die haalt u de naam van de auteur van het codefragment.</span><span class="sxs-lookup"><span data-stu-id="dc070-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="dc070-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="dc070-111">CodeFragment</span></span>

<span data-ttu-id="dc070-112">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="dc070-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="dc070-113">De alleen-lezen eigenschap waarmee het codefragment moet worden ingevoegd in de editor worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="dc070-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="dc070-114">Snelkoppeling</span><span class="sxs-lookup"><span data-stu-id="dc070-114">Shortcut</span></span>

<span data-ttu-id="dc070-115">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="dc070-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="dc070-116">De alleen-lezen eigenschap die opgehaald van de Windows sneltoets voor de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="dc070-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="dc070-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dc070-117">See Also</span></span>

- [<span data-ttu-id="dc070-118">Het ISESnippetCollection-Object</span><span class="sxs-lookup"><span data-stu-id="dc070-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="dc070-119">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="dc070-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="dc070-120">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="dc070-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)