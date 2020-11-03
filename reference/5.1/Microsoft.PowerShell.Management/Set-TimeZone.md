---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: bfeb838ca8f67bac7c257ef3485eff9b55753933
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250548"
---
# <span data-ttu-id="422bd-103">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="422bd-103">Set-TimeZone</span></span>

## <span data-ttu-id="422bd-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="422bd-104">SYNOPSIS</span></span>
<span data-ttu-id="422bd-105">Hiermee stelt u de systeem tijd zone in op een opgegeven tijd zone.</span><span class="sxs-lookup"><span data-stu-id="422bd-105">Sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="422bd-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="422bd-106">SYNTAX</span></span>

### <span data-ttu-id="422bd-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="422bd-107">Name (Default)</span></span>

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="422bd-108">Id</span><span class="sxs-lookup"><span data-stu-id="422bd-108">Id</span></span>

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="422bd-109">Input object</span><span class="sxs-lookup"><span data-stu-id="422bd-109">InputObject</span></span>

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="422bd-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="422bd-110">DESCRIPTION</span></span>

<span data-ttu-id="422bd-111">`Set-TimeZone`Met de cmdlet wordt de systeem tijd zone ingesteld op een opgegeven tijd zone.</span><span class="sxs-lookup"><span data-stu-id="422bd-111">The `Set-TimeZone` cmdlet sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="422bd-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="422bd-112">EXAMPLES</span></span>

### <span data-ttu-id="422bd-113">Voor beeld 1: de tijd zone instellen op id</span><span class="sxs-lookup"><span data-stu-id="422bd-113">Example 1: Set the time zone by Id</span></span>

<span data-ttu-id="422bd-114">In dit voor beeld wordt de tijd zone op de lokale computer ingesteld op Russische standaard tijd.</span><span class="sxs-lookup"><span data-stu-id="422bd-114">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Id "Russian Standard Time" -PassThru
```

```Output
Id                         : Russian Standard Time
DisplayName                : (UTC+03:00) Moscow, St. Petersburg
StandardName               : Russia TZ 2 Standard Time
DaylightName               : Russia TZ 2 Daylight Time
BaseUtcOffset              : 03:00:00
SupportsDaylightSavingTime : True
```

### <span data-ttu-id="422bd-115">Voor beeld 2: de tijd zone instellen op naam</span><span class="sxs-lookup"><span data-stu-id="422bd-115">Example 2: Set the time zone by name</span></span>

<span data-ttu-id="422bd-116">In dit voor beeld wordt de tijd zone op de lokale computer ingesteld op Russische standaard tijd.</span><span class="sxs-lookup"><span data-stu-id="422bd-116">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

<span data-ttu-id="422bd-117">Zoals we in het vorige voor beeld hebben gezien, komen de **id** en de **naam** van de tijd zone niet altijd overeen.</span><span class="sxs-lookup"><span data-stu-id="422bd-117">As we saw in the previous example, the **Id** and the **Name** of the Time Zone do not always match.</span></span>
<span data-ttu-id="422bd-118">De para meter **name** moet overeenkomen met de **standaard** eigenschappen of de eigenschap **zomernaam** van het object **time zone info** .</span><span class="sxs-lookup"><span data-stu-id="422bd-118">The **Name** parameter must match the **StandardName** or **DaylightName** properties of the **TimeZoneInfo** object.</span></span>

## <span data-ttu-id="422bd-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="422bd-119">PARAMETERS</span></span>

### <span data-ttu-id="422bd-120">-Id</span><span class="sxs-lookup"><span data-stu-id="422bd-120">-Id</span></span>

<span data-ttu-id="422bd-121">Hiermee geeft u de ID op van de tijd zone die met deze cmdlet wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="422bd-121">Specifies the ID of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="422bd-122">U kunt een volledige lijst met tijd zone-Id's verkrijgen door de volgende opdracht uit te voeren: `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="422bd-122">A full list of Time Zone IDs can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="422bd-123">-Input object</span><span class="sxs-lookup"><span data-stu-id="422bd-123">-InputObject</span></span>

<span data-ttu-id="422bd-124">Hiermee geeft u een **time zone info** -object moet worden gebruikt als invoer.</span><span class="sxs-lookup"><span data-stu-id="422bd-124">Specifies a **TimeZoneInfo** object to use as input.</span></span>

```yaml
Type: System.TimeZoneInfo
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="422bd-125">-Name</span><span class="sxs-lookup"><span data-stu-id="422bd-125">-Name</span></span>

<span data-ttu-id="422bd-126">Hiermee geeft u de naam van de tijd zone op die met deze cmdlet wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="422bd-126">Specifies the name of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="422bd-127">U kunt een volledige lijst met tijd zone namen verkrijgen door de volgende opdracht uit te voeren: `Get-TimeZone -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="422bd-127">A full list of Time Zone names can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422bd-128">-PassThru</span><span class="sxs-lookup"><span data-stu-id="422bd-128">-PassThru</span></span>

<span data-ttu-id="422bd-129">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="422bd-129">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="422bd-130">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="422bd-130">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422bd-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="422bd-131">-Confirm</span></span>

<span data-ttu-id="422bd-132">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="422bd-132">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422bd-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="422bd-133">-WhatIf</span></span>

<span data-ttu-id="422bd-134">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="422bd-134">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="422bd-135">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="422bd-135">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422bd-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="422bd-136">CommonParameters</span></span>

<span data-ttu-id="422bd-137">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="422bd-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="422bd-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="422bd-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="422bd-139">INVOER</span><span class="sxs-lookup"><span data-stu-id="422bd-139">INPUTS</span></span>

### <span data-ttu-id="422bd-140">System. String, System. time zone info, System. String</span><span class="sxs-lookup"><span data-stu-id="422bd-140">System.String, System.TimeZoneInfo, System.String</span></span>

## <span data-ttu-id="422bd-141">UITVOER</span><span class="sxs-lookup"><span data-stu-id="422bd-141">OUTPUTS</span></span>

## <span data-ttu-id="422bd-142">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="422bd-142">NOTES</span></span>

## <span data-ttu-id="422bd-143">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="422bd-143">RELATED LINKS</span></span>

[<span data-ttu-id="422bd-144">Get-time zone</span><span class="sxs-lookup"><span data-stu-id="422bd-144">Get-TimeZone</span></span>](Get-TimeZone.md)
