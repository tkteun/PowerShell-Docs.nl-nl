---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: fac6369859c3f8e3181a9044d381d01c12fea062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250012"
---
# <span data-ttu-id="56d13-103">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="56d13-103">Stop-Service</span></span>

## <span data-ttu-id="56d13-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="56d13-104">SYNOPSIS</span></span>
<span data-ttu-id="56d13-105">Hiermee worden een of meer actieve services gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-105">Stops one or more running services.</span></span>

## <span data-ttu-id="56d13-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="56d13-106">SYNTAX</span></span>

### <span data-ttu-id="56d13-107">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="56d13-107">InputObject (Default)</span></span>

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="56d13-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="56d13-108">Default</span></span>

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="56d13-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="56d13-109">DisplayName</span></span>

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="56d13-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="56d13-110">DESCRIPTION</span></span>

<span data-ttu-id="56d13-111">De **Stop-Service-** cmdlet verzendt een Stop bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="56d13-111">The **Stop-Service** cmdlet sends a stop message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="56d13-112">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object door te geven dat de service vertegenwoordigt die u wilt stoppen.</span><span class="sxs-lookup"><span data-stu-id="56d13-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the service that you want to stop.</span></span>

## <span data-ttu-id="56d13-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="56d13-113">EXAMPLES</span></span>

### <span data-ttu-id="56d13-114">Voor beeld 1: een service op de lokale computer stoppen</span><span class="sxs-lookup"><span data-stu-id="56d13-114">Example 1: Stop a service on the local computer</span></span>

```
PS C:\> Stop-Service -Name "sysmonlog"
```

<span data-ttu-id="56d13-115">Met deze opdracht wordt de Performance Logs and Alerts-service (SysmonLog) op de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-115">This command stops the Performance Logs and Alerts (SysmonLog) service on the local computer.</span></span>

### <span data-ttu-id="56d13-116">Voor beeld 2: een service stoppen met de weergave naam</span><span class="sxs-lookup"><span data-stu-id="56d13-116">Example 2: Stop a service by using the display name</span></span>

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

<span data-ttu-id="56d13-117">Met deze opdracht wordt de Telnet-service op de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-117">This command stops the Telnet service on the local computer.</span></span>
<span data-ttu-id="56d13-118">De opdracht gebruikt **Get-service** om een object op te halen dat de Telnet-service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="56d13-118">The command uses **Get-Service** to get an object that represents the Telnet service.</span></span>
<span data-ttu-id="56d13-119">De pijplijn operator (|) sluizen het object om te **stoppen-service** , waardoor de service wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-119">The pipeline operator (|) pipes the object to **Stop-Service** , which stops the service.</span></span>

### <span data-ttu-id="56d13-120">Voor beeld 3: een service met afhankelijke services stoppen</span><span class="sxs-lookup"><span data-stu-id="56d13-120">Example 3: Stop a service that has dependent services</span></span>

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

<span data-ttu-id="56d13-121">In dit voor beeld wordt de IISAdmin-service op de lokale computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-121">This example stops the IISAdmin service on the local computer.</span></span>
<span data-ttu-id="56d13-122">Omdat het stoppen van deze service ook de services stopt die afhankelijk zijn van de IISAdmin-service, is het raadzaam om de service te **stoppen** met een opdracht met een lijst met de services die afhankelijk zijn van de IISADMIN-service.</span><span class="sxs-lookup"><span data-stu-id="56d13-122">Because stopping this service also stops the services that depend on the IISAdmin service, it is best to precede **Stop-Service** with a command that lists the services that depend on the IISAdmin service.</span></span>

<span data-ttu-id="56d13-123">De eerste opdracht geeft de services weer die afhankelijk zijn van IISAdmin.</span><span class="sxs-lookup"><span data-stu-id="56d13-123">The first command lists the services that depend on IISAdmin.</span></span>
<span data-ttu-id="56d13-124">Er wordt **Get-service** gebruikt om een object op te halen dat de IISADMIN-service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="56d13-124">It uses **Get-Service** to get an object that represents the IISAdmin service.</span></span>
<span data-ttu-id="56d13-125">De pijplijn operator (|) geeft het resultaat door aan de cmdlet Format-List.</span><span class="sxs-lookup"><span data-stu-id="56d13-125">The pipeline operator (|) passes the result to the Format-List cmdlet.</span></span>
<span data-ttu-id="56d13-126">De opdracht gebruikt de *eigenschaps* parameter van de **notatie lijst** om alleen de eigenschappen **name** en **DependentServices** van de service weer te geven.</span><span class="sxs-lookup"><span data-stu-id="56d13-126">The command uses the *Property* parameter of **Format-List** to list only the **Name** and **DependentServices** properties of the service.</span></span>

<span data-ttu-id="56d13-127">Met de tweede opdracht wordt de IISAdmin-service gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-127">The second command stops the IISAdmin service.</span></span>
<span data-ttu-id="56d13-128">De para meter *Force* is vereist voor het stoppen van een service met afhankelijke services.</span><span class="sxs-lookup"><span data-stu-id="56d13-128">The *Force* parameter is required to stop a service that has dependent services.</span></span>
<span data-ttu-id="56d13-129">De opdracht gebruikt de *confirm* -para meter om een bevestiging van de gebruiker aan te vragen voordat de service wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-129">The command uses the *Confirm* parameter to request confirmation from the user before it stops each service.</span></span>

## <span data-ttu-id="56d13-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="56d13-130">PARAMETERS</span></span>

