---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 3/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4add39c09b6123aaf8c9302529346a6b1dec391
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250363"
---
# <span data-ttu-id="88d48-103">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="88d48-103">Start-Sleep</span></span>

## <span data-ttu-id="88d48-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="88d48-104">SYNOPSIS</span></span>
<span data-ttu-id="88d48-105">Hiermee wordt de activiteit in een script of sessie onderbroken gedurende de opgegeven periode.</span><span class="sxs-lookup"><span data-stu-id="88d48-105">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="88d48-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="88d48-106">SYNTAX</span></span>

### <span data-ttu-id="88d48-107">Seconden (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="88d48-107">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="88d48-108">Milliseconden</span><span class="sxs-lookup"><span data-stu-id="88d48-108">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="88d48-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="88d48-109">DESCRIPTION</span></span>

<span data-ttu-id="88d48-110">De `Start-Sleep` cmdlet onderbreekt de activiteit in een script of sessie voor de opgegeven periode.</span><span class="sxs-lookup"><span data-stu-id="88d48-110">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span>
<span data-ttu-id="88d48-111">U kunt deze gebruiken voor veel taken, zoals het wachten op het volt ooien of onderbreken van een bewerking voordat een bewerking wordt herhaald.</span><span class="sxs-lookup"><span data-stu-id="88d48-111">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="88d48-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="88d48-112">EXAMPLES</span></span>

### <span data-ttu-id="88d48-113">Voor beeld 1: alle opdrachten in de slaap stand gedurende 15 seconden</span><span class="sxs-lookup"><span data-stu-id="88d48-113">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

<span data-ttu-id="88d48-114">Met deze opdracht worden alle opdrachten in de sessie-slaap stand 15 seconden.</span><span class="sxs-lookup"><span data-stu-id="88d48-114">This command makes all commands in the session sleep for 15 seconds.</span></span>

### <span data-ttu-id="88d48-115">Voor beeld 2: alle opdrachten in de slaap stand zetten</span><span class="sxs-lookup"><span data-stu-id="88d48-115">Example 2: Sleep all commands</span></span>

```powershell
Start-Sleep -m 500
```

<span data-ttu-id="88d48-116">Met deze opdracht worden alle opdrachten in de sessie-slaap stand voor een helft van een seconde (500 milliseconden).</span><span class="sxs-lookup"><span data-stu-id="88d48-116">This command makes all the commands in the session sleep for one-half of a second (500 milliseconds).</span></span>

## <span data-ttu-id="88d48-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="88d48-117">PARAMETERS</span></span>

### <span data-ttu-id="88d48-118">-Milliseconden</span><span class="sxs-lookup"><span data-stu-id="88d48-118">-Milliseconds</span></span>

<span data-ttu-id="88d48-119">Hiermee geeft u op hoe lang de resource in milliseconden slaap stand wordt gezet.</span><span class="sxs-lookup"><span data-stu-id="88d48-119">Specifies how long the resource sleeps in milliseconds.</span></span>
<span data-ttu-id="88d48-120">De para meter kan worden afgekort tot **m**.</span><span class="sxs-lookup"><span data-stu-id="88d48-120">The parameter can be abbreviated as **m**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="88d48-121">-Seconden</span><span class="sxs-lookup"><span data-stu-id="88d48-121">-Seconds</span></span>

<span data-ttu-id="88d48-122">Hiermee geeft u op hoe lang de resource in seconden slaap stand heeft.</span><span class="sxs-lookup"><span data-stu-id="88d48-122">Specifies how long the resource sleeps in seconds.</span></span>
<span data-ttu-id="88d48-123">U kunt de parameter naam ( **seconden** ) weglaten, of u kunt deze afkorten als **s**.</span><span class="sxs-lookup"><span data-stu-id="88d48-123">You can omit the parameter name ( **Seconds** ), or you can abbreviate it as **s**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="88d48-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="88d48-124">CommonParameters</span></span>

<span data-ttu-id="88d48-125">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="88d48-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="88d48-126">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="88d48-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="88d48-127">INVOER</span><span class="sxs-lookup"><span data-stu-id="88d48-127">INPUTS</span></span>

### <span data-ttu-id="88d48-128">System. Int32</span><span class="sxs-lookup"><span data-stu-id="88d48-128">System.Int32</span></span>

<span data-ttu-id="88d48-129">U kunt het aantal seconden door sluizen `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="88d48-129">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="88d48-130">UITVOER</span><span class="sxs-lookup"><span data-stu-id="88d48-130">OUTPUTS</span></span>

### <span data-ttu-id="88d48-131">Geen</span><span class="sxs-lookup"><span data-stu-id="88d48-131">None</span></span>

<span data-ttu-id="88d48-132">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="88d48-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="88d48-133">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="88d48-133">NOTES</span></span>

- <span data-ttu-id="88d48-134">U kunt ook verwijzen naar `Start-Sleep` de ingebouwde alias `sleep` .</span><span class="sxs-lookup"><span data-stu-id="88d48-134">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="88d48-135">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="88d48-135">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="88d48-136">`Ctrl+C` afgebroken `Start-Sleep` .</span><span class="sxs-lookup"><span data-stu-id="88d48-136">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="88d48-137">`Ctrl+C` niet onderbroken `[Threading.Thread]::Sleep` .</span><span class="sxs-lookup"><span data-stu-id="88d48-137">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="88d48-138">Zie voor meer informatie [thread. slaap methode](/dotnet/api/system.threading.thread.sleep).</span><span class="sxs-lookup"><span data-stu-id="88d48-138">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="88d48-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="88d48-139">RELATED LINKS</span></span>
