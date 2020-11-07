---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 425b5e56286c22b6595954916d8aa66eec807d83
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345252"
---
# <span data-ttu-id="c7d7f-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="c7d7f-103">Get-Service</span></span>

## <span data-ttu-id="c7d7f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c7d7f-104">SYNOPSIS</span></span>
<span data-ttu-id="c7d7f-105">Hiermee worden de services op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-105">Gets the services on the computer.</span></span>

## <span data-ttu-id="c7d7f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c7d7f-106">SYNTAX</span></span>

### <span data-ttu-id="c7d7f-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="c7d7f-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="c7d7f-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c7d7f-108">DisplayName</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="c7d7f-109">Input object</span><span class="sxs-lookup"><span data-stu-id="c7d7f-109">InputObject</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="c7d7f-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c7d7f-110">DESCRIPTION</span></span>

<span data-ttu-id="c7d7f-111">De `Get-Service` cmdlet haalt objecten op die de services op een computer vertegenwoordigen, waaronder het uitvoeren en stoppen van services.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-111">The `Get-Service` cmdlet gets objects that represent the services on a computer, including running and stopped services.</span></span> <span data-ttu-id="c7d7f-112">Wanneer `Get-Service` wordt uitgevoerd zonder para meters, worden standaard alle services van de lokale computer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-112">By default, when `Get-Service` is run without parameters, all the local computer's services are returned.</span></span>

<span data-ttu-id="c7d7f-113">U kunt deze cmdlet gebruiken om alleen bepaalde services op te halen door de service naam of de weergave naam van de services op te geven, of u kunt Service objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-113">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="c7d7f-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c7d7f-114">EXAMPLES</span></span>

### <span data-ttu-id="c7d7f-115">Voor beeld 1: alle services op de computer ophalen</span><span class="sxs-lookup"><span data-stu-id="c7d7f-115">Example 1: Get all services on the computer</span></span>

<span data-ttu-id="c7d7f-116">In dit voor beeld worden alle services op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-116">This example gets all of the services on the computer.</span></span> <span data-ttu-id="c7d7f-117">Het gedraagt zich alsof u hebt getypt `Get-Service *` .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-117">It behaves as though you typed `Get-Service *`.</span></span> <span data-ttu-id="c7d7f-118">In de standaard weergave worden de status, de service naam en de weergave naam van elke service weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-118">The default display shows the status, service name, and display name of each service.</span></span>

```powershell
Get-Service
```

### <span data-ttu-id="c7d7f-119">Voor beeld 2: services ophalen die beginnen met een zoek reeks</span><span class="sxs-lookup"><span data-stu-id="c7d7f-119">Example 2: Get services that begin with a search string</span></span>

<span data-ttu-id="c7d7f-120">In dit voor beeld worden services opgehaald met service namen die beginnen met WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="c7d7f-120">This example retrieves services with service names that begin with WMI (Windows Management Instrumentation).</span></span>

```powershell
Get-Service "wmi*"
```

### <span data-ttu-id="c7d7f-121">Voor beeld 3: services weer geven die een zoek reeks bevatten</span><span class="sxs-lookup"><span data-stu-id="c7d7f-121">Example 3: Display services that include a search string</span></span>

<span data-ttu-id="c7d7f-122">In dit voor beeld worden de services weer gegeven met een weergave naam die het woord netwerk bevat.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-122">This example displays services with a display name that includes the word network.</span></span> <span data-ttu-id="c7d7f-123">Als u zoekt in de weergave naam, worden er netwerkgerelateerde services gevonden, zelfs wanneer de service naam geen netwerk bevat, zoals xmlprov, de Network Provisioning Service.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-123">Searching the display name finds network-related services even when the service name doesn't include Net, such as xmlprov, the Network Provisioning Service.</span></span>

```powershell
Get-Service -Displayname "*network*"
```

