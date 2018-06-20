---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een grafische datumkiezer maken
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 3727c90c314a6fc1b3a338ec60e44259f153d954
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954837"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="9ed88-103">Een grafische datumkiezer maken</span><span class="sxs-lookup"><span data-stu-id="9ed88-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="9ed88-104">Gebruik Windows PowerShell 3.0 en latere versies te maken van een formulier met een grafische, agenda-stijl-besturingselement waarmee gebruikers een dag van de maand selecteren.</span><span class="sxs-lookup"><span data-stu-id="9ed88-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="9ed88-105">Het maken van een besturingselement grafische datum kiezen</span><span class="sxs-lookup"><span data-stu-id="9ed88-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="9ed88-106">Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).</span><span class="sxs-lookup"><span data-stu-id="9ed88-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="9ed88-107">Het script begint met het laden van twee klassen van .NET Framework: **System.Drawing** en **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="9ed88-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="9ed88-108">Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **Windows.Forms.Form**; die zorgt voor een leeg formulier of besturingselementen venster waarnaar u kunt starten toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="9ed88-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="9ed88-109">Nadat u een exemplaar van de klasse van het formulier hebt gemaakt, kunt u de waarden toewijzen aan drie eigenschappen van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="9ed88-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="9ed88-110">**De tekst.**</span><span class="sxs-lookup"><span data-stu-id="9ed88-110">**Text.**</span></span> <span data-ttu-id="9ed88-111">Dit wordt de titel van het venster.</span><span class="sxs-lookup"><span data-stu-id="9ed88-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="9ed88-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="9ed88-112">**Size.**</span></span> <span data-ttu-id="9ed88-113">Dit is de grootte van het formulier in pixels.</span><span class="sxs-lookup"><span data-stu-id="9ed88-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="9ed88-114">Dit script maakt een formulier 243 pixels breed met 230 pixels hoog.</span><span class="sxs-lookup"><span data-stu-id="9ed88-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="9ed88-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="9ed88-115">**StartingPosition.**</span></span> <span data-ttu-id="9ed88-116">Deze optionele eigenschap is ingesteld op **CenterScreen** in het voorgaande script.</span><span class="sxs-lookup"><span data-stu-id="9ed88-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="9ed88-117">Als u deze eigenschap niet toevoegt, wordt een locatie geselecteerd wanneer het formulier wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="9ed88-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="9ed88-118">Door in te stellen de **StartingPosition** naar **CenterScreen**, u automatisch weergeeft het formulier in het midden van het scherm elke keer dat wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="9ed88-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="9ed88-119">Vervolgens maken en voeg vervolgens een kalenderbesturingselement in het formulier.</span><span class="sxs-lookup"><span data-stu-id="9ed88-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="9ed88-120">De huidige dag is niet in dit voorbeeld gemarkeerd of omcirkeld.</span><span class="sxs-lookup"><span data-stu-id="9ed88-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="9ed88-121">Gebruikers kunnen slechts één dag in de kalender in één keer selecteren.</span><span class="sxs-lookup"><span data-stu-id="9ed88-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="9ed88-122">Maak vervolgens een **OK** knop voor het formulier.</span><span class="sxs-lookup"><span data-stu-id="9ed88-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="9ed88-123">Geef de grootte en het gedrag van de **OK** knop.</span><span class="sxs-lookup"><span data-stu-id="9ed88-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="9ed88-124">In dit voorbeeld is de knop positie 165 pixels vanaf de bovenkant van het formulier en 38 pixels van de linkerrand.</span><span class="sxs-lookup"><span data-stu-id="9ed88-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="9ed88-125">De hoogte van de knop wordt 23 pixels wanneer de lengte van de knop 75 pixels.</span><span class="sxs-lookup"><span data-stu-id="9ed88-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="9ed88-126">Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.</span><span class="sxs-lookup"><span data-stu-id="9ed88-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="9ed88-127">Op deze manier maakt u een **annuleren** knop.</span><span class="sxs-lookup"><span data-stu-id="9ed88-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="9ed88-128">De **annuleren** knop 165 pixels vanaf de bovenkant, maar 113 pixels van de linkerrand van het venster is.</span><span class="sxs-lookup"><span data-stu-id="9ed88-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="9ed88-129">Stel de **Topmost** eigenschap **$true** om af te dwingen van het venster te openen op een andere geopende vensters en dialoogvensters.</span><span class="sxs-lookup"><span data-stu-id="9ed88-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="9ed88-130">Voeg de volgende regel code om het formulier in Windows weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9ed88-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="9ed88-131">Ten slotte de code in de **als** blok geeft Windows opdracht wat te doen met het formulier wanneer gebruikers een dag in de kalender selecteren en klik vervolgens op de **OK** of drukt u op de **Enter** sleutel.</span><span class="sxs-lookup"><span data-stu-id="9ed88-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="9ed88-132">Windows PowerShell geeft de geselecteerde datum bij gebruikers.</span><span class="sxs-lookup"><span data-stu-id="9ed88-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="9ed88-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9ed88-133">See Also</span></span>

- [<span data-ttu-id="9ed88-134">Hey Scripting Guy: Waarom werken niet op deze voorbeelden PowerShell GUI?</span><span class="sxs-lookup"><span data-stu-id="9ed88-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="9ed88-135">GitHub: Dave Wyatt van WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="9ed88-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="9ed88-136">Windows PowerShell Tip van de Week: een grafische datum objectkiezer maken</span><span class="sxs-lookup"><span data-stu-id="9ed88-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](http://technet.microsoft.com/library/ff730942.aspx)