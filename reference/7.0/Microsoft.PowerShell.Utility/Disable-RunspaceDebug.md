---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-runspacedebug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-RunspaceDebug
ms.openlocfilehash: 58665cd06e39784721be9a538b70dd8b7c2a1c14
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249595"
---
# <span data-ttu-id="b421b-103">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="b421b-103">Disable-RunspaceDebug</span></span>

## <span data-ttu-id="b421b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b421b-104">SYNOPSIS</span></span>
<span data-ttu-id="b421b-105">Hiermee schakelt u fout opsporing op een of meer runspaces uit en worden alle in behandeling zijnde debugging stoppen vrijgegeven.</span><span class="sxs-lookup"><span data-stu-id="b421b-105">Disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="b421b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b421b-106">SYNTAX</span></span>

### <span data-ttu-id="b421b-107">RunspaceNameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="b421b-107">RunspaceNameParameterSet (Default)</span></span>

```
Disable-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="b421b-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="b421b-108">RunspaceParameterSet</span></span>

```
Disable-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="b421b-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="b421b-109">RunspaceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="b421b-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="b421b-110">RunspaceInstanceIdParameterSet</span></span>

```
Disable-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="b421b-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="b421b-111">ProcessNameParameterSet</span></span>

```
Disable-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="b421b-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b421b-112">DESCRIPTION</span></span>

<span data-ttu-id="b421b-113">Met de `Disable-RunspaceDebug` cmdlet wordt fout opsporing op een of meer runspaces uitgeschakeld en worden alle in behandeling zijnde debugging gestopt.</span><span class="sxs-lookup"><span data-stu-id="b421b-113">The `Disable-RunspaceDebug` cmdlet disables debugging on one or more runspaces, and releases any pending debugger stop.</span></span>

## <span data-ttu-id="b421b-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b421b-114">EXAMPLES</span></span>

### <span data-ttu-id="b421b-115">1: de standaard runs Pace-fout opsporing uitschakelen</span><span class="sxs-lookup"><span data-stu-id="b421b-115">1: Disable the default runspace debugger</span></span>

```powershell
Disable-RunspaceDebug
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="b421b-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b421b-116">PARAMETERS</span></span>

### <span data-ttu-id="b421b-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="b421b-117">-AppDomainName</span></span>

<span data-ttu-id="b421b-118">De naam van het toepassings domein dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="b421b-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="b421b-119">-Procesnaam</span><span class="sxs-lookup"><span data-stu-id="b421b-119">-ProcessName</span></span>

<span data-ttu-id="b421b-120">De naam van het proces dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="b421b-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="b421b-121">-Runs Pace</span><span class="sxs-lookup"><span data-stu-id="b421b-121">-Runspace</span></span>

<span data-ttu-id="b421b-122">Een of meer **runs Pace** -objecten die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b421b-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="b421b-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="b421b-123">-RunspaceId</span></span>

<span data-ttu-id="b421b-124">Een of meer **runs Pace** -id-nummers die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b421b-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="b421b-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="b421b-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="b421b-126">Een of meer **runs Pace** -guid's die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b421b-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="b421b-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="b421b-127">-RunspaceName</span></span>

<span data-ttu-id="b421b-128">Een of meer **runs Pace** -namen die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b421b-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="b421b-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b421b-129">CommonParameters</span></span>

<span data-ttu-id="b421b-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b421b-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b421b-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b421b-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b421b-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="b421b-132">INPUTS</span></span>

## <span data-ttu-id="b421b-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b421b-133">OUTPUTS</span></span>

## <span data-ttu-id="b421b-134">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b421b-134">NOTES</span></span>

## <span data-ttu-id="b421b-135">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b421b-135">RELATED LINKS</span></span>

[<span data-ttu-id="b421b-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="b421b-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

[<span data-ttu-id="b421b-137">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="b421b-137">Get-RunspaceDebug</span></span>](Get-RunspaceDebug.md)
