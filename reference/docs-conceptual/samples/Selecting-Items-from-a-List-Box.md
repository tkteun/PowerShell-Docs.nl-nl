---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Items selecteren in een keuzelijst
ms.openlocfilehash: 55bc9409b0e330a2080781bfd4c586109896258f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030828"
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="7be9f-103">Items selecteren in een keuzelijst</span><span class="sxs-lookup"><span data-stu-id="7be9f-103">Selecting Items from a List Box</span></span>

<span data-ttu-id="7be9f-104">Gebruik Windows Power Shell 3,0 en latere versies om een dialoog venster te maken waarmee gebruikers items kunnen selecteren in een besturings element keuze lijst.</span><span class="sxs-lookup"><span data-stu-id="7be9f-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="7be9f-105">Een besturings element keuze lijst maken en items hiervan selecteren</span><span class="sxs-lookup"><span data-stu-id="7be9f-105">Create a list box control, and select items from it</span></span>

<span data-ttu-id="7be9f-106">Kopieer en plak het volgende in Windows PowerShell ISE en sla het vervolgens op als Windows Power shell-script (. ps1).</span><span class="sxs-lookup"><span data-stu-id="7be9f-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="7be9f-107">Het script begint met het laden van twee .NET Framework klassen: **System. Drawing** en **System. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="7be9f-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="7be9f-108">Vervolgens start u een nieuw exemplaar van het .NET Framework-klassen **systeem. Windows. Forms. Form**; Dit biedt een leeg formulier of venster waaraan u besturings elementen kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="7be9f-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="7be9f-109">Nadat u een exemplaar van de formulier klasse hebt gemaakt, wijst u waarden toe aan drie eigenschappen van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="7be9f-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="7be9f-110">**SMS.**</span><span class="sxs-lookup"><span data-stu-id="7be9f-110">**Text.**</span></span> <span data-ttu-id="7be9f-111">Dit wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="7be9f-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="7be9f-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="7be9f-112">**Size.**</span></span> <span data-ttu-id="7be9f-113">Dit is de grootte van het formulier, in pixels.</span><span class="sxs-lookup"><span data-stu-id="7be9f-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="7be9f-114">Met het voor gaande script maakt u een formulier dat 300 pixels breed is en 200 pixels hoog.</span><span class="sxs-lookup"><span data-stu-id="7be9f-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="7be9f-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="7be9f-115">**StartingPosition.**</span></span> <span data-ttu-id="7be9f-116">Deze optionele eigenschap wordt ingesteld op **CenterScreen** in het voor gaande script.</span><span class="sxs-lookup"><span data-stu-id="7be9f-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="7be9f-117">Als u deze eigenschap niet toevoegt, selecteert Windows een locatie wanneer het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="7be9f-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="7be9f-118">Door de **StartingPosition** in te stellen op **CenterScreen**, wordt het formulier telkens wanneer het wordt geladen automatisch in het midden van het scherm weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7be9f-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="7be9f-119">Maak vervolgens een knop **OK** voor uw formulier.</span><span class="sxs-lookup"><span data-stu-id="7be9f-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="7be9f-120">Geef de grootte en het gedrag op van de knop **OK** .</span><span class="sxs-lookup"><span data-stu-id="7be9f-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="7be9f-121">In dit voor beeld is de knop positie 120 pixels van de bovenrand van het formulier en 75 pixels vanaf de linkerrand.</span><span class="sxs-lookup"><span data-stu-id="7be9f-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="7be9f-122">De knop hoogte is 23 pixels en de knop lengte is 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="7be9f-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="7be9f-123">Het script maakt gebruik van vooraf gedefinieerde Windows Forms typen om het knop gedrag te bepalen.</span><span class="sxs-lookup"><span data-stu-id="7be9f-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="7be9f-124">Op dezelfde manier maakt u een knop **Annuleren** .</span><span class="sxs-lookup"><span data-stu-id="7be9f-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="7be9f-125">De knop **Annuleren** is 120 pixels vanaf de bovenkant, maar 150 pixels vanaf de linkerrand van het venster.</span><span class="sxs-lookup"><span data-stu-id="7be9f-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="7be9f-126">Geef vervolgens label tekst op in het venster waarin de informatie wordt beschreven die gebruikers moeten opgeven.</span><span class="sxs-lookup"><span data-stu-id="7be9f-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="7be9f-127">In dit geval wilt u dat gebruikers een computer selecteren.</span><span class="sxs-lookup"><span data-stu-id="7be9f-127">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="7be9f-128">Voeg het besturings element (in dit geval een keuze lijst) toe waarmee gebruikers de informatie kunnen opgeven die u in de label tekst hebt beschreven.</span><span class="sxs-lookup"><span data-stu-id="7be9f-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="7be9f-129">Er zijn veel andere besturings elementen die u kunt Toep assen naast keuze lijsten. Zie [System. Windows. Forms naam ruimte](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) op MSDN voor meer besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="7be9f-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="7be9f-130">In de volgende sectie geeft u de waarden op die u in de keuze lijst wilt weer geven voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="7be9f-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="7be9f-131">In de keuze lijst die door dit script wordt gemaakt, is slechts één selectie toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7be9f-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="7be9f-132">Als u een besturings element keuze lijst wilt maken dat meerdere selecties toestaat, geeft u een waarde op voor de eigenschap **SelectionMode** , op de volgende manier: `$listBox.SelectionMode = 'MultiExtended'`.</span><span class="sxs-lookup"><span data-stu-id="7be9f-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="7be9f-133">Zie [keuze lijsten met meerdere keuze mogelijkheden](Multiple-selection-List-Boxes.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7be9f-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="7be9f-134">Voeg het besturings element keuze lijst aan het formulier toe en geef Windows opdracht om het formulier te openen hierop andere vensters en dialoog vensters wanneer deze wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="7be9f-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="7be9f-135">Voeg de volgende regel code toe om het formulier in Windows weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7be9f-135">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="7be9f-136">Ten slotte geeft de code in het **if** -blok aan Windows wat er moet worden gedaan met het formulier nadat gebruikers een optie in de keuze lijst hebben geselecteerd, en klik vervolgens op de knop **OK** of druk op de **Enter** -toets.</span><span class="sxs-lookup"><span data-stu-id="7be9f-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="7be9f-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7be9f-137">See Also</span></span>

- [<span data-ttu-id="7be9f-138">Hoi Scripting Guy: Waarom werken deze Power shell GUI-voor beelden niet?</span><span class="sxs-lookup"><span data-stu-id="7be9f-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="7be9f-139">GitHub: de WinFormsExampleUpdates van Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="7be9f-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="7be9f-140">Windows Power shell-Tip van de week: items selecteren in een keuze lijst</span><span class="sxs-lookup"><span data-stu-id="7be9f-140">Windows PowerShell Tip of the Week:  Selecting Items from a List Box</span></span>](https://technet.microsoft.com/library/ff730949.aspx)
