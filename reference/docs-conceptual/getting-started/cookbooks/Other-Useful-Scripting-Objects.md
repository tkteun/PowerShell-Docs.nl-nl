---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Andere nuttige scriptobjecten
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 0e87e9919199e011ab5abec5b07dccc8494ad64a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="57440-103">Andere nuttige scriptobjecten</span><span class="sxs-lookup"><span data-stu-id="57440-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="57440-104">De volgende objecten bieden extra scripting functionaliteit in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="57440-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="57440-105">Ze maken geen deel uit van de **$psISE** hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="57440-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="57440-106">Nuttige Scripting-objecten</span><span class="sxs-lookup"><span data-stu-id="57440-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="57440-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="57440-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="57440-108">Er zijn enkele beperkingen op de interactie van Windows PowerShell ISE met consoletoepassingen.</span><span class="sxs-lookup"><span data-stu-id="57440-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="57440-109">Een opdracht of een automatiseringsscript dat vereist dat tussenkomst van de gebruiker werken de werking van de Windows PowerShell-console niet.</span><span class="sxs-lookup"><span data-stu-id="57440-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="57440-110">Het is raadzaam om deze opdrachten of scripts worden uitgevoerd in het deelvenster met Windows PowerShell ISE-opdracht te blokkeren.</span><span class="sxs-lookup"><span data-stu-id="57440-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="57440-111">De **$psUnsupportedConsoleApplications** object houdt een lijst van deze opdrachten.</span><span class="sxs-lookup"><span data-stu-id="57440-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="57440-112">Als u probeert de opdrachten uitvoeren in deze lijst, krijgt u een bericht dat ze niet worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="57440-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="57440-113">Het volgende script voegt een vermelding toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="57440-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="57440-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="57440-114">$psLocalHelp</span></span>

<span data-ttu-id="57440-115">Dit is een dictionary-object dat wordt de contextgevoelige toewijzing tussen het Help-onderwerpen en hun bijbehorende koppelingen in het lokale gecompileerde HTML Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="57440-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="57440-116">Deze wordt gebruikt voor het vinden van de lokale Help voor een bepaald onderwerp.</span><span class="sxs-lookup"><span data-stu-id="57440-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="57440-117">U kunt toevoegen of verwijderen van onderwerpen uit deze lijst.</span><span class="sxs-lookup"><span data-stu-id="57440-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="57440-118">Het volgende codevoorbeeld toont een aantal voorbeelden van sleutel-waardeparen die zijn opgenomen in **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="57440-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="57440-119">Voorbeelduitvoer</span><span class="sxs-lookup"><span data-stu-id="57440-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="57440-120">Sleutel:-Computer</span><span class="sxs-lookup"><span data-stu-id="57440-120">Key : Add-Computer</span></span>|<span data-ttu-id="57440-121">Waarde: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="57440-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="57440-122">Sleutel:-Inhoud</span><span class="sxs-lookup"><span data-stu-id="57440-122">Key : Add-Content</span></span>|<span data-ttu-id="57440-123">Waarde: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="57440-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

<span data-ttu-id="57440-124">Het volgende script voegt een vermelding toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="57440-124">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="57440-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="57440-125">$psOnlineHelp</span></span>

<span data-ttu-id="57440-126">Dit is een dictionary-object dat wordt de contextgevoelige toewijzing tussen de titels van Help-onderwerpen en de bijbehorende externe URL's.</span><span class="sxs-lookup"><span data-stu-id="57440-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="57440-127">Wordt gebruikt voor het vinden van de Help voor een bepaald onderwerp op het web.</span><span class="sxs-lookup"><span data-stu-id="57440-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="57440-128">U kunt toevoegen of verwijderen van onderwerpen uit deze lijst.</span><span class="sxs-lookup"><span data-stu-id="57440-128">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

### <a name="sample-output"></a><span data-ttu-id="57440-129">Voorbeelduitvoer</span><span class="sxs-lookup"><span data-stu-id="57440-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="57440-130">Sleutel:-Computer</span><span class="sxs-lookup"><span data-stu-id="57440-130">Key : Add-Computer</span></span>|<span data-ttu-id="57440-131">Waarde: http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="57440-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="57440-132">Sleutel:-Inhoud</span><span class="sxs-lookup"><span data-stu-id="57440-132">Key : Add-Content</span></span>|<span data-ttu-id="57440-133">Waarde: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="57440-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="57440-134">Het volgende script voegt een vermelding toe aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="57440-134">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="57440-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="57440-135">See Also</span></span>

- [<span data-ttu-id="57440-136">Doel van de Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="57440-136">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)