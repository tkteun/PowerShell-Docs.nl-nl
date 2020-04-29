---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Een grafische datumkiezer maken
ms.openlocfilehash: b748e301b24ed643488079b547e2da1a5a7a6551
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "77706122"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="a6d93-103">Een grafische datumkiezer maken</span><span class="sxs-lookup"><span data-stu-id="a6d93-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="a6d93-104">Gebruik Windows Power Shell 3,0 en latere versies om een formulier te maken met een grafisch besturings element voor de kalender stijl waarmee gebruikers een dag van de maand kunnen selecteren.</span><span class="sxs-lookup"><span data-stu-id="a6d93-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="a6d93-105">Een besturings element voor een grafische datum kiezer maken</span><span class="sxs-lookup"><span data-stu-id="a6d93-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="a6d93-106">Kopieer en plak het volgende in Windows PowerShell ISE en sla het vervolgens op als Windows Power shell-script (. ps1).</span><span class="sxs-lookup"><span data-stu-id="a6d93-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="a6d93-107">Het script begint met het laden van twee .NET Framework klassen: **System. Drawing** en **System. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="a6d93-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="a6d93-108">Vervolgens start u een nieuwe instantie van de .NET Framework klasse **Windows. Forms. Form**; Dit biedt een leeg formulier of venster waaraan u besturings elementen kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="a6d93-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="a6d93-109">In dit voor beeld worden waarden toegewezen aan vier eigenschappen van deze klasse met behulp van de **eigenschap** Property en de hashtabel.</span><span class="sxs-lookup"><span data-stu-id="a6d93-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="a6d93-110">**Waarde gelijk**: als u deze eigenschap niet toevoegt, wordt door Windows een locatie geselecteerd wanneer het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="a6d93-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="a6d93-111">Als u deze eigenschap instelt op **CenterScreen**, wordt het formulier in het midden van het scherm telkens weer gegeven wanneer het wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="a6d93-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="a6d93-112">**Grootte**: dit is de grootte van het formulier, in pixels.</span><span class="sxs-lookup"><span data-stu-id="a6d93-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="a6d93-113">Met het voor gaande script maakt u een formulier dat 243 pixels breed is en 230 pixels hoog.</span><span class="sxs-lookup"><span data-stu-id="a6d93-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="a6d93-114">**Tekst**: dit wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="a6d93-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="a6d93-115">**Bovenste**: door deze eigenschap in te `$true`stellen op, kunt u ervoor zorgen dat het venster hierop andere open vensters en dialoog vensters opent.</span><span class="sxs-lookup"><span data-stu-id="a6d93-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="a6d93-116">Vervolgens maakt en voegt u vervolgens een besturings element kalender toe aan het formulier.</span><span class="sxs-lookup"><span data-stu-id="a6d93-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="a6d93-117">In dit voor beeld wordt de huidige dag niet gemarkeerd of omcirkeld.</span><span class="sxs-lookup"><span data-stu-id="a6d93-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="a6d93-118">Gebruikers kunnen per keer slechts één dag selecteren in de agenda.</span><span class="sxs-lookup"><span data-stu-id="a6d93-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="a6d93-119">Maak vervolgens een knop **OK** voor uw formulier.</span><span class="sxs-lookup"><span data-stu-id="a6d93-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="a6d93-120">Geef de grootte en het gedrag op van de knop **OK** .</span><span class="sxs-lookup"><span data-stu-id="a6d93-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="a6d93-121">In dit voor beeld is de knop positie 165 pixels van de bovenrand van het formulier en 38 pixels vanaf de linkerrand.</span><span class="sxs-lookup"><span data-stu-id="a6d93-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="a6d93-122">De knop hoogte is 23 pixels en de knop lengte is 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="a6d93-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="a6d93-123">Het script maakt gebruik van vooraf gedefinieerde Windows Forms typen om het knop gedrag te bepalen.</span><span class="sxs-lookup"><span data-stu-id="a6d93-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

<span data-ttu-id="a6d93-124">Op dezelfde manier maakt u een knop **Annuleren** .</span><span class="sxs-lookup"><span data-stu-id="a6d93-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="a6d93-125">De knop **Annuleren** is 165 pixels vanaf de bovenkant, maar 113 pixels vanaf de linkerrand van het venster.</span><span class="sxs-lookup"><span data-stu-id="a6d93-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="a6d93-126">Voeg de volgende regel code toe om het formulier in Windows weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a6d93-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="a6d93-127">Ten slotte krijgt de code in `if` de blok kering van Windows wat te doen met het formulier nadat gebruikers een dag in de agenda hebben geselecteerd. Klik vervolgens op de knop **OK** of druk op **Enter** .</span><span class="sxs-lookup"><span data-stu-id="a6d93-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="a6d93-128">De geselecteerde datum wordt weer gegeven voor gebruikers in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="a6d93-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="a6d93-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a6d93-129">See Also</span></span>

- [<span data-ttu-id="a6d93-130">GitHub: de WinFormsExampleUpdates van Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="a6d93-130">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- <span data-ttu-id="a6d93-131">[Windows Power shell-Tip van de week: een grafische datum kiezer maken](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="a6d93-131">[Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))</span></span>
