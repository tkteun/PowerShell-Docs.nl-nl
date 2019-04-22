---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een grafische datumkiezer maken
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59506798"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="a3175-103">Een grafische datumkiezer maken</span><span class="sxs-lookup"><span data-stu-id="a3175-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="a3175-104">Gebruik Windows PowerShell 3.0 en latere versies naar een formulier maken met een grafische, agenda-stijl-besturingselement waarmee gebruikers een dag van de maand selecteren.</span><span class="sxs-lookup"><span data-stu-id="a3175-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="a3175-105">Een grafische datumkiezer maken</span><span class="sxs-lookup"><span data-stu-id="a3175-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="a3175-106">Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).</span><span class="sxs-lookup"><span data-stu-id="a3175-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="a3175-107">Het script begint met het laden van twee .NET Framework-klassen: **System.Drawing** en **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="a3175-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span>
<span data-ttu-id="a3175-108">Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **Windows.Forms.Form**; die zorgt voor een leeg formulier of Hiermee bepaalt u venster waaraan u kunt beginnen met het toevoegen.</span><span class="sxs-lookup"><span data-stu-id="a3175-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="a3175-109">In dit voorbeeld waarden aan vier eigenschappen van deze klasse worden toegewezen met behulp van de **eigenschap** eigenschap en hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="a3175-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="a3175-110">**StartPosition zijn**: Als u deze eigenschap niet toevoegt, wordt in Windows een locatie geselecteerd als het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="a3175-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span>
   <span data-ttu-id="a3175-111">Als deze eigenschap instelt op **CenterScreen**, u bent automatisch weergeven van het formulier in het midden van het scherm telkens worden geladen.</span><span class="sxs-lookup"><span data-stu-id="a3175-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="a3175-112">**Grootte**: Dit is de grootte van het formulier, in pixels.</span><span class="sxs-lookup"><span data-stu-id="a3175-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="a3175-113">Dit script maakt u een formulier 243 pixels breed 230 pixels hoog is.</span><span class="sxs-lookup"><span data-stu-id="a3175-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="a3175-114">**Tekst**: Hiermee wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="a3175-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="a3175-115">**Bovenste**: Als deze eigenschap instelt op `$true`, u kunt afdwingen dat het venster te openen op een andere openstaande vensters en dialoogvensters.</span><span class="sxs-lookup"><span data-stu-id="a3175-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="a3175-116">Vervolgens maken en voeg een kalenderbesturingselement in het formulier.</span><span class="sxs-lookup"><span data-stu-id="a3175-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="a3175-117">In dit voorbeeld wordt de huidige dag niet gemarkeerd of omcirkeld.</span><span class="sxs-lookup"><span data-stu-id="a3175-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="a3175-118">Gebruikers kunnen slechts één dag in de kalender in één keer selecteren.</span><span class="sxs-lookup"><span data-stu-id="a3175-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="a3175-119">Maak vervolgens een **OK** knop voor het formulier.</span><span class="sxs-lookup"><span data-stu-id="a3175-119">Next, create an **OK** button for your form.</span></span>
<span data-ttu-id="a3175-120">Geef de grootte en het gedrag van de **OK** knop.</span><span class="sxs-lookup"><span data-stu-id="a3175-120">Specify the size and behavior of the **OK** button.</span></span>
<span data-ttu-id="a3175-121">In dit voorbeeld is de positie van de knop 165 pixels vanaf de bovenkant van het formulier en 38 pixels vanaf de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="a3175-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span>
<span data-ttu-id="a3175-122">De hoogte van de knop is 23 pixels, terwijl de lengte van de knop 75 pixels is.</span><span class="sxs-lookup"><span data-stu-id="a3175-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span>
<span data-ttu-id="a3175-123">Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.</span><span class="sxs-lookup"><span data-stu-id="a3175-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="a3175-124">Op deze manier maakt u een **annuleren** knop.</span><span class="sxs-lookup"><span data-stu-id="a3175-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="a3175-125">De **annuleren** knop is 165 pixels vanaf de bovenkant, maar 113 pixels vanaf de linkerrand van het venster.</span><span class="sxs-lookup"><span data-stu-id="a3175-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="a3175-126">Voeg de volgende regel code om weer te geven van het formulier in Windows.</span><span class="sxs-lookup"><span data-stu-id="a3175-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="a3175-127">Ten slotte de code binnen de `if` blok geeft Windows wat te doen met het formulier wanneer gebruikers een dag in de kalender selecteren en klik vervolgens op de **OK** of drukt u op de **Enter** sleutel.</span><span class="sxs-lookup"><span data-stu-id="a3175-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span>
<span data-ttu-id="a3175-128">Windows PowerShell wordt de geselecteerde datum weergegeven voor gebruikers.</span><span class="sxs-lookup"><span data-stu-id="a3175-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="a3175-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a3175-129">See Also</span></span>

- [<span data-ttu-id="a3175-130">Hey Scripting Guy:  Waarom werken de voorbeelden van deze PowerShell-GUI niet?</span><span class="sxs-lookup"><span data-stu-id="a3175-130">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="a3175-131">GitHub: Dave Wyatt's WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="a3175-131">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="a3175-132">Windows PowerShell Tip of the Week:  Een grafische datumkiezer maken</span><span class="sxs-lookup"><span data-stu-id="a3175-132">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)