---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 11c957157231a858c9e76b5a339872538b142270
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346178"
---
# <span data-ttu-id="51c0b-103">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="51c0b-103">Suspend-Service</span></span>

## <span data-ttu-id="51c0b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="51c0b-104">SYNOPSIS</span></span>
<span data-ttu-id="51c0b-105">Hiermee worden een of meer actieve services onderbroken (onderbroken).</span><span class="sxs-lookup"><span data-stu-id="51c0b-105">Suspends (pauses) one or more running services.</span></span>

## <span data-ttu-id="51c0b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="51c0b-106">SYNTAX</span></span>

### <span data-ttu-id="51c0b-107">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="51c0b-107">InputObject (Default)</span></span>

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="51c0b-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="51c0b-108">Default</span></span>

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="51c0b-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="51c0b-109">DisplayName</span></span>

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="51c0b-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="51c0b-110">DESCRIPTION</span></span>

<span data-ttu-id="51c0b-111">De `Suspend-Service` cmdlet verzendt een suspend-bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="51c0b-111">The `Suspend-Service` cmdlet sends a suspend message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="51c0b-112">Tijdens de onderbreking wordt de service nog steeds uitgevoerd, maar de actie wordt gestopt totdat deze wordt hervat, bijvoorbeeld door de usingthe- `Resume-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51c0b-112">While suspended, the service is still running, but its action is stopped until resumed, such as by usingthe `Resume-Service` cmdlet.</span></span> <span data-ttu-id="51c0b-113">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object door te geven dat staat voor de services die u wilt onderbreken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to suspend.</span></span>

## <span data-ttu-id="51c0b-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="51c0b-114">EXAMPLES</span></span>

### <span data-ttu-id="51c0b-115">Voor beeld 1: een service opschorten</span><span class="sxs-lookup"><span data-stu-id="51c0b-115">Example 1: Suspend a service</span></span>

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

<span data-ttu-id="51c0b-116">Met deze opdracht wordt de service Telnet-service (TlntSvr) op de lokale computer onderbroken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-116">This command suspends the Telnet service (Tlntsvr) service on the local computer.</span></span>

### <span data-ttu-id="51c0b-117">Voor beeld 2: weer geven wat er gebeurt als u services uitbreekt</span><span class="sxs-lookup"><span data-stu-id="51c0b-117">Example 2: Display what would happen if you suspend services</span></span>

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

<span data-ttu-id="51c0b-118">Met deze opdracht wordt aangegeven wat er gebeurt als u de services met een service naam die begint met LANMAN hebt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-118">This command tells what would happen if you suspended the services that have a service name that starts with lanman.</span></span> <span data-ttu-id="51c0b-119">Als u de services wilt onderbreken, voert u de opdracht opnieuw uit zonder de para meter **WhatIf** .</span><span class="sxs-lookup"><span data-stu-id="51c0b-119">To suspend the services, rerun the command without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="51c0b-120">Voor beeld 3: een service ophalen en opschorten</span><span class="sxs-lookup"><span data-stu-id="51c0b-120">Example 3: Get and suspend a service</span></span>

```
PS C:\> Get-Service schedule | Suspend-Service
```

<span data-ttu-id="51c0b-121">Met deze opdracht wordt de `Get-Service` cmdlet gebruikt om een object op te halen dat de taak planner-service (Schedule) op de computer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="51c0b-121">This command uses the `Get-Service` cmdlet to get an object that represents the Task Scheduler (Schedule) service on the computer.</span></span> <span data-ttu-id="51c0b-122">Met de pijplijn operator ( `|` ) wordt het resultaat door gegeven aan `Suspend-Service` , waardoor de service wordt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-122">The pipeline operator (`|`) passes the result to `Suspend-Service`, which suspends the service.</span></span>

### <span data-ttu-id="51c0b-123">Voor beeld 4: alle services onderbreken die kunnen worden onderbroken</span><span class="sxs-lookup"><span data-stu-id="51c0b-123">Example 4: Suspend all services that can be suspended</span></span>

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

<span data-ttu-id="51c0b-124">Met deze opdracht worden alle services op de computer opgeschort die kunnen worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-124">This command suspends all of the services on the computer that can be suspended.</span></span> <span data-ttu-id="51c0b-125">Hiermee worden `Get-Service` objecten opgehaald die de services op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="51c0b-125">It uses `Get-Service` to get objects that represent the services on the computer.</span></span> <span data-ttu-id="51c0b-126">De pijplijn operator geeft de resultaten door aan de `Where-Object` cmdlet, waarmee alleen de services worden geselecteerd met een waarde van `$True` voor de eigenschap **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="51c0b-126">The pipeline operator passes the results to the `Where-Object` cmdlet, which selects only the services that have a value of `$True` for the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="51c0b-127">Een andere pijplijn operator geeft de resultaten door `Suspend-Service` .</span><span class="sxs-lookup"><span data-stu-id="51c0b-127">Another pipeline operator passes the results to `Suspend-Service`.</span></span> <span data-ttu-id="51c0b-128">De **bevestigings** parameter vraagt u om bevestiging voordat alle services worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-128">The **Confirm** parameter prompts you for confirmation before suspending each of the services.</span></span>

## <span data-ttu-id="51c0b-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="51c0b-129">PARAMETERS</span></span>

### <span data-ttu-id="51c0b-130">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="51c0b-130">-DisplayName</span></span>

<span data-ttu-id="51c0b-131">Hiermee geeft u de weergave namen op van de services die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-131">Specifies the display names of the services to be suspended.</span></span> <span data-ttu-id="51c0b-132">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="51c0b-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="51c0b-133">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="51c0b-133">-Exclude</span></span>

<span data-ttu-id="51c0b-134">Hiermee geeft u services op die van de opgegeven services worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="51c0b-134">Specifies services to omit from the specified services.</span></span> <span data-ttu-id="51c0b-135">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="51c0b-135">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="51c0b-136">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="51c0b-136">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="51c0b-137">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="51c0b-137">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="51c0b-138">-Include</span><span class="sxs-lookup"><span data-stu-id="51c0b-138">-Include</span></span>

<span data-ttu-id="51c0b-139">Hiermee worden de services opgegeven die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-139">Specifies services to suspend.</span></span> <span data-ttu-id="51c0b-140">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="51c0b-140">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="51c0b-141">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="51c0b-141">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="51c0b-142">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="51c0b-142">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="51c0b-143">-Input object</span><span class="sxs-lookup"><span data-stu-id="51c0b-143">-InputObject</span></span>

<span data-ttu-id="51c0b-144">Hiermee geeft u **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-144">Specifies **ServiceController** objects that represent the services to suspend.</span></span> <span data-ttu-id="51c0b-145">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="51c0b-145">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="51c0b-146">-Name</span><span class="sxs-lookup"><span data-stu-id="51c0b-146">-Name</span></span>

<span data-ttu-id="51c0b-147">Hiermee geeft u de service namen op van de services die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="51c0b-147">Specifies the service names of the services to suspend.</span></span> <span data-ttu-id="51c0b-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="51c0b-148">Wildcard characters are permitted.</span></span>

<span data-ttu-id="51c0b-149">De parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="51c0b-149">The parameter name is optional.</span></span> <span data-ttu-id="51c0b-150">U kunt de **naam** of de alias ervan **gebruiken, of** u kunt de parameter naam weglaten.</span><span class="sxs-lookup"><span data-stu-id="51c0b-150">You can use **Name** or its alias, **ServiceName** , or you can omit the parameter name.</span></span>

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

### <span data-ttu-id="51c0b-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="51c0b-151">-PassThru</span></span>

<span data-ttu-id="51c0b-152">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="51c0b-152">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="51c0b-153">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="51c0b-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="51c0b-154">-Confirm</span><span class="sxs-lookup"><span data-stu-id="51c0b-154">-Confirm</span></span>

<span data-ttu-id="51c0b-155">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="51c0b-155">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="51c0b-156">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="51c0b-156">-WhatIf</span></span>

<span data-ttu-id="51c0b-157">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="51c0b-157">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="51c0b-158">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="51c0b-158">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="51c0b-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51c0b-159">CommonParameters</span></span>

<span data-ttu-id="51c0b-160">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51c0b-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51c0b-161">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="51c0b-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51c0b-162">INVOER</span><span class="sxs-lookup"><span data-stu-id="51c0b-162">INPUTS</span></span>

### <span data-ttu-id="51c0b-163">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="51c0b-163">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="51c0b-164">U kunt een service object of een teken reeks die een service naam bevat door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51c0b-164">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="51c0b-165">UITVOER</span><span class="sxs-lookup"><span data-stu-id="51c0b-165">OUTPUTS</span></span>

### <span data-ttu-id="51c0b-166">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="51c0b-166">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="51c0b-167">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="51c0b-167">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="51c0b-168">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="51c0b-168">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="51c0b-169">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="51c0b-169">NOTES</span></span>

<span data-ttu-id="51c0b-170">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="51c0b-170">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="51c0b-171">`Suspend-Service` kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="51c0b-171">`Suspend-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="51c0b-172">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="51c0b-172">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="51c0b-173">`Suspend-Service` kan alleen services onderbreken die ondersteuning bieden voor onderbroken en hervat.</span><span class="sxs-lookup"><span data-stu-id="51c0b-173">`Suspend-Service` can suspend only services that support being suspended and resumed.</span></span> <span data-ttu-id="51c0b-174">Als u wilt bepalen of een bepaalde service kan worden onderbroken, gebruikt u de `Get-Service` cmdlet samen met de eigenschap **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="51c0b-174">To determine whether a particular service can be suspended, use the `Get-Service` cmdlet together with the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="51c0b-175">Bijvoorbeeld `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span><span class="sxs-lookup"><span data-stu-id="51c0b-175">For example, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span></span> <span data-ttu-id="51c0b-176">Als u wilt zoeken naar alle services op de computer die kunnen worden onderbroken, typt u `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` .</span><span class="sxs-lookup"><span data-stu-id="51c0b-176">To find all services on the computer that can be suspended, type `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}`.</span></span>
- <span data-ttu-id="51c0b-177">Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="51c0b-177">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="51c0b-178">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="51c0b-178">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="51c0b-179">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="51c0b-179">RELATED LINKS</span></span>

[<span data-ttu-id="51c0b-180">Get-Service</span><span class="sxs-lookup"><span data-stu-id="51c0b-180">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="51c0b-181">New-Service</span><span class="sxs-lookup"><span data-stu-id="51c0b-181">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="51c0b-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="51c0b-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="51c0b-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="51c0b-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="51c0b-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="51c0b-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="51c0b-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="51c0b-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="51c0b-186">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="51c0b-186">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="51c0b-187">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="51c0b-187">Remove-Service</span></span>](Remove-Service.md)
