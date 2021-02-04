---
title: Aan de slag met PowerShell
description: Waar u kunt zoeken en hoe u Power shell kunt starten voor nieuwe gebruikers.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 8b9fee222347970df4e35f9ba0841232952a292d
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216177"
---
# <a name="chapter-1---getting-started-with-powershell"></a><span data-ttu-id="c933c-103">Hoofd stuk 1: aan de slag met Power shell</span><span class="sxs-lookup"><span data-stu-id="c933c-103">Chapter 1 - Getting Started with PowerShell</span></span>

<span data-ttu-id="c933c-104">Ik vind vaak dat presentatoren bij conferenties en gebruikers groeps vergaderingen al Power shell uitvoeren bij het starten van presentaties op instap niveau.</span><span class="sxs-lookup"><span data-stu-id="c933c-104">I often find that presenters at conferences and user group meetings already have PowerShell running when they start entry-level presentations.</span></span> <span data-ttu-id="c933c-105">Dit boek begint met het beantwoorden van de vragen die ik heb gehoord en die Power shell nog niet eerder hebben gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c933c-105">This book begins by answering the questions I've heard attendees who haven't previously used PowerShell ask in those sessions.</span></span>

<span data-ttu-id="c933c-106">Dit hoofd stuk is specifiek gericht op het zoeken en starten van Power shell en het oplossen van enkele van de eerste knel punten die nieuwe gebruikers met Power shell ervaren.</span><span class="sxs-lookup"><span data-stu-id="c933c-106">Specifically, this chapter focuses on finding and launching PowerShell, and solving some of the initial pain points that new users experience with PowerShell.</span></span> <span data-ttu-id="c933c-107">Zorg ervoor dat u de voor beelden die in dit hoofd stuk worden weer gegeven op uw computer met Windows 10 test omgeving volgt.</span><span class="sxs-lookup"><span data-stu-id="c933c-107">Be sure to follow along and walk through the examples shown in this chapter on your Windows 10 lab environment computer.</span></span>

## <a name="what-do-i-need-to-get-started-with-powershell"></a><span data-ttu-id="c933c-108">Wat heb ik nodig om aan de slag te gaan met Power shell?</span><span class="sxs-lookup"><span data-stu-id="c933c-108">What do I need to get started with PowerShell?</span></span>

<span data-ttu-id="c933c-109">Alle moderne versies van Windows-besturings systemen worden geleverd met Power shell geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c933c-109">All modern versions of Windows operating systems ship with PowerShell installed.</span></span> <span data-ttu-id="c933c-110">Als u een oudere versie dan 5,1 gebruikt, moet u de nieuwste versie installeren.</span><span class="sxs-lookup"><span data-stu-id="c933c-110">If you're running a version older than 5.1, you should install the latest version.</span></span>

- <span data-ttu-id="c933c-111">Zie [bestaande Windows Power shell bijwerken][] als u een upgrade wilt uitvoeren naar Windows power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="c933c-111">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][]</span></span>
- <span data-ttu-id="c933c-112">Zie [Power Shell installeren][] voor informatie over het installeren van de meest recente versie van Power shell</span><span class="sxs-lookup"><span data-stu-id="c933c-112">To install the latest version of PowerShell, see [Installing PowerShell][]</span></span>

## <a name="where-do-i-find-powershell"></a><span data-ttu-id="c933c-113">Waar vind ik Power shell?</span><span class="sxs-lookup"><span data-stu-id="c933c-113">Where do I find PowerShell?</span></span>

<span data-ttu-id="c933c-114">De eenvoudigste manier om Power shell te vinden in Windows 10 is **Power shell** in de zoek balk te typen, zoals weer gegeven in afbeelding 1-1.</span><span class="sxs-lookup"><span data-stu-id="c933c-114">The easiest way to find PowerShell on Windows 10 is to type **PowerShell** into the search bar as shown in Figure 1-1.</span></span>

![Afbeelding 1-1-zoeken naar Power shell in het menu Start](media/figure1-1.png)

