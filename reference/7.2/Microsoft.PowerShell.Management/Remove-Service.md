---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: 645efc2d271a3b95801c8d0d264ee33ed788f15f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705884"
---
# <span data-ttu-id="f8bdd-102">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="f8bdd-102">Remove-Service</span></span>

## <span data-ttu-id="f8bdd-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f8bdd-103">SYNOPSIS</span></span>
<span data-ttu-id="f8bdd-104">Hiermee verwijdert u een Windows-service.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-104">Removes a Windows service.</span></span>

## <span data-ttu-id="f8bdd-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f8bdd-105">SYNTAX</span></span>

### <span data-ttu-id="f8bdd-106">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="f8bdd-106">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f8bdd-107">Input object</span><span class="sxs-lookup"><span data-stu-id="f8bdd-107">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f8bdd-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f8bdd-108">DESCRIPTION</span></span>

<span data-ttu-id="f8bdd-109">Met de `Remove-Service` cmdlet wordt een Windows-service in het REGI ster en in de service database verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-109">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="f8bdd-110">De `Remove-Service` cmdlet is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-110">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="f8bdd-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f8bdd-111">EXAMPLES</span></span>

### <span data-ttu-id="f8bdd-112">Voor beeld 1: een service verwijderen</span><span class="sxs-lookup"><span data-stu-id="f8bdd-112">Example 1: Remove a service</span></span>

<span data-ttu-id="f8bdd-113">Hiermee verwijdert u een service met de naam TestService.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-113">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="f8bdd-114">Voor beeld 2: een service verwijderen met de weergave naam</span><span class="sxs-lookup"><span data-stu-id="f8bdd-114">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="f8bdd-115">In dit voor beeld wordt een service met de naam TestService verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-115">This example removes a service named TestService.</span></span> <span data-ttu-id="f8bdd-116">De opdracht wordt gebruikt `Get-Service` om een object op te halen dat de TestService-service vertegenwoordigt met behulp van de weergave naam.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-116">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="f8bdd-117">De pijplijn operator ( `|` ) sluizen het object naar `Remove-Service` , waardoor de service wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-117">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="f8bdd-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f8bdd-118">PARAMETERS</span></span>

### <span data-ttu-id="f8bdd-119">-Input object</span><span class="sxs-lookup"><span data-stu-id="f8bdd-119">-InputObject</span></span>

<span data-ttu-id="f8bdd-120">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-120">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="f8bdd-121">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-121">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="f8bdd-122">-Name</span><span class="sxs-lookup"><span data-stu-id="f8bdd-122">-Name</span></span>

<span data-ttu-id="f8bdd-123">Hiermee geeft u de service namen op van de services die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-123">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="f8bdd-124">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-124">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f8bdd-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f8bdd-125">-Confirm</span></span>

<span data-ttu-id="f8bdd-126">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f8bdd-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f8bdd-127">-WhatIf</span></span>

<span data-ttu-id="f8bdd-128">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-128">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f8bdd-129">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f8bdd-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f8bdd-130">CommonParameters</span></span>

<span data-ttu-id="f8bdd-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f8bdd-132">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f8bdd-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="f8bdd-133">INPUTS</span></span>

### <span data-ttu-id="f8bdd-134">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="f8bdd-134">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="f8bdd-135">U kunt een service object of een teken reeks die de naam van een service bevat, door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-135">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="f8bdd-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f8bdd-136">OUTPUTS</span></span>

### <span data-ttu-id="f8bdd-137">Geen</span><span class="sxs-lookup"><span data-stu-id="f8bdd-137">None</span></span>

<span data-ttu-id="f8bdd-138">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-138">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="f8bdd-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f8bdd-139">NOTES</span></span>

<span data-ttu-id="f8bdd-140">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="f8bdd-140">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="f8bdd-141">Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="f8bdd-141">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="f8bdd-142">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f8bdd-142">RELATED LINKS</span></span>

[<span data-ttu-id="f8bdd-143">Get-Service</span><span class="sxs-lookup"><span data-stu-id="f8bdd-143">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="f8bdd-144">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="f8bdd-144">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="f8bdd-145">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="f8bdd-145">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="f8bdd-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="f8bdd-146">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="f8bdd-147">Start-Service</span><span class="sxs-lookup"><span data-stu-id="f8bdd-147">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="f8bdd-148">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="f8bdd-148">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="f8bdd-149">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="f8bdd-149">Suspend-Service</span></span>](Suspend-Service.md)
