---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISESnippetCollection-object
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030512"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="fa883-103">Het ISESnippetCollection-object</span><span class="sxs-lookup"><span data-stu-id="fa883-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="fa883-104">De **ISESnippetCollection** object is een verzameling van **ISESnippet** objecten.</span><span class="sxs-lookup"><span data-stu-id="fa883-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="fa883-105">De verzameling bestanden dat is gekoppeld aan een **PowerShellTab** object is lid van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="fa883-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="fa883-106">Een voorbeeld is de **$psISE.CurrentPowerShellTab.Files** verzameling.</span><span class="sxs-lookup"><span data-stu-id="fa883-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="fa883-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="fa883-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="fa883-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="fa883-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="fa883-109">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="fa883-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="fa883-110">Belasting een. snippets.ps1xml-bestand met de gebruiker gedefinieerde codefragmenten.</span><span class="sxs-lookup"><span data-stu-id="fa883-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="fa883-111">Er is de eenvoudigste manier om codefragmenten maken met de cmdlet New-IseSnippet, die automatisch in de profielmap van uw opgeslagen zodat ze geladen elke keer worden dat u start Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa883-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="fa883-112">**FilePathName** - tekenreeks van het pad en bestandsnaam naar een. snippets.ps1xml-bestand dat fragment definities bevat.</span><span class="sxs-lookup"><span data-stu-id="fa883-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="fa883-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fa883-113">See Also</span></span>

- [<span data-ttu-id="fa883-114">The ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="fa883-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="fa883-115">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="fa883-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="fa883-116">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="fa883-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