<span data-ttu-id="c933c-116">U ziet dat er vier verschillende snelkoppelingen voor Power shell worden weer gegeven in afbeelding 1-1.</span><span class="sxs-lookup"><span data-stu-id="c933c-116">Notice that four different shortcuts for PowerShell are shown in Figure 1-1.</span></span> <span data-ttu-id="c933c-117">Op de computer die wordt gebruikt voor demonstratie doeleinden in dit boek wordt de 64-bits versie van Windows 10 uitgevoerd, dus is er een 64-bits versie van de Power shell-console en de Power shell ISE (Integrated Scripting Environment), en een 32-bits versie van elk item, zoals aangeduid door het achtervoegsel (x86) op de snelkoppelingen.</span><span class="sxs-lookup"><span data-stu-id="c933c-117">The computer used for demonstration purposes in this book is running the 64-bit version of Windows 10 so there's a 64-bit version of the PowerShell console and the PowerShell ISE (Integrated Scripting Environment), and a 32-bit version of each one as denoted by the (x86) suffix on the shortcuts.</span></span> <span data-ttu-id="c933c-118">Als u een 32-bits versie van Windows 10 gebruikt, hebt u slechts twee snelkoppelingen.</span><span class="sxs-lookup"><span data-stu-id="c933c-118">If you happen to be running a 32-bit version of Windows 10, you'll only have two shortcuts.</span></span> <span data-ttu-id="c933c-119">Deze items hebben niet het achtervoegsel (x86), maar zijn 32-bits versies.</span><span class="sxs-lookup"><span data-stu-id="c933c-119">Those items don't have the (x86) suffix, but are 32-bit versions.</span></span> <span data-ttu-id="c933c-120">Als u een 64-bits besturings systeem hebt, is het raadzaam om de 64-bits versie van Power shell uit te voeren, tenzij u een specifieke reden hebt om de 32-bits versie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c933c-120">If you have a 64-bit operating system, my recommendation is to run the 64-bit version of PowerShell unless you have a specific reason for running the 32-bit version.</span></span>

<span data-ttu-id="c933c-121">Zie [Starting Windows Power shell][](Engelstalig) voor meer informatie over het starten van Power shell op andere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="c933c-121">For information about starting PowerShell on other versions of Windows, see [Starting Windows PowerShell][].</span></span>

## <a name="how-do-i-launch-powershell"></a><span data-ttu-id="c933c-122">Hoe kan ik Power shell starten?</span><span class="sxs-lookup"><span data-stu-id="c933c-122">How do I launch PowerShell?</span></span>

<span data-ttu-id="c933c-123">In de Enter prise-bedrijfs omgevingen die worden ondersteund, gebruiken we drie verschillende Active Directory gebruikers accounts.</span><span class="sxs-lookup"><span data-stu-id="c933c-123">In the production enterprise environments that I support, I use three different Active Directory user accounts.</span></span> <span data-ttu-id="c933c-124">Ik heb deze accounts gespiegeld in de test omgeving die in dit boek wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c933c-124">I've mirrored those accounts in the lab environment used in this book.</span></span> <span data-ttu-id="c933c-125">Meld u bij de Windows 10-computer aan als een domein gebruiker die geen domein of lokale beheerder is.</span><span class="sxs-lookup"><span data-stu-id="c933c-125">I log into the Windows 10 computer as a domain user who is not a domain or local administrator.</span></span>

<span data-ttu-id="c933c-126">Ik heb de Power shell-console gestart door te klikken op de snelkoppeling Windows Power shell, zoals weer gegeven in afbeelding 1-1.</span><span class="sxs-lookup"><span data-stu-id="c933c-126">I've launched the PowerShell console by clicking on the "Windows PowerShell" shortcut as shown in Figure 1-1.</span></span>

![Afbeelding 1-4-titel balk van het Power shell-venster](media/figure1-4.png)

