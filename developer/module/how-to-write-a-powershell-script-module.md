---
title: Over het schrijven van een PowerShell-Script-Module | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470800"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="f7c84-102">Een PowerShell-scriptmodule schrijven</span><span class="sxs-lookup"><span data-stu-id="f7c84-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="f7c84-103">Een scriptmodule is in feite een geldig PowerShell-script opgeslagen in een psm1-extensie.</span><span class="sxs-lookup"><span data-stu-id="f7c84-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="f7c84-104">Deze extensie kunt de PowerShell-engine een aantal regels en -cmdlets gebruiken in uw bestand.</span><span class="sxs-lookup"><span data-stu-id="f7c84-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="f7c84-105">De meeste van deze mogelijkheden zijn er kunt u uw code ook beheer scoping installeren op andere systemen.</span><span class="sxs-lookup"><span data-stu-id="f7c84-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="f7c84-106">U kunt ook een module manifest-bestand dat wordt beschreven en nog meer complexe-installaties en -oplossingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f7c84-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="f7c84-107">Een PowerShell-Script-Module schrijven</span><span class="sxs-lookup"><span data-stu-id="f7c84-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="f7c84-108">U maakt een scriptmodule een geldig PowerShell-script opslaan in een psm1-bestand en vervolgens dat bestand op te slaan in een map waar PowerShell deze kan vinden.</span><span class="sxs-lookup"><span data-stu-id="f7c84-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="f7c84-109">In de map die u kunt ook alle resources die u wilt uitvoeren van uw script plaatsen, evenals een manifestbestand waarin wordt beschreven in PowerShell de werking van uw module.</span><span class="sxs-lookup"><span data-stu-id="f7c84-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="f7c84-110">Een eenvoudige PowerShell-Module maken</span><span class="sxs-lookup"><span data-stu-id="f7c84-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="f7c84-111">Neemt een bestaande PowerShell-script en sla het script met de extensie .psm1.</span><span class="sxs-lookup"><span data-stu-id="f7c84-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="f7c84-112">Opslaan van een script met de .psm1 extensie betekent dat u de module-cmdlets, zoals kunt [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), erop.</span><span class="sxs-lookup"><span data-stu-id="f7c84-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="f7c84-113">Deze cmdlets bestaat voornamelijk zodat u eenvoudig kunt importeren en exporteren van uw code op systemen van andere gebruikers.</span><span class="sxs-lookup"><span data-stu-id="f7c84-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="f7c84-114">(Of de alternatieve oplossing zou worden het laden van uw code op andere systemen en punt-bron in het geheugen is een bijzonder schaalbare oplossing niet actief.) Zie voor meer informatie de **-Module-Cmdlets en variabelen** in sectie [Windows PowerShell-Modules](./understanding-a-windows-powershell-module.md) Houd er rekening mee dat alle functies in uw script zijn standaard toegankelijk voor gebruikers die uw psm1-bestand importeren maar eigenschappen zijn niet.</span><span class="sxs-lookup"><span data-stu-id="f7c84-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="f7c84-115">Een voorbeeld PowerShell-script, hebben recht `Show-Calendar`, vindt u aan het einde van dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="f7c84-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

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

