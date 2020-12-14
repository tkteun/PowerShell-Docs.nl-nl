---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspacedebug?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-RunspaceDebug
ms.openlocfilehash: a77695fe32345fda8e6a0284cd29becb432a4273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705932"
---
# <span data-ttu-id="9b1da-102">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="9b1da-102">Get-RunspaceDebug</span></span>

## <span data-ttu-id="9b1da-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9b1da-103">SYNOPSIS</span></span>
<span data-ttu-id="9b1da-104">Hiermee worden opties voor fout opsporing in runs weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9b1da-104">Shows runspace debugging options.</span></span>

## <span data-ttu-id="9b1da-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9b1da-105">SYNTAX</span></span>

### <span data-ttu-id="9b1da-106">RunspaceNameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="9b1da-106">RunspaceNameParameterSet (Default)</span></span>

```
Get-RunspaceDebug [[-RunspaceName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="9b1da-107">RunspaceParameterSet</span><span class="sxs-lookup"><span data-stu-id="9b1da-107">RunspaceParameterSet</span></span>

```
Get-RunspaceDebug [-Runspace] <Runspace[]> [<CommonParameters>]
```

### <span data-ttu-id="9b1da-108">RunspaceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="9b1da-108">RunspaceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceId] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="9b1da-109">RunspaceInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="9b1da-109">RunspaceInstanceIdParameterSet</span></span>

```
Get-RunspaceDebug [-RunspaceInstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="9b1da-110">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="9b1da-110">ProcessNameParameterSet</span></span>

```
Get-RunspaceDebug [[-ProcessName] <String>] [[-AppDomainName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="9b1da-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9b1da-111">DESCRIPTION</span></span>

<span data-ttu-id="9b1da-112">Met de `Get-RunspaceDebug` cmdlet worden de opties voor fout opsporing in runs weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9b1da-112">The `Get-RunspaceDebug` cmdlet shows runspace debugging options.</span></span>

## <span data-ttu-id="9b1da-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9b1da-113">EXAMPLES</span></span>

### <span data-ttu-id="9b1da-114">1: de status van de standaard fout opsporing voor runs Pace weer geven</span><span class="sxs-lookup"><span data-stu-id="9b1da-114">1: Show the state of the default runspace debugger</span></span>

```powershell
Get-RunspaceDebug
```

```Output
 Id Name                 Enabled    BreakAll
 -- ----                 -------    --------
  1 Runspace1            False      False
```

## <span data-ttu-id="9b1da-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9b1da-115">PARAMETERS</span></span>

### <span data-ttu-id="9b1da-116">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="9b1da-116">-AppDomainName</span></span>

<span data-ttu-id="9b1da-117">De naam van het toepassings domein dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="9b1da-117">The name of the application domain that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="9b1da-118">-Procesnaam</span><span class="sxs-lookup"><span data-stu-id="9b1da-118">-ProcessName</span></span>

<span data-ttu-id="9b1da-119">De naam van het proces dat als host fungeert voor de Power shell-runs Pace.</span><span class="sxs-lookup"><span data-stu-id="9b1da-119">The name of the process that hosts the PowerShell runspace.</span></span>

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

### <span data-ttu-id="9b1da-120">-Runs Pace</span><span class="sxs-lookup"><span data-stu-id="9b1da-120">-Runspace</span></span>

<span data-ttu-id="9b1da-121">Een of meer **runs Pace** -objecten die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9b1da-121">One or more **Runspace** objects to be disabled.</span></span>

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

### <span data-ttu-id="9b1da-122">-RunspaceId</span><span class="sxs-lookup"><span data-stu-id="9b1da-122">-RunspaceId</span></span>

<span data-ttu-id="9b1da-123">Een of meer **runs Pace** -id-nummers die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9b1da-123">One or more **Runspace** Id numbers to be disabled.</span></span>

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

### <span data-ttu-id="9b1da-124">-RunspaceInstanceId</span><span class="sxs-lookup"><span data-stu-id="9b1da-124">-RunspaceInstanceId</span></span>

<span data-ttu-id="9b1da-125">Een of meer **runs Pace** -guid's die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9b1da-125">One or more **Runspace** GUIDs to be disabled.</span></span>

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

### <span data-ttu-id="9b1da-126">-RunspaceName</span><span class="sxs-lookup"><span data-stu-id="9b1da-126">-RunspaceName</span></span>

<span data-ttu-id="9b1da-127">Een of meer **runs Pace** -namen die moeten worden uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9b1da-127">One or more **Runspace** names to be disabled.</span></span>

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

### <span data-ttu-id="9b1da-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b1da-128">CommonParameters</span></span>

<span data-ttu-id="9b1da-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9b1da-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b1da-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9b1da-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9b1da-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="9b1da-131">INPUTS</span></span>

## <span data-ttu-id="9b1da-132">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9b1da-132">OUTPUTS</span></span>

## <span data-ttu-id="9b1da-133">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9b1da-133">NOTES</span></span>

## <span data-ttu-id="9b1da-134">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9b1da-134">RELATED LINKS</span></span>

[<span data-ttu-id="9b1da-135">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="9b1da-135">Disable-RunspaceDebug</span></span>](Disable-RunspaceDebug.md)

[<span data-ttu-id="9b1da-136">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="9b1da-136">Enable-RunspaceDebug</span></span>](Enable-RunspaceDebug.md)

