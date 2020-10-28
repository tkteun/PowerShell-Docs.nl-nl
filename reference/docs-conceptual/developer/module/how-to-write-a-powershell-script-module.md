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
# <a name="how-to-write-a-powershell-script-module"></a>Een PowerShell-scriptmodule schrijven

Een script module is een geldig Power shell-script dat is opgeslagen in een `.psm1` uitbrei ding. Met deze uitbrei ding kan de Power shell-engine regels en module-cmdlets gebruiken in uw bestand. De meeste van deze mogelijkheden zijn er om u te helpen bij het installeren van uw code op andere systemen en voor het beheren van scopes. U kunt ook een module manifest bestand gebruiken, waarin complexere installaties en oplossingen worden beschreven.

## <a name="writing-a-powershell-script-module"></a>Een Power shell-script module schrijven

Als u een script module wilt maken, slaat u een geldig Power shell-script op in een `.psm1` bestand. Het script en de map waarin het bestand is opgeslagen, moeten dezelfde naam gebruiken. Bijvoorbeeld, een script met de naam `MyPsScript.psm1` wordt opgeslagen in een map met de naam `MyPsScript` .

De directory van de module moet zich in een pad bevinden dat is opgegeven in `$env:PSModulePath` . De directory van de module kan alle resources bevatten die nodig zijn voor het uitvoeren van het script, en een module manifest bestand dat wordt beschreven in Power shell hoe uw module werkt.

## <a name="create-a-basic-powershell-module"></a>Een Basic Power shell-module maken

In de volgende stappen wordt beschreven hoe u een Power shell-module maakt.

1. Een Power shell-script met een `.psm1` extensie opslaan. Gebruik dezelfde naam voor het script en de map waarin het script is opgeslagen.

   Het opslaan van een script met de `.psm1` uitbrei ding betekent dat u de module-cmdlets, zoals [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), kunt gebruiken. De module-cmdlets bestaan voornamelijk, zodat u uw code kunt importeren en exporteren naar de systemen van andere gebruikers. De alternatieve oplossing is het laden van uw code op andere systemen en vervolgens punt-bron in actief geheugen, dat geen schaal bare oplossing is. Zie [informatie over een Windows Power shell-module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables)voor meer informatie.
   Wanneer gebruikers uw `.psm1` bestand importeren, zijn standaard alle functies in uw script toegankelijk, maar variabelen niet.

   Aan het einde van dit artikel vindt u een voor beeld van een Power shell-script `Show-Calendar` met de titel.

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

2. Als u de gebruikers toegang tot bepaalde functies of variabelen wilt beheren, roept u [export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) aan het einde van uw script aan.

   De voorbeeld code aan de onderkant van het artikel heeft slechts één functie, die standaard wordt weer gegeven. U kunt echter het beste expliciet aanroepen welke functies u beschikbaar wilt stellen, zoals beschreven in de volgende code:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   U kunt de items die worden geïmporteerd beperken met behulp van een module manifest. Zie [een Power shell-module importeren](./importing-a-powershell-module.md) en [een Power shell-module manifest schrijven](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.

3. Als u modules hebt die uw eigen module moet laden, kunt u `Import-Module` aan de bovenkant van uw module gebruiken.

   De `Import-Module` cmdlet importeert een doel module op een systeem en kan op een later tijdstip worden gebruikt in de procedure om uw eigen module te installeren. In de voorbeeld code onder in dit artikel worden geen import modules gebruikt. Als dat wel het geval is, worden ze boven aan het bestand weer gegeven, zoals in de volgende code wordt weer gegeven:

   ```powershell
   Import-Module GenericModule
   ```

4. Als u de module wilt beschrijven in het Help-systeem van Power shell, kunt u standaard opmerkingen voor de Help in het bestand gebruiken of een extra Help-bestand maken.

   Het code voorbeeld onder in dit artikel bevat de Help-informatie in de opmerkingen. U kunt ook uitgebreide XML-bestanden schrijven die extra Help-inhoud bevatten. Zie hulp bij het [schrijven van Help voor Windows Power shell-modules](./writing-help-for-windows-powershell-modules.md)voor meer informatie.

5. Als u meer modules, XML-bestanden of andere inhoud wilt inpakken met uw module, kunt u een module manifest gebruiken.

   Een module manifest is een bestand met de namen van andere modules, Directory-indelingen, versie nummers, auteurgegevens en andere stukjes informatie. Power shell gebruikt het manifest bestand van de module om uw oplossing te organiseren en te implementeren. Zie [een Power shell-module manifest schrijven](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.

6. Sla de module op in een van de juiste Power shell-paden en gebruik om de module te installeren en uit te voeren `Import-Module` .

   De paden waar u uw module kunt installeren, bevinden zich in de `$env:PSModulePath` globale variabele. Bijvoorbeeld, een gemeen schappelijk pad om een module op een systeem op te slaan zou zijn `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>` . Zorg ervoor dat u een map maakt voor uw module die dezelfde naam gebruikt als de script module, zelfs als het slechts één bestand is `.psm1` . Als u de module niet hebt opgeslagen in een van deze paden, moet u de locatie van de module opgeven in de `Import-Module` opdracht. Als dat niet het geval is, kan Power shell de module niet vinden.

   Als u begint met Power Shell 3,0 en u uw module hebt geplaatst in een van de Power shell-module paden, hoeft u deze niet expliciet te importeren. Uw module wordt automatisch geladen wanneer een gebruiker uw functie aanroept. Zie [een Power shell-module importeren](./importing-a-powershell-module.md) en het installatiepad van [PSModulePath wijzigen](./modifying-the-psmodulepath-installation-path.md)voor meer informatie over het pad naar de module.

7. Als u een module van de actieve service in de huidige Power shell-sessie wilt verwijderen, gebruikt u [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   > [!NOTE]
   > `Remove-Module` Hiermee wordt een module verwijderd uit de huidige Power shell-sessie, maar wordt de module niet verwijderd of worden de bestanden van de module verwijderd.

## <a name="show-calendar-code-example"></a>Voor beeld van Show-Calendar code

Het volgende voor beeld is een script module met een enkele functie met de naam `Show-Calendar` . Met deze functie wordt een visuele weer gave van een kalender weer gegeven. Het voor beeld bevat de Help-teken reeksen van Power shell voor de samen vatting, beschrijving, parameter waarden en code. Wanneer de module wordt geïmporteerd, `Export-ModuleMember` zorgt de opdracht ervoor dat de `Show-Calendar` functie wordt geëxporteerd als een module-lid.

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
