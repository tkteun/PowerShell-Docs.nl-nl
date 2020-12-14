---
description: Hierin worden Power shell-sessies (PSSessions) beschreven en wordt uitgelegd hoe u een permanente verbinding met een externe computer tot stand brengt.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: edc7109f3f79376ac1d348d3c3cd65e3a8d3e69c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705356"
---
# <a name="about-pssessions"></a><span data-ttu-id="3a5a1-103">Over PSSessions</span><span class="sxs-lookup"><span data-stu-id="3a5a1-103">About PSSessions</span></span>

## <a name="short-description"></a><span data-ttu-id="3a5a1-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="3a5a1-104">Short Description</span></span>
<span data-ttu-id="3a5a1-105">Hierin worden Power shell-sessies (PSSessions) beschreven en wordt uitgelegd hoe u een permanente verbinding met een externe computer tot stand brengt.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-105">Describes PowerShell sessions (PSSessions) and explains how to establish a persistent connection to a remote computer.</span></span>

## <a name="long-description"></a><span data-ttu-id="3a5a1-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="3a5a1-106">Long Description</span></span>

<span data-ttu-id="3a5a1-107">Als u Power shell-opdrachten wilt uitvoeren op een externe computer, kunt u de para meter **ComputerName** van een cmdlet gebruiken, of u kunt een Power shell-sessie (PSSession) maken en opdrachten uitvoeren in de PSSession.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-107">To run PowerShell commands on a remote computer, you can use the **ComputerName** parameter of a cmdlet, or you can create a PowerShell session (PSSession) and run commands in the PSSession.</span></span>

<span data-ttu-id="3a5a1-108">Wanneer u een PSSession maakt, brengt Power shell een permanente verbinding met de externe computer tot stand.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-108">When you create a PSSession, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="3a5a1-109">Gebruik een PSSession om een reeks gerelateerde opdrachten uit te voeren op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-109">Use a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="3a5a1-110">Opdrachten die worden uitgevoerd in dezelfde PSSession kunnen gegevens delen, zoals de waarden van variabelen, aliassen en functies.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-110">Commands that run in the same PSSession can share data, such as the values of variables, aliases, and functions.</span></span>

<span data-ttu-id="3a5a1-111">U kunt ook een PSSession maken op de lokale computer en daar opdrachten op uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-111">You can also create a PSSession on the local computer and run commands in it.</span></span>
<span data-ttu-id="3a5a1-112">Een lokale PSSession maakt gebruik van de externe infra structuur van Power shell om de PSSession te maken en te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-112">A local PSSession uses the PowerShell remoting infrastructure to create and maintain the PSSession.</span></span>

<span data-ttu-id="3a5a1-113">Vanaf Windows Power Shell 3,0 zijn PSSessions onafhankelijk van de sessies waarin ze zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-113">Beginning in Windows PowerShell 3.0, PSSessions are independent of the sessions in which they are created.</span></span> <span data-ttu-id="3a5a1-114">Actieve PSSessions worden onderhouden op de externe computer (of de computer aan het externe einde of aan de server zijde van de verbinding).</span><span class="sxs-lookup"><span data-stu-id="3a5a1-114">Active PSSessions are maintained on the remote computer (or the computer at the remote end or "server-side" of the connection).</span></span> <span data-ttu-id="3a5a1-115">Als gevolg hiervan kunt u de verbinding met de PSSession verbreken en op een later tijdstip opnieuw verbinding maken vanaf dezelfde computer of vanaf een andere computer.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-115">As a result, you can disconnect from the PSSession and reconnect to it at a later time from the same computer or from a different computer.</span></span>

<span data-ttu-id="3a5a1-116">In dit onderwerp wordt uitgelegd hoe u PSSessions kunt maken, gebruiken, ophalen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-116">This topic explains how to create, use, get, and delete PSSessions.</span></span> <span data-ttu-id="3a5a1-117">Zie [about_PSSession_Details](about_PSSession_Details.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-117">For more advanced information, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

<span data-ttu-id="3a5a1-118">Opmerking: PSSessions de externe infra structuur van Power shell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-118">Note: PSSessions use the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="3a5a1-119">Als u PSSessions wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-119">To use PSSessions, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="3a5a1-120">Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-120">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