### <span data-ttu-id="56d13-131">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="56d13-131">-DisplayName</span></span>

<span data-ttu-id="56d13-132">Hiermee geeft u de weergave namen op van de services die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-132">Specifies the display names of the services to stop.</span></span>
<span data-ttu-id="56d13-133">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="56d13-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="56d13-134">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="56d13-134">-Exclude</span></span>

<span data-ttu-id="56d13-135">Hiermee geeft u de services die door deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="56d13-135">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="56d13-136">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="56d13-136">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="56d13-137">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="56d13-137">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="56d13-138">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="56d13-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="56d13-139">-Force</span><span class="sxs-lookup"><span data-stu-id="56d13-139">-Force</span></span>

<span data-ttu-id="56d13-140">Hiermee wordt de cmdlet gedwongen een service te stoppen, zelfs als die service afhankelijke services heeft.</span><span class="sxs-lookup"><span data-stu-id="56d13-140">Forces the cmdlet to stop a service even if that service has dependent services.</span></span>

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

### <span data-ttu-id="56d13-141">-Include</span><span class="sxs-lookup"><span data-stu-id="56d13-141">-Include</span></span>

<span data-ttu-id="56d13-142">Hiermee geeft u de services op die met deze cmdlet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-142">Specifies services that this cmdlet stops.</span></span>
<span data-ttu-id="56d13-143">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="56d13-143">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="56d13-144">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="56d13-144">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="56d13-145">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="56d13-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="56d13-146">-Input object</span><span class="sxs-lookup"><span data-stu-id="56d13-146">-InputObject</span></span>

<span data-ttu-id="56d13-147">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-147">Specifies **ServiceController** objects that represent the services to stop.</span></span>
<span data-ttu-id="56d13-148">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="56d13-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="56d13-149">-Name</span><span class="sxs-lookup"><span data-stu-id="56d13-149">-Name</span></span>

<span data-ttu-id="56d13-150">Hiermee geeft u de service namen op van de services die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="56d13-150">Specifies the service names of the services to stop.</span></span>
<span data-ttu-id="56d13-151">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="56d13-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="56d13-152">-Wait</span><span class="sxs-lookup"><span data-stu-id="56d13-152">-NoWait</span></span>

<span data-ttu-id="56d13-153">Geeft aan dat deze cmdlet de optie geen wait gebruikt.</span><span class="sxs-lookup"><span data-stu-id="56d13-153">Indicates that this cmdlet uses the no wait option.</span></span>

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

### <span data-ttu-id="56d13-154">-PassThru</span><span class="sxs-lookup"><span data-stu-id="56d13-154">-PassThru</span></span>

<span data-ttu-id="56d13-155">Retourneert een object dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="56d13-155">Returns an object that represents the service.</span></span>
<span data-ttu-id="56d13-156">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="56d13-156">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="56d13-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="56d13-157">-Confirm</span></span>

<span data-ttu-id="56d13-158">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="56d13-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="56d13-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="56d13-159">-WhatIf</span></span>

<span data-ttu-id="56d13-160">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="56d13-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="56d13-161">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="56d13-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="56d13-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56d13-162">CommonParameters</span></span>

<span data-ttu-id="56d13-163">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="56d13-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56d13-164">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="56d13-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56d13-165">INVOER</span><span class="sxs-lookup"><span data-stu-id="56d13-165">INPUTS</span></span>

### <span data-ttu-id="56d13-166">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="56d13-166">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="56d13-167">U kunt een service object of een teken reeks die de naam van een service bevat, door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="56d13-167">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="56d13-168">UITVOER</span><span class="sxs-lookup"><span data-stu-id="56d13-168">OUTPUTS</span></span>

### <span data-ttu-id="56d13-169">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="56d13-169">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="56d13-170">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u de para meter *PassThru* gebruikt.</span><span class="sxs-lookup"><span data-stu-id="56d13-170">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you use the *PassThru* parameter.</span></span>
<span data-ttu-id="56d13-171">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="56d13-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="56d13-172">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="56d13-172">NOTES</span></span>

* <span data-ttu-id="56d13-173">U kunt ook verwijzen naar **Stop-Service** door de ingebouwde alias, **spsv**.</span><span class="sxs-lookup"><span data-stu-id="56d13-173">You can also refer to **Stop-Service** by its built-in alias, **spsv**.</span></span> <span data-ttu-id="56d13-174">Zie about_Aliases voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="56d13-174">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="56d13-175">**Stop-Service** kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="56d13-175">**Stop-Service** can control services only when the current user has permission to do this.</span></span>
<span data-ttu-id="56d13-176">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="56d13-176">If a command does not work correctly, you might not have the required permissions.</span></span>

  <span data-ttu-id="56d13-177">Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="56d13-177">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
<span data-ttu-id="56d13-178">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="56d13-178">The service names appear in the **Name** column and the display names appear in the **DisplayName** column.</span></span>

*

## <span data-ttu-id="56d13-179">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="56d13-179">RELATED LINKS</span></span>

[<span data-ttu-id="56d13-180">Get-Service</span><span class="sxs-lookup"><span data-stu-id="56d13-180">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="56d13-181">New-Service</span><span class="sxs-lookup"><span data-stu-id="56d13-181">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="56d13-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="56d13-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="56d13-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="56d13-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="56d13-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="56d13-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="56d13-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="56d13-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="56d13-186">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="56d13-186">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="56d13-187">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="56d13-187">Remove-Service</span></span>](Remove-Service.md)
