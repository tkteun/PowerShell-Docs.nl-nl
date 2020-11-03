---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250792"
---
# <span data-ttu-id="e3457-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="e3457-103">Get-Service</span></span>

## <span data-ttu-id="e3457-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e3457-104">SYNOPSIS</span></span>
<span data-ttu-id="e3457-105">Hiermee worden de services op een lokale of externe computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-105">Gets the services on a local or remote computer.</span></span>

## <span data-ttu-id="e3457-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e3457-106">SYNTAX</span></span>

### <span data-ttu-id="e3457-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="e3457-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="e3457-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e3457-108">DisplayName</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="e3457-109">Input object</span><span class="sxs-lookup"><span data-stu-id="e3457-109">InputObject</span></span>

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="e3457-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e3457-110">DESCRIPTION</span></span>

<span data-ttu-id="e3457-111">Met de cmdlet **Get-service** worden objecten opgehaald die de services op een lokale computer of op een externe computer vertegenwoordigen, waaronder het uitvoeren en stoppen van services.</span><span class="sxs-lookup"><span data-stu-id="e3457-111">The **Get-Service** cmdlet gets objects that represent the services on a local computer or on a remote computer, including running and stopped services.</span></span>

<span data-ttu-id="e3457-112">U kunt deze cmdlet gebruiken om alleen bepaalde services op te halen door de service naam of de weergave naam van de services op te geven, of u kunt Service objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3457-112">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="e3457-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e3457-113">EXAMPLES</span></span>

### <span data-ttu-id="e3457-114">Voor beeld 1: alle services op de computer ophalen</span><span class="sxs-lookup"><span data-stu-id="e3457-114">Example 1: Get all services on the computer</span></span>

```powershell
Get-Service
```

<span data-ttu-id="e3457-115">Met deze opdracht worden alle services op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-115">This command gets all of the services on the computer.</span></span>
<span data-ttu-id="e3457-116">Het gedraagt zich alsof u hebt getypt `Get-Service *` .</span><span class="sxs-lookup"><span data-stu-id="e3457-116">It behaves as though you typed `Get-Service *`.</span></span>
<span data-ttu-id="e3457-117">In de standaard weergave worden de status, de service naam en de weergave naam van elke service weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e3457-117">The default display shows the status, service name, and display name of each service.</span></span>

### <span data-ttu-id="e3457-118">Voor beeld 2: services ophalen die beginnen met een zoek reeks</span><span class="sxs-lookup"><span data-stu-id="e3457-118">Example 2: Get services that begin with a search string</span></span>

```powershell
Get-Service "wmi*"
```

<span data-ttu-id="e3457-119">Met deze opdracht worden services opgehaald met service namen die beginnen met WMI (de acroniem voor Windows Management Instrumentation).</span><span class="sxs-lookup"><span data-stu-id="e3457-119">This command retrieves services with service names that begin with WMI (the acronym for Windows Management Instrumentation).</span></span>

### <span data-ttu-id="e3457-120">Voor beeld 3: services weer geven die een zoek reeks bevatten</span><span class="sxs-lookup"><span data-stu-id="e3457-120">Example 3: Display services that include a search string</span></span>

```powershell
Get-Service -Displayname "*network*"
```

<span data-ttu-id="e3457-121">Met deze opdracht worden de services weer gegeven met een weergave naam die het woord netwerk bevat.</span><span class="sxs-lookup"><span data-stu-id="e3457-121">This command displays services with a display name that includes the word network.</span></span>
<span data-ttu-id="e3457-122">Als u zoekt in de weergave naam, worden er netwerkgerelateerde services gevonden, zelfs wanneer de service naam geen ' net ' bevat, zoals xmlprov, de Network Provisioning Service.</span><span class="sxs-lookup"><span data-stu-id="e3457-122">Searching the display name finds network-related services even when the service name does not include "Net", such as xmlprov, the Network Provisioning Service.</span></span>

### <span data-ttu-id="e3457-123">Voor beeld 4: services ophalen die beginnen met een zoek reeks en een uitsluiting</span><span class="sxs-lookup"><span data-stu-id="e3457-123">Example 4: Get services that begin with a search string and an exclusion</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

