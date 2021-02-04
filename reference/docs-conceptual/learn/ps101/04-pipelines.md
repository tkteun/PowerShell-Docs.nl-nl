---
title: One-liners en de pijplijn
description: Een Power shell One-line is een doorlopende pijp lijn met meerdere opdrachten om één taak uit te voeren.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 1483ec6b76d17c3dd081356ecff85a929fc43e2c
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216156"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a><span data-ttu-id="02d2e-103">Hoofd stuk 4: One-Lines en de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="02d2e-103">Chapter 4 - One-liners and the pipeline</span></span>

<span data-ttu-id="02d2e-104">Als ik Power shell voor het eerst heb gestart, heb ik dan terug naar de gebruikers interface, als ik een taak met een Power shell-One-line-instructie niet kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="02d2e-104">When I first started learning PowerShell, if I couldn't accomplish a task with a PowerShell one-liner, I went back to the GUI.</span></span> <span data-ttu-id="02d2e-105">Na verloop van tijd heb ik mijn vaardig heden ontwikkeld voor het schrijven van scripts, functies en modules.</span><span class="sxs-lookup"><span data-stu-id="02d2e-105">Over time, I built my skills up to writing scripts, functions, and modules.</span></span> <span data-ttu-id="02d2e-106">Zorg ervoor dat u geen overmatige voor beelden meer kunt zien op internet.</span><span class="sxs-lookup"><span data-stu-id="02d2e-106">Don't allow yourself to become overwhelmed by some of the more advanced examples you may see on the internet.</span></span> <span data-ttu-id="02d2e-107">Niemand is een natuurlijke expert met Power shell.</span><span class="sxs-lookup"><span data-stu-id="02d2e-107">No one is a natural expert with PowerShell.</span></span> <span data-ttu-id="02d2e-108">Alle beginners worden in één keer tegelijk besproken.</span><span class="sxs-lookup"><span data-stu-id="02d2e-108">We were all beginners at one time.</span></span>

<span data-ttu-id="02d2e-109">Ik heb een stukje advies om gebruikers te bieden die nog steeds gebruikmaken van de GUI voor beheer: Installeer de beheer hulpprogramma's op uw beheer werkstation en beheer uw servers op afstand.</span><span class="sxs-lookup"><span data-stu-id="02d2e-109">I have a bit of advice to offer those of you who are still using the GUI for administration: install the management tools on your admin workstation and manage your servers remotely.</span></span> <span data-ttu-id="02d2e-110">Op deze manier is het niet van belang dat de server een GUI of Server Core-installatie van het besturings systeem uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02d2e-110">This way it won't matter if the server is running a GUI or Server Core installation of the operating system.</span></span>
<span data-ttu-id="02d2e-111">U kunt u helpen bij het voorbereiden van het extern beheren van servers met Power shell.</span><span class="sxs-lookup"><span data-stu-id="02d2e-111">It's going to help prepare you for managing servers remotely with PowerShell.</span></span>

<span data-ttu-id="02d2e-112">Net als bij vorige hoofd stukken moet u de computer van uw Windows 10-test omgeving volgen.</span><span class="sxs-lookup"><span data-stu-id="02d2e-112">As with previous chapters, be sure to follow along on your Windows 10 lab environment computer.</span></span>

## <a name="one-liners"></a><span data-ttu-id="02d2e-113">One-Liners</span><span class="sxs-lookup"><span data-stu-id="02d2e-113">One-Liners</span></span>

<span data-ttu-id="02d2e-114">Een Power shell One-line is een doorlopende pijp lijn en niet noodzakelijkerwijs een opdracht die zich op één fysieke lijn bevindt.</span><span class="sxs-lookup"><span data-stu-id="02d2e-114">A PowerShell one-liner is one continuous pipeline and not necessarily a command that's on one physical line.</span></span> <span data-ttu-id="02d2e-115">Niet alle opdrachten op één fysieke regel zijn One-Lines.</span><span class="sxs-lookup"><span data-stu-id="02d2e-115">Not all commands that are on one physical line are one-liners.</span></span>

<span data-ttu-id="02d2e-116">Hoewel de volgende opdracht zich op meerdere fysieke regels bevindt, is het een Power shell One-line, omdat het een doorlopende pijp lijn is.</span><span class="sxs-lookup"><span data-stu-id="02d2e-116">Even though the following command is on multiple physical lines, it's a PowerShell one-liner because it's one continuous pipeline.</span></span> <span data-ttu-id="02d2e-117">Het kan op één fysieke regel worden geschreven, maar ik heb ervoor gekozen om op het pipe-symbool een regel afbreek punt te zetten.</span><span class="sxs-lookup"><span data-stu-id="02d2e-117">It could be written on one physical line, but I've chosen to line break at the pipe symbol.</span></span> <span data-ttu-id="02d2e-118">Het pipe-symbool is een van de tekens waarin een natuurlijke regel afbreeking is toegestaan in Power shell.</span><span class="sxs-lookup"><span data-stu-id="02d2e-118">The pipe symbol is one of the characters where a natural line break is allowed in PowerShell.</span></span>

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

