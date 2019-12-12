---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISESnippetCollection-object
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030512"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="f78fe-103">Het ISESnippetCollection-object</span><span class="sxs-lookup"><span data-stu-id="f78fe-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="f78fe-104">Het **ISESnippetCollection** -object is een verzameling **ISESnippet** -objecten.</span><span class="sxs-lookup"><span data-stu-id="f78fe-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="f78fe-105">De verzameling bestanden die is gekoppeld aan een **PowerShellTab** -object, is een lid van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="f78fe-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="f78fe-106">Een voor beeld is de verzameling **$psISE. CurrentPowerShellTab. files** .</span><span class="sxs-lookup"><span data-stu-id="f78fe-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="f78fe-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="f78fe-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="f78fe-108">\( bestandspad laden \)</span><span class="sxs-lookup"><span data-stu-id="f78fe-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="f78fe-109">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="f78fe-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f78fe-110">Hiermee wordt een. fragmenten. ps1xml-bestand geladen dat door de gebruiker gedefinieerde fragmenten bevat.</span><span class="sxs-lookup"><span data-stu-id="f78fe-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="f78fe-111">De eenvoudigste manier om fragmenten te maken, is met behulp van de cmdlet New-IseSnippet, die deze automatisch opslaat in de profielmap, zodat ze elke keer dat u begint Windows PowerShell ISE worden geladen.</span><span class="sxs-lookup"><span data-stu-id="f78fe-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="f78fe-112">**Filepath** -teken reeks het pad en de bestands naam naar een. fragmenten. ps1xml-bestand dat fragment definities bevat.</span><span class="sxs-lookup"><span data-stu-id="f78fe-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="f78fe-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f78fe-113">See Also</span></span>

- [<span data-ttu-id="f78fe-114">De ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="f78fe-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="f78fe-115">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="f78fe-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f78fe-116">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="f78fe-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