<span data-ttu-id="e3457-124">Deze opdrachten krijgen alleen de services met service namen die beginnen met Win, met uitzonde ring van de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="e3457-124">These commands get only the services with service names that begin with win, except for the WinRM service.</span></span>

### <span data-ttu-id="e3457-125">Voor beeld 5: services weer geven die momenteel actief zijn</span><span class="sxs-lookup"><span data-stu-id="e3457-125">Example 5: Display services that are currently active</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="e3457-126">Met deze opdracht worden alleen de services weer gegeven die momenteel actief zijn.</span><span class="sxs-lookup"><span data-stu-id="e3457-126">This command displays only the services that are currently active.</span></span>
<span data-ttu-id="e3457-127">Er wordt gebruikgemaakt van de cmdlet **Get-service** om alle services op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="e3457-127">It uses the **Get-Service** cmdlet to get all of the services on the computer.</span></span>
<span data-ttu-id="e3457-128">De pijplijn operator (|) geeft de resultaten door aan de cmdlet Where-Object, waarmee alleen de services worden geselecteerd met een status eigenschap die gelijk is aan die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e3457-128">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects only the services with a Status property that equals Running.</span></span>

<span data-ttu-id="e3457-129">De status is slechts één eigenschap van service objecten.</span><span class="sxs-lookup"><span data-stu-id="e3457-129">Status is only one property of service objects.</span></span>
<span data-ttu-id="e3457-130">Als u alle eigenschappen wilt weer geven, typt u `Get-Service | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="e3457-130">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="e3457-131">Voor beeld 6: de services op een externe computer ophalen</span><span class="sxs-lookup"><span data-stu-id="e3457-131">Example 6: Get the services on a remote computer</span></span>

```powershell
Get-Service -ComputerName "Server02"
```

<span data-ttu-id="e3457-132">Met deze opdracht worden de services op de externe computer Server02 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-132">This command gets the services on the Server02 remote computer.</span></span>

<span data-ttu-id="e3457-133">Omdat de para meter *ComputerName* van **Get-service** geen gebruik maakt van Windows Power shell Remoting, kunt u deze para meter ook gebruiken als de computer niet is geconfigureerd voor externe toegang in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e3457-133">Because the *ComputerName* parameter of **Get-Service** does not use Windows PowerShell remoting, you can use this parameter even if the computer is not configured for remoting in Windows PowerShell.</span></span>

### <span data-ttu-id="e3457-134">Voor beeld 7: de services op de lokale computer weer geven die afhankelijke services hebben</span><span class="sxs-lookup"><span data-stu-id="e3457-134">Example 7: List the services on the local computer that have dependent services</span></span>

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

<span data-ttu-id="e3457-135">Met de eerste opdracht wordt de cmdlet **Get-service** gebruikt om de services op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="e3457-135">The first command uses the **Get-Service** cmdlet to get the services on the computer.</span></span>
<span data-ttu-id="e3457-136">Een pijplijn operator (|) verzendt de services naar de **where-object-** cmdlet, waarmee de services worden geselecteerd waarvan de eigenschap **DependentServices** niet null is.</span><span class="sxs-lookup"><span data-stu-id="e3457-136">A pipeline operator (|) sends the services to the **Where-Object** cmdlet, which selects the services whose **DependentServices** property is not null.</span></span>

<span data-ttu-id="e3457-137">Een andere pijplijn operator verzendt de resultaten naar de Format-List-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3457-137">Another pipeline operator sends the results to the Format-List cmdlet.</span></span>
<span data-ttu-id="e3457-138">De opdracht gebruikt de *eigenschaps* parameter voor het weer geven van de naam van de service, de naam van de afhankelijke services en een berekende eigenschap waarmee het aantal afhankelijke services wordt weer gegeven dat elke service heeft.</span><span class="sxs-lookup"><span data-stu-id="e3457-138">The command uses its *Property* parameter to display the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services that each service has.</span></span>

### <span data-ttu-id="e3457-139">Voor beeld 8: Services sorteren op eigenschaps waarde</span><span class="sxs-lookup"><span data-stu-id="e3457-139">Example 8: Sort services by property value</span></span>

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

<span data-ttu-id="e3457-140">Met deze opdracht wordt aangegeven dat wanneer u services in oplopende volg orde sorteert op de waarde van de eigenschap **status** , gestopt services worden weer gegeven voordat Services worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e3457-140">This command shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span>
<span data-ttu-id="e3457-141">Dit gebeurt omdat de waarde van status een opsomming is, waarbij gestopt de waarde 1 heeft en de waarde 4 heeft.</span><span class="sxs-lookup"><span data-stu-id="e3457-141">This happens because the value of Status is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span>

<span data-ttu-id="e3457-142">Als u eerst actieve services wilt weer geven, gebruikt u de para meter *Aflopend* van de cmdlet Sort-Object.</span><span class="sxs-lookup"><span data-stu-id="e3457-142">To list running services first, use the *Descending* parameter of the Sort-Object cmdlet.</span></span>

### <span data-ttu-id="e3457-143">Voor beeld 9: Services op meerdere computers ophalen</span><span class="sxs-lookup"><span data-stu-id="e3457-143">Example 9: Get services on multiple computers</span></span>

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

<span data-ttu-id="e3457-144">Met deze opdracht wordt de cmdlet **Get-service** gebruikt om een Get-Service WinRM-opdracht uit te voeren op twee externe computers en op de lokale computer (' localhost ').</span><span class="sxs-lookup"><span data-stu-id="e3457-144">This command uses the **Get-Service** cmdlet to run a Get-Service Winrm command on two remote computers and the local computer ("localhost").</span></span>

<span data-ttu-id="e3457-145">De opdracht wordt uitgevoerd op de externe computers en de resultaten worden geretourneerd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="e3457-145">The command runs on the remote computers, and the results are returned to the local computer.</span></span>
<span data-ttu-id="e3457-146">Een pijplijn operator (|) verzendt de resultaten naar de **indeling-tabel-** cmdlet, waarmee de services als tabel worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="e3457-146">A pipeline operator (|) sends the results to the **Format-Table** cmdlet, which formats the services as a table.</span></span>
<span data-ttu-id="e3457-147">De **notatie tabel** opdracht gebruikt de para meter *Property* om de eigenschappen op te geven die in de tabel worden weer gegeven, met inbegrip van de **MachineName** -eigenschap.</span><span class="sxs-lookup"><span data-stu-id="e3457-147">The **Format-Table** command uses the *Property* parameter to specify the properties displayed in the table, including the **MachineName** property.</span></span>

### <span data-ttu-id="e3457-148">Voor beeld 10: de afhankelijke services van een service ophalen</span><span class="sxs-lookup"><span data-stu-id="e3457-148">Example 10: Get the dependent services of a service</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

<span data-ttu-id="e3457-149">Met deze opdracht worden de services opgehaald die nodig zijn voor de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="e3457-149">This command gets the services that the WinRM service requires.</span></span>

<span data-ttu-id="e3457-150">De opdracht retourneert de waarde van de eigenschap **ServicesDependedOn** van de service.</span><span class="sxs-lookup"><span data-stu-id="e3457-150">The command returns the value of the **ServicesDependedOn** property of the service.</span></span>

### <span data-ttu-id="e3457-151">Voor beeld 11: een service ophalen via de pijplijn operator</span><span class="sxs-lookup"><span data-stu-id="e3457-151">Example 11: Get a service through the pipeline operator</span></span>

```powershell
"WinRM" | Get-Service
```

<span data-ttu-id="e3457-152">Met deze opdracht wordt de WinRM-service op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-152">This command gets the WinRM service on the local computer.</span></span>
<span data-ttu-id="e3457-153">Dit voor beeld laat zien dat u een teken reeks met een service naam (tussen aanhalings tekens) kunt plaatsen om **service te verkrijgen**.</span><span class="sxs-lookup"><span data-stu-id="e3457-153">This example shows that you can pipe a service name string (enclosed in quotation marks) to **Get-Service**.</span></span>

## <span data-ttu-id="e3457-154">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e3457-154">PARAMETERS</span></span>

### <span data-ttu-id="e3457-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e3457-155">-ComputerName</span></span>

<span data-ttu-id="e3457-156">Hiermee worden de services opgehaald die worden uitgevoerd op de opgegeven computers.</span><span class="sxs-lookup"><span data-stu-id="e3457-156">Gets the services running on the specified computers.</span></span>
<span data-ttu-id="e3457-157">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="e3457-157">The default is the local computer.</span></span>

<span data-ttu-id="e3457-158">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name (FQDN) van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="e3457-158">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="e3457-159">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.</span><span class="sxs-lookup"><span data-stu-id="e3457-159">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="e3457-160">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e3457-160">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="e3457-161">U kunt de para meter *ComputerName* van **Get-service gebruiken,** zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e3457-161">You can use the *ComputerName* parameter of **Get-Service** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e3457-162">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="e3457-162">-DependentServices</span></span>

<span data-ttu-id="e3457-163">Geeft aan dat met deze cmdlet alleen de services worden opgehaald die afhankelijk zijn van de opgegeven service.</span><span class="sxs-lookup"><span data-stu-id="e3457-163">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

<span data-ttu-id="e3457-164">Deze cmdlet haalt standaard alle services op.</span><span class="sxs-lookup"><span data-stu-id="e3457-164">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e3457-165">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="e3457-165">-DisplayName</span></span>

<span data-ttu-id="e3457-166">Hiermee geeft u als een teken reeks matrix de weergave namen op van de services die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-166">Specifies, as a string array, the display names of services to be retrieved.</span></span>
<span data-ttu-id="e3457-167">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e3457-167">Wildcards are permitted.</span></span>
<span data-ttu-id="e3457-168">Met deze cmdlet worden standaard alle services op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-168">By default, this cmdlet gets all services on the computer.</span></span>

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

### <span data-ttu-id="e3457-169">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="e3457-169">-Exclude</span></span>

<span data-ttu-id="e3457-170">Hiermee wordt een teken reeks matrix opgegeven, een service of services die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="e3457-170">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="e3457-171">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="e3457-171">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="e3457-172">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="e3457-172">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="e3457-173">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e3457-173">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e3457-174">-Include</span><span class="sxs-lookup"><span data-stu-id="e3457-174">-Include</span></span>

<span data-ttu-id="e3457-175">Hiermee wordt een teken reeks matrix opgegeven, een service of services die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="e3457-175">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="e3457-176">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="e3457-176">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="e3457-177">Voer een naam element of patroon in, zoals ' s \* '.</span><span class="sxs-lookup"><span data-stu-id="e3457-177">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="e3457-178">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e3457-178">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="e3457-179">-Input object</span><span class="sxs-lookup"><span data-stu-id="e3457-179">-InputObject</span></span>

<span data-ttu-id="e3457-180">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-180">Specifies **ServiceController** objects representing the services to be retrieved.</span></span>
<span data-ttu-id="e3457-181">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-181">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>
<span data-ttu-id="e3457-182">U kunt ook een service object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3457-182">You can also pipe a service object to this cmdlet.</span></span>

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

### <span data-ttu-id="e3457-183">-Name</span><span class="sxs-lookup"><span data-stu-id="e3457-183">-Name</span></span>

<span data-ttu-id="e3457-184">Hiermee geeft u de service namen op van de services die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-184">Specifies the service names of services to be retrieved.</span></span>
<span data-ttu-id="e3457-185">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e3457-185">Wildcards are permitted.</span></span>
<span data-ttu-id="e3457-186">Met deze cmdlet worden standaard alle services op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-186">By default, this cmdlet gets all of the services on the computer.</span></span>

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

### <span data-ttu-id="e3457-187">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="e3457-187">-RequiredServices</span></span>

<span data-ttu-id="e3457-188">Geeft aan dat met deze cmdlet alleen de services worden opgehaald die door deze service zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="e3457-188">Indicates that this cmdlet gets only the services that this service requires.</span></span>

<span data-ttu-id="e3457-189">Met deze para meter wordt de waarde van de eigenschap **ServicesDependedOn** van de service opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e3457-189">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>
<span data-ttu-id="e3457-190">Deze cmdlet haalt standaard alle services op.</span><span class="sxs-lookup"><span data-stu-id="e3457-190">By default, this cmdlet gets all services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e3457-191">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e3457-191">CommonParameters</span></span>

<span data-ttu-id="e3457-192">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e3457-192">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e3457-193">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e3457-193">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e3457-194">INVOER</span><span class="sxs-lookup"><span data-stu-id="e3457-194">INPUTS</span></span>

### <span data-ttu-id="e3457-195">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="e3457-195">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="e3457-196">U kunt een service object of een service naam door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3457-196">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="e3457-197">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e3457-197">OUTPUTS</span></span>

### <span data-ttu-id="e3457-198">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="e3457-198">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="e3457-199">Deze cmdlet retourneert objecten die de services op de computer vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="e3457-199">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="e3457-200">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e3457-200">NOTES</span></span>

<span data-ttu-id="e3457-201">U kunt ook verwijzen naar **Get-service** door de ingebouwde alias, ' GSV '.</span><span class="sxs-lookup"><span data-stu-id="e3457-201">You can also refer to **Get-Service** by its built-in alias, "gsv".</span></span> <span data-ttu-id="e3457-202">Zie about_Aliases voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e3457-202">For more information, see about_Aliases.</span></span>

<span data-ttu-id="e3457-203">Met deze cmdlet kunnen alleen services worden weer gegeven wanneer de huidige gebruiker gemachtigd is om deze te bekijken.</span><span class="sxs-lookup"><span data-stu-id="e3457-203">This cmdlet can display services only when the current user has permission to see them.</span></span>
<span data-ttu-id="e3457-204">Als met deze cmdlet geen services worden weer gegeven, bent u mogelijk niet gemachtigd om deze weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e3457-204">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="e3457-205">Als u de service naam en de weergave naam van elke service op uw systeem wilt zoeken, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="e3457-205">To find the service name and display name of each service on your system, type `Get-Service`.</span></span>
<span data-ttu-id="e3457-206">De service namen worden weer gegeven in de kolom naam en de weergave namen worden weer gegeven in de kolom DisplayName.</span><span class="sxs-lookup"><span data-stu-id="e3457-206">The service names appear in the Name column, and the display names appear in the DisplayName column.</span></span>

<span data-ttu-id="e3457-207">Wanneer u in oplopende volg orde sorteren op status waarde, worden de Services ' gestopt ' weer gegeven voor services die worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e3457-207">When you sort in ascending order by status value, "Stopped" services appear before "Running" services.</span></span>
<span data-ttu-id="e3457-208">De eigenschap status van een service is een opsommings waarde waarin de namen van de status waarden gehele getallen vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="e3457-208">The Status property of a service is an enumerated value in which the names of the statuses represent integer values.</span></span>
<span data-ttu-id="e3457-209">De sorteer bewerking is gebaseerd op de gehele waarde, niet de naam.</span><span class="sxs-lookup"><span data-stu-id="e3457-209">The sort is based on the integer value, not the name.</span></span>
<span data-ttu-id="e3457-210">' Running ' wordt weer gegeven vóór ' Stopped ' omdat ' Stopped ' de waarde ' 1 ' heeft en ' running ' de waarde ' 4 ' heeft.</span><span class="sxs-lookup"><span data-stu-id="e3457-210">"Running" appears before "Stopped" because "Stopped" has a value of "1", and "Running" has a value of "4".</span></span>

## <span data-ttu-id="e3457-211">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e3457-211">RELATED LINKS</span></span>

[<span data-ttu-id="e3457-212">New-Service</span><span class="sxs-lookup"><span data-stu-id="e3457-212">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="e3457-213">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="e3457-213">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="e3457-214">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="e3457-214">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="e3457-215">Set-Service</span><span class="sxs-lookup"><span data-stu-id="e3457-215">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="e3457-216">Start-Service</span><span class="sxs-lookup"><span data-stu-id="e3457-216">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="e3457-217">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="e3457-217">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="e3457-218">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="e3457-218">Suspend-Service</span></span>](Suspend-Service.md)
