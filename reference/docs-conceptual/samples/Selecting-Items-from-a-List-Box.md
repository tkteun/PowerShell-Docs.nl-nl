---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Items selecteren in een keuzelijst
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: e3d52839409a2fd58fbdc924a2b92d96fbecee53
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404353"
---
# <a name="selecting-items-from-a-list-box"></a>Items selecteren in een keuzelijst

Gebruik Windows PowerShell 3.0 en latere versies te maken van een dialoogvenster Hiermee kunnen gebruikers items uit een besturingselement voor een lijst selecteren.

## <a name="create-a-list-box-control-and-select-items-from-it"></a>Een besturingselement voor een lijst maken en items selecteren

Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
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

Het script begint met het laden van twee .NET Framework-klassen: **System.Drawing** en **System.Windows.Forms**. Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **System.Windows.Forms.Form**; die zorgt voor een leeg formulier of Hiermee bepaalt u venster waaraan u kunt beginnen met het toevoegen.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

Nadat u een exemplaar van de klasse van het formulier hebt gemaakt, kunt u de waarden toewijzen aan drie eigenschappen van deze klasse.

- **De tekst.** Hiermee wordt de titel van het venster.

- **De grootte.** Dit is de grootte van het formulier, in pixels. Dit script maakt u een formulier is 300 pixels breed met 200 pixels hoog.

- **StartingPosition.** Deze optionele eigenschap is ingesteld op **CenterScreen** in het vorige script. Als u deze eigenschap niet toevoegt, wordt in Windows een locatie geselecteerd als het formulier wordt geopend. Door in te stellen de **StartingPosition** naar **CenterScreen**, u bent automatisch weergeven van het formulier in het midden van het scherm telkens worden geladen.

```powershell
$form.Text = 'Select a Computer'
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

Geef vervolgens de labeltekst op uw venster dat wordt beschreven welke informatie die u wilt dat gebruikers om te bieden. In dit geval wilt u dat gebruikers om een computer te selecteren.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

Het besturingselement (in dit geval een keuzelijst) waarmee gebruikers kunnen de gegevens hebt die worden beschreven in uw labeltekst toevoegen. Er zijn veel andere besturingselementen die u naast keuzelijsten toepassen kunt. Zie voor meer besturingselementen [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) op MSDN.

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

In de volgende sectie geeft u de waarden die u wilt dat de keuzelijst met invoervak om weer te geven aan gebruikers.

> [!NOTE]
> De keuzelijst met dit script gemaakte kan slechts één selectie. Voor het maken van een keuzelijst waarmee meerdere selecties, Geef een waarde op voor de **SelectionMode** eigenschap, vergelijkbaar met het volgende: `$listBox.SelectionMode = 'MultiExtended'`. Zie voor meer informatie, [meervoudige selectie keuzelijsten](Multiple-selection-List-Boxes.md).

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

Het besturingselement keuzelijst toevoegen aan uw formulier en vertelt u Windows het formulier op andere windows- en dialoogvensters openen wanneer deze wordt geopend.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Voeg de volgende regel code om weer te geven van het formulier in Windows.

```powershell
$result = $form.ShowDialog()
```

Ten slotte de code binnen de **als** blok geeft Windows wat te doen met het formulier wanneer gebruikers een optie in de lijst selecteren en klik vervolgens op de **OK** of drukt u op de **Enter**sleutel.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>Zie ook

- [Hey Scripting Guy:  Waarom werken de voorbeelden van deze PowerShell-GUI niet?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt van WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell Tip of the Week:  Items selecteren in een keuzelijst](https://technet.microsoft.com/library/ff730949.aspx)