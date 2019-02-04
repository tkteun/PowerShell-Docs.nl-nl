---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een grafische datumkiezer maken
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686500"
---
# <a name="creating-a-graphical-date-picker"></a>Een grafische datumkiezer maken

Gebruik Windows PowerShell 3.0 en latere versies naar een formulier maken met een grafische, agenda-stijl-besturingselement waarmee gebruikers een dag van de maand selecteren.

## <a name="create-a-graphical-date-picker-control"></a>Een grafische datumkiezer maken

Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Het script begint met het laden van twee .NET Framework-klassen: **System.Drawing** en **System.Windows.Forms**. Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **Windows.Forms.Form**; die zorgt voor een leeg formulier of Hiermee bepaalt u venster waaraan u kunt beginnen met het toevoegen.

```powershell
$form = New-Object Windows.Forms.Form
```

Nadat u een exemplaar van de klasse van het formulier hebt gemaakt, kunt u de waarden toewijzen aan drie eigenschappen van deze klasse.

- **De tekst.** Hiermee wordt de titel van het venster.

- **De grootte.** Dit is de grootte van het formulier, in pixels. Dit script maakt u een formulier 243 pixels breed 230 pixels hoog is.

- **StartingPosition.** Deze optionele eigenschap is ingesteld op **CenterScreen** in het vorige script. Als u deze eigenschap niet toevoegt, wordt in Windows een locatie geselecteerd als het formulier wordt geopend. Door in te stellen de **StartingPosition** naar **CenterScreen**, u bent automatisch weergeven van het formulier in het midden van het scherm telkens worden geladen.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Vervolgens maken en voeg een kalenderbesturingselement in het formulier. In dit voorbeeld wordt de huidige dag niet gemarkeerd of omcirkeld. Gebruikers kunnen slechts één dag in de kalender in één keer selecteren.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Maak vervolgens een **OK** knop voor het formulier. Geef de grootte en het gedrag van de **OK** knop. In dit voorbeeld is de positie van de knop 165 pixels vanaf de bovenkant van het formulier en 38 pixels vanaf de linkerkant. De hoogte van de knop is 23 pixels, terwijl de lengte van de knop 75 pixels is. Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Op deze manier maakt u een **annuleren** knop. De **annuleren** knop is 165 pixels vanaf de bovenkant, maar 113 pixels vanaf de linkerrand van het venster.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Stel de **Topmost** eigenschap **$true** om af te dwingen van het venster te openen op een andere openstaande vensters en dialoogvensters.

```powershell
$form.Topmost = $true
```

Voeg de volgende regel code om weer te geven van het formulier in Windows.

```powershell
$result = $form.ShowDialog()
```

Ten slotte de code binnen de **als** blok geeft Windows wat te doen met het formulier wanneer gebruikers een dag in de kalender selecteren en klik vervolgens op de **OK** of drukt u op de **Enter** de sleutel. Windows PowerShell wordt de geselecteerde datum weergegeven voor gebruikers.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Zie ook

- [Hey Scripting Guy:  Waarom werken de voorbeelden van deze PowerShell-GUI niet?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell Tip of the Week:  Een grafische datumkiezer maken](https://technet.microsoft.com/library/ff730942.aspx)