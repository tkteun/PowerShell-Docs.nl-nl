---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: 999ef16ef3065c26dc1d51e49c5ba5793af7db4a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251085"
---
# <span data-ttu-id="f421e-102">Get-Uptime</span><span class="sxs-lookup"><span data-stu-id="f421e-102">Get-Uptime</span></span>

## <span data-ttu-id="f421e-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f421e-103">SYNOPSIS</span></span>
<span data-ttu-id="f421e-104">Haal de **tijds duur** op sinds de laatste keer dat deze is opgestart.</span><span class="sxs-lookup"><span data-stu-id="f421e-104">Get the **TimeSpan** since last boot.</span></span>

## <span data-ttu-id="f421e-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f421e-105">SYNTAX</span></span>

### <span data-ttu-id="f421e-106">Time span (standaard)</span><span class="sxs-lookup"><span data-stu-id="f421e-106">Timespan (Default)</span></span>

```
Get-Uptime [<CommonParameters>]
```

### <span data-ttu-id="f421e-107">Moment</span><span class="sxs-lookup"><span data-stu-id="f421e-107">Since</span></span>

```
Get-Uptime [-Since] [<CommonParameters>]
```

## <span data-ttu-id="f421e-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f421e-108">DESCRIPTION</span></span>

<span data-ttu-id="f421e-109">Deze cmdlet retourneert de tijd die is verstreken sinds de laatste keer dat het besturings systeem is opgestart.</span><span class="sxs-lookup"><span data-stu-id="f421e-109">This cmdlet returns the time elapsed since the last boot of the operating system.</span></span>

<span data-ttu-id="f421e-110">De `Get-Uptime` cmdlet is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f421e-110">The `Get-Uptime` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="f421e-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f421e-111">EXAMPLES</span></span>

### <span data-ttu-id="f421e-112">Voor beeld 1: tijd weer geven sinds laatste keer opstarten</span><span class="sxs-lookup"><span data-stu-id="f421e-112">Example 1 - Show time since last boot</span></span>

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### <span data-ttu-id="f421e-113">Voor beeld 2: de tijd van de laatste keer opstarten weer geven</span><span class="sxs-lookup"><span data-stu-id="f421e-113">Example 2 - Show the time of the last boot</span></span>

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## <span data-ttu-id="f421e-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f421e-114">PARAMETERS</span></span>

### <span data-ttu-id="f421e-115">-Sinds</span><span class="sxs-lookup"><span data-stu-id="f421e-115">-Since</span></span>

<span data-ttu-id="f421e-116">Zorgt ervoor dat de cmdlet een **DateTime** -object retourneert dat de laatste keer dat het besturings systeem is opgestart.</span><span class="sxs-lookup"><span data-stu-id="f421e-116">Cause the cmdlet to return a **DateTime** object representing the last time that the operating system was booted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f421e-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f421e-117">CommonParameters</span></span>

<span data-ttu-id="f421e-118">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f421e-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f421e-119">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f421e-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f421e-120">INVOER</span><span class="sxs-lookup"><span data-stu-id="f421e-120">INPUTS</span></span>

### <span data-ttu-id="f421e-121">Geen</span><span class="sxs-lookup"><span data-stu-id="f421e-121">None</span></span>

## <span data-ttu-id="f421e-122">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f421e-122">OUTPUTS</span></span>

### <span data-ttu-id="f421e-123">System. time span</span><span class="sxs-lookup"><span data-stu-id="f421e-123">System.TimeSpan</span></span>

<span data-ttu-id="f421e-124">Dit is het standaard retour type wanneer er geen para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f421e-124">This is the default return type when no parameters are used.</span></span>

### <span data-ttu-id="f421e-125">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="f421e-125">System.DateTime</span></span>

<span data-ttu-id="f421e-126">Dit type wordt geretourneerd wanneer de **sinds** -para meter wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f421e-126">This type is returned when using the **Since** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="f421e-127">Als Windows snel opstarten is ingeschakeld, wordt de waarde die is opgeslagen in **LastBootUpTime** niet door Windows bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="f421e-127">If Windows fast startup is enabled, Windows does not update the value stored in **LastBootUpTime**.</span></span> <span data-ttu-id="f421e-128">Als u snel opstarten wilt uitschakelen, voert u de volgende opdracht uit: `Powercfg -h off` .</span><span class="sxs-lookup"><span data-stu-id="f421e-128">To disable fast startup, run the following command: `Powercfg -h off`.</span></span>
>
> <span data-ttu-id="f421e-129">Zie voor meer informatie over het snel opstarten van Windows een [onderscheid maken tussen snel opstarten vanuit](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation)de slaap stand.</span><span class="sxs-lookup"><span data-stu-id="f421e-129">For more information about Windows fast startup, see [Distinguishing Fast Startup from Wake-from-Hibernation](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).</span></span>

## <span data-ttu-id="f421e-130">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f421e-130">NOTES</span></span>

<span data-ttu-id="f421e-131">In Windows is de geretourneerde waarde hetzelfde als de eigenschap **LastBootUpTime** van de klasse **Win32_OperatingSystem** in WMI.</span><span class="sxs-lookup"><span data-stu-id="f421e-131">On Windows, the value returned is the same as the **LastBootUpTime** property of the **Win32_OperatingSystem** class in WMI.</span></span>

## <span data-ttu-id="f421e-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f421e-132">RELATED LINKS</span></span>

[<span data-ttu-id="f421e-133">Win32_OperatingSystem</span><span class="sxs-lookup"><span data-stu-id="f421e-133">Win32_OperatingSystem</span></span>](/windows/win32/cimwin32prov/win32-operatingsystem#properties)
