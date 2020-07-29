---
title: Stoombeheer
description: Power shell biedt methoden om lussen te maken, beslissingen te nemen en de stroom van code in scripts logisch te beheren.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436307"
---
# <a name="chapter-6---flow-control"></a><span data-ttu-id="4816a-103">Hoofd stuk 6-Datatransport besturing</span><span class="sxs-lookup"><span data-stu-id="4816a-103">Chapter 6 - Flow control</span></span>

## <a name="scripting"></a><span data-ttu-id="4816a-104">Script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="4816a-104">Scripting</span></span>

<span data-ttu-id="4816a-105">Wanneer u de Power shell-One-Lines schrijft voor het schrijven van scripts, klinkt het veel ingewik kelder dan echt.</span><span class="sxs-lookup"><span data-stu-id="4816a-105">When you move from writing PowerShell one-liners to writing scripts, it sounds a lot more complicated than it really is.</span></span> <span data-ttu-id="4816a-106">Een script is niets meer dan dezelfde of vergelijk bare opdrachten die u interactief zou uitvoeren in de Power shell-console, behalve dat ze worden opgeslagen als een `.PS1` bestand.</span><span class="sxs-lookup"><span data-stu-id="4816a-106">A script is nothing more than the same or similar commands that you would run interactively in the PowerShell console, except they're saved as a `.PS1` file.</span></span> <span data-ttu-id="4816a-107">Er zijn een aantal script constructies die u kunt gebruiken, zoals een `foreach` lus in plaats van de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4816a-107">There are some scripting constructs that you may use such as a `foreach` loop instead of the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="4816a-108">Voor beginners kunnen de verschillen verwarrend zijn, vooral als u rekening `foreach` houdt met een script constructie en een alias voor de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4816a-108">To beginners, the differences can be confusing especially when you consider that `foreach` is both a scripting construct and an alias for the `ForEach-Object` cmdlet.</span></span>

## <a name="looping"></a><span data-ttu-id="4816a-109">Lussen</span><span class="sxs-lookup"><span data-stu-id="4816a-109">Looping</span></span>

<span data-ttu-id="4816a-110">Een van de fantastische dingen over Power shell is, wanneer u hebt nagegaan hoe u een item kunt uitvoeren, is het bijna net zo eenvoudig om dezelfde taak uit te voeren voor honderden items.</span><span class="sxs-lookup"><span data-stu-id="4816a-110">One of the great things about PowerShell is, once you figure out how to do something for one item, it's almost as easy to do the same task for hundreds of items.</span></span> <span data-ttu-id="4816a-111">Door loop de items met een van de vele verschillende typen lussen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="4816a-111">Simply loop through the items using one of the many different types of loops in PowerShell.</span></span>

### <a name="foreach-object"></a><span data-ttu-id="4816a-112">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="4816a-112">ForEach-Object</span></span>

<span data-ttu-id="4816a-113">`ForEach-Object`is een cmdlet voor het door lopen van items in een pijp lijn, zoals met One-line Power shell.</span><span class="sxs-lookup"><span data-stu-id="4816a-113">`ForEach-Object` is a cmdlet for iterating through items in a pipeline such as with PowerShell one-liners.</span></span> <span data-ttu-id="4816a-114">`ForEach-Object`streamt de objecten via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="4816a-114">`ForEach-Object` streams the objects through the pipeline.</span></span>

<span data-ttu-id="4816a-115">Hoewel de **module** parameter van `Get-Command` meerdere waarden accepteert die teken reeksen zijn, worden deze alleen geaccepteerd via pijplijn invoer door de naam van de eigenschap of via de invoer van para meters.</span><span class="sxs-lookup"><span data-stu-id="4816a-115">Although the **Module** parameter of `Get-Command` accepts multiple values that are strings, it only accepts them via pipeline input by property name or via parameter input.</span></span> <span data-ttu-id="4816a-116">Als ik in het volgende scenario twee teken reeksen wil pipeen op waarde `Get-Command` voor gebruik met de **module** parameter, moet ik de `ForEach-Object` cmdlet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4816a-116">In the following scenario, if I want to pipe two strings by value to `Get-Command` for use with the **Module** parameter, I would need to use the `ForEach-Object` cmdlet.</span></span>

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

