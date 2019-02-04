---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Objecten uit de pijplijn verwijderen Where-Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: c060b93a3823be26ad6c7757acc633bb4fc2fcfa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685723"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="03906-103">Objecten verwijderen uit de pijplijn (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="03906-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="03906-104">In Windows PowerShell kunt u vaak genereren en geven meer objecten voor een pijplijn dan u wilt.</span><span class="sxs-lookup"><span data-stu-id="03906-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="03906-105">Kunt u de eigenschappen van bepaalde objecten om weer te geven met behulp van de **indeling** cmdlets, maar dit niet helpt met het probleem van het gehele objecten verwijderen uit de weergave.</span><span class="sxs-lookup"><span data-stu-id="03906-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="03906-106">U wilt filteren objecten vóór het einde van een pijplijn, zodat u acties op slechts een subset van de objecten in eerste instantie gegenereerd uitvoeren kunt.</span><span class="sxs-lookup"><span data-stu-id="03906-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="03906-107">Windows PowerShell bevat een `Where-Object` u elk object in de pijplijn testen en alleen langs de pijplijn te doorgeven kunt als deze voldoet aan de voorwaarde van een bepaalde test-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03906-107">Windows PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="03906-108">Objecten die niet door de test worden verwijderd uit de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="03906-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="03906-109">U de testvoorwaarde opgeven als de waarde van de `Where-Object` **FilterScript** parameter.</span><span class="sxs-lookup"><span data-stu-id="03906-109">You supply the test condition as the value of the `Where-Object` **FilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="03906-110">Uitvoeren van eenvoudige tests uit met het Where-Object</span><span class="sxs-lookup"><span data-stu-id="03906-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="03906-111">De waarde van **FilterScript** is een *scriptblok* -een of meer Windows PowerShell-opdrachten omgeven door accolades {} -die wordt geëvalueerd op waar of ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="03906-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="03906-112">Deze scriptblokken kunnen zeer eenvoudig, maar ze worden gemaakt moet weten over andere Windows PowerShell-concept, vergelijkingsoperators.</span><span class="sxs-lookup"><span data-stu-id="03906-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="03906-113">Een vergelijkingsoperator vergelijkt de items die worden weergegeven voor elke zijde van het.</span><span class="sxs-lookup"><span data-stu-id="03906-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="03906-114">Vergelijkingsoperators beginnen met een '-' teken en worden gevolgd door een naam.</span><span class="sxs-lookup"><span data-stu-id="03906-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="03906-115">Basic vergelijkingsoperators werken op vrijwel elk soort object.</span><span class="sxs-lookup"><span data-stu-id="03906-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="03906-116">De meer geavanceerde vergelijkingsoperators kunnen uitsluitend worden gebruikt voor tekst- of -matrices.</span><span class="sxs-lookup"><span data-stu-id="03906-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="03906-117">Windows PowerShell-vergelijkingsoperators zijn standaard bij het werken met tekst, niet hoofdlettergevoelig.</span><span class="sxs-lookup"><span data-stu-id="03906-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="03906-118">Vanwege het parseren van overwegingen, symbolen zoals <>, en = niet als vergelijkingsoperators worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="03906-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="03906-119">In plaats daarvan vergelijkingsoperators bestaan uit letters.</span><span class="sxs-lookup"><span data-stu-id="03906-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="03906-120">De basic vergelijkingsoperators worden weergegeven in de volgende tabel.</span><span class="sxs-lookup"><span data-stu-id="03906-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="03906-121">Vergelijkingsoperator</span><span class="sxs-lookup"><span data-stu-id="03906-121">Comparison Operator</span></span>|<span data-ttu-id="03906-122">Betekenis</span><span class="sxs-lookup"><span data-stu-id="03906-122">Meaning</span></span>|<span data-ttu-id="03906-123">Voorbeeld (retourneert ' True ')</span><span class="sxs-lookup"><span data-stu-id="03906-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="03906-124">-eq</span><span class="sxs-lookup"><span data-stu-id="03906-124">-eq</span></span>|<span data-ttu-id="03906-125">is gelijk aan</span><span class="sxs-lookup"><span data-stu-id="03906-125">is equal to</span></span>|<span data-ttu-id="03906-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="03906-126">1 -eq 1</span></span>|
|<span data-ttu-id="03906-127">-ne</span><span class="sxs-lookup"><span data-stu-id="03906-127">-ne</span></span>|<span data-ttu-id="03906-128">Is niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="03906-128">Is not equal to</span></span>|<span data-ttu-id="03906-129">1 - ne 2</span><span class="sxs-lookup"><span data-stu-id="03906-129">1 -ne 2</span></span>|
|<span data-ttu-id="03906-130">-lt</span><span class="sxs-lookup"><span data-stu-id="03906-130">-lt</span></span>|<span data-ttu-id="03906-131">is kleiner dan</span><span class="sxs-lookup"><span data-stu-id="03906-131">Is less than</span></span>|<span data-ttu-id="03906-132">1 - lt 2</span><span class="sxs-lookup"><span data-stu-id="03906-132">1 -lt 2</span></span>|
|<span data-ttu-id="03906-133">-le</span><span class="sxs-lookup"><span data-stu-id="03906-133">-le</span></span>|<span data-ttu-id="03906-134">Is kleiner dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="03906-134">Is less than or equal to</span></span>|<span data-ttu-id="03906-135">1 - le 2</span><span class="sxs-lookup"><span data-stu-id="03906-135">1 -le 2</span></span>|
|<span data-ttu-id="03906-136">-gt</span><span class="sxs-lookup"><span data-stu-id="03906-136">-gt</span></span>|<span data-ttu-id="03906-137">is groter dan</span><span class="sxs-lookup"><span data-stu-id="03906-137">Is greater than</span></span>|<span data-ttu-id="03906-138">2 - gt 1</span><span class="sxs-lookup"><span data-stu-id="03906-138">2 -gt 1</span></span>|
|<span data-ttu-id="03906-139">-ge</span><span class="sxs-lookup"><span data-stu-id="03906-139">-ge</span></span>|<span data-ttu-id="03906-140">Is groter dan of gelijk zijn aan</span><span class="sxs-lookup"><span data-stu-id="03906-140">Is greater than or equal to</span></span>|<span data-ttu-id="03906-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="03906-141">2 -ge 1</span></span>|
|<span data-ttu-id="03906-142">-like</span><span class="sxs-lookup"><span data-stu-id="03906-142">-like</span></span>|<span data-ttu-id="03906-143">Is vergelijkbaar met (vergelijking van jokertekens voor tekst)</span><span class="sxs-lookup"><span data-stu-id="03906-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="03906-144">"bestand.doc"-, zoals ' f\*basisbedrijfstoepassingen? "</span><span class="sxs-lookup"><span data-stu-id="03906-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="03906-145">-notlike zijn</span><span class="sxs-lookup"><span data-stu-id="03906-145">-notlike</span></span>|<span data-ttu-id="03906-146">Is niet als (vergelijking van jokertekens voor tekst)</span><span class="sxs-lookup"><span data-stu-id="03906-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="03906-147">"bestand.doc"-notlike zijn "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="03906-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="03906-148">-bevat</span><span class="sxs-lookup"><span data-stu-id="03906-148">-contains</span></span>|<span data-ttu-id="03906-149">bevat</span><span class="sxs-lookup"><span data-stu-id="03906-149">Contains</span></span>|<span data-ttu-id="03906-150">1,2,3 - 1 bevat</span><span class="sxs-lookup"><span data-stu-id="03906-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="03906-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="03906-151">-notcontains</span></span>|<span data-ttu-id="03906-152">bevat niet</span><span class="sxs-lookup"><span data-stu-id="03906-152">Does not contain</span></span>|<span data-ttu-id="03906-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="03906-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="03906-154">WHERE-Object-scriptblokken de speciale variabele gebruiken `$_` om te verwijzen naar het huidige object in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="03906-154">Where-Object script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="03906-155">Hier volgt een voorbeeld van hoe het werkt.</span><span class="sxs-lookup"><span data-stu-id="03906-155">Here is an example of how it works.</span></span> <span data-ttu-id="03906-156">Als u een lijst met getallen hebben en alleen wilt retourneren die minder dan 3 zijn, kunt u Where-Object voor het filteren van de getallen door te typen:</span><span class="sxs-lookup"><span data-stu-id="03906-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="03906-157">Filteren op basis van eigenschappen van het Object</span><span class="sxs-lookup"><span data-stu-id="03906-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="03906-158">Aangezien `$_` verwijst naar de huidige pipeline-object, hebben we toegang tot de eigenschappen voor onze tests.</span><span class="sxs-lookup"><span data-stu-id="03906-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="03906-159">Als u bijvoorbeeld kunt kijken we de klasse Win32_SystemDriver in WMI.</span><span class="sxs-lookup"><span data-stu-id="03906-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="03906-160">Er zijn mogelijk honderden stuurprogramma's op een bepaald systeem, maar u alleen mogelijk ook geïnteresseerd in een bepaalde set de systeem-stuurprogramma's, zoals die momenteel worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="03906-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="03906-161">Als u een Get-Member kunt Win32_SystemDriver leden weergeven (**Get-WmiObject-klasse Win32_SystemDriver | De eigenschap Get-Member - MemberType**) ziet u dat de relevante eigenschap status is en dat er een waarde van het 'Uitvoeren' als het stuurprogramma wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="03906-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="03906-162">U kunt de stuurprogramma's, filteren selecteren alleen de actieve door door te typen:</span><span class="sxs-lookup"><span data-stu-id="03906-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="03906-163">Dit levert nog steeds een lange lijst.</span><span class="sxs-lookup"><span data-stu-id="03906-163">This still produces a long list.</span></span> <span data-ttu-id="03906-164">U wilt filteren zodat alleen de stuurprogramma's automatisch worden gestart door de waarde van StartMode ook testen selecteren:</span><span class="sxs-lookup"><span data-stu-id="03906-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

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