2. <span data-ttu-id="f7c84-116">Aanroepen voor het beheren van toegang tot bepaalde functies of de eigenschappen voor gebruikers, [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) aan het einde van uw script.</span><span class="sxs-lookup"><span data-stu-id="f7c84-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="f7c84-117">De voorbeeldcode aan de onderkant van de pagina heeft slechts één functie, die standaard beschikbaar zou worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f7c84-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="f7c84-118">Het is echter raadzaam dat u expliciet uit welke functies u weergeven aanroepen, wilt zoals beschreven in de volgende code:</span><span class="sxs-lookup"><span data-stu-id="f7c84-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="f7c84-119">U kunt ook beperken wat wordt geïmporteerd met behulp van een module-manifest.</span><span class="sxs-lookup"><span data-stu-id="f7c84-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="f7c84-120">Zie voor meer informatie, [importeren van een PowerShell-Module](./importing-a-powershell-module.md) en [over het schrijven van een PowerShell-Module-Manifest](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="f7c84-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="f7c84-121">Als u modules waarvoor uw eigen module moet zijn geladen hebt, kunt u deze gebruiken met een aanroep naar `Import-Module`, aan de bovenkant van uw eigen module.</span><span class="sxs-lookup"><span data-stu-id="f7c84-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="f7c84-122">`Import-Module` is een cmdlet die een bepaalde module op een systeem wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f7c84-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="f7c84-123">Als zodanig wordt het ook gebruikt op een later tijdstip in de procedure ook uw eigen module te installeren.</span><span class="sxs-lookup"><span data-stu-id="f7c84-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="f7c84-124">De voorbeeldcode onderaan deze pagina wordt niet gebruikt voor alle modules importeren.</span><span class="sxs-lookup"><span data-stu-id="f7c84-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="f7c84-125">Als het is echter zouden ze worden weergegeven aan de bovenkant van het bestand, zoals beschreven in de volgende code:</span><span class="sxs-lookup"><span data-stu-id="f7c84-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="f7c84-126">Om te beschrijven van de module naar het PowerShell-Help-systeem, kunt u gebruiken standaard help opmerkingen in het bestand, of maakt u een extra helpbestand.</span><span class="sxs-lookup"><span data-stu-id="f7c84-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="f7c84-127">De voorbeeldcode aan de onderkant van dit onderwerp bevat de help-informatie in de opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="f7c84-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="f7c84-128">U kunt ook uitgebreide XML-bestanden met extra help-inhoud schrijven.</span><span class="sxs-lookup"><span data-stu-id="f7c84-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="f7c84-129">Zie voor meer informatie, [schrijven Help voor Windows PowerShell-Modules](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="f7c84-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="f7c84-130">Als u aanvullende modules, XML-bestanden of andere inhoud die u wilt verpakken met de module hebt, kunt u dit doen met een module-manifest.</span><span class="sxs-lookup"><span data-stu-id="f7c84-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="f7c84-131">Een module-manifest is een bestand met de namen van andere modules, directory-indelingen, versiebeheer getallen, de auteur van gegevens en andere stukjes informatie.</span><span class="sxs-lookup"><span data-stu-id="f7c84-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="f7c84-132">PowerShell maakt gebruik van het manifestbestand van de module uw oplossing te organiseren en te implementeren.</span><span class="sxs-lookup"><span data-stu-id="f7c84-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="f7c84-133">Echter, vanwege de relatief eenvoudige aard van dit voorbeeld wordt een manifestbestand is niet nodig.</span><span class="sxs-lookup"><span data-stu-id="f7c84-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="f7c84-134">Zie voor meer informatie, [Module manifesten](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="f7c84-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="f7c84-135">Als u wilt installeren en uitvoeren van uw module, slaat u de module aan een van de juiste PowerShell-paden en aanroepen van `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="f7c84-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="f7c84-136">De paden waar kunt u uw module bevinden zich in de `$env:PSModulePath` globale variabele.</span><span class="sxs-lookup"><span data-stu-id="f7c84-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="f7c84-137">Bijvoorbeeld, een algemeen pad naar het opslaan van een module op een systeem zouden worden `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="f7c84-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="f7c84-138">Zorg ervoor dat een map maken voor uw module bestaat, zelfs als deze alleen een enkel psm1-bestand.</span><span class="sxs-lookup"><span data-stu-id="f7c84-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="f7c84-139">Als u de module niet op een van deze paden hebt opgeslagen, moet u om door te geven op de locatie van de module in de aanroep naar `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="f7c84-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="f7c84-140">(Anders PowerShell niet zou kunnen vinden.) Beginnen met PowerShell 3.0, als u uw module in een van de paden van PowerShell-module hebt geplaatst, hoeft u niet expliciet om deze te importeren.</span><span class="sxs-lookup"><span data-stu-id="f7c84-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="f7c84-141">U module wordt automatisch geladen wanneer een gebruiker uw functie aanroept.</span><span class="sxs-lookup"><span data-stu-id="f7c84-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="f7c84-142">Zie voor meer informatie over de modulepad [importeren van een PowerShell-Module](./importing-a-powershell-module.md) en [PSModulePath omgevingsvariabele](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="f7c84-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="f7c84-143">Als u wilt verwijderen een module van actieve service, maken een aanroep van [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="f7c84-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="f7c84-144">Houd er rekening mee dat [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) uw module wordt verwijderd uit het geheugen - het wordt niet daadwerkelijk verwijderd uit waar u de module-bestanden hebt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f7c84-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="f7c84-145">Codevoorbeeld weergeven-agenda</span><span class="sxs-lookup"><span data-stu-id="f7c84-145">Show-Calendar code example</span></span>

<span data-ttu-id="f7c84-146">Het volgende voorbeeld wordt een eenvoudig script-module met een enkele functie met de naam `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="f7c84-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="f7c84-147">Deze functie wordt een visuele representatie van een kalender weergegeven.</span><span class="sxs-lookup"><span data-stu-id="f7c84-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="f7c84-148">Daarnaast bevat het voorbeeld de tekenreeksen PowerShell Help voor de samenvatting, beschrijving, parameterwaarden en voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="f7c84-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="f7c84-149">Houd er rekening mee dat de laatste regel van code, zorgt ervoor dat de `Show-Calendar` functie wordt geëxporteerd als lid van de module wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f7c84-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

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
