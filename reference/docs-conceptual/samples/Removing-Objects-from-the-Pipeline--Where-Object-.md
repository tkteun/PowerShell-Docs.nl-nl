---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Objecten verwijderen uit de pijp lijn waarbij het object
ms.openlocfilehash: c47efd38e2ff40ce3b7bf50b161cc38de922c5da
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030877"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="a190c-103">Objecten uit de pijp lijn verwijderen (where-object)</span><span class="sxs-lookup"><span data-stu-id="a190c-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="a190c-104">In Windows Power shell genereert u vaak meerdere objecten naar een pijp lijn dan u wilt.</span><span class="sxs-lookup"><span data-stu-id="a190c-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="a190c-105">U kunt de eigenschappen van bepaalde objecten opgeven die moeten worden weer gegeven met de **Format** -cmdlets, maar dit biedt geen ondersteuning voor het probleem van het verwijderen van volledige objecten uit de weer gave.</span><span class="sxs-lookup"><span data-stu-id="a190c-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="a190c-106">Misschien wilt u objecten filteren vóór het einde van een pijp lijn, zodat u alleen acties kunt uitvoeren op een subset van de eerste gegenereerde objecten.</span><span class="sxs-lookup"><span data-stu-id="a190c-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="a190c-107">Windows Power shell bevat een `Where-Object`-cmdlet waarmee u elk object in de pijp lijn kunt testen en dit alleen door geven aan de pijp lijn als het voldoet aan een bepaalde test voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="a190c-107">Windows PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="a190c-108">Objecten die de test niet door lopen, worden uit de pijp lijn verwijderd.</span><span class="sxs-lookup"><span data-stu-id="a190c-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="a190c-109">U geeft de test voorwaarde op als de waarde van de para meter `Where-Object` **FilterScript** .</span><span class="sxs-lookup"><span data-stu-id="a190c-109">You supply the test condition as the value of the `Where-Object` **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="a190c-110">Eenvoudige tests uitvoeren met where-object</span><span class="sxs-lookup"><span data-stu-id="a190c-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="a190c-111">De waarde van **FilterScript** is een *script blok* : een of meer Windows Power shell-opdrachten omgeven door accolades {}-dat resulteert in waar of onwaar.</span><span class="sxs-lookup"><span data-stu-id="a190c-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="a190c-112">Deze script blokken kunnen zeer eenvoudig zijn, maar het maken ervan vereist dat u weet wat een ander Windows Power shell-concept, vergelijkings operators is.</span><span class="sxs-lookup"><span data-stu-id="a190c-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="a190c-113">Een vergelijkings operator vergelijkt de items die aan elkaar worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a190c-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="a190c-114">Vergelijkings operatoren beginnen met een '-'-teken en worden gevolgd door een naam.</span><span class="sxs-lookup"><span data-stu-id="a190c-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="a190c-115">Eenvoudige vergelijkings operators werken aan bijna elk soort object.</span><span class="sxs-lookup"><span data-stu-id="a190c-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="a190c-116">De geavanceerde vergelijkings operators kunnen alleen werken met tekst of matrices.</span><span class="sxs-lookup"><span data-stu-id="a190c-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="a190c-117">Wanneer u werkt met tekst, zijn Windows Power shell-vergelijkings operatoren standaard niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="a190c-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="a190c-118">Als gevolg van het parseren van overwegingen, zoals <, > en =, worden niet gebruikt als vergelijkings operators.</span><span class="sxs-lookup"><span data-stu-id="a190c-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="a190c-119">In plaats daarvan bestaan vergelijkings operatoren uit letters.</span><span class="sxs-lookup"><span data-stu-id="a190c-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="a190c-120">De basis-vergelijkings operatoren worden weer gegeven in de volgende tabel.</span><span class="sxs-lookup"><span data-stu-id="a190c-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="a190c-121">Vergelijkingsoperator</span><span class="sxs-lookup"><span data-stu-id="a190c-121">Comparison Operator</span></span>|<span data-ttu-id="a190c-122">Betekenis</span><span class="sxs-lookup"><span data-stu-id="a190c-122">Meaning</span></span>|<span data-ttu-id="a190c-123">Voor beeld (retourneert waar)</span><span class="sxs-lookup"><span data-stu-id="a190c-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="a190c-124">-eq</span><span class="sxs-lookup"><span data-stu-id="a190c-124">-eq</span></span>|<span data-ttu-id="a190c-125">is gelijk aan</span><span class="sxs-lookup"><span data-stu-id="a190c-125">is equal to</span></span>|<span data-ttu-id="a190c-126">1-EQ 1</span><span class="sxs-lookup"><span data-stu-id="a190c-126">1 -eq 1</span></span>|
|<span data-ttu-id="a190c-127">-ne</span><span class="sxs-lookup"><span data-stu-id="a190c-127">-ne</span></span>|<span data-ttu-id="a190c-128">Is niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="a190c-128">Is not equal to</span></span>|<span data-ttu-id="a190c-129">1-ne 2</span><span class="sxs-lookup"><span data-stu-id="a190c-129">1 -ne 2</span></span>|
|<span data-ttu-id="a190c-130">-lt</span><span class="sxs-lookup"><span data-stu-id="a190c-130">-lt</span></span>|<span data-ttu-id="a190c-131">Is kleiner dan</span><span class="sxs-lookup"><span data-stu-id="a190c-131">Is less than</span></span>|<span data-ttu-id="a190c-132">1-lt 2</span><span class="sxs-lookup"><span data-stu-id="a190c-132">1 -lt 2</span></span>|
|<span data-ttu-id="a190c-133">-Le</span><span class="sxs-lookup"><span data-stu-id="a190c-133">-le</span></span>|<span data-ttu-id="a190c-134">is kleiner dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="a190c-134">Is less than or equal to</span></span>|<span data-ttu-id="a190c-135">1-Le 2</span><span class="sxs-lookup"><span data-stu-id="a190c-135">1 -le 2</span></span>|
|<span data-ttu-id="a190c-136">-gt</span><span class="sxs-lookup"><span data-stu-id="a190c-136">-gt</span></span>|<span data-ttu-id="a190c-137">Is groter dan</span><span class="sxs-lookup"><span data-stu-id="a190c-137">Is greater than</span></span>|<span data-ttu-id="a190c-138">2-gt 1</span><span class="sxs-lookup"><span data-stu-id="a190c-138">2 -gt 1</span></span>|
|<span data-ttu-id="a190c-139">-ge</span><span class="sxs-lookup"><span data-stu-id="a190c-139">-ge</span></span>|<span data-ttu-id="a190c-140">is groter dan of gelijk zijn aan</span><span class="sxs-lookup"><span data-stu-id="a190c-140">Is greater than or equal to</span></span>|<span data-ttu-id="a190c-141">2-ge 1</span><span class="sxs-lookup"><span data-stu-id="a190c-141">2 -ge 1</span></span>|
|<span data-ttu-id="a190c-142">-like</span><span class="sxs-lookup"><span data-stu-id="a190c-142">-like</span></span>|<span data-ttu-id="a190c-143">Is vergelijkbaar (vergelijking van joker tekens voor tekst)</span><span class="sxs-lookup"><span data-stu-id="a190c-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="a190c-144">"file. doc"-like "f\*. do?"</span><span class="sxs-lookup"><span data-stu-id="a190c-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="a190c-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="a190c-145">-notlike</span></span>|<span data-ttu-id="a190c-146">Is niet hetzelfde (vergelijking van joker tekens voor tekst)</span><span class="sxs-lookup"><span data-stu-id="a190c-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="a190c-147">"file. doc"-notlike "p\*. doc"</span><span class="sxs-lookup"><span data-stu-id="a190c-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="a190c-148">-bevat</span><span class="sxs-lookup"><span data-stu-id="a190c-148">-contains</span></span>|<span data-ttu-id="a190c-149">bevat</span><span class="sxs-lookup"><span data-stu-id="a190c-149">Contains</span></span>|<span data-ttu-id="a190c-150">1, 2, 3-bevat 1</span><span class="sxs-lookup"><span data-stu-id="a190c-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="a190c-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="a190c-151">-notcontains</span></span>|<span data-ttu-id="a190c-152">Bevat niet</span><span class="sxs-lookup"><span data-stu-id="a190c-152">Does not contain</span></span>|<span data-ttu-id="a190c-153">1, 2, 3-notcontains 4</span><span class="sxs-lookup"><span data-stu-id="a190c-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="a190c-154">Where-object-script blokken gebruiken de speciale variabele `$_` om te verwijzen naar het huidige object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="a190c-154">Where-Object script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="a190c-155">Hier volgt een voor beeld van hoe het werkt.</span><span class="sxs-lookup"><span data-stu-id="a190c-155">Here is an example of how it works.</span></span> <span data-ttu-id="a190c-156">Als u een lijst met getallen hebt en alleen de waarden wilt retour neren die kleiner zijn dan 3, kunt u WHERE-object gebruiken om de getallen te filteren door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="a190c-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="a190c-157">Filteren op basis van object eigenschappen</span><span class="sxs-lookup"><span data-stu-id="a190c-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="a190c-158">Omdat `$_` naar het huidige pijplijn object verwijst, hebben we toegang tot de eigenschappen van de tests.</span><span class="sxs-lookup"><span data-stu-id="a190c-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="a190c-159">U kunt bijvoorbeeld de klasse Win32_SystemDriver in WMI bekijken.</span><span class="sxs-lookup"><span data-stu-id="a190c-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="a190c-160">Er zijn mogelijk honderden systeem Stuur Programma's op een bepaald systeem, maar u bent mogelijk alleen geïnteresseerd in een bepaalde set van de systeem Stuur Programma's, zoals die op dit moment worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a190c-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="a190c-161">Als u Get-member gebruikt om Win32_SystemDriver leden te bekijken (**Get-WmiObject-Class Win32_SystemDriver | Get-member-member type-eigenschap**) u ziet dat de relevante eigenschap status is en dat deze de waarde ' running ' heeft wanneer het stuur programma wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a190c-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="a190c-162">U kunt de systeem Stuur Programma's filteren en alleen de actieve items selecteren door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="a190c-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="a190c-163">Er wordt nog steeds een lange lijst gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="a190c-163">This still produces a long list.</span></span> <span data-ttu-id="a190c-164">U kunt filteren op alleen de ingestelde Stuur Programma's selecteren om automatisch te starten door de start modus-waarde te testen:</span><span class="sxs-lookup"><span data-stu-id="a190c-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

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

