---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: 5b92af5f98239375eec35b82c3ae3756c9853d22
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251125"
---
# <span data-ttu-id="63e3c-103">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="63e3c-103">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="63e3c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="63e3c-104">SYNOPSIS</span></span>
<span data-ttu-id="63e3c-105">Hiermee schakelt u fout opsporing in voor runspaces waarbij een onderbrekings punt wordt bewaard totdat er een fout opsporingsprogramma is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="63e3c-105">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="63e3c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="63e3c-106">SYNTAX</span></span>

### <span data-ttu-id="63e3c-107">RunspaceNameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="63e3c-107">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="63e3c-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="63e3c-108">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="63e3c-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="63e3c-109">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="63e3c-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="63e3c-110">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="63e3c-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="63e3c-111">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="63e3c-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="63e3c-112">DESCRIPTION</span></span>

<span data-ttu-id="63e3c-113">De `Enable-RunspaceDebug` cmdlet schakelt fout opsporing in voor runspaces waarbij een onderbrekings punt wordt bewaard totdat er een fout opsporingsprogramma is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="63e3c-113">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="63e3c-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="63e3c-114">EXAMPLES</span></span>

### <span data-ttu-id="63e3c-115">1: de standaard runs Pace-fout opsporing inschakelen</span><span class="sxs-lookup"><span data-stu-id="63e3c-115">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="63e3c-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="63e3c-116">PARAMETERS</span></span>

### <span data-ttu-id="63e3c-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="63e3c-117">-AppDomainName</span></span>

<span data-ttu-id="63e3c-118">De naam van het toepassings domein dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="63e3c-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63e3c-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="63e3c-119">-BreakAll</span></span>

<span data-ttu-id="63e3c-120">Zorgt ervoor dat een wille keurige opdracht of script in de runs Pace stopt in stap modus, ongeacht of er momenteel een fout opsporingsprogramma is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="63e3c-120">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="63e3c-121">Het script of de opdracht blijft actief totdat er een fout opsporingsprogramma is gekoppeld aan het opsporen van fouten in het huidige stop punt.</span><span class="sxs-lookup"><span data-stu-id="63e3c-121">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RunspaceNameParameterSet, RunspaceParameterSet, RunspaceIdParameterSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63e3c-122">-Procesnaam</span><span class="sxs-lookup"><span data-stu-id="63e3c-122">-ProcessName</span></span>

<span data-ttu-id="63e3c-123">De naam van het proces dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="63e3c-123">The name of the process that hosts the PowerShell runspace.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63e3c-124">-Runs Pace</span><span class="sxs-lookup"><span data-stu-id="63e3c-124">-Runspace</span></span>

<span data-ttu-id="63e3c-125">Een of meer **runs Pace** -objecten die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="63e3c-125">One or more **Runspace** objects to be disabled.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace[]
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="63e3c-126">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="63e3c-126">-RunspaceId</span></span>

<span data-ttu-id="63e3c-127">Een of meer **runs Pace** -id-nummers die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="63e3c-127">One or more **Runspace** Id numbers to be disabled.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: RunspaceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63e3c-128">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="63e3c-128">-RunspaceInstanceId</span></span>

<span data-ttu-id="63e3c-129">Een of meer **runs Pace** -guid's die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="63e3c-129">One or more **Runspace** GUIDs to be disabled.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: RunspaceInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63e3c-130">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="63e3c-130">-RunspaceName</span></span>

<span data-ttu-id="63e3c-131">Een of meer **runs Pace** -namen die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="63e3c-131">One or more **Runspace** names to be disabled.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RunspaceNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63e3c-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63e3c-132">CommonParameters</span></span>

<span data-ttu-id="63e3c-133">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="63e3c-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="63e3c-134">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="63e3c-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="63e3c-135">INVOER</span><span class="sxs-lookup"><span data-stu-id="63e3c-135">INPUTS</span></span>

## <span data-ttu-id="63e3c-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="63e3c-136">OUTPUTS</span></span>

## <span data-ttu-id="63e3c-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="63e3c-137">NOTES</span></span>

## <span data-ttu-id="63e3c-138">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="63e3c-138">RELATED LINKS</span></span>

[<span data-ttu-id="63e3c-139">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="63e3c-139">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="63e3c-140">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="63e3c-140">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)
