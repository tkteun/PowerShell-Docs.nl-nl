---
ms.date: 11/21/2019
ms.topic: reference
title: Een PowerShell-scriptmodule schrijven
description: Een PowerShell-scriptmodule schrijven
ms.openlocfilehash: c44b09a915501fb10773ab11cf13136d5035ba69
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649147"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="e3c0e-103">Een PowerShell-scriptmodule schrijven</span><span class="sxs-lookup"><span data-stu-id="e3c0e-103">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="e3c0e-104">Een script module is een geldig Power shell-script dat is opgeslagen in een `.psm1` uitbrei ding.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-104">A script module is any valid PowerShell script saved in a `.psm1` extension.</span></span> <span data-ttu-id="e3c0e-105">Met deze uitbrei ding kan de Power shell-engine regels en module-cmdlets gebruiken in uw bestand.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-105">This extension allows the PowerShell engine to use rules and module cmdlets on your file.</span></span> <span data-ttu-id="e3c0e-106">De meeste van deze mogelijkheden zijn er om u te helpen bij het installeren van uw code op andere systemen en voor het beheren van scopes.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-106">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="e3c0e-107">U kunt ook een module manifest bestand gebruiken, waarin complexere installaties en oplossingen worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-107">You can also use a module manifest file, which describes more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="e3c0e-108">Een Power shell-script module schrijven</span><span class="sxs-lookup"><span data-stu-id="e3c0e-108">Writing a PowerShell script module</span></span>

<span data-ttu-id="e3c0e-109">Als u een script module wilt maken, slaat u een geldig Power shell-script op in een `.psm1` bestand.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-109">To create a script module, save a valid PowerShell script to a `.psm1` file.</span></span> <span data-ttu-id="e3c0e-110">Het script en de map waarin het bestand is opgeslagen, moeten dezelfde naam gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-110">The script and the directory where it's stored must use the same name.</span></span> <span data-ttu-id="e3c0e-111">Bijvoorbeeld, een script met de naam `MyPsScript.psm1` wordt opgeslagen in een map met de naam `MyPsScript` .</span><span class="sxs-lookup"><span data-stu-id="e3c0e-111">For example, a script named `MyPsScript.psm1` is stored in a directory named `MyPsScript`.</span></span>

