---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Items selecteren in een keuzelijst
description: In dit artikel wordt beschreven hoe u een besturings element keuze lijst maakt met behulp van de functies voor het maken van .NET Framework formulier in Windows Power shell.
ms.openlocfilehash: cfd6110a9cfcc3cea891d68d8ce7be5b332a949a
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501045"
---
# <a name="selecting-items-from-a-list-box"></a>Items selecteren in een keuzelijst

Gebruik Windows Power Shell 3,0 en latere versies om een dialoog venster te maken waarmee gebruikers items kunnen selecteren in een besturings element keuze lijst.

## <a name="create-a-list-box-control-and-select-items-from-it"></a>Een besturings element keuze lijst maken en items hiervan selecteren

Kopieer en plak het volgende in Windows PowerShell ISE en sla het vervolgens op als Windows Power shell-script (. ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

Het script begint met het laden van twee .NET Framework klassen: **System. Drawing** en **System. Windows. Forms**. Vervolgens start u een nieuw exemplaar van het .NET Framework-klassen **systeem. Windows. Forms. Form**; Dit biedt een leeg formulier of venster waaraan u besturings elementen kunt toevoegen.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

Nadat u een exemplaar van de formulier klasse hebt gemaakt, wijst u waarden toe aan drie eigenschappen van deze klasse.

- **SMS.** Dit wordt de titel van het venster.

- **Size.** Dit is de grootte van het formulier, in pixels. Met het voor gaande script maakt u een formulier dat 300 pixels breed is en 200 pixels hoog.

- **StartingPosition.** Deze optionele eigenschap wordt ingesteld op **CenterScreen** in het voor gaande script.
  Als u deze eigenschap niet toevoegt, selecteert Windows een locatie wanneer het formulier wordt geopend. Door de **StartingPosition** in te stellen op **CenterScreen**, wordt het formulier telkens wanneer het wordt geladen automatisch in het midden van het scherm weer gegeven.

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Maak vervolgens een knop **OK** voor uw formulier. Geef de grootte en het gedrag op van de knop **OK** . In dit voor beeld is de knop positie 120 pixels van de bovenrand van het formulier en 75 pixels vanaf de linkerrand. De knop hoogte is 23 pixels en de knop lengte is 75 pixels. Het script maakt gebruik van vooraf gedefinieerde Windows Forms typen om het knop gedrag te bepalen.

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

Op dezelfde manier maakt u een knop **Annuleren** . De knop **Annuleren** is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerrand van het venster.

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

Geef vervolgens label tekst op in het venster waarin de informatie wordt beschreven die gebruikers moeten opgeven. In dit geval wilt u dat gebruikers een computer selecteren.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

Voeg het besturings element (in dit geval een keuze lijst) toe waarmee gebruikers de informatie kunnen opgeven die u in de label tekst hebt beschreven. Er zijn veel andere besturings elementen die u kunt Toep assen naast keuze lijsten. Zie [System. Windows. Forms naam ruimte](/dotnet/api/system.windows.forms) op MSDN voor meer besturings elementen.

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

In de volgende sectie geeft u de waarden op die u in de keuze lijst wilt weer geven voor gebruikers.

> [!NOTE]
> In de keuze lijst die door dit script wordt gemaakt, is slechts één selectie toegestaan. Als u een besturings element keuze lijst wilt maken dat meerdere selecties toestaat, geeft u een waarde op voor de eigenschap **SelectionMode** , op de volgende manier: `$listBox.SelectionMode = 'MultiExtended'` . Zie [keuze lijsten met meerdere keuze mogelijkheden](Multiple-selection-List-Boxes.md)voor meer informatie.

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

Voeg het besturings element keuze lijst aan het formulier toe en geef Windows opdracht om het formulier te openen hierop andere vensters en dialoog vensters wanneer deze wordt geopend.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Voeg de volgende regel code toe om het formulier in Windows weer te geven.

```powershell
$result = $form.ShowDialog()
```

Ten slotte geeft de code in het **if** -blok aan Windows wat er moet worden gedaan met het formulier nadat gebruikers een optie in de keuze lijst hebben geselecteerd, en klik vervolgens op de knop **OK** of druk op de **Enter** -toets.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>Zie ook

- [GitHub: de WinFormsExampleUpdates van Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows Power shell-Tip van de week: items selecteren in een keuze lijst](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))