<span data-ttu-id="02d2e-119">Natuurlijke lijn onderbrekingen kunnen zich voordoen bij veelgebruikte tekens, zoals komma ( `,` ) en haakjes ( `[` ), accolades () en `{` haakjes () `(` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-119">Natural line breaks can occur at commonly used characters including comma (`,`) and opening brackets (`[`), braces (`{`), and parenthesis (`(`).</span></span> <span data-ttu-id="02d2e-120">Andere die niet algemeen zijn, bevatten de punt komma ( `;` ), is gelijk aan teken ( `=` ) en zowel dubbele aanhalings tekens openen ( `'` , `"` ).</span><span class="sxs-lookup"><span data-stu-id="02d2e-120">Others that aren't so common include the semicolon (`;`), equals sign (`=`), and both opening single and double quotes (`'`,`"`).</span></span>

<span data-ttu-id="02d2e-121">Het `` ` `` accent teken apostroffen () of accent grave gebruiken als een regel vervolg teken is een controversieel-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="02d2e-121">Using the backtick (`` ` ``) or grave accent character as a line continuation character is a controversial topic.</span></span> <span data-ttu-id="02d2e-122">Mijn aanbeveling is om dit te voor komen als dat mogelijk is.</span><span class="sxs-lookup"><span data-stu-id="02d2e-122">My recommendation is to try to avoid it if at all possible.</span></span> <span data-ttu-id="02d2e-123">Er worden vaak Power shell-opdrachten weer geven die zijn geschreven met behulp van een apostroffen direct na een natuurlijk regel teken.</span><span class="sxs-lookup"><span data-stu-id="02d2e-123">I often see PowerShell commands written using a backtick immediately after a natural line break character.</span></span>
<span data-ttu-id="02d2e-124">Er is geen reden om het te zijn.</span><span class="sxs-lookup"><span data-stu-id="02d2e-124">There's no reason for it to be there.</span></span>

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="02d2e-125">De opdrachten die worden weer gegeven in de vorige twee voor beelden, werken prima in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="02d2e-125">The commands shown in the previous two examples work fine in the PowerShell console.</span></span> <span data-ttu-id="02d2e-126">Maar als u deze probeert uit te voeren in het console venster van de Power shell-ISE, wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-126">But if you try to run them in the console pane of the PowerShell ISE, they'll generate an error.</span></span> <span data-ttu-id="02d2e-127">Het console venster van de Power shell-ISE wacht niet totdat de rest van de opdracht wordt ingevoerd op de volgende regel, zoals de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="02d2e-127">The console pane of the PowerShell ISE doesn't wait for the rest of the command to be entered on the next line like the PowerShell console does.</span></span> <span data-ttu-id="02d2e-128">Als u dit probleem wilt voor komen in het console venster van de Power shell-ISE, gebruikt u <kbd>SHIFT</kbd> + <kbd>Enter</kbd> in plaats van alleen op <kbd>Enter</kbd> om door te gaan met een opdracht op een andere regel.</span><span class="sxs-lookup"><span data-stu-id="02d2e-128">To avoid this problem in the console pane of the PowerShell ISE, use <kbd>Shift</kbd>+<kbd>Enter</kbd> instead of just pressing <kbd>Enter</kbd> when continuing a command on another line.</span></span>

<span data-ttu-id="02d2e-129">Dit volgende voor beeld is geen Power shell One-line, omdat het niet een doorlopende pijp lijn is.</span><span class="sxs-lookup"><span data-stu-id="02d2e-129">This next example isn't a PowerShell one-liner because it's not one continuous pipeline.</span></span> <span data-ttu-id="02d2e-130">Het is twee afzonderlijke opdrachten op één regel, gescheiden door een punt komma.</span><span class="sxs-lookup"><span data-stu-id="02d2e-130">It's two separate commands on one line, separated by a semicolon.</span></span>

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="02d2e-131">Veel programmeer-en script talen vereisen een punt komma aan het einde van elke regel.</span><span class="sxs-lookup"><span data-stu-id="02d2e-131">Many programming and scripting languages require a semicolon at the end of each line.</span></span> <span data-ttu-id="02d2e-132">Hoewel ze op die manier kunnen worden gebruikt in Power shell, wordt het niet aanbevolen, omdat ze niet nodig zijn.</span><span class="sxs-lookup"><span data-stu-id="02d2e-132">While they can be used that way in PowerShell, it's not recommended because they're not needed.</span></span>

## <a name="filtering-left"></a><span data-ttu-id="02d2e-133">Filters links</span><span class="sxs-lookup"><span data-stu-id="02d2e-133">Filtering Left</span></span>

<span data-ttu-id="02d2e-134">De resultaten van de opdrachten die in dit hoofd stuk worden weer gegeven, zijn gefilterd op een subset.</span><span class="sxs-lookup"><span data-stu-id="02d2e-134">The results of the commands shown in this chapter have been filtered down to a subset.</span></span> <span data-ttu-id="02d2e-135">`Get-Service`Is bijvoorbeeld gebruikt met de para meter **name** voor het filteren van de lijst met services die zijn geretourneerd door alleen de Windows Time-service.</span><span class="sxs-lookup"><span data-stu-id="02d2e-135">For example, `Get-Service` was used with the **Name** parameter to filter the list of services that were returned to only the Windows Time service.</span></span>