<span data-ttu-id="3a5a1-121">In Windows Vista en latere versies van Windows moet u Power shell starten met de optie als administrator uitvoeren om een PSSession te maken op een lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-121">In Windows Vista and later versions of Windows, to create a PSSession on a local computer, you must start PowerShell with the "Run as administrator" option.</span></span>

## <a name="what-is-a-session"></a><span data-ttu-id="3a5a1-122">Wat is een sessie?</span><span class="sxs-lookup"><span data-stu-id="3a5a1-122">What Is a Session?</span></span>

<span data-ttu-id="3a5a1-123">Een sessie is een omgeving waarin Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-123">A session is an environment in which PowerShell runs.</span></span>

<span data-ttu-id="3a5a1-124">Telkens wanneer u Power shell start, wordt er een sessie voor u gemaakt en kunt u opdrachten uitvoeren in de sessie.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-124">Each time you start PowerShell, a session is created for you, and you can run commands in the session.</span></span> <span data-ttu-id="3a5a1-125">U kunt ook items toevoegen aan uw sessie, zoals modules en modules, en u kunt items maken, zoals variabelen, functies en aliassen.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-125">You can also add items to your session, such as modules and snap-ins, and you can create items, such as variables, functions, and aliases.</span></span> <span data-ttu-id="3a5a1-126">Deze items bestaan alleen in de sessie en worden verwijderd wanneer de sessie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-126">These items exist only in the session and are deleted when the session ends.</span></span>

<span data-ttu-id="3a5a1-127">U kunt ook door gebruikers beheerde sessies (Power shell-sessies) of PSSessions, op de lokale computer of op een externe computer maken.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-127">You can also create user-managed sessions, known as " PowerShell sessions" or "PSSessions," on the local computer or on a remote computer.</span></span> <span data-ttu-id="3a5a1-128">Net als bij de standaard sessie kunt u opdrachten uitvoeren in een PSSession en items toevoegen en maken.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-128">Like the default session, you can run commands in a PSSession and add and create items.</span></span> <span data-ttu-id="3a5a1-129">Maar in tegens telling tot de sessie die automatisch wordt gestart, kunt u de PSSessions die u maakt, beheren.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-129">However, unlike the session that starts automatically, you can control the PSSessions that you create.</span></span> <span data-ttu-id="3a5a1-130">U kunt ze ophalen, maken, configureren en verwijderen, de verbinding verbreken en opnieuw verbinding maken en meerdere opdrachten uitvoeren in dezelfde PSSession.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-130">You can get, create, configure, and remove them, disconnect and reconnect to them, and run multiple commands in the same PSSession.</span></span> <span data-ttu-id="3a5a1-131">De PSSession blijft beschikbaar totdat u deze verwijdert of als er een time-out optreedt.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-131">The PSSession remains available until you delete it or it times out.</span></span>

<span data-ttu-id="3a5a1-132">Normaal gesp roken maakt u een PSSession om een reeks gerelateerde opdrachten uit te voeren op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-132">Typically, you create a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="3a5a1-133">Wanneer u een PSSession op een externe computer maakt, brengt Power shell een permanente verbinding met de externe computer tot stand om de sessie te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-133">When you create a PSSession on a remote computer, PowerShell establishes a persistent connection to the remote computer to support the session.</span></span>

<span data-ttu-id="3a5a1-134">Als u de para meter **ComputerName** van de- `Invoke-Command` cmdlet gebruikt `Enter-PSSession` om een externe opdracht uit te voeren of een interactieve sessie te starten, maakt Power shell een tijdelijke sessie op de externe computer en wordt de sessie gesloten zodra de opdracht is voltooid of zodra de interactieve sessie is beëindigd.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-134">If you use the **ComputerName** parameter of the `Invoke-Command` or `Enter-PSSession` cmdlet to run a remote command or to start an interactive session, PowerShell creates a temporary session on the remote computer and closes the session as soon as the command is complete or as soon as the interactive session ends.</span></span> <span data-ttu-id="3a5a1-135">U kunt deze tijdelijke sessies niet beheren en u kunt deze niet gebruiken voor meer dan één opdracht of één interactieve sessie.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-135">You cannot control these temporary sessions, and you cannot use them for more than a single command or a single interactive session.</span></span>

