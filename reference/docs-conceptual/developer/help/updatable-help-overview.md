---
title: Overzicht van bijwerk bare Help | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810804"
---
# <a name="updatable-help-overview"></a><span data-ttu-id="e6302-102">Overzicht van Help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="e6302-102">Updatable Help Overview</span></span>

<span data-ttu-id="e6302-103">Dit document bevat een basis kennis van het ontwerp en de werking van de Windows Power shell-functie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e6302-103">This document provides a basic introduction to the design and operation of the Windows PowerShell Updatable Help feature.</span></span> <span data-ttu-id="e6302-104">Het is ontworpen voor auteurs van modules en anderen die Windows Power shell Help-onderwerpen leveren aan gebruikers.</span><span class="sxs-lookup"><span data-stu-id="e6302-104">It is designed for module authors and others who deliver Windows PowerShell help topics to users.</span></span>

## <a name="introduction"></a><span data-ttu-id="e6302-105">Inleiding</span><span class="sxs-lookup"><span data-stu-id="e6302-105">Introduction</span></span>

<span data-ttu-id="e6302-106">Windows Power shell Help-onderwerpen vormen een integraal onderdeel van de Windows Power shell-ervaring.</span><span class="sxs-lookup"><span data-stu-id="e6302-106">Windows PowerShell help topics are an integral part of the Windows PowerShell experience.</span></span> <span data-ttu-id="e6302-107">Net als Windows Power shell-modules worden Help-onderwerpen voortdurend bijgewerkt en verbeterd door de auteurs en door de bijdragen van de community van Windows Power shell-gebruikers.</span><span class="sxs-lookup"><span data-stu-id="e6302-107">Like Windows PowerShell modules, help topics are continually updated and improved by the authors and by the contributions of the community of Windows PowerShell users.</span></span>

<span data-ttu-id="e6302-108">De *bijwerk bare Help* -functie, geïntroduceerd in Windows power Shell 3,0, zorgt ervoor dat gebruikers over de nieuwste versies van Help-onderwerpen beschikken bij de opdracht prompt, zelfs voor ingebouwde Windows Power shell-opdrachten, zonder nieuwe modules te downloaden of Windows Update uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e6302-108">The *Updatable Help* feature, introduced in Windows PowerShell 3.0, ensures that users have the newest versions of help topics at the command prompt, even for built-in Windows PowerShell commands, without downloading new modules or running Windows Update.</span></span> <span data-ttu-id="e6302-109">Met de bijwerk bare Help kunt u eenvoudig een update maken door cmdlets te bieden waarmee de nieuwste versies van Help-onderwerpen van Internet worden gedownload en geïnstalleerd in de juiste submappen op de lokale computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e6302-109">Updatable Help makes updating simple by providing cmdlets that download the newest versions of help topics from the Internet and install them in the correct subdirectories on the user's local computer.</span></span> <span data-ttu-id="e6302-110">Zelfs gebruikers die zich achter een firewall bevinden, kunnen de nieuwe cmdlets gebruiken om bijgewerkte hulp te krijgen van een interne bestands share.</span><span class="sxs-lookup"><span data-stu-id="e6302-110">Even users who are behind firewalls can use the new cmdlets to get updated help from an internal file share.</span></span>

<span data-ttu-id="e6302-111">Help-informatie die kan worden bijgewerkt, wordt volledig ondersteund door alle Windows Power shell-modules in Windows® 8 en Windows Server® 2012, en de bijbehorende functies zijn beschikbaar voor alle auteurs van Windows Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="e6302-111">Updatable Help is fully supported by all Windows PowerShell modules in Windows® 8 and Windows Server® 2012, and its features are available to all Windows PowerShell module authors.</span></span> <span data-ttu-id="e6302-112">Help-informatie die kan worden bijgewerkt, ondersteunt alleen op XML gebaseerde Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="e6302-112">Updatable Help supports only XML-based help files.</span></span> <span data-ttu-id="e6302-113">Het biedt geen ondersteuning voor Help op basis van opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="e6302-113">It does not support comment-based help.</span></span>

