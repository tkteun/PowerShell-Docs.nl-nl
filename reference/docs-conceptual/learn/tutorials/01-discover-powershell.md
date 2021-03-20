---
title: Power shell detecteren
ms.date: 03/12/2021
ms.custom: chnoring
ms.reviewer: sewhee
description: Meer informatie over Power shell en enkele essentiële opdrachten die worden gebruikt om meer te weten te komen over Power shell.
ms.openlocfilehash: 34bbd465a918224c203e7243834e7fb3a3a6070c
ms.sourcegitcommit: 16a02ae47d1a85b01692101aa0aa6e91e1ba398e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730017"
---
# <a name="discover-powershell"></a><span data-ttu-id="5ba45-103">Power shell detecteren</span><span class="sxs-lookup"><span data-stu-id="5ba45-103">Discover PowerShell</span></span>

<span data-ttu-id="5ba45-104">Power shell is een opdracht regel shell en een script taal in één.</span><span class="sxs-lookup"><span data-stu-id="5ba45-104">PowerShell is a command-line shell and a scripting language in one.</span></span> <span data-ttu-id="5ba45-105">Power shell is gestart op Windows.</span><span class="sxs-lookup"><span data-stu-id="5ba45-105">PowerShell started out on Windows.</span></span> <span data-ttu-id="5ba45-106">Het is bedoeld om u te helpen bij het automatiseren van taken voor beheer taken, maar is nu gegroeid naar meerdere platformen en kan worden gebruikt voor verschillende taken.</span><span class="sxs-lookup"><span data-stu-id="5ba45-106">It was meant to help with task automation for administration tasks but has now grown to be cross platform and can be used for a variety of tasks.</span></span>

<span data-ttu-id="5ba45-107">Het maken van een unieke Power shell is het accepteren en retour neren van .NET-objecten in plaats van tekst.</span><span class="sxs-lookup"><span data-stu-id="5ba45-107">The thing that makes PowerShell unique is that accepts and returns .NET objects, rather than text.</span></span>
<span data-ttu-id="5ba45-108">Dit betekent dat het eenvoudiger is om verschillende opdrachten in reeksen te verbinden in een _pijp lijn_.</span><span class="sxs-lookup"><span data-stu-id="5ba45-108">This fact makes it easier to connect different commands in series, in a _pipeline_.</span></span>

> [!NOTE]
> <span data-ttu-id="5ba45-109">Pijp lijnen worden gedetailleerd besproken in deze zelfstudie reeks.</span><span class="sxs-lookup"><span data-stu-id="5ba45-109">Pipelines will be covered more in detail in this tutorial series.</span></span>

<span data-ttu-id="5ba45-110">Het kan ook voor komen dat u de resultaten enigszins moet _massage_ .</span><span class="sxs-lookup"><span data-stu-id="5ba45-110">Even then, you might need to _massage_ the results a little.</span></span>

## <a name="what-can-powershell--be-used-for"></a><span data-ttu-id="5ba45-111">Waarvoor kan Power shell worden gebruikt?</span><span class="sxs-lookup"><span data-stu-id="5ba45-111">What can PowerShell  be used for?</span></span>

<span data-ttu-id="5ba45-112">Het gebruik van Power shell is toegenomen sinds de dagen waarop het alleen Windows is.</span><span class="sxs-lookup"><span data-stu-id="5ba45-112">Usage of PowerShell has grown since the days when it was Windows-only.</span></span> <span data-ttu-id="5ba45-113">Het wordt nog steeds gebruikt voor Windows-taak automatisering, maar u kunt deze gebruiken voor verschillende taken, zoals:</span><span class="sxs-lookup"><span data-stu-id="5ba45-113">It's still used for Windows task automation, but today, you can use for a variety of tasks like:</span></span>

- <span data-ttu-id="5ba45-114">**Cloud beheer**.</span><span class="sxs-lookup"><span data-stu-id="5ba45-114">**Cloud management**.</span></span> <span data-ttu-id="5ba45-115">Power shell kan worden gebruikt om cloud resources te beheren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-115">PowerShell can be used to manage cloud resources.</span></span> <span data-ttu-id="5ba45-116">U kunt bijvoorbeeld informatie over cloud resources ophalen en nieuwe resources bijwerken of implementeren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-116">For example, you can retrieve information about cloud resources, as well as update or deploy new resources.</span></span>
- <span data-ttu-id="5ba45-117">**CI/cd**.</span><span class="sxs-lookup"><span data-stu-id="5ba45-117">**CI/CD**.</span></span> <span data-ttu-id="5ba45-118">Het kan ook worden gebruikt als onderdeel van een continue integratie/doorlopende implementatie pijplijn.</span><span class="sxs-lookup"><span data-stu-id="5ba45-118">It can also be used as part of a Continuous Integration/Continuous Deployment pipeline.</span></span>
- <span data-ttu-id="5ba45-119">**Taken automatiseren voor Active Directory en Exchange**.</span><span class="sxs-lookup"><span data-stu-id="5ba45-119">**Automate tasks for Active Directory and Exchange**.</span></span> <span data-ttu-id="5ba45-120">U kunt dit gebruiken om bijna elke taak in Windows te automatiseren, zoals het maken van gebruikers in Active Directory en post vakken in Exchange.</span><span class="sxs-lookup"><span data-stu-id="5ba45-120">You can use it to automate almost any task on Windows like creating users in Active Directory and mailboxes in Exchange.</span></span>

