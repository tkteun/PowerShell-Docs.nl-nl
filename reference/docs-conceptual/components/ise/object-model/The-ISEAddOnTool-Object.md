---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEAddOnTool-object
ms.openlocfilehash: c71602d200b941ed4fb142b9c35f0fe68982e3e9
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028999"
---
# <a name="the-iseaddontool-object"></a>Het ISEAddOnTool-object

Een **ISEAddonTool** object vertegenwoordigt een geïnstalleerde invoegtoepassingen-hulpprogramma dat aanvullende functionaliteit voor Windows PowerShell ISE biedt. Een voorbeeld is de **opdrachten** hulpprogramma die u kunt weergeven door te klikken op **weergave**, klikt u vervolgens **weergeven opdracht invoegtoepassing**. Dit hulpprogramma is vervolgens toegankelijk is voor u door het bewerken van de verschillende beschikbare **ISEAddOnTool** objecten.

Elk hulpprogramma invoegtoepassing kan worden gekoppeld aan het deelvenster met verticale of horizontale deelvenster. De verticale deelvenster is gekoppeld aan de rechterkant van de Windows PowerShell ISE. De horizontale deelvenster is gekoppeld aan de onderkant.

Elk tabblad PowerShell in Windows PowerShell ISE kan een eigen set Add-on-hulpprogramma's geïnstalleerd hebben. Zie [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) en [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) voor toegang tot de verzameling van hulpprogramma's die beschikbaar zijn voor het geselecteerde tabblad of de dezelfde eigenschappen op een van de **PowerShellTab** objecten in de [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) verzamelingsobject.

## <a name="methods"></a>Methoden

Er zijn geen Windows PowerShell ISE-specifieke methoden beschikbaar voor objecten van deze klasse.

## <a name="properties"></a>Properties

### <a name="control"></a>Beheer

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De **besturingselement** eigenschap hebt u leestoegang tot veel van de details van het hulpprogramma van de invoegtoepassing opdrachten.

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

### <a name="isvisible"></a>IsVisible

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De Booleaanse eigenschap die aangeeft of het hulpprogramma invoegtoepassing momenteel weergegeven in het deelvenster met toegewezen wordt. Als het zichtbaar is, kunt u instellen de **IsVisible** eigenschap **$false** instellen of verbergen van het hulpprogramma de **IsVisible** eigenschap **$true** om te maken een invoegtoepassing hulpprogramma zichtbaar in de PowerShell-tabblad. Houd er rekening mee dat als een invoegtoepassing hulpprogramma verborgen is, niet meer toegankelijk zijn via is de **CurrentVisibleHorizontalTool** of **CurrentVisibleVerticalTool** objecten en daarom kan niet worden zichtbaar gemaakt met behulp van Deze eigenschap voor dat object.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Name

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De alleen-lezen eigenschap die haalt u de naam van de invoegtoepassing-hulpprogramma.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a>Zie ook

- [Het ISEAddOnToolCollection-Object](The-ISEAddOnToolCollection-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