<span data-ttu-id="e6302-114">Bij te werken Help omvat de volgende functies.</span><span class="sxs-lookup"><span data-stu-id="e6302-114">Updatable Help includes the following features.</span></span>

- <span data-ttu-id="e6302-115">De cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) , waarmee wordt bepaald of gebruikers over de nieuwste Help-bestanden voor een module beschikken en, als dat niet het geval is, downloadt de nieuwste Help-bestanden van Internet, pakt ze uit en installeert ze in de juiste module submappen op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e6302-115">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet, which determines whether users have the newest help files for a module and, if not, downloads the newest help files from the Internet, unpacks them, and installs them in the correct module subdirectories on the user's computer.</span></span>
  <span data-ttu-id="e6302-116">Gebruikers kunnen de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) gebruiken om onmiddellijk de zojuist geïnstalleerde Help-onderwerpen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e6302-116">Users can use the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet to view the newly-installed help topics immediately.</span></span>
  <span data-ttu-id="e6302-117">Het is niet nodig om Power shell opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="e6302-117">They do not need to restart PowerShell.</span></span>

- <span data-ttu-id="e6302-118">De cmdlet [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) , waarmee de nieuwste Help-bestanden van Internet worden gedownload en opgeslagen in een map van het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="e6302-118">The [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet, which downloads the newest help files from the Internet and saves them in a file system directory.</span></span> <span data-ttu-id="e6302-119">Gebruikers kunnen de `Update-Help` cmdlet gebruiken om Help-bestanden op te halen uit de map van het bestands systeem en deze uit te pakken en te installeren in de module submappen op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e6302-119">Users can use the `Update-Help` cmdlet to get help files from the file system directory, and unpack and install them in the module subdirectories on the user's computer.</span></span> <span data-ttu-id="e6302-120">De `Save-Help` cmdlet is bedoeld voor gebruikers met beperkte of geen Internet toegang en voor ondernemingen die de toegang tot internet liever beperken.</span><span class="sxs-lookup"><span data-stu-id="e6302-120">The `Save-Help` cmdlet is designed for users who have limited or no Internet access and for enterprises who prefer to limit Internet access.</span></span>

- <span data-ttu-id="e6302-121">**Help voor een module**.</span><span class="sxs-lookup"><span data-stu-id="e6302-121">**Help for a Module**.</span></span> <span data-ttu-id="e6302-122">Help-bestanden voor een module worden beheerd en geleverd als eenheid, zodat gebruikers alle Help-bestanden kunnen ophalen voor de modules die ze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e6302-122">Help files for a module are managed and delivered as a unit, so users can get all of the help files for the modules they use.</span></span> <span data-ttu-id="e6302-123">Help-informatie die kan worden bijgewerkt, wordt alleen ondersteund voor modules, niet voor Windows Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="e6302-123">Updatable help is supported only for modules, not for Windows PowerShell snap-ins.</span></span>

- <span data-ttu-id="e6302-124">**Versie ondersteuning**.</span><span class="sxs-lookup"><span data-stu-id="e6302-124">**Version support**.</span></span> <span data-ttu-id="e6302-125">Bij te werken Help wordt standaard vier Position (N1. N2. N3. N4) versie nummers.</span><span class="sxs-lookup"><span data-stu-id="e6302-125">Updatable Help uses standard four-position (N1.N2.N3.N4) version numbers.</span></span> <span data-ttu-id="e6302-126">Bij te werken Help worden Help-bestanden gedownload wanneer het versie nummer van de Help-bestanden op de computer van de gebruiker (of in de `Save-Help` map) lager is dan het versie nummer van de Help-bestanden op de Internet locatie.</span><span class="sxs-lookup"><span data-stu-id="e6302-126">Updatable Help downloads help files when the version number of the help files on the user's computer (or in the `Save-Help` directory) is lower than the version number of the  help files at the Internet location.</span></span>

- <span data-ttu-id="e6302-127">**Ondersteuning voor meerdere talen**.</span><span class="sxs-lookup"><span data-stu-id="e6302-127">**Multi-language support**.</span></span> <span data-ttu-id="e6302-128">Bij te werken Help ondersteunt de Help-bestanden van de module in meerdere GEBRUIKERSINTERFACE culturen.</span><span class="sxs-lookup"><span data-stu-id="e6302-128">Updatable Help supports module help files in multiple UI cultures.</span></span> <span data-ttu-id="e6302-129">De namen van de bij te werken Help-bestanden zijn standaard taal codes, zoals ' en-US ' en ' ja-JP ', en de `Update-Help` `Save-Help` cmdlets en de Help-bestanden worden in taalspecifieke submappen van de module directory geplaatst.</span><span class="sxs-lookup"><span data-stu-id="e6302-129">Updatable Help file names include standard language codes, such as "en-US" and "ja-JP", and the `Update-Help` and `Save-Help` cmdlets place the help files into language-specific subdirectories of the module directory.</span></span>

- <span data-ttu-id="e6302-130">**Automatisch gegenereerde Help**.</span><span class="sxs-lookup"><span data-stu-id="e6302-130">**Auto-generated help**.</span></span> <span data-ttu-id="e6302-131">Met de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) wordt de basis Help weer gegeven voor opdrachten die geen Help-bestanden hebben.</span><span class="sxs-lookup"><span data-stu-id="e6302-131">The [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet displays basic help for commands that do not have help files.</span></span> <span data-ttu-id="e6302-132">De automatisch gegenereerde Help omvat de opdracht syntaxis en aliassen, en instructies voor het gebruik van online-Help en Help bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e6302-132">The auto-generated help includes the command syntax and aliases, and instructions for using online help and Updatable Help.</span></span>

- <span data-ttu-id="e6302-133">**Uitgebreide online-Help**.</span><span class="sxs-lookup"><span data-stu-id="e6302-133">**Enhanced Online help**.</span></span> <span data-ttu-id="e6302-134">Voor eenvoudige toegang tot online-Help is geen Help-bestanden meer nodig.</span><span class="sxs-lookup"><span data-stu-id="e6302-134">Easy access to online help no longer requires help files.</span></span> <span data-ttu-id="e6302-135">De para meter **online** van de `Get-Help` cmdlet haalt nu de URL van een online Help-onderwerp op uit de waarde van de eigenschap **HelpUri** van elke opdracht, als de URL van de online Help niet kan worden gevonden in een Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="e6302-135">The **Online** parameter of the `Get-Help` cmdlet now gets the URL of an online help topic from the value of the **HelpUri** property of any command, if it cannot find the online help URL in a help file.</span></span> <span data-ttu-id="e6302-136">U kunt de eigenschap **HelpUri** invullen door een **HelpUri** -kenmerk toe te voegen aan de code van cmdlets, functions en CIM-opdrachten of door gebruik te maken van de \*\*. \*\*Een Help-instructie op basis van opmerkingen in werk stromen en scripts.</span><span class="sxs-lookup"><span data-stu-id="e6302-136">You can populate the **HelpUri** property by adding a **HelpUri** attribute to the code of cmdlets, functions, and CIM commands, or by using the **.Link** comment-based help directive in workflows and scripts.</span></span>

  <span data-ttu-id="e6302-137">Om ervoor te zorgen dat de Help-bestanden kunnen worden bijgewerkt, worden de Windows Power shell-modules in Windows 8 en Windows Server vNext niet geleverd met Help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="e6302-137">To make our help files updatable, the Windows PowerShell modules in Windows 8 and Windows Server vNext do not come with help files.</span></span> <span data-ttu-id="e6302-138">Gebruikers kunnen de Help-informatie die kan worden bijgewerkt, gebruiken om Help-bestanden te installeren en ze bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e6302-138">Users can use Updatable Help to install help files and update them.</span></span> <span data-ttu-id="e6302-139">Auteurs van andere modules kunnen Help-bestanden in modules bevatten of deze weglaten.</span><span class="sxs-lookup"><span data-stu-id="e6302-139">Authors of other modules can include help files in modules or omit them.</span></span> <span data-ttu-id="e6302-140">Ondersteuning voor bijwerk bare Help is optioneel, maar wordt aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="e6302-140">Support for Updatable Help is optional, but recommended.</span></span>