<span data-ttu-id="02d2e-136">In de pijp lijn wilt u de resultaten altijd filteren op wat u zo snel mogelijk op zoek bent.</span><span class="sxs-lookup"><span data-stu-id="02d2e-136">In the pipeline, you always want to filter the results down to what you're looking for as early as possible.</span></span> <span data-ttu-id="02d2e-137">U kunt dit doen met behulp van para meters op de eerste opdracht of, de één helemaal links.</span><span class="sxs-lookup"><span data-stu-id="02d2e-137">This is accomplished using parameters on the first command or, the one to the far left.</span></span>
<span data-ttu-id="02d2e-138">Dit wordt soms _filters links_ genoemd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-138">This is sometimes called _filtering left_.</span></span>

<span data-ttu-id="02d2e-139">In het volgende voor beeld wordt de para meter **name** van gebruikt `Get-Service` om de resultaten direct te filteren op de Windows Time-service.</span><span class="sxs-lookup"><span data-stu-id="02d2e-139">The following example uses the **Name** parameter of `Get-Service` to immediately filter the results to the Windows Time service only.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="02d2e-140">Het is niet ongebruikelijk om voor beelden te bekijken waarbij de opdracht wordt gebruikt om `Where-Object` de filtering uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="02d2e-140">It's not uncommon to see examples where the command is piped to `Where-Object` to perform the filtering.</span></span>

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

<span data-ttu-id="02d2e-141">Het eerste voor beeld filtert op de bron en retourneert alleen de resultaten voor de Windows Time-service.</span><span class="sxs-lookup"><span data-stu-id="02d2e-141">The first example filters at the source and only returns the results for the Windows Time service.</span></span>
<span data-ttu-id="02d2e-142">In het tweede voor beeld worden alle services geretourneerd, waarna ze naar een andere opdracht worden gesluisd om het filter uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="02d2e-142">The second example returns all the services then pipes them to another command to perform the filtering.</span></span> <span data-ttu-id="02d2e-143">In dit voor beeld lijkt dit mogelijk niet op een grote manier als u een query uitvoert op een lijst met Active Directory gebruikers.</span><span class="sxs-lookup"><span data-stu-id="02d2e-143">While this may not seem like a big deal in this example, imagine if you were querying a list of Active Directory users.</span></span> <span data-ttu-id="02d2e-144">Weet u zeker dat u de informatie voor veel duizenden gebruikers accounts van Active Directory alleen wilt door sluizen naar een andere opdracht die ze naar een kleine subset gefiltert?</span><span class="sxs-lookup"><span data-stu-id="02d2e-144">Do you really want to return the information for many thousands of user accounts from Active Directory only to pipe them to another command that filters them down to a tiny subset?</span></span> <span data-ttu-id="02d2e-145">Mijn aanbeveling is om altijd naar links te filteren, zelfs wanneer het niet van belang is.</span><span class="sxs-lookup"><span data-stu-id="02d2e-145">My recommendation is to always filter left even when it doesn't seem to matter.</span></span> <span data-ttu-id="02d2e-146">U kunt er ook voor zorgen dat u automatisch naar links filtert wanneer dat echt van belang is.</span><span class="sxs-lookup"><span data-stu-id="02d2e-146">You'll be so use to it that you'll automatically filter left when it really does matter.</span></span>

<span data-ttu-id="02d2e-147">Ik heb een gebruiker verteld dat de volg orde waarin u de opdrachten opgeeft, niet van belang is.</span><span class="sxs-lookup"><span data-stu-id="02d2e-147">I once had someone tell me that the order you specify the commands in doesn't matter.</span></span> <span data-ttu-id="02d2e-148">Dat kan niet verder van de waarheid zijn.</span><span class="sxs-lookup"><span data-stu-id="02d2e-148">That couldn't be further from the truth.</span></span> <span data-ttu-id="02d2e-149">De volg orde waarin de opdrachten worden opgegeven, is inderdaad het uitvoeren van filters.</span><span class="sxs-lookup"><span data-stu-id="02d2e-149">The order that the commands are specified in does indeed matter when performing filtering.</span></span> <span data-ttu-id="02d2e-150">Denk bijvoorbeeld aan het scenario waarin u gebruikt `Select-Object` om slechts enkele eigenschappen te selecteren en `Where-Object` te filteren op eigenschappen die niet in de selectie zijn.</span><span class="sxs-lookup"><span data-stu-id="02d2e-150">For example, consider the scenario where you are using `Select-Object` to select only a few properties and `Where-Object` to filter on properties that won't be in the selection.</span></span> <span data-ttu-id="02d2e-151">In dat scenario moet het filter eerst worden uitgevoerd, anders wordt de eigenschap niet in de pijp lijn opgenomen wanneer het filteren probeert uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="02d2e-151">In that scenario, the filtering must occur first, otherwise the property won't exist in the pipeline when try to perform the filtering.</span></span>

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

