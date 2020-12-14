---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 22034eeac6988478a5f2ff87b2582cc5e1acc1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705728"
---
# <span data-ttu-id="6d35d-102">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="6d35d-102">Get-TimeZone</span></span>

## <span data-ttu-id="6d35d-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6d35d-103">SYNOPSIS</span></span>
<span data-ttu-id="6d35d-104">Hiermee wordt de huidige tijd zone of een lijst met beschik bare tijd zones opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6d35d-104">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="6d35d-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6d35d-105">SYNTAX</span></span>

### <span data-ttu-id="6d35d-106">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="6d35d-106">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="6d35d-107">Id</span><span class="sxs-lookup"><span data-stu-id="6d35d-107">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6d35d-108">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="6d35d-108">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="6d35d-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6d35d-109">DESCRIPTION</span></span>

<span data-ttu-id="6d35d-110">Met de cmdlet **Get-time** zone wordt de huidige tijdzone of een lijst met beschik bare tijd zones opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6d35d-110">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="6d35d-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6d35d-111">EXAMPLES</span></span>

### <span data-ttu-id="6d35d-112">Voor beeld 1: de huidige tijd zone ophalen</span><span class="sxs-lookup"><span data-stu-id="6d35d-112">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="6d35d-113">Met deze opdracht wordt de huidige tijd zone opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6d35d-113">This command gets the current time zone.</span></span>

### <span data-ttu-id="6d35d-114">Voor beeld 2: tijd zones ophalen die overeenkomen met een opgegeven teken reeks</span><span class="sxs-lookup"><span data-stu-id="6d35d-114">Example 2: Get time zones that match a specified string</span></span>

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

<span data-ttu-id="6d35d-115">Met deze opdracht worden alle tijd zones opgehaald die overeenkomen met het opgegeven Joker teken.</span><span class="sxs-lookup"><span data-stu-id="6d35d-115">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="6d35d-116">Voor beeld 3: alle beschik bare tijd zones ophalen</span><span class="sxs-lookup"><span data-stu-id="6d35d-116">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="6d35d-117">Met deze opdracht worden alle beschik bare tijd zones opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6d35d-117">This command gets all available time zones.</span></span>

## <span data-ttu-id="6d35d-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6d35d-118">PARAMETERS</span></span>

### <span data-ttu-id="6d35d-119">-Id</span><span class="sxs-lookup"><span data-stu-id="6d35d-119">-Id</span></span>

<span data-ttu-id="6d35d-120">Hiermee geeft u als een teken reeks matrix de ID of Id's op van de tijd zones die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6d35d-120">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="6d35d-121">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="6d35d-121">-ListAvailable</span></span>

<span data-ttu-id="6d35d-122">Geeft aan dat met deze cmdlet alle beschik bare tijd zones worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6d35d-122">Indicates that this cmdlet gets all available time zones.</span></span>

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

### <span data-ttu-id="6d35d-123">-Name</span><span class="sxs-lookup"><span data-stu-id="6d35d-123">-Name</span></span>

<span data-ttu-id="6d35d-124">Hiermee geeft u als een teken reeks matrix de naam of namen op van de tijd zones die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6d35d-124">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

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

### <span data-ttu-id="6d35d-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6d35d-125">CommonParameters</span></span>

<span data-ttu-id="6d35d-126">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6d35d-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6d35d-127">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6d35d-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6d35d-128">INVOER</span><span class="sxs-lookup"><span data-stu-id="6d35d-128">INPUTS</span></span>

### <span data-ttu-id="6d35d-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6d35d-129">System.String[]</span></span>

## <span data-ttu-id="6d35d-130">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6d35d-130">OUTPUTS</span></span>

### <span data-ttu-id="6d35d-131">System. time zone info []</span><span class="sxs-lookup"><span data-stu-id="6d35d-131">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="6d35d-132">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6d35d-132">NOTES</span></span>

<span data-ttu-id="6d35d-133">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="6d35d-133">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="6d35d-134">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6d35d-134">RELATED LINKS</span></span>

[<span data-ttu-id="6d35d-135">Set-tijd zone</span><span class="sxs-lookup"><span data-stu-id="6d35d-135">Set-TimeZone</span></span>](Set-TimeZone.md)
