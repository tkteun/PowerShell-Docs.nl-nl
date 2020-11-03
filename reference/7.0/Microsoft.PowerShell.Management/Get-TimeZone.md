---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 4ed02426fbce279adc3f30af0c95b11966fe75a5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249703"
---
# <span data-ttu-id="cc28f-103">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="cc28f-103">Get-TimeZone</span></span>

## <span data-ttu-id="cc28f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cc28f-104">SYNOPSIS</span></span>
<span data-ttu-id="cc28f-105">Hiermee wordt de huidige tijd zone of een lijst met beschik bare tijd zones opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc28f-105">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="cc28f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cc28f-106">SYNTAX</span></span>

### <span data-ttu-id="cc28f-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="cc28f-107">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="cc28f-108">Id</span><span class="sxs-lookup"><span data-stu-id="cc28f-108">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="cc28f-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="cc28f-109">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="cc28f-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cc28f-110">DESCRIPTION</span></span>

<span data-ttu-id="cc28f-111">Met de cmdlet **Get-time** zone wordt de huidige tijdzone of een lijst met beschik bare tijd zones opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc28f-111">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="cc28f-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cc28f-112">EXAMPLES</span></span>

### <span data-ttu-id="cc28f-113">Voor beeld 1: de huidige tijd zone ophalen</span><span class="sxs-lookup"><span data-stu-id="cc28f-113">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="cc28f-114">Met deze opdracht wordt de huidige tijd zone opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc28f-114">This command gets the current time zone.</span></span>

### <span data-ttu-id="cc28f-115">Voor beeld 2: tijd zones ophalen die overeenkomen met een opgegeven teken reeks</span><span class="sxs-lookup"><span data-stu-id="cc28f-115">Example 2: Get time zones that match a specified string</span></span>

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

<span data-ttu-id="cc28f-116">Met deze opdracht worden alle tijd zones opgehaald die overeenkomen met het opgegeven Joker teken.</span><span class="sxs-lookup"><span data-stu-id="cc28f-116">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="cc28f-117">Voor beeld 3: alle beschik bare tijd zones ophalen</span><span class="sxs-lookup"><span data-stu-id="cc28f-117">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="cc28f-118">Met deze opdracht worden alle beschik bare tijd zones opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc28f-118">This command gets all available time zones.</span></span>

## <span data-ttu-id="cc28f-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cc28f-119">PARAMETERS</span></span>

### <span data-ttu-id="cc28f-120">-Id</span><span class="sxs-lookup"><span data-stu-id="cc28f-120">-Id</span></span>

<span data-ttu-id="cc28f-121">Hiermee geeft u als een teken reeks matrix de ID of Id's op van de tijd zones die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc28f-121">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="cc28f-122">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="cc28f-122">-ListAvailable</span></span>

<span data-ttu-id="cc28f-123">Geeft aan dat met deze cmdlet alle beschik bare tijd zones worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc28f-123">Indicates that this cmdlet gets all available time zones.</span></span>

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

### <span data-ttu-id="cc28f-124">-Name</span><span class="sxs-lookup"><span data-stu-id="cc28f-124">-Name</span></span>

<span data-ttu-id="cc28f-125">Hiermee geeft u als een teken reeks matrix de naam of namen op van de tijd zones die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc28f-125">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="cc28f-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cc28f-126">CommonParameters</span></span>

<span data-ttu-id="cc28f-127">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cc28f-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cc28f-128">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cc28f-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cc28f-129">INVOER</span><span class="sxs-lookup"><span data-stu-id="cc28f-129">INPUTS</span></span>

### <span data-ttu-id="cc28f-130">System.String[]</span><span class="sxs-lookup"><span data-stu-id="cc28f-130">System.String[]</span></span>

## <span data-ttu-id="cc28f-131">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cc28f-131">OUTPUTS</span></span>

### <span data-ttu-id="cc28f-132">System. time zone info []</span><span class="sxs-lookup"><span data-stu-id="cc28f-132">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="cc28f-133">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cc28f-133">NOTES</span></span>

## <span data-ttu-id="cc28f-134">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cc28f-134">RELATED LINKS</span></span>

[<span data-ttu-id="cc28f-135">Set-tijd zone</span><span class="sxs-lookup"><span data-stu-id="cc28f-135">Set-TimeZone</span></span>](Set-TimeZone.md)
