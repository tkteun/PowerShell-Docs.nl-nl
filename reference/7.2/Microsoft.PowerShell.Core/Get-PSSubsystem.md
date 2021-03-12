---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssubsystem?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSubsystem
ms.openlocfilehash: 19129eb8a0b478d10fdbf1e35f15b7f86969b5fb
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194988"
---
# <span data-ttu-id="b6985-102">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="b6985-102">Get-PSSubsystem</span></span>

## <span data-ttu-id="b6985-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b6985-103">SYNOPSIS</span></span>
<span data-ttu-id="b6985-104">Haalt informatie op over de subsystemen die zijn geregistreerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="b6985-104">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="b6985-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b6985-105">SYNTAX</span></span>

### <span data-ttu-id="b6985-106">GetAllSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="b6985-106">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="b6985-107">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="b6985-107">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="b6985-108">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="b6985-108">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="b6985-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b6985-109">DESCRIPTION</span></span>

<span data-ttu-id="b6985-110">Haalt informatie op over de subsystemen die zijn geregistreerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="b6985-110">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="b6985-111">Dit is een experimentele functie.</span><span class="sxs-lookup"><span data-stu-id="b6985-111">This is an experimental feature.</span></span> <span data-ttu-id="b6985-112">Deze cmdlet is alleen beschikbaar wanneer de `PSSubsystemPluginModel` functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b6985-112">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="b6985-113">Zie [experimentele functies gebruiken](/powershell/scripting/learn/experimental-features)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b6985-113">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="b6985-114">De functie maakt het mogelijk om onderdelen van te scheiden `System.Management.Automation.dll` in afzonderlijke subsystemen die zich in hun eigen assembly bevinden.</span><span class="sxs-lookup"><span data-stu-id="b6985-114">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="b6985-115">Deze schei ding vermindert het schijf gebruik van de kern-Power shell-engine en maakt het mogelijk dat deze onderdelen optionele functies worden voor een minimale Power shell-installatie.</span><span class="sxs-lookup"><span data-stu-id="b6985-115">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="b6985-116">Op dit moment wordt alleen het subsysteem **CommandPredictor** ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b6985-116">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="b6985-117">Dit subsysteem wordt samen met de PSReadLine-module gebruikt om aangepaste Voorspellings-invoeg toepassingen te bieden.</span><span class="sxs-lookup"><span data-stu-id="b6985-117">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="b6985-118">In de toekomst kunnen **Job**, **CommandCompleter**, **Remoting** en andere onderdelen worden gescheiden in subsysteem-assembly's buiten `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="b6985-118">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="b6985-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b6985-119">EXAMPLES</span></span>

### <span data-ttu-id="b6985-120">Voor beeld 1: alle beschik bare subsystemen weer geven</span><span class="sxs-lookup"><span data-stu-id="b6985-120">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="b6985-121">Voor beeld 2: alle beschik bare subsystemen van een specifiek type weer geven</span><span class="sxs-lookup"><span data-stu-id="b6985-121">Example 2 - Display all available subsystems of a specific kind</span></span>

```powershell
PS> Get-PSSubsystem -Kind CommandPredictor | Format-List
```

```Output
Kind                      : CommandPredictor
SubsystemType             : System.Management.Automation.Subsystem.ICommandPredictor
AllowUnregistration       : True
AllowMultipleRegistration : True
RequiredCmdlets           : {}
RequiredFunctions         : {}
IsRegistered              : False
Implementations           : {}
```

## <span data-ttu-id="b6985-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b6985-122">PARAMETERS</span></span>

### <span data-ttu-id="b6985-123">-Soort</span><span class="sxs-lookup"><span data-stu-id="b6985-123">-Kind</span></span>


<span data-ttu-id="b6985-124">Hiermee geeft u het soort subsysteem moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b6985-124">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="b6985-125">Geldige waarden zijn: `CommandPredictor` .</span><span class="sxs-lookup"><span data-stu-id="b6985-125">Valid values are: `CommandPredictor`.</span></span>

```yaml
Type: System.Management.Automation.Subsystem.SubsystemKind
Parameter Sets: GetByKindSet
Aliases:
Accepted values: CommandPredictor

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b6985-126">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="b6985-126">-SubsystemType</span></span>

<span data-ttu-id="b6985-127">Hiermee geeft u het type subsysteem moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b6985-127">Specifies the type of subsystem to be returned.</span></span>

```yaml
Type: System.Type
Parameter Sets: GetByTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b6985-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b6985-128">CommonParameters</span></span>

<span data-ttu-id="b6985-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b6985-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b6985-130">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b6985-130">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b6985-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="b6985-131">INPUTS</span></span>

### <span data-ttu-id="b6985-132">System. Management. Automation. subsysteem. SubsystemKind</span><span class="sxs-lookup"><span data-stu-id="b6985-132">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="b6985-133">System. type</span><span class="sxs-lookup"><span data-stu-id="b6985-133">System.Type</span></span>

## <span data-ttu-id="b6985-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b6985-134">OUTPUTS</span></span>

### <span data-ttu-id="b6985-135">System. Management. Automation. subsysteem. SubsystemInfo</span><span class="sxs-lookup"><span data-stu-id="b6985-135">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="b6985-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b6985-136">NOTES</span></span>

## <span data-ttu-id="b6985-137">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b6985-137">RELATED LINKS</span></span>

[<span data-ttu-id="b6985-138">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="b6985-138">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="b6985-139">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="b6985-139">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="b6985-140">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="b6985-140">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="b6985-141">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="b6985-141">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="b6985-142">Experimentele functies gebruiken</span><span class="sxs-lookup"><span data-stu-id="b6985-142">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