<span data-ttu-id="02d2e-152">De opdracht in het vorige voor beeld retourneert geen resultaten omdat de eigenschap **CanStopAndContinue** niet bestaat wanneer de resultaten van `Select-Object` worden gepiped naar `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-152">The command in the previous example doesn't return any results because the **CanStopAndContinue** property doesn't exist when the results of `Select-Object` are piped to `Where-Object`.</span></span> <span data-ttu-id="02d2e-153">De betreffende eigenschap is niet geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-153">That particular property wasn't "selected".</span></span> <span data-ttu-id="02d2e-154">In essentie is het uitgefilterd. De volg orde van `Select-Object` en `Where-Object` de gewenste resultaten worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-154">In essence, it was filtered out. Reversing the order of `Select-Object` and `Where-Object` produces the desired results.</span></span>

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a><span data-ttu-id="02d2e-155">De pijp lijn</span><span class="sxs-lookup"><span data-stu-id="02d2e-155">The Pipeline</span></span>

<span data-ttu-id="02d2e-156">Zoals u hebt gezien in veel van de voor beelden die in dit boek tot nu toe zijn weer gegeven, kan de uitvoer van één opdracht vaak worden gebruikt als invoer voor een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="02d2e-156">As you've seen in many of the examples shown so far throughout this book, many times the output of one command can be used as input for another command.</span></span> <span data-ttu-id="02d2e-157">In hoofd stuk 3 `Get-Member` is gebruikt om te bepalen welk type object een opdracht produceert.</span><span class="sxs-lookup"><span data-stu-id="02d2e-157">In Chapter 3, `Get-Member` was used to determine what type of object a command produces.</span></span> <span data-ttu-id="02d2e-158">Hoofd stuk 3 heeft ook geleerd hoe u de para meter **parameter type** van gebruikt `Get-Command` om te bepalen welke opdrachten het type invoer hebben geaccepteerd, maar niet per pijp lijn invoer.</span><span class="sxs-lookup"><span data-stu-id="02d2e-158">Chapter 3 also showed using the **ParameterType** parameter of `Get-Command` to determine what commands accepted that type of input, although not necessarily by pipeline input.</span></span>

<span data-ttu-id="02d2e-159">Afhankelijk van hoe uitgebreide opdrachten in de Help zijn, kan dit een sectie voor **invoer** en **uitvoer** bevatten.</span><span class="sxs-lookup"><span data-stu-id="02d2e-159">Depending on how thorough a commands help is, it may include an **INPUTS** and **OUTPUTS** section.</span></span>

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

<span data-ttu-id="02d2e-160">Alleen de relevante sectie van de Help wordt weer gegeven in de vorige resultaten.</span><span class="sxs-lookup"><span data-stu-id="02d2e-160">Only the relevant section of the help is shown in the previous results.</span></span> <span data-ttu-id="02d2e-161">Zoals u ziet, wordt in de sectie **invoer** aangegeven dat een **ServiceController** of een **teken reeks** object naar de cmdlet kan worden gepiped `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-161">As you can see, the **INPUTS** section states that a **ServiceController** or a **String** object can be piped to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="02d2e-162">U weet niet welke para meters dit type invoer accepteren.</span><span class="sxs-lookup"><span data-stu-id="02d2e-162">It doesn't tell you which parameters accept that type of input.</span></span> <span data-ttu-id="02d2e-163">Een van de eenvoudigste manieren om deze informatie te bepalen, is door de verschillende para meters in de volledige versie van de Help voor de cmdlet te bekijken `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-163">One of the easiest ways to determine that information is to look through the different parameters in the full version of the help for the `Stop-Service` cmdlet.</span></span>

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

<span data-ttu-id="02d2e-164">Daarna hebt u alleen het relevante gedeelte van de Help weer gegeven in de vorige set resultaten.</span><span class="sxs-lookup"><span data-stu-id="02d2e-164">Once again, I've only shown the relevant portion of the help in the previous set of results.</span></span> <span data-ttu-id="02d2e-165">U ziet dat de para meter **DisplayName** geen pijplijn invoer accepteert, de para meter **input object** accepteert invoer **van** de pijp lijn met de waarde voor **ServiceController** -objecten en de para meter **name** accepteert invoer van de pijp lijn **met waarde** voor **teken reeks** objecten.</span><span class="sxs-lookup"><span data-stu-id="02d2e-165">Notice that the **DisplayName** parameter doesn't accept pipeline input, the **InputObject** parameter accepts pipeline input **by value** for **ServiceController** objects, and the **Name** parameter accepts pipeline input **by value** for **string** objects.</span></span> <span data-ttu-id="02d2e-166">Het accepteert ook pijplijn invoer **per eigenschaps naam**.</span><span class="sxs-lookup"><span data-stu-id="02d2e-166">It also accepts pipeline input **by property name**.</span></span>

