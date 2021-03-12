---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssubsystem?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSubsystem
ms.openlocfilehash: 1e08715562ab5a5b52193dacdd2c48cacb4540e8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195517"
---
# <span data-ttu-id="3945c-102">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="3945c-102">Get-PSSubsystem</span></span>

## <span data-ttu-id="3945c-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3945c-103">SYNOPSIS</span></span>
<span data-ttu-id="3945c-104">Haalt informatie op over de subsystemen die zijn geregistreerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="3945c-104">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="3945c-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3945c-105">SYNTAX</span></span>

### <span data-ttu-id="3945c-106">GetAllSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="3945c-106">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="3945c-107">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="3945c-107">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="3945c-108">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="3945c-108">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="3945c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3945c-109">DESCRIPTION</span></span>

<span data-ttu-id="3945c-110">Haalt informatie op over de subsystemen die zijn geregistreerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="3945c-110">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="3945c-111">Dit is een experimentele functie.</span><span class="sxs-lookup"><span data-stu-id="3945c-111">This is an experimental feature.</span></span> <span data-ttu-id="3945c-112">Deze cmdlet is alleen beschikbaar wanneer de `PSSubsystemPluginModel` functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3945c-112">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="3945c-113">Zie [experimentele functies gebruiken](/powershell/scripting/learn/experimental-features)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3945c-113">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="3945c-114">De functie maakt het mogelijk om onderdelen van te scheiden `System.Management.Automation.dll` in afzonderlijke subsystemen die zich in hun eigen assembly bevinden.</span><span class="sxs-lookup"><span data-stu-id="3945c-114">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="3945c-115">Deze schei ding vermindert het schijf gebruik van de kern-Power shell-engine en maakt het mogelijk dat deze onderdelen optionele functies worden voor een minimale Power shell-installatie.</span><span class="sxs-lookup"><span data-stu-id="3945c-115">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="3945c-116">Op dit moment wordt alleen het subsysteem **CommandPredictor** ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3945c-116">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="3945c-117">Dit subsysteem wordt samen met de PSReadLine-module gebruikt om aangepaste Voorspellings-invoeg toepassingen te bieden.</span><span class="sxs-lookup"><span data-stu-id="3945c-117">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="3945c-118">In de toekomst kunnen **Job**, **CommandCompleter**, **Remoting** en andere onderdelen worden gescheiden in subsysteem-assembly's buiten `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="3945c-118">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="3945c-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3945c-119">EXAMPLES</span></span>

### <span data-ttu-id="3945c-120">Voor beeld 1: alle beschik bare subsystemen weer geven</span><span class="sxs-lookup"><span data-stu-id="3945c-120">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="3945c-121">Voor beeld 2: alle beschik bare subsystemen van een specifiek type weer geven</span><span class="sxs-lookup"><span data-stu-id="3945c-121">Example 2 - Display all available subsystems of a specific kind</span></span>

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

## <span data-ttu-id="3945c-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3945c-122">PARAMETERS</span></span>

### <span data-ttu-id="3945c-123">-Soort</span><span class="sxs-lookup"><span data-stu-id="3945c-123">-Kind</span></span>


<span data-ttu-id="3945c-124">Hiermee geeft u het soort subsysteem moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3945c-124">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="3945c-125">Geldige waarden zijn: `CommandPredictor` .</span><span class="sxs-lookup"><span data-stu-id="3945c-125">Valid values are: `CommandPredictor`.</span></span>

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

### <span data-ttu-id="3945c-126">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="3945c-126">-SubsystemType</span></span>

<span data-ttu-id="3945c-127">Hiermee geeft u het type subsysteem moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3945c-127">Specifies the type of subsystem to be returned.</span></span>

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

### <span data-ttu-id="3945c-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3945c-128">CommonParameters</span></span>

<span data-ttu-id="3945c-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3945c-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3945c-130">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3945c-130">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3945c-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="3945c-131">INPUTS</span></span>

### <span data-ttu-id="3945c-132">System. Management. Automation. subsysteem. SubsystemKind</span><span class="sxs-lookup"><span data-stu-id="3945c-132">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="3945c-133">System. type</span><span class="sxs-lookup"><span data-stu-id="3945c-133">System.Type</span></span>

## <span data-ttu-id="3945c-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3945c-134">OUTPUTS</span></span>

### <span data-ttu-id="3945c-135">System. Management. Automation. subsysteem. SubsystemInfo</span><span class="sxs-lookup"><span data-stu-id="3945c-135">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="3945c-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3945c-136">NOTES</span></span>

## <span data-ttu-id="3945c-137">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3945c-137">RELATED LINKS</span></span>

[<span data-ttu-id="3945c-138">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="3945c-138">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="3945c-139">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="3945c-139">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="3945c-140">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="3945c-140">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="3945c-141">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="3945c-141">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="3945c-142">Experimentele functies gebruiken</span><span class="sxs-lookup"><span data-stu-id="3945c-142">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
