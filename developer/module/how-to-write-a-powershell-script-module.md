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
# <a name="how-to-write-a-powershell-script-module"></a>Een PowerShell-scriptmodule schrijven

Een scriptmodule is in feite een geldig PowerShell-script opgeslagen in een psm1-extensie. Deze extensie kunt de PowerShell-engine een aantal regels en -cmdlets gebruiken in uw bestand. De meeste van deze mogelijkheden zijn er kunt u uw code ook beheer scoping installeren op andere systemen. U kunt ook een module manifest-bestand dat wordt beschreven en nog meer complexe-installaties en -oplossingen gebruiken.

## <a name="writing-a-powershell-script-module"></a>Een PowerShell-Script-Module schrijven

U maakt een scriptmodule een geldig PowerShell-script opslaan in een psm1-bestand en vervolgens dat bestand op te slaan in een map waar PowerShell deze kan vinden. In de map die u kunt ook alle resources die u wilt uitvoeren van uw script plaatsen, evenals een manifestbestand waarin wordt beschreven in PowerShell de werking van uw module.

#### <a name="to-create-a-basic-powershell-module"></a>Een eenvoudige PowerShell-Module maken

1. Neemt een bestaande PowerShell-script en sla het script met de extensie .psm1.

   Opslaan van een script met de .psm1 extensie betekent dat u de module-cmdlets, zoals kunt [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), erop. Deze cmdlets bestaat voornamelijk zodat u eenvoudig kunt importeren en exporteren van uw code op systemen van andere gebruikers. (Of de alternatieve oplossing zou worden het laden van uw code op andere systemen en punt-bron in het geheugen is een bijzonder schaalbare oplossing niet actief.) Zie voor meer informatie de **-Module-Cmdlets en variabelen** in sectie [Windows PowerShell-Modules](./understanding-a-windows-powershell-module.md) Houd er rekening mee dat alle functies in uw script zijn standaard toegankelijk voor gebruikers die uw psm1-bestand importeren maar eigenschappen zijn niet.

   Een voorbeeld PowerShell-script, hebben recht `Show-Calendar`, vindt u aan het einde van dit onderwerp.

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

2. Aanroepen voor het beheren van toegang tot bepaalde functies of de eigenschappen voor gebruikers, [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) aan het einde van uw script.

   De voorbeeldcode aan de onderkant van de pagina heeft slechts één functie, die standaard beschikbaar zou worden gemaakt. Het is echter raadzaam dat u expliciet uit welke functies u weergeven aanroepen, wilt zoals beschreven in de volgende code:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   U kunt ook beperken wat wordt geïmporteerd met behulp van een module-manifest. Zie voor meer informatie, [importeren van een PowerShell-Module](./importing-a-powershell-module.md) en [over het schrijven van een PowerShell-Module-Manifest](./how-to-write-a-powershell-module-manifest.md).

3. Als u modules waarvoor uw eigen module moet zijn geladen hebt, kunt u deze gebruiken met een aanroep naar `Import-Module`, aan de bovenkant van uw eigen module.

   `Import-Module` is een cmdlet die een bepaalde module op een systeem wordt geïmporteerd. Als zodanig wordt het ook gebruikt op een later tijdstip in de procedure ook uw eigen module te installeren. De voorbeeldcode onderaan deze pagina wordt niet gebruikt voor alle modules importeren. Als het is echter zouden ze worden weergegeven aan de bovenkant van het bestand, zoals beschreven in de volgende code:

   ```powershell
   Import-Module GenericModule
   ```

4. Om te beschrijven van de module naar het PowerShell-Help-systeem, kunt u gebruiken standaard help opmerkingen in het bestand, of maakt u een extra helpbestand.

   De voorbeeldcode aan de onderkant van dit onderwerp bevat de help-informatie in de opmerkingen. U kunt ook uitgebreide XML-bestanden met extra help-inhoud schrijven. Zie voor meer informatie, [schrijven Help voor Windows PowerShell-Modules](./writing-help-for-windows-powershell-modules.md).

5. Als u aanvullende modules, XML-bestanden of andere inhoud die u wilt verpakken met de module hebt, kunt u dit doen met een module-manifest.

   Een module-manifest is een bestand met de namen van andere modules, directory-indelingen, versiebeheer getallen, de auteur van gegevens en andere stukjes informatie. PowerShell maakt gebruik van het manifestbestand van de module uw oplossing te organiseren en te implementeren. Echter, vanwege de relatief eenvoudige aard van dit voorbeeld wordt een manifestbestand is niet nodig. Zie voor meer informatie, [Module manifesten](./how-to-write-a-powershell-module-manifest.md).

6. Als u wilt installeren en uitvoeren van uw module, slaat u de module aan een van de juiste PowerShell-paden en aanroepen van `Import-Module`.

   De paden waar kunt u uw module bevinden zich in de `$env:PSModulePath` globale variabele. Bijvoorbeeld, een algemeen pad naar het opslaan van een module op een systeem zouden worden `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Zorg ervoor dat een map maken voor uw module bestaat, zelfs als deze alleen een enkel psm1-bestand. Als u de module niet op een van deze paden hebt opgeslagen, moet u om door te geven op de locatie van de module in de aanroep naar `Import-Module`. (Anders PowerShell niet zou kunnen vinden.) Beginnen met PowerShell 3.0, als u uw module in een van de paden van PowerShell-module hebt geplaatst, hoeft u niet expliciet om deze te importeren. U module wordt automatisch geladen wanneer een gebruiker uw functie aanroept.
   Zie voor meer informatie over de modulepad [importeren van een PowerShell-Module](./importing-a-powershell-module.md) en [PSModulePath omgevingsvariabele](./modifying-the-psmodulepath-installation-path.md).

7. Als u wilt verwijderen een module van actieve service, maken een aanroep van [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   Houd er rekening mee dat [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) uw module wordt verwijderd uit het geheugen - het wordt niet daadwerkelijk verwijderd uit waar u de module-bestanden hebt opgeslagen.

### <a name="show-calendar-code-example"></a>Codevoorbeeld weergeven-agenda

Het volgende voorbeeld wordt een eenvoudig script-module met een enkele functie met de naam `Show-Calendar`.
Deze functie wordt een visuele representatie van een kalender weergegeven. Daarnaast bevat het voorbeeld de tekenreeksen PowerShell Help voor de samenvatting, beschrijving, parameterwaarden en voorbeeld. Houd er rekening mee dat de laatste regel van code, zorgt ervoor dat de `Show-Calendar` functie wordt geëxporteerd als lid van de module wanneer de module wordt geïmporteerd.

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