<span data-ttu-id="4816a-117">In het vorige voor beeld `$_` is het huidige object.</span><span class="sxs-lookup"><span data-stu-id="4816a-117">In the previous example, `$_` is the current object.</span></span> <span data-ttu-id="4816a-118">Vanaf Power shell versie 3,0 `$PSItem` kan worden gebruikt in plaats van `$_` .</span><span class="sxs-lookup"><span data-stu-id="4816a-118">Beginning with PowerShell version 3.0, `$PSItem` can be used instead of `$_`.</span></span> <span data-ttu-id="4816a-119">Maar ik vind dat de meeste ervaren Power shell-gebruikers nog steeds gebruikmaken `$_` van de voor keur omdat deze compatibel is met het type.</span><span class="sxs-lookup"><span data-stu-id="4816a-119">But I find that most experienced PowerShell users still prefer using `$_` since it's backward compatible and less to type.</span></span>

<span data-ttu-id="4816a-120">Wanneer u het `foreach` tref woord gebruikt, moet u alle items in het geheugen opslaan voordat u deze kunt door lopen. Dit kan lastig zijn als u niet weet hoeveel items u aan het werk hebt.</span><span class="sxs-lookup"><span data-stu-id="4816a-120">When using the `foreach` keyword, you must store all of the items in memory before iterating through them, which could be difficult if you don't know how many items you're working with.</span></span>

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="4816a-121">Vaak een lus zoals `foreach` of `ForEach-Object` is nodig.</span><span class="sxs-lookup"><span data-stu-id="4816a-121">Many times a loop such as `foreach` or `ForEach-Object` is necessary.</span></span> <span data-ttu-id="4816a-122">Anders wordt er een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4816a-122">Otherwise you'll receive an error message.</span></span>

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

<span data-ttu-id="4816a-123">Andere keren, kunt u dezelfde resultaten verkrijgen terwijl de lus helemaal niet meer wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4816a-123">Other times, you can get the same results while eliminating the loop altogether.</span></span> <span data-ttu-id="4816a-124">Raadpleeg de Help van de cmdlet voor meer informatie over uw opties.</span><span class="sxs-lookup"><span data-stu-id="4816a-124">Consult the cmdlet help to understand your options.</span></span>

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="4816a-125">Zoals u in de voor gaande voor beelden kunt zien, accepteert de para meter **Identity** `Get-ADComputer` alleen een enkele waarde wanneer deze wordt opgegeven via de invoer van para meters, maar is het mogelijk om meerdere items toe te staan wanneer de invoer wordt opgegeven via pijplijn invoer.</span><span class="sxs-lookup"><span data-stu-id="4816a-125">As you can see in the previous examples, the **Identity** parameter for `Get-ADComputer` only accepts a single value when provided via parameter input, but it allows for multiple items when the input is provided via pipeline input.</span></span>

### <a name="for"></a><span data-ttu-id="4816a-126">Voor</span><span class="sxs-lookup"><span data-stu-id="4816a-126">For</span></span>

<span data-ttu-id="4816a-127">Een `for` lus wordt herhaald terwijl een opgegeven voor waarde waar is.</span><span class="sxs-lookup"><span data-stu-id="4816a-127">A `for` loop iterates while a specified condition is true.</span></span> <span data-ttu-id="4816a-128">De `for` lus is niet iets dat ik vaak gebruik, maar wel het gebruik ervan.</span><span class="sxs-lookup"><span data-stu-id="4816a-128">The `for` loop is not something that I use often, but it does have its uses.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

<span data-ttu-id="4816a-129">In het vorige voor beeld wordt de lus vier keer herhaald door te beginnen met het cijfer 1 en wordt de teller variabel `$i` kleiner dan 5.</span><span class="sxs-lookup"><span data-stu-id="4816a-129">In the previous example, the loop will iterate four times by starting off with the number one and continue as long as the counter variable `$i` is less than 5.</span></span> <span data-ttu-id="4816a-130">In slaap stand wordt in totaal tien seconden geslapen.</span><span class="sxs-lookup"><span data-stu-id="4816a-130">It will sleep for a total of 10 seconds.</span></span>

### <a name="do"></a><span data-ttu-id="4816a-131">Wel doen</span><span class="sxs-lookup"><span data-stu-id="4816a-131">Do</span></span>

<span data-ttu-id="4816a-132">Er zijn twee verschillende `do` lussen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="4816a-132">There are two different `do` loops in PowerShell.</span></span> <span data-ttu-id="4816a-133">`Do Until`wordt uitgevoerd terwijl de opgegeven voor waarde False is.</span><span class="sxs-lookup"><span data-stu-id="4816a-133">`Do Until` runs while the specified condition is false.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

<span data-ttu-id="4816a-134">Het vorige voor beeld is een nummer dat wordt voortgezet totdat de waarde die u hebt geschat gelijk is aan het nummer dat de `Get-Random` cmdlet heeft gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4816a-134">The previous example is a numbers game that continues until the value you guess equals the same number that the `Get-Random` cmdlet generated.</span></span>

