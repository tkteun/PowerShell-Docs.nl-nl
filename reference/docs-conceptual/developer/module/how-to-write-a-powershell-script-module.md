---
title: Een Power shell-script module schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352897"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="85626-102">Een PowerShell-scriptmodule schrijven</span><span class="sxs-lookup"><span data-stu-id="85626-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="85626-103">Een script module is in wezen een geldig Power shell-script dat is opgeslagen in de extensie. psm1.</span><span class="sxs-lookup"><span data-stu-id="85626-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="85626-104">Met deze uitbrei ding kan de Power shell-engine gebruikmaken van een aantal regels en cmdlets in uw bestand.</span><span class="sxs-lookup"><span data-stu-id="85626-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="85626-105">De meeste van deze mogelijkheden zijn er om u te helpen bij het installeren van uw code op andere systemen en voor het beheren van scopes.</span><span class="sxs-lookup"><span data-stu-id="85626-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="85626-106">U kunt ook een manifest bestand van een module gebruiken, waarmee u nog complexe installaties en oplossingen kunt beschrijven.</span><span class="sxs-lookup"><span data-stu-id="85626-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="85626-107">Een Power shell-script module schrijven</span><span class="sxs-lookup"><span data-stu-id="85626-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="85626-108">U maakt een script module door een geldig Power shell-script op te slaan in een. psm1-bestand en het bestand vervolgens op te slaan in een map die zich in de directory bevindt waarin Power shell deze kan vinden.</span><span class="sxs-lookup"><span data-stu-id="85626-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="85626-109">In deze map kunt u ook resources plaatsen die u nodig hebt om uw script uit te voeren, evenals een manifest bestand dat beschrijft hoe de module werkt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="85626-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="85626-110">Een eenvoudige Power shell-module maken</span><span class="sxs-lookup"><span data-stu-id="85626-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="85626-111">Maak een bestaand Power shell-script en sla het script op met de extensie. psm1.</span><span class="sxs-lookup"><span data-stu-id="85626-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="85626-112">Het opslaan van een script met de extensie. psm1 betekent dat u de module-cmdlets, zoals [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="85626-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="85626-113">Deze cmdlets bestaan voornamelijk, zodat u uw code eenvoudig kunt importeren en exporteren naar de systemen van andere gebruikers.</span><span class="sxs-lookup"><span data-stu-id="85626-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="85626-114">(De alternatieve oplossing is het laden van uw code op andere systemen en vervolgens punt-bron in actief geheugen, wat geen bijzonder schaal bare oplossing is.) Zie de sectie module- **cmdlets en variabelen** in [Windows Power shell-modules](./understanding-a-windows-powershell-module.md) voor meer informatie. alle functies in uw script zijn standaard toegankelijk voor gebruikers die uw. psm1-bestand importeren, maar eigenschappen zijn niet.</span><span class="sxs-lookup"><span data-stu-id="85626-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="85626-115">Aan het einde van dit onderwerp vindt u een voor beeld van een Power shell-script met de titel `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="85626-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. <span data-ttu-id="85626-116">Als u de gebruikers toegang tot bepaalde functies of eigenschappen wilt beheren, roept u [export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) aan het einde van uw script aan.</span><span class="sxs-lookup"><span data-stu-id="85626-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="85626-117">De voorbeeld code aan de onderkant van de pagina heeft slechts één functie die standaard wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="85626-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="85626-118">Het wordt echter aangeraden om de functies die u wilt weer geven expliciet aan te roepen, zoals beschreven in de volgende code:</span><span class="sxs-lookup"><span data-stu-id="85626-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="85626-119">U kunt ook beperken wat wordt geïmporteerd met behulp van een module manifest.</span><span class="sxs-lookup"><span data-stu-id="85626-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="85626-120">Zie [een Power shell-module importeren](./importing-a-powershell-module.md) en [een Power shell-module manifest schrijven](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="85626-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="85626-121">Als u modules hebt waarvoor uw eigen module moet worden geladen, kunt u deze gebruiken met een aanroep van `Import-Module`, bovenin uw eigen module.</span><span class="sxs-lookup"><span data-stu-id="85626-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="85626-122">`Import-Module` is een cmdlet waarmee een doel module op een systeem wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85626-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="85626-123">Daarom wordt het ook op een later tijdstip in de procedure gebruikt om ook uw eigen module te installeren.</span><span class="sxs-lookup"><span data-stu-id="85626-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="85626-124">In de voorbeeld code onder aan deze pagina worden geen import modules gebruikt.</span><span class="sxs-lookup"><span data-stu-id="85626-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="85626-125">Als dat wel het geval is, wordt deze boven aan het bestand weer gegeven, zoals beschreven in de volgende code:</span><span class="sxs-lookup"><span data-stu-id="85626-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="85626-126">Als u de module wilt beschrijven in het Help-systeem van Power shell, kunt u standaard opmerkingen voor de Help in het bestand gebruiken of een extra Help-bestand maken.</span><span class="sxs-lookup"><span data-stu-id="85626-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="85626-127">Het code voorbeeld onder in dit onderwerp bevat de Help-informatie in de opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="85626-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="85626-128">U kunt ook uitgebreide XML-bestanden schrijven die extra Help-inhoud bevatten.</span><span class="sxs-lookup"><span data-stu-id="85626-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="85626-129">Zie hulp bij het [schrijven van Help voor Windows Power shell-modules](./writing-help-for-windows-powershell-modules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="85626-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="85626-130">Als u meer modules, XML-bestanden of andere inhoud die u wilt inpakken met uw module, kunt u dit doen met een module manifest.</span><span class="sxs-lookup"><span data-stu-id="85626-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="85626-131">Een module manifest is een bestand met de namen van andere modules, Directory-indelingen, versie nummers, auteurgegevens en andere stukjes informatie.</span><span class="sxs-lookup"><span data-stu-id="85626-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="85626-132">Power shell gebruikt het manifest bestand van de module om uw oplossing te organiseren en te implementeren.</span><span class="sxs-lookup"><span data-stu-id="85626-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="85626-133">Vanwege de relatief eenvoudige aard van dit voor beeld was er echter geen manifest bestand nodig.</span><span class="sxs-lookup"><span data-stu-id="85626-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="85626-134">Zie [module manifests](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="85626-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="85626-135">Als u uw module wilt installeren en uitvoeren, slaat u de module op in een van de juiste Power shell-paden en maakt u een aanroep naar `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="85626-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="85626-136">De paden waar u uw module kunt installeren, bevinden zich in de globale variabele `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="85626-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="85626-137">Een gemeen schappelijk pad om een module op een systeem op te slaan, zou bijvoorbeeld `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>` zijn.</span><span class="sxs-lookup"><span data-stu-id="85626-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="85626-138">Zorg ervoor dat u een map maakt voor uw module, zelfs als deze slechts één. psm1-bestand is.</span><span class="sxs-lookup"><span data-stu-id="85626-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="85626-139">Als u de module niet hebt opgeslagen in een van deze paden, moet u de locatie van uw module door geven in de aanroep van `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="85626-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="85626-140">(Als dit niet het geval is, kan Power shell het niet vinden.) Als u vanaf Power Shell 3,0 een module in een van de paden van de Power shell-module hebt geplaatst, hoeft u deze niet expliciet te importeren.</span><span class="sxs-lookup"><span data-stu-id="85626-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="85626-141">De module wordt automatisch geladen wanneer een gebruiker uw functie aanroept.</span><span class="sxs-lookup"><span data-stu-id="85626-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="85626-142">Zie [een Power shell-module](./importing-a-powershell-module.md) en [PSModulePath-omgevings variabele](./modifying-the-psmodulepath-installation-path.md)importeren voor meer informatie over het pad naar de module.</span><span class="sxs-lookup"><span data-stu-id="85626-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="85626-143">Als u een module van de actieve service wilt verwijderen, maakt u een aanroep van [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="85626-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="85626-144">Als de module [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) uit het actieve geheugen wordt verwijderd, wordt deze niet verwijderd uit de locatie waar u de module bestanden hebt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="85626-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="85626-145">Voor beeld van agenda code weer geven</span><span class="sxs-lookup"><span data-stu-id="85626-145">Show-Calendar code example</span></span>

<span data-ttu-id="85626-146">Het volgende voor beeld is een eenvoudige script module met een enkele functie met de naam `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="85626-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="85626-147">Met deze functie wordt een visuele weer gave van een kalender weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="85626-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="85626-148">Daarnaast bevat het voor beeld de Power shell-Help-teken reeksen voor de samen vatting, beschrijving, parameter waarden en een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="85626-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="85626-149">Houd er rekening mee dat de laatste regel code ervoor zorgt dat de functie @no__t 0 wordt geëxporteerd als een module-lid wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85626-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
