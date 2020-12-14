---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-RunspaceDebug
ms.openlocfilehash: 26ab9b9135eedafa0238eab5c07aa7abb7880ed4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705830"
---
# <span data-ttu-id="25d6b-102">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="25d6b-102">Enable-RunspaceDebug</span></span>

## <span data-ttu-id="25d6b-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="25d6b-103">SYNOPSIS</span></span>
<span data-ttu-id="25d6b-104">Hiermee schakelt u fout opsporing in voor runspaces waarbij een onderbrekings punt wordt bewaard totdat er een fout opsporingsprogramma is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="25d6b-104">Enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="25d6b-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="25d6b-105">SYNTAX</span></span>

### <span data-ttu-id="25d6b-106">RunspaceNameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="25d6b-106">RunspaceNameParameterSet (Default)</span></span>

```
Enable-RunspaceDebug [-BreakAll] [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="25d6b-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="25d6b-107">RunspaceParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="25d6b-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="25d6b-108">RunspaceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-BreakAll] [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="25d6b-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="25d6b-109">RunspaceInstanceIdParameterSet</span></span>

```
Enable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="25d6b-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="25d6b-110">ProcessNameParameterSet</span></span>

```
Enable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="25d6b-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="25d6b-111">DESCRIPTION</span></span>

<span data-ttu-id="25d6b-112">De `Enable-RunspaceDebug` cmdlet schakelt fout opsporing in voor runspaces waarbij een onderbrekings punt wordt bewaard totdat er een fout opsporingsprogramma is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="25d6b-112">The `Enable-RunspaceDebug` cmdlet enables debugging on runspaces where any breakpoint is preserved until a debugger is attached.</span></span>

## <span data-ttu-id="25d6b-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="25d6b-113">EXAMPLES</span></span>

### <span data-ttu-id="25d6b-114">1: de standaard runs Pace-fout opsporing inschakelen</span><span class="sxs-lookup"><span data-stu-id="25d6b-114">1: Enable the default runspace debugger</span></span>

```powershell
Enable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            True       False
```

## <span data-ttu-id="25d6b-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="25d6b-115">PARAMETERS</span></span>

### <span data-ttu-id="25d6b-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="25d6b-116">-AppDomainName</span></span>

<span data-ttu-id="25d6b-117">De naam van het toepassings domein dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="25d6b-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="25d6b-118">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="25d6b-118">-BreakAll</span></span>

<span data-ttu-id="25d6b-119">Zorgt ervoor dat een wille keurige opdracht of script in de runs Pace stopt in stap modus, ongeacht of er momenteel een fout opsporingsprogramma is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="25d6b-119">Causes any running command or script in the Runspace to stop in step mode, regardless of whether a debugger is currently attached.</span></span> <span data-ttu-id="25d6b-120">Het script of de opdracht blijft actief totdat er een fout opsporingsprogramma is gekoppeld aan het opsporen van fouten in het huidige stop punt.</span><span class="sxs-lookup"><span data-stu-id="25d6b-120">The script or command will remain stopped until a debugger is attached to debug the current stop point.</span></span>

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

### <span data-ttu-id="25d6b-121">-Procesnaam</span><span class="sxs-lookup"><span data-stu-id="25d6b-121">-ProcessName</span></span>

<span data-ttu-id="25d6b-122">De naam van het proces dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="25d6b-122">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="25d6b-123">-Runs Pace</span><span class="sxs-lookup"><span data-stu-id="25d6b-123">-Runspace</span></span>

<span data-ttu-id="25d6b-124">Een of meer **runs Pace** -objecten die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="25d6b-124">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="25d6b-125">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="25d6b-125">-RunspaceId</span></span>

<span data-ttu-id="25d6b-126">Een of meer **runs Pace** -id-nummers die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="25d6b-126">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="25d6b-127">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="25d6b-127">-RunspaceInstanceId</span></span>

<span data-ttu-id="25d6b-128">Een of meer **runs Pace** -guid's die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="25d6b-128">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="25d6b-129">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="25d6b-129">-RunspaceName</span></span>

<span data-ttu-id="25d6b-130">Een of meer **runs Pace** -namen die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="25d6b-130">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="25d6b-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="25d6b-131">CommonParameters</span></span>

<span data-ttu-id="25d6b-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="25d6b-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="25d6b-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="25d6b-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="25d6b-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="25d6b-134">INPUTS</span></span>

## <span data-ttu-id="25d6b-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="25d6b-135">OUTPUTS</span></span>

## <span data-ttu-id="25d6b-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="25d6b-136">NOTES</span></span>

## <span data-ttu-id="25d6b-137">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="25d6b-137">RELATED LINKS</span></span>

[<span data-ttu-id="25d6b-138">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="25d6b-138">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="25d6b-139">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="25d6b-139">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

