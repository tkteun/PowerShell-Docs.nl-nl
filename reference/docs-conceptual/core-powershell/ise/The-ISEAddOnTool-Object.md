---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEAddOnTool-object
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954803"
---
# <a name="the-iseaddontool-object"></a>Het ISEAddOnTool-object

Een **ISEAddonTool** object vertegenwoordigt een geïnstalleerde invoegtoepassing hulpprogramma dat aanvullende functionaliteit voor Windows PowerShell ISE biedt. Een voorbeeld is de **opdrachten** hulpprogramma dat u kunt weergeven door te klikken op **weergave**, klikt u vervolgens **weergeven opdracht invoegtoepassing**. Dit hulpprogramma vervolgens toegankelijk is voor u het bewerken van de verschillende beschikbare **ISEAddOnTool** objecten.

Elke invoegtoepassing hulpprogramma kan worden gekoppeld aan het deelvenster met verticale of horizontale deelvenster. De verticale deelvenster is de rechterrand van Windows PowerShell ISE gedokt. De horizontale deelvenster is de onderrand gedokt.

Elk tabblad PowerShell in Windows PowerShell ISE kunt hebben een eigen set hulpprogramma's voor invoegtoepassing geïnstalleerd. Zie [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) en [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) voor toegang tot de verzameling van hulpprogramma's beschikbaar zijn voor het momenteel geselecteerde tabblad of de dezelfde eigenschappen op een van de **PowerShellTab** objecten in de [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) verzamelingsobject.

## <a name="methods"></a>Methoden

Er zijn geen Windows PowerShell ISE-specifieke-methoden beschikbaar voor objecten van deze klasse.

## <a name="properties"></a>Eigenschappen

### <a name="control"></a>Beheer

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

De **besturingselement** eigenschap leestoegang tot veel van de details van het hulpprogramma van de invoegtoepassing opdrachten bevat.

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

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

De eigenschap van het Boolean-waarde die aangeeft of het hulpprogramma invoegtoepassing zichtbaar in het deelvenster toegewezen is. Als zichtbaar is, kunt u instellen de **IsVisible** eigenschap **$false** verbergen van het hulpprogramma of stel de **IsVisible** eigenschap **$true** om ervoor te een invoegtoepassing hulpprogramma zichtbaar op het tabblad PowerShell. Houd er rekening mee dat wanneer een invoegtoepassing hulpprogramma verborgen is, niet meer toegankelijk zijn via is de **CurrentVisibleHorizontalTool** of **CurrentVisibleVerticalTool** objecten en daarom kan niet worden doorgevoerd zichtbaar met behulp van Deze eigenschap voor dat object.

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a>Naam

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap die de naam van het hulpprogramma invoegtoepassing krijgt.

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a>Zie ook

- [Het Object ISEAddOnToolCollection](The-ISEAddOnToolCollection-Object.md)
- [Doel van de Windows PowerShell ISE-objectmodel Scripting](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)