<span data-ttu-id="c933c-128">U ziet dat de titel balk van de Power shell-console ' Windows Power shell ' aangeeft, zoals wordt weer gegeven in afbeelding 1-4.</span><span class="sxs-lookup"><span data-stu-id="c933c-128">Notice that the title bar of the PowerShell console says "Windows PowerShell" as shown in Figure 1-4.</span></span> <span data-ttu-id="c933c-129">Sommige opdrachten worden prima uitgevoerd, maar Power shell kan niet deel nemen aan gebruikers Access Control (UAC).</span><span class="sxs-lookup"><span data-stu-id="c933c-129">Some commands run fine, but PowerShell can't participate in User Access Control (UAC).</span></span> <span data-ttu-id="c933c-130">Dit betekent dat het niet mogelijk is om te vragen om benodigde bevoegdheden voor taken die de goed keuring van een beheerder vereisen.</span><span class="sxs-lookup"><span data-stu-id="c933c-130">That means it's unable to prompt for elevation for tasks that require the approval of an administrator.</span></span>
<span data-ttu-id="c933c-131">Het volgende fout bericht wordt gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="c933c-131">The following error message is generated:</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

<span data-ttu-id="c933c-132">De oplossing voor dit probleem is om Power shell uit te voeren als een domein gebruiker die een lokale beheerder is.</span><span class="sxs-lookup"><span data-stu-id="c933c-132">The solution to this problem is to run PowerShell as a domain user who is a local administrator.</span></span>
<span data-ttu-id="c933c-133">Dit is hoe mijn tweede domein gebruikers account is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="c933c-133">This is how my second domain user account is configured.</span></span> <span data-ttu-id="c933c-134">Met de principal van de minimale bevoegdheid moet dit account geen domein beheerder zijn of een verhoogde bevoegdheid hebben in het domein.</span><span class="sxs-lookup"><span data-stu-id="c933c-134">Using the principal of least privilege, this account should NOT be a domain administrator, or have any elevated privileges in the domain.</span></span>

<span data-ttu-id="c933c-135">Sluit Power shell.</span><span class="sxs-lookup"><span data-stu-id="c933c-135">Close PowerShell.</span></span> <span data-ttu-id="c933c-136">Start de Power shell-console opnieuw, behalve deze tijd, klik met de rechter muisknop op de snelkoppeling **Windows Power shell** en selecteer als **administrator uitvoeren** , zoals weer gegeven in afbeelding 1-5.</span><span class="sxs-lookup"><span data-stu-id="c933c-136">Relaunch the PowerShell console, except this time right-click on the **Windows PowerShell** shortcut and select **Run as administrator** as shown in Figure 1-5.</span></span>

![Afbeelding 1-5-context menu-als administrator uitvoeren](media/figure1-5.png)

<span data-ttu-id="c933c-138">Als u bent aangemeld als normale gebruiker bij Windows, wordt u gevraagd om referenties.</span><span class="sxs-lookup"><span data-stu-id="c933c-138">If you're logged into Windows as a normal user, you'll be prompted for credentials.</span></span> <span data-ttu-id="c933c-139">Ik voer de referenties in voor mijn gebruikers account dat een domein gebruiker en een lokale beheerder is, zoals wordt weer gegeven in afbeelding 1-6.</span><span class="sxs-lookup"><span data-stu-id="c933c-139">I'll enter the credentials for my user account who is a domain user and local admin as shown in Figure 1-6.</span></span>

![Afbeelding 1-6](media/figure1-6.png)

<span data-ttu-id="c933c-141">Zodra Power shell als beheerder opnieuw wordt gestart, moet de titel balk ' beheerder: Windows Power shell ' zeggen, zoals wordt weer gegeven in afbeelding 1-7.</span><span class="sxs-lookup"><span data-stu-id="c933c-141">Once PowerShell is relaunched as an administrator, the title bar should say "Administrator: Windows PowerShell" as shown in Figure 1-7.</span></span>

![Afbeelding 1-7](media/figure1-7.png)

<span data-ttu-id="c933c-143">Nu Power shell wordt uitgevoerd als een lokale beheerder, is UAC niet meer een probleem wanneer een opdracht wordt uitgevoerd op de lokale computer waarvoor normaal gesp roken een prompt vereist.</span><span class="sxs-lookup"><span data-stu-id="c933c-143">Now that PowerShell is being run elevated as a local administrator, UAC will no longer be a problem when a command is run on the local computer that would normally require a prompt for elevation.</span></span> <span data-ttu-id="c933c-144">Denk eraan dat elke opdracht die wordt uitgevoerd vanuit dit verhoogde exemplaar van de Power shell-console, ook met verhoogde bevoegdheden kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c933c-144">Keep in mind though that any command run from this elevated instance of the PowerShell console, also runs elevated.</span></span>

