---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een aangepast invoervak maken
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 2d04ad6df65cdb4ff13d136dea47bbba6a01f3a2
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320394"
---
# <a name="creating-a-custom-input-box"></a>Een aangepast invoervak maken

Script voor een grafische aangepast invoervak met behulp van Microsoft .NET Framework bouwen van een formulier functies in Windows PowerShell 3.0 en latere versies.

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

Het script begint met het laden van twee klassen voor .NET Framework: **System.Drawing** en **System.Windows.Forms**. Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **System.Windows.Forms.Form**; die zorgt voor een leeg formulier of Hiermee bepaalt u venster waaraan u kunt beginnen met het toevoegen.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Nadat u een exemplaar van de klasse van het formulier hebt gemaakt, kunt u de waarden toewijzen aan drie eigenschappen van deze klasse.

- **De tekst.** Hiermee wordt de titel van het venster.

- **De grootte.** Dit is de grootte van het formulier, in pixels. Dit script maakt u een formulier is 300 pixels breed met 200 pixels hoog.

- **StartingPosition.** Deze optionele eigenschap is ingesteld op **CenterScreen** in het vorige script. Als u deze eigenschap niet toevoegt, wordt in Windows een locatie geselecteerd als het formulier wordt geopend. Door in te stellen de **StartingPosition** naar **CenterScreen**, u bent automatisch weergeven van het formulier in het midden van het scherm telkens worden geladen.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Maak vervolgens een **OK** knop voor het formulier. Geef de grootte en het gedrag van de **OK** knop. In dit voorbeeld is de positie van de knop 120 pixels vanaf de bovenkant van het formulier, en 75 pixels vanaf de linkerkant. De hoogte van de knop is 23 pixels, terwijl de lengte van de knop 75 pixels is. Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Op deze manier maakt u een **annuleren** knop. De **annuleren** knop is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerrand van het venster.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Geef vervolgens de labeltekst op uw venster dat wordt beschreven welke informatie die u wilt dat gebruikers om te bieden.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

Het besturingselement (in dit geval een tekstvak) waarmee gebruikers kunnen de gegevens hebt die worden beschreven in uw labeltekst toevoegen. Er zijn veel andere besturingselementen die kunt u naast tekstvakken; toepassen Zie voor meer besturingselementen [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) op MSDN.

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

Stel de **Topmost** eigenschap **$true** om af te dwingen van het venster te openen op een andere openstaande vensters en dialoogvensters.

```powershell
$form.Topmost = $true
```

Vervolgens deze regel met code voor het activeren van het formulier toevoegen en de focus ingesteld op het tekstvak dat u hebt gemaakt.

```powershell
$form.Add_Shown({$textBox.Select()})
```

Voeg de volgende regel code om weer te geven van het formulier in Windows.

```powershell
$result = $form.ShowDialog()
```

Ten slotte de code binnen de **als** blok geeft Windows wat te doen met het formulier nadat gebruikers tekst in het tekstvak in en klik vervolgens op de **OK** of drukt u op de **Enter** de sleutel.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a>Zie ook

- [Hey Scripting Guy: waarom deze PowerShell-GUI-voorbeelden werken niet?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt van WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell Tip of the Week: het maken van een aangepast invoervak](https://technet.microsoft.com/library/ff730941.aspx)