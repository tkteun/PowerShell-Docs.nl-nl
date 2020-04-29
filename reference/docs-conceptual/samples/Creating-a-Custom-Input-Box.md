---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Een aangepast invoervak maken
ms.openlocfilehash: ff0588b44169bc276e2833254cec60eda759e2c8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "77706186"
---
# <a name="creating-a-custom-input-box"></a>Een aangepast invoervak maken

Een grafisch aangepast invoervak in een script maken met behulp van Microsoft .NET Framework-formulier: functies bouwen in Windows Power Shell 3,0 en latere versies.

## <a name="create-a-custom-graphical-input-box"></a>Een aangepast, grafisch invoervak maken

Kopieer en plak het volgende in Windows PowerShell ISE en sla het vervolgens op als Windows Power shell-script (. ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
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
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

Het script begint met het laden van twee .NET Framework klassen: **System. Drawing** en **System. Windows. Forms**. Vervolgens start u een nieuw exemplaar van het .NET Framework-klassen **systeem. Windows. Forms. Form**; Dit biedt een leeg formulier of venster waaraan u besturings elementen kunt toevoegen.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Nadat u een exemplaar van de formulier klasse hebt gemaakt, wijst u waarden toe aan drie eigenschappen van deze klasse.

- **SMS.** Dit wordt de titel van het venster.

- **Size.** Dit is de grootte van het formulier, in pixels. Met het voor gaande script maakt u een formulier dat 300 pixels breed is en 200 pixels hoog.

- **StartingPosition.** Deze optionele eigenschap wordt ingesteld op **CenterScreen** in het voor gaande script.
  Als u deze eigenschap niet toevoegt, selecteert Windows een locatie wanneer het formulier wordt geopend. Door de **StartingPosition** in te stellen op **CenterScreen**, wordt het formulier telkens wanneer het wordt geladen automatisch in het midden van het scherm weer gegeven.

```powershell
$form.Text = 'Data Entry Form'
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
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
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

Geef vervolgens label tekst op in het venster waarin de informatie wordt beschreven die gebruikers moeten opgeven.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

Voeg het besturings element (in dit geval een tekstvak) toe waarmee gebruikers de informatie kunnen opgeven die u in de label tekst hebt beschreven. Er zijn veel andere besturings elementen die u kunt Toep assen naast tekst vakken. Zie [System. Windows. Forms naam ruimte](/dotnet/api/system.windows.forms) op MSDN voor meer besturings elementen.

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

Stel de eigenschap **bovenste** in op **$True** om ervoor te zorgen dat het venster hierop andere open vensters en dialoog vensters opent.

```powershell
$form.Topmost = $true
```

Voeg vervolgens deze regel code toe om het formulier te activeren en stel de focus in op het tekstvak dat u hebt gemaakt.

```powershell
$form.Add_Shown({$textBox.Select()})
```

Voeg de volgende regel code toe om het formulier in Windows weer te geven.

```powershell
$result = $form.ShowDialog()
```

Ten slotte geeft de code in het **if** -blok aan Windows wat er moet worden gedaan met het formulier nadat gebruikers tekst hebben opgegeven in het tekstvak en klik vervolgens op de knop **OK** of druk op **Enter** .

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a>Zie ook

- [GitHub: de WinFormsExampleUpdates van Dave Wyatt](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))
- [Windows Power shell-Tip van de week: een aangepast invoervak maken](https://technet.microsoft.com/library/ff730941.aspx)
