---
ms.date: 12/31/2019
title: Het ISESnippetCollection-object
description: Het ISESnippetCollection-object is een verzameling ISESnippet-objecten. De verzameling bestanden die is gekoppeld aan een PowerShellTab-object, is een lid van deze klasse.
ms.openlocfilehash: e6170ddf72d5ead840aa3015d4de1dcb21dbfeff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655969"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="a4a22-104">Het ISESnippetCollection-object</span><span class="sxs-lookup"><span data-stu-id="a4a22-104">The ISESnippetCollection Object</span></span>

<span data-ttu-id="a4a22-105">Het **ISESnippetCollection** -object is een verzameling **ISESnippet** -objecten.</span><span class="sxs-lookup"><span data-stu-id="a4a22-105">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="a4a22-106">De verzameling bestanden die is gekoppeld aan een **PowerShellTab** -object, is een lid van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="a4a22-106">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="a4a22-107">Een voor beeld is de `$psISE.CurrentPowerShellTab.Files` verzameling.</span><span class="sxs-lookup"><span data-stu-id="a4a22-107">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="a4a22-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="a4a22-108">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="a4a22-109">Load \( filepath \)</span><span class="sxs-lookup"><span data-stu-id="a4a22-109">Load\( FilePathName \)</span></span>

<span data-ttu-id="a4a22-110">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="a4a22-110">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="a4a22-111">Hiermee wordt een `.snippets.ps1xml` bestand geladen dat door de gebruiker gedefinieerde fragmenten bevat.</span><span class="sxs-lookup"><span data-stu-id="a4a22-111">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="a4a22-112">De eenvoudigste manier om fragmenten te maken, is door de `New-IseSnippet` cmdlet te gebruiken, die deze automatisch opslaat in de profielmap, zodat ze elke keer dat u begint Windows PowerShell ISE worden geladen.</span><span class="sxs-lookup"><span data-stu-id="a4a22-112">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="a4a22-113">**Filepath** -teken reeks het pad en de bestands naam naar een .snippets.ps1XML-bestand dat fragment definities bevat.</span><span class="sxs-lookup"><span data-stu-id="a4a22-113">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="a4a22-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a4a22-114">See Also</span></span>

- [<span data-ttu-id="a4a22-115">Het ISESnippet-object</span><span class="sxs-lookup"><span data-stu-id="a4a22-115">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="a4a22-116">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a4a22-116">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="a4a22-117">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="a4a22-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
