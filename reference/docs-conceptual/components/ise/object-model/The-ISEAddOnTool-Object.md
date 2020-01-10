---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISEAddOnTool-object
ms.openlocfilehash: a5357005ec1a883f5a14882a42e3150e09ff33a2
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736127"
---
# <a name="the-iseaddontool-object"></a>Het ISEAddOnTool-object

Een **ISEAddonTool** -object vertegenwoordigt een geïnstalleerd add-on hulp programma dat extra functionaliteit biedt ToWindows Power shell ISE. Een voor beeld is het hulp programma **opdrachten** dat u kunt weer geven door te klikken op **weer geven**en vervolgens **op invoeg toepassing opdracht weer geven**. Dit hulp programma is vervolgens toegankelijk voor u door de verschillende beschik bare **ISEAddOnTool** -objecten te bewerken.

Elk hulp programma voor invoeg toepassingen kan worden gekoppeld aan het verticale deel venster of het horizontale deel venster. Het verticale deel venster is gedokt aan de rechter kant van Windows PowerShell ISE. Het horizontale deel venster is gedokt aan de onderkant.

Op elk Power shell-tabblad in Windows PowerShell ISE kan een eigen set hulpprogram ma's voor toevoegen zijn geïnstalleerd. Zie [$psISE. CurrentPowerShellTab. HorizontalAddOnTools](The-PowerShellTab-Object.md) en [$psISE. CurrentPowerShellTab. VerticalAddOnTools](The-PowerShellTab-Object.md) om toegang te krijgen tot de verzameling hulpprogram ma's die beschikbaar is op het geselecteerde tabblad of op dezelfde eigenschappen van een van de **PowerShellTab** -objecten in het verzamelings object [$psISE. PowerShellTabs](The-PowerShellTabCollection-Object.md) .

## <a name="methods"></a>Methoden

Er zijn geen Windows PowerShell ISE-specifieke methoden beschikbaar voor objecten van deze klasse.

## <a name="properties"></a>Eigenschappen

### <a name="control"></a>Beheer

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De eigenschap **Control** biedt Lees toegang tot veel van de details van het hulp programma opdrachten toevoegen.

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
```

```Output
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

### <a name="isvisible"></a>IsVisible

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De eigenschap Boolean die aangeeft of het invoeg programma momenteel zichtbaar is in het toegewezen deel venster. Als deze zichtbaar is, kunt u de eigenschap **IsVisible** instellen op `$false` om het hulp programma te verbergen of de eigenschap **isvisible** instellen op `$true` om een invoeg toepassing zichtbaar te maken op het Power shell-tabblad. Houd er rekening mee dat na het verbergen van een invoeg toepassing niet meer toegankelijk is via de objecten **CurrentVisibleHorizontalTool** of **CurrentVisibleVerticalTool** en daarom niet zichtbaar kan worden gemaakt met behulp van deze eigenschap voor dat object.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Name

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap waarmee de naam van het hulp programma voor toevoegen wordt opgehaald.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
```

```Output
Commands
```

## <a name="see-also"></a>Zie ook

- [Het ISEAddOnToolCollection-object](The-ISEAddOnToolCollection-Object.md)
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