<span data-ttu-id="03906-165">Dit biedt ons een grote hoeveelheid informatie die we niet langer nodig hebt omdat we weten dat de stuurprogramma's worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="03906-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="03906-166">De enige informatie die we waarschijnlijk nodig hebt op dit moment zijn in feite de naam en de weergavenaam.</span><span class="sxs-lookup"><span data-stu-id="03906-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="03906-167">De volgende opdracht bevat alleen deze twee eigenschappen, wat resulteert in veel eenvoudiger uitvoer:</span><span class="sxs-lookup"><span data-stu-id="03906-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

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

<span data-ttu-id="03906-168">Er zijn twee Where-Object-elementen in de bovenstaande opdracht, maar ze kunnen worden uitgedrukt in één element Where-Object met behulp van de - en de logische operator, als volgt:</span><span class="sxs-lookup"><span data-stu-id="03906-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="03906-169">De standaard logische operators worden weergegeven in de volgende tabel.</span><span class="sxs-lookup"><span data-stu-id="03906-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="03906-170">Logische Operator</span><span class="sxs-lookup"><span data-stu-id="03906-170">Logical Operator</span></span>|<span data-ttu-id="03906-171">Betekenis</span><span class="sxs-lookup"><span data-stu-id="03906-171">Meaning</span></span>|<span data-ttu-id="03906-172">Voorbeeld (retourneert ' True ')</span><span class="sxs-lookup"><span data-stu-id="03906-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="03906-173">- en</span><span class="sxs-lookup"><span data-stu-id="03906-173">-and</span></span>|<span data-ttu-id="03906-174">Logische en; ' True ' als beide kanten ' True ' zijn</span><span class="sxs-lookup"><span data-stu-id="03906-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="03906-175">(1 - eq 1) - en (2 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="03906-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="03906-176">- of</span><span class="sxs-lookup"><span data-stu-id="03906-176">-or</span></span>|<span data-ttu-id="03906-177">Logische of; ' True ' als beide kanten ingesteld op true is</span><span class="sxs-lookup"><span data-stu-id="03906-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="03906-178">(1 - eq 1) - of (1 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="03906-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="03906-179">-niet</span><span class="sxs-lookup"><span data-stu-id="03906-179">-not</span></span>|<span data-ttu-id="03906-180">Logische not; keert de waarde true en false</span><span class="sxs-lookup"><span data-stu-id="03906-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="03906-181">-geen (1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="03906-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="03906-182">Logische not; keert de waarde true en false</span><span class="sxs-lookup"><span data-stu-id="03906-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="03906-183">\!(1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="03906-183">\!(1 -eq 2)</span></span>|