<span data-ttu-id="a190c-165">Dit biedt ons veel informatie die we niet meer nodig hebben omdat we weten dat de Stuur Programma's worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a190c-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="a190c-166">De enige informatie die we waarschijnlijk op dit moment nodig hebben, zijn de naam en de weergave naam.</span><span class="sxs-lookup"><span data-stu-id="a190c-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="a190c-167">De volgende opdracht bevat alleen die twee eigenschappen, wat resulteert in veel eenvoudiger uitvoer:</span><span class="sxs-lookup"><span data-stu-id="a190c-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

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

<span data-ttu-id="a190c-168">Er zijn twee where-object elementen in de bovenstaande opdracht, maar ze kunnen worden uitgedrukt in één where-object-element met behulp van de-en logische operator, zoals:</span><span class="sxs-lookup"><span data-stu-id="a190c-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="a190c-169">De standaard logische Opera tors worden weer gegeven in de volgende tabel.</span><span class="sxs-lookup"><span data-stu-id="a190c-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="a190c-170">Logische operator</span><span class="sxs-lookup"><span data-stu-id="a190c-170">Logical Operator</span></span>|<span data-ttu-id="a190c-171">Betekenis</span><span class="sxs-lookup"><span data-stu-id="a190c-171">Meaning</span></span>|<span data-ttu-id="a190c-172">Voor beeld (retourneert waar)</span><span class="sxs-lookup"><span data-stu-id="a190c-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="a190c-173">-en</span><span class="sxs-lookup"><span data-stu-id="a190c-173">-and</span></span>|<span data-ttu-id="a190c-174">Logische en; waar als beide zijden waar zijn</span><span class="sxs-lookup"><span data-stu-id="a190c-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="a190c-175">(1-EQ 1)-en (2-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="a190c-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="a190c-176">-of</span><span class="sxs-lookup"><span data-stu-id="a190c-176">-or</span></span>|<span data-ttu-id="a190c-177">Logische of; waar als een van beide zijden waar is</span><span class="sxs-lookup"><span data-stu-id="a190c-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="a190c-178">(1-EQ 1)-of (1-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="a190c-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="a190c-179">-niet</span><span class="sxs-lookup"><span data-stu-id="a190c-179">-not</span></span>|<span data-ttu-id="a190c-180">Logische niet; keert waar en ONWAAR om</span><span class="sxs-lookup"><span data-stu-id="a190c-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="a190c-181">-niet (1-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="a190c-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="a190c-182">Logische niet; keert waar en ONWAAR om</span><span class="sxs-lookup"><span data-stu-id="a190c-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="a190c-183">\!(1-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="a190c-183">\!(1 -eq 2)</span></span>|
