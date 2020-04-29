---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISESnippetCollection-object
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736042"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="05d71-103">Het ISESnippetCollection-object</span><span class="sxs-lookup"><span data-stu-id="05d71-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="05d71-104">Het **ISESnippetCollection** -object is een verzameling **ISESnippet** -objecten.</span><span class="sxs-lookup"><span data-stu-id="05d71-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="05d71-105">De verzameling bestanden die is gekoppeld aan een **PowerShellTab** -object, is een lid van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="05d71-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="05d71-106">Een voor beeld is `$psISE.CurrentPowerShellTab.Files` de verzameling.</span><span class="sxs-lookup"><span data-stu-id="05d71-106">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="05d71-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="05d71-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="05d71-108">Load\( filepath\)</span><span class="sxs-lookup"><span data-stu-id="05d71-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="05d71-109">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="05d71-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="05d71-110">Hiermee wordt `.snippets.ps1xml` een bestand geladen dat door de gebruiker gedefinieerde fragmenten bevat.</span><span class="sxs-lookup"><span data-stu-id="05d71-110">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="05d71-111">De eenvoudigste manier om fragmenten te maken, is door de `New-IseSnippet` cmdlet te gebruiken, die deze automatisch opslaat in de profielmap, zodat ze elke keer dat u begint Windows PowerShell ISE worden geladen.</span><span class="sxs-lookup"><span data-stu-id="05d71-111">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="05d71-112">**Filepath** -teken reeks het pad en de bestands naam naar een. fragmenten. ps1xml-bestand dat fragment definities bevat.</span><span class="sxs-lookup"><span data-stu-id="05d71-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="05d71-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="05d71-113">See Also</span></span>

- [<span data-ttu-id="05d71-114">Het ISESnippet-object</span><span class="sxs-lookup"><span data-stu-id="05d71-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="05d71-115">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="05d71-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="05d71-116">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="05d71-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
