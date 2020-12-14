---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: 0216c7fae722121ead1c8e9ba122fbc3f1713725
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705949"
---
# <span data-ttu-id="12cf2-102">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="12cf2-102">Stop-Service</span></span>

## <span data-ttu-id="12cf2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="12cf2-103">SYNOPSIS</span></span>
<span data-ttu-id="12cf2-104">Hiermee worden een of meer actieve services gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-104">Stops one or more running services.</span></span>

## <span data-ttu-id="12cf2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="12cf2-105">SYNTAX</span></span>

### <span data-ttu-id="12cf2-106">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="12cf2-106">InputObject (Default)</span></span>

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12cf2-107">Standaard</span><span class="sxs-lookup"><span data-stu-id="12cf2-107">Default</span></span>

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12cf2-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="12cf2-108">DisplayName</span></span>

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="12cf2-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="12cf2-109">DESCRIPTION</span></span>

<span data-ttu-id="12cf2-110">De `Stop-Service` cmdlet verzendt een Stop bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="12cf2-110">The `Stop-Service` cmdlet sends a stop message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="12cf2-111">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object door te geven dat de service vertegenwoordigt die u wilt stoppen.</span><span class="sxs-lookup"><span data-stu-id="12cf2-111">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the service that you want to stop.</span></span>

## <span data-ttu-id="12cf2-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="12cf2-112">EXAMPLES</span></span>

### <span data-ttu-id="12cf2-113">Voor beeld 1: een service op de lokale computer stoppen</span><span class="sxs-lookup"><span data-stu-id="12cf2-113">Example 1: Stop a service on the local computer</span></span>

```
PS C:\> Stop-Service -Name "sysmonlog"
```

<span data-ttu-id="12cf2-114">Met deze opdracht wordt de Performance Logs and Alerts-service (SysmonLog) op de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-114">This command stops the Performance Logs and Alerts (SysmonLog) service on the local computer.</span></span>

### <span data-ttu-id="12cf2-115">Voor beeld 2: een service stoppen met de weergave naam</span><span class="sxs-lookup"><span data-stu-id="12cf2-115">Example 2: Stop a service by using the display name</span></span>

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

<span data-ttu-id="12cf2-116">Met deze opdracht wordt de Telnet-service op de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-116">This command stops the Telnet service on the local computer.</span></span> <span data-ttu-id="12cf2-117">De opdracht wordt gebruikt `Get-Service` om een object op te halen dat de Telnet-service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-117">The command uses `Get-Service` to get an object that represents the Telnet service.</span></span> <span data-ttu-id="12cf2-118">De pijplijn operator ( `|` ) sluizen het object naar `Stop-Service` , waardoor de service wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-118">The pipeline operator (`|`) pipes the object to `Stop-Service`, which stops the service.</span></span>

### <span data-ttu-id="12cf2-119">Voor beeld 3: een service met afhankelijke services stoppen</span><span class="sxs-lookup"><span data-stu-id="12cf2-119">Example 3: Stop a service that has dependent services</span></span>

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

<span data-ttu-id="12cf2-120">In dit voor beeld wordt de IISAdmin-service op de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-120">This example stops the IISAdmin service on the local computer.</span></span> <span data-ttu-id="12cf2-121">Omdat het stoppen van deze service ook de services stopt die afhankelijk zijn van de IISAdmin-service, is het raadzaam om te beginnen `Stop-Service` met een opdracht met een lijst met de services die afhankelijk zijn van de IISADMIN-service.</span><span class="sxs-lookup"><span data-stu-id="12cf2-121">Because stopping this service also stops the services that depend on the IISAdmin service, it is best to precede `Stop-Service` with a command that lists the services that depend on the IISAdmin service.</span></span>

<span data-ttu-id="12cf2-122">De eerste opdracht geeft de services weer die afhankelijk zijn van IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="12cf2-122">The first command lists the services that depend on IISAdmin.</span></span> <span data-ttu-id="12cf2-123">Er wordt gebruikgemaakt van `Get-Service` om een object op te halen dat de IISADMIN-service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-123">It uses `Get-Service` to get an object that represents the IISAdmin service.</span></span> <span data-ttu-id="12cf2-124">De pijplijn operator ( `|` ) geeft het resultaat door aan de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="12cf2-124">The pipeline operator (`|`) passes the result to the `Format-List` cmdlet.</span></span> <span data-ttu-id="12cf2-125">De opdracht gebruikt de para meter **Property** van `Format-List` om alleen de eigenschappen **name** en **DependentServices** van de service weer te geven.</span><span class="sxs-lookup"><span data-stu-id="12cf2-125">The command uses the **Property** parameter of `Format-List` to list only the **Name** and **DependentServices** properties of the service.</span></span>

<span data-ttu-id="12cf2-126">Met de tweede opdracht wordt de IISAdmin-service gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-126">The second command stops the IISAdmin service.</span></span> <span data-ttu-id="12cf2-127">De para meter **Force** is vereist voor het stoppen van een service met afhankelijke services.</span><span class="sxs-lookup"><span data-stu-id="12cf2-127">The **Force** parameter is required to stop a service that has dependent services.</span></span> <span data-ttu-id="12cf2-128">De opdracht gebruikt de **confirm** -para meter om een bevestiging van de gebruiker aan te vragen voordat de service wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-128">The command uses the **Confirm** parameter to request confirmation from the user before it stops each service.</span></span>

## <span data-ttu-id="12cf2-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12cf2-129">PARAMETERS</span></span>