<span data-ttu-id="5ba45-121">Er zijn veel meer gebruiks gebieden, maar de bovenstaande lijst biedt u een hint die Power shell op een lange manier heeft geduurd.</span><span class="sxs-lookup"><span data-stu-id="5ba45-121">There are many more areas of usage but the list above gives you a hint that PowerShell has come a long way.</span></span>

## <a name="who-uses-powershell"></a><span data-ttu-id="5ba45-122">Wie gebruikt Power shell?</span><span class="sxs-lookup"><span data-stu-id="5ba45-122">Who uses PowerShell?</span></span>

<span data-ttu-id="5ba45-123">Power shell is zeer krachtig en veel mensen die in talrijke rollen werken, kunnen profiteren van het gebruik ervan.</span><span class="sxs-lookup"><span data-stu-id="5ba45-123">PowerShell is very powerful and a lot of people, working in multitude of roles, can benefit from using it.</span></span> <span data-ttu-id="5ba45-124">Traditioneel is Power shell gebruikt door de rol systeem beheerder, maar wordt dit nu gebruikt door mensen die zelf DevOps, Cloud-Ops en zelfs ontwikkel aars aanroepen.</span><span class="sxs-lookup"><span data-stu-id="5ba45-124">Traditionally, PowerShell has been used by the System Administrator role but is now being used by people calling themselves DevOps, Cloud Ops, and even Developers.</span></span>

## <a name="powershell-cmdlets"></a><span data-ttu-id="5ba45-125">PowerShell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="5ba45-125">PowerShell cmdlets</span></span>

<span data-ttu-id="5ba45-126">Power shell wordt geleverd met honderden vooraf geïnstalleerde opdrachten.</span><span class="sxs-lookup"><span data-stu-id="5ba45-126">PowerShell comes with hundreds of preinstalled commands.</span></span> <span data-ttu-id="5ba45-127">De Power shell-opdracht worden cmdlets genoemd. uitgesp roken als ' opdracht-Hiermee '.</span><span class="sxs-lookup"><span data-stu-id="5ba45-127">PowerShell command are called cmdlets; pronounced as "command-lets".</span></span>

<span data-ttu-id="5ba45-128">De naam van elke cmdlet bestaat uit een ' verb-zelfstandig '-paar. bijvoorbeeld `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-128">The name of each cmdlet consists of a "Verb-Noun" pair; for example `Get-Process`.</span></span> <span data-ttu-id="5ba45-129">Deze naamgevings Conventie maakt het gemakkelijker om te begrijpen wat de cmdlet doet.</span><span class="sxs-lookup"><span data-stu-id="5ba45-129">This naming convention makes it easier to understand what the cmdlet does.</span></span> <span data-ttu-id="5ba45-130">U kunt de opdracht die u zoekt ook gemakkelijker vinden.</span><span class="sxs-lookup"><span data-stu-id="5ba45-130">It also make it easier to find the command your looking for.</span></span> <span data-ttu-id="5ba45-131">Wanneer u op zoek bent naar een cmdlet die moet worden gebruikt, kunt u filteren op de term of het zelfstandig naam woord.</span><span class="sxs-lookup"><span data-stu-id="5ba45-131">When looking for a cmdlet to use, you can filter on the verb or noun.</span></span>

### <a name="using-cmdlets-to-explore-powershell"></a><span data-ttu-id="5ba45-132">Cmdlets gebruiken om Power shell te verkennen</span><span class="sxs-lookup"><span data-stu-id="5ba45-132">Using cmdlets to explore PowerShell</span></span>

<span data-ttu-id="5ba45-133">Wanneer u Power shell voor het eerst ophaalt, kan dit intimideren lijken, omdat er zo veel te leren is.</span><span class="sxs-lookup"><span data-stu-id="5ba45-133">When you first pick up PowerShell, it might feel intimidating as there seems to be so much to learn.</span></span>
<span data-ttu-id="5ba45-134">Power shell is echter ontworpen om u te helpen een beetje per keer te leren, zoals u dat nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="5ba45-134">However, PowerShell is designed to help you learn a little at a time, as you need it.</span></span>

<span data-ttu-id="5ba45-135">Power shell bevat cmdlets die u helpen bij het detecteren van Power shell.</span><span class="sxs-lookup"><span data-stu-id="5ba45-135">PowerShell includes cmdlets that help you discover PowerShell.</span></span> <span data-ttu-id="5ba45-136">Met deze drie cmdlets kunt u ontdekken welke opdrachten beschikbaar zijn, wat ze doen en op welke typen ze worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5ba45-136">Using these three cmdlets, you can discover what commands available, what they do, and what types they operate on.</span></span>

- <span data-ttu-id="5ba45-137">`Get-Verb`.</span><span class="sxs-lookup"><span data-stu-id="5ba45-137">`Get-Verb`.</span></span> <span data-ttu-id="5ba45-138">Als u deze opdracht uitvoert, wordt een lijst geretourneerd met de woorden die de meeste opdrachten naleven.</span><span class="sxs-lookup"><span data-stu-id="5ba45-138">Running this command returns a list of verbs that most commands adhere to.</span></span>
  <span data-ttu-id="5ba45-139">Daarnaast wordt met het antwoord de werking van deze termen beschreven.</span><span class="sxs-lookup"><span data-stu-id="5ba45-139">Additionally, the response describes what these verbs does.</span></span> <span data-ttu-id="5ba45-140">Aangezien de meeste opdrachten deze naam volgen, worden er verwachtingen ingesteld voor wat een opdracht doet, waarmee u de juiste opdracht kunt selecteren, maar ook de naam van een opdracht moet u er een maken.</span><span class="sxs-lookup"><span data-stu-id="5ba45-140">As most commands follow this naming, it sets expectations on what a command does, which helps you select the appropriate command but also what to name a command, should you be creating one.</span></span>
- <span data-ttu-id="5ba45-141">`Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="5ba45-141">`Get-Command`.</span></span> <span data-ttu-id="5ba45-142">Met deze opdracht wordt een lijst opgehaald met alle opdrachten die op uw computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="5ba45-142">This command retrieves a list of all commands installed on your machine.</span></span>
- <span data-ttu-id="5ba45-143">`Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="5ba45-143">`Get-Member`.</span></span> <span data-ttu-id="5ba45-144">Het werkt op objecten gebaseerd op uitvoer en kan detecteren welk object, eigenschappen en methoden beschikbaar zijn voor een opdracht.</span><span class="sxs-lookup"><span data-stu-id="5ba45-144">It operates on object based output and is able to discover what object, properties and methods are available for a command.</span></span>
- <span data-ttu-id="5ba45-145">`Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="5ba45-145">`Get-Help`.</span></span> <span data-ttu-id="5ba45-146">Als u deze opdracht aanroept met de naam van een opdracht als argument, wordt een Help-pagina weer gegeven met een beschrijving van de verschillende onderdelen van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="5ba45-146">Invoking this command with the name of a command as an argument displays a help page describing various parts of a command.</span></span>