### <span data-ttu-id="c7d7f-124">Voor beeld 4: services ophalen die beginnen met een zoek reeks en een uitsluiting</span><span class="sxs-lookup"><span data-stu-id="c7d7f-124">Example 4: Get services that begin with a search string and an exclusion</span></span>

<span data-ttu-id="c7d7f-125">In dit voor beeld worden alleen de services met service namen opgehaald die beginnen met **Win** , met uitzonde ring van de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-125">This example only gets the services with service names that begin with **win** , except for the WinRM service.</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### <span data-ttu-id="c7d7f-126">Voor beeld 5: services weer geven die momenteel actief zijn</span><span class="sxs-lookup"><span data-stu-id="c7d7f-126">Example 5: Display services that are currently active</span></span>

<span data-ttu-id="c7d7f-127">In dit voor beeld worden alleen de services weer gegeven met de status wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-127">This example displays only the services with a status of Running.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="c7d7f-128">`Get-Service` Hiermee worden alle services op de computer opgehaald en worden de objecten van de pijp lijn omlaag verzonden.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-128">`Get-Service` gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="c7d7f-129">De `Where-Object` cmdlet selecteert alleen de services met een **status** eigenschap die gelijk is aan die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-129">The `Where-Object` cmdlet, selects only the services with a **Status** property that equals Running.</span></span>

<span data-ttu-id="c7d7f-130">De status is slechts één eigenschap van service objecten.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-130">Status is only one property of service objects.</span></span> <span data-ttu-id="c7d7f-131">Als u alle eigenschappen wilt weer geven, typt u `Get-Service | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-131">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="c7d7f-132">Voor beeld 6: de services op de computer weer geven die afhankelijke services hebben</span><span class="sxs-lookup"><span data-stu-id="c7d7f-132">Example 6: List the services on the computer that have dependent services</span></span>

<span data-ttu-id="c7d7f-133">In dit voor beeld worden services met afhankelijke services opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-133">This example gets services that have dependent services.</span></span>

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

<span data-ttu-id="c7d7f-134">De `Get-Service` cmdlet haalt alle services op de computer op en verzendt de objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-134">The `Get-Service` cmdlet gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="c7d7f-135">De `Where-Object` cmdlet selecteert de services waarvan de eigenschap **DependentServices** niet null is.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-135">The `Where-Object` cmdlet selects the services whose **DependentServices** property isn't null.</span></span>

<span data-ttu-id="c7d7f-136">De resultaten worden vanuit de pijp lijn naar de `Format-List` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-136">The results are sent down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="c7d7f-137">De **eigenschap** para meter geeft de naam van de service, de naam van de afhankelijke services en een berekende eigenschap weer die het aantal afhankelijke services voor elke service weergeeft.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-137">The **Property** parameter displays the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services for each service.</span></span>

### <span data-ttu-id="c7d7f-138">Voor beeld 7: Services sorteren op eigenschaps waarde</span><span class="sxs-lookup"><span data-stu-id="c7d7f-138">Example 7: Sort services by property value</span></span>

<span data-ttu-id="c7d7f-139">Dit voor beeld laat zien dat wanneer u services in oplopende volg orde sorteert op de waarde van de eigenschap **status** , gestopt services worden weer gegeven voordat Services worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-139">This example shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span> <span data-ttu-id="c7d7f-140">De reden hiervoor is dat de waarde van **status** een opsomming is, waarbij gestopt de waarde 1 heeft en de waarde 4 heeft.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-140">The reason is because the value of **Status** is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="c7d7f-141">Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-141">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="c7d7f-142">Als u eerst actieve services wilt weer geven, gebruikt u de para meter **Aflopend** van de `Sort-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-142">To list running services first, use the **Descending** parameter of the `Sort-Object` cmdlet.</span></span>

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

### <span data-ttu-id="c7d7f-143">Voor beeld 8: de afhankelijke services van een service ophalen</span><span class="sxs-lookup"><span data-stu-id="c7d7f-143">Example 8: Get the dependent services of a service</span></span>