### <span data-ttu-id="12cf2-130">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="12cf2-130">-DisplayName</span></span>

<span data-ttu-id="12cf2-131">Hiermee geeft u de weergave namen op van de services die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-131">Specifies the display names of the services to stop.</span></span>
<span data-ttu-id="12cf2-132">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="12cf2-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="12cf2-133">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="12cf2-133">-Exclude</span></span>

<span data-ttu-id="12cf2-134">Hiermee geeft u de services die door deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="12cf2-134">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="12cf2-135">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="12cf2-135">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="12cf2-136">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="12cf2-136">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="12cf2-137">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="12cf2-137">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="12cf2-138">-Force</span><span class="sxs-lookup"><span data-stu-id="12cf2-138">-Force</span></span>

<span data-ttu-id="12cf2-139">Hiermee wordt de cmdlet gedwongen een service te stoppen, zelfs als die service afhankelijke services heeft.</span><span class="sxs-lookup"><span data-stu-id="12cf2-139">Forces the cmdlet to stop a service even if that service has dependent services.</span></span>

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

### <span data-ttu-id="12cf2-140">-Include</span><span class="sxs-lookup"><span data-stu-id="12cf2-140">-Include</span></span>

<span data-ttu-id="12cf2-141">Hiermee geeft u de services op die met deze cmdlet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-141">Specifies services that this cmdlet stops.</span></span> <span data-ttu-id="12cf2-142">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="12cf2-142">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="12cf2-143">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="12cf2-143">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="12cf2-144">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="12cf2-144">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="12cf2-145">-Input object</span><span class="sxs-lookup"><span data-stu-id="12cf2-145">-InputObject</span></span>

<span data-ttu-id="12cf2-146">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-146">Specifies **ServiceController** objects that represent the services to stop.</span></span> <span data-ttu-id="12cf2-147">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="12cf2-147">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="12cf2-148">-Name</span><span class="sxs-lookup"><span data-stu-id="12cf2-148">-Name</span></span>

<span data-ttu-id="12cf2-149">Hiermee geeft u de service namen op van de services die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-149">Specifies the service names of the services to stop.</span></span> <span data-ttu-id="12cf2-150">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="12cf2-150">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="12cf2-151">-Wait</span><span class="sxs-lookup"><span data-stu-id="12cf2-151">-NoWait</span></span>

<span data-ttu-id="12cf2-152">Geeft aan dat deze cmdlet de optie geen wait gebruikt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-152">Indicates that this cmdlet uses the no wait option.</span></span>

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

### <span data-ttu-id="12cf2-153">-PassThru</span><span class="sxs-lookup"><span data-stu-id="12cf2-153">-PassThru</span></span>

<span data-ttu-id="12cf2-154">Retourneert een object dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-154">Returns an object that represents the service.</span></span> <span data-ttu-id="12cf2-155">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="12cf2-155">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="12cf2-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="12cf2-156">-Confirm</span></span>

<span data-ttu-id="12cf2-157">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="12cf2-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="12cf2-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="12cf2-158">-WhatIf</span></span>

<span data-ttu-id="12cf2-159">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="12cf2-159">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="12cf2-160">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="12cf2-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="12cf2-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12cf2-161">CommonParameters</span></span>

<span data-ttu-id="12cf2-162">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12cf2-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12cf2-163">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12cf2-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12cf2-164">INVOER</span><span class="sxs-lookup"><span data-stu-id="12cf2-164">INPUTS</span></span>

### <span data-ttu-id="12cf2-165">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="12cf2-165">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="12cf2-166">U kunt een service object of een teken reeks die de naam van een service bevat, door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="12cf2-166">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="12cf2-167">UITVOER</span><span class="sxs-lookup"><span data-stu-id="12cf2-167">OUTPUTS</span></span>

### <span data-ttu-id="12cf2-168">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="12cf2-168">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="12cf2-169">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u de para meter **PassThru** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="12cf2-169">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you use the **PassThru** parameter.</span></span> <span data-ttu-id="12cf2-170">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="12cf2-170">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="12cf2-171">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="12cf2-171">NOTES</span></span>

<span data-ttu-id="12cf2-172">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="12cf2-172">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="12cf2-173">U kunt ook verwijzen naar `Stop-Service` de ingebouwde alias, **spsv**.</span><span class="sxs-lookup"><span data-stu-id="12cf2-173">You can also refer to `Stop-Service` by its built-in alias, **spsv**.</span></span> <span data-ttu-id="12cf2-174">Zie about_Aliases voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12cf2-174">For more information, see about_Aliases.</span></span>

<span data-ttu-id="12cf2-175">`Stop-Service` kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="12cf2-175">`Stop-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="12cf2-176">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="12cf2-176">If a command does not work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="12cf2-177">Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="12cf2-177">To find the service names and display names of the services on your system, type `Get-Service`.</span></span> <span data-ttu-id="12cf2-178">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="12cf2-178">The service names appear in the **Name** column and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="12cf2-179">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="12cf2-179">RELATED LINKS</span></span>

[<span data-ttu-id="12cf2-180">Get-Service</span><span class="sxs-lookup"><span data-stu-id="12cf2-180">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="12cf2-181">New-Service</span><span class="sxs-lookup"><span data-stu-id="12cf2-181">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="12cf2-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="12cf2-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="12cf2-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="12cf2-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="12cf2-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="12cf2-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="12cf2-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="12cf2-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="12cf2-186">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="12cf2-186">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="12cf2-187">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="12cf2-187">Remove-Service</span></span>](Remove-Service.md)