<span data-ttu-id="5ba45-147">Met deze opdrachten kunt u bijna alles ontdekken wat u nodig hebt om te weten te komen over Power shell.</span><span class="sxs-lookup"><span data-stu-id="5ba45-147">Using these commands, you can discover almost anything you need to know about PowerShell.</span></span>

### <a name="verb"></a><span data-ttu-id="5ba45-148">Verb</span><span class="sxs-lookup"><span data-stu-id="5ba45-148">Verb</span></span>

<span data-ttu-id="5ba45-149">Term is een belang rijke concepten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="5ba45-149">Verb is an important concepts in PowerShell.</span></span> <span data-ttu-id="5ba45-150">Het is een naamgevings standaard die de meeste cmdlets volgt.</span><span class="sxs-lookup"><span data-stu-id="5ba45-150">It's a naming standard that most cmdlets follow.</span></span> <span data-ttu-id="5ba45-151">Het is ook een naamgevings standaard die u verwacht te volgen, wanneer u uw eigen opdrachten schrijft.</span><span class="sxs-lookup"><span data-stu-id="5ba45-151">It's also a naming standard you're expected to follow, once you write your own commands.</span></span> <span data-ttu-id="5ba45-152">Het idee is dat de _term_ aangeeft wat u probeert te doen, gegevens te lezen of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="5ba45-152">The idea is that the _verb_ says what you're trying to do, read data or maybe change it.</span></span> <span data-ttu-id="5ba45-153">Power Shell heeft een gestandaardiseerde lijst met termen.</span><span class="sxs-lookup"><span data-stu-id="5ba45-153">PowerShell has a standardized list of verbs.</span></span> <span data-ttu-id="5ba45-154">Gebruik de cmdlet om een volledige lijst met alle mogelijke termen te verkrijgen `Get-Verb` :</span><span class="sxs-lookup"><span data-stu-id="5ba45-154">To get a full list of all possible verbs, use the `Get-Verb` cmdlet:</span></span>

```powershell
Get-Verb
```

<span data-ttu-id="5ba45-155">De uitvoer van de uitvoering is een lange lijst met woorden.</span><span class="sxs-lookup"><span data-stu-id="5ba45-155">The output from running it, is a long list of verbs.</span></span> <span data-ttu-id="5ba45-156">Wat er op de hoogte is van het antwoord, is dat er ook meer context wordt weer gegeven, wat een dergelijke term bedoeld is.</span><span class="sxs-lookup"><span data-stu-id="5ba45-156">What's informative about the response, is that it also shows more context, what such a verb is meant to do.</span></span> <span data-ttu-id="5ba45-157">Dit is de eerste rij van de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="5ba45-157">Here's the first row of the output:</span></span>

```output
Verb        AliasPrefix Group          Description
----        ----------- -----          -----------
Add         a           Common         Adds a resource to a container, or attaches an item to ano…
```

## <a name="find-commands-with-get-command"></a><span data-ttu-id="5ba45-158">Zoek opdrachten met Get-Command</span><span class="sxs-lookup"><span data-stu-id="5ba45-158">Find commands with Get-Command</span></span>

<span data-ttu-id="5ba45-159">De `Get-Command` cmdlet retourneert een lijst van alle beschik bare opdrachten die op uw systeem zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="5ba45-159">The `Get-Command` cmdlet returns a list of all available commands that are installed on your system.</span></span>
<span data-ttu-id="5ba45-160">Deze lijst wordt weer gegeven, maar is wel erg groot.</span><span class="sxs-lookup"><span data-stu-id="5ba45-160">That list you get back, is quite large though.</span></span> <span data-ttu-id="5ba45-161">Als u de Zoek opdrachten eenvoudiger wilt maken, kunt u de hoeveelheid gegevens die wordt weer gegeven, beperken.</span><span class="sxs-lookup"><span data-stu-id="5ba45-161">To make finding commands easier you can limit the amount of information that comes back.</span></span> <span data-ttu-id="5ba45-162">U kunt het antwoord filteren met behulp van para meters of met helper-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5ba45-162">You can filter the response using either parameters or by using helper cmdlets.</span></span>

### <a name="filter-on-name"></a><span data-ttu-id="5ba45-163">Filteren op naam</span><span class="sxs-lookup"><span data-stu-id="5ba45-163">Filter on name</span></span>

