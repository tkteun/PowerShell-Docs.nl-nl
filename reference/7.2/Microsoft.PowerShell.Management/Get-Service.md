---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: c27dac11cdd8ebbf1705ac3bba0c0aa5147d4fa8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705485"
---
# <span data-ttu-id="1530b-102">Get-Service</span><span class="sxs-lookup"><span data-stu-id="1530b-102">Get-Service</span></span>

## <span data-ttu-id="1530b-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1530b-103">SYNOPSIS</span></span>
<span data-ttu-id="1530b-104">Hiermee worden de services op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1530b-104">Gets the services on the computer.</span></span>

## <span data-ttu-id="1530b-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1530b-105">SYNTAX</span></span>

### <span data-ttu-id="1530b-106">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="1530b-106">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1530b-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1530b-107">DisplayName</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1530b-108">Input object</span><span class="sxs-lookup"><span data-stu-id="1530b-108">InputObject</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="1530b-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1530b-109">DESCRIPTION</span></span>

<span data-ttu-id="1530b-110">De `Get-Service` cmdlet haalt objecten op die de services op een computer vertegenwoordigen, waaronder het uitvoeren en stoppen van services.</span><span class="sxs-lookup"><span data-stu-id="1530b-110">The `Get-Service` cmdlet gets objects that represent the services on a computer, including running and stopped services.</span></span> <span data-ttu-id="1530b-111">Wanneer `Get-Service` wordt uitgevoerd zonder para meters, worden standaard alle services van de lokale computer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1530b-111">By default, when `Get-Service` is run without parameters, all the local computer's services are returned.</span></span>

<span data-ttu-id="1530b-112">U kunt deze cmdlet gebruiken om alleen bepaalde services op te halen door de service naam of de weergave naam van de services op te geven, of u kunt Service objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1530b-112">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="1530b-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1530b-113">EXAMPLES</span></span>

### <span data-ttu-id="1530b-114">Voor beeld 1: alle services op de computer ophalen</span><span class="sxs-lookup"><span data-stu-id="1530b-114">Example 1: Get all services on the computer</span></span>

<span data-ttu-id="1530b-115">In dit voor beeld worden alle services op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1530b-115">This example gets all of the services on the computer.</span></span> <span data-ttu-id="1530b-116">Het gedraagt zich alsof u hebt getypt `Get-Service *` .</span><span class="sxs-lookup"><span data-stu-id="1530b-116">It behaves as though you typed `Get-Service *`.</span></span> <span data-ttu-id="1530b-117">In de standaard weergave worden de status, de service naam en de weergave naam van elke service weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1530b-117">The default display shows the status, service name, and display name of each service.</span></span>

```powershell
Get-Service
```

### <span data-ttu-id="1530b-118">Voor beeld 2: services ophalen die beginnen met een zoek reeks</span><span class="sxs-lookup"><span data-stu-id="1530b-118">Example 2: Get services that begin with a search string</span></span>

