---
description: De experimentele functies ondersteuning in Power shell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in Power shell-of Power shell-modules kunnen worden gebruikt.
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over experimentele functies
ms.openlocfilehash: 82f5ef9838fcbb98e71e362ad00b1ec68f9a9f67
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706105"
---
# <a name="experimental-features"></a><span data-ttu-id="bbdcf-103">Experimentele functies</span><span class="sxs-lookup"><span data-stu-id="bbdcf-103">Experimental Features</span></span>

<span data-ttu-id="bbdcf-104">De experimentele functies ondersteuning in Power shell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in Power shell-of Power shell-modules kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="bbdcf-105">Een experimentele functie is een onderdeel waar het ontwerp niet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="bbdcf-106">De functie is beschikbaar voor gebruikers om te testen en feedback te geven.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="bbdcf-107">Zodra een experimentele functie is voltooid, worden de wijzigingen in het ontwerp doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span> <span data-ttu-id="bbdcf-108">Experimentele functies zijn niet bedoeld om te worden gebruikt in productie, omdat de wijzigingen niet mogen worden opgesplitst.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span>

<span data-ttu-id="bbdcf-109">Experimentele functies zijn standaard uitgeschakeld en moeten expliciet worden ingeschakeld door de gebruiker of beheerder van het systeem.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-109">Experimental features are disabled by default and need to be explicitly enabled by the user or administrator of the system.</span></span>

<span data-ttu-id="bbdcf-110">Ingeschakelde experimentele functies worden vermeld in het `powershell.config.json` bestand in `$PSHOME` voor alle gebruikers of het gebruikersspecifieke configuratie bestand voor een specifieke gebruiker.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-110">Enabled experimental features are listed in the `powershell.config.json` file in `$PSHOME` for all users or the user-specific configuration file for a specific user.</span></span>

> [!NOTE]
> <span data-ttu-id="bbdcf-111">Experimentele functies die in het gebruikers configuratie bestand zijn ingeschakeld, hebben voor rang op experimentele functies die worden vermeld in het systeem configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-111">Experimental features enabled in the user configuration file take precedence over experimental features listed in the system configuration file.</span></span>

## <a name="the-experimental-attribute"></a><span data-ttu-id="bbdcf-112">Het experimentele kenmerk</span><span class="sxs-lookup"><span data-stu-id="bbdcf-112">The Experimental Attribute</span></span>

<span data-ttu-id="bbdcf-113">Gebruik het `Experimental` kenmerk om een code te declareren als experimenteel.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-113">Use the `Experimental` attribute to declare some code as experimental.</span></span>

<span data-ttu-id="bbdcf-114">Gebruik de volgende syntaxis voor het declareren `Experimental` van het kenmerk dat de naam van de experimentele functie oplevert en de actie die moet worden uitgevoerd als de experimentele functie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="bbdcf-114">Use the following syntax to declare the `Experimental` attribute providing the name of the experimental feature and the action to take if the experimental feature is enabled:</span></span>

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

<span data-ttu-id="bbdcf-115">Voor modules moet de de `NameOfExperimentalFeature` volgende indeling volgen `<modulename>.<experimentname>` .</span><span class="sxs-lookup"><span data-stu-id="bbdcf-115">For modules, the `NameOfExperimentalFeature` must follow the form of `<modulename>.<experimentname>`.</span></span> <span data-ttu-id="bbdcf-116">De `ExperimentAction` para meter moet worden opgegeven en de enige geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="bbdcf-116">The `ExperimentAction` parameter must be specified and the only valid values are:</span></span>

- <span data-ttu-id="bbdcf-117">`Show` betekent dat deze experimentele functie wordt weer gegeven als de functie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="bbdcf-117">`Show` means to show this experimental feature if the feature is enabled</span></span>
- <span data-ttu-id="bbdcf-118">`Hide` houdt in dat deze experimentele functie wordt verborgen als de functie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="bbdcf-118">`Hide` means to hide this experimental feature if the feature is enabled</span></span>

### <a name="declaring-experimental-features-in-modules-written-in-c"></a><span data-ttu-id="bbdcf-119">Experimentele functies declareren in modules die zijn geschreven in C\#</span><span class="sxs-lookup"><span data-stu-id="bbdcf-119">Declaring Experimental Features in Modules Written in C\#</span></span>

<span data-ttu-id="bbdcf-120">Module auteurs die de experimentele functie vlaggen willen gebruiken, kunnen een cmdlet als experiment declareren met behulp van het- `Experimental` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-120">Module authors who want to use the Experimental Feature flags can declare a cmdlet as experimental by using the `Experimental` attribute.</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a><span data-ttu-id="bbdcf-121">Experimentele functies declareren in modules die zijn geschreven in Power shell</span><span class="sxs-lookup"><span data-stu-id="bbdcf-121">Declaring Experimental Features in Modules written in PowerShell</span></span>

<span data-ttu-id="bbdcf-122">Module die is geschreven in Power shell kan het kenmerk ook gebruiken `Experimental` voor het declareren van experimentele cmdlets:</span><span class="sxs-lookup"><span data-stu-id="bbdcf-122">Module written in PowerShell can also use the `Experimental` attribute to declare experimental cmdlets:</span></span>

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a><span data-ttu-id="bbdcf-123">Wederzijds exclusieve experimentele functies</span><span class="sxs-lookup"><span data-stu-id="bbdcf-123">Mutually Exclusive Experimental Features</span></span>

