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
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="1696d-103">Een aangepast invoervak maken</span><span class="sxs-lookup"><span data-stu-id="1696d-103">Creating a Custom Input Box</span></span>

<span data-ttu-id="1696d-104">Script voor een grafische aangepast invoervak met behulp van Microsoft .NET Framework bouwen van een formulier functies in Windows PowerShell 3.0 en latere versies.</span><span class="sxs-lookup"><span data-stu-id="1696d-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="1696d-105">Een aangepaste, grafische invoervak maken</span><span class="sxs-lookup"><span data-stu-id="1696d-105">Create a custom, graphical input box</span></span>

<span data-ttu-id="1696d-106">Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).</span><span class="sxs-lookup"><span data-stu-id="1696d-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="1696d-107">Het script begint met het laden van twee klassen voor .NET Framework: **System.Drawing** en **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="1696d-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="1696d-108">Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **System.Windows.Forms.Form**; die zorgt voor een leeg formulier of Hiermee bepaalt u venster waaraan u kunt beginnen met het toevoegen.</span><span class="sxs-lookup"><span data-stu-id="1696d-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="1696d-109">Nadat u een exemplaar van de klasse van het formulier hebt gemaakt, kunt u de waarden toewijzen aan drie eigenschappen van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="1696d-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="1696d-110">**De tekst.**</span><span class="sxs-lookup"><span data-stu-id="1696d-110">**Text.**</span></span> <span data-ttu-id="1696d-111">Hiermee wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="1696d-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="1696d-112">**De grootte.**</span><span class="sxs-lookup"><span data-stu-id="1696d-112">**Size.**</span></span> <span data-ttu-id="1696d-113">Dit is de grootte van het formulier, in pixels.</span><span class="sxs-lookup"><span data-stu-id="1696d-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="1696d-114">Dit script maakt u een formulier is 300 pixels breed met 200 pixels hoog.</span><span class="sxs-lookup"><span data-stu-id="1696d-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="1696d-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="1696d-115">**StartingPosition.**</span></span> <span data-ttu-id="1696d-116">Deze optionele eigenschap is ingesteld op **CenterScreen** in het vorige script.</span><span class="sxs-lookup"><span data-stu-id="1696d-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="1696d-117">Als u deze eigenschap niet toevoegt, wordt in Windows een locatie geselecteerd als het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="1696d-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="1696d-118">Door in te stellen de **StartingPosition** naar **CenterScreen**, u bent automatisch weergeven van het formulier in het midden van het scherm telkens worden geladen.</span><span class="sxs-lookup"><span data-stu-id="1696d-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="1696d-119">Maak vervolgens een **OK** knop voor het formulier.</span><span class="sxs-lookup"><span data-stu-id="1696d-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="1696d-120">Geef de grootte en het gedrag van de **OK** knop.</span><span class="sxs-lookup"><span data-stu-id="1696d-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="1696d-121">In dit voorbeeld is de positie van de knop 120 pixels vanaf de bovenkant van het formulier, en 75 pixels vanaf de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="1696d-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="1696d-122">De hoogte van de knop is 23 pixels, terwijl de lengte van de knop 75 pixels is.</span><span class="sxs-lookup"><span data-stu-id="1696d-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="1696d-123">Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.</span><span class="sxs-lookup"><span data-stu-id="1696d-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="1696d-124">Op deze manier maakt u een **annuleren** knop.</span><span class="sxs-lookup"><span data-stu-id="1696d-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="1696d-125">De **annuleren** knop is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerrand van het venster.</span><span class="sxs-lookup"><span data-stu-id="1696d-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="1696d-126">Geef vervolgens de labeltekst op uw venster dat wordt beschreven welke informatie die u wilt dat gebruikers om te bieden.</span><span class="sxs-lookup"><span data-stu-id="1696d-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="1696d-127">Het besturingselement (in dit geval een tekstvak) waarmee gebruikers kunnen de gegevens hebt die worden beschreven in uw labeltekst toevoegen.</span><span class="sxs-lookup"><span data-stu-id="1696d-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="1696d-128">Er zijn veel andere besturingselementen die kunt u naast tekstvakken; toepassen Zie voor meer besturingselementen [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) op MSDN.</span><span class="sxs-lookup"><span data-stu-id="1696d-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="1696d-129">Stel de **Topmost** eigenschap **$true** om af te dwingen van het venster te openen op een andere openstaande vensters en dialoogvensters.</span><span class="sxs-lookup"><span data-stu-id="1696d-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="1696d-130">Vervolgens deze regel met code voor het activeren van het formulier toevoegen en de focus ingesteld op het tekstvak dat u hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1696d-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="1696d-131">Voeg de volgende regel code om weer te geven van het formulier in Windows.</span><span class="sxs-lookup"><span data-stu-id="1696d-131">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="1696d-132">Ten slotte de code binnen de **als** blok geeft Windows wat te doen met het formulier nadat gebruikers tekst in het tekstvak in en klik vervolgens op de **OK** of drukt u op de **Enter** de sleutel.</span><span class="sxs-lookup"><span data-stu-id="1696d-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="1696d-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1696d-133">See Also</span></span>

- [<span data-ttu-id="1696d-134">Hey Scripting Guy: waarom deze PowerShell-GUI-voorbeelden werken niet?</span><span class="sxs-lookup"><span data-stu-id="1696d-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="1696d-135">GitHub: Dave Wyatt van WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="1696d-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="1696d-136">Windows PowerShell Tip of the Week: het maken van een aangepast invoervak</span><span class="sxs-lookup"><span data-stu-id="1696d-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)