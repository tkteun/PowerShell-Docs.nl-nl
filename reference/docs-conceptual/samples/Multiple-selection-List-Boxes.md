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
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="4e1e7-104">Keuze lijsten met meerdere keuze mogelijkheden</span><span class="sxs-lookup"><span data-stu-id="4e1e7-104">Multiple-selection List Boxes</span></span>

<span data-ttu-id="4e1e7-105">Gebruik Windows Power Shell 3,0 en hoger om een besturings element keuze lijst met meerdere keuze mogelijkheden te maken in een aangepast Windows-formulier.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-105">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="4e1e7-106">Besturings elementen keuze lijst maken waarmee meerdere selecties mogelijk zijn</span><span class="sxs-lookup"><span data-stu-id="4e1e7-106">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="4e1e7-107">Kopieer en plak het volgende in Windows PowerShell ISE en sla het vervolgens op als Windows Power shell-script (. ps1).</span><span class="sxs-lookup"><span data-stu-id="4e1e7-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="4e1e7-108">Het script begint met het laden van twee .NET Framework klassen: **System. Drawing** en **System. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="4e1e7-109">Vervolgens start u een nieuw exemplaar van het .NET Framework-klassen **systeem. Windows. Forms. Form** ; Dit biedt een leeg formulier of venster waaraan u besturings elementen kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-109">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form** ; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="4e1e7-110">Nadat u een exemplaar van de formulier klasse hebt gemaakt, wijst u waarden toe aan drie eigenschappen van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-110">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="4e1e7-111">**SMS.**</span><span class="sxs-lookup"><span data-stu-id="4e1e7-111">**Text.**</span></span> <span data-ttu-id="4e1e7-112">Dit wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-112">This becomes the title of the window.</span></span>

- <span data-ttu-id="4e1e7-113">**Size.**</span><span class="sxs-lookup"><span data-stu-id="4e1e7-113">**Size.**</span></span> <span data-ttu-id="4e1e7-114">Dit is de grootte van het formulier, in pixels.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-114">This is the size of the form, in pixels.</span></span> <span data-ttu-id="4e1e7-115">Met het voor gaande script maakt u een formulier dat 300 pixels breed is en 200 pixels hoog.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-115">The preceding script creates a form that's 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="4e1e7-116">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="4e1e7-116">**StartingPosition.**</span></span> <span data-ttu-id="4e1e7-117">Deze optionele eigenschap wordt ingesteld op **CenterScreen** in het voor gaande script.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-117">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="4e1e7-118">Als u deze eigenschap niet toevoegt, selecteert Windows een locatie wanneer het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-118">If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="4e1e7-119">Door de **StartingPosition** in te stellen op **CenterScreen** , wordt het formulier telkens wanneer het wordt geladen automatisch in het midden van het scherm weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-119">By setting the **StartingPosition** to **CenterScreen** , you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="4e1e7-120">Maak vervolgens een knop **OK** voor uw formulier.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="4e1e7-121">Geef de grootte en het gedrag op van de knop **OK** .</span><span class="sxs-lookup"><span data-stu-id="4e1e7-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="4e1e7-122">In dit voor beeld is de knop positie 120 pixels van de bovenrand van het formulier en 75 pixels vanaf de linkerrand.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-122">In this example, the button position is 120 pixels from the form's top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="4e1e7-123">De knop hoogte is 23 pixels en de knop lengte is 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="4e1e7-124">Het script maakt gebruik van vooraf gedefinieerde Windows Forms typen om het knop gedrag te bepalen.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="4e1e7-125">Op dezelfde manier maakt u een knop **Annuleren** .</span><span class="sxs-lookup"><span data-stu-id="4e1e7-125">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="4e1e7-126">De knop **Annuleren** is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerrand van het venster.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-126">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="4e1e7-127">Geef vervolgens label tekst op in het venster waarin de informatie wordt beschreven die gebruikers moeten opgeven.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-127">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="4e1e7-128">Voeg het besturings element (in dit geval een keuze lijst) toe waarmee gebruikers de informatie kunnen opgeven die u in de label tekst hebt beschreven.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-128">Add the control (in this case, a list box) that lets users provide the information you've described in your label text.</span></span> <span data-ttu-id="4e1e7-129">Er zijn veel andere besturings elementen die u kunt Toep assen naast tekst vakken. Zie [System. Windows. Forms naam ruimte](/dotnet/api/system.windows.forms)voor meer besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-129">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms).</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="4e1e7-130">Hier geeft u op hoe u gebruikers in staat wilt stellen om meerdere waarden te selecteren in de lijst.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-130">Here's how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="4e1e7-131">In de volgende sectie geeft u de waarden op die u in de keuze lijst wilt weer geven voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-131">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="4e1e7-132">De maximum hoogte van het besturings element keuze lijst opgeven.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-132">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="4e1e7-133">Voeg het besturings element keuze lijst aan het formulier toe en geef Windows opdracht om het formulier te openen hierop andere vensters en dialoog vensters wanneer deze wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-133">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it's opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="4e1e7-134">Voeg de volgende regel code toe om het formulier in Windows weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-134">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="4e1e7-135">Ten slotte geeft de code in het **if** -blok aan Windows wat er moet worden gedaan met het formulier nadat gebruikers een of meer opties in de keuze lijst hebben geselecteerd, en klik vervolgens op de knop **OK** of druk op de **Enter** -toets.</span><span class="sxs-lookup"><span data-stu-id="4e1e7-135">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="4e1e7-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4e1e7-136">See Also</span></span>

- [<span data-ttu-id="4e1e7-137">Weekend scripter: Power shell GUI-voor beelden worden hersteld</span><span class="sxs-lookup"><span data-stu-id="4e1e7-137">Weekend Scripter: Fixing PowerShell GUI Examples</span></span>](https://devblogs.microsoft.com/scripting/weekend-scripter-fixing-powershell-gui-examples/)
- [<span data-ttu-id="4e1e7-138">GitHub: de WinFormsExampleUpdates van Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="4e1e7-138">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- <span data-ttu-id="4e1e7-139">[Windows Power shell-Tip van de week: meervoudige selectie vakken-en meer!](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730950(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="4e1e7-139">[Windows PowerShell Tip of the Week: Multi-Select List Boxes - And More!](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730950(v=technet.10))</span></span>
