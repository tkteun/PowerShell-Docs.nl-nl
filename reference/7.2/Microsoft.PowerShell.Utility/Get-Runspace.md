---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Runspace
ms.openlocfilehash: 34843894cb6253e3d8e89072cf79cb9237d4fc19
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705934"
---
# <span data-ttu-id="f04f5-102">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="f04f5-102">Get-Runspace</span></span>

## <span data-ttu-id="f04f5-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f04f5-103">SYNOPSIS</span></span>
<span data-ttu-id="f04f5-104">Hiermee wordt een actief runspaces binnen een Power shell-hostproces opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f04f5-104">Gets active runspaces within a PowerShell host process.</span></span>

## <span data-ttu-id="f04f5-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f04f5-105">SYNTAX</span></span>

### <span data-ttu-id="f04f5-106">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="f04f5-106">NameParameterSet (Default)</span></span>

```
Get-Runspace [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f04f5-107">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f04f5-107">IdParameterSet</span></span>

```
Get-Runspace [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="f04f5-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f04f5-108">InstanceIdParameterSet</span></span>

```
Get-Runspace [-InstanceId] <Guid[]> [<CommonParameters>]
```

## <span data-ttu-id="f04f5-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f04f5-109">DESCRIPTION</span></span>

<span data-ttu-id="f04f5-110">De `Get-Runspace` cmdlet krijgt actieve runspaces in een Power shell-hostproces.</span><span class="sxs-lookup"><span data-stu-id="f04f5-110">The `Get-Runspace` cmdlet gets active runspaces in a PowerShell host process.</span></span>

## <span data-ttu-id="f04f5-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f04f5-111">EXAMPLES</span></span>

### <span data-ttu-id="f04f5-112">Voor beeld 1: runspaces ophalen</span><span class="sxs-lookup"><span data-stu-id="f04f5-112">Example 1: Get runspaces</span></span>

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

### <span data-ttu-id="f04f5-113">Voor beeld 2: runs Pace op id ophalen</span><span class="sxs-lookup"><span data-stu-id="f04f5-113">Example 2: Get runspace by Id</span></span>

```powershell
Get-Runspace -Id 2
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  2 Runspace2       localhost       Local         Opened        Available
```

### <span data-ttu-id="f04f5-114">Voor beeld 3: een runs Pace op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="f04f5-114">Example 3: Get runspace by Name</span></span>

```powershell
Get-Runspace -Name Runspace1
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

### <span data-ttu-id="f04f5-115">Voor beeld 4: runs Pace op InstanceId ophalen</span><span class="sxs-lookup"><span data-stu-id="f04f5-115">Example 4: Get runspace by InstanceId</span></span>

<span data-ttu-id="f04f5-116">In dit voor beeld identificeren we een beschik bare runs Pace met behulp van de `Name` para meter en slaan we het retour object op in de variabele `$activeRunspace` .</span><span class="sxs-lookup"><span data-stu-id="f04f5-116">In this example, we identify an available runspace using the `Name` parameter and store the return object to the variable `$activeRunspace`.</span></span> <span data-ttu-id="f04f5-117">Hierdoor kunt u de eigenschappen van de **runs Pace** gebruiken in de volgende uitvoeringen van `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="f04f5-117">This allows you to use the properties of the **Runspace** in subsequent runs of `Get-Runspace`.</span></span>

```powershell
$activeRunspace = Get-Runspace -Name Runspace1
Get-Runspace -InstanceId $activeRunspace.InstanceId
```

```Output
Id Name            ComputerName    Type          State         Availability
 -- ----            ------------    ----          -----         ------------
  1 Runspace1       localhost       Local         Opened        Busy
```

## <span data-ttu-id="f04f5-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f04f5-118">PARAMETERS</span></span>

### <span data-ttu-id="f04f5-119">-Id</span><span class="sxs-lookup"><span data-stu-id="f04f5-119">-Id</span></span>

<span data-ttu-id="f04f5-120">Hiermee wordt de id van een runs Pace opgegeven</span><span class="sxs-lookup"><span data-stu-id="f04f5-120">Specifies the Id of a runspace</span></span>

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

### <span data-ttu-id="f04f5-121">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f04f5-121">-InstanceId</span></span>

<span data-ttu-id="f04f5-122">Hiermee geeft u de exemplaar-ID-GUID van een actieve taak op.</span><span class="sxs-lookup"><span data-stu-id="f04f5-122">Specifies the instance ID GUID of a running job.</span></span>

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

### <span data-ttu-id="f04f5-123">-Name</span><span class="sxs-lookup"><span data-stu-id="f04f5-123">-Name</span></span>

<span data-ttu-id="f04f5-124">Hiermee wordt de naam van een runs Pace opgegeven</span><span class="sxs-lookup"><span data-stu-id="f04f5-124">Specifies the Name of a runspace</span></span>

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

### <span data-ttu-id="f04f5-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f04f5-125">CommonParameters</span></span>

<span data-ttu-id="f04f5-126">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f04f5-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f04f5-127">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f04f5-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f04f5-128">INVOER</span><span class="sxs-lookup"><span data-stu-id="f04f5-128">INPUTS</span></span>

## <span data-ttu-id="f04f5-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f04f5-129">OUTPUTS</span></span>

### <span data-ttu-id="f04f5-130">System. Management. Automation. Runspaces. runs Pace</span><span class="sxs-lookup"><span data-stu-id="f04f5-130">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="f04f5-131">U kunt de resultaten van een opdracht door sluizen `Get-Runspace` naar `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="f04f5-131">You can pipe the results of a `Get-Runspace` command to `Debug-Runspace`.</span></span>

## <span data-ttu-id="f04f5-132">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f04f5-132">NOTES</span></span>

## <span data-ttu-id="f04f5-133">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f04f5-133">RELATED LINKS</span></span>

[<span data-ttu-id="f04f5-134">Fout opsporing-runs Pace</span><span class="sxs-lookup"><span data-stu-id="f04f5-134">Debug-Runspace</span></span>](Debug-Runspace.md)

