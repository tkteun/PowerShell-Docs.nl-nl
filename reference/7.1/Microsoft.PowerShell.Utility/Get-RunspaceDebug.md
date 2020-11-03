---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: 821b532dc44702af4243bf36ca7f5d4089a057d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250206"
---
# <span data-ttu-id="77ff1-103">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="77ff1-103">Get-RunspaceDebug</span></span>

## <span data-ttu-id="77ff1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="77ff1-104">SYNOPSIS</span></span>
<span data-ttu-id="77ff1-105">Hiermee worden opties voor fout opsporing in runs weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="77ff1-105">Shows runspace debugging options.</span></span>

## <span data-ttu-id="77ff1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="77ff1-106">SYNTAX</span></span>

### <span data-ttu-id="77ff1-107">RunspaceNameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="77ff1-107">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="77ff1-108">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="77ff1-108">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="77ff1-109">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="77ff1-109">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="77ff1-110">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="77ff1-110">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="77ff1-111">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="77ff1-111">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="77ff1-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="77ff1-112">DESCRIPTION</span></span>

<span data-ttu-id="77ff1-113">Met de `Get-RunspaceDebug` cmdlet worden de opties voor fout opsporing in runs weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="77ff1-113">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="77ff1-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="77ff1-114">EXAMPLES</span></span>

### <span data-ttu-id="77ff1-115">1: de status van de standaard fout opsporing voor runs Pace weer geven</span><span class="sxs-lookup"><span data-stu-id="77ff1-115">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="77ff1-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="77ff1-116">PARAMETERS</span></span>

### <span data-ttu-id="77ff1-117">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="77ff1-117">-AppDomainName</span></span>

<span data-ttu-id="77ff1-118">De naam van het toepassings domein dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="77ff1-118">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="77ff1-119">-Procesnaam</span><span class="sxs-lookup"><span data-stu-id="77ff1-119">-ProcessName</span></span>

<span data-ttu-id="77ff1-120">De naam van het proces dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="77ff1-120">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="77ff1-121">-Runs Pace</span><span class="sxs-lookup"><span data-stu-id="77ff1-121">-Runspace</span></span>

<span data-ttu-id="77ff1-122">Een of meer **runs Pace** -objecten die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="77ff1-122">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="77ff1-123">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="77ff1-123">-RunspaceId</span></span>

<span data-ttu-id="77ff1-124">Een of meer **runs Pace** -id-nummers die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="77ff1-124">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="77ff1-125">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="77ff1-125">-RunspaceInstanceId</span></span>

<span data-ttu-id="77ff1-126">Een of meer **runs Pace** -guid's die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="77ff1-126">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="77ff1-127">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="77ff1-127">-RunspaceName</span></span>

<span data-ttu-id="77ff1-128">Een of meer **runs Pace** -namen die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="77ff1-128">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="77ff1-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="77ff1-129">CommonParameters</span></span>

<span data-ttu-id="77ff1-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="77ff1-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="77ff1-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="77ff1-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="77ff1-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="77ff1-132">INPUTS</span></span>

## <span data-ttu-id="77ff1-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="77ff1-133">OUTPUTS</span></span>

## <span data-ttu-id="77ff1-134">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="77ff1-134">NOTES</span></span>

## <span data-ttu-id="77ff1-135">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="77ff1-135">RELATED LINKS</span></span>

[<span data-ttu-id="77ff1-136">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="77ff1-136">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="77ff1-137">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="77ff1-137">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