<span data-ttu-id="5ba45-164">U kunt de uitvoer van filteren `Get-Command` met behulp van verschillende para meters.</span><span class="sxs-lookup"><span data-stu-id="5ba45-164">You can filter the output of `Get-Command`, using different parameters.</span></span> <span data-ttu-id="5ba45-165">Als u op deze manier filtert, wordt een query uitgevoerd op een specifieke eigenschap van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5ba45-165">Filtering this way, is about querying a specific property on the command.</span></span> <span data-ttu-id="5ba45-166">Het idee is dat u opgeeft op welke eigenschap u wilt filteren en vervolgens een teken reeks opgeeft waarmee u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="5ba45-166">The idea is that you specify what property you want to filter against, and then you provide a string that you want to match against.</span></span> <span data-ttu-id="5ba45-167">Daarom krijgt u een vergelijking die er als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="5ba45-167">You'll therefore get a comparison that looks like this:</span></span>

```powershell
Get-Command -Name '*Process'
```

<span data-ttu-id="5ba45-168">Op dit moment probeert het filter precies te vergelijken met het gegeven teken reeks argument.</span><span class="sxs-lookup"><span data-stu-id="5ba45-168">At this point, the filtering is trying to do an exact matching against the provided string argument.</span></span>
<span data-ttu-id="5ba45-169">Als u meer flexibiliteit wilt, kunt u in de vergelijking gebruikmaken van een Joker teken `*` dat overeenkomt met het patroon.</span><span class="sxs-lookup"><span data-stu-id="5ba45-169">If you want to have more flexibility, in the comparison, you can use a wildcard `*`, that does pattern matching.</span></span> <span data-ttu-id="5ba45-170">De volgende code zoekt naar alle opdrachten, waarvan de naam eindigt met het proces:</span><span class="sxs-lookup"><span data-stu-id="5ba45-170">The following code would look for all commands, who's name ends with process:</span></span>

<span data-ttu-id="5ba45-171">Hierboven, de para meter `-Name` die wordt gebruikt om te filteren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-171">Above, the parameter the `-Name` is used to filter.</span></span> <span data-ttu-id="5ba45-172">`-Name`U kunt ook filteren op `-ParameterName` en `-Type` , bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="5ba45-172">Apart from `-Name`, you can also filter on `-ParameterName` and `-Type`, for example.</span></span>

### <a name="filtering-on-noun-and-verb"></a><span data-ttu-id="5ba45-173">Filteren op zelfstandig naam woord en werk woord</span><span class="sxs-lookup"><span data-stu-id="5ba45-173">Filtering on Noun and Verb</span></span>

<span data-ttu-id="5ba45-174">U hebt gezien hoe u kunt filteren op `-Name` en u kunt ook andere para meters filteren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-174">You've seen how you can filter on `-Name`, and that there are other parameters you can filter on as well.</span></span> <span data-ttu-id="5ba45-175">Werk woord en zelfstandig naam woord kan ook worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="5ba45-175">Verb and noun is something you can filter on as well.</span></span> <span data-ttu-id="5ba45-176">Dergelijke filters hebben als doel een deel van de naam van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="5ba45-176">Such filtering targets part of a command's name.</span></span>

- <span data-ttu-id="5ba45-177">**Filter op term**.</span><span class="sxs-lookup"><span data-stu-id="5ba45-177">**Filter on verb**.</span></span> <span data-ttu-id="5ba45-178">Het gedeelte van de naam van een opdracht is het meest linkse deel.</span><span class="sxs-lookup"><span data-stu-id="5ba45-178">The verb part of a command's name is the leftmost part.</span></span> <span data-ttu-id="5ba45-179">In de opdracht `Get-Process` is het deel van de bewerking `Get` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-179">In the command `Get-Process`, the verb part is `Get`.</span></span> <span data-ttu-id="5ba45-180">Als u wilt filteren op het deel van de werk woord, geeft u `-Verb` als volgt op als para meter:</span><span class="sxs-lookup"><span data-stu-id="5ba45-180">To filter on th verb part, specify `-Verb` as a parameter like so:</span></span>

   ```powershell
   Get-Command -Verb 'Get'
   ```

   <span data-ttu-id="5ba45-181">Met de bovenstaande opdracht worden alle opdrachten weer geven waarvan het onderdeel deel uitmaakt `Get` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-181">The above command would list all the commands where the verb part is `Get`.</span></span>

- <span data-ttu-id="5ba45-182">**Filteren op zelfstandig naam woord**.</span><span class="sxs-lookup"><span data-stu-id="5ba45-182">**Filter on noun**.</span></span> <span data-ttu-id="5ba45-183">Het meest rechtse deel van een opdracht is het onderdeel van de zelfstandig naam woord.</span><span class="sxs-lookup"><span data-stu-id="5ba45-183">The rightmost part of a command is the noun part.</span></span> <span data-ttu-id="5ba45-184">Waarbij de term moet liggen tussen de bewerkingen die worden geretourneerd door aanroepen `Get-Verb` , kan een zelfstandig naam woord zijn.</span><span class="sxs-lookup"><span data-stu-id="5ba45-184">Where verb should be among the verbs returned from invoking `Get-Verb`, a noun can be anything.</span></span> <span data-ttu-id="5ba45-185">In de opdracht `Get-Process` is het onderdeel van de zelfstandig naam woord `Process` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-185">In the command `Get-Process`, the noun part is `Process`.</span></span> <span data-ttu-id="5ba45-186">Als u wilt filteren op zelfstandig naam woord, geeft u `-Noun` als een para meter en een teken reeks argument op, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5ba45-186">To filter on noun, specify `-Noun` as a parameter and a string argument, like so:</span></span>

   ```powershell
   Get-Command -Noun U*
   ```

