---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 6e9fd5dd7a5736ef95976cb5195dd1d210d81651
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250011"
---
# <span data-ttu-id="e64cd-103">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="e64cd-103">Suspend-Service</span></span>

## <span data-ttu-id="e64cd-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e64cd-104">SYNOPSIS</span></span>
<span data-ttu-id="e64cd-105">Hiermee worden een of meer actieve services onderbroken (onderbroken).</span><span class="sxs-lookup"><span data-stu-id="e64cd-105">Suspends (pauses) one or more running services.</span></span>

## <span data-ttu-id="e64cd-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e64cd-106">SYNTAX</span></span>

### <span data-ttu-id="e64cd-107">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="e64cd-107">InputObject (Default)</span></span>

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e64cd-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="e64cd-108">Default</span></span>

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="e64cd-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e64cd-109">DisplayName</span></span>

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e64cd-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e64cd-110">DESCRIPTION</span></span>

<span data-ttu-id="e64cd-111">De cmdlet **suspend-service** stuurt een suspend-bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="e64cd-111">The **Suspend-Service** cmdlet sends a suspend message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="e64cd-112">Tijdens de onderbreking wordt de service nog steeds uitgevoerd, maar de actie wordt gestopt totdat deze wordt hervat, bijvoorbeeld door de usingthe Resume-Service-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e64cd-112">While suspended, the service is still running, but its action is stopped until resumed, such as by usingthe Resume-Service cmdlet.</span></span>
<span data-ttu-id="e64cd-113">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter *input object* gebruiken om een service object door te geven dat staat voor de services die u wilt onderbreken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-113">You can specify the services by their service names or display names, or you can use the *InputObject* parameter to pass a service object that represents the services that you want to suspend.</span></span>

## <span data-ttu-id="e64cd-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e64cd-114">EXAMPLES</span></span>

### <span data-ttu-id="e64cd-115">Voor beeld 1: een service opschorten</span><span class="sxs-lookup"><span data-stu-id="e64cd-115">Example 1: Suspend a service</span></span>

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

<span data-ttu-id="e64cd-116">Met deze opdracht wordt de service Telnet-service (TlntSvr) op de lokale computer onderbroken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-116">This command suspends the Telnet service (Tlntsvr) service on the local computer.</span></span>

### <span data-ttu-id="e64cd-117">Voor beeld 2: weer geven wat er gebeurt als u services uitbreekt</span><span class="sxs-lookup"><span data-stu-id="e64cd-117">Example 2: Display what would happen if you suspend services</span></span>

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

<span data-ttu-id="e64cd-118">Met deze opdracht wordt aangegeven wat er gebeurt als u de services met een service naam die begint met LANMAN hebt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-118">This command tells what would happen if you suspended the services that have a service name that starts with lanman.</span></span>
<span data-ttu-id="e64cd-119">Als u de services wilt onderbreken, voert u de opdracht opnieuw uit zonder de para meter *WhatIf* .</span><span class="sxs-lookup"><span data-stu-id="e64cd-119">To suspend the services, rerun the command without the *WhatIf* parameter.</span></span>

### <span data-ttu-id="e64cd-120">Voor beeld 3: een service ophalen en opschorten</span><span class="sxs-lookup"><span data-stu-id="e64cd-120">Example 3: Get and suspend a service</span></span>

```
PS C:\> Get-Service schedule | Suspend-Service
```

<span data-ttu-id="e64cd-121">Met deze opdracht wordt de cmdlet **Get-service** gebruikt om een object op te halen dat de taak planner-service (Schedule) op de computer vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="e64cd-121">This command uses the **Get-Service** cmdlet to get an object that represents the Task Scheduler (Schedule) service on the computer.</span></span>
<span data-ttu-id="e64cd-122">De pijplijn operator (|) geeft het resultaat door aan **suspend-service** , waardoor de service wordt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-122">The pipeline operator (|) passes the result to **Suspend-Service** , which suspends the service.</span></span>

### <span data-ttu-id="e64cd-123">Voor beeld 4: alle services onderbreken die kunnen worden onderbroken</span><span class="sxs-lookup"><span data-stu-id="e64cd-123">Example 4: Suspend all services that can be suspended</span></span>

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

<span data-ttu-id="e64cd-124">Met deze opdracht worden alle services op de computer opgeschort die kunnen worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-124">This command suspends all of the services on the computer that can be suspended.</span></span>
<span data-ttu-id="e64cd-125">Er wordt **Get-service** gebruikt om objecten op te halen die de services op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="e64cd-125">It uses **Get-Service** to get objects that represent the services on the computer.</span></span>
<span data-ttu-id="e64cd-126">De pijplijn operator geeft de resultaten door aan de cmdlet Where-Object, waarmee alleen de services worden geselecteerd met de waarde $True voor de eigenschap **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="e64cd-126">The pipeline operator passes the results to the Where-Object cmdlet, which selects only the services that have a value of $True for the **CanPauseAndContinue** property.</span></span>
<span data-ttu-id="e64cd-127">Een andere pijplijn operator geeft de resultaten door aan **suspend-service**.</span><span class="sxs-lookup"><span data-stu-id="e64cd-127">Another pipeline operator passes the results to **Suspend-Service**.</span></span>
<span data-ttu-id="e64cd-128">De *bevestigings* parameter vraagt u om bevestiging voordat alle services worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-128">The *Confirm* parameter prompts you for confirmation before suspending each of the services.</span></span>

## <span data-ttu-id="e64cd-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e64cd-129">PARAMETERS</span></span>

### <span data-ttu-id="e64cd-130">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="e64cd-130">-DisplayName</span></span>

