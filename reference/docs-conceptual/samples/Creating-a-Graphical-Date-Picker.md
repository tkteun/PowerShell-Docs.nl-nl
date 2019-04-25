---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een grafische datumkiezer maken
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058604"
---
# <a name="creating-a-graphical-date-picker"></a>Een grafische datumkiezer maken

Gebruik Windows PowerShell 3.0 en latere versies naar een formulier maken met een grafische, agenda-stijl-besturingselement waarmee gebruikers een dag van de maand selecteren.

## <a name="create-a-graphical-date-picker-control"></a>Een grafische datumkiezer maken

Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Het script begint met het laden van twee .NET Framework-klassen: **System.Drawing** en **System.Windows.Forms**.
Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **Windows.Forms.Form**; die zorgt voor een leeg formulier of Hiermee bepaalt u venster waaraan u kunt beginnen met het toevoegen.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

In dit voorbeeld waarden aan vier eigenschappen van deze klasse worden toegewezen met behulp van de **eigenschap** eigenschap en hash-tabel.

1. **StartPosition zijn**: Als u deze eigenschap niet toevoegt, wordt in Windows een locatie geselecteerd als het formulier wordt geopend.
   Als deze eigenschap instelt op **CenterScreen**, u bent automatisch weergeven van het formulier in het midden van het scherm telkens worden geladen.

2. **Grootte**: Dit is de grootte van het formulier, in pixels.
   Dit script maakt u een formulier 243 pixels breed 230 pixels hoog is.

3. **Tekst**: Hiermee wordt de titel van het venster.

4. **Bovenste**: Als deze eigenschap instelt op `$true`, u kunt afdwingen dat het venster te openen op een andere openstaande vensters en dialoogvensters.

Vervolgens maken en voeg een kalenderbesturingselement in het formulier.
In dit voorbeeld wordt de huidige dag niet gemarkeerd of omcirkeld.
Gebruikers kunnen slechts één dag in de kalender in één keer selecteren.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

Maak vervolgens een **OK** knop voor het formulier.
Geef de grootte en het gedrag van de **OK** knop.
In dit voorbeeld is de positie van de knop 165 pixels vanaf de bovenkant van het formulier en 38 pixels vanaf de linkerkant.
De hoogte van de knop is 23 pixels, terwijl de lengte van de knop 75 pixels is.
Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Op deze manier maakt u een **annuleren** knop.
De **annuleren** knop is 165 pixels vanaf de bovenkant, maar 113 pixels vanaf de linkerrand van het venster.

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Voeg de volgende regel code om weer te geven van het formulier in Windows.

```powershell
$result = $form.ShowDialog()
```

Ten slotte de code binnen de `if` blok geeft Windows wat te doen met het formulier wanneer gebruikers een dag in de kalender selecteren en klik vervolgens op de **OK** of drukt u op de **Enter** sleutel.
Windows PowerShell wordt de geselecteerde datum weergegeven voor gebruikers.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Zie ook

- [Hey Scripting Guy:  Waarom werken de voorbeelden van deze PowerShell-GUI niet?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell Tip of the Week:  Een grafische datumkiezer maken](https://technet.microsoft.com/library/ff730942.aspx)