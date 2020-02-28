---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Een grafische datumkiezer maken
ms.openlocfilehash: b748e301b24ed643488079b547e2da1a5a7a6551
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706122"
---
# <a name="creating-a-graphical-date-picker"></a>Een grafische datumkiezer maken

Gebruik Windows Power Shell 3,0 en latere versies om een formulier te maken met een grafisch besturings element voor de kalender stijl waarmee gebruikers een dag van de maand kunnen selecteren.

## <a name="create-a-graphical-date-picker-control"></a>Een besturings element voor een grafische datum kiezer maken

Kopieer en plak het volgende in Windows PowerShell ISE en sla het vervolgens op als Windows Power shell-script (. ps1).

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

$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Het script begint met het laden van twee .NET Framework klassen: **System. Drawing** en **System. Windows. Forms**. Vervolgens start u een nieuwe instantie van de .NET Framework klasse **Windows. Forms. Form**; Dit biedt een leeg formulier of venster waaraan u besturings elementen kunt toevoegen.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

In dit voor beeld worden waarden toegewezen aan vier eigenschappen van deze klasse met behulp van de **eigenschap** Property en de hashtabel.

1. **Waarde gelijk**: als u deze eigenschap niet toevoegt, wordt door Windows een locatie geselecteerd wanneer het formulier wordt geopend. Als u deze eigenschap instelt op **CenterScreen**, wordt het formulier in het midden van het scherm telkens weer gegeven wanneer het wordt geladen.

2. **Grootte**: dit is de grootte van het formulier, in pixels.
   Met het voor gaande script maakt u een formulier dat 243 pixels breed is en 230 pixels hoog.

3. **Tekst**: dit wordt de titel van het venster.

4. **Bovenste**: door deze eigenschap in te stellen op `$true`, kunt u het venster dwingen hierop andere open vensters en dialoog vensters te openen.

Vervolgens maakt en voegt u vervolgens een besturings element kalender toe aan het formulier.
In dit voor beeld wordt de huidige dag niet gemarkeerd of omcirkeld.
Gebruikers kunnen per keer slechts één dag selecteren in de agenda.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

Maak vervolgens een knop **OK** voor uw formulier. Geef de grootte en het gedrag op van de knop **OK** . In dit voor beeld is de knop positie 165 pixels van de bovenrand van het formulier en 38 pixels vanaf de linkerrand. De knop hoogte is 23 pixels en de knop lengte is 75 pixels. Het script maakt gebruik van vooraf gedefinieerde Windows Forms typen om het knop gedrag te bepalen.

```powershell
$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

Op dezelfde manier maakt u een knop **Annuleren** .
De knop **Annuleren** is 165 pixels vanaf de bovenkant, maar 113 pixels vanaf de linkerrand van het venster.

```powershell
$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

Voeg de volgende regel code toe om het formulier in Windows weer te geven.

```powershell
$result = $form.ShowDialog()
```

Ten slotte geeft de code binnen het `if`-blok aan dat Windows wat er moet gebeuren met het formulier nadat gebruikers een dag in de agenda hebben geselecteerd, en klik vervolgens op de knop **OK** of druk op **Enter** . De geselecteerde datum wordt weer gegeven voor gebruikers in Windows Power shell.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Zie ook

- [GitHub: de WinFormsExampleUpdates van Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows Power shell-Tip van de week: een grafische datum kiezer maken](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))