<span data-ttu-id="02d2e-167">Wanneer een para meter invoer van de pijp lijn accepteert door de naam van de eigenschap en op waarde, wordt altijd eerst de **waarde** geprobeerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-167">When a parameter accepts pipeline input by both property name and by value, it always tries **by value** first.</span></span> <span data-ttu-id="02d2e-168">Als de **waarde** mislukt, wordt geprobeerd de **naam van de eigenschap**.</span><span class="sxs-lookup"><span data-stu-id="02d2e-168">If **by value** fails, then it tries **by property name**.</span></span> <span data-ttu-id="02d2e-169">**Op waarde** is een beetje misleidende.</span><span class="sxs-lookup"><span data-stu-id="02d2e-169">**By value** is a little misleading.</span></span> <span data-ttu-id="02d2e-170">Ik wil het nummer aanroepen **op type**.</span><span class="sxs-lookup"><span data-stu-id="02d2e-170">I prefer to call it **by type**.</span></span> <span data-ttu-id="02d2e-171">Dit betekent dat als u de resultaten van een opdracht die een **ServiceController** -object type produceert `Stop-Service` , de-invoer verbindt met de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="02d2e-171">This means if you pipe the results of a command that produces a **ServiceController** object type to `Stop-Service`, it binds that input to the **InputObject** parameter.</span></span> <span data-ttu-id="02d2e-172">Maar als u de resultaten van een opdracht die **teken reeks** uitvoer produceert, in de pipet `Stop-Service` , wordt deze aan de para meter **name** gebonden.</span><span class="sxs-lookup"><span data-stu-id="02d2e-172">But if you pipe the results of a command that produces **String** output to `Stop-Service`, it binds it to the **Name** parameter.</span></span> <span data-ttu-id="02d2e-173">Als u de resultaten van een opdracht pipet die geen **ServiceController** of **teken reeks** object produceert `Stop-Service` , maar deze uitvoer een eigenschap met de naam **name** produceert, wordt de eigenschap **name** van de uitvoer met de para meter **name** van weer gegeven `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-173">If you pipe the results of a command that doesn't produce a **ServiceController** or **String** object to `Stop-Service`, but it does produce output containing a property called **Name**, then it binds the **Name** property from the output to the **Name** parameter of `Stop-Service`.</span></span>

<span data-ttu-id="02d2e-174">Bepaal welk type uitvoer de `Get-Service` opdracht produceert.</span><span class="sxs-lookup"><span data-stu-id="02d2e-174">Determine what type of output the `Get-Service` command produces.</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

<span data-ttu-id="02d2e-175">`Get-Service` Hiermee wordt een ServiceController-object type gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-175">`Get-Service` produces a ServiceController object type.</span></span>

<span data-ttu-id="02d2e-176">Zoals u eerder in de Help hebt gezien, accepteert de para meter **input object** van `Stop-Service` **ServiceController** -objecten via de pijp lijn **op waarde** (per type).</span><span class="sxs-lookup"><span data-stu-id="02d2e-176">As you previously saw in the help, the **InputObject** parameter of `Stop-Service` accepts **ServiceController** objects via the pipeline **by value** (by type).</span></span> <span data-ttu-id="02d2e-177">Dit betekent dat wanneer de resultaten van de `Get-Service` cmdlet worden gepiped naar `Stop-Service` , ze zijn verbonden met de para meter **input object** van `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-177">This means that when the results of the `Get-Service` cmdlet are piped to `Stop-Service`, they bind to the **InputObject** parameter of `Stop-Service`.</span></span>

```powershell
Get-Service -Name w32time | Stop-Service
```

<span data-ttu-id="02d2e-178">Probeer nu teken reeks invoer.</span><span class="sxs-lookup"><span data-stu-id="02d2e-178">Now to try string input.</span></span> <span data-ttu-id="02d2e-179">Pipe `w32time` om te `Get-Member` bevestigen dat het een teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="02d2e-179">Pipe `w32time` to `Get-Member` just to confirm that it's a string.</span></span>

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

<span data-ttu-id="02d2e-180">Zoals eerder in de Help wordt weer gegeven, kan een teken reeks worden `Stop-Service` gekoppeld aan de **waarde** van de para meter **name** van `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-180">As previously shown in the help, piping a string to `Stop-Service` binds it **by value** to the **Name** parameter of `Stop-Service`.</span></span> <span data-ttu-id="02d2e-181">Test dit door sluizen `w32time` naar `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-181">Test this by piping `w32time` to `Stop-Service`.</span></span>

```powershell
'w32time' | Stop-Service
```

<span data-ttu-id="02d2e-182">In het vorige voor beeld gebruikte ik enkele aanhalings tekens rond de teken reeks `w32time` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-182">Notice that in the previous example, I used single quotes around the string `w32time`.</span></span> <span data-ttu-id="02d2e-183">In Power shell moet u altijd enkele aanhalings tekens gebruiken in plaats van een dubbele aanhalings teken, tenzij de inhoud van de reeks aanhalings tekens een variabele bevat die moet worden uitgevouwen naar de werkelijke waarde.</span><span class="sxs-lookup"><span data-stu-id="02d2e-183">In PowerShell, you should always use single quotes instead of double quotes unless the contents of the quoted string contains a variable that needs to be expanded to its actual value.</span></span> <span data-ttu-id="02d2e-184">Door gebruik te maken van enkele aanhalings tekens is het niet mogelijk om de inhoud binnen de aanhalings tekens te parseren zodat uw code iets sneller wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-184">By using single quotes, PowerShell doesn't have to parse the contents contained within the quotes so your code runs a little faster.</span></span>