<span data-ttu-id="4816a-135">`Do While`is precies het tegenovergestelde.</span><span class="sxs-lookup"><span data-stu-id="4816a-135">`Do While` is just the opposite.</span></span> <span data-ttu-id="4816a-136">Het wordt uitgevoerd zolang de opgegeven voor waarde resulteert in waar.</span><span class="sxs-lookup"><span data-stu-id="4816a-136">It runs as long as the specified condition evaluates to true.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

<span data-ttu-id="4816a-137">Dezelfde resultaten worden met een lus behaald `Do While` door de test voorwaarde om te keren naar niet gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="4816a-137">The same results are achieved with a `Do While` loop by reversing the test condition to not equals.</span></span>

<span data-ttu-id="4816a-138">`Do`lussen worden altijd ten minste één keer uitgevoerd, omdat de voor waarde aan het einde van de lus wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="4816a-138">`Do` loops always run at least once because the condition is evaluated at the end of the loop.</span></span>

### <a name="while"></a><span data-ttu-id="4816a-139">Het</span><span class="sxs-lookup"><span data-stu-id="4816a-139">While</span></span>

<span data-ttu-id="4816a-140">Net als bij de `Do While` lus wordt een `While` lus uitgevoerd zolang de opgegeven voor waarde waar is.</span><span class="sxs-lookup"><span data-stu-id="4816a-140">Similar to the `Do While` loop, a `While` loop runs as long as the specified condition is true.</span></span> <span data-ttu-id="4816a-141">Het verschil is echter dat een `While` lus de voor waarde aan de bovenkant van de lus evalueert voordat een wille keurige code wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4816a-141">The difference however, is that a `While` loop evaluates the condition at the top of the loop before any code is run.</span></span> <span data-ttu-id="4816a-142">Het wordt dus niet uitgevoerd als de voor waarde resulteert in ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="4816a-142">So it doesn't run if the condition evaluates to false.</span></span>

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

<span data-ttu-id="4816a-143">In het vorige voor beeld wordt berekend op welke dag Thanksgiving Day is in de Verenigde Staten.</span><span class="sxs-lookup"><span data-stu-id="4816a-143">The previous example calculates what day Thanksgiving Day is on in the United States.</span></span> <span data-ttu-id="4816a-144">Het is altijd op de vierde donderdag van november.</span><span class="sxs-lookup"><span data-stu-id="4816a-144">It's always on the fourth Thursday of November.</span></span> <span data-ttu-id="4816a-145">De lus begint dus met de 22 dag van november en voegt een dag toe wanneer de dag van de week niet gelijk is aan donderdag.</span><span class="sxs-lookup"><span data-stu-id="4816a-145">So the loop starts with the 22nd day of November and adds a day while the day of the week isn't equal to Thursday.</span></span> <span data-ttu-id="4816a-146">Als de 22 een donderdag is, wordt de lus helemaal niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4816a-146">If the 22nd is a Thursday, the loop doesn't run at all.</span></span>

## <a name="break-continue-and-return"></a><span data-ttu-id="4816a-147">Onderbreken, door gaan en retour neren</span><span class="sxs-lookup"><span data-stu-id="4816a-147">Break, Continue, and Return</span></span>

<span data-ttu-id="4816a-148">`Break`is ontworpen om een lus te verstoren.</span><span class="sxs-lookup"><span data-stu-id="4816a-148">`Break` is designed to break out of a loop.</span></span> <span data-ttu-id="4816a-149">Het wordt ook vaak gebruikt met de `switch` instructie.</span><span class="sxs-lookup"><span data-stu-id="4816a-149">It's also commonly used with the `switch` statement.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

<span data-ttu-id="4816a-150">De `break` instructie die in het vorige voor beeld wordt weer gegeven, zorgt ervoor dat de lus wordt afgesloten bij de eerste iteratie.</span><span class="sxs-lookup"><span data-stu-id="4816a-150">The `break` statement shown in the previous example causes the loop to exit on the first iteration.</span></span>

<span data-ttu-id="4816a-151">Door gaan is ontworpen om naar de volgende herhaling van een lus over te slaan.</span><span class="sxs-lookup"><span data-stu-id="4816a-151">Continue is designed to skip to the next iteration of a loop.</span></span>

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