<span data-ttu-id="3a5a1-136">In Power shell is de ' huidige sessie ' de sessie waarin u werkt.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-136">In PowerShell, the "current session" is the session that you are working in.</span></span> <span data-ttu-id="3a5a1-137">De ' huidige sessie ' kan verwijzen naar een wille keurige sessie, met inbegrip van een tijdelijke sessie of een PSSession.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-137">The "current session" can refer to any session, including a temporary session or a PSSession.</span></span>

## <a name="why-use-a-pssession"></a><span data-ttu-id="3a5a1-138">Waarom een PSSession gebruiken?</span><span class="sxs-lookup"><span data-stu-id="3a5a1-138">Why Use a PSSession?</span></span>

<span data-ttu-id="3a5a1-139">Gebruik een PSSession wanneer u een permanente verbinding met een externe computer nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-139">Use a PSSession when you need a persistent connection to a remote computer.</span></span>
<span data-ttu-id="3a5a1-140">Met een PSSession kunt u een reeks opdrachten uitvoeren die gegevens delen, zoals de waarde van variabelen, de inhoud van een functie of de definitie van een alias.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-140">With a PSSession, you can run a series of commands that share data, such as the value of variables, the contents of a function, or the definition of an alias.</span></span>

<span data-ttu-id="3a5a1-141">U kunt externe opdrachten uitvoeren zonder een PSSession te maken.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-141">You can run remote commands without creating a PSSession.</span></span> <span data-ttu-id="3a5a1-142">Gebruik de para meter **ComputerName** van cmdlets voor externe ondersteuning om één opdracht uit te voeren of een reeks niet-gerelateerde opdrachten op een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-142">Use the **ComputerName** parameter of remote-enabled cmdlets to run a single command or a series of unrelated commands on one or many computers.</span></span>

<span data-ttu-id="3a5a1-143">Wanneer u de para meter **ComputerName** van `Invoke-Command` of gebruikt `Enter-PSSession` , brengt Power shell een tijdelijke verbinding met de externe computer tot stand en wordt vervolgens de verbinding gesloten zodra de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-143">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, PowerShell establishes a temporary connection to the remote computer and then closes the connection as soon as the command is complete.</span></span> <span data-ttu-id="3a5a1-144">Alle gegevens elementen die u maakt, gaan verloren wanneer de verbinding wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-144">Any data elements that you create are lost when the connection is closed.</span></span>

<span data-ttu-id="3a5a1-145">Andere cmdlets die de para meter **ComputerName** hebben, zoals `Get-Eventlog` en `Get-WmiObject` , gebruiken verschillende externe technologieën om gegevens te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-145">Other cmdlets that have a **ComputerName** parameter, such as `Get-Eventlog` and `Get-WmiObject`, use different remoting technologies to gather data.</span></span> <span data-ttu-id="3a5a1-146">Geen permanente verbinding maken, zoals een PSSession.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-146">None create a persistent connection like a PSSession.</span></span>

## <a name="how-to-create-a-pssession"></a><span data-ttu-id="3a5a1-147">Een PSSession maken</span><span class="sxs-lookup"><span data-stu-id="3a5a1-147">How to Create a PSSession</span></span>

<span data-ttu-id="3a5a1-148">Gebruik de cmdlet om een PSSession te maken `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="3a5a1-148">To create a PSSession, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="3a5a1-149">Als u de PSSession op een externe computer wilt maken, gebruikt u de para meter **ComputerName** van de `New-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-149">To create the PSSession on a remote computer, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="3a5a1-150">Met de volgende opdracht maakt u bijvoorbeeld een nieuwe PSSession op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-150">For example, the following command creates a new PSSession on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