<span data-ttu-id="c933c-145">Als u Power shell wilt vereenvoudigen en als beheerder wilt starten, kunt u deze het beste vastmaken aan de taak balk en instellen dat deze automatisch wordt gestart als een beheerder telkens wanneer deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c933c-145">To simplify finding PowerShell and launching it as an administrator, I recommend pinning it to the taskbar and setting it to automatically launch as an admin each time it's run.</span></span>

<span data-ttu-id="c933c-146">Zoek opnieuw naar Power shell, maar deze keer met de rechter muisknop op en selecteer ' aan taak balk vastmaken ', zoals wordt weer gegeven in afbeelding 1-8.</span><span class="sxs-lookup"><span data-stu-id="c933c-146">Search for PowerShell again, except this time right-click on it and select "Pin to taskbar" as shown in Figure 1-8.</span></span>

![Afbeelding 1-8](media/figure1-8.png)

<span data-ttu-id="c933c-148">Klik met de rechter muisknop op de Power shell-snelkoppeling die nu is vastgemaakt aan de taak balk en selecteer Eigenschappen, zoals weer gegeven in afbeelding 1-9.</span><span class="sxs-lookup"><span data-stu-id="c933c-148">Right-click on the PowerShell shortcut that's now pinned to the taskbar and select properties as shown in Figure 1-9.</span></span>

![Afbeelding 1-9-gebruikers account beheer-referenties opgeven](media/figure1-9.png)

<span data-ttu-id="c933c-150">Klik op Geavanceerd als aangeduid door #1 in afbeelding 1-10, schakel het selectie vakje als administrator uitvoeren in zoals aangegeven door #2 in afbeelding 1-10, en klik vervolgens twee maal op OK om de wijzigingen te accepteren en af te sluiten van beide dialoog vensters.</span><span class="sxs-lookup"><span data-stu-id="c933c-150">Click on "Advanced" as denoted by #1 in Figure 1-10, then check the "Run as administrator" checkbox as denoted by #2 in Figure 1-10, and then click OK twice to accept the changes and exit out of both dialog boxes.</span></span>

![Afbeelding 1-10: titel balk met "beheerder"](media/figure1-10.png)

<span data-ttu-id="c933c-152">U hoeft zich nooit zorgen te maken over het vinden van Power shell of het al dan niet uitvoeren van een beheerder.</span><span class="sxs-lookup"><span data-stu-id="c933c-152">You'll never have to worry about finding PowerShell or whether or not it's running as an administrator again.</span></span>

<span data-ttu-id="c933c-153">Het uitvoeren van Power shell is verhoogd als beheerder om te voor komen dat problemen met UAC alleen gevolgen hebben voor opdrachten die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c933c-153">Running PowerShell elevated as an administrator to prevent having problems with UAC only impacts commands that are run against the local computer.</span></span> <span data-ttu-id="c933c-154">Dit heeft geen invloed op opdrachten die op externe computers zijn gericht.</span><span class="sxs-lookup"><span data-stu-id="c933c-154">It has no effect on commands that target remote computers.</span></span>

## <a name="what-version-of-powershell-am-i-running"></a><span data-ttu-id="c933c-155">Welke versie van Power shell wordt uitgevoerd?</span><span class="sxs-lookup"><span data-stu-id="c933c-155">What version of PowerShell am I running?</span></span>