<span data-ttu-id="4816a-152">In het vorige voor beeld worden de getallen 1, 2, 4 en 5 uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4816a-152">The previous example will output the numbers 1, 2, 4, and 5.</span></span> <span data-ttu-id="4816a-153">Nummer 3 wordt overgeslagen en gaat verder met de volgende herhaling van de lus.</span><span class="sxs-lookup"><span data-stu-id="4816a-153">It skips number 3 and continues with the next iteration of the loop.</span></span> <span data-ttu-id="4816a-154">Vergelijkbaar met `break` , wordt `continue` de lus onderbroken, behalve alleen voor de huidige iteratie.</span><span class="sxs-lookup"><span data-stu-id="4816a-154">Similar to `break`, `continue` breaks out of the loop except only for the current iteration.</span></span> <span data-ttu-id="4816a-155">De uitvoering wordt voortgezet met de volgende iteratie in plaats van de lus af te breken en te stoppen.</span><span class="sxs-lookup"><span data-stu-id="4816a-155">Execution continues with the next iteration instead of breaking out of the loop and stopping.</span></span>

<span data-ttu-id="4816a-156">Retour is ontworpen om uit te sluiten van de bestaande scope.</span><span class="sxs-lookup"><span data-stu-id="4816a-156">Return is designed to exit out of the existing scope.</span></span>

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

<span data-ttu-id="4816a-157">U ziet dat in het vorige voor beeld het eerste resultaat wordt geretourneerd en vervolgens uit de lus bestaat.</span><span class="sxs-lookup"><span data-stu-id="4816a-157">Notice that in the previous example, return outputs the first result and then exists out of the loop.</span></span> <span data-ttu-id="4816a-158">Een uitgebreidere uitleg van de resultaten verklaring vindt u in een van mijn blog artikelen: [' het Power shell-retour trefwoord '][].</span><span class="sxs-lookup"><span data-stu-id="4816a-158">A more thorough explanation of the result statement can be found in one of my blog articles: ["The PowerShell return keyword"][].</span></span>

## <a name="summary"></a><span data-ttu-id="4816a-159">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="4816a-159">Summary</span></span>

<span data-ttu-id="4816a-160">In dit hoofd stuk hebt u geleerd over de verschillende typen lussen die voor komen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="4816a-160">In this chapter, you've learned about the different types of loops that exist in PowerShell.</span></span>

## <a name="review"></a><span data-ttu-id="4816a-161">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="4816a-161">Review</span></span>

1. <span data-ttu-id="4816a-162">Wat is het verschil in de `ForEach-Object` cmdlet en de script constructie foreach?</span><span class="sxs-lookup"><span data-stu-id="4816a-162">What is the difference in the `ForEach-Object` cmdlet and the foreach scripting construct?</span></span>
1. <span data-ttu-id="4816a-163">Wat is het belangrijkste voor deel van het gebruik van een while-lus in plaats van een do while-of do until-lus.</span><span class="sxs-lookup"><span data-stu-id="4816a-163">What is the primary advantage of using a While loop instead of a Do While or Do Until loop.</span></span>
1. <span data-ttu-id="4816a-164">Wat is het verschil tussen de instructies voor onderbreken en hervatten?</span><span class="sxs-lookup"><span data-stu-id="4816a-164">How do the break and continue statements differ?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="4816a-165">Aanbevolen Lees bewerkingen</span><span class="sxs-lookup"><span data-stu-id="4816a-165">Recommended Reading</span></span>

- <span data-ttu-id="4816a-166">[ForEach-object][]</span><span class="sxs-lookup"><span data-stu-id="4816a-166">[ForEach-Object][]</span></span>
- <span data-ttu-id="4816a-167">[about_ForEach][]</span><span class="sxs-lookup"><span data-stu-id="4816a-167">[about_ForEach][]</span></span>
- <span data-ttu-id="4816a-168">[about_For][]</span><span class="sxs-lookup"><span data-stu-id="4816a-168">[about_For][]</span></span>
- <span data-ttu-id="4816a-169">[about_Do][]</span><span class="sxs-lookup"><span data-stu-id="4816a-169">[about_Do][]</span></span>
- <span data-ttu-id="4816a-170">[about_While][]</span><span class="sxs-lookup"><span data-stu-id="4816a-170">[about_While][]</span></span>
- <span data-ttu-id="4816a-171">[about_Break][]</span><span class="sxs-lookup"><span data-stu-id="4816a-171">[about_Break][]</span></span>
- <span data-ttu-id="4816a-172">[about_Continue][]</span><span class="sxs-lookup"><span data-stu-id="4816a-172">[about_Continue][]</span></span>
- <span data-ttu-id="4816a-173">[about_Return][]</span><span class="sxs-lookup"><span data-stu-id="4816a-173">[about_Return][]</span></span>

<!-- link references -->
[ForEach-object]: /powershell/module/microsoft.powershell.core/foreach-object
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
["Het Power shell-retour trefwoord"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
["The PowerShell return keyword"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/