<span data-ttu-id="bbdcf-124">Er zijn gevallen waarin een experimentele functie niet naast elkaar kan worden gebruikt met een bestaande functie of een andere experimentele functie.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-124">There are cases where an experimental feature cannot co-exist side-by-side with an existing feature or another experimental feature.</span></span>

<span data-ttu-id="bbdcf-125">U kunt bijvoorbeeld een experimentele cmdlet hebben die een bestaande cmdlet overschrijft.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-125">For example, you can have an experimental cmdlet that overrides an existing cmdlet.</span></span> <span data-ttu-id="bbdcf-126">De twee versies kunnen niet naast elkaar bestaan.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-126">The two versions can't coexist side by side.</span></span> <span data-ttu-id="bbdcf-127">Met deze `ExperimentAction.Hide` instelling kan slechts één van de twee cmdlets tegelijk worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-127">The `ExperimentAction.Hide` setting allows only one of the two cmdlets to be enabled at one time.</span></span>

<span data-ttu-id="bbdcf-128">In dit voor beeld maken we een nieuwe experimentele `Invoke-WebRequest` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-128">In this example, we create a new experimental `Invoke-WebRequest` cmdlet.</span></span>
<span data-ttu-id="bbdcf-129">`InvokeWebRequestCommand` bevat de niet-experimentele implementatie.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-129">`InvokeWebRequestCommand` contains the non-experimental implementation.</span></span>
<span data-ttu-id="bbdcf-130">`InvokeWebRequestCommandV2` bevat de experimentele versie van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-130">`InvokeWebRequestCommandV2` contains the experimental version of the cmdlet.</span></span>

<span data-ttu-id="bbdcf-131">Door het gebruik van kunt `ExperimentAction.Hide` u slechts één van de twee functies tegelijk inschakelen:</span><span class="sxs-lookup"><span data-stu-id="bbdcf-131">The use of `ExperimentAction.Hide` will allow only one of the two features to be enabled at one time:</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

<span data-ttu-id="bbdcf-132">Wanneer de `MyWebCmdlets.PSWebCmdletV2` experimentele functie is ingeschakeld, wordt de bestaande `InvokeWebRequestCommand` implementatie verborgen en `InvokeWebRequestCommandV2` biedt de implementatie van `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="bbdcf-132">When the `MyWebCmdlets.PSWebCmdletV2` experimental feature is enabled, the existing `InvokeWebRequestCommand` implementation is hidden and the `InvokeWebRequestCommandV2` provides the implementation of `Invoke-WebRequest`.</span></span>

<span data-ttu-id="bbdcf-133">Hiermee kunnen gebruikers de nieuwe cmdlet uitproberen en feedback geven en vervolgens terugkeren naar de niet-experimentele versie wanneer dit nodig is.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-133">This allows users to try out the new cmdlet and provide feedback then revert to the non-experimental version when needed.</span></span>

### <a name="experimental-parameters-in-cmdlets"></a><span data-ttu-id="bbdcf-134">Experimentele para meters in cmdlets</span><span class="sxs-lookup"><span data-stu-id="bbdcf-134">Experimental Parameters in Cmdlets</span></span>

<span data-ttu-id="bbdcf-135">Het `Experimental` kenmerk kan ook worden toegepast op afzonderlijke para meters.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-135">The `Experimental` attribute can also be applied to individual parameters.</span></span> <span data-ttu-id="bbdcf-136">Zo kunt u een experimentele set para meters voor een bestaande cmdlet maken in plaats van een geheel nieuwe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-136">This allows you to create an experimental set of parameters for an existing cmdlet rather than an entirely new cmdlet.</span></span>

<span data-ttu-id="bbdcf-137">Hier volgt een voor beeld in C#:</span><span class="sxs-lookup"><span data-stu-id="bbdcf-137">Here is an example in C#:</span></span>

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

<span data-ttu-id="bbdcf-138">Hier volgt een ander voor beeld in het Power shell-script:</span><span class="sxs-lookup"><span data-stu-id="bbdcf-138">Here is a different example in PowerShell script:</span></span>

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a><span data-ttu-id="bbdcf-139">Controleren of een experimentele functie is ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="bbdcf-139">Checking if an Experimental Feature is Enabled</span></span>

<span data-ttu-id="bbdcf-140">In uw code moet u controleren of uw experimentele functie is ingeschakeld voordat u de juiste actie onderneemt.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-140">In your code, you will need to check if your experimental feature is enabled before taking appropriate action.</span></span> <span data-ttu-id="bbdcf-141">U kunt bepalen of een experimentele functie is ingeschakeld met behulp `IsEnabled()` van de statische methode op de `System.Management.Automation.ExperimentalFeature` klasse.</span><span class="sxs-lookup"><span data-stu-id="bbdcf-141">You can determine if an experimental feature is enabled using the static `IsEnabled()` method on the `System.Management.Automation.ExperimentalFeature` class.</span></span>

<span data-ttu-id="bbdcf-142">Hier volgt een voor beeld in C#:</span><span class="sxs-lookup"><span data-stu-id="bbdcf-142">Here is an example in C#:</span></span>

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

<span data-ttu-id="bbdcf-143">Hier volgt een voor beeld van een Power shell-script:</span><span class="sxs-lookup"><span data-stu-id="bbdcf-143">Here is an example in PowerShell script:</span></span>

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a><span data-ttu-id="bbdcf-144">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bbdcf-144">See also</span></span>

[<span data-ttu-id="bbdcf-145">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="bbdcf-145">Enable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[<span data-ttu-id="bbdcf-146">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="bbdcf-146">Disable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[<span data-ttu-id="bbdcf-147">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="bbdcf-147">Get-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)

