---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4d06fdd1d5a616c24a4dd7bec10ea4dadea4062
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705808"
---
# <span data-ttu-id="3d6dc-102">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="3d6dc-102">Start-Sleep</span></span>

## <span data-ttu-id="3d6dc-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3d6dc-103">SYNOPSIS</span></span>
<span data-ttu-id="3d6dc-104">Hiermee wordt de activiteit in een script of sessie onderbroken gedurende de opgegeven periode.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-104">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="3d6dc-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3d6dc-105">SYNTAX</span></span>

### <span data-ttu-id="3d6dc-106">Seconden (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="3d6dc-106">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### <span data-ttu-id="3d6dc-107">Milliseconden</span><span class="sxs-lookup"><span data-stu-id="3d6dc-107">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="3d6dc-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3d6dc-108">DESCRIPTION</span></span>

<span data-ttu-id="3d6dc-109">De `Start-Sleep` cmdlet onderbreekt de activiteit in een script of sessie voor de opgegeven periode.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-109">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span> <span data-ttu-id="3d6dc-110">U kunt deze gebruiken voor veel taken, zoals het wachten op het volt ooien of onderbreken van een bewerking voordat een bewerking wordt herhaald.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-110">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="3d6dc-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3d6dc-111">EXAMPLES</span></span>

### <span data-ttu-id="3d6dc-112">Voor beeld 1: alle opdrachten in de slaap stand gedurende 15 seconden</span><span class="sxs-lookup"><span data-stu-id="3d6dc-112">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

### <span data-ttu-id="3d6dc-113">Voor beeld 2: alle opdrachten in de slaap stand gedurende 1,5 seconden</span><span class="sxs-lookup"><span data-stu-id="3d6dc-113">Example 2: Sleep all commands for 1.5 seconds</span></span>

<span data-ttu-id="3d6dc-114">In dit voor beeld worden alle opdrachten in de sessie binnen een paar seconden in de slaap stand gemaakt.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-114">This example makes all the commands in the session sleep for one and one-half of a seconds.</span></span>

```powershell
Start-Sleep -Seconds 1.5
```

## <span data-ttu-id="3d6dc-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d6dc-115">PARAMETERS</span></span>

### <span data-ttu-id="3d6dc-116">-Milliseconden</span><span class="sxs-lookup"><span data-stu-id="3d6dc-116">-Milliseconds</span></span>

<span data-ttu-id="3d6dc-117">Hiermee geeft u op hoe lang de resource in milliseconden slaap stand wordt gezet.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-117">Specifies how long the resource sleeps in milliseconds.</span></span> <span data-ttu-id="3d6dc-118">De para meter kan worden afgekort tot **m**.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-118">The parameter can be abbreviated as **m**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d6dc-119">-Seconden</span><span class="sxs-lookup"><span data-stu-id="3d6dc-119">-Seconds</span></span>

<span data-ttu-id="3d6dc-120">Hiermee geeft u op hoe lang de resource in seconden slaap stand heeft.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-120">Specifies how long the resource sleeps in seconds.</span></span> <span data-ttu-id="3d6dc-121">U kunt de parameter naam weglaten of u kunt deze als **s** afkorten.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-121">You can omit the parameter name or you can abbreviate it as **s**.</span></span> <span data-ttu-id="3d6dc-122">Vanaf Power shell 6.2.0 accepteert deze para meter nu breuk waarden.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-122">Beginning in PowerShell 6.2.0, this parameter now accepts fractional values.</span></span>

```yaml
Type: System.Double
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3d6dc-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d6dc-123">CommonParameters</span></span>

<span data-ttu-id="3d6dc-124">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d6dc-125">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-125">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3d6dc-126">INVOER</span><span class="sxs-lookup"><span data-stu-id="3d6dc-126">INPUTS</span></span>

### <span data-ttu-id="3d6dc-127">System. Int32</span><span class="sxs-lookup"><span data-stu-id="3d6dc-127">System.Int32</span></span>

<span data-ttu-id="3d6dc-128">U kunt het aantal seconden door sluizen `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="3d6dc-128">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="3d6dc-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3d6dc-129">OUTPUTS</span></span>

### <span data-ttu-id="3d6dc-130">Geen</span><span class="sxs-lookup"><span data-stu-id="3d6dc-130">None</span></span>

<span data-ttu-id="3d6dc-131">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-131">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="3d6dc-132">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3d6dc-132">NOTES</span></span>

- <span data-ttu-id="3d6dc-133">U kunt ook verwijzen naar `Start-Sleep` de ingebouwde alias `sleep` .</span><span class="sxs-lookup"><span data-stu-id="3d6dc-133">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="3d6dc-134">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3d6dc-134">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="3d6dc-135">`Ctrl+C` afgebroken `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="3d6dc-135">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="3d6dc-136">`Ctrl+C` niet onderbroken `[Threading.Thread]::Sleep` .</span><span class="sxs-lookup"><span data-stu-id="3d6dc-136">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="3d6dc-137">Zie voor meer informatie [thread. slaap methode](/dotnet/api/system.threading.thread.sleep).</span><span class="sxs-lookup"><span data-stu-id="3d6dc-137">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="3d6dc-138">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3d6dc-138">RELATED LINKS</span></span>

