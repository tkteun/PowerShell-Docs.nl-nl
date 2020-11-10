---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Meerdere selectielijstvelden
description: In dit artikel wordt beschreven hoe u een keuze lijst met meerdere selectie vakjes kunt maken met behulp van de functies .NET Framework formulier maken in Windows Power shell.
ms.openlocfilehash: 2724188695f054d1115b385987cda8a578c102de
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391524"
---
# <a name="multiple-selection-list-boxes"></a>Keuze lijsten met meerdere keuze mogelijkheden

Gebruik Windows Power Shell 3,0 en hoger om een besturings element keuze lijst met meerdere keuze mogelijkheden te maken in een aangepast Windows-formulier.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Besturings elementen keuze lijst maken waarmee meerdere selecties mogelijk zijn

Kopieer en plak het volgende in Windows PowerShell ISE en sla het vervolgens op als Windows Power shell-script (. ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

Het script begint met het laden van twee .NET Framework klassen: **System. Drawing** en **System. Windows. Forms**. Vervolgens start u een nieuw exemplaar van het .NET Framework-klassen **systeem. Windows. Forms. Form** ; Dit biedt een leeg formulier of venster waaraan u besturings elementen kunt toevoegen.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Nadat u een exemplaar van de formulier klasse hebt gemaakt, wijst u waarden toe aan drie eigenschappen van deze klasse.

- **SMS.** Dit wordt de titel van het venster.

- **Size.** Dit is de grootte van het formulier, in pixels. Met het voor gaande script maakt u een formulier dat 300 pixels breed is en 200 pixels hoog.

- **StartingPosition.** Deze optionele eigenschap wordt ingesteld op **CenterScreen** in het voor gaande script.
  Als u deze eigenschap niet toevoegt, selecteert Windows een locatie wanneer het formulier wordt geopend. Door de **StartingPosition** in te stellen op **CenterScreen** , wordt het formulier telkens wanneer het wordt geladen automatisch in het midden van het scherm weer gegeven.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Maak vervolgens een knop **OK** voor uw formulier. Geef de grootte en het gedrag op van de knop **OK** . In dit voor beeld is de knop positie 120 pixels van de bovenrand van het formulier en 75 pixels vanaf de linkerrand. De knop hoogte is 23 pixels en de knop lengte is 75 pixels. Het script maakt gebruik van vooraf gedefinieerde Windows Forms typen om het knop gedrag te bepalen.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Op dezelfde manier maakt u een knop **Annuleren** . De knop **Annuleren** is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerrand van het venster.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Geef vervolgens label tekst op in het venster waarin de informatie wordt beschreven die gebruikers moeten opgeven.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

Voeg het besturings element (in dit geval een keuze lijst) toe waarmee gebruikers de informatie kunnen opgeven die u in de label tekst hebt beschreven. Er zijn veel andere besturings elementen die u kunt Toep assen naast tekst vakken. Zie [System. Windows. Forms naam ruimte](/dotnet/api/system.windows.forms)voor meer besturings elementen.

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

Hier geeft u op hoe u gebruikers in staat wilt stellen om meerdere waarden te selecteren in de lijst.

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

In de volgende sectie geeft u de waarden op die u in de keuze lijst wilt weer geven voor gebruikers.

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

De maximum hoogte van het besturings element keuze lijst opgeven.

```powershell
$listBox.Height = 70
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

Ten slotte geeft de code in het **if** -blok aan Windows wat er moet worden gedaan met het formulier nadat gebruikers een of meer opties in de keuze lijst hebben geselecteerd, en klik vervolgens op de knop **OK** of druk op de **Enter** -toets.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Zie ook

- [Weekend scripter: Power shell GUI-voor beelden worden hersteld](https://devblogs.microsoft.com/scripting/weekend-scripter-fixing-powershell-gui-examples/)
- [GitHub: de WinFormsExampleUpdates van Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows Power shell-Tip van de week: meervoudige selectie vakken-en meer!](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730950(v=technet.10))
