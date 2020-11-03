---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: b23e263c2d6ff64ca2a799614d213f1e549cdfe3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249841"
---
# <span data-ttu-id="4f60f-103">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="4f60f-103">Remove-Service</span></span>

## <span data-ttu-id="4f60f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4f60f-104">SYNOPSIS</span></span>
<span data-ttu-id="4f60f-105">Hiermee verwijdert u een Windows-service.</span><span class="sxs-lookup"><span data-stu-id="4f60f-105">Removes a Windows service.</span></span>

## <span data-ttu-id="4f60f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4f60f-106">SYNTAX</span></span>

### <span data-ttu-id="4f60f-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="4f60f-107">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4f60f-108">Input object</span><span class="sxs-lookup"><span data-stu-id="4f60f-108">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4f60f-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4f60f-109">DESCRIPTION</span></span>

<span data-ttu-id="4f60f-110">Met de `Remove-Service` cmdlet wordt een Windows-service in het REGI ster en in de service database verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4f60f-110">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="4f60f-111">De `Remove-Service` cmdlet is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="4f60f-111">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="4f60f-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4f60f-112">EXAMPLES</span></span>

### <span data-ttu-id="4f60f-113">Voor beeld 1: een service verwijderen</span><span class="sxs-lookup"><span data-stu-id="4f60f-113">Example 1: Remove a service</span></span>

<span data-ttu-id="4f60f-114">Hiermee verwijdert u een service met de naam TestService.</span><span class="sxs-lookup"><span data-stu-id="4f60f-114">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="4f60f-115">Voor beeld 2: een service verwijderen met de weergave naam</span><span class="sxs-lookup"><span data-stu-id="4f60f-115">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="4f60f-116">In dit voor beeld wordt een service met de naam TestService verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4f60f-116">This example removes a service named TestService.</span></span> <span data-ttu-id="4f60f-117">De opdracht wordt gebruikt `Get-Service` om een object op te halen dat de TestService-service vertegenwoordigt met behulp van de weergave naam.</span><span class="sxs-lookup"><span data-stu-id="4f60f-117">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="4f60f-118">De pijplijn operator ( `|` ) sluizen het object naar `Remove-Service` , waardoor de service wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4f60f-118">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="4f60f-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f60f-119">PARAMETERS</span></span>

### <span data-ttu-id="4f60f-120">-Input object</span><span class="sxs-lookup"><span data-stu-id="4f60f-120">-InputObject</span></span>

<span data-ttu-id="4f60f-121">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4f60f-121">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="4f60f-122">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="4f60f-122">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4f60f-123">-Name</span><span class="sxs-lookup"><span data-stu-id="4f60f-123">-Name</span></span>

<span data-ttu-id="4f60f-124">Hiermee geeft u de service namen op van de services die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="4f60f-124">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="4f60f-125">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="4f60f-125">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="4f60f-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4f60f-126">-Confirm</span></span>

<span data-ttu-id="4f60f-127">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4f60f-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4f60f-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4f60f-128">-WhatIf</span></span>

<span data-ttu-id="4f60f-129">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4f60f-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4f60f-130">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4f60f-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4f60f-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f60f-131">CommonParameters</span></span>

<span data-ttu-id="4f60f-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4f60f-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f60f-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4f60f-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f60f-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="4f60f-134">INPUTS</span></span>

### <span data-ttu-id="4f60f-135">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="4f60f-135">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="4f60f-136">U kunt een service object of een teken reeks die de naam van een service bevat, door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f60f-136">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="4f60f-137">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4f60f-137">OUTPUTS</span></span>

### <span data-ttu-id="4f60f-138">Geen</span><span class="sxs-lookup"><span data-stu-id="4f60f-138">None</span></span>

<span data-ttu-id="4f60f-139">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4f60f-139">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="4f60f-140">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4f60f-140">NOTES</span></span>

<span data-ttu-id="4f60f-141">Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="4f60f-141">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="4f60f-142">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4f60f-142">RELATED LINKS</span></span>

[<span data-ttu-id="4f60f-143">Get-Service</span><span class="sxs-lookup"><span data-stu-id="4f60f-143">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="4f60f-144">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="4f60f-144">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="4f60f-145">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="4f60f-145">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="4f60f-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="4f60f-146">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="4f60f-147">Start-Service</span><span class="sxs-lookup"><span data-stu-id="4f60f-147">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="4f60f-148">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="4f60f-148">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="4f60f-149">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="4f60f-149">Suspend-Service</span></span>](Suspend-Service.md)

