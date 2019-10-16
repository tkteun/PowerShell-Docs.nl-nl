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
# <a name="how-to-write-a-powershell-script-module"></a>Een PowerShell-scriptmodule schrijven

Een script module is in wezen een geldig Power shell-script dat is opgeslagen in de extensie. psm1. Met deze uitbrei ding kan de Power shell-engine gebruikmaken van een aantal regels en cmdlets in uw bestand. De meeste van deze mogelijkheden zijn er om u te helpen bij het installeren van uw code op andere systemen en voor het beheren van scopes. U kunt ook een manifest bestand van een module gebruiken, waarmee u nog complexe installaties en oplossingen kunt beschrijven.

## <a name="writing-a-powershell-script-module"></a>Een Power shell-script module schrijven

U maakt een script module door een geldig Power shell-script op te slaan in een. psm1-bestand en het bestand vervolgens op te slaan in een map die zich in de directory bevindt waarin Power shell deze kan vinden. In deze map kunt u ook resources plaatsen die u nodig hebt om uw script uit te voeren, evenals een manifest bestand dat beschrijft hoe de module werkt in Power shell.

#### <a name="to-create-a-basic-powershell-module"></a>Een eenvoudige Power shell-module maken

1. Maak een bestaand Power shell-script en sla het script op met de extensie. psm1.

   Het opslaan van een script met de extensie. psm1 betekent dat u de module-cmdlets, zoals [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), kunt gebruiken. Deze cmdlets bestaan voornamelijk, zodat u uw code eenvoudig kunt importeren en exporteren naar de systemen van andere gebruikers. (De alternatieve oplossing is het laden van uw code op andere systemen en vervolgens punt-bron in actief geheugen, wat geen bijzonder schaal bare oplossing is.) Zie de sectie module- **cmdlets en variabelen** in [Windows Power shell-modules](./understanding-a-windows-powershell-module.md) voor meer informatie. alle functies in uw script zijn standaard toegankelijk voor gebruikers die uw. psm1-bestand importeren, maar eigenschappen zijn niet.

   Aan het einde van dit onderwerp vindt u een voor beeld van een Power shell-script met de titel `Show-Calendar`.

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

2. Als u de gebruikers toegang tot bepaalde functies of eigenschappen wilt beheren, roept u [export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) aan het einde van uw script aan.

   De voorbeeld code aan de onderkant van de pagina heeft slechts één functie die standaard wordt weer gegeven. Het wordt echter aangeraden om de functies die u wilt weer geven expliciet aan te roepen, zoals beschreven in de volgende code:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   U kunt ook beperken wat wordt geïmporteerd met behulp van een module manifest. Zie [een Power shell-module importeren](./importing-a-powershell-module.md) en [een Power shell-module manifest schrijven](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.

3. Als u modules hebt waarvoor uw eigen module moet worden geladen, kunt u deze gebruiken met een aanroep van `Import-Module`, bovenin uw eigen module.

   `Import-Module` is een cmdlet waarmee een doel module op een systeem wordt geïmporteerd. Daarom wordt het ook op een later tijdstip in de procedure gebruikt om ook uw eigen module te installeren. In de voorbeeld code onder aan deze pagina worden geen import modules gebruikt. Als dat wel het geval is, wordt deze boven aan het bestand weer gegeven, zoals beschreven in de volgende code:

   ```powershell
   Import-Module GenericModule
   ```

4. Als u de module wilt beschrijven in het Help-systeem van Power shell, kunt u standaard opmerkingen voor de Help in het bestand gebruiken of een extra Help-bestand maken.

   Het code voorbeeld onder in dit onderwerp bevat de Help-informatie in de opmerkingen. U kunt ook uitgebreide XML-bestanden schrijven die extra Help-inhoud bevatten. Zie hulp bij het [schrijven van Help voor Windows Power shell-modules](./writing-help-for-windows-powershell-modules.md)voor meer informatie.

5. Als u meer modules, XML-bestanden of andere inhoud die u wilt inpakken met uw module, kunt u dit doen met een module manifest.

   Een module manifest is een bestand met de namen van andere modules, Directory-indelingen, versie nummers, auteurgegevens en andere stukjes informatie. Power shell gebruikt het manifest bestand van de module om uw oplossing te organiseren en te implementeren. Vanwege de relatief eenvoudige aard van dit voor beeld was er echter geen manifest bestand nodig. Zie [module manifests](./how-to-write-a-powershell-module-manifest.md)voor meer informatie.

6. Als u uw module wilt installeren en uitvoeren, slaat u de module op in een van de juiste Power shell-paden en maakt u een aanroep naar `Import-Module`.

   De paden waar u uw module kunt installeren, bevinden zich in de globale variabele `$env:PSModulePath`. Een gemeen schappelijk pad om een module op een systeem op te slaan, zou bijvoorbeeld `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>` zijn. Zorg ervoor dat u een map maakt voor uw module, zelfs als deze slechts één. psm1-bestand is. Als u de module niet hebt opgeslagen in een van deze paden, moet u de locatie van uw module door geven in de aanroep van `Import-Module`. (Als dit niet het geval is, kan Power shell het niet vinden.) Als u vanaf Power Shell 3,0 een module in een van de paden van de Power shell-module hebt geplaatst, hoeft u deze niet expliciet te importeren. De module wordt automatisch geladen wanneer een gebruiker uw functie aanroept.
   Zie [een Power shell-module](./importing-a-powershell-module.md) en [PSModulePath-omgevings variabele](./modifying-the-psmodulepath-installation-path.md)importeren voor meer informatie over het pad naar de module.

7. Als u een module van de actieve service wilt verwijderen, maakt u een aanroep van [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   Als de module [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) uit het actieve geheugen wordt verwijderd, wordt deze niet verwijderd uit de locatie waar u de module bestanden hebt opgeslagen.

### <a name="show-calendar-code-example"></a>Voor beeld van agenda code weer geven

Het volgende voor beeld is een eenvoudige script module met een enkele functie met de naam `Show-Calendar`.
Met deze functie wordt een visuele weer gave van een kalender weer gegeven. Daarnaast bevat het voor beeld de Power shell-Help-teken reeksen voor de samen vatting, beschrijving, parameter waarden en een voor beeld. Houd er rekening mee dat de laatste regel code ervoor zorgt dat de functie @no__t 0 wordt geëxporteerd als een module-lid wanneer de module wordt geïmporteerd.

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
