---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 9515f524df38813817b3fefd1437a3e2df296392
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705950"
---
# <span data-ttu-id="62478-102">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="62478-102">Suspend-Service</span></span>

## <span data-ttu-id="62478-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="62478-103">SYNOPSIS</span></span>
<span data-ttu-id="62478-104">Hiermee worden een of meer actieve services onderbroken (onderbroken).</span><span class="sxs-lookup"><span data-stu-id="62478-104">Suspends (pauses) one or more running services.</span></span>

## <span data-ttu-id="62478-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="62478-105">SYNTAX</span></span>

### <span data-ttu-id="62478-106">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="62478-106">InputObject (Default)</span></span>

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="62478-107">Standaard</span><span class="sxs-lookup"><span data-stu-id="62478-107">Default</span></span>

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="62478-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="62478-108">DisplayName</span></span>

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="62478-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="62478-109">DESCRIPTION</span></span>

<span data-ttu-id="62478-110">De `Suspend-Service` cmdlet verzendt een suspend-bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="62478-110">The `Suspend-Service` cmdlet sends a suspend message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="62478-111">Tijdens de onderbreking wordt de service nog steeds uitgevoerd, maar de actie wordt gestopt totdat deze wordt hervat, bijvoorbeeld door de usingthe- `Resume-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="62478-111">While suspended, the service is still running, but its action is stopped until resumed, such as by usingthe `Resume-Service` cmdlet.</span></span> <span data-ttu-id="62478-112">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object door te geven dat staat voor de services die u wilt onderbreken.</span><span class="sxs-lookup"><span data-stu-id="62478-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to suspend.</span></span>

## <span data-ttu-id="62478-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="62478-113">EXAMPLES</span></span>

### <span data-ttu-id="62478-114">Voor beeld 1: een service opschorten</span><span class="sxs-lookup"><span data-stu-id="62478-114">Example 1: Suspend a service</span></span>

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

<span data-ttu-id="62478-115">Met deze opdracht wordt de service Telnet-service (TlntSvr) op de lokale computer onderbroken.</span><span class="sxs-lookup"><span data-stu-id="62478-115">This command suspends the Telnet service (Tlntsvr) service on the local computer.</span></span>

### <span data-ttu-id="62478-116">Voor beeld 2: weer geven wat er gebeurt als u services uitbreekt</span><span class="sxs-lookup"><span data-stu-id="62478-116">Example 2: Display what would happen if you suspend services</span></span>

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

<span data-ttu-id="62478-117">Met deze opdracht wordt aangegeven wat er gebeurt als u de services met een service naam die begint met LANMAN hebt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="62478-117">This command tells what would happen if you suspended the services that have a service name that starts with lanman.</span></span> <span data-ttu-id="62478-118">Als u de services wilt onderbreken, voert u de opdracht opnieuw uit zonder de para meter **WhatIf** .</span><span class="sxs-lookup"><span data-stu-id="62478-118">To suspend the services, rerun the command without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="62478-119">Voor beeld 3: een service ophalen en opschorten</span><span class="sxs-lookup"><span data-stu-id="62478-119">Example 3: Get and suspend a service</span></span>

```
PS C:\> Get-Service schedule | Suspend-Service
```

<span data-ttu-id="62478-120">Met deze opdracht wordt de `Get-Service` cmdlet gebruikt om een object op te halen dat de taak planner-service (Schedule) op de computer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="62478-120">This command uses the `Get-Service` cmdlet to get an object that represents the Task Scheduler (Schedule) service on the computer.</span></span> <span data-ttu-id="62478-121">Met de pijplijn operator ( `|` ) wordt het resultaat door gegeven aan `Suspend-Service` , waardoor de service wordt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="62478-121">The pipeline operator (`|`) passes the result to `Suspend-Service`, which suspends the service.</span></span>

### <span data-ttu-id="62478-122">Voor beeld 4: alle services onderbreken die kunnen worden onderbroken</span><span class="sxs-lookup"><span data-stu-id="62478-122">Example 4: Suspend all services that can be suspended</span></span>

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

<span data-ttu-id="62478-123">Met deze opdracht worden alle services op de computer opgeschort die kunnen worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="62478-123">This command suspends all of the services on the computer that can be suspended.</span></span> <span data-ttu-id="62478-124">Hiermee worden `Get-Service` objecten opgehaald die de services op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="62478-124">It uses `Get-Service` to get objects that represent the services on the computer.</span></span> <span data-ttu-id="62478-125">De pijplijn operator geeft de resultaten door aan de `Where-Object` cmdlet, waarmee alleen de services worden geselecteerd met een waarde van `$True` voor de eigenschap **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="62478-125">The pipeline operator passes the results to the `Where-Object` cmdlet, which selects only the services that have a value of `$True` for the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="62478-126">Een andere pijplijn operator geeft de resultaten door `Suspend-Service` .</span><span class="sxs-lookup"><span data-stu-id="62478-126">Another pipeline operator passes the results to `Suspend-Service`.</span></span> <span data-ttu-id="62478-127">De **bevestigings** parameter vraagt u om bevestiging voordat alle services worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="62478-127">The **Confirm** parameter prompts you for confirmation before suspending each of the services.</span></span>

## <span data-ttu-id="62478-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="62478-128">PARAMETERS</span></span>

### <span data-ttu-id="62478-129">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="62478-129">-DisplayName</span></span>

<span data-ttu-id="62478-130">Hiermee geeft u de weergave namen op van de services die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="62478-130">Specifies the display names of the services to be suspended.</span></span> <span data-ttu-id="62478-131">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="62478-131">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="62478-132">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="62478-132">-Exclude</span></span>

<span data-ttu-id="62478-133">Hiermee geeft u services op die van de opgegeven services worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="62478-133">Specifies services to omit from the specified services.</span></span> <span data-ttu-id="62478-134">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="62478-134">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="62478-135">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="62478-135">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="62478-136">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="62478-136">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="62478-137">-Include</span><span class="sxs-lookup"><span data-stu-id="62478-137">-Include</span></span>

<span data-ttu-id="62478-138">Hiermee worden de services opgegeven die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="62478-138">Specifies services to suspend.</span></span> <span data-ttu-id="62478-139">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="62478-139">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="62478-140">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="62478-140">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="62478-141">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="62478-141">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="62478-142">-Input object</span><span class="sxs-lookup"><span data-stu-id="62478-142">-InputObject</span></span>

<span data-ttu-id="62478-143">Hiermee geeft u **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="62478-143">Specifies **ServiceController** objects that represent the services to suspend.</span></span> <span data-ttu-id="62478-144">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="62478-144">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="62478-145">-Name</span><span class="sxs-lookup"><span data-stu-id="62478-145">-Name</span></span>

<span data-ttu-id="62478-146">Hiermee geeft u de service namen op van de services die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="62478-146">Specifies the service names of the services to suspend.</span></span> <span data-ttu-id="62478-147">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="62478-147">Wildcard characters are permitted.</span></span>

<span data-ttu-id="62478-148">De parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="62478-148">The parameter name is optional.</span></span> <span data-ttu-id="62478-149">U kunt de **naam** of de alias ervan **gebruiken, of** u kunt de parameter naam weglaten.</span><span class="sxs-lookup"><span data-stu-id="62478-149">You can use **Name** or its alias, **ServiceName**, or you can omit the parameter name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="62478-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="62478-150">-PassThru</span></span>

<span data-ttu-id="62478-151">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="62478-151">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="62478-152">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="62478-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="62478-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="62478-153">-Confirm</span></span>

<span data-ttu-id="62478-154">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="62478-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="62478-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="62478-155">-WhatIf</span></span>

<span data-ttu-id="62478-156">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="62478-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="62478-157">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="62478-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="62478-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="62478-158">CommonParameters</span></span>

<span data-ttu-id="62478-159">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="62478-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="62478-160">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="62478-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="62478-161">INVOER</span><span class="sxs-lookup"><span data-stu-id="62478-161">INPUTS</span></span>

### <span data-ttu-id="62478-162">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="62478-162">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="62478-163">U kunt een service object of een teken reeks die een service naam bevat door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="62478-163">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="62478-164">UITVOER</span><span class="sxs-lookup"><span data-stu-id="62478-164">OUTPUTS</span></span>

### <span data-ttu-id="62478-165">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="62478-165">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="62478-166">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="62478-166">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="62478-167">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="62478-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="62478-168">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="62478-168">NOTES</span></span>

<span data-ttu-id="62478-169">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="62478-169">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="62478-170">`Suspend-Service` kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="62478-170">`Suspend-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="62478-171">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="62478-171">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="62478-172">`Suspend-Service` kan alleen services onderbreken die ondersteuning bieden voor onderbroken en hervat.</span><span class="sxs-lookup"><span data-stu-id="62478-172">`Suspend-Service` can suspend only services that support being suspended and resumed.</span></span> <span data-ttu-id="62478-173">Als u wilt bepalen of een bepaalde service kan worden onderbroken, gebruikt u de `Get-Service` cmdlet samen met de eigenschap **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="62478-173">To determine whether a particular service can be suspended, use the `Get-Service` cmdlet together with the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="62478-174">Bijvoorbeeld `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span><span class="sxs-lookup"><span data-stu-id="62478-174">For example, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span></span> <span data-ttu-id="62478-175">Als u wilt zoeken naar alle services op de computer die kunnen worden onderbroken, typt u `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` .</span><span class="sxs-lookup"><span data-stu-id="62478-175">To find all services on the computer that can be suspended, type `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}`.</span></span>
- <span data-ttu-id="62478-176">Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="62478-176">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="62478-177">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="62478-177">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="62478-178">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="62478-178">RELATED LINKS</span></span>

[<span data-ttu-id="62478-179">Get-Service</span><span class="sxs-lookup"><span data-stu-id="62478-179">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="62478-180">New-Service</span><span class="sxs-lookup"><span data-stu-id="62478-180">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="62478-181">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="62478-181">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="62478-182">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="62478-182">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="62478-183">Set-Service</span><span class="sxs-lookup"><span data-stu-id="62478-183">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="62478-184">Start-Service</span><span class="sxs-lookup"><span data-stu-id="62478-184">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="62478-185">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="62478-185">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="62478-186">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="62478-186">Remove-Service</span></span>](Remove-Service.md)
