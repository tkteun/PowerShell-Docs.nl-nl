---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een aangepast invoervak maken
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 681a75a28a8fb03eb4442d5e20b32b25a337d540
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954752"
---
# <a name="creating-a-custom-input-box"></a>Een aangepast invoervak maken

Script een grafische aangepaste invoervak met behulp van Microsoft .NET Framework formulier gebouw functies in Windows PowerShell 3.0 en latere versies.

## <a name="create-a-custom-graphical-input-box"></a>Een aangepaste, grafische invoervak maken

Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).

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

Het script begint met het laden van twee klassen van .NET Framework: **System.Drawing** en **System.Windows.Forms**. Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **System.Windows.Forms.Form**; die zorgt voor een leeg formulier of besturingselementen venster waarnaar u kunt starten toe te voegen.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Nadat u een exemplaar van de klasse van het formulier hebt gemaakt, kunt u de waarden toewijzen aan drie eigenschappen van deze klasse.

- **De tekst.** Dit wordt de titel van het venster.

- **Size.** Dit is de grootte van het formulier in pixels. Dit script maakt een formulier 300 pixels breed door 200 pixels hoog.

- **StartingPosition.** Deze optionele eigenschap is ingesteld op **CenterScreen** in het voorgaande script. Als u deze eigenschap niet toevoegt, wordt een locatie geselecteerd wanneer het formulier wordt geopend. Door in te stellen de **StartingPosition** naar **CenterScreen**, u automatisch weergeeft het formulier in het midden van het scherm elke keer dat wordt geladen.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Maak vervolgens een **OK** knop voor het formulier. Geef de grootte en het gedrag van de **OK** knop. In dit voorbeeld is de knop positie 120 pixels vanaf de bovenkant van het formulier en 75 pixels van de linkerrand. De hoogte van de knop wordt 23 pixels wanneer de lengte van de knop 75 pixels. Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Op deze manier maakt u een **annuleren** knop. De **annuleren** knop is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerkant van het venster.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Geef vervolgens labeltekst op uw venster dat wordt beschreven welke informatie die u wilt dat gebruikers om te bieden.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

Het besturingselement (in dit geval een tekstvak) waarmee gebruikers de informatie die u hebt dat wordt beschreven in de labeltekst toevoegen. Er zijn veel andere besturingselementen die u naast tekstvakken toepassen kunt; Zie voor meer besturingselementen [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) op MSDN.

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

Stel de **Topmost** eigenschap **$true** om af te dwingen van het venster te openen op een andere geopende vensters en dialoogvensters.

```powershell
$form.Topmost = $true
```

Vervolgens, voeg deze regel code voor het activeren van het formulier en de focus instellen op het tekstvak dat u hebt gemaakt.

```powershell
$form.Add_Shown({$textBox.Select()})
```

Voeg de volgende regel code om het formulier in Windows weer te geven.

```powershell
$result = $form.ShowDialog()
```

Ten slotte de code in de **als** blok geeft Windows opdracht wat te doen met de vorm nadat gebruikers in het tekstvak tekst en klik vervolgens op de **OK** of drukt u op de **Enter** sleutel.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a>Zie ook

- [Hey Scripting Guy: Waarom werken niet op deze voorbeelden PowerShell GUI?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt van WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell Tip van de Week: maken van aangepaste invoervak](http://technet.microsoft.com/library/ff730941.aspx)