<span data-ttu-id="c933c-156">Er zijn een aantal automatische variabelen in Power shell die status informatie opslaan.</span><span class="sxs-lookup"><span data-stu-id="c933c-156">There are a number of automatic variables in PowerShell that store state information.</span></span> <span data-ttu-id="c933c-157">Een van deze variabelen is `$PSVersionTable` , die een hashtabel bevat die kan worden gebruikt om de relevante informatie over de Power shell-versie weer te geven:</span><span class="sxs-lookup"><span data-stu-id="c933c-157">One of these variables is `$PSVersionTable`, which contains a hashtable that can be used to display the relevant PowerShell version information:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="c933c-158">Nieuwere versies van Windows Power shell worden gedistribueerd als onderdeel van het Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="c933c-158">Newer versions of Windows PowerShell are distributed as part of the Windows Management Framework (WMF).</span></span> <span data-ttu-id="c933c-159">Er is een specifieke versie van de .NET Framework vereist, afhankelijk van de versie van WMF.</span><span class="sxs-lookup"><span data-stu-id="c933c-159">A specific version of the .NET Framework is required depending on the WMF version.</span></span> <span data-ttu-id="c933c-160">Zie [bestaande Windows Power shell bijwerken][]als u een upgrade wilt uitvoeren naar Windows power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="c933c-160">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][].</span></span>

## <a name="execution-policy"></a><span data-ttu-id="c933c-161">Uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="c933c-161">Execution Policy</span></span>

<span data-ttu-id="c933c-162">In tegens telling tot populaire overtuiging is het uitvoerings beleid in Power shell geen beveiligings grens.</span><span class="sxs-lookup"><span data-stu-id="c933c-162">Contrary to popular belief, the execution policy in PowerShell is not a security boundary.</span></span> <span data-ttu-id="c933c-163">Het is ontworpen om te voor komen dat een gebruiker onbewust een script uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c933c-163">It's designed to prevent a user from unknowingly running a script.</span></span> <span data-ttu-id="c933c-164">Een bepaalde gebruiker kan het uitvoerings beleid eenvoudig overs laan in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c933c-164">A determined user can easily bypass the execution policy in PowerShell.</span></span> <span data-ttu-id="c933c-165">In tabel 1-2 wordt het standaard uitvoerings beleid voor de huidige Windows-besturings systemen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c933c-165">Table 1-2 shows the default execution policy for current Windows operating systems.</span></span>

| <span data-ttu-id="c933c-166">Versie van het Windows-besturings systeem</span><span class="sxs-lookup"><span data-stu-id="c933c-166">Windows Operating System Version</span></span> | <span data-ttu-id="c933c-167">Standaard uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="c933c-167">Default Execution Policy</span></span> |
| -------------------------------- | ------------------------ |
| <span data-ttu-id="c933c-168">Server 2019</span><span class="sxs-lookup"><span data-stu-id="c933c-168">Server 2019</span></span>                      | <span data-ttu-id="c933c-169">Externe hand tekening</span><span class="sxs-lookup"><span data-stu-id="c933c-169">Remote Signed</span></span>            |
| <span data-ttu-id="c933c-170">Server 2016</span><span class="sxs-lookup"><span data-stu-id="c933c-170">Server 2016</span></span>                      | <span data-ttu-id="c933c-171">Externe hand tekening</span><span class="sxs-lookup"><span data-stu-id="c933c-171">Remote Signed</span></span>            |
| <span data-ttu-id="c933c-172">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c933c-172">Windows 10</span></span>                       | <span data-ttu-id="c933c-173">Beperkt</span><span class="sxs-lookup"><span data-stu-id="c933c-173">Restricted</span></span>               |

<span data-ttu-id="c933c-174">Ongeacht de instelling voor het uitvoerings beleid, kan elke Power shell-opdracht interactief worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c933c-174">Regardless of the execution policy setting, any PowerShell command can be run interactively.</span></span> <span data-ttu-id="c933c-175">Het uitvoerings beleid is alleen van invloed op opdrachten die worden uitgevoerd in een script.</span><span class="sxs-lookup"><span data-stu-id="c933c-175">The execution policy only affects commands running in a script.</span></span> <span data-ttu-id="c933c-176">De `Get-ExecutionPolicy` cmdlet wordt gebruikt om te bepalen wat de huidige uitvoerings beleids instelling is en de `Set-ExecutionPolicy` cmdlet wordt gebruikt om het uitvoerings beleid te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c933c-176">The `Get-ExecutionPolicy` cmdlet is used to determine what the current execution policy setting is and the `Set-ExecutionPolicy` cmdlet is used to change the execution policy.</span></span> <span data-ttu-id="c933c-177">Mijn aanbeveling is het **RemoteSigned** -beleid te gebruiken. hiervoor moeten gedownloade scripts worden ondertekend door een vertrouwde uitgever om te worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c933c-177">My recommendation is to use the **RemoteSigned** policy, which requires downloaded scripts to be signed by a trusted publisher in order to be run.</span></span>