<span data-ttu-id="02d2e-185">Maak een aangepast object om de invoer van de pijp lijn te testen op naam van eigenschap voor de para meter **name** van `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-185">Create a custom object to test pipeline input by property name for the **Name** parameter of `Stop-Service`.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
 Name = 'w32time'
 }
```

<span data-ttu-id="02d2e-186">De inhoud van de variabele **CustomObject** is een object type **PSCustomObject** en bevat een eigenschap met de naam **naam**.</span><span class="sxs-lookup"><span data-stu-id="02d2e-186">The contents of the **CustomObject** variable is a **PSCustomObject** object type and it contains a property named **Name**.</span></span>

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

<span data-ttu-id="02d2e-187">Als u de variabele wilt omgeven `$CustomObject` door aanhalings tekens, wilt u dubbele aanhalings tekens gebruiken.</span><span class="sxs-lookup"><span data-stu-id="02d2e-187">If you were to surround the `$CustomObject` variable with quotes, you want to use double quotes.</span></span>
<span data-ttu-id="02d2e-188">Anders wordt met enkele aanhalings tekens de letterlijke teken reeks in `$CustomObject` `Get-Member` plaats van de waarde die is opgenomen door de variabele.</span><span class="sxs-lookup"><span data-stu-id="02d2e-188">Otherwise, using single quotes, the literal string `$CustomObject` is piped to `Get-Member` instead of the value contained by the variable.</span></span>

<span data-ttu-id="02d2e-189">Hoewel de inhoud van de `$CustomObject` `Stop-Service` cmdlet wordt gekoppeld aan de para meter **name** , wordt deze keer door de **naam** van de eigenschap gebonden, in plaats van **met waarde** , omdat de inhoud van `$CustomObject` een object is dat een eigenschap met de naam **name** heeft.</span><span class="sxs-lookup"><span data-stu-id="02d2e-189">Although piping the contents of `$CustomObject` to `Stop-Service` cmdlet binds to the **Name** parameter, this time it binds **by property name** instead of **by value** because the contents of `$CustomObject` is an object that has a property named **Name**.</span></span>

<span data-ttu-id="02d2e-190">In dit voor beeld maakt u een ander aangepast object met behulp van een andere eigenschaps naam, zoals de **service**.</span><span class="sxs-lookup"><span data-stu-id="02d2e-190">In this example, I create another custom object using a different property name, such as **Service**.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

<span data-ttu-id="02d2e-191">Er wordt een fout gegenereerd bij het `$CustomObject` maken van een pipe naar `Stop-Service` , omdat deze geen **ServiceController** of **teken reeks** object produceert en geen eigenschap met de naam **name** heeft.</span><span class="sxs-lookup"><span data-stu-id="02d2e-191">An error is generated when trying to pipe `$CustomObject` to `Stop-Service` because it doesn't produce a **ServiceController** or **String** object, and it doesn't have a property named **Name**.</span></span>

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

<span data-ttu-id="02d2e-192">Als de uitvoer van één opdracht niet wordt uitgelijnd met de invoer opties voor de pijp lijn voor een andere opdracht, `Select-Object` kan worden gebruikt om de naam van de eigenschap te wijzigen zodat de eigenschappen correct worden genoteerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-192">If the output of one command doesn't line up with the pipeline input options for another command, `Select-Object` can be used to rename the property so that the properties lineup correctly.</span></span>

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

<span data-ttu-id="02d2e-193">In dit voor beeld `Select-Object` is gebruikt om de naam van de **service** -eigenschap te wijzigen in een eigenschap met de naam **name**.</span><span class="sxs-lookup"><span data-stu-id="02d2e-193">In this example, `Select-Object` was used to rename the **Service** property to a property named **Name**.</span></span>

<span data-ttu-id="02d2e-194">De syntaxis van dit voor beeld lijkt eerst iets ingewikkeld.</span><span class="sxs-lookup"><span data-stu-id="02d2e-194">The syntax this example may seem a little complicated at first.</span></span> <span data-ttu-id="02d2e-195">Wat ik heb geleerd, is dat u de syntaxis nooit leert door code te kopiëren en te plakken.</span><span class="sxs-lookup"><span data-stu-id="02d2e-195">What I have learned is that you'll never learn the syntax by copy and pasting code.</span></span> <span data-ttu-id="02d2e-196">Neem de tijd om de code in te typen.</span><span class="sxs-lookup"><span data-stu-id="02d2e-196">Take the time to type the code in.</span></span> <span data-ttu-id="02d2e-197">Na een paar keer wordt het tweede karakter.</span><span class="sxs-lookup"><span data-stu-id="02d2e-197">After a few times, it becomes second nature.</span></span> <span data-ttu-id="02d2e-198">Het gebruik van meerdere monitors is een enorm voor deel omdat u de voorbeeld code op één scherm kunt weer geven en deze op een andere op een andere pagina typt.</span><span class="sxs-lookup"><span data-stu-id="02d2e-198">Having multiple monitors is a huge benefit because you can display the example code on one screen and type it in on another one.</span></span>

