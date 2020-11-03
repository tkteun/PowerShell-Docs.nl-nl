---
description: De experimentele functies ondersteuning in Power shell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in Power shell-of Power shell-modules kunnen worden gebruikt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over experimentele functies
ms.openlocfilehash: fb13d605607b3f6daaba30cef9e7ee339221191c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252442"
---
# <a name="experimental-features"></a>Experimentele functies

De experimentele functies ondersteuning in Power shell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in Power shell-of Power shell-modules kunnen worden gebruikt.

Een experimentele functie is een onderdeel waar het ontwerp niet is voltooid. De functie is beschikbaar voor gebruikers om te testen en feedback te geven. Zodra een experimentele functie is voltooid, worden de wijzigingen in het ontwerp doorgevoerd. Experimentele functies zijn niet bedoeld om te worden gebruikt in productie, omdat de wijzigingen niet mogen worden opgesplitst.

Experimentele functies zijn standaard uitgeschakeld en moeten expliciet worden ingeschakeld door de gebruiker of beheerder van het systeem.

Ingeschakelde experimentele functies worden vermeld in het `powershell.config.json` bestand in `$PSHOME` voor alle gebruikers of het gebruikersspecifieke configuratie bestand voor een specifieke gebruiker.

> [!NOTE]
> Experimentele functies die in het gebruikers configuratie bestand zijn ingeschakeld, hebben voor rang op experimentele functies die worden vermeld in het systeem configuratie bestand.

## <a name="the-experimental-attribute"></a>Het experimentele kenmerk

Gebruik het `Experimental` kenmerk om een code te declareren als experimenteel.

Gebruik de volgende syntaxis voor het declareren `Experimental` van het kenmerk dat de naam van de experimentele functie oplevert en de actie die moet worden uitgevoerd als de experimentele functie is ingeschakeld:

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

Voor modules moet de de `NameOfExperimentalFeature` volgende indeling volgen `<modulename>.<experimentname>` . De `ExperimentAction` para meter moet worden opgegeven en de enige geldige waarden zijn:

- `Show` betekent dat deze experimentele functie wordt weer gegeven als de functie is ingeschakeld
- `Hide` houdt in dat deze experimentele functie wordt verborgen als de functie is ingeschakeld

### <a name="declaring-experimental-features-in-modules-written-in-c"></a>Experimentele functies declareren in modules die zijn geschreven in C\#

Module auteurs die de experimentele functie vlaggen willen gebruiken, kunnen een cmdlet als experiment declareren met behulp van het- `Experimental` kenmerk.

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a>Experimentele functies declareren in modules die zijn geschreven in Power shell

Module die is geschreven in Power shell kan het kenmerk ook gebruiken `Experimental` voor het declareren van experimentele cmdlets:

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a>Wederzijds exclusieve experimentele functies

Er zijn gevallen waarin een experimentele functie niet naast elkaar kan worden gebruikt met een bestaande functie of een andere experimentele functie.

U kunt bijvoorbeeld een experimentele cmdlet hebben die een bestaande cmdlet overschrijft. De twee versies kunnen niet naast elkaar bestaan. Met deze `ExperimentAction.Hide` instelling kan slechts één van de twee cmdlets tegelijk worden ingeschakeld.

In dit voor beeld maken we een nieuwe experimentele `Invoke-WebRequest` cmdlet.
`InvokeWebRequestCommand` bevat de niet-experimentele implementatie.
`InvokeWebRequestCommandV2` bevat de experimentele versie van de cmdlet.

Door het gebruik van kunt `ExperimentAction.Hide` u slechts één van de twee functies tegelijk inschakelen:

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

Wanneer de `MyWebCmdlets.PSWebCmdletV2` experimentele functie is ingeschakeld, wordt de bestaande `InvokeWebRequestCommand` implementatie verborgen en `InvokeWebRequestCommandV2` biedt de implementatie van `Invoke-WebRequest` .

Hiermee kunnen gebruikers de nieuwe cmdlet uitproberen en feedback geven en vervolgens terugkeren naar de niet-experimentele versie wanneer dit nodig is.

### <a name="experimental-parameters-in-cmdlets"></a>Experimentele para meters in cmdlets

Het `Experimental` kenmerk kan ook worden toegepast op afzonderlijke para meters. Zo kunt u een experimentele set para meters voor een bestaande cmdlet maken in plaats van een geheel nieuwe cmdlet.

Hier volgt een voor beeld in C#:

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

Hier volgt een ander voor beeld in het Power shell-script:

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a>Controleren of een experimentele functie is ingeschakeld

In uw code moet u controleren of uw experimentele functie is ingeschakeld voordat u de juiste actie onderneemt. U kunt bepalen of een experimentele functie is ingeschakeld met behulp `IsEnabled()` van de statische methode op de `System.Management.Automation.ExperimentalFeature` klasse.

Hier volgt een voor beeld in C#:

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

Hier volgt een voor beeld van een Power shell-script:

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a>Zie ook

[Enable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[Disable-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[Get-ExperimentalFeature](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)

