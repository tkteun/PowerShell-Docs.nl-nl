---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISESnippetCollection-object
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: bd5ed4a1f15e0a398b7c6a17f0071cad889be4a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950947"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="b9ba0-103">Het ISESnippetCollection-object</span><span class="sxs-lookup"><span data-stu-id="b9ba0-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="b9ba0-104">De **ISESnippetCollection** object is een verzameling **ISESnippet** objecten.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="b9ba0-105">De verzameling bestanden dat is gekoppeld aan een **PowerShellTab** object is lid van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="b9ba0-106">Een voorbeeld is de **$psISE.CurrentPowerShellTab.Files** verzameling.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="b9ba0-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="b9ba0-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="b9ba0-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="b9ba0-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="b9ba0-109">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b9ba0-110">Laadt een. snippets.ps1xml-bestand waarin de gebruiker gedefinieerde codefragmenten.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="b9ba0-111">De eenvoudigste manier om fragmenten te maken is met de cmdlet New-IseSnippet, waarmee automatisch in de profielmap van uw opgeslagen zodat ze worden geladen telkens wanneer u Windows PowerShell ISE start.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="b9ba0-112">**FilePathName** - tekenreeks van het pad en bestandsnaam naar een. snippets.ps1xml-bestand dat codefragment definities bevat.</span><span class="sxs-lookup"><span data-stu-id="b9ba0-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="b9ba0-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9ba0-113">See Also</span></span>

- [<span data-ttu-id="b9ba0-114">De ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="b9ba0-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="b9ba0-115">Doel van de Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="b9ba0-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b9ba0-116">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="b9ba0-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)