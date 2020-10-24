---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Andere nuttige scriptobjecten
description: In dit artikel worden objecten beschreven die extra script functionaliteit bieden in de Windows PowerShell ISE.
ms.openlocfilehash: c20daa0045bc07b1f21aafa42a80ce7c47ee7331
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500263"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="bb163-104">Andere nuttige scriptobjecten</span><span class="sxs-lookup"><span data-stu-id="bb163-104">Other Useful Scripting Objects</span></span>

<span data-ttu-id="bb163-105">De volgende objecten bieden extra script functionaliteit in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bb163-105">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="bb163-106">Ze maken geen deel uit van de **$psISE** hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="bb163-106">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="bb163-107">Nuttige script objecten</span><span class="sxs-lookup"><span data-stu-id="bb163-107">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="bb163-108">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="bb163-108">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="bb163-109">Er zijn enkele beperkingen ten aanzien van de interactie van Windows PowerShell ISE met console toepassingen.</span><span class="sxs-lookup"><span data-stu-id="bb163-109">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="bb163-110">Een opdracht of een automatiserings script waarvoor tussen komst van de gebruiker is vereist, werkt mogelijk niet zoals in de Windows Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="bb163-110">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="bb163-111">U kunt voor komen dat deze opdrachten of scripts worden uitgevoerd in het opdracht venster Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bb163-111">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="bb163-112">Het **$psUnsupportedConsoleApplications** -object houdt een lijst bij van deze opdrachten.</span><span class="sxs-lookup"><span data-stu-id="bb163-112">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="bb163-113">Als u de opdrachten in deze lijst probeert uit te voeren, wordt er een bericht weer gegeven dat niet wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bb163-113">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="bb163-114">Met het volgende script wordt een item toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="bb163-114">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="bb163-115">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="bb163-115">$psLocalHelp</span></span>

<span data-ttu-id="bb163-116">Dit is een woordenlijst object dat een context gevoelige toewijzing onderhoudt tussen Help-onderwerpen en de bijbehorende koppelingen in het lokale gecompileerde HTML Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="bb163-116">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="bb163-117">Het wordt gebruikt om de lokale Help voor een bepaald onderwerp te vinden.</span><span class="sxs-lookup"><span data-stu-id="bb163-117">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="bb163-118">U kunt onderwerpen uit deze lijst toevoegen of verwijderen.</span><span class="sxs-lookup"><span data-stu-id="bb163-118">You can add or delete topics from this list.</span></span> <span data-ttu-id="bb163-119">In het volgende code voorbeeld ziet u enkele voor beelden van sleutel-waardeparen die zijn opgenomen in `$psLocalHelp` .</span><span class="sxs-lookup"><span data-stu-id="bb163-119">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```Output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="bb163-120">Met het volgende script wordt een item toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="bb163-120">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="bb163-121">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="bb163-121">$psOnlineHelp</span></span>

<span data-ttu-id="bb163-122">Dit is een woordenlijst object dat een context gevoelige toewijzing onderhoudt tussen de titels van de Help-onderwerpen en de bijbehorende externe Url's.</span><span class="sxs-lookup"><span data-stu-id="bb163-122">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="bb163-123">Het wordt gebruikt om de Help voor een bepaald onderwerp op het web te vinden.</span><span class="sxs-lookup"><span data-stu-id="bb163-123">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="bb163-124">U kunt onderwerpen uit deze lijst toevoegen of verwijderen.</span><span class="sxs-lookup"><span data-stu-id="bb163-124">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```Output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="bb163-125">Met het volgende script wordt een item toegevoegd aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="bb163-125">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="bb163-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bb163-126">See Also</span></span>

[<span data-ttu-id="bb163-127">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="bb163-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