<span data-ttu-id="02d2e-199">Soms wilt u een para meter gebruiken waarvoor geen pijplijn invoer wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-199">Occasionally, you may want to use a parameter that doesn't accept pipeline input.</span></span> <span data-ttu-id="02d2e-200">In het volgende voor beeld ziet u de uitvoer van een opdracht als invoer voor een andere.</span><span class="sxs-lookup"><span data-stu-id="02d2e-200">The following example demonstrates using the output of one command as input for another.</span></span> <span data-ttu-id="02d2e-201">Sla de weergave naam voor een aantal Windows-services eerst op in een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="02d2e-201">First save the display name for a couple of Windows services into a text file.</span></span>

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

<span data-ttu-id="02d2e-202">U kunt de opdracht uitvoeren die de benodigde uitvoer tussen haakjes levert als de waarde voor de para meter van de opdracht die de invoer vereist.</span><span class="sxs-lookup"><span data-stu-id="02d2e-202">You can run the command that provides the needed output within parentheses as the value for the parameter of the command requiring the input.</span></span>

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

<span data-ttu-id="02d2e-203">Dit is net als de volg orde van de bewerkingen in algebra voor degene die weet hoe het werkt.</span><span class="sxs-lookup"><span data-stu-id="02d2e-203">This is just like order of operations in Algebra for those of you who remember how it works.</span></span> <span data-ttu-id="02d2e-204">De opdracht tussen haakjes wordt altijd uitgevoerd vóór het buitenste gedeelte van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="02d2e-204">The command within parentheses always runs prior to the outer portion of the command.</span></span>

## <a name="powershellget"></a><span data-ttu-id="02d2e-205">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="02d2e-205">PowerShellGet</span></span>

<span data-ttu-id="02d2e-206">PowerShellGet is een Power shell-module met opdrachten voor het detecteren, installeren, publiceren en bijwerken van Power shell-modules (en andere artefacten) van of naar een NuGet-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="02d2e-206">PowerShellGet is a PowerShell module that contains commands for discovering, installing, publishing, and updating PowerShell modules (and other artifacts) to or from a NuGet repository.</span></span> <span data-ttu-id="02d2e-207">PowerShellGet wordt geleverd met Power shell versie 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="02d2e-207">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="02d2e-208">Het is beschikbaar als afzonderlijke down load voor Power shell versie 3,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="02d2e-208">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="02d2e-209">Micro soft host een online NuGet-opslag plaats met de naam [PowerShell Gallery][].</span><span class="sxs-lookup"><span data-stu-id="02d2e-209">Microsoft hosts an online NuGet repository called the [PowerShell Gallery][].</span></span> <span data-ttu-id="02d2e-210">Hoewel deze opslag plaats wordt gehost door micro soft, wordt het meren deel van de modules in de opslag plaats niet door micro soft geschreven.</span><span class="sxs-lookup"><span data-stu-id="02d2e-210">Although this repository is hosted by Microsoft, the majority of the modules contained within the repository aren't written by Microsoft.</span></span> <span data-ttu-id="02d2e-211">Code verkrijgen van de PowerShell Gallery moet grondig worden geëvalueerd in een geïsoleerde test omgeving voordat ze geschikt zijn voor gebruik in een productie omgeving.</span><span class="sxs-lookup"><span data-stu-id="02d2e-211">Any code obtain from the PowerShell Gallery should be thoroughly reviewed in an isolated test environment before being considered suitable for use in a production environment.</span></span>

<span data-ttu-id="02d2e-212">De meeste bedrijven willen hun eigen interne persoonlijke NuGet-opslag plaats hosten, waar ze hun intern gebruik alleen modules kunnen plaatsen, evenals modules die ze hebben gedownload van andere bronnen zodra ze ze als niet-schadelijk hebben gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-212">Most companies will want to host their own internal private NuGet repository where they can post their internal use only modules as well as modules that they've downloaded from other sources once they've validated them as being non-malicious.</span></span>

<span data-ttu-id="02d2e-213">Gebruik de `Find-Module` cmdlet die deel uitmaakt van de PowerShellGet-module om een module te vinden in de PowerShell Gallery die ik heb geschreven met de naam MrToolkit.</span><span class="sxs-lookup"><span data-stu-id="02d2e-213">Use the `Find-Module` cmdlet that's part of the PowerShellGet module to find a module in the PowerShell Gallery that I wrote named MrToolkit.</span></span>

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

<span data-ttu-id="02d2e-214">De eerste keer dat u een van de opdrachten uit de PowerShellGet-module gebruikt, wordt u gevraagd om de NuGet-provider te installeren.</span><span class="sxs-lookup"><span data-stu-id="02d2e-214">The first time you use one of the commands from the PowerShellGet module, you'll be prompted to install the NuGet provider.</span></span>

