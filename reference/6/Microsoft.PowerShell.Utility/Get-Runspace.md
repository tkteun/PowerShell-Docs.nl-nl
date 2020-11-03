---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 12530b9cf30b34598dfc3a049f5553920abecc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251098"
---
# <span data-ttu-id="853c8-103">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="853c8-103">Get-Runspace</span></span>

## <span data-ttu-id="853c8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="853c8-104">SYNOPSIS</span></span>
<span data-ttu-id="853c8-105">Hiermee wordt een actief runspaces binnen een Power shell-hostproces opgehaald.</span><span class="sxs-lookup"><span data-stu-id="853c8-105">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="853c8-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="853c8-106">SYNTAX</span></span>

### <span data-ttu-id="853c8-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="853c8-107">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="853c8-108">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="853c8-108">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="853c8-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="853c8-109">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="853c8-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="853c8-110">DESCRIPTION</span></span>

<span data-ttu-id="853c8-111">De `Get-Runspace` cmdlet krijgt actieve runspaces in een Power shell-hostproces.</span><span class="sxs-lookup"><span data-stu-id="853c8-111">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="853c8-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="853c8-112">EXAMPLES</span></span>

### <span data-ttu-id="853c8-113">Voor beeld 1: runspaces ophalen</span><span class="sxs-lookup"><span data-stu-id="853c8-113">Example 1: Get runspaces</span></span>

```powershell
Get-Runspace
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
  2 Runspace2       localhost       Local         Opened        Available
  3 Runspace3       localhost       Local         Opened        Available
```

### <span data-ttu-id="853c8-114">Voor beeld 2: runs Pace op id ophalen</span><span class="sxs-lookup"><span data-stu-id="853c8-114">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="853c8-115">Voor beeld 3: een runs Pace op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="853c8-115">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="853c8-116">Voor beeld 4: runs Pace op InstanceId ophalen</span><span class="sxs-lookup"><span data-stu-id="853c8-116">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="853c8-117">In dit voor beeld identificeren we een beschik bare runs Pace met behulp van de `Name` para meter en slaan we het retour object op in de variabele `$activeRunspace` .</span><span class="sxs-lookup"><span data-stu-id="853c8-117">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="853c8-118">Hierdoor kunt u de eigenschappen van de **runs Pace** gebruiken in de volgende uitvoeringen van `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="853c8-118">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="853c8-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="853c8-119">PARAMETERS</span></span>

### <span data-ttu-id="853c8-120">-Id</span><span class="sxs-lookup"><span data-stu-id="853c8-120">-Id</span></span>

<span data-ttu-id="853c8-121">Hiermee wordt de id van een runs Pace opgegeven</span><span class="sxs-lookup"><span data-stu-id="853c8-121">Specifies the Id of a runspace</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="853c8-122">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="853c8-122">-InstanceId</span></span>

<span data-ttu-id="853c8-123">Hiermee geeft u de exemplaar-ID-GUID van een actieve taak op.</span><span class="sxs-lookup"><span data-stu-id="853c8-123">Specifies the instance ID GUID of a running job.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="853c8-124">-Name</span><span class="sxs-lookup"><span data-stu-id="853c8-124">-Name</span></span>

<span data-ttu-id="853c8-125">Hiermee wordt de naam van een runs Pace opgegeven</span><span class="sxs-lookup"><span data-stu-id="853c8-125">Specifies the Name of a runspace</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="853c8-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="853c8-126">CommonParameters</span></span>

<span data-ttu-id="853c8-127">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="853c8-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="853c8-128">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="853c8-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="853c8-129">INVOER</span><span class="sxs-lookup"><span data-stu-id="853c8-129">INPUTS</span></span>

## <span data-ttu-id="853c8-130">UITVOER</span><span class="sxs-lookup"><span data-stu-id="853c8-130">OUTPUTS</span></span>

### <span data-ttu-id="853c8-131">System. Management. Automation. Runspaces. runs Pace</span><span class="sxs-lookup"><span data-stu-id="853c8-131">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="853c8-132">U kunt de resultaten van een opdracht door sluizen `Get-Runspace` naar `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="853c8-132">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="853c8-133">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="853c8-133">NOTES</span></span>

## <span data-ttu-id="853c8-134">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="853c8-134">RELATED LINKS</span></span>

[<span data-ttu-id="853c8-135">Fout opsporing-runs Pace</span><span class="sxs-lookup"><span data-stu-id="853c8-135">Debug-Runspace</span></span>](Debug-Runspace.md)
