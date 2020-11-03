---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250843"
---
# <span data-ttu-id="b1898-103">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="b1898-103">Checkpoint-Computer</span></span>

## <span data-ttu-id="b1898-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b1898-104">SYNOPSIS</span></span>
<span data-ttu-id="b1898-105">Hiermee maakt u een systeem herstel punt op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b1898-105">Creates a system restore point on the local computer.</span></span>

## <span data-ttu-id="b1898-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b1898-106">SYNTAX</span></span>

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## <span data-ttu-id="b1898-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b1898-107">DESCRIPTION</span></span>

<span data-ttu-id="b1898-108">De `Checkpoint-Computer` cmdlet maakt een systeem herstel punt op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b1898-108">The `Checkpoint-Computer` cmdlet creates a system restore point on the local computer.</span></span>

<span data-ttu-id="b1898-109">Systeem herstel punten en de `Checkpoint-Computer` cmdlet worden alleen ondersteund op client besturingssystemen, zoals Windows 8, Windows 7, Windows Vista en Windows XP.</span><span class="sxs-lookup"><span data-stu-id="b1898-109">System restore points and the `Checkpoint-Computer` cmdlet are supported only on client operating systems, such as Windows 8, Windows 7, Windows Vista, and Windows XP.</span></span>

<span data-ttu-id="b1898-110">Vanaf Windows 8 `Checkpoint-Computer` kan niet meer dan één controle punt elke dag maken.</span><span class="sxs-lookup"><span data-stu-id="b1898-110">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one checkpoint each day.</span></span>

## <span data-ttu-id="b1898-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b1898-111">EXAMPLES</span></span>

### <span data-ttu-id="b1898-112">Voor beeld 1: een systeem herstel punt maken</span><span class="sxs-lookup"><span data-stu-id="b1898-112">Example 1: Create a system restore point</span></span>

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

<span data-ttu-id="b1898-113">Met deze opdracht maakt u een systeem herstel punt met de naam Install Mijntoep.</span><span class="sxs-lookup"><span data-stu-id="b1898-113">This command creates a system restore point called Install MyApp.</span></span>
<span data-ttu-id="b1898-114">Het standaard APPLICATION_INSTALL herstel punt type wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b1898-114">It uses the default APPLICATION_INSTALL restore point type.</span></span>

### <span data-ttu-id="b1898-115">Voor beeld 2: een systeem MODIFY_SETTINGS herstel punt maken</span><span class="sxs-lookup"><span data-stu-id="b1898-115">Example 2: Create a system MODIFY_SETTINGS restore point</span></span>

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

<span data-ttu-id="b1898-116">Met deze opdracht maakt u een MODIFY_SETTINGS systeem herstel punt met de naam ' ChangeNetSettings '.</span><span class="sxs-lookup"><span data-stu-id="b1898-116">This command creates a MODIFY_SETTINGS system restore point called "ChangeNetSettings".</span></span>

## <span data-ttu-id="b1898-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b1898-117">PARAMETERS</span></span>

### <span data-ttu-id="b1898-118">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b1898-118">-Description</span></span>

<span data-ttu-id="b1898-119">Hiermee geeft u een beschrijvende naam op voor het herstel punt.</span><span class="sxs-lookup"><span data-stu-id="b1898-119">Specifies a descriptive name for the restore point.</span></span>
<span data-ttu-id="b1898-120">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="b1898-120">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1898-121">-RestorePointType</span><span class="sxs-lookup"><span data-stu-id="b1898-121">-RestorePointType</span></span>

<span data-ttu-id="b1898-122">Hiermee geeft u het type herstel punt op.</span><span class="sxs-lookup"><span data-stu-id="b1898-122">Specifies the type of restore point.</span></span>
<span data-ttu-id="b1898-123">De standaard waarde is APPLICATION_INSTALL.</span><span class="sxs-lookup"><span data-stu-id="b1898-123">The default is APPLICATION_INSTALL.</span></span>

<span data-ttu-id="b1898-124">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="b1898-124">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b1898-125">APPLICATION_INSTALL</span><span class="sxs-lookup"><span data-stu-id="b1898-125">APPLICATION_INSTALL</span></span>
- <span data-ttu-id="b1898-126">APPLICATION_UNINSTALL</span><span class="sxs-lookup"><span data-stu-id="b1898-126">APPLICATION_UNINSTALL</span></span>
- <span data-ttu-id="b1898-127">DEVICE_DRIVER_INSTALL</span><span class="sxs-lookup"><span data-stu-id="b1898-127">DEVICE_DRIVER_INSTALL</span></span>
- <span data-ttu-id="b1898-128">MODIFY_SETTINGS</span><span class="sxs-lookup"><span data-stu-id="b1898-128">MODIFY_SETTINGS</span></span>
- <span data-ttu-id="b1898-129">CANCELLED_OPERATION</span><span class="sxs-lookup"><span data-stu-id="b1898-129">CANCELLED_OPERATION</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1898-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b1898-130">CommonParameters</span></span>

<span data-ttu-id="b1898-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b1898-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b1898-132">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b1898-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b1898-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="b1898-133">INPUTS</span></span>

### <span data-ttu-id="b1898-134">Geen</span><span class="sxs-lookup"><span data-stu-id="b1898-134">None</span></span>

<span data-ttu-id="b1898-135">U kunt geen objecten pipeen naar `Checkpoint-Computer` .</span><span class="sxs-lookup"><span data-stu-id="b1898-135">You cannot pipe objects to `Checkpoint-Computer`.</span></span>

## <span data-ttu-id="b1898-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b1898-136">OUTPUTS</span></span>

### <span data-ttu-id="b1898-137">Geen</span><span class="sxs-lookup"><span data-stu-id="b1898-137">None</span></span>

<span data-ttu-id="b1898-138">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b1898-138">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b1898-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b1898-139">NOTES</span></span>

- <span data-ttu-id="b1898-140">Deze cmdlet gebruikt de methode **CreateRestorePoint** van de klasse **SystemRestore** met een **BEGIN_SYSTEM_CHANGE** gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="b1898-140">This cmdlet uses the **CreateRestorePoint** method of the **SystemRestore** class with a **BEGIN_SYSTEM_CHANGE** event.</span></span>
- <span data-ttu-id="b1898-141">Vanaf Windows 8 `Checkpoint-Computer` kan elke dag niet meer dan één systeem herstel punt maken.</span><span class="sxs-lookup"><span data-stu-id="b1898-141">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one system restore point each day.</span></span> <span data-ttu-id="b1898-142">Als u probeert een nieuw herstel punt te maken voordat de periode van 24 uur is verstreken, genereert Windows Power shell de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="b1898-142">If you try to create a new restore point before the 24-hour period has elapsed, Windows PowerShell generates the following error:</span></span>

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## <span data-ttu-id="b1898-143">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b1898-143">RELATED LINKS</span></span>

[<span data-ttu-id="b1898-144">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="b1898-144">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="b1898-145">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="b1898-145">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="b1898-146">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="b1898-146">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="b1898-147">Herstellen-computer</span><span class="sxs-lookup"><span data-stu-id="b1898-147">Restore-Computer</span></span>](Restore-Computer.md)
