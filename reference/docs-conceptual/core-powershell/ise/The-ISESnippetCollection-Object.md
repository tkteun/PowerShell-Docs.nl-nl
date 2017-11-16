---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="e8f94-103">Het Object ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="e8f94-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="e8f94-104">De **ISESnippetCollection** object is een verzameling **ISESnippet** objecten.</span><span class="sxs-lookup"><span data-stu-id="e8f94-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="e8f94-105">De verzameling bestanden dat is gekoppeld aan een **PowerShellTab** object is lid van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="e8f94-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="e8f94-106">Een voorbeeld is de **$psISE.CurrentPowerShellTab.Files** verzameling.</span><span class="sxs-lookup"><span data-stu-id="e8f94-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="e8f94-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="e8f94-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="e8f94-108">Load\( FilePathName\)</span><span class="sxs-lookup"><span data-stu-id="e8f94-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="e8f94-109">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="e8f94-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="e8f94-110">Laadt een. snippets.ps1xml-bestand waarin de gebruiker gedefinieerde codefragmenten.</span><span class="sxs-lookup"><span data-stu-id="e8f94-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="e8f94-111">De eenvoudigste manier om fragmenten te maken is met de cmdlet New-IseSnippet, waarmee automatisch in de profielmap van uw opgeslagen zodat ze worden geladen telkens wanneer u Windows PowerShell ISE start.</span><span class="sxs-lookup"><span data-stu-id="e8f94-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="e8f94-112">**FilePathName** - tekenreeks van het pad en bestandsnaam naar een. snippets.ps1xml-bestand dat codefragment definities bevat.</span><span class="sxs-lookup"><span data-stu-id="e8f94-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="e8f94-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e8f94-113">See Also</span></span>
- [<span data-ttu-id="e8f94-114">De ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="e8f94-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="e8f94-115">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="e8f94-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="e8f94-116">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="e8f94-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="e8f94-117">De hiërarchie ISE</span><span class="sxs-lookup"><span data-stu-id="e8f94-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
