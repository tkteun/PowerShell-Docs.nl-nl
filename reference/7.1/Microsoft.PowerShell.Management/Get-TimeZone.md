---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 6e0ed432713cabc4db23f3b070a3e925639a60fb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249865"
---
# <span data-ttu-id="429f6-103">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="429f6-103">Get-TimeZone</span></span>

## <span data-ttu-id="429f6-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="429f6-104">SYNOPSIS</span></span>
<span data-ttu-id="429f6-105">Hiermee wordt de huidige tijd zone of een lijst met beschik bare tijd zones opgehaald.</span><span class="sxs-lookup"><span data-stu-id="429f6-105">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="429f6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="429f6-106">SYNTAX</span></span>

### <span data-ttu-id="429f6-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="429f6-107">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="429f6-108">Id</span><span class="sxs-lookup"><span data-stu-id="429f6-108">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="429f6-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="429f6-109">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="429f6-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="429f6-110">DESCRIPTION</span></span>

<span data-ttu-id="429f6-111">Met de cmdlet **Get-time** zone wordt de huidige tijdzone of een lijst met beschik bare tijd zones opgehaald.</span><span class="sxs-lookup"><span data-stu-id="429f6-111">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="429f6-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="429f6-112">EXAMPLES</span></span>

### <span data-ttu-id="429f6-113">Voor beeld 1: de huidige tijd zone ophalen</span><span class="sxs-lookup"><span data-stu-id="429f6-113">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="429f6-114">Met deze opdracht wordt de huidige tijd zone opgehaald.</span><span class="sxs-lookup"><span data-stu-id="429f6-114">This command gets the current time zone.</span></span>

### <span data-ttu-id="429f6-115">Voor beeld 2: tijd zones ophalen die overeenkomen met een opgegeven teken reeks</span><span class="sxs-lookup"><span data-stu-id="429f6-115">Example 2: Get time zones that match a specified string</span></span>

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

<span data-ttu-id="429f6-116">Met deze opdracht worden alle tijd zones opgehaald die overeenkomen met het opgegeven Joker teken.</span><span class="sxs-lookup"><span data-stu-id="429f6-116">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="429f6-117">Voor beeld 3: alle beschik bare tijd zones ophalen</span><span class="sxs-lookup"><span data-stu-id="429f6-117">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="429f6-118">Met deze opdracht worden alle beschik bare tijd zones opgehaald.</span><span class="sxs-lookup"><span data-stu-id="429f6-118">This command gets all available time zones.</span></span>

## <span data-ttu-id="429f6-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="429f6-119">PARAMETERS</span></span>

### <span data-ttu-id="429f6-120">-Id</span><span class="sxs-lookup"><span data-stu-id="429f6-120">-Id</span></span>

<span data-ttu-id="429f6-121">Hiermee geeft u als een teken reeks matrix de ID of Id's op van de tijd zones die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="429f6-121">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="429f6-122">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="429f6-122">-ListAvailable</span></span>

<span data-ttu-id="429f6-123">Geeft aan dat met deze cmdlet alle beschik bare tijd zones worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="429f6-123">Indicates that this cmdlet gets all available time zones.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="429f6-124">-Name</span><span class="sxs-lookup"><span data-stu-id="429f6-124">-Name</span></span>

<span data-ttu-id="429f6-125">Hiermee geeft u als een teken reeks matrix de naam of namen op van de tijd zones die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="429f6-125">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="429f6-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="429f6-126">CommonParameters</span></span>

<span data-ttu-id="429f6-127">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="429f6-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="429f6-128">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="429f6-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="429f6-129">INVOER</span><span class="sxs-lookup"><span data-stu-id="429f6-129">INPUTS</span></span>

### <span data-ttu-id="429f6-130">System.String[]</span><span class="sxs-lookup"><span data-stu-id="429f6-130">System.String[]</span></span>

## <span data-ttu-id="429f6-131">UITVOER</span><span class="sxs-lookup"><span data-stu-id="429f6-131">OUTPUTS</span></span>

### <span data-ttu-id="429f6-132">System. time zone info []</span><span class="sxs-lookup"><span data-stu-id="429f6-132">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="429f6-133">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="429f6-133">NOTES</span></span>

## <span data-ttu-id="429f6-134">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="429f6-134">RELATED LINKS</span></span>

[<span data-ttu-id="429f6-135">Set-tijd zone</span><span class="sxs-lookup"><span data-stu-id="429f6-135">Set-TimeZone</span></span>](Set-TimeZone.md)

