---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Andere nuttige scriptobjecten
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: ff494f375c0d43d83b2a067dbe4f2ab35a90d564
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086201"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="0eb19-103">Andere nuttige scriptobjecten</span><span class="sxs-lookup"><span data-stu-id="0eb19-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="0eb19-104">De volgende objecten bieden extra scripts functionaliteit in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0eb19-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="0eb19-105">Ze zijn niet deel uitmaakt van de **$psISE** hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="0eb19-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="0eb19-106">Nuttige Scripting-objecten</span><span class="sxs-lookup"><span data-stu-id="0eb19-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="0eb19-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="0eb19-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="0eb19-108">Er zijn enkele beperkingen met betrekking tot de interactie van Windows PowerShell ISE met consoletoepassingen.</span><span class="sxs-lookup"><span data-stu-id="0eb19-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="0eb19-109">Een opdracht of een automatiseringsscript dat vereist dat tussenkomst van de gebruiker mogelijk niet werken voor de werking van de Windows PowerShell-console.</span><span class="sxs-lookup"><span data-stu-id="0eb19-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="0eb19-110">Het is raadzaam om te blokkeren van deze opdrachten of scripts niet kunnen worden uitgevoerd in het deelvenster met Windows PowerShell ISE-opdracht.</span><span class="sxs-lookup"><span data-stu-id="0eb19-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="0eb19-111">De **$psUnsupportedConsoleApplications** object houdt een lijst van deze opdrachten.</span><span class="sxs-lookup"><span data-stu-id="0eb19-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="0eb19-112">Als u probeert uit te voeren van de opdrachten in deze lijst, krijgt u een bericht weergegeven dat ze niet worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0eb19-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="0eb19-113">Het volgende script voegt een vermelding toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="0eb19-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="0eb19-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="0eb19-114">$psLocalHelp</span></span>

<span data-ttu-id="0eb19-115">Dit is een dictionary-object die wordt onderhouden door een contextgevoelige toewijzing tussen het Help-onderwerpen en hun bijbehorende koppelingen in het lokale gecompileerde HTML Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="0eb19-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="0eb19-116">Deze wordt gebruikt om de lokale Help voor een bepaald onderwerp zoekt.</span><span class="sxs-lookup"><span data-stu-id="0eb19-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="0eb19-117">U kunt toevoegen of verwijderen van onderwerpen in deze lijst.</span><span class="sxs-lookup"><span data-stu-id="0eb19-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="0eb19-118">Het volgende codevoorbeeld toont een voorbeeld sleutel / waarde-paren die zijn opgenomen in `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="0eb19-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="0eb19-119">Het volgende script voegt een vermelding toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="0eb19-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="0eb19-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="0eb19-120">$psOnlineHelp</span></span>

<span data-ttu-id="0eb19-121">Dit is een dictionary-object die wordt onderhouden door een contextgevoelige toewijzing tussen de titels van Help-onderwerpen en de bijbehorende externe URL's.</span><span class="sxs-lookup"><span data-stu-id="0eb19-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="0eb19-122">Deze wordt gebruikt om de Help voor een bepaald onderwerp vinden op het web.</span><span class="sxs-lookup"><span data-stu-id="0eb19-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="0eb19-123">U kunt toevoegen of verwijderen van onderwerpen in deze lijst.</span><span class="sxs-lookup"><span data-stu-id="0eb19-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="0eb19-124">Het volgende script voegt een vermelding toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="0eb19-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="0eb19-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0eb19-125">See Also</span></span>

[<span data-ttu-id="0eb19-126">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0eb19-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)