<span data-ttu-id="e64cd-131">Hiermee geeft u de weergave namen op van de services die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-131">Specifies the display names of the services to be suspended.</span></span>
<span data-ttu-id="e64cd-132">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e64cd-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e64cd-133">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="e64cd-133">-Exclude</span></span>

<span data-ttu-id="e64cd-134">Hiermee geeft u services op die van de opgegeven services worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="e64cd-134">Specifies services to omit from the specified services.</span></span>
<span data-ttu-id="e64cd-135">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="e64cd-135">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="e64cd-136">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="e64cd-136">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="e64cd-137">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e64cd-137">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e64cd-138">-Include</span><span class="sxs-lookup"><span data-stu-id="e64cd-138">-Include</span></span>

<span data-ttu-id="e64cd-139">Hiermee worden de services opgegeven die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-139">Specifies services to suspend.</span></span>
<span data-ttu-id="e64cd-140">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="e64cd-140">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="e64cd-141">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="e64cd-141">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="e64cd-142">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e64cd-142">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e64cd-143">-Input object</span><span class="sxs-lookup"><span data-stu-id="e64cd-143">-InputObject</span></span>

<span data-ttu-id="e64cd-144">Hiermee geeft u **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-144">Specifies **ServiceController** objects that represent the services to suspend.</span></span>
<span data-ttu-id="e64cd-145">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e64cd-145">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="e64cd-146">-Name</span><span class="sxs-lookup"><span data-stu-id="e64cd-146">-Name</span></span>

<span data-ttu-id="e64cd-147">Hiermee geeft u de service namen op van de services die moeten worden onderbroken.</span><span class="sxs-lookup"><span data-stu-id="e64cd-147">Specifies the service names of the services to suspend.</span></span>
<span data-ttu-id="e64cd-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e64cd-148">Wildcard characters are permitted.</span></span>

<span data-ttu-id="e64cd-149">De parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="e64cd-149">The parameter name is optional.</span></span>
<span data-ttu-id="e64cd-150">U kunt de *naam* of de alias ervan *gebruiken, of* u kunt de parameter naam weglaten.</span><span class="sxs-lookup"><span data-stu-id="e64cd-150">You can use *Name* or its alias, *ServiceName* , or you can omit the parameter name.</span></span>

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

### <span data-ttu-id="e64cd-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e64cd-151">-PassThru</span></span>

<span data-ttu-id="e64cd-152">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="e64cd-152">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="e64cd-153">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e64cd-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e64cd-154">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e64cd-154">-Confirm</span></span>

<span data-ttu-id="e64cd-155">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e64cd-155">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e64cd-156">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e64cd-156">-WhatIf</span></span>

<span data-ttu-id="e64cd-157">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e64cd-157">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e64cd-158">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e64cd-158">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e64cd-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e64cd-159">CommonParameters</span></span>

<span data-ttu-id="e64cd-160">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e64cd-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e64cd-161">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e64cd-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e64cd-162">INVOER</span><span class="sxs-lookup"><span data-stu-id="e64cd-162">INPUTS</span></span>

### <span data-ttu-id="e64cd-163">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="e64cd-163">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="e64cd-164">U kunt een service object of een teken reeks die een service naam bevat door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e64cd-164">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="e64cd-165">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e64cd-165">OUTPUTS</span></span>

### <span data-ttu-id="e64cd-166">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="e64cd-166">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="e64cd-167">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u de para meter *PassThru* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="e64cd-167">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="e64cd-168">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e64cd-168">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e64cd-169">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e64cd-169">NOTES</span></span>

* <span data-ttu-id="e64cd-170">**Suspend-service** kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e64cd-170">**Suspend-Service** can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="e64cd-171">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="e64cd-171">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="e64cd-172">**Suspend-service** kan alleen services opschorten die ondersteuning bieden voor onderbroken en hervat.</span><span class="sxs-lookup"><span data-stu-id="e64cd-172">**Suspend-Service** can suspend only services that support being suspended and resumed.</span></span> <span data-ttu-id="e64cd-173">Als u wilt bepalen of een bepaalde service kan worden onderbroken, gebruikt u de Get-Service cmdlet samen met de eigenschap **CanPauseAndContinue** .</span><span class="sxs-lookup"><span data-stu-id="e64cd-173">To determine whether a particular service can be suspended, use the Get-Service cmdlet together with the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="e64cd-174">Bijvoorbeeld `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span><span class="sxs-lookup"><span data-stu-id="e64cd-174">For example, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span></span> <span data-ttu-id="e64cd-175">Als u wilt zoeken naar alle services op de computer die kunnen worden onderbroken, typt u `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` .</span><span class="sxs-lookup"><span data-stu-id="e64cd-175">To find all services on the computer that can be suspended, type `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}`.</span></span>
* <span data-ttu-id="e64cd-176">Typ **Get-service** om de service namen te vinden en de namen van de services op uw systeem weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e64cd-176">To find the service names and display names of the services on your system, type **Get-Service**.</span></span> <span data-ttu-id="e64cd-177">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="e64cd-177">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="e64cd-178">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e64cd-178">RELATED LINKS</span></span>

[<span data-ttu-id="e64cd-179">Get-Service</span><span class="sxs-lookup"><span data-stu-id="e64cd-179">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="e64cd-180">New-Service</span><span class="sxs-lookup"><span data-stu-id="e64cd-180">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="e64cd-181">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="e64cd-181">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="e64cd-182">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="e64cd-182">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="e64cd-183">Set-Service</span><span class="sxs-lookup"><span data-stu-id="e64cd-183">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="e64cd-184">Start-Service</span><span class="sxs-lookup"><span data-stu-id="e64cd-184">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="e64cd-185">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="e64cd-185">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="e64cd-186">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="e64cd-186">Remove-Service</span></span>](Remove-Service.md)
