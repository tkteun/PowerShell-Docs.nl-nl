---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Andere nuttige Scripting objecten
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="f17af-103">Andere nuttige Scripting objecten</span><span class="sxs-lookup"><span data-stu-id="f17af-103">Other Useful Scripting Objects</span></span>
  <span data-ttu-id="f17af-104">De volgende objecten bieden extra scripting functionaliteit in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f17af-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="f17af-105">Ze maken geen deel uit van de **$psISE** hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="f17af-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="f17af-106">Nuttige Scripting-objecten</span><span class="sxs-lookup"><span data-stu-id="f17af-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="f17af-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="f17af-107">$psUnsupportedConsoleApplications</span></span>
 <span data-ttu-id="f17af-108">Er zijn enkele beperkingen op de interactie van Windows PowerShell ISE met consoletoepassingen.</span><span class="sxs-lookup"><span data-stu-id="f17af-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="f17af-109">Een opdracht of een automatiseringsscript dat vereist dat tussenkomst van de gebruiker werken de werking van de Windows PowerShell-console niet.</span><span class="sxs-lookup"><span data-stu-id="f17af-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="f17af-110">Het is raadzaam om deze opdrachten of scripts worden uitgevoerd in het deelvenster met Windows PowerShell ISE-opdracht te blokkeren.</span><span class="sxs-lookup"><span data-stu-id="f17af-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="f17af-111">De **$psUnsupportedConsoleApplications** object houdt een lijst van deze opdrachten.</span><span class="sxs-lookup"><span data-stu-id="f17af-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="f17af-112">Als u probeert de opdrachten uitvoeren in deze lijst, krijgt u een bericht dat ze niet worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="f17af-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="f17af-113">Het volgende script voegt een vermelding toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="f17af-113">The following script adds an entry to the list.</span></span>

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a><span data-ttu-id="f17af-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="f17af-114">$psLocalHelp</span></span>
 <span data-ttu-id="f17af-115">Dit is een dictionary-object dat wordt de contextgevoelige toewijzing tussen het Help-onderwerpen en hun bijbehorende koppelingen in het lokale gecompileerde HTML Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="f17af-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="f17af-116">Deze wordt gebruikt voor het vinden van de lokale Help voor een bepaald onderwerp.</span><span class="sxs-lookup"><span data-stu-id="f17af-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="f17af-117">U kunt toevoegen of verwijderen van onderwerpen uit deze lijst.</span><span class="sxs-lookup"><span data-stu-id="f17af-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="f17af-118">Het volgende codevoorbeeld toont een aantal voorbeelden van sleutel-waardeparen die zijn opgenomen in **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="f17af-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="f17af-119">Voorbeelduitvoer</span><span class="sxs-lookup"><span data-stu-id="f17af-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="f17af-120">Sleutel:-Computer</span><span class="sxs-lookup"><span data-stu-id="f17af-120">Key : Add-Computer</span></span>|<span data-ttu-id="f17af-121">Waarde: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="f17af-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="f17af-122">Sleutel:-Inhoud</span><span class="sxs-lookup"><span data-stu-id="f17af-122">Key : Add-Content</span></span>|<span data-ttu-id="f17af-123">Waarde: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="f17af-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

 <span data-ttu-id="f17af-124">Het volgende script voegt een vermelding toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="f17af-124">The following script adds an entry to the list.</span></span>

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="f17af-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="f17af-125">$psOnlineHelp</span></span>
 <span data-ttu-id="f17af-126">Dit is een dictionary-object dat wordt de contextgevoelige toewijzing tussen de titels van Help-onderwerpen en de bijbehorende externe URL's.</span><span class="sxs-lookup"><span data-stu-id="f17af-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="f17af-127">Wordt gebruikt voor het vinden van de Help voor een bepaald onderwerp op het web.</span><span class="sxs-lookup"><span data-stu-id="f17af-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="f17af-128">U kunt toevoegen of verwijderen van onderwerpen uit deze lijst.</span><span class="sxs-lookup"><span data-stu-id="f17af-128">You can add or delete topics from this list.</span></span>

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="f17af-129">Voorbeelduitvoer</span><span class="sxs-lookup"><span data-stu-id="f17af-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="f17af-130">Sleutel:-Computer</span><span class="sxs-lookup"><span data-stu-id="f17af-130">Key : Add-Computer</span></span>|<span data-ttu-id="f17af-131">Waarde: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="f17af-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="f17af-132">Sleutel:-Inhoud</span><span class="sxs-lookup"><span data-stu-id="f17af-132">Key : Add-Content</span></span>|<span data-ttu-id="f17af-133">Waarde: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="f17af-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="f17af-134">Het volgende script voegt een vermelding toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="f17af-134">The following script adds an entry to the list.</span></span>

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="f17af-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f17af-135">See Also</span></span>
- [<span data-ttu-id="f17af-136">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="f17af-136">The Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
