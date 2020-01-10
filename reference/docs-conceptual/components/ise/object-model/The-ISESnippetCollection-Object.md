---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISESnippetCollection-object
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736042"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="dd6d5-103">Het ISESnippetCollection-object</span><span class="sxs-lookup"><span data-stu-id="dd6d5-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="dd6d5-104">Het **ISESnippetCollection** -object is een verzameling **ISESnippet** -objecten.</span><span class="sxs-lookup"><span data-stu-id="dd6d5-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="dd6d5-105">De verzameling bestanden die is gekoppeld aan een **PowerShellTab** -object, is een lid van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="dd6d5-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="dd6d5-106">Een voor beeld is de verzameling `$psISE.CurrentPowerShellTab.Files`.</span><span class="sxs-lookup"><span data-stu-id="dd6d5-106">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="dd6d5-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="dd6d5-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="dd6d5-108">\( bestandspad laden \)</span><span class="sxs-lookup"><span data-stu-id="dd6d5-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="dd6d5-109">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="dd6d5-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="dd6d5-110">Hiermee wordt een `.snippets.ps1xml`-bestand geladen dat door de gebruiker gedefinieerde fragmenten bevat.</span><span class="sxs-lookup"><span data-stu-id="dd6d5-110">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="dd6d5-111">De eenvoudigste manier om fragmenten te maken, is met behulp van de cmdlet `New-IseSnippet`, die deze automatisch opslaat in de profielmap, zodat deze elke keer dat u begint Windows PowerShell ISE wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="dd6d5-111">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="dd6d5-112">**Filepath** -teken reeks het pad en de bestands naam naar een. fragmenten. ps1xml-bestand dat fragment definities bevat.</span><span class="sxs-lookup"><span data-stu-id="dd6d5-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="dd6d5-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dd6d5-113">See Also</span></span>

- [<span data-ttu-id="dd6d5-114">De ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="dd6d5-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="dd6d5-115">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="dd6d5-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="dd6d5-116">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="dd6d5-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