<span data-ttu-id="e3c0e-112">De directory van de module moet zich in een pad bevinden dat is opgegeven in `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="e3c0e-112">The module's directory needs to be in a path specified in `$env:PSModulePath`.</span></span> <span data-ttu-id="e3c0e-113">De directory van de module kan alle resources bevatten die nodig zijn voor het uitvoeren van het script, en een module manifest bestand dat wordt beschreven in Power shell hoe uw module werkt.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-113">The module's directory can contain any resources that are needed to run the script, and a module manifest file that describes to PowerShell how your module works.</span></span>

## <a name="create-a-basic-powershell-module"></a><span data-ttu-id="e3c0e-114">Een Basic Power shell-module maken</span><span class="sxs-lookup"><span data-stu-id="e3c0e-114">Create a basic PowerShell module</span></span>

<span data-ttu-id="e3c0e-115">In de volgende stappen wordt beschreven hoe u een Power shell-module maakt.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-115">The following steps describe how to create a PowerShell module.</span></span>

1. <span data-ttu-id="e3c0e-116">Een Power shell-script met een `.psm1` extensie opslaan.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-116">Save a PowerShell script with a `.psm1` extension.</span></span> <span data-ttu-id="e3c0e-117">Gebruik dezelfde naam voor het script en de map waarin het script is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-117">Use the same name for the script and the directory where the script is saved.</span></span>

   <span data-ttu-id="e3c0e-118">Het opslaan van een script met de `.psm1` uitbrei ding betekent dat u de module-cmdlets, zoals [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-118">Saving a script with the `.psm1` extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span> <span data-ttu-id="e3c0e-119">De module-cmdlets bestaan voornamelijk, zodat u uw code kunt importeren en exporteren naar de systemen van andere gebruikers.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-119">The module cmdlets exist primarily so that you can import and export your code onto other user's systems.</span></span> <span data-ttu-id="e3c0e-120">De alternatieve oplossing is het laden van uw code op andere systemen en vervolgens punt-bron in actief geheugen, dat geen schaal bare oplossing is.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-120">The alternate solution would be to load your code on other systems and then dot-source it into active memory, which isn't a scalable solution.</span></span> <span data-ttu-id="e3c0e-121">Zie [informatie over een Windows Power shell-module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-121">For more information, see [Understanding a Windows PowerShell Module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span></span>
   <span data-ttu-id="e3c0e-122">Wanneer gebruikers uw `.psm1` bestand importeren, zijn standaard alle functies in uw script toegankelijk, maar variabelen niet.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-122">By default, when users import your `.psm1` file, all functions in your script are accessible, but variables aren't.</span></span>

   <span data-ttu-id="e3c0e-123">Aan het einde van dit artikel vindt u een voor beeld van een Power shell-script `Show-Calendar` met de titel.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-123">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this article.</span></span>

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

2. <span data-ttu-id="e3c0e-124">Als u de gebruikers toegang tot bepaalde functies of variabelen wilt beheren, roept u [export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) aan het einde van uw script aan.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-124">To control user access to certain functions or variables, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="e3c0e-125">De voorbeeld code aan de onderkant van het artikel heeft slechts één functie, die standaard wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-125">The example code at the bottom of the article has only one function, which by default would be exposed.</span></span> <span data-ttu-id="e3c0e-126">U kunt echter het beste expliciet aanroepen welke functies u beschikbaar wilt stellen, zoals beschreven in de volgende code:</span><span class="sxs-lookup"><span data-stu-id="e3c0e-126">However, it's recommended you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="e3c0e-127">U kunt de items die worden geïmporteerd beperken met behulp van een module manifest.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-127">You can restrict what's imported using a module manifest.</span></span> <span data-ttu-id="e3c0e-128">Zie [een Power shell-module importeren](./importing-a-powershell-module.md) en [een Power shell-module manifest schrijven](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-128">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="e3c0e-129">Als u modules hebt die uw eigen module moet laden, kunt u `Import-Module` aan de bovenkant van uw module gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-129">If you have modules that your own module needs to load, you can use `Import-Module`, at the top of your module.</span></span>

   <span data-ttu-id="e3c0e-130">De `Import-Module` cmdlet importeert een doel module op een systeem en kan op een later tijdstip worden gebruikt in de procedure om uw eigen module te installeren.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-130">The `Import-Module` cmdlet imports a targeted module onto a system, and can be used at a later point in the procedure to install your own module.</span></span> <span data-ttu-id="e3c0e-131">In de voorbeeld code onder in dit artikel worden geen import modules gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-131">The sample code at the bottom of this article doesn't use any import modules.</span></span> <span data-ttu-id="e3c0e-132">Als dat wel het geval is, worden ze boven aan het bestand weer gegeven, zoals in de volgende code wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="e3c0e-132">But if it did, they would be listed at the top of the file, as shown in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="e3c0e-133">Als u de module wilt beschrijven in het Help-systeem van Power shell, kunt u standaard opmerkingen voor de Help in het bestand gebruiken of een extra Help-bestand maken.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-133">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="e3c0e-134">Het code voorbeeld onder in dit artikel bevat de Help-informatie in de opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-134">The code sample at the bottom of this article includes the help information in the comments.</span></span> <span data-ttu-id="e3c0e-135">U kunt ook uitgebreide XML-bestanden schrijven die extra Help-inhoud bevatten.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-135">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="e3c0e-136">Zie hulp bij het [schrijven van Help voor Windows Power shell-modules](./writing-help-for-windows-powershell-modules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-136">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="e3c0e-137">Als u meer modules, XML-bestanden of andere inhoud wilt inpakken met uw module, kunt u een module manifest gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-137">If you have additional modules, XML files, or other content you want to package with your module, you can use a module manifest.</span></span>

   <span data-ttu-id="e3c0e-138">Een module manifest is een bestand met de namen van andere modules, Directory-indelingen, versie nummers, auteurgegevens en andere stukjes informatie.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-138">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="e3c0e-139">Power shell gebruikt het manifest bestand van de module om uw oplossing te organiseren en te implementeren.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-139">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="e3c0e-140">Zie [een Power shell-module manifest schrijven](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-140">For more information, see [How to write a PowerShell module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="e3c0e-141">Sla de module op in een van de juiste Power shell-paden en gebruik om de module te installeren en uit te voeren `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="e3c0e-141">To install and run your module, save the module to one of the appropriate PowerShell paths, and use `Import-Module`.</span></span>

   <span data-ttu-id="e3c0e-142">De paden waar u uw module kunt installeren, bevinden zich in de `$env:PSModulePath` globale variabele.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-142">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="e3c0e-143">Bijvoorbeeld, een gemeen schappelijk pad om een module op een systeem op te slaan zou zijn `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>` .</span><span class="sxs-lookup"><span data-stu-id="e3c0e-143">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="e3c0e-144">Zorg ervoor dat u een map maakt voor uw module die dezelfde naam gebruikt als de script module, zelfs als het slechts één bestand is `.psm1` .</span><span class="sxs-lookup"><span data-stu-id="e3c0e-144">Be sure to create a directory for your module that uses the same name as the script module, even if it's only a single `.psm1` file.</span></span> <span data-ttu-id="e3c0e-145">Als u de module niet hebt opgeslagen in een van deze paden, moet u de locatie van de module opgeven in de `Import-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-145">If you didn't save your module to one of these paths, you would have to specify the module's location in the `Import-Module` command.</span></span> <span data-ttu-id="e3c0e-146">Als dat niet het geval is, kan Power shell de module niet vinden.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-146">Otherwise, PowerShell wouldn't be able to find the module.</span></span>

   <span data-ttu-id="e3c0e-147">Als u begint met Power Shell 3,0 en u uw module hebt geplaatst in een van de Power shell-module paden, hoeft u deze niet expliciet te importeren.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-147">Starting with PowerShell 3.0, if you've placed your module in one of the PowerShell module paths, you don't need to explicitly import it.</span></span> <span data-ttu-id="e3c0e-148">Uw module wordt automatisch geladen wanneer een gebruiker uw functie aanroept.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-148">Your module is automatically loaded when a user calls your function.</span></span> <span data-ttu-id="e3c0e-149">Zie [een Power shell-module importeren](./importing-a-powershell-module.md) en het installatiepad van [PSModulePath wijzigen](./modifying-the-psmodulepath-installation-path.md)voor meer informatie over het pad naar de module.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-149">For more information about the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="e3c0e-150">Als u een module van de actieve service in de huidige Power shell-sessie wilt verwijderen, gebruikt u [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="e3c0e-150">To remove a module from active service in the current PowerShell session, use [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   > [!NOTE]
   > <span data-ttu-id="e3c0e-151">`Remove-Module` Hiermee wordt een module verwijderd uit de huidige Power shell-sessie, maar wordt de module niet verwijderd of worden de bestanden van de module verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-151">`Remove-Module` removes a module from the current PowerShell session, but doesn't uninstall the module or delete the module's files.</span></span>