<span data-ttu-id="c7d7f-144">In dit voor beeld worden de services opgehaald die voor de WinRM-service zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-144">This example gets the services that the WinRM service requires.</span></span> <span data-ttu-id="c7d7f-145">De waarde van de eigenschap **ServicesDependedOn** van de service wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-145">The value of the service's **ServicesDependedOn** property is returned.</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

### <span data-ttu-id="c7d7f-146">Voor beeld 9: een service ophalen via de pijplijn operator</span><span class="sxs-lookup"><span data-stu-id="c7d7f-146">Example 9: Get a service through the pipeline operator</span></span>

<span data-ttu-id="c7d7f-147">In dit voor beeld wordt de WinRM-service op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-147">This example gets the WinRM service on the local computer.</span></span> <span data-ttu-id="c7d7f-148">De service naam teken reeks tussen aanhalings tekens, wordt naar beneden verzonden naar de pijp lijn `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-148">The service name string, enclosed in quotation marks, is sent down the pipeline to `Get-Service`.</span></span>

```powershell
"WinRM" | Get-Service
```

## <span data-ttu-id="c7d7f-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c7d7f-149">PARAMETERS</span></span>

### <span data-ttu-id="c7d7f-150">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="c7d7f-150">-DependentServices</span></span>

<span data-ttu-id="c7d7f-151">Geeft aan dat met deze cmdlet alleen de services worden opgehaald die afhankelijk zijn van de opgegeven service.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-151">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c7d7f-152">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="c7d7f-152">-DisplayName</span></span>

<span data-ttu-id="c7d7f-153">Hiermee geeft u als een teken reeks matrix de weergave namen op van de services die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-153">Specifies, as a string array, the display names of services to be retrieved.</span></span> <span data-ttu-id="c7d7f-154">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="c7d7f-155">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="c7d7f-155">-Exclude</span></span>

<span data-ttu-id="c7d7f-156">Hiermee wordt een teken reeks matrix opgegeven, een service of services die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-156">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="c7d7f-157">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-157">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="c7d7f-158">Voer een naam element of patroon in, bijvoorbeeld `s*` .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-158">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="c7d7f-159">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-159">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="c7d7f-160">-Include</span><span class="sxs-lookup"><span data-stu-id="c7d7f-160">-Include</span></span>

<span data-ttu-id="c7d7f-161">Hiermee wordt een teken reeks matrix opgegeven, een service of services die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-161">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c7d7f-162">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-162">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="c7d7f-163">Voer een naam element of patroon in, bijvoorbeeld `s*` .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-163">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="c7d7f-164">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-164">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="c7d7f-165">-Input object</span><span class="sxs-lookup"><span data-stu-id="c7d7f-165">-InputObject</span></span>

<span data-ttu-id="c7d7f-166">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-166">Specifies **ServiceController** objects representing the services to be retrieved.</span></span> <span data-ttu-id="c7d7f-167">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-167">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="c7d7f-168">U kunt een service object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-168">You can pipe a service object to this cmdlet.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c7d7f-169">-Name</span><span class="sxs-lookup"><span data-stu-id="c7d7f-169">-Name</span></span>

<span data-ttu-id="c7d7f-170">Hiermee geeft u de service namen op van de services die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-170">Specifies the service names of services to be retrieved.</span></span> <span data-ttu-id="c7d7f-171">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-171">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="c7d7f-172">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="c7d7f-172">-RequiredServices</span></span>

<span data-ttu-id="c7d7f-173">Geeft aan dat met deze cmdlet alleen de services worden opgehaald die door deze service zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-173">Indicates that this cmdlet gets only the services that this service requires.</span></span> <span data-ttu-id="c7d7f-174">Met deze para meter wordt de waarde van de eigenschap **ServicesDependedOn** van de service opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-174">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c7d7f-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c7d7f-175">CommonParameters</span></span>