<span data-ttu-id="3a5a1-151">Wanneer u de opdracht verzendt, `New-PSSession` wordt de PSSession gemaakt en wordt een object geretourneerd dat staat voor de PSSession.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-151">When you submit the command, `New-PSSession` creates the PSSession and returns an object that represents the PSSession.</span></span> <span data-ttu-id="3a5a1-152">U kunt het object opslaan in een variabele wanneer u de PSSession maakt, maar u kunt ook een `Get-PSSession` opdracht gebruiken om de PSSession op een later tijdstip op te halen.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-152">You can save the object in a variable when you create the PSSession, or you can use a `Get-PSSession` command to get the PSSession at a later time.</span></span>

<span data-ttu-id="3a5a1-153">Met de volgende opdracht maakt u bijvoorbeeld een nieuwe PSSession op de Server01-computer en slaat het resulterende object op in de variabele $ps.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-153">For example, the following command creates a new PSSession on the Server01 computer and saves the resulting object in the $ps variable.</span></span>

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a><span data-ttu-id="3a5a1-154">PSSessions maken op meerdere computers</span><span class="sxs-lookup"><span data-stu-id="3a5a1-154">How to Create PSSessions on Multiple Computers</span></span>

<span data-ttu-id="3a5a1-155">Als u PSSessions op meerdere computers wilt maken, gebruikt u de para meter **ComputerName** van de `New-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-155">To create PSSessions on multiple computers, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="3a5a1-156">Typ de namen van de externe computers in een lijst met door komma's gescheiden waarden.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-156">Type the names of the remote computers in a comma-separated list.</span></span>

<span data-ttu-id="3a5a1-157">Als u bijvoorbeeld PSSessions wilt maken op de Server01-, Server02-en Server03-computers, typt u:</span><span class="sxs-lookup"><span data-stu-id="3a5a1-157">For example, to create PSSessions on the Server01, Server02, and Server03 computers, type:</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="3a5a1-158">`New-PSSession` Hiermee maakt u één PSSession op elke externe computer.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-158">`New-PSSession` creates one PSSession on each of the remote computers.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="3a5a1-159">PSSessions ophalen</span><span class="sxs-lookup"><span data-stu-id="3a5a1-159">How to Get PSSessions</span></span>

<span data-ttu-id="3a5a1-160">Als u de PSSessions wilt ophalen die in uw huidige sessie zijn gemaakt, gebruikt u de `Get-PSSession` cmdlet zonder de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="3a5a1-160">To get the PSSessions that were created in your current session, use the `Get-PSSession` cmdlet without the **ComputerName** parameter.</span></span> <span data-ttu-id="3a5a1-161">`Get-PSSession` retourneert hetzelfde type object dat `New-PSSession` retourneert.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-161">`Get-PSSession` returns the same type of object that `New-PSSession` returns.</span></span>

<span data-ttu-id="3a5a1-162">Met de volgende opdracht worden alle PSSessions opgehaald die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-162">The following command gets all the PSSessions that were created in the current session.</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="3a5a1-163">De standaard weergave van de PSSessions toont de ID en een standaard weergave naam.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-163">The default display of the PSSessions shows their ID and a default display name.</span></span> <span data-ttu-id="3a5a1-164">Wanneer u de sessie maakt, kunt u een alternatieve weergave naam toewijzen.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-164">You can assign an alternate display name when you create the session.</span></span>

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

<span data-ttu-id="3a5a1-165">U kunt de PSSessions ook opslaan in een variabele.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-165">You can also save the PSSessions in a variable.</span></span> <span data-ttu-id="3a5a1-166">Met de volgende opdracht wordt de PSSessions opgehaald en opgeslagen in de \$ variabele ps123.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-166">The following command gets the PSSessions and saves them in the \$ps123 variable.</span></span>

```powershell
$ps123 = Get-PSSession
```

<span data-ttu-id="3a5a1-167">Wanneer u de PSSession-cmdlets gebruikt, kunt u naar een PSSession verwijzen met de bijbehorende ID, met de naam of met de ID van het exemplaar (een GUID).</span><span class="sxs-lookup"><span data-stu-id="3a5a1-167">When using the PSSession cmdlets, you can refer to a PSSession by its ID, by its name, or by its instance ID (a GUID).</span></span> <span data-ttu-id="3a5a1-168">Met de volgende opdracht wordt een PSSession op basis van de ID opgehaald en opgeslagen in de \$ variabele PS01.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-168">The following command gets a PSSession by its ID and saves it in the \$ps01 variable.</span></span>

```powershell
$ps01 = Get-PSSession -Id 1
```

<span data-ttu-id="3a5a1-169">Vanaf Windows Power Shell 3,0 worden PSSessions onderhouden op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-169">Beginning in Windows PowerShell 3.0, PSSessions are maintained on the remote computer.</span></span> <span data-ttu-id="3a5a1-170">Gebruik de para meter **ComputerName** van de cmdlet om PSSessions op te halen die u op bepaalde externe computers hebt gemaakt `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="3a5a1-170">To get PSSessions that you created on particular remote computers, use the **ComputerName** parameter of the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="3a5a1-171">Met de volgende opdracht wordt de PSSessions opgehaald die u hebt gemaakt op de externe computer met Server01.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-171">The following command gets the PSSessions that you created on the Server01 remote computer.</span></span> <span data-ttu-id="3a5a1-172">Dit omvat PSSessions die zijn gemaakt in de huidige sessie en in andere sessies op de lokale computer of op andere computers.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-172">This includes PSSessions created in the current session and in other sessions on the local computer or other computers.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