<span data-ttu-id="1530b-119">In dit voor beeld worden services opgehaald met service namen die beginnen met WMI (Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="1530b-119">This example retrieves services with service names that begin with WMI (Windows Management Instrumentation).</span></span>

```powershell
Get-Service "wmi*"
```

### <span data-ttu-id="1530b-120">Voor beeld 3: services weer geven die een zoek reeks bevatten</span><span class="sxs-lookup"><span data-stu-id="1530b-120">Example 3: Display services that include a search string</span></span>

<span data-ttu-id="1530b-121">In dit voor beeld worden de services weer gegeven met een weergave naam die het woord netwerk bevat.</span><span class="sxs-lookup"><span data-stu-id="1530b-121">This example displays services with a display name that includes the word network.</span></span> <span data-ttu-id="1530b-122">Als u zoekt in de weergave naam, worden er netwerkgerelateerde services gevonden, zelfs wanneer de service naam geen netwerk bevat, zoals xmlprov, de Network Provisioning Service.</span><span class="sxs-lookup"><span data-stu-id="1530b-122">Searching the display name finds network-related services even when the service name doesn't include Net, such as xmlprov, the Network Provisioning Service.</span></span>

```powershell
Get-Service -Displayname "*network*"
```

### <span data-ttu-id="1530b-123">Voor beeld 4: services ophalen die beginnen met een zoek reeks en een uitsluiting</span><span class="sxs-lookup"><span data-stu-id="1530b-123">Example 4: Get services that begin with a search string and an exclusion</span></span>

<span data-ttu-id="1530b-124">In dit voor beeld worden alleen de services met service namen opgehaald die beginnen met **Win**, met uitzonde ring van de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="1530b-124">This example only gets the services with service names that begin with **win**, except for the WinRM service.</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### <span data-ttu-id="1530b-125">Voor beeld 5: services weer geven die momenteel actief zijn</span><span class="sxs-lookup"><span data-stu-id="1530b-125">Example 5: Display services that are currently active</span></span>

<span data-ttu-id="1530b-126">In dit voor beeld worden alleen de services weer gegeven met de status wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1530b-126">This example displays only the services with a status of Running.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="1530b-127">`Get-Service` Hiermee worden alle services op de computer opgehaald en worden de objecten van de pijp lijn omlaag verzonden.</span><span class="sxs-lookup"><span data-stu-id="1530b-127">`Get-Service` gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="1530b-128">De `Where-Object` cmdlet selecteert alleen de services met een **status** eigenschap die gelijk is aan die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1530b-128">The `Where-Object` cmdlet, selects only the services with a **Status** property that equals Running.</span></span>

<span data-ttu-id="1530b-129">De status is slechts één eigenschap van service objecten.</span><span class="sxs-lookup"><span data-stu-id="1530b-129">Status is only one property of service objects.</span></span> <span data-ttu-id="1530b-130">Als u alle eigenschappen wilt weer geven, typt u `Get-Service | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="1530b-130">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="1530b-131">Voor beeld 6: de services op de computer weer geven die afhankelijke services hebben</span><span class="sxs-lookup"><span data-stu-id="1530b-131">Example 6: List the services on the computer that have dependent services</span></span>

<span data-ttu-id="1530b-132">In dit voor beeld worden services met afhankelijke services opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1530b-132">This example gets services that have dependent services.</span></span>

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

<span data-ttu-id="1530b-133">De `Get-Service` cmdlet haalt alle services op de computer op en verzendt de objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="1530b-133">The `Get-Service` cmdlet gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="1530b-134">De `Where-Object` cmdlet selecteert de services waarvan de eigenschap **DependentServices** niet null is.</span><span class="sxs-lookup"><span data-stu-id="1530b-134">The `Where-Object` cmdlet selects the services whose **DependentServices** property isn't null.</span></span>

<span data-ttu-id="1530b-135">De resultaten worden vanuit de pijp lijn naar de `Format-List` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="1530b-135">The results are sent down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="1530b-136">De **eigenschap** para meter geeft de naam van de service, de naam van de afhankelijke services en een berekende eigenschap weer die het aantal afhankelijke services voor elke service weergeeft.</span><span class="sxs-lookup"><span data-stu-id="1530b-136">The **Property** parameter displays the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services for each service.</span></span>

### <span data-ttu-id="1530b-137">Voor beeld 7: Services sorteren op eigenschaps waarde</span><span class="sxs-lookup"><span data-stu-id="1530b-137">Example 7: Sort services by property value</span></span>

<span data-ttu-id="1530b-138">Dit voor beeld laat zien dat wanneer u services in oplopende volg orde sorteert op de waarde van de eigenschap **status** , gestopt services worden weer gegeven voordat Services worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1530b-138">This example shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span> <span data-ttu-id="1530b-139">De reden hiervoor is dat de waarde van **status** een opsomming is, waarbij gestopt de waarde 1 heeft en de waarde 4 heeft.</span><span class="sxs-lookup"><span data-stu-id="1530b-139">The reason is because the value of **Status** is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="1530b-140">Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1530b-140">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="1530b-141">Als u eerst actieve services wilt weer geven, gebruikt u de para meter **Aflopend** van de `Sort-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1530b-141">To list running services first, use the **Descending** parameter of the `Sort-Object` cmdlet.</span></span>

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

### <span data-ttu-id="1530b-142">Voor beeld 8: de afhankelijke services van een service ophalen</span><span class="sxs-lookup"><span data-stu-id="1530b-142">Example 8: Get the dependent services of a service</span></span>

<span data-ttu-id="1530b-143">In dit voor beeld worden de services opgehaald die voor de WinRM-service zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="1530b-143">This example gets the services that the WinRM service requires.</span></span> <span data-ttu-id="1530b-144">De waarde van de eigenschap **ServicesDependedOn** van de service wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1530b-144">The value of the service's **ServicesDependedOn** property is returned.</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

### <span data-ttu-id="1530b-145">Voor beeld 9: een service ophalen via de pijplijn operator</span><span class="sxs-lookup"><span data-stu-id="1530b-145">Example 9: Get a service through the pipeline operator</span></span>

<span data-ttu-id="1530b-146">In dit voor beeld wordt de WinRM-service op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1530b-146">This example gets the WinRM service on the local computer.</span></span> <span data-ttu-id="1530b-147">De service naam teken reeks tussen aanhalings tekens, wordt naar beneden verzonden naar de pijp lijn `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="1530b-147">The service name string, enclosed in quotation marks, is sent down the pipeline to `Get-Service`.</span></span>

```powershell
"WinRM" | Get-Service
```

## <span data-ttu-id="1530b-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1530b-148">PARAMETERS</span></span>

### <span data-ttu-id="1530b-149">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="1530b-149">-DependentServices</span></span>

<span data-ttu-id="1530b-150">Geeft aan dat met deze cmdlet alleen de services worden opgehaald die afhankelijk zijn van de opgegeven service.</span><span class="sxs-lookup"><span data-stu-id="1530b-150">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

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

### <span data-ttu-id="1530b-151">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="1530b-151">-DisplayName</span></span>

<span data-ttu-id="1530b-152">Hiermee geeft u als een teken reeks matrix de weergave namen op van de services die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1530b-152">Specifies, as a string array, the display names of services to be retrieved.</span></span> <span data-ttu-id="1530b-153">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1530b-153">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1530b-154">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="1530b-154">-Exclude</span></span>

<span data-ttu-id="1530b-155">Hiermee wordt een teken reeks matrix opgegeven, een service of services die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="1530b-155">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="1530b-156">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="1530b-156">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="1530b-157">Voer een naam element of patroon in, bijvoorbeeld `s*` .</span><span class="sxs-lookup"><span data-stu-id="1530b-157">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="1530b-158">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1530b-158">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1530b-159">-Include</span><span class="sxs-lookup"><span data-stu-id="1530b-159">-Include</span></span>

<span data-ttu-id="1530b-160">Hiermee wordt een teken reeks matrix opgegeven, een service of services die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="1530b-160">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span> <span data-ttu-id="1530b-161">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="1530b-161">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="1530b-162">Voer een naam element of patroon in, bijvoorbeeld `s*` .</span><span class="sxs-lookup"><span data-stu-id="1530b-162">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="1530b-163">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1530b-163">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1530b-164">-Input object</span><span class="sxs-lookup"><span data-stu-id="1530b-164">-InputObject</span></span>

<span data-ttu-id="1530b-165">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1530b-165">Specifies **ServiceController** objects representing the services to be retrieved.</span></span> <span data-ttu-id="1530b-166">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1530b-166">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="1530b-167">U kunt een service object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1530b-167">You can pipe a service object to this cmdlet.</span></span>

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

### <span data-ttu-id="1530b-168">-Name</span><span class="sxs-lookup"><span data-stu-id="1530b-168">-Name</span></span>

<span data-ttu-id="1530b-169">Hiermee geeft u de service namen op van de services die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1530b-169">Specifies the service names of services to be retrieved.</span></span> <span data-ttu-id="1530b-170">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1530b-170">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1530b-171">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="1530b-171">-RequiredServices</span></span>

<span data-ttu-id="1530b-172">Geeft aan dat met deze cmdlet alleen de services worden opgehaald die door deze service zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="1530b-172">Indicates that this cmdlet gets only the services that this service requires.</span></span> <span data-ttu-id="1530b-173">Met deze para meter wordt de waarde van de eigenschap **ServicesDependedOn** van de service opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1530b-173">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>

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

### <span data-ttu-id="1530b-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1530b-174">CommonParameters</span></span>

<span data-ttu-id="1530b-175">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1530b-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1530b-176">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1530b-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1530b-177">INVOER</span><span class="sxs-lookup"><span data-stu-id="1530b-177">INPUTS</span></span>

### <span data-ttu-id="1530b-178">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="1530b-178">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="1530b-179">U kunt een service object of een service naam door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1530b-179">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="1530b-180">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1530b-180">OUTPUTS</span></span>

### <span data-ttu-id="1530b-181">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="1530b-181">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="1530b-182">Deze cmdlet retourneert objecten die de services op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="1530b-182">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="1530b-183">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1530b-183">NOTES</span></span>

<span data-ttu-id="1530b-184">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="1530b-184">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="1530b-185">Vanaf Power shell 6,0 worden de volgende eigenschappen toegevoegd aan de **ServiceController** -objecten: **username**, **Description**, **DelayedAutoStart**, **BinaryPathName** en **opstart type** .</span><span class="sxs-lookup"><span data-stu-id="1530b-185">Beginning in PowerShell 6.0, the following properties are added to the **ServiceController** objects: **UserName**, **Description**, **DelayedAutoStart**, **BinaryPathName**, and **StartupType** .</span></span>

<span data-ttu-id="1530b-186">U kunt ook verwijzen naar `Get-Service` de ingebouwde alias `gsv` .</span><span class="sxs-lookup"><span data-stu-id="1530b-186">You can also refer to `Get-Service` by its built-in alias, `gsv`.</span></span> <span data-ttu-id="1530b-187">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1530b-187">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="1530b-188">Met deze cmdlet kunnen alleen services worden weer gegeven wanneer de huidige gebruiker gemachtigd is om deze te bekijken.</span><span class="sxs-lookup"><span data-stu-id="1530b-188">This cmdlet can display services only when the current user has permission to see them.</span></span> <span data-ttu-id="1530b-189">Als met deze cmdlet geen services worden weer gegeven, bent u mogelijk niet gemachtigd om deze weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1530b-189">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="1530b-190">Als u de service naam en de weergave naam van elke service op uw systeem wilt zoeken, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="1530b-190">To find the service name and display name of each service on your system, type `Get-Service`.</span></span> <span data-ttu-id="1530b-191">De service namen worden weer gegeven in de kolom naam en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="1530b-191">The service names appear in the Name column, and the display names appear in the **DisplayName** column.</span></span>

<span data-ttu-id="1530b-192">Wanneer u in oplopende volg orde sorteert op de waarde van de eigenschap **status** , worden de gestopte services weer gegeven voordat u Services uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1530b-192">When you sort in ascending order by the **Status** property's value, Stopped services appear before Running services.</span></span> <span data-ttu-id="1530b-193">De eigenschap **status** van de service is een opsommings waarde en de status namen vertegenwoordigen gehele waarden.</span><span class="sxs-lookup"><span data-stu-id="1530b-193">The service's **Status** property is an enumerated value and the status names represent integer values.</span></span> <span data-ttu-id="1530b-194">De sorteer volgorde is gebaseerd op de gehele waarde, niet de naam.</span><span class="sxs-lookup"><span data-stu-id="1530b-194">The sort order is based on the integer value, not the name.</span></span> <span data-ttu-id="1530b-195">Gestopt wordt weer gegeven voordat de actie wordt uitgevoerd, omdat de waarde is gestopt, en het uitvoeren van de waarde 4.</span><span class="sxs-lookup"><span data-stu-id="1530b-195">Stopped appears before because Running because Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="1530b-196">Zie [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1530b-196">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="1530b-197">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1530b-197">RELATED LINKS</span></span>

[<span data-ttu-id="1530b-198">New-Service</span><span class="sxs-lookup"><span data-stu-id="1530b-198">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="1530b-199">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="1530b-199">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="1530b-200">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="1530b-200">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="1530b-201">Set-Service</span><span class="sxs-lookup"><span data-stu-id="1530b-201">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="1530b-202">Start-Service</span><span class="sxs-lookup"><span data-stu-id="1530b-202">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="1530b-203">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="1530b-203">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="1530b-204">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="1530b-204">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="1530b-205">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="1530b-205">Remove-Service</span></span>](Remove-Service.md)