<span data-ttu-id="c933c-178">Controleer het huidige uitvoerings beleid:</span><span class="sxs-lookup"><span data-stu-id="c933c-178">Check the current execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

<span data-ttu-id="c933c-179">Power shell-scripts kunnen niet worden uitgevoerd als het uitvoerings beleid is ingesteld op **beperkt**.</span><span class="sxs-lookup"><span data-stu-id="c933c-179">PowerShell scripts can't be run at all when the execution policy is set to **Restricted**.</span></span> <span data-ttu-id="c933c-180">Dit is de standaard instelling op alle Windows client-besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="c933c-180">This is the default setting on all Windows client operating systems.</span></span> <span data-ttu-id="c933c-181">Als u het probleem wilt demonstreren, slaat u de volgende code op als een bestand met de `.ps1` naam `Stop-TimeService.ps1` .</span><span class="sxs-lookup"><span data-stu-id="c933c-181">To demonstrate the problem, save the following code as a `.ps1` file named `Stop-TimeService.ps1`.</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

<span data-ttu-id="c933c-182">Deze opdracht wordt interactief uitgevoerd zonder fouten zolang Power shell wordt uitgevoerd als beheerder.</span><span class="sxs-lookup"><span data-stu-id="c933c-182">That command runs interactively without error as long as PowerShell is run elevated as an administrator.</span></span> <span data-ttu-id="c933c-183">Maar zodra het is opgeslagen als een script bestand en u het script probeert uit te voeren, wordt er een fout gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="c933c-183">But as soon as it's saved as a script file and you try to execute the script, it generates an error:</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="c933c-184">U ziet dat de fout die wordt weer gegeven in de vorige set resultaten precies aangeeft wat het probleem is (het uitvoeren van scripts is uitgeschakeld op dit systeem).</span><span class="sxs-lookup"><span data-stu-id="c933c-184">Notice that the error shown in the previous set of results tells you exactly what the problem is (running scripts is disabled on this system).</span></span> <span data-ttu-id="c933c-185">Wanneer u een opdracht uitvoert in Power shell waarmee een fout bericht wordt gegenereerd, lees dan het fout bericht in plaats van de opdracht opnieuw uit te voeren en stel in dat het programma met succes wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c933c-185">When you run a command in PowerShell that generates an error message, be sure to read the error message instead of just rerunning the command and hoping that it runs successfully.</span></span>

<span data-ttu-id="c933c-186">Wijzig het Power shell-uitvoerings beleid in extern ondertekend.</span><span class="sxs-lookup"><span data-stu-id="c933c-186">Change the PowerShell execution policy to remote signed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

<span data-ttu-id="c933c-187">Lees de waarschuwing die wordt weer gegeven wanneer u het uitvoerings beleid wijzigt.</span><span class="sxs-lookup"><span data-stu-id="c933c-187">Be sure to read the warning that's displayed when changing the execution policy.</span></span> <span data-ttu-id="c933c-188">U wordt ook aangeraden de [about_Execution_Policies][] Help-onderwerp te bekijken om te controleren of u de beveiligings implicaties van het wijzigen van het uitvoerings beleid begrijpt.</span><span class="sxs-lookup"><span data-stu-id="c933c-188">I also recommend taking a look at the [about_Execution_Policies][] help topic to make sure you understand the security implications of changing the execution policy.</span></span>

<span data-ttu-id="c933c-189">Nu het uitvoerings beleid is ingesteld op **RemoteSigned**, `Stop-TimeService.ps1` wordt het script zonder fouten beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="c933c-189">Now that the execution policy has been set to **RemoteSigned**, the `Stop-TimeService.ps1` script runs error free.</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

<span data-ttu-id="c933c-190">Zorg ervoor dat u de Windows Time-service start voordat u doorgaat, anders kunt u onverwachte problemen ondervinden.</span><span class="sxs-lookup"><span data-stu-id="c933c-190">Be sure to start your Windows Time service before continuing otherwise you may run into unforeseen problems.</span></span>

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a><span data-ttu-id="c933c-191">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="c933c-191">Summary</span></span>

