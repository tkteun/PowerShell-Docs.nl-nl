---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: fae0ac83c86bb6e1767bcc9b48ce492e8068139c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347564"
---
# <span data-ttu-id="72c72-103">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="72c72-103">Stop-Service</span></span>

## <span data-ttu-id="72c72-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="72c72-104">SYNOPSIS</span></span>
<span data-ttu-id="72c72-105">Hiermee worden een of meer actieve services gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-105">Stops one or more running services.</span></span>

## <span data-ttu-id="72c72-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="72c72-106">SYNTAX</span></span>

### <span data-ttu-id="72c72-107">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="72c72-107">InputObject (Default)</span></span>

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="72c72-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="72c72-108">Default</span></span>

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="72c72-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="72c72-109">DisplayName</span></span>

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="72c72-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="72c72-110">DESCRIPTION</span></span>

<span data-ttu-id="72c72-111">De `Stop-Service` cmdlet verzendt een Stop bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="72c72-111">The `Stop-Service` cmdlet sends a stop message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="72c72-112">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object door te geven dat de service vertegenwoordigt die u wilt stoppen.</span><span class="sxs-lookup"><span data-stu-id="72c72-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the service that you want to stop.</span></span>

## <span data-ttu-id="72c72-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="72c72-113">EXAMPLES</span></span>

### <span data-ttu-id="72c72-114">Voor beeld 1: een service op de lokale computer stoppen</span><span class="sxs-lookup"><span data-stu-id="72c72-114">Example 1: Stop a service on the local computer</span></span>

```
PS C:\> Stop-Service -Name "sysmonlog"
```

<span data-ttu-id="72c72-115">Met deze opdracht wordt de Performance Logs and Alerts-service (SysmonLog) op de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-115">This command stops the Performance Logs and Alerts (SysmonLog) service on the local computer.</span></span>

### <span data-ttu-id="72c72-116">Voor beeld 2: een service stoppen met de weergave naam</span><span class="sxs-lookup"><span data-stu-id="72c72-116">Example 2: Stop a service by using the display name</span></span>

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

<span data-ttu-id="72c72-117">Met deze opdracht wordt de Telnet-service op de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-117">This command stops the Telnet service on the local computer.</span></span> <span data-ttu-id="72c72-118">De opdracht wordt gebruikt `Get-Service` om een object op te halen dat de Telnet-service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="72c72-118">The command uses `Get-Service` to get an object that represents the Telnet service.</span></span> <span data-ttu-id="72c72-119">De pijplijn operator ( `|` ) sluizen het object naar `Stop-Service` , waardoor de service wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-119">The pipeline operator (`|`) pipes the object to `Stop-Service`, which stops the service.</span></span>

### <span data-ttu-id="72c72-120">Voor beeld 3: een service met afhankelijke services stoppen</span><span class="sxs-lookup"><span data-stu-id="72c72-120">Example 3: Stop a service that has dependent services</span></span>

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

<span data-ttu-id="72c72-121">In dit voor beeld wordt de IISAdmin-service op de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-121">This example stops the IISAdmin service on the local computer.</span></span> <span data-ttu-id="72c72-122">Omdat het stoppen van deze service ook de services stopt die afhankelijk zijn van de IISAdmin-service, is het raadzaam om te beginnen `Stop-Service` met een opdracht met een lijst met de services die afhankelijk zijn van de IISADMIN-service.</span><span class="sxs-lookup"><span data-stu-id="72c72-122">Because stopping this service also stops the services that depend on the IISAdmin service, it is best to precede `Stop-Service` with a command that lists the services that depend on the IISAdmin service.</span></span>