<span data-ttu-id="5ba45-187">Alleen het gebruik van de term of het zelfstandige naam om te filteren op, kan nog steeds een groot resultaat opleveren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-187">Only using the verb, or the noun, to filter on, might lead to a big result still.</span></span> <span data-ttu-id="5ba45-188">Om uw zoek opdracht te verfijnen, is het handig om de twee para meters te combi neren, zoals in het onderstaande voor beeld:</span><span class="sxs-lookup"><span data-stu-id="5ba45-188">To narrow down your search, it's good to combine the two parameters like the below example:</span></span>

```powershell
Get-Command -Verb Get -Noun U*
```

<span data-ttu-id="5ba45-189">Het resultaat van het bovenstaande ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="5ba45-189">The result of the above looks like so:</span></span>

```output
CommandType     Name                         Version    Source
-----------     ----                         -------    ------
Cmdlet          Get-UICulture                7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-Unique                   7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-Uptime                   7.0.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-UsageAggregates          2.0.0      Az.Billing
```

<span data-ttu-id="5ba45-190">Zo kunt u de uitvoer echt beperken door de term te weten en wat deze wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="5ba45-190">Thereby, you narrowed down the output quite bit by knowing the verb and what it's called.</span></span>

### <a name="use-helper-cmdlets-to-filter-results"></a><span data-ttu-id="5ba45-191">Helper-cmdlets gebruiken om resultaten te filteren</span><span class="sxs-lookup"><span data-stu-id="5ba45-191">Use helper cmdlets to filter results</span></span>

<span data-ttu-id="5ba45-192">Naast het gebruik van para meters om te filteren, kunt u ook opdrachten gebruiken om u te helpen met deze taak.</span><span class="sxs-lookup"><span data-stu-id="5ba45-192">Apart from using parameters to filter, you can also use commands to help you with this task.</span></span> <span data-ttu-id="5ba45-193">Hier volgen enkele opdrachten die kunnen fungeren als filters:</span><span class="sxs-lookup"><span data-stu-id="5ba45-193">Here's some commands that can act as filters:</span></span>

