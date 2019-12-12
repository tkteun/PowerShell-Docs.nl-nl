---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Andere nuttige scriptobjecten
ms.openlocfilehash: 4f236246714b0608658bbd535851489912430336
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71325144"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="5a643-103">Andere nuttige scriptobjecten</span><span class="sxs-lookup"><span data-stu-id="5a643-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="5a643-104">De volgende objecten bieden extra script functionaliteit in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="5a643-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="5a643-105">Ze maken geen deel uit van de **$psISE** hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="5a643-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="5a643-106">Nuttige script objecten</span><span class="sxs-lookup"><span data-stu-id="5a643-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="5a643-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="5a643-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="5a643-108">Er zijn enkele beperkingen ten aanzien van de interactie van Windows PowerShell ISE met console toepassingen.</span><span class="sxs-lookup"><span data-stu-id="5a643-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="5a643-109">Een opdracht of een automatiserings script waarvoor tussen komst van de gebruiker is vereist, werkt mogelijk niet zoals in de Windows Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="5a643-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="5a643-110">U kunt voor komen dat deze opdrachten of scripts worden uitgevoerd in het opdracht venster Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="5a643-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="5a643-111">Het **$psUnsupportedConsoleApplications** -object houdt een lijst bij van deze opdrachten.</span><span class="sxs-lookup"><span data-stu-id="5a643-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="5a643-112">Als u de opdrachten in deze lijst probeert uit te voeren, wordt er een bericht weer gegeven dat niet wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5a643-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="5a643-113">Met het volgende script wordt een item toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="5a643-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="5a643-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="5a643-114">$psLocalHelp</span></span>

<span data-ttu-id="5a643-115">Dit is een woordenlijst object dat een context gevoelige toewijzing onderhoudt tussen Help-onderwerpen en de bijbehorende koppelingen in het lokale gecompileerde HTML Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="5a643-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="5a643-116">Het wordt gebruikt om de lokale Help voor een bepaald onderwerp te vinden.</span><span class="sxs-lookup"><span data-stu-id="5a643-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="5a643-117">U kunt onderwerpen uit deze lijst toevoegen of verwijderen.</span><span class="sxs-lookup"><span data-stu-id="5a643-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="5a643-118">In het volgende code voorbeeld ziet u enkele voor beelden van sleutel-waardeparen die zijn opgenomen in `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="5a643-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

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

<span data-ttu-id="5a643-119">Met het volgende script wordt een item toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="5a643-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="5a643-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="5a643-120">$psOnlineHelp</span></span>

<span data-ttu-id="5a643-121">Dit is een woordenlijst object dat een context gevoelige toewijzing onderhoudt tussen de titels van de Help-onderwerpen en de bijbehorende externe Url's.</span><span class="sxs-lookup"><span data-stu-id="5a643-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="5a643-122">Het wordt gebruikt om de Help voor een bepaald onderwerp op het web te vinden.</span><span class="sxs-lookup"><span data-stu-id="5a643-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="5a643-123">U kunt onderwerpen uit deze lijst toevoegen of verwijderen.</span><span class="sxs-lookup"><span data-stu-id="5a643-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="5a643-124">Met het volgende script wordt een item toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="5a643-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="5a643-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5a643-125">See Also</span></span>

[<span data-ttu-id="5a643-126">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="5a643-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
