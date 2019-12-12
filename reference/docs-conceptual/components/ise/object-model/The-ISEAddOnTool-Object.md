---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISEAddOnTool-object
ms.openlocfilehash: c71602d200b941ed4fb142b9c35f0fe68982e3e9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028999"
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="2672b-103">Het ISEAddOnTool-object</span><span class="sxs-lookup"><span data-stu-id="2672b-103">The ISEAddOnTool Object</span></span>

<span data-ttu-id="2672b-104">Een **ISEAddonTool** -object vertegenwoordigt een geïnstalleerd add-on hulp programma dat extra functionaliteit biedt ToWindows Power shell ISE.</span><span class="sxs-lookup"><span data-stu-id="2672b-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="2672b-105">Een voor beeld is het hulp programma **opdrachten** dat u kunt weer geven door te klikken op **weer geven**en vervolgens **op invoeg toepassing opdracht weer geven**.</span><span class="sxs-lookup"><span data-stu-id="2672b-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="2672b-106">Dit hulp programma is vervolgens toegankelijk voor u door de verschillende beschik bare **ISEAddOnTool** -objecten te bewerken.</span><span class="sxs-lookup"><span data-stu-id="2672b-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

<span data-ttu-id="2672b-107">Elk hulp programma voor invoeg toepassingen kan worden gekoppeld aan het verticale deel venster of het horizontale deel venster.</span><span class="sxs-lookup"><span data-stu-id="2672b-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="2672b-108">Het verticale deel venster is gedokt aan de rechter kant van Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2672b-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="2672b-109">Het horizontale deel venster is gedokt aan de onderkant.</span><span class="sxs-lookup"><span data-stu-id="2672b-109">The horizontal pane is docked to the bottom edge.</span></span>

<span data-ttu-id="2672b-110">Op elk Power shell-tabblad in Windows PowerShell ISE kan een eigen set hulpprogram ma's voor toevoegen zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="2672b-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="2672b-111">Zie [$psISE. CurrentPowerShellTab. HorizontalAddOnTools](The-PowerShellTab-Object.md) en [$psISE. CurrentPowerShellTab. VerticalAddOnTools](The-PowerShellTab-Object.md) om toegang te krijgen tot de verzameling hulpprogram ma's die beschikbaar is op het geselecteerde tabblad of op dezelfde eigenschappen van een van de **PowerShellTab** -objecten in het verzamelings object [$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md) .</span><span class="sxs-lookup"><span data-stu-id="2672b-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="2672b-112">Methoden</span><span class="sxs-lookup"><span data-stu-id="2672b-112">Methods</span></span>

<span data-ttu-id="2672b-113">Er zijn geen Windows PowerShell ISE-specifieke methoden beschikbaar voor objecten van deze klasse.</span><span class="sxs-lookup"><span data-stu-id="2672b-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="2672b-114">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="2672b-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="2672b-115">Beheer</span><span class="sxs-lookup"><span data-stu-id="2672b-115">Control</span></span>

<span data-ttu-id="2672b-116">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="2672b-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="2672b-117">De eigenschap **Control** biedt Lees toegang tot veel van de details van het hulp programma opdrachten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="2672b-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### <a name="isvisible"></a><span data-ttu-id="2672b-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="2672b-118">IsVisible</span></span>

<span data-ttu-id="2672b-119">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="2672b-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="2672b-120">De eigenschap Boolean die aangeeft of het invoeg programma momenteel zichtbaar is in het toegewezen deel venster.</span><span class="sxs-lookup"><span data-stu-id="2672b-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="2672b-121">Als deze zichtbaar is, kunt u de eigenschap **IsVisible** instellen op **$False** om het hulp programma te verbergen of de eigenschap **IsVisible** instellen op **$True** om een invoeg toepassing zichtbaar te maken op het Power shell-tabblad. Houd er rekening mee dat na het verbergen van een invoeg toepassing niet meer toegankelijk is via de objecten **CurrentVisibleHorizontalTool** of **CurrentVisibleVerticalTool** en daarom niet zichtbaar kan worden gemaakt met behulp van deze eigenschap voor dat object.</span><span class="sxs-lookup"><span data-stu-id="2672b-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a><span data-ttu-id="2672b-122">Naam</span><span class="sxs-lookup"><span data-stu-id="2672b-122">Name</span></span>

<span data-ttu-id="2672b-123">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="2672b-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="2672b-124">De alleen-lezen eigenschap waarmee de naam van het hulp programma voor toevoegen wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2672b-124">The read-only property that gets the name of the add-on tool.</span></span>

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a><span data-ttu-id="2672b-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2672b-125">See Also</span></span>

- [<span data-ttu-id="2672b-126">Het ISEAddOnToolCollection-object</span><span class="sxs-lookup"><span data-stu-id="2672b-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="2672b-127">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="2672b-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2672b-128">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="2672b-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
