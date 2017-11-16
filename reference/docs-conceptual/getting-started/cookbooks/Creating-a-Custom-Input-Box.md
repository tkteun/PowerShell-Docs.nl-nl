---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Maken van een aangepaste invoervak
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 94172102fb81a9b31b7e84188f3e60a372e9cba2
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="4d032-103">Maken van een aangepaste invoervak</span><span class="sxs-lookup"><span data-stu-id="4d032-103">Creating a Custom Input Box</span></span>
<span data-ttu-id="4d032-104">Script een grafische aangepaste invoervak met behulp van Microsoft .NET Framework formulier gebouw functies in Windows PowerShell 3.0 en latere versies.</span><span class="sxs-lookup"><span data-stu-id="4d032-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="4d032-105">Een aangepaste, grafische invoervak maken</span><span class="sxs-lookup"><span data-stu-id="4d032-105">Create a custom, graphical input box</span></span>
<span data-ttu-id="4d032-106">Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).</span><span class="sxs-lookup"><span data-stu-id="4d032-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
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
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label) 

$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox) 

$form.Topmost = $True

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="4d032-107">Het script begint met het laden van twee klassen van .NET Framework: **System.Drawing** en **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="4d032-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="4d032-108">Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **System.Windows.Forms.Form**; die zorgt voor een leeg formulier of besturingselementen venster waarnaar u kunt starten toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="4d032-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="4d032-109">Nadat u een exemplaar van de klasse van het formulier hebt gemaakt, kunt u de waarden toewijzen aan drie eigenschappen van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="4d032-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="4d032-110">**De tekst.**</span><span class="sxs-lookup"><span data-stu-id="4d032-110">**Text.**</span></span> <span data-ttu-id="4d032-111">Dit wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="4d032-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="4d032-112">**Grootte.**</span><span class="sxs-lookup"><span data-stu-id="4d032-112">**Size.**</span></span> <span data-ttu-id="4d032-113">Dit is de grootte van het formulier in pixels.</span><span class="sxs-lookup"><span data-stu-id="4d032-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="4d032-114">Dit script maakt een formulier 300 pixels breed door 200 pixels hoog.</span><span class="sxs-lookup"><span data-stu-id="4d032-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="4d032-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="4d032-115">**StartingPosition.**</span></span> <span data-ttu-id="4d032-116">Deze optionele eigenschap is ingesteld op **CenterScreen** in het voorgaande script.</span><span class="sxs-lookup"><span data-stu-id="4d032-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="4d032-117">Als u deze eigenschap niet toevoegt, wordt een locatie geselecteerd wanneer het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="4d032-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="4d032-118">Door in te stellen de **StartingPosition** naar **CenterScreen**, u automatisch weergeeft het formulier in het midden van het scherm elke keer dat wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="4d032-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="4d032-119">Maak vervolgens een **OK** knop voor het formulier.</span><span class="sxs-lookup"><span data-stu-id="4d032-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="4d032-120">Geef de grootte en het gedrag van de **OK** knop.</span><span class="sxs-lookup"><span data-stu-id="4d032-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="4d032-121">In dit voorbeeld is de knop positie 120 pixels vanaf de bovenkant van het formulier en 75 pixels van de linkerrand.</span><span class="sxs-lookup"><span data-stu-id="4d032-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="4d032-122">De hoogte van de knop wordt 23 pixels wanneer de lengte van de knop 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="4d032-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="4d032-123">Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.</span><span class="sxs-lookup"><span data-stu-id="4d032-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="4d032-124">Op deze manier maakt u een **annuleren** knop.</span><span class="sxs-lookup"><span data-stu-id="4d032-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="4d032-125">De **annuleren** knop is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerkant van het venster.</span><span class="sxs-lookup"><span data-stu-id="4d032-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="4d032-126">Geef vervolgens labeltekst op uw venster dat wordt beschreven welke informatie die u wilt dat gebruikers om te bieden.</span><span class="sxs-lookup"><span data-stu-id="4d032-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label)
```

<span data-ttu-id="4d032-127">Het besturingselement (in dit geval een tekstvak) waarmee gebruikers de informatie die u hebt dat wordt beschreven in de labeltekst toevoegen.</span><span class="sxs-lookup"><span data-stu-id="4d032-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="4d032-128">Er zijn veel andere besturingselementen die u naast tekstvakken toepassen kunt; Zie voor meer besturingselementen [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) op MSDN.</span><span class="sxs-lookup"><span data-stu-id="4d032-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox)
```

<span data-ttu-id="4d032-129">Stel de **Topmost** eigenschap **$True** om af te dwingen van het venster te openen op een andere geopende vensters en dialoogvensters.</span><span class="sxs-lookup"><span data-stu-id="4d032-129">Set the **Topmost** property to **$True** to force the window to open atop other open windows and dialog boxes.</span></span>

```
$form.Topmost = $True
```

<span data-ttu-id="4d032-130">Vervolgens, voeg deze regel code voor het activeren van het formulier en de focus instellen op het tekstvak dat u hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4d032-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="4d032-131">Voeg de volgende regel code om het formulier in Windows weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4d032-131">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="4d032-132">Ten slotte de code in de **als** blok geeft Windows opdracht wat te doen met de vorm nadat gebruikers in het tekstvak tekst en klik vervolgens op de **OK** of drukt u op de **Enter** sleutel.</span><span class="sxs-lookup"><span data-stu-id="4d032-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="4d032-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4d032-133">See Also</span></span>
- [<span data-ttu-id="4d032-134">Hey Scripting Guy: Waarom werken niet op deze voorbeelden PowerShell GUI?</span><span class="sxs-lookup"><span data-stu-id="4d032-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="4d032-135">GitHub: Dave Wyatt van WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="4d032-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="4d032-136">Windows PowerShell Tip van de Week: maken van aangepaste invoervak</span><span class="sxs-lookup"><span data-stu-id="4d032-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](http://technet.microsoft.com/library/ff730941.aspx)

