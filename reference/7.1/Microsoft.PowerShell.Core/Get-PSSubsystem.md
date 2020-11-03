---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: ''
schema: 2.0.0
ms.openlocfilehash: 34998e7c4a6876821df949019970dc1d87297397
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253061"
---
# <span data-ttu-id="3ce91-101">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="3ce91-101">Get-PSSubsystem</span></span>

## <span data-ttu-id="3ce91-102">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3ce91-102">SYNOPSIS</span></span>
<span data-ttu-id="3ce91-103">Haalt informatie op over de subsystemen die zijn geregistreerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="3ce91-103">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="3ce91-104">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3ce91-104">SYNTAX</span></span>

### <span data-ttu-id="3ce91-105">GetAllSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="3ce91-105">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="3ce91-106">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="3ce91-106">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="3ce91-107">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="3ce91-107">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="3ce91-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3ce91-108">DESCRIPTION</span></span>

<span data-ttu-id="3ce91-109">Haalt informatie op over de subsystemen die zijn geregistreerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="3ce91-109">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="3ce91-110">Dit is een experimentele functie.</span><span class="sxs-lookup"><span data-stu-id="3ce91-110">This is an experimental feature.</span></span> <span data-ttu-id="3ce91-111">Deze cmdlet is alleen beschikbaar wanneer de `PSSubsystemPluginModel` functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3ce91-111">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="3ce91-112">Zie [experimentele functies gebruiken](/powershell/scripting/learn/experimental-features)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3ce91-112">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="3ce91-113">De functie maakt het mogelijk om onderdelen van te scheiden `System.Management.Automation.dll` in afzonderlijke subsystemen die zich in hun eigen assembly bevinden.</span><span class="sxs-lookup"><span data-stu-id="3ce91-113">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="3ce91-114">Deze schei ding vermindert het schijf gebruik van de kern-Power shell-engine en maakt het mogelijk dat deze onderdelen optionele functies worden voor een minimale Power shell-installatie.</span><span class="sxs-lookup"><span data-stu-id="3ce91-114">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="3ce91-115">Op dit moment wordt alleen het subsysteem **CommandPredictor** ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3ce91-115">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="3ce91-116">Dit subsysteem wordt samen met de PSReadLine-module gebruikt om aangepaste Voorspellings-invoeg toepassingen te bieden.</span><span class="sxs-lookup"><span data-stu-id="3ce91-116">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="3ce91-117">In de toekomst kunnen **Job** , **CommandCompleter** , **Remoting** en andere onderdelen worden gescheiden in subsysteem-assembly's buiten `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="3ce91-117">In future, **Job** , **CommandCompleter** , **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="3ce91-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3ce91-118">EXAMPLES</span></span>

### <span data-ttu-id="3ce91-119">Voor beeld 1: alle beschik bare subsystemen weer geven</span><span class="sxs-lookup"><span data-stu-id="3ce91-119">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="3ce91-120">Voor beeld 2: alle beschik bare subsystemen van een specifiek type weer geven</span><span class="sxs-lookup"><span data-stu-id="3ce91-120">Example 2 - Display all available subsystems of a specific kind</span></span>

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

## <span data-ttu-id="3ce91-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3ce91-121">PARAMETERS</span></span>

### <span data-ttu-id="3ce91-122">-Soort</span><span class="sxs-lookup"><span data-stu-id="3ce91-122">-Kind</span></span>


<span data-ttu-id="3ce91-123">Hiermee geeft u het soort subsysteem moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3ce91-123">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="3ce91-124">Geldige waarden zijn: `CommandPredictor` .</span><span class="sxs-lookup"><span data-stu-id="3ce91-124">Valid values are: `CommandPredictor`.</span></span>

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

### <span data-ttu-id="3ce91-125">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="3ce91-125">-SubsystemType</span></span>

<span data-ttu-id="3ce91-126">Hiermee geeft u het type subsysteem moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3ce91-126">Specifies the type of subsystem to be returned.</span></span>

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

### <span data-ttu-id="3ce91-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3ce91-127">CommonParameters</span></span>

<span data-ttu-id="3ce91-128">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3ce91-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3ce91-129">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3ce91-129">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3ce91-130">INVOER</span><span class="sxs-lookup"><span data-stu-id="3ce91-130">INPUTS</span></span>

### <span data-ttu-id="3ce91-131">System. Management. Automation. subsysteem. SubsystemKind</span><span class="sxs-lookup"><span data-stu-id="3ce91-131">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="3ce91-132">System. type</span><span class="sxs-lookup"><span data-stu-id="3ce91-132">System.Type</span></span>

## <span data-ttu-id="3ce91-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3ce91-133">OUTPUTS</span></span>

### <span data-ttu-id="3ce91-134">System. Management. Automation. subsysteem. SubsystemInfo</span><span class="sxs-lookup"><span data-stu-id="3ce91-134">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="3ce91-135">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3ce91-135">NOTES</span></span>

## <span data-ttu-id="3ce91-136">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3ce91-136">RELATED LINKS</span></span>

[<span data-ttu-id="3ce91-137">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="3ce91-137">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="3ce91-138">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="3ce91-138">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="3ce91-139">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="3ce91-139">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="3ce91-140">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="3ce91-140">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="3ce91-141">Experimentele functies gebruiken</span><span class="sxs-lookup"><span data-stu-id="3ce91-141">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
