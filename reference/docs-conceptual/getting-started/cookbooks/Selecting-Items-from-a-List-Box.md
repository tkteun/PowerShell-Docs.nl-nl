---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Items selecteren in een keuzelijst met invoervak
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: 5b41ebfb193062a17abcc6ad6ddf1a2d9241a39e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="79d3c-103">Items selecteren in een keuzelijst met invoervak</span><span class="sxs-lookup"><span data-stu-id="79d3c-103">Selecting Items from a List Box</span></span>
<span data-ttu-id="79d3c-104">Gebruik Windows PowerShell 3.0 en latere versies te maken van een dialoogvenster waarmee gebruikers kunnen selecteren van items uit een keuzelijst.</span><span class="sxs-lookup"><span data-stu-id="79d3c-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="79d3c-105">Maken van een keuzelijstbesturingselement en items selecteren</span><span class="sxs-lookup"><span data-stu-id="79d3c-105">Create a list box control, and select items from it</span></span>
<span data-ttu-id="79d3c-106">Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).</span><span class="sxs-lookup"><span data-stu-id="79d3c-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80

[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")

$form.Controls.Add($listBox) 

$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

<span data-ttu-id="79d3c-107">Het script begint met het laden van twee klassen van .NET Framework: **System.Drawing** en **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="79d3c-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="79d3c-108">Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **System.Windows.Forms.Form**; die zorgt voor een leeg formulier of besturingselementen venster waarnaar u kunt starten toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="79d3c-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="79d3c-109">Nadat u een exemplaar van de klasse van het formulier hebt gemaakt, kunt u de waarden toewijzen aan drie eigenschappen van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="79d3c-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="79d3c-110">**De tekst.**</span><span class="sxs-lookup"><span data-stu-id="79d3c-110">**Text.**</span></span> <span data-ttu-id="79d3c-111">Dit wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="79d3c-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="79d3c-112">**Grootte.**</span><span class="sxs-lookup"><span data-stu-id="79d3c-112">**Size.**</span></span> <span data-ttu-id="79d3c-113">Dit is de grootte van het formulier in pixels.</span><span class="sxs-lookup"><span data-stu-id="79d3c-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="79d3c-114">Dit script maakt een formulier 300 pixels breed door 200 pixels hoog.</span><span class="sxs-lookup"><span data-stu-id="79d3c-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="79d3c-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="79d3c-115">**StartingPosition.**</span></span> <span data-ttu-id="79d3c-116">Deze optionele eigenschap is ingesteld op **CenterScreen** in het voorgaande script.</span><span class="sxs-lookup"><span data-stu-id="79d3c-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="79d3c-117">Als u deze eigenschap niet toevoegt, wordt een locatie geselecteerd wanneer het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="79d3c-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="79d3c-118">Door in te stellen de **StartingPosition** naar **CenterScreen**, u automatisch weergeeft het formulier in het midden van het scherm elke keer dat wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="79d3c-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="79d3c-119">Maak vervolgens een **OK** knop voor het formulier.</span><span class="sxs-lookup"><span data-stu-id="79d3c-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="79d3c-120">Geef de grootte en het gedrag van de **OK** knop.</span><span class="sxs-lookup"><span data-stu-id="79d3c-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="79d3c-121">In dit voorbeeld is de knop positie 120 pixels vanaf de bovenkant van het formulier en 75 pixels van de linkerrand.</span><span class="sxs-lookup"><span data-stu-id="79d3c-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="79d3c-122">De hoogte van de knop wordt 23 pixels wanneer de lengte van de knop 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="79d3c-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="79d3c-123">Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.</span><span class="sxs-lookup"><span data-stu-id="79d3c-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="79d3c-124">Op deze manier maakt u een **annuleren** knop.</span><span class="sxs-lookup"><span data-stu-id="79d3c-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="79d3c-125">De **annuleren** knop is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerkant van het venster.</span><span class="sxs-lookup"><span data-stu-id="79d3c-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="79d3c-126">Geef vervolgens labeltekst op uw venster dat wordt beschreven welke informatie die u wilt dat gebruikers om te bieden.</span><span class="sxs-lookup"><span data-stu-id="79d3c-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="79d3c-127">In dit geval wilt u dat gebruikers een computer selecteren.</span><span class="sxs-lookup"><span data-stu-id="79d3c-127">In this case, you want users to select a computer.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label)
```

<span data-ttu-id="79d3c-128">Het besturingselement (in dit geval een keuzelijst) waarmee gebruikers de informatie die u hebt dat wordt beschreven in de labeltekst toevoegen.</span><span class="sxs-lookup"><span data-stu-id="79d3c-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="79d3c-129">Er zijn veel andere besturingselementen die u naast keuzelijsten toepassen kunt. Zie voor meer besturingselementen [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) op MSDN.</span><span class="sxs-lookup"><span data-stu-id="79d3c-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80
```

<span data-ttu-id="79d3c-130">In de volgende sectie geeft u de waarden die u wilt dat de keuzelijst met invoervak aan gebruikers wilt weergeven.</span><span class="sxs-lookup"><span data-stu-id="79d3c-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="79d3c-131">De keuzelijst met invoervak gemaakt met dit script kan slechts één selectie.</span><span class="sxs-lookup"><span data-stu-id="79d3c-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="79d3c-132">Voor het maken van een keuzelijstbesturingselement waarmee meerdere selecties een waarde opgeven voor de **SelectionMode** -eigenschap op dezelfde manier als volgt: `$listBox.SelectionMode = "MultiExtended"`.</span><span class="sxs-lookup"><span data-stu-id="79d3c-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = "MultiExtended"`.</span></span> <span data-ttu-id="79d3c-133">Zie voor meer informatie [meervoudige selectie keuzelijsten](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="79d3c-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```
[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")
```

<span data-ttu-id="79d3c-134">Het besturingselement keuzelijst toevoegen aan uw formulier en door middel van het formulier op andere vensters en dialoogvensters openen wanneer deze wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="79d3c-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

<span data-ttu-id="79d3c-135">Voeg de volgende regel code om het formulier in Windows weer te geven.</span><span class="sxs-lookup"><span data-stu-id="79d3c-135">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="79d3c-136">Ten slotte de code in de **als** blok geeft Windows opdracht wat te doen met het formulier wanneer gebruikers een optie in de lijst selecteren en klik vervolgens op de **OK** of drukt u op de **Enter**sleutel.</span><span class="sxs-lookup"><span data-stu-id="79d3c-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="79d3c-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="79d3c-137">See Also</span></span>
- [<span data-ttu-id="79d3c-138">Hey Scripting Guy: Waarom werken niet op deze voorbeelden PowerShell GUI?</span><span class="sxs-lookup"><span data-stu-id="79d3c-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="79d3c-139">GitHub: Dave Wyatt van WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="79d3c-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="79d3c-140">Windows PowerShell Tip van de Week: selecteren van Items in een keuzelijst met invoervak</span><span class="sxs-lookup"><span data-stu-id="79d3c-140">Windows PowerShell Tip of the Week:  Selecting Items from a List Box</span></span>](http://technet.microsoft.com/library/ff730949.aspx)