## <a name="show-calendar-code-example"></a><span data-ttu-id="e3c0e-152">Voor beeld van Show-Calendar code</span><span class="sxs-lookup"><span data-stu-id="e3c0e-152">Show-Calendar code example</span></span>

<span data-ttu-id="e3c0e-153">Het volgende voor beeld is een script module met een enkele functie met de naam `Show-Calendar` .</span><span class="sxs-lookup"><span data-stu-id="e3c0e-153">The following example is a script module that contains a single function named `Show-Calendar`.</span></span> <span data-ttu-id="e3c0e-154">Met deze functie wordt een visuele weer gave van een kalender weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-154">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="e3c0e-155">Het voor beeld bevat de Help-teken reeksen van Power shell voor de samen vatting, beschrijving, parameter waarden en code.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-155">The sample contains the PowerShell Help strings for the synopsis, description, parameter values, and code.</span></span> <span data-ttu-id="e3c0e-156">Wanneer de module wordt geïmporteerd, `Export-ModuleMember` zorgt de opdracht ervoor dat de `Show-Calendar` functie wordt geëxporteerd als een module-lid.</span><span class="sxs-lookup"><span data-stu-id="e3c0e-156">When the module is imported, the `Export-ModuleMember` command ensures that the `Show-Calendar` function is exported as a module member.</span></span>

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
