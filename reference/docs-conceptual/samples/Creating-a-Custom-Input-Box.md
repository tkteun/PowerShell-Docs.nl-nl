---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Een aangepast invoervak maken
ms.openlocfilehash: 9c1c3c72482157e849c0259e7d2e25ed969a4aab
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030240"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="26ae8-103">Een aangepast invoervak maken</span><span class="sxs-lookup"><span data-stu-id="26ae8-103">Creating a Custom Input Box</span></span>

<span data-ttu-id="26ae8-104">Een grafisch aangepast invoervak in een script maken met behulp van Microsoft .NET Framework-formulier: functies bouwen in Windows Power Shell 3,0 en latere versies.</span><span class="sxs-lookup"><span data-stu-id="26ae8-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="26ae8-105">Een aangepast, grafisch invoervak maken</span><span class="sxs-lookup"><span data-stu-id="26ae8-105">Create a custom, graphical input box</span></span>

<span data-ttu-id="26ae8-106">Kopieer en plak het volgende in Windows PowerShell ISE en sla het vervolgens op als Windows Power shell-script (. ps1).</span><span class="sxs-lookup"><span data-stu-id="26ae8-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="26ae8-107">Het script begint met het laden van twee .NET Framework klassen: **System. Drawing** en **System. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="26ae8-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="26ae8-108">Vervolgens start u een nieuw exemplaar van het .NET Framework-klassen **systeem. Windows. Forms. Form**; Dit biedt een leeg formulier of venster waaraan u besturings elementen kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="26ae8-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="26ae8-109">Nadat u een exemplaar van de formulier klasse hebt gemaakt, wijst u waarden toe aan drie eigenschappen van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="26ae8-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="26ae8-110">**SMS.**</span><span class="sxs-lookup"><span data-stu-id="26ae8-110">**Text.**</span></span> <span data-ttu-id="26ae8-111">Dit wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="26ae8-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="26ae8-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="26ae8-112">**Size.**</span></span> <span data-ttu-id="26ae8-113">Dit is de grootte van het formulier, in pixels.</span><span class="sxs-lookup"><span data-stu-id="26ae8-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="26ae8-114">Met het voor gaande script maakt u een formulier dat 300 pixels breed is en 200 pixels hoog.</span><span class="sxs-lookup"><span data-stu-id="26ae8-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="26ae8-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="26ae8-115">**StartingPosition.**</span></span> <span data-ttu-id="26ae8-116">Deze optionele eigenschap wordt ingesteld op **CenterScreen** in het voor gaande script.</span><span class="sxs-lookup"><span data-stu-id="26ae8-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="26ae8-117">Als u deze eigenschap niet toevoegt, selecteert Windows een locatie wanneer het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="26ae8-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="26ae8-118">Door de **StartingPosition** in te stellen op **CenterScreen**, wordt het formulier telkens wanneer het wordt geladen automatisch in het midden van het scherm weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="26ae8-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="26ae8-119">Maak vervolgens een knop **OK** voor uw formulier.</span><span class="sxs-lookup"><span data-stu-id="26ae8-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="26ae8-120">Geef de grootte en het gedrag op van de knop **OK** .</span><span class="sxs-lookup"><span data-stu-id="26ae8-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="26ae8-121">In dit voor beeld is de knop positie 120 pixels van de bovenrand van het formulier en 75 pixels vanaf de linkerrand.</span><span class="sxs-lookup"><span data-stu-id="26ae8-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="26ae8-122">De knop hoogte is 23 pixels en de knop lengte is 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="26ae8-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="26ae8-123">Het script maakt gebruik van vooraf gedefinieerde Windows Forms typen om het knop gedrag te bepalen.</span><span class="sxs-lookup"><span data-stu-id="26ae8-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="26ae8-124">Op dezelfde manier maakt u een knop **Annuleren** .</span><span class="sxs-lookup"><span data-stu-id="26ae8-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="26ae8-125">De knop **Annuleren** is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerrand van het venster.</span><span class="sxs-lookup"><span data-stu-id="26ae8-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="26ae8-126">Geef vervolgens label tekst op in het venster waarin de informatie wordt beschreven die gebruikers moeten opgeven.</span><span class="sxs-lookup"><span data-stu-id="26ae8-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="26ae8-127">Voeg het besturings element (in dit geval een tekstvak) toe waarmee gebruikers de informatie kunnen opgeven die u in de label tekst hebt beschreven.</span><span class="sxs-lookup"><span data-stu-id="26ae8-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="26ae8-128">Er zijn veel andere besturings elementen die u kunt Toep assen naast tekst vakken. Zie [System. Windows. Forms naam ruimte](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) op MSDN voor meer besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="26ae8-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="26ae8-129">Stel de eigenschap **bovenste** in op **$True** om ervoor te zorgen dat het venster hierop andere open vensters en dialoog vensters opent.</span><span class="sxs-lookup"><span data-stu-id="26ae8-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="26ae8-130">Voeg vervolgens deze regel code toe om het formulier te activeren en stel de focus in op het tekstvak dat u hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="26ae8-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="26ae8-131">Voeg de volgende regel code toe om het formulier in Windows weer te geven.</span><span class="sxs-lookup"><span data-stu-id="26ae8-131">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="26ae8-132">Ten slotte geeft de code in het **if** -blok aan Windows wat er moet worden gedaan met het formulier nadat gebruikers tekst hebben opgegeven in het tekstvak en klik vervolgens op de knop **OK** of druk op **Enter** .</span><span class="sxs-lookup"><span data-stu-id="26ae8-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="26ae8-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="26ae8-133">See Also</span></span>

- [<span data-ttu-id="26ae8-134">Hoi Scripting Guy: Waarom werken deze Power shell GUI-voor beelden niet?</span><span class="sxs-lookup"><span data-stu-id="26ae8-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="26ae8-135">GitHub: de WinFormsExampleUpdates van Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="26ae8-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="26ae8-136">Windows Power shell-Tip van de week: een aangepast invoervak maken</span><span class="sxs-lookup"><span data-stu-id="26ae8-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)
