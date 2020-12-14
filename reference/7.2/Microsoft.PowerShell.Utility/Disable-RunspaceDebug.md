---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 589c8cb36a91de510ffc30973fe70729700ad020
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705834"
---
# <span data-ttu-id="5addc-102">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5addc-102">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="5addc-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5addc-103">SYNOPSIS</span></span>
<span data-ttu-id="5addc-104">Hiermee schakelt u fout opsporing op een of meer runspaces uit en worden alle in behandeling zijnde debugging stoppen vrijgegeven.</span><span class="sxs-lookup"><span data-stu-id="5addc-104">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="5addc-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5addc-105">SYNTAX</span></span>

### <span data-ttu-id="5addc-106">RunspaceNameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="5addc-106">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="5addc-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="5addc-107">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="5addc-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="5addc-108">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="5addc-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="5addc-109">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="5addc-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="5addc-110">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5addc-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5addc-111">DESCRIPTION</span></span>

<span data-ttu-id="5addc-112">Met de `Disable-RunspaceDebug` cmdlet wordt fout opsporing op een of meer runspaces uitgeschakeld en worden alle in behandeling zijnde debugging gestopt.</span><span class="sxs-lookup"><span data-stu-id="5addc-112">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="5addc-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5addc-113">EXAMPLES</span></span>

### <span data-ttu-id="5addc-114">1: de standaard runs Pace-fout opsporing uitschakelen</span><span class="sxs-lookup"><span data-stu-id="5addc-114">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="5addc-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5addc-115">PARAMETERS</span></span>

### <span data-ttu-id="5addc-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="5addc-116">-AppDomainName</span></span>

<span data-ttu-id="5addc-117">De naam van het toepassings domein dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="5addc-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="5addc-118">-Procesnaam</span><span class="sxs-lookup"><span data-stu-id="5addc-118">-ProcessName</span></span>

<span data-ttu-id="5addc-119">De naam van het proces dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="5addc-119">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="5addc-120">-Runs Pace</span><span class="sxs-lookup"><span data-stu-id="5addc-120">-Runspace</span></span>

<span data-ttu-id="5addc-121">Een of meer **runs Pace** -objecten die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="5addc-121">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="5addc-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="5addc-122">-RunspaceId</span></span>

<span data-ttu-id="5addc-123">Een of meer **runs Pace** -id-nummers die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="5addc-123">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="5addc-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="5addc-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="5addc-125">Een of meer **runs Pace** -guid's die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="5addc-125">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="5addc-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="5addc-126">-RunspaceName</span></span>

<span data-ttu-id="5addc-127">Een of meer **runs Pace** -namen die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="5addc-127">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="5addc-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5addc-128">CommonParameters</span></span>

<span data-ttu-id="5addc-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5addc-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5addc-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5addc-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5addc-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="5addc-131">INPUTS</span></span>

## <span data-ttu-id="5addc-132">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5addc-132">OUTPUTS</span></span>

## <span data-ttu-id="5addc-133">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5addc-133">NOTES</span></span>

## <span data-ttu-id="5addc-134">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5addc-134">RELATED LINKS</span></span>

[<span data-ttu-id="5addc-135">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5addc-135">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="5addc-136">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5addc-136">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)

