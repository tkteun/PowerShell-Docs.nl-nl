---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objecten verwijderen vanuit de Pipeline waar Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 4140c4c3ebb26223d03ca139992fedf6e184a38b
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="94626-103">Verwijderen van objecten uit de pijplijn (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="94626-103">Removing Objects from the Pipeline (Where-Object)</span></span>
<span data-ttu-id="94626-104">In Windows PowerShell kunt u vaak genereren en doorgegeven meer objecten voor een pijplijn dan u wenst.</span><span class="sxs-lookup"><span data-stu-id="94626-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="94626-105">U kunt opgeven dat de eigenschappen van bepaalde objecten worden weergegeven met behulp van de **indeling** cmdlets, maar dit niet helpt met het probleem van het gehele objecten verwijderen uit de weergave.</span><span class="sxs-lookup"><span data-stu-id="94626-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="94626-106">U wilt filteren, objecten vóór het einde van een pijplijn, zodat u acties op slechts een subset van de objecten in eerste instantie gegenereerd uitvoeren kan.</span><span class="sxs-lookup"><span data-stu-id="94626-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="94626-107">Windows PowerShell omvat een **Where-Object** u elk object in de pijplijn te testen en alleen langs de pijplijn te doorgeven kunt als deze voldoet aan de voorwaarde van een afzonderlijke test-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="94626-107">Windows PowerShell includes a **Where-Object** cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="94626-108">Objecten die niet door de test worden verwijderd vanuit de pipeline.</span><span class="sxs-lookup"><span data-stu-id="94626-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="94626-109">U de testvoorwaarde opgeven als de waarde van de **waar ObjectFilterScript** parameter.</span><span class="sxs-lookup"><span data-stu-id="94626-109">You supply the test condition as the value of the **Where-ObjectFilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="94626-110">U eenvoudige tests uitvoert met de Where-Object</span><span class="sxs-lookup"><span data-stu-id="94626-110">Performing Simple Tests with Where-Object</span></span>
<span data-ttu-id="94626-111">De waarde van **FilterScript** is een *scriptblok* - een of meer Windows PowerShell-opdrachten omgeven door accolades {} - die resulteert in waar of ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="94626-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="94626-112">Deze scriptblokken is zeer eenvoudig, maar ze worden gemaakt moet weten over een andere Windows PowerShell-concept vergelijkingsoperators.</span><span class="sxs-lookup"><span data-stu-id="94626-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="94626-113">Een vergelijkingsoperator vergelijkt de items die worden weergegeven voor elke zijde van deze.</span><span class="sxs-lookup"><span data-stu-id="94626-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="94626-114">Vergelijkingsoperators beginnen met een '-' teken en worden gevolgd door een naam.</span><span class="sxs-lookup"><span data-stu-id="94626-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="94626-115">Basic vergelijkingsoperators werken op vrijwel elke soort object.</span><span class="sxs-lookup"><span data-stu-id="94626-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="94626-116">De meer geavanceerde vergelijkingsoperators mogelijk werken alleen op tekst- of -matrices.</span><span class="sxs-lookup"><span data-stu-id="94626-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="94626-117">Als u werkt met tekst zijn, Windows PowerShell-vergelijkingsoperators standaard niet hoofdlettergevoelig.</span><span class="sxs-lookup"><span data-stu-id="94626-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="94626-118">Symbolen zoals <>, vanwege het parseren van de overwegingen en = niet als vergelijkingsoperators worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="94626-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="94626-119">In plaats daarvan vergelijkingsoperators bestaan uit letters.</span><span class="sxs-lookup"><span data-stu-id="94626-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="94626-120">De basic vergelijkingsoperators worden weergegeven in de volgende tabel.</span><span class="sxs-lookup"><span data-stu-id="94626-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="94626-121">Vergelijkingsoperator</span><span class="sxs-lookup"><span data-stu-id="94626-121">Comparison Operator</span></span>|<span data-ttu-id="94626-122">Betekenis</span><span class="sxs-lookup"><span data-stu-id="94626-122">Meaning</span></span>|<span data-ttu-id="94626-123">Voorbeeld (' true ' geretourneerd)</span><span class="sxs-lookup"><span data-stu-id="94626-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="94626-124">-eq</span><span class="sxs-lookup"><span data-stu-id="94626-124">-eq</span></span>|<span data-ttu-id="94626-125">is gelijk aan</span><span class="sxs-lookup"><span data-stu-id="94626-125">is equal to</span></span>|<span data-ttu-id="94626-126">1 - eq 1</span><span class="sxs-lookup"><span data-stu-id="94626-126">1 -eq 1</span></span>|
|<span data-ttu-id="94626-127">-ne</span><span class="sxs-lookup"><span data-stu-id="94626-127">-ne</span></span>|<span data-ttu-id="94626-128">Is niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="94626-128">Is not equal to</span></span>|<span data-ttu-id="94626-129">1 - ne 2</span><span class="sxs-lookup"><span data-stu-id="94626-129">1 -ne 2</span></span>|
|<span data-ttu-id="94626-130">-lt</span><span class="sxs-lookup"><span data-stu-id="94626-130">-lt</span></span>|<span data-ttu-id="94626-131">Is kleiner dan</span><span class="sxs-lookup"><span data-stu-id="94626-131">Is less than</span></span>|<span data-ttu-id="94626-132">1 - lt 2</span><span class="sxs-lookup"><span data-stu-id="94626-132">1 -lt 2</span></span>|
|<span data-ttu-id="94626-133">-RP</span><span class="sxs-lookup"><span data-stu-id="94626-133">-le</span></span>|<span data-ttu-id="94626-134">Is kleiner dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="94626-134">Is less than or equal to</span></span>|<span data-ttu-id="94626-135">1 - RP 2</span><span class="sxs-lookup"><span data-stu-id="94626-135">1 -le 2</span></span>|
|<span data-ttu-id="94626-136">-gt</span><span class="sxs-lookup"><span data-stu-id="94626-136">-gt</span></span>|<span data-ttu-id="94626-137">Is groter dan</span><span class="sxs-lookup"><span data-stu-id="94626-137">Is greater than</span></span>|<span data-ttu-id="94626-138">2 - gt 1</span><span class="sxs-lookup"><span data-stu-id="94626-138">2 -gt 1</span></span>|
|<span data-ttu-id="94626-139">-ge</span><span class="sxs-lookup"><span data-stu-id="94626-139">-ge</span></span>|<span data-ttu-id="94626-140">Is groter dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="94626-140">Is greater than or equal to</span></span>|<span data-ttu-id="94626-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="94626-141">2 -ge 1</span></span>|
|<span data-ttu-id="94626-142">-zoals</span><span class="sxs-lookup"><span data-stu-id="94626-142">-like</span></span>|<span data-ttu-id="94626-143">Lijkt (vergelijking van jokertekens voor tekst)</span><span class="sxs-lookup"><span data-stu-id="94626-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="94626-144">"bestand.doc'-zoals ' f\*basisbedrijfstoepassingen?"</span><span class="sxs-lookup"><span data-stu-id="94626-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="94626-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="94626-145">-notlike</span></span>|<span data-ttu-id="94626-146">Is geen zoals (vergelijking van jokertekens voor tekst)</span><span class="sxs-lookup"><span data-stu-id="94626-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="94626-147">'bestand.doc'-notlike ' p\*.doc '</span><span class="sxs-lookup"><span data-stu-id="94626-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="94626-148">-bevat</span><span class="sxs-lookup"><span data-stu-id="94626-148">-contains</span></span>|<span data-ttu-id="94626-149">Bevat</span><span class="sxs-lookup"><span data-stu-id="94626-149">Contains</span></span>|<span data-ttu-id="94626-150">1,2,3 - 1 bevat</span><span class="sxs-lookup"><span data-stu-id="94626-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="94626-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="94626-151">-notcontains</span></span>|<span data-ttu-id="94626-152">Bevat geen</span><span class="sxs-lookup"><span data-stu-id="94626-152">Does not contain</span></span>|<span data-ttu-id="94626-153">1,2,3 - notcontains 4</span><span class="sxs-lookup"><span data-stu-id="94626-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="94626-154">De speciale variabele '$_' WHERE-Object scriptblokken gebruiken om te verwijzen naar het huidige object in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="94626-154">Where-Object script blocks use the special variable '$_' to refer to the current object in the pipeline.</span></span> <span data-ttu-id="94626-155">Hier volgt een voorbeeld van hoe het werkt.</span><span class="sxs-lookup"><span data-stu-id="94626-155">Here is an example of how it works.</span></span> <span data-ttu-id="94626-156">Als u een lijst met getallen hebben en retourneren van de waarden die minder dan 3 zijn, kunt u Where-Object voor het filteren van de getallen door te typen:</span><span class="sxs-lookup"><span data-stu-id="94626-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="94626-157">Filteren op basis van eigenschappen van het Object</span><span class="sxs-lookup"><span data-stu-id="94626-157">Filtering Based on Object Properties</span></span>
<span data-ttu-id="94626-158">Aangezien $_ naar de huidige pipeline-object verwijst, wordt toegang tot de eigenschappen voor onze tests.</span><span class="sxs-lookup"><span data-stu-id="94626-158">Since $_ refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="94626-159">Als u bijvoorbeeld kunt kijken we de klasse Win32_SystemDriver in WMI.</span><span class="sxs-lookup"><span data-stu-id="94626-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="94626-160">Er zijn mogelijk honderden besturingsprogramma's op een bepaald systeem, maar u mogelijk alleen geïnteresseerd zijn in een bepaalde set van het besturingsprogramma's, zoals die momenteel worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="94626-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="94626-161">Als u lid zijn van Get Win32_SystemDriver leden weergeven (**Get-WmiObject-klasse Win32_SystemDriver | De eigenschap Get-Member - MemberType**) ziet u dat de relevante eigenschap status is en dat er een waarde van het 'Uitvoeren' wanneer het stuurprogramma wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="94626-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="94626-162">U kunt de systeem-stuurprogramma's filteren selecteren uitgevoerd die door te typen:</span><span class="sxs-lookup"><span data-stu-id="94626-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"}
```

<span data-ttu-id="94626-163">Dit resulteert in nog steeds een lange lijst.</span><span class="sxs-lookup"><span data-stu-id="94626-163">This still produces a long list.</span></span> <span data-ttu-id="94626-164">U wilt filteren zodat alleen de stuurprogramma's automatisch worden gestart door de waarde van StartMode ook testen selecteren:</span><span class="sxs-lookup"><span data-stu-id="94626-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

<span data-ttu-id="94626-165">Dit biedt ons veel informatie die we niet meer nodig omdat we weten dat de stuurprogramma's worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="94626-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="94626-166">De enige informatie die we waarschijnlijk nodig hebt op dit moment zijn in feite de naam en de weergavenaam.</span><span class="sxs-lookup"><span data-stu-id="94626-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="94626-167">De volgende opdracht bevat alleen deze twee eigenschappen, wat resulteert in veel eenvoudiger uitvoer:</span><span class="sxs-lookup"><span data-stu-id="94626-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="94626-168">Er zijn twee elementen van de Where-Object in de bovenstaande opdracht, maar ze kunnen worden uitgedrukt in een enkel element in de Where-Object met behulp van de - en de logische operator, als volgt:</span><span class="sxs-lookup"><span data-stu-id="94626-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq "Running") -and ($_.StartMode -eq "Manual") } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="94626-169">De standaard logische operators worden weergegeven in de volgende tabel.</span><span class="sxs-lookup"><span data-stu-id="94626-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="94626-170">Logische Operator</span><span class="sxs-lookup"><span data-stu-id="94626-170">Logical Operator</span></span>|<span data-ttu-id="94626-171">Betekenis</span><span class="sxs-lookup"><span data-stu-id="94626-171">Meaning</span></span>|<span data-ttu-id="94626-172">Voorbeeld (' true ' geretourneerd)</span><span class="sxs-lookup"><span data-stu-id="94626-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="94626-173">- en</span><span class="sxs-lookup"><span data-stu-id="94626-173">-and</span></span>|<span data-ttu-id="94626-174">Logische en; True als aan beide zijden wordt voldaan</span><span class="sxs-lookup"><span data-stu-id="94626-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="94626-175">(1 - eq 1) - en (2 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="94626-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="94626-176">- of</span><span class="sxs-lookup"><span data-stu-id="94626-176">-or</span></span>|<span data-ttu-id="94626-177">Logische of; True als beide zijden ingesteld op true is</span><span class="sxs-lookup"><span data-stu-id="94626-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="94626-178">(1 - eq 1) - of (1 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="94626-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="94626-179">-niet</span><span class="sxs-lookup"><span data-stu-id="94626-179">-not</span></span>|<span data-ttu-id="94626-180">Logische not; keert true en false</span><span class="sxs-lookup"><span data-stu-id="94626-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="94626-181">-niet (1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="94626-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="94626-182">Logische not; keert true en false</span><span class="sxs-lookup"><span data-stu-id="94626-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="94626-183">\!(1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="94626-183">\!(1 -eq 2)</span></span>|