<span data-ttu-id="c7d7f-176">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c7d7f-177">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c7d7f-178">INVOER</span><span class="sxs-lookup"><span data-stu-id="c7d7f-178">INPUTS</span></span>

### <span data-ttu-id="c7d7f-179">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="c7d7f-179">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="c7d7f-180">U kunt een service object of een service naam door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-180">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="c7d7f-181">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c7d7f-181">OUTPUTS</span></span>

### <span data-ttu-id="c7d7f-182">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="c7d7f-182">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="c7d7f-183">Deze cmdlet retourneert objecten die de services op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-183">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="c7d7f-184">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c7d7f-184">NOTES</span></span>

<span data-ttu-id="c7d7f-185">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-185">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="c7d7f-186">Vanaf Power shell 6,0 worden de volgende eigenschappen toegevoegd aan de **ServiceController** -objecten: **username** , **Description** , **DelayedAutoStart** , **BinaryPathName** en **opstart type** .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-186">Beginning in PowerShell 6.0, the following properties are added to the **ServiceController** objects: **UserName** , **Description** , **DelayedAutoStart** , **BinaryPathName** , and **StartupType** .</span></span>

<span data-ttu-id="c7d7f-187">U kunt ook verwijzen naar `Get-Service` de ingebouwde alias `gsv` .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-187">You can also refer to `Get-Service` by its built-in alias, `gsv`.</span></span> <span data-ttu-id="c7d7f-188">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-188">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="c7d7f-189">Met deze cmdlet kunnen alleen services worden weer gegeven wanneer de huidige gebruiker gemachtigd is om deze te bekijken.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-189">This cmdlet can display services only when the current user has permission to see them.</span></span> <span data-ttu-id="c7d7f-190">Als met deze cmdlet geen services worden weer gegeven, bent u mogelijk niet gemachtigd om deze weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-190">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="c7d7f-191">Als u de service naam en de weergave naam van elke service op uw systeem wilt zoeken, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-191">To find the service name and display name of each service on your system, type `Get-Service`.</span></span> <span data-ttu-id="c7d7f-192">De service namen worden weer gegeven in de kolom naam en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="c7d7f-192">The service names appear in the Name column, and the display names appear in the **DisplayName** column.</span></span>

<span data-ttu-id="c7d7f-193">Wanneer u in oplopende volg orde sorteert op de waarde van de eigenschap **status** , worden de gestopte services weer gegeven voordat u Services uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-193">When you sort in ascending order by the **Status** property's value, Stopped services appear before Running services.</span></span> <span data-ttu-id="c7d7f-194">De eigenschap **status** van de service is een opsommings waarde en de status namen vertegenwoordigen gehele waarden.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-194">The service's **Status** property is an enumerated value and the status names represent integer values.</span></span> <span data-ttu-id="c7d7f-195">De sorteer volgorde is gebaseerd op de gehele waarde, niet de naam.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-195">The sort order is based on the integer value, not the name.</span></span> <span data-ttu-id="c7d7f-196">Gestopt wordt weer gegeven voordat de actie wordt uitgevoerd, omdat de waarde is gestopt, en het uitvoeren van de waarde 4.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-196">Stopped appears before because Running because Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="c7d7f-197">Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c7d7f-197">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="c7d7f-198">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c7d7f-198">RELATED LINKS</span></span>

[<span data-ttu-id="c7d7f-199">New-Service</span><span class="sxs-lookup"><span data-stu-id="c7d7f-199">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="c7d7f-200">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="c7d7f-200">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="c7d7f-201">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="c7d7f-201">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="c7d7f-202">Set-Service</span><span class="sxs-lookup"><span data-stu-id="c7d7f-202">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="c7d7f-203">Start-Service</span><span class="sxs-lookup"><span data-stu-id="c7d7f-203">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="c7d7f-204">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="c7d7f-204">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="c7d7f-205">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="c7d7f-205">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="c7d7f-206">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="c7d7f-206">Remove-Service</span></span>](Remove-Service.md)