<span data-ttu-id="02d2e-215">Als u de MrToolkit-module wilt installeren, pipet u de vorige opdracht naar `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-215">To install the MrToolkit module, pipe the previous command to `Install-Module`.</span></span>

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

<span data-ttu-id="02d2e-216">Omdat de PowerShell Gallery een niet-vertrouwde opslag plaats is, wordt u gevraagd om de installatie van de module goed te keuren.</span><span class="sxs-lookup"><span data-stu-id="02d2e-216">Since the PowerShell Gallery is an untrusted repository, it prompts you to approve the installation of the module.</span></span>

## <a name="finding-pipeline-input-the-easy-way"></a><span data-ttu-id="02d2e-217">Pijp lijn invoer op eenvoudige wijze zoeken</span><span class="sxs-lookup"><span data-stu-id="02d2e-217">Finding pipeline input the easy way</span></span>

<span data-ttu-id="02d2e-218">De MrToolkit-module bevat een functie met de naam `Get-MrPipelineInput` .</span><span class="sxs-lookup"><span data-stu-id="02d2e-218">The MrToolkit module contains a function named `Get-MrPipelineInput`.</span></span> <span data-ttu-id="02d2e-219">Met deze cmdlet kunt u eenvoudig bepalen welke para meters van een opdracht pijplijn invoer accepteren, welk type object ze accepteren en of ze de invoer van de pijp lijn **op waarde** of **eigenschaps naam** accepteren.</span><span class="sxs-lookup"><span data-stu-id="02d2e-219">This cmdlet can be used to easily determine which parameters of a command accept pipeline input, what type of object they accept, and if they accept pipeline input **by value** or **by property name**.</span></span>

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

<span data-ttu-id="02d2e-220">Zoals u kunt zien, kunnen dezelfde gegevens die we eerder hebben bepaald door de Help-informatie, gemakkelijk worden bepaald met deze functie.</span><span class="sxs-lookup"><span data-stu-id="02d2e-220">As you can see, the same information we previously determined by sifting through the help can easily be determined with this function.</span></span>

## <a name="summary"></a><span data-ttu-id="02d2e-221">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="02d2e-221">Summary</span></span>

<span data-ttu-id="02d2e-222">In dit hoofd stuk hebt u meer informatie over Power shell-One-Lines geleerd.</span><span class="sxs-lookup"><span data-stu-id="02d2e-222">In this chapter, you've learned about PowerShell one-liners.</span></span> <span data-ttu-id="02d2e-223">U hebt geleerd dat het aantal fysieke regels waarop een opdracht zich bevindt, niets hoeft te doen, ongeacht of het een Power shell-regel is.</span><span class="sxs-lookup"><span data-stu-id="02d2e-223">You've learned that the number of physical lines that a command is on has nothing to do with whether or not it's a PowerShell one-liner.</span></span> <span data-ttu-id="02d2e-224">U hebt ook geleerd over filteren links, de pijp lijn en PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="02d2e-224">You've also learned about filtering left, the pipeline, and PowerShellGet.</span></span>

## <a name="review"></a><span data-ttu-id="02d2e-225">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="02d2e-225">Review</span></span>

1. <span data-ttu-id="02d2e-226">Wat is een Power shell One-line?</span><span class="sxs-lookup"><span data-stu-id="02d2e-226">What is a PowerShell one-liner?</span></span>
1. <span data-ttu-id="02d2e-227">Wat zijn de tekens waar natuurlijke lijn onderbrekingen kunnen voor komen in Power shell?</span><span class="sxs-lookup"><span data-stu-id="02d2e-227">What are some of the characters where natural line breaks can occur in PowerShell?</span></span>
1. <span data-ttu-id="02d2e-228">Waarom moet u het filter verlaten?</span><span class="sxs-lookup"><span data-stu-id="02d2e-228">Why should you filter left?</span></span>
1. <span data-ttu-id="02d2e-229">Wat zijn de twee manieren waarop een Power shell-opdracht pijplijn invoer kan accepteren?</span><span class="sxs-lookup"><span data-stu-id="02d2e-229">What are the two ways that a PowerShell command can accept pipeline input?</span></span>
1. <span data-ttu-id="02d2e-230">Waarom moet u de opdrachten in de PowerShell Gallery niet vertrouwen?</span><span class="sxs-lookup"><span data-stu-id="02d2e-230">Why shouldn't you trust commands found in the PowerShell Gallery?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="02d2e-231">Aanbevolen documentatie</span><span class="sxs-lookup"><span data-stu-id="02d2e-231">Recommended Reading</span></span>

- <span data-ttu-id="02d2e-232">[about_Pipelines][]</span><span class="sxs-lookup"><span data-stu-id="02d2e-232">[about_Pipelines][]</span></span>
- <span data-ttu-id="02d2e-233">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="02d2e-233">[about_Command_Syntax][]</span></span>
- <span data-ttu-id="02d2e-234">[about_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="02d2e-234">[about_Parameters][]</span></span>
- <span data-ttu-id="02d2e-235">[PowerShellGet: de grote eenvoudige manier om Power shell-modules te detecteren, te installeren en bij te werken][psget]</span><span class="sxs-lookup"><span data-stu-id="02d2e-235">[PowerShellGet: The BIG EASY way to discover, install, and update PowerShell modules][psget]</span></span>

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell Gallery]: https://www.powershellgallery.com/