<span data-ttu-id="c933c-192">In dit hoofd stuk hebt u geleerd hoe u Power shell kunt vinden en starten, en hoe u een snelkoppeling maakt waarmee Power shell als beheerder wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="c933c-192">In this chapter, you've learned how to find and launch PowerShell, and how to create a shortcut that launches PowerShell as an administrator.</span></span> <span data-ttu-id="c933c-193">U hebt ook geleerd over het standaard uitvoerings beleid en hoe u dit kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c933c-193">You've also learned about the default execution policy and how to change it.</span></span>

## <a name="review"></a><span data-ttu-id="c933c-194">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="c933c-194">Review</span></span>

1. <span data-ttu-id="c933c-195">Hoe kunt u bepalen welke Power shell-versie op een computer wordt uitgevoerd?</span><span class="sxs-lookup"><span data-stu-id="c933c-195">How do you determine what PowerShell version a computer is running?</span></span>
1. <span data-ttu-id="c933c-196">Waarom is het belang rijk om Power shell met verhoogde bevoegdheid als beheerder te starten?</span><span class="sxs-lookup"><span data-stu-id="c933c-196">Why is it important to launch PowerShell elevated as an administrator?</span></span>
1. <span data-ttu-id="c933c-197">Hoe kunt u het huidige Power shell-uitvoerings beleid bepalen?</span><span class="sxs-lookup"><span data-stu-id="c933c-197">How do you determine the current PowerShell execution policy?</span></span>
1. <span data-ttu-id="c933c-198">Wat voor komt het standaard beleid voor Power shell-uitvoering op Windows-client computers?</span><span class="sxs-lookup"><span data-stu-id="c933c-198">What does the default PowerShell execution policy on Windows client computers prevent from occurring?</span></span>
1. <span data-ttu-id="c933c-199">Hoe wijzigt u het Power shell-uitvoerings beleid?</span><span class="sxs-lookup"><span data-stu-id="c933c-199">How do you change the PowerShell execution policy?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="c933c-200">Aanbevolen documentatie</span><span class="sxs-lookup"><span data-stu-id="c933c-200">Recommended Reading</span></span>

<span data-ttu-id="c933c-201">Voor degenen die meer informatie willen over de onderwerpen die in dit hoofd stuk worden behandeld, raden we u aan de volgende Help-onderwerpen voor Power shell te lezen.</span><span class="sxs-lookup"><span data-stu-id="c933c-201">For those who want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="c933c-202">[about_Automatic_Variables][]</span><span class="sxs-lookup"><span data-stu-id="c933c-202">[about_Automatic_Variables][]</span></span>
- <span data-ttu-id="c933c-203">[about_Hash_Tables][]</span><span class="sxs-lookup"><span data-stu-id="c933c-203">[about_Hash_Tables][]</span></span>
- <span data-ttu-id="c933c-204">[about_Execution_Policies][]</span><span class="sxs-lookup"><span data-stu-id="c933c-204">[about_Execution_Policies][]</span></span>

<span data-ttu-id="c933c-205">In het volgende hoofd stuk vindt u informatie over de vind baarheid van opdrachten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c933c-205">In the next chapter, you'll learn about the discoverability of commands in PowerShell.</span></span> <span data-ttu-id="c933c-206">Een van de dingen die worden behandeld, is het bijwerken van Power shell, zodat deze Help-onderwerpen direct vanuit Power shell kunnen worden weer gegeven in plaats van ze op internet te hoeven bekijken.</span><span class="sxs-lookup"><span data-stu-id="c933c-206">One of the things that will be covered is how to update PowerShell so those help topics can be viewed right from within PowerShell instead of having to view them on the internet.</span></span>

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Hash_Tables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[about_Execution_Policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[Bestaande Windows Power shell bijwerken]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Upgrading existing Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[PowerShell installeren]: /powershell/scripting/install/installing-powershell
[Installing PowerShell]: /powershell/scripting/install/installing-powershell
[Windows PowerShell starten]: /powershell/scripting/windows-powershell/starting-windows-powershell
[Starting Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