- <span data-ttu-id="5ba45-194">`Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="5ba45-194">`Select-Object`.</span></span> <span data-ttu-id="5ba45-195">Het is een zeer veelzijdige opdracht waarmee u specifieke eigenschappen van een of meer objecten kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="5ba45-195">It's a very versatile command that helps you pick out specific properties from one or more objects.</span></span> <span data-ttu-id="5ba45-196">Daarnaast kunt u met behulp van de para meters het antwoord dat u terugkrijgt, beperken.</span><span class="sxs-lookup"><span data-stu-id="5ba45-196">Additionally by using it's parameters you can limit the response you get back.</span></span> <span data-ttu-id="5ba45-197">Hier volgt een voor beeld van `Select-Object` dat wordt gebruikt om te vragen naar een beperkt aantal records:</span><span class="sxs-lookup"><span data-stu-id="5ba45-197">Here's an example of `Select-Object` being used to ask for a limited number of records:</span></span>

   ```powershell
   Get-Command | Select-Object -First 3
   ```

   <span data-ttu-id="5ba45-198">Het resultaat van de bovenstaande is de drie eerste opdrachten, geteld vanaf de bovenkant.</span><span class="sxs-lookup"><span data-stu-id="5ba45-198">The result from the above is the three first commands, counted from the top.</span></span> <span data-ttu-id="5ba45-199">Het resultaat ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="5ba45-199">The result looks like so:</span></span>

   ```output
   CommandType     Name                                               Version    Source
   -----------     ----                                               -------    ------
   Alias           Add-AdlAnalyticsDataSource                         1.0.2      Az.DataLakeAnalytics
   Alias           Add-AdlAnalyticsFirewallRule                       1.0.2      Az.DataLakeAnalytics
   Alias           Add-AdlStoreFirewallRule                           1.3.0      Az.DataLakeStore
   ```

   <span data-ttu-id="5ba45-200">Het is een goed idee om te kijken naar deze opdracht, omdat het veel meer  [documenten kan selecteren-object](/powershell/module/microsoft.powershell.utility/select-object)</span><span class="sxs-lookup"><span data-stu-id="5ba45-200">It's worth looking into to this command further as it can do a lot more  [docs Select-Object](/powershell/module/microsoft.powershell.utility/select-object)</span></span>

- <span data-ttu-id="5ba45-201">`Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="5ba45-201">`Where-Object`.</span></span> <span data-ttu-id="5ba45-202">Het object where helpt u bij het selecteren van objecten uit een verzameling op basis van de waarden van eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="5ba45-202">The where object helps you select objects from a collection based on the values of properties.</span></span> <span data-ttu-id="5ba45-203">De opdracht heeft een expressie waarin u kunt zien welke kolom/s u wilt laten overeenkomen met welke waarden.</span><span class="sxs-lookup"><span data-stu-id="5ba45-203">The command takes an expression in which you are able to express what column/s you want to match against what values.</span></span> <span data-ttu-id="5ba45-204">Als u wilt zoeken naar alle proces objecten waarbij de `ProcessName` begint met `p` , kunt u het `Where-Object` volgende gebruiken:</span><span class="sxs-lookup"><span data-stu-id="5ba45-204">To find all process object where the `ProcessName` starts with `p`, you could use `Where-Object` like so:</span></span>

  ```powershell
  Get-Process | Where-Object {$_.ProcessName -Like "p*"}
  ```

  <span data-ttu-id="5ba45-205">Hierboven maakt de `Get-Process` cmdlet een verzameling proces objecten.</span><span class="sxs-lookup"><span data-stu-id="5ba45-205">Above, the `Get-Process` cmdlet produces a collection of process objects.</span></span> <span data-ttu-id="5ba45-206">Als u het antwoord wilt filteren, kunt u de opdracht door _sluizen_ `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-206">To filter down the response, you _pipe_ the command `Where-Object`.</span></span> <span data-ttu-id="5ba45-207">Leidingen houdt in dat er twee of meer opdrachten zijn verbonden via een sluis `|` teken.</span><span class="sxs-lookup"><span data-stu-id="5ba45-207">Piping means that two or more commands are connected via a pipe `|` character.</span></span> <span data-ttu-id="5ba45-208">Het idee is dat de uitvoer van de ene opdracht als de invoer voor de volgende opdracht fungeert, zoals gelezen van links naar rechts.</span><span class="sxs-lookup"><span data-stu-id="5ba45-208">The idea is that the output from one command serves as the input for the next command, as read from left to right.</span></span> <span data-ttu-id="5ba45-209">De `Where-Object` gebruikt een expressie om te filteren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-209">The `Where-Object` uses an expression to filter.</span></span> <span data-ttu-id="5ba45-210">De expressie zelf maakt gebruik van de `-Like` operator en het teken reeks argument die een Joker teken expressie zijn.</span><span class="sxs-lookup"><span data-stu-id="5ba45-210">The expression itself uses the `-Like` operator and string argument that is a wildcard expression.</span></span>

## <a name="explore-objects-with-get-member"></a><span data-ttu-id="5ba45-211">Objecten verkennen met Get-Member</span><span class="sxs-lookup"><span data-stu-id="5ba45-211">Explore objects with Get-Member</span></span>

<span data-ttu-id="5ba45-212">Wanneer u de gewenste cmdlet hebt gevonden, wilt u meer weten over wat deze produceert, de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="5ba45-212">Once you've been able to locate the cmdlet you want, you want to know more about what it produces, the output.</span></span> <span data-ttu-id="5ba45-213">De uitvoer is om verschillende redenen interessant, zoals:</span><span class="sxs-lookup"><span data-stu-id="5ba45-213">The output is interesting for several reasons like:</span></span>

- <span data-ttu-id="5ba45-214">**Zelfstandig**.</span><span class="sxs-lookup"><span data-stu-id="5ba45-214">**Standalone**.</span></span> <span data-ttu-id="5ba45-215">U kunt slechts één cmdlet uitvoeren en de uitvoer weer geven in een rapport waarop u wilt sorteren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-215">You might run just one cmdlet and you want to display the output in some sort of report.</span></span> <span data-ttu-id="5ba45-216">De vraag om u te vragen of de opdracht een uitvoer produceert die geschikt is voor u, of dat u deze moet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="5ba45-216">The question to ask yourself is whether the command produces an output that works for you, or if you need to change it.</span></span>
- <span data-ttu-id="5ba45-217">**Bij gebruik in een pijp lijn**.</span><span class="sxs-lookup"><span data-stu-id="5ba45-217">**When used in a pipeline**.</span></span> <span data-ttu-id="5ba45-218">Het is gebruikelijk in Power shell om meerdere opdrachten in een pijp lijn te verbinden, gegevens op te halen, te filteren en tot slot te transformeren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-218">It's common in PowerShell to connect several commands in a pipeline, to fetch data, filter and finally to transform it.</span></span> <span data-ttu-id="5ba45-219">Als u wilt dat een opdracht in een pijp lijn past, moet u kijken welke invoer en uitvoer er worden geproduceerd.</span><span class="sxs-lookup"><span data-stu-id="5ba45-219">For a command to fit into a pipeline, you have to look at what input and output it produces.</span></span> <span data-ttu-id="5ba45-220">Het idee is dat de uitvoer van een opdracht wordt gebruikt als invoer van een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="5ba45-220">The idea is that the output of a command is used as the input of another command.</span></span>

<span data-ttu-id="5ba45-221">`Get-Member`Met de cmdlet worden de eigenschappen en methoden van het resultaat weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5ba45-221">The `Get-Member` cmdlet displays the properties and methods of the result.</span></span> <span data-ttu-id="5ba45-222">Daarnaast wordt ook het type van het object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5ba45-222">Additionally it also show the type of the object.</span></span> <span data-ttu-id="5ba45-223">Pipet de uitvoer die u wilt inspecteren `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-223">Pipe the output you want to inspect to `Get-Member`.</span></span>

```powershell
Get-Process | Get-Member
```

<span data-ttu-id="5ba45-224">Het resultaat geeft het geretourneerde type weer als `TypeName` en vervolgens alle eigenschappen en methoden van het object.</span><span class="sxs-lookup"><span data-stu-id="5ba45-224">The result displays the returned type as `TypeName` and then all the properties and methods of the object.</span></span> <span data-ttu-id="5ba45-225">Hier volgt een fragment van een dergelijk resultaat:</span><span class="sxs-lookup"><span data-stu-id="5ba45-225">Here's an excerpt of such a result:</span></span>

```output
TypeName: System.Diagnostics.Process

Name        MemberType     Definition
----        ----------     ----------
Handles     AliasProperty  Handles = Handlecount
Name        AliasProperty  Name = ProcessName
```

