---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Een aangepast invoervak maken
description: In dit artikel wordt beschreven hoe u een aangepast invoervak maakt met behulp van de functies .NET Framework formulier maken in Windows Power shell.
ms.openlocfilehash: b7786706d2461c329da429c1bd4971d7dc874d6d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390079"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="06054-104">Een aangepast invoervak maken</span><span class="sxs-lookup"><span data-stu-id="06054-104">Creating a Custom Input Box</span></span>

<span data-ttu-id="06054-105">Een grafisch aangepast invoervak in een script maken met behulp van Microsoft .NET Framework-formulier: functies bouwen in Windows Power Shell 3,0 en latere versies.</span><span class="sxs-lookup"><span data-stu-id="06054-105">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="06054-106">Een aangepast, grafisch invoervak maken</span><span class="sxs-lookup"><span data-stu-id="06054-106">Create a custom, graphical input box</span></span>

<span data-ttu-id="06054-107">Kopieer en plak het volgende in Windows PowerShell ISE en sla het vervolgens op als Windows Power shell-script (. ps1).</span><span class="sxs-lookup"><span data-stu-id="06054-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="06054-108">Het script begint met het laden van twee .NET Framework klassen: **System. Drawing** en **System. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="06054-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="06054-109">Vervolgens start u een nieuw exemplaar van het .NET Framework-klassen **systeem. Windows. Forms. Form** ; Dit biedt een leeg formulier of venster waaraan u besturings elementen kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="06054-109">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form** ; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="06054-110">Nadat u een exemplaar van de formulier klasse hebt gemaakt, wijst u waarden toe aan drie eigenschappen van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="06054-110">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="06054-111">**SMS.**</span><span class="sxs-lookup"><span data-stu-id="06054-111">**Text.**</span></span> <span data-ttu-id="06054-112">Dit wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="06054-112">This becomes the title of the window.</span></span>

- <span data-ttu-id="06054-113">**Size.**</span><span class="sxs-lookup"><span data-stu-id="06054-113">**Size.**</span></span> <span data-ttu-id="06054-114">Dit is de grootte van het formulier, in pixels.</span><span class="sxs-lookup"><span data-stu-id="06054-114">This is the size of the form, in pixels.</span></span> <span data-ttu-id="06054-115">Met het voor gaande script maakt u een formulier dat 300 pixels breed is en 200 pixels hoog.</span><span class="sxs-lookup"><span data-stu-id="06054-115">The preceding script creates a form that's 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="06054-116">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="06054-116">**StartingPosition.**</span></span> <span data-ttu-id="06054-117">Deze optionele eigenschap wordt ingesteld op **CenterScreen** in het voor gaande script.</span><span class="sxs-lookup"><span data-stu-id="06054-117">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="06054-118">Als u deze eigenschap niet toevoegt, selecteert Windows een locatie wanneer het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="06054-118">If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="06054-119">Door de **StartingPosition** in te stellen op **CenterScreen** , wordt het formulier telkens wanneer het wordt geladen automatisch in het midden van het scherm weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="06054-119">By setting the **StartingPosition** to **CenterScreen** , you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="06054-120">Maak vervolgens een knop **OK** voor uw formulier.</span><span class="sxs-lookup"><span data-stu-id="06054-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="06054-121">Geef de grootte en het gedrag op van de knop **OK** .</span><span class="sxs-lookup"><span data-stu-id="06054-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="06054-122">In dit voor beeld is de knop positie 120 pixels van de bovenrand van het formulier en 75 pixels vanaf de linkerrand.</span><span class="sxs-lookup"><span data-stu-id="06054-122">In this example, the button position is 120 pixels from the form's top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="06054-123">De knop hoogte is 23 pixels en de knop lengte is 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="06054-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="06054-124">Het script maakt gebruik van vooraf gedefinieerde Windows Forms typen om het knop gedrag te bepalen.</span><span class="sxs-lookup"><span data-stu-id="06054-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="06054-125">Op dezelfde manier maakt u een knop **Annuleren** .</span><span class="sxs-lookup"><span data-stu-id="06054-125">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="06054-126">De knop **Annuleren** is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerrand van het venster.</span><span class="sxs-lookup"><span data-stu-id="06054-126">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="06054-127">Geef vervolgens label tekst op in het venster waarin de informatie wordt beschreven die gebruikers moeten opgeven.</span><span class="sxs-lookup"><span data-stu-id="06054-127">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="06054-128">Voeg het besturings element (in dit geval een tekstvak) toe waarmee gebruikers de informatie kunnen opgeven die u in de label tekst hebt beschreven.</span><span class="sxs-lookup"><span data-stu-id="06054-128">Add the control (in this case, a text box) that lets users provide the information you've described in your label text.</span></span> <span data-ttu-id="06054-129">Er zijn veel andere besturings elementen die u kunt Toep assen naast tekst vakken. Zie [System. Windows. Forms naam ruimte](/dotnet/api/system.windows.forms)voor meer besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="06054-129">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms).</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="06054-130">Stel de eigenschap **bovenste** in op **$True** om ervoor te zorgen dat het venster hierop andere open vensters en dialoog vensters opent.</span><span class="sxs-lookup"><span data-stu-id="06054-130">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="06054-131">Voeg vervolgens deze regel code toe om het formulier te activeren en stel de focus in op het tekstvak dat u hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="06054-131">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="06054-132">Voeg de volgende regel code toe om het formulier in Windows weer te geven.</span><span class="sxs-lookup"><span data-stu-id="06054-132">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="06054-133">Ten slotte geeft de code in het **if** -blok aan Windows wat er moet worden gedaan met het formulier nadat gebruikers tekst hebben opgegeven in het tekstvak en klik vervolgens op de knop **OK** of druk op **Enter** .</span><span class="sxs-lookup"><span data-stu-id="06054-133">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="06054-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="06054-134">See Also</span></span>

- <span data-ttu-id="06054-135">[GitHub: de WinFormsExampleUpdates van Dave Wyatt](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="06054-135">[GitHub: Dave Wyatt's WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))</span></span>
- [<span data-ttu-id="06054-136">Windows Power shell-Tip van de week: een aangepast invoervak maken</span><span class="sxs-lookup"><span data-stu-id="06054-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)
