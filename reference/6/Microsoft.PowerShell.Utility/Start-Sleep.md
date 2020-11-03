---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: 1a107b2e4c7414250154d576d6dc9554cb9d800b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250995"
---
# <span data-ttu-id="bee11-103">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="bee11-103">Start-Sleep</span></span>

## <span data-ttu-id="bee11-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bee11-104">SYNOPSIS</span></span>
<span data-ttu-id="bee11-105">Hiermee wordt de activiteit in een script of sessie onderbroken gedurende de opgegeven periode.</span><span class="sxs-lookup"><span data-stu-id="bee11-105">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="bee11-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bee11-106">SYNTAX</span></span>

### <span data-ttu-id="bee11-107">Seconden (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="bee11-107">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### <span data-ttu-id="bee11-108">Milliseconden</span><span class="sxs-lookup"><span data-stu-id="bee11-108">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="bee11-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bee11-109">DESCRIPTION</span></span>

<span data-ttu-id="bee11-110">De `Start-Sleep` cmdlet onderbreekt de activiteit in een script of sessie voor de opgegeven periode.</span><span class="sxs-lookup"><span data-stu-id="bee11-110">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span> <span data-ttu-id="bee11-111">U kunt deze gebruiken voor veel taken, zoals het wachten op het volt ooien of onderbreken van een bewerking voordat een bewerking wordt herhaald.</span><span class="sxs-lookup"><span data-stu-id="bee11-111">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="bee11-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bee11-112">EXAMPLES</span></span>

### <span data-ttu-id="bee11-113">Voor beeld 1: alle opdrachten in de slaap stand gedurende 15 seconden</span><span class="sxs-lookup"><span data-stu-id="bee11-113">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

### <span data-ttu-id="bee11-114">Voor beeld 2: alle opdrachten in de slaap stand gedurende 1,5 seconden</span><span class="sxs-lookup"><span data-stu-id="bee11-114">Example 2: Sleep all commands for 1.5 seconds</span></span>

<span data-ttu-id="bee11-115">In dit voor beeld worden alle opdrachten in de sessie binnen een paar seconden in de slaap stand gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bee11-115">This example makes all the commands in the session sleep for one and one-half of a seconds.</span></span>

```powershell
Start-Sleep -Seconds 1.5
```

## <span data-ttu-id="bee11-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bee11-116">PARAMETERS</span></span>

### <span data-ttu-id="bee11-117">-Milliseconden</span><span class="sxs-lookup"><span data-stu-id="bee11-117">-Milliseconds</span></span>

<span data-ttu-id="bee11-118">Hiermee geeft u op hoe lang de resource in milliseconden slaap stand wordt gezet.</span><span class="sxs-lookup"><span data-stu-id="bee11-118">Specifies how long the resource sleeps in milliseconds.</span></span> <span data-ttu-id="bee11-119">De para meter kan worden afgekort tot **m**.</span><span class="sxs-lookup"><span data-stu-id="bee11-119">The parameter can be abbreviated as **m**.</span></span>

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

### <span data-ttu-id="bee11-120">-Seconden</span><span class="sxs-lookup"><span data-stu-id="bee11-120">-Seconds</span></span>

<span data-ttu-id="bee11-121">Hiermee geeft u op hoe lang de resource in seconden slaap stand heeft.</span><span class="sxs-lookup"><span data-stu-id="bee11-121">Specifies how long the resource sleeps in seconds.</span></span> <span data-ttu-id="bee11-122">U kunt de parameter naam weglaten of u kunt deze als **s** afkorten.</span><span class="sxs-lookup"><span data-stu-id="bee11-122">You can omit the parameter name or you can abbreviate it as **s**.</span></span> <span data-ttu-id="bee11-123">Vanaf Power shell 6.2.0 accepteert deze para meter nu breuk waarden.</span><span class="sxs-lookup"><span data-stu-id="bee11-123">Beginning in PowerShell 6.2.0, this parameter now accepts fractional values.</span></span>

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

### <span data-ttu-id="bee11-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bee11-124">CommonParameters</span></span>

<span data-ttu-id="bee11-125">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bee11-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bee11-126">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bee11-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bee11-127">INVOER</span><span class="sxs-lookup"><span data-stu-id="bee11-127">INPUTS</span></span>

### <span data-ttu-id="bee11-128">System. Int32</span><span class="sxs-lookup"><span data-stu-id="bee11-128">System.Int32</span></span>

<span data-ttu-id="bee11-129">U kunt het aantal seconden door sluizen `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="bee11-129">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="bee11-130">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bee11-130">OUTPUTS</span></span>

### <span data-ttu-id="bee11-131">Geen</span><span class="sxs-lookup"><span data-stu-id="bee11-131">None</span></span>

<span data-ttu-id="bee11-132">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bee11-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="bee11-133">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="bee11-133">NOTES</span></span>

- <span data-ttu-id="bee11-134">U kunt ook verwijzen naar `Start-Sleep` de ingebouwde alias `sleep` .</span><span class="sxs-lookup"><span data-stu-id="bee11-134">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="bee11-135">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bee11-135">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="bee11-136">`Ctrl+C` afgebroken `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="bee11-136">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="bee11-137">`Ctrl+C` niet onderbroken `[Threading.Thread]::Sleep` .</span><span class="sxs-lookup"><span data-stu-id="bee11-137">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="bee11-138">Zie voor meer informatie [thread. slaap methode](/dotnet/api/system.threading.thread.sleep).</span><span class="sxs-lookup"><span data-stu-id="bee11-138">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="bee11-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="bee11-139">RELATED LINKS</span></span>