<span data-ttu-id="5ba45-226">Een object heeft meestal uitgebreide eigenschappen en methoden, zodat u gemakkelijker kunt vinden wat u zoekt, de resultaten kunnen filteren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-226">An object usually has plenty of properties and methods, to more easily find what you're looking for, you can filter the results.</span></span> <span data-ttu-id="5ba45-227">Met behulp van de para meter `-MemberType` kunt u opgeven dat u bijvoorbeeld alle methoden wilt zien, zoals in het onderstaande voor beeld:</span><span class="sxs-lookup"><span data-stu-id="5ba45-227">By using the parameter `-MemberType`, you can specify to, for example see all the methods, like in the below example:</span></span>

```powershell
Get-Process | Get-Member -MemberType Method
```

<span data-ttu-id="5ba45-228">Wanneer u terugkeert naar een reactie, worden in Power shell meestal slechts enkele eigenschappen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5ba45-228">When you get a response back, PowerShell usually only displays a few properties.</span></span> <span data-ttu-id="5ba45-229">In het bovenstaande antwoord wordt `Name` `MemberType` en `Definition` weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5ba45-229">In the above response, `Name`, `MemberType` and `Definition` was displayed.</span></span> <span data-ttu-id="5ba45-230">Als u deze weer gave wilt wijzigen, kunt u de cmdlet gebruiken `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-230">To change that display, you can use the cmdlet `Select-Object`.</span></span> <span data-ttu-id="5ba45-231">`Select-Object` Hiermee kunt u opgeven welke kolommen u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="5ba45-231">`Select-Object` allows you to specify what columns you want to see.</span></span> <span data-ttu-id="5ba45-232">U kunt deze opgeven met de naam van de kolom, een door komma's gescheiden lijst of een Joker teken `*` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-232">You can either provide it with the name of the column, a comma separated list or a wildcard `*`.</span></span> <span data-ttu-id="5ba45-233">Hier volgt een voor beeld waarin `Select-Object` wordt gebruikt om op te halen `Name` en `Definition` :</span><span class="sxs-lookup"><span data-stu-id="5ba45-233">Here's an example where `Select-Object` is used to retrieve `Name` and `Definition`:</span></span>

```powershell
Get-Process | Get-Member | Select-Object Name, Definition
```

### <a name="search-by-type"></a><span data-ttu-id="5ba45-234">Zoeken op type</span><span class="sxs-lookup"><span data-stu-id="5ba45-234">Search by type</span></span>

<span data-ttu-id="5ba45-235">Een andere manier om te zoeken naar de gewenste opdracht, is door te zoeken naar opdrachten die allemaal op hetzelfde type werken.</span><span class="sxs-lookup"><span data-stu-id="5ba45-235">Another way to approach searching for the command you want, is by searching for commands all operating on the same type.</span></span> <span data-ttu-id="5ba45-236">Wanneer u hebt gebruikt `Get-Member` , hebt u het geretourneerde type als de eerste regel van de reactie als volgt:</span><span class="sxs-lookup"><span data-stu-id="5ba45-236">When you used `Get-Member`, you got the returned type as the first line of the response like so:</span></span>

```output
TypeName: System.Diagnostics.Process
```

<span data-ttu-id="5ba45-237">U kunt dit type nu gebruiken en zoeken naar opdrachten als volgt:</span><span class="sxs-lookup"><span data-stu-id="5ba45-237">You can now use this type and search for commands like so:</span></span>

```powershell
Get-Command -ParameterType Process
```

<span data-ttu-id="5ba45-238">Het resultaat van het aanroepen van de bovenstaande is een lijst met opdrachten die alleen voor het type worden uitgevoerd `Process` :</span><span class="sxs-lookup"><span data-stu-id="5ba45-238">The result from invoking the above is a list with commands that solely operates on the `Process` type:</span></span>

```output
CommandType     Name                         Version    Source
-----------     ----                         -------    ------
Cmdlet          Debug-Process                7.0.0.0    Microsoft.PowerShell.Managem…
Cmdlet          Enter-PSHostProcess          7.1.0.0    Microsoft.PowerShell.Core
Cmdlet          Get-Process                  7.0.0.0    Microsoft.PowerShell.Managem…
Cmdlet          Get-PSHostProcessInfo        7.1.0.0    Microsoft.PowerShell.Core
Cmdlet          Stop-Process                 7.0.0.0    Microsoft.PowerShell.Managem…
Cmdlet          Wait-Process                 7.0.0.0    Microsoft.PowerShell.Managem…
```

<span data-ttu-id="5ba45-239">Zoals u kunt zien, is het type van een opdracht, zodat u de zoek actie aanzienlijk kunt verfijnen na opdrachten die voor u interessant kunnen zijn.</span><span class="sxs-lookup"><span data-stu-id="5ba45-239">As you can see, knowing the type of a command, can greatly narrow down your search after commands that might be interesting for you.</span></span>

## <a name="exercise---calling-your-first-command"></a><span data-ttu-id="5ba45-240">Oefenen: uw eerste opdracht aanroepen</span><span class="sxs-lookup"><span data-stu-id="5ba45-240">Exercise - calling your first command</span></span>

<span data-ttu-id="5ba45-241">In deze oefening leert u hoe u uw eerste opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5ba45-241">In this exercise, you'll learn how to run your first command.</span></span>

1. <span data-ttu-id="5ba45-242">Start een Power shell-console door het volgende te typen `pwsh` :</span><span class="sxs-lookup"><span data-stu-id="5ba45-242">Start a PowerShell console by typing `pwsh`:</span></span>

   ```powershell
   pwsh
   ```

1. <span data-ttu-id="5ba45-243">Voer de volgende `$PSVersionTable.PSVersion` handelingen uit:</span><span class="sxs-lookup"><span data-stu-id="5ba45-243">Run the following `$PSVersionTable.PSVersion`:</span></span>

   ```powershell
   $PSVersionTable.PSVersion
   ```

   <span data-ttu-id="5ba45-244">De uitvoer ziet er ongeveer als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="5ba45-244">Your output looks similar to this:</span></span>

   ```output
   Major  Minor  Patch  PreReleaseLabel BuildLabel
   -----  -----  -----  --------------- ----------
   7      1      0
   ```

   <span data-ttu-id="5ba45-245">Gefeliciteerd, u hebt uw eerste opdracht uitgevoerd en kon informatie krijgen over de versie van Power shell die op uw systeem is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="5ba45-245">Congrats, you've successfully run your first command and was able to get information of what version of PowerShell is installed on your system.</span></span>

## <a name="exercise---find-related-commands"></a><span data-ttu-id="5ba45-246">Oefenen: verwante opdrachten zoeken</span><span class="sxs-lookup"><span data-stu-id="5ba45-246">Exercise - find related commands</span></span>

<span data-ttu-id="5ba45-247">In deze oefening is het doel om meer te weten te komen over een opdracht.</span><span class="sxs-lookup"><span data-stu-id="5ba45-247">In this exercise your goal is to learn more about a command.</span></span> <span data-ttu-id="5ba45-248">In dat geval vindt u ook informatie over het type waarmee deze werkt en wat andere vergelijk bare opdrachten op hetzelfde type uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-248">In doing so you'll also find things like what type it operates on and what other similar commands operate on that same type.</span></span>

1. <span data-ttu-id="5ba45-249">Zorg ervoor dat u een Power shell-shell hebt gestart</span><span class="sxs-lookup"><span data-stu-id="5ba45-249">Ensure you have a started PowerShell shell</span></span>
1. <span data-ttu-id="5ba45-250">Voer de volgende opdracht uit `Get-Process` :</span><span class="sxs-lookup"><span data-stu-id="5ba45-250">Run the the command `Get-Process`:</span></span>

   ```powershell
   Get-Process | Get-Member | Select-Object TypeName -Unique
   ```

   <span data-ttu-id="5ba45-251">De uitvoer ziet er ongeveer als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="5ba45-251">Your output resembles this:</span></span>

   ```output
   TypeName
   --------
   System.Diagnostics.Process
   --------
   ```

   <span data-ttu-id="5ba45-252">Wat u terugkrijgt, is een van de typen die worden geretourneerd door de opdracht `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-252">What you're getting back, is a the types returned by the command `Get-Command`.</span></span> <span data-ttu-id="5ba45-253">Op dit moment kunt u nu zien welke andere opdracht ook op deze typen wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5ba45-253">At this point you can now find out what other command also operates on these types.</span></span>