<span data-ttu-id="3a5a1-173">In Windows Power Shell 2,0 worden `Get-PSSession` alleen de PSSessions opgehaald die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-173">In Windows PowerShell 2.0, `Get-PSSession` gets only the PSSessions that were created in the current session.</span></span> <span data-ttu-id="3a5a1-174">Er worden geen PSSessions opgehaald die zijn gemaakt in andere sessies of op andere computers, zelfs als de sessies zijn verbonden met en opdrachten op de lokale computer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-174">It does not get PSSessions that were created in other sessions or on other computers, even if the sessions are connected to and are running commands on the local computer.</span></span>

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="3a5a1-175">Opdrachten uitvoeren in een PSSession</span><span class="sxs-lookup"><span data-stu-id="3a5a1-175">How to Run Commands in a PSSession</span></span>

<span data-ttu-id="3a5a1-176">Als u een opdracht wilt uitvoeren in een of meer PSSessions, gebruikt u de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-176">To run a command in one or more PSSessions, use the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="3a5a1-177">Gebruik de para meter Session om de PSSessions en de para meter **script Block** op te geven om de opdracht op te geven.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-177">Use the Session parameter to specify the PSSessions and the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="3a5a1-178">Als u bijvoorbeeld een `Get-ChildItem` opdracht ' dir ' wilt uitvoeren in elk van de drie PSSessions die zijn opgeslagen in de variabele $ps 123, typt u:</span><span class="sxs-lookup"><span data-stu-id="3a5a1-178">For example, to run a `Get-ChildItem` ("dir") command in each of the three PSSessions saved in the $ps123 variable, type:</span></span>

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a><span data-ttu-id="3a5a1-179">PSSessions verwijderen</span><span class="sxs-lookup"><span data-stu-id="3a5a1-179">How to Delete PSSessions</span></span>

<span data-ttu-id="3a5a1-180">Wanneer u klaar bent met de PSSession, gebruikt u de `Remove-PSSession` cmdlet om de PSSession te verwijderen en om de resources vrij te geven die het gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-180">When you are finished with the PSSession, use the `Remove-PSSession` cmdlet to delete the PSSession and to release the resources that it was using.</span></span>

```powershell
Remove-PSSession -Session $ps
```

<span data-ttu-id="3a5a1-181">of</span><span class="sxs-lookup"><span data-stu-id="3a5a1-181">or</span></span>

```powershell
Remove-PSSession -Id 1
```