<span data-ttu-id="72c72-123">De eerste opdracht geeft de services weer die afhankelijk zijn van IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="72c72-123">The first command lists the services that depend on IISAdmin.</span></span> <span data-ttu-id="72c72-124">Er wordt gebruikgemaakt van `Get-Service` om een object op te halen dat de IISADMIN-service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="72c72-124">It uses `Get-Service` to get an object that represents the IISAdmin service.</span></span> <span data-ttu-id="72c72-125">De pijplijn operator ( `|` ) geeft het resultaat door aan de `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72c72-125">The pipeline operator (`|`) passes the result to the `Format-List` cmdlet.</span></span> <span data-ttu-id="72c72-126">De opdracht gebruikt de para meter **Property** van `Format-List` om alleen de eigenschappen **name** en **DependentServices** van de service weer te geven.</span><span class="sxs-lookup"><span data-stu-id="72c72-126">The command uses the **Property** parameter of `Format-List` to list only the **Name** and **DependentServices** properties of the service.</span></span>

<span data-ttu-id="72c72-127">Met de tweede opdracht wordt de IISAdmin-service gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-127">The second command stops the IISAdmin service.</span></span> <span data-ttu-id="72c72-128">De para meter **Force** is vereist voor het stoppen van een service met afhankelijke services.</span><span class="sxs-lookup"><span data-stu-id="72c72-128">The **Force** parameter is required to stop a service that has dependent services.</span></span> <span data-ttu-id="72c72-129">De opdracht gebruikt de **confirm** -para meter om een bevestiging van de gebruiker aan te vragen voordat de service wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-129">The command uses the **Confirm** parameter to request confirmation from the user before it stops each service.</span></span>

## <span data-ttu-id="72c72-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="72c72-130">PARAMETERS</span></span>

### <span data-ttu-id="72c72-131">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="72c72-131">-DisplayName</span></span>

<span data-ttu-id="72c72-132">Hiermee geeft u de weergave namen op van de services die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-132">Specifies the display names of the services to stop.</span></span>
<span data-ttu-id="72c72-133">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="72c72-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="72c72-134">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="72c72-134">-Exclude</span></span>

<span data-ttu-id="72c72-135">Hiermee geeft u de services die door deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="72c72-135">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="72c72-136">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="72c72-136">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="72c72-137">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="72c72-137">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="72c72-138">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="72c72-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="72c72-139">-Force</span><span class="sxs-lookup"><span data-stu-id="72c72-139">-Force</span></span>

<span data-ttu-id="72c72-140">Hiermee wordt de cmdlet gedwongen een service te stoppen, zelfs als die service afhankelijke services heeft.</span><span class="sxs-lookup"><span data-stu-id="72c72-140">Forces the cmdlet to stop a service even if that service has dependent services.</span></span>

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

### <span data-ttu-id="72c72-141">-Include</span><span class="sxs-lookup"><span data-stu-id="72c72-141">-Include</span></span>

<span data-ttu-id="72c72-142">Hiermee geeft u de services op die met deze cmdlet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-142">Specifies services that this cmdlet stops.</span></span> <span data-ttu-id="72c72-143">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="72c72-143">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="72c72-144">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="72c72-144">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="72c72-145">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="72c72-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="72c72-146">-Input object</span><span class="sxs-lookup"><span data-stu-id="72c72-146">-InputObject</span></span>

<span data-ttu-id="72c72-147">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-147">Specifies **ServiceController** objects that represent the services to stop.</span></span> <span data-ttu-id="72c72-148">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="72c72-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="72c72-149">-Name</span><span class="sxs-lookup"><span data-stu-id="72c72-149">-Name</span></span>

<span data-ttu-id="72c72-150">Hiermee geeft u de service namen op van de services die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="72c72-150">Specifies the service names of the services to stop.</span></span> <span data-ttu-id="72c72-151">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="72c72-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="72c72-152">-Wait</span><span class="sxs-lookup"><span data-stu-id="72c72-152">-NoWait</span></span>

<span data-ttu-id="72c72-153">Geeft aan dat deze cmdlet de optie geen wait gebruikt.</span><span class="sxs-lookup"><span data-stu-id="72c72-153">Indicates that this cmdlet uses the no wait option.</span></span>

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

### <span data-ttu-id="72c72-154">-PassThru</span><span class="sxs-lookup"><span data-stu-id="72c72-154">-PassThru</span></span>

<span data-ttu-id="72c72-155">Retourneert een object dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="72c72-155">Returns an object that represents the service.</span></span> <span data-ttu-id="72c72-156">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="72c72-156">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="72c72-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="72c72-157">-Confirm</span></span>

<span data-ttu-id="72c72-158">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="72c72-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="72c72-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="72c72-159">-WhatIf</span></span>

<span data-ttu-id="72c72-160">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="72c72-160">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="72c72-161">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="72c72-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="72c72-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="72c72-162">CommonParameters</span></span>

<span data-ttu-id="72c72-163">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="72c72-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="72c72-164">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72c72-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="72c72-165">INVOER</span><span class="sxs-lookup"><span data-stu-id="72c72-165">INPUTS</span></span>

### <span data-ttu-id="72c72-166">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="72c72-166">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="72c72-167">U kunt een service object of een teken reeks die de naam van een service bevat, door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72c72-167">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="72c72-168">UITVOER</span><span class="sxs-lookup"><span data-stu-id="72c72-168">OUTPUTS</span></span>

### <span data-ttu-id="72c72-169">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="72c72-169">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="72c72-170">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u de para meter **PassThru** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="72c72-170">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you use the **PassThru** parameter.</span></span> <span data-ttu-id="72c72-171">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="72c72-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="72c72-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="72c72-172">NOTES</span></span>

<span data-ttu-id="72c72-173">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="72c72-173">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="72c72-174">U kunt ook verwijzen naar `Stop-Service` de ingebouwde alias, **spsv**.</span><span class="sxs-lookup"><span data-stu-id="72c72-174">You can also refer to `Stop-Service` by its built-in alias, **spsv**.</span></span> <span data-ttu-id="72c72-175">Zie about_Aliases voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="72c72-175">For more information, see about_Aliases.</span></span>

<span data-ttu-id="72c72-176">`Stop-Service` kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="72c72-176">`Stop-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="72c72-177">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="72c72-177">If a command does not work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="72c72-178">Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="72c72-178">To find the service names and display names of the services on your system, type `Get-Service`.</span></span> <span data-ttu-id="72c72-179">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="72c72-179">The service names appear in the **Name** column and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="72c72-180">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="72c72-180">RELATED LINKS</span></span>

[<span data-ttu-id="72c72-181">Get-Service</span><span class="sxs-lookup"><span data-stu-id="72c72-181">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="72c72-182">New-Service</span><span class="sxs-lookup"><span data-stu-id="72c72-182">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="72c72-183">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="72c72-183">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="72c72-184">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="72c72-184">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="72c72-185">Set-Service</span><span class="sxs-lookup"><span data-stu-id="72c72-185">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="72c72-186">Start-Service</span><span class="sxs-lookup"><span data-stu-id="72c72-186">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="72c72-187">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="72c72-187">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="72c72-188">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="72c72-188">Remove-Service</span></span>](Remove-Service.md)