1. <span data-ttu-id="5ba45-254">Voer de opdracht `Get-Command` uit:</span><span class="sxs-lookup"><span data-stu-id="5ba45-254">Run the command `Get-Command`:</span></span>

   ```powershell
   Get-Command -ParameterType Process
   ```

   <span data-ttu-id="5ba45-255">De uitvoer ziet er ongeveer als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="5ba45-255">Your output resembles this:</span></span>

   ```output
   CommandType     Name                         Version    Source
    -----------     ----                        -------    ------
    Cmdlet          Debug-Process               7.0.0.0    Microsoft.PowerShell.Managem…
    Cmdlet          Enter-PSHostProcess         7.1.0.0    Microsoft.PowerShell.Core
    Cmdlet          Get-Process                 7.0.0.0    Microsoft.PowerShell.Managem…
    Cmdlet          Get-PSHostProcessInfo       7.1.0.0    Microsoft.PowerShell.Core
    Cmdlet          Stop-Process                7.0.0.0    Microsoft.PowerShell.Managem…
    Cmdlet          Wait-Process                7.0.0.0    Microsoft.PowerShell.Managem…
   ```

   <span data-ttu-id="5ba45-256">Gefeliciteerd, u hebt beheerd om andere opdrachten te vinden die actief zijn op hetzelfde type `Process` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-256">Congratulations, you've managed to find other commands that operates on the same type `Process`.</span></span>
   <span data-ttu-id="5ba45-257">Gebruik `Get-Member` is een goed uitgangs punt om te begrijpen welke andere opdrachten u moet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="5ba45-257">Using `Get-Member` is a good starting point to understand what other commands you should check out next.</span></span>

## <a name="summary"></a><span data-ttu-id="5ba45-258">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="5ba45-258">Summary</span></span>

<span data-ttu-id="5ba45-259">In dit eerste deel hebt u geleerd wat Power shell is en welke gebieden in kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5ba45-259">In this first part, you learned what PowerShell is and what areas in can be used.</span></span> <span data-ttu-id="5ba45-260">Vervolgens kunt u met de cursus over cmdlets en met name `Get-Command` `Get-Verb` en `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="5ba45-260">You where then taught about cmdlets and in particular `Get-Command`, `Get-Verb` and `Get-Member`.</span></span> <span data-ttu-id="5ba45-261">Het is belang rijk dat u weet hoe u deze cmdlets kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5ba45-261">Knowing theses cmdlets is important as it teaches you how to learn.</span></span> <span data-ttu-id="5ba45-262">In het volgende deel wordt beschreven hoe u het krachtige Help-systeem gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5ba45-262">In the next part, you'll learn how to use the powerful help system.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5ba45-263">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="5ba45-263">Additional resources</span></span>

- [<span data-ttu-id="5ba45-264">Get-Command</span><span class="sxs-lookup"><span data-stu-id="5ba45-264">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)
- [<span data-ttu-id="5ba45-265">Get-member</span><span class="sxs-lookup"><span data-stu-id="5ba45-265">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