<span data-ttu-id="3a5a1-182">Als u een PSSession van een externe computer wilt verwijderen, gebruikt u de para meter **ComputerName** van de `Remove-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-182">To remove a PSSession from a remote computer, use the **ComputerName** parameter of the `Remove-PSSession` cmdlet.</span></span>

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

<span data-ttu-id="3a5a1-183">Als u de PSSession niet verwijdert, blijft de PSSession beschikbaar voor gebruik totdat er een time-out optreedt.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-183">If you do not delete the PSSession, the PSSession remains available for use until it times out.</span></span>

<span data-ttu-id="3a5a1-184">U kunt ook de para meter **IdleTimeout** van de `New-PSSessionOption` cmdlet gebruiken om een verval tijd in te stellen voor een niet-actieve PSSession.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-184">You can also use the **IdleTimeout** parameter of the `New-PSSessionOption` cmdlet to set an expiration time for an idle PSSession.</span></span> <span data-ttu-id="3a5a1-185">Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-185">For more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="the-pssession-cmdlets"></a><span data-ttu-id="3a5a1-186">De PSSession-cmdlets</span><span class="sxs-lookup"><span data-stu-id="3a5a1-186">The PSSession Cmdlets</span></span>

<span data-ttu-id="3a5a1-187">Voor een lijst met PSSession-cmdlets typt u:</span><span class="sxs-lookup"><span data-stu-id="3a5a1-187">For a list of PSSession cmdlets, type:</span></span>

```powershell
Get-Help *-PSSession
```

- <span data-ttu-id="3a5a1-188">Connect-PSSession: verbindt een PSSession met de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="3a5a1-188">Connect-PSSession: Connects a PSSession to the current session</span></span>
- <span data-ttu-id="3a5a1-189">Disconnect-PSSession: de verbinding van een PSSession met de huidige sessie wordt verbroken</span><span class="sxs-lookup"><span data-stu-id="3a5a1-189">Disconnect-PSSession: Disconnects a PSSession from the current session</span></span>
- <span data-ttu-id="3a5a1-190">Enter-PSSession: start een interactieve sessie</span><span class="sxs-lookup"><span data-stu-id="3a5a1-190">Enter-PSSession: Starts an interactive session</span></span>
- <span data-ttu-id="3a5a1-191">Afsluiten-PSSession: Hiermee wordt een interactieve sessie beëindigd</span><span class="sxs-lookup"><span data-stu-id="3a5a1-191">Exit-PSSession: Ends an interactive session</span></span>
- <span data-ttu-id="3a5a1-192">Get-PSSession: Hiermee wordt de PSSessions in de huidige sessie opgehaald</span><span class="sxs-lookup"><span data-stu-id="3a5a1-192">Get-PSSession: Gets the PSSessions in the current session</span></span>
- <span data-ttu-id="3a5a1-193">New-PSSession: maakt een nieuwe PSSession op een lokale of externe computer</span><span class="sxs-lookup"><span data-stu-id="3a5a1-193">New-PSSession: Creates a new PSSession on a local or remote computer</span></span>
- <span data-ttu-id="3a5a1-194">Receive-PSSession: Hiermee worden de resultaten opgehaald van opdrachten die zijn uitgevoerd in een verbroken sessie</span><span class="sxs-lookup"><span data-stu-id="3a5a1-194">Receive-PSSession: Gets the results of commands that ran in a disconnected session</span></span>
- <span data-ttu-id="3a5a1-195">Remove-PSSession: Hiermee wordt de PSSessions in de huidige sessie verwijderd</span><span class="sxs-lookup"><span data-stu-id="3a5a1-195">Remove-PSSession: Deletes the PSSessions in the current session</span></span>

## <a name="for-more-information"></a><span data-ttu-id="3a5a1-196">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="3a5a1-196">For More Information</span></span>

<span data-ttu-id="3a5a1-197">Zie [about_PSSession_Details](about_PSSession_Details.md)voor meer informatie over PSSessions.</span><span class="sxs-lookup"><span data-stu-id="3a5a1-197">For more information about PSSessions, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a5a1-198">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3a5a1-198">See Also</span></span>

[<span data-ttu-id="3a5a1-199">about_Remote</span><span class="sxs-lookup"><span data-stu-id="3a5a1-199">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="3a5a1-200">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="3a5a1-200">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="3a5a1-201">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="3a5a1-201">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="3a5a1-202">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a5a1-202">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="3a5a1-203">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a5a1-203">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="3a5a1-204">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a5a1-204">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="3a5a1-205">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a5a1-205">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[<span data-ttu-id="3a5a1-206">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a5a1-206">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="3a5a1-207">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="3a5a1-207">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="3a5a1-208">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a5a1-208">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="3a5a1-209">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="3a5a1-209">Remove-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSession)

