---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: df4fda68508e21700235d2b772c6dd43c8e1fe1e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250547"
---
# <span data-ttu-id="a9453-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="a9453-103">Set-Service</span></span>

## <span data-ttu-id="a9453-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a9453-104">SYNOPSIS</span></span>
<span data-ttu-id="a9453-105">Hiermee wordt een service gestart, gestopt en onderbroken, en worden de eigenschappen ervan gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a9453-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="a9453-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a9453-106">SYNTAX</span></span>

### <span data-ttu-id="a9453-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="a9453-107">Name (Default)</span></span>

```
Set-Service [-ComputerName <String[]>] [-Name] <String> [-DisplayName <String>]
 [-Description <String>] [-StartupType <ServiceStartMode>] [-Status <String>] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a9453-108">Input object</span><span class="sxs-lookup"><span data-stu-id="a9453-108">InputObject</span></span>

```
Set-Service [-ComputerName <String[]>] [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Status <String>] [-InputObject <ServiceController>] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a9453-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a9453-109">DESCRIPTION</span></span>

<span data-ttu-id="a9453-110">`Set-Service`Met de cmdlet worden de eigenschappen van een service gewijzigd, zoals de **status** , **Beschrijving** , **DisplayName** en **opstart type**.</span><span class="sxs-lookup"><span data-stu-id="a9453-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType**.</span></span> <span data-ttu-id="a9453-111">`Set-Service` kan een service starten, stoppen, onderbreken of onderbreken.</span><span class="sxs-lookup"><span data-stu-id="a9453-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="a9453-112">Als u een service wilt identificeren, voert u de service naam in of verzendt u een service object.</span><span class="sxs-lookup"><span data-stu-id="a9453-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="a9453-113">Of verzend een service naam of Service object omlaag in de pijp lijn `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a9453-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="a9453-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a9453-114">EXAMPLES</span></span>

### <span data-ttu-id="a9453-115">Voor beeld 1: een weergave naam wijzigen</span><span class="sxs-lookup"><span data-stu-id="a9453-115">Example 1: Change a display name</span></span>

<span data-ttu-id="a9453-116">In dit voor beeld wordt de weergave naam van een service gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a9453-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="a9453-117">Als u de oorspronkelijke weergave naam wilt weer geven, gebruikt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="a9453-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="a9453-118">`Set-Service` maakt gebruik van de para meter **name** om de naam van de service op te geven, **lanmanworkstation**.</span><span class="sxs-lookup"><span data-stu-id="a9453-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation**.</span></span> <span data-ttu-id="a9453-119">Met de para meter **DisplayName** geeft u de nieuwe weergave naam op: **LANMAN-werk station**.</span><span class="sxs-lookup"><span data-stu-id="a9453-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation**.</span></span>

### <span data-ttu-id="a9453-120">Voor beeld 2: het opstart type van Services wijzigen</span><span class="sxs-lookup"><span data-stu-id="a9453-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="a9453-121">In dit voor beeld ziet u hoe u het opstart type van een service wijzigt.</span><span class="sxs-lookup"><span data-stu-id="a9453-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="a9453-122">`Set-Service`maakt gebruik van de para meter **name** om de naam van de service **op te geven.**</span><span class="sxs-lookup"><span data-stu-id="a9453-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS**.</span></span> <span data-ttu-id="a9453-123">Met de para meter **opstart type** wordt de service ingesteld op **automatisch**.</span><span class="sxs-lookup"><span data-stu-id="a9453-123">The **StartupType** parameter sets the service to **Automatic**.</span></span>

<span data-ttu-id="a9453-124">`Get-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="a9453-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="a9453-125">`Select-Object` gebruikt de para meter **Property** om de status van de **bits** -service weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a9453-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="a9453-126">Voor beeld 3: de beschrijving van een service wijzigen</span><span class="sxs-lookup"><span data-stu-id="a9453-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="a9453-127">In dit voor beeld wordt de beschrijving van de BITS-service gewijzigd en wordt het resultaat weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a9453-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="a9453-128">De `Get-CimInstance` cmdlet wordt gebruikt omdat deze een **Win32_Service** -object retourneert dat de **Beschrijving** van de service bevat.</span><span class="sxs-lookup"><span data-stu-id="a9453-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description**.</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

<span data-ttu-id="a9453-129">`Get-CimInstance` Hiermee wordt het object naar beneden verzonden naar de pijp lijn `Format-List` en worden de naam en beschrijving van de service weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a9453-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="a9453-130">Voor vergelijkings doeleinden wordt de opdracht uitgevoerd vóór en na het bijwerken van de beschrijving.</span><span class="sxs-lookup"><span data-stu-id="a9453-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="a9453-131">`Set-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven.</span><span class="sxs-lookup"><span data-stu-id="a9453-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="a9453-132">De **beschrijvings** parameter bevat de bijgewerkte tekst voor de beschrijving van de service.</span><span class="sxs-lookup"><span data-stu-id="a9453-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="a9453-133">Voor beeld 4: een service starten</span><span class="sxs-lookup"><span data-stu-id="a9453-133">Example 4: Start a service</span></span>

<span data-ttu-id="a9453-134">In dit voor beeld wordt een service gestart.</span><span class="sxs-lookup"><span data-stu-id="a9453-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="a9453-135">`Set-Service` maakt gebruik van de para meter **name** om de service, **WinRM** op te geven.</span><span class="sxs-lookup"><span data-stu-id="a9453-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM**.</span></span> <span data-ttu-id="a9453-136">De para meter **status** gebruikt de waarde **die wordt gebruikt** om de service te starten.</span><span class="sxs-lookup"><span data-stu-id="a9453-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="a9453-137">De para meter **PassThru** voert een **ServiceController** -object uit dat de resultaten weergeeft.</span><span class="sxs-lookup"><span data-stu-id="a9453-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="a9453-138">Voor beeld 5: een service opschorten</span><span class="sxs-lookup"><span data-stu-id="a9453-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="a9453-139">In dit voor beeld wordt de pijp lijn gebruikt om de service te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="a9453-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="a9453-140">`Get-Service` maakt gebruik van de para meter **name** om de **Schedule** -service op te geven en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="a9453-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="a9453-141">`Set-Service` maakt gebruik van de para meter **status** om de service in te stellen op **onderbroken**.</span><span class="sxs-lookup"><span data-stu-id="a9453-141">`Set-Service` uses the **Status** parameter to set the service to **Paused**.</span></span>

### <span data-ttu-id="a9453-142">Voor beeld 6: een service stoppen</span><span class="sxs-lookup"><span data-stu-id="a9453-142">Example 6: Stop a service</span></span>

<span data-ttu-id="a9453-143">In dit voor beeld wordt een variabele gebruikt om een service te stoppen.</span><span class="sxs-lookup"><span data-stu-id="a9453-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="a9453-144">`Get-Service` maakt gebruik van de para meter **name** om de service, de **planning** op te geven.</span><span class="sxs-lookup"><span data-stu-id="a9453-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule**.</span></span> <span data-ttu-id="a9453-145">Het object wordt opgeslagen in de variabele `$S` .</span><span class="sxs-lookup"><span data-stu-id="a9453-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="a9453-146">`Set-Service` maakt gebruik van de para meter **input object** en geeft het object op dat is opgeslagen `$S` .</span><span class="sxs-lookup"><span data-stu-id="a9453-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="a9453-147">Met de para meter **status** wordt de service ingesteld op **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="a9453-147">The **Status** parameter sets the service to **Stopped**.</span></span>

## <span data-ttu-id="a9453-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a9453-148">PARAMETERS</span></span>

### <span data-ttu-id="a9453-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a9453-149">-ComputerName</span></span>

<span data-ttu-id="a9453-150">Hiermee geeft u een of meer computers op.</span><span class="sxs-lookup"><span data-stu-id="a9453-150">Specifies one or more computers.</span></span> <span data-ttu-id="a9453-151">Voor externe computers typt u de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name.</span><span class="sxs-lookup"><span data-stu-id="a9453-151">For remote computers, type the NetBIOS name, an IP address, or a fully qualified domain name.</span></span> <span data-ttu-id="a9453-152">Als de para meter **ComputerName** niet is opgegeven, wordt de opdracht uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="a9453-152">If the **ComputerName** parameter isn't specified, the command runs on the local computer.</span></span>

<span data-ttu-id="a9453-153">Deze para meter is niet afhankelijk van externe communicatie met Power shell.</span><span class="sxs-lookup"><span data-stu-id="a9453-153">This parameter doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="a9453-154">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a9453-154">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9453-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a9453-155">-Confirm</span></span>

<span data-ttu-id="a9453-156">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a9453-156">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="a9453-157">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a9453-157">-Description</span></span>

<span data-ttu-id="a9453-158">Hiermee geeft u een nieuwe beschrijving op voor de service.</span><span class="sxs-lookup"><span data-stu-id="a9453-158">Specifies a new description for the service.</span></span>

<span data-ttu-id="a9453-159">De beschrijving van de service wordt weer gegeven in **computer beheer, services**.</span><span class="sxs-lookup"><span data-stu-id="a9453-159">The service description appears in **Computer Management, Services**.</span></span> <span data-ttu-id="a9453-160">De **Beschrijving** is geen eigenschap van het `Get-Service` **ServiceController** -object.</span><span class="sxs-lookup"><span data-stu-id="a9453-160">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="a9453-161">Als u de beschrijving van de service wilt zien, gebruikt u `Get-CimInstance` die een **Win32_Service** -object retourneert dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a9453-161">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9453-162">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="a9453-162">-DisplayName</span></span>

<span data-ttu-id="a9453-163">Hiermee geeft u een nieuwe weergave naam voor de service op.</span><span class="sxs-lookup"><span data-stu-id="a9453-163">Specifies a new display name for the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9453-164">-Input object</span><span class="sxs-lookup"><span data-stu-id="a9453-164">-InputObject</span></span>

<span data-ttu-id="a9453-165">Hiermee geeft u een **ServiceController** -object op dat de service vertegenwoordigt die moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a9453-165">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="a9453-166">Voer een variabele in die het object bevat of typ een opdracht of expressie waarmee het object wordt opgehaald, zoals een `Get-Service` opdracht.</span><span class="sxs-lookup"><span data-stu-id="a9453-166">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="a9453-167">U kunt de pijp lijn gebruiken om een service object naar te verzenden `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a9453-167">You can use the pipeline to send a service object to `Set-Service`.</span></span>

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

### <span data-ttu-id="a9453-168">-Name</span><span class="sxs-lookup"><span data-stu-id="a9453-168">-Name</span></span>

<span data-ttu-id="a9453-169">Hiermee geeft u de service naam op van de service die moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a9453-169">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="a9453-170">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="a9453-170">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="a9453-171">U kunt de pijp lijn gebruiken om een service naam naar te verzenden `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a9453-171">You can use the pipeline to send a service name to `Set-Service`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a9453-172">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a9453-172">-PassThru</span></span>

<span data-ttu-id="a9453-173">Retourneert een **ServiceController** -object dat staat voor de services die zijn gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a9453-173">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="a9453-174">Standaard genereert geen `Set-Service` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a9453-174">By default, `Set-Service` doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9453-175">-Opstart type</span><span class="sxs-lookup"><span data-stu-id="a9453-175">-StartupType</span></span>

<span data-ttu-id="a9453-176">Hiermee stelt u het opstart type van de service in.</span><span class="sxs-lookup"><span data-stu-id="a9453-176">Sets the startup type of the service.</span></span> <span data-ttu-id="a9453-177">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="a9453-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a9453-178">**Automatisch** : de service wordt gestart of is door het besturings systeem gestart tijdens het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="a9453-178">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="a9453-179">Als een service die automatisch wordt gestart, afhankelijk is van een hand matig gestarte service, wordt de hand matig gestarte service ook automatisch gestart bij het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="a9453-179">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="a9453-180">**Uitgeschakeld** : de service is uitgeschakeld en kan niet worden gestart door een gebruiker of toepassing.</span><span class="sxs-lookup"><span data-stu-id="a9453-180">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="a9453-181">**Hand matig** : de service wordt alleen hand matig gestart door een gebruiker, met behulp van service besturings beheer of door een toepassing.</span><span class="sxs-lookup"><span data-stu-id="a9453-181">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="a9453-182">**Boot** : geeft aan dat de service een apparaatstuurprogramma is dat door de System loader wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="a9453-182">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="a9453-183">Deze waarde is alleen geldig voor apparaatstuurprogramma's.</span><span class="sxs-lookup"><span data-stu-id="a9453-183">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="a9453-184">**Systeem** : geeft aan dat de service een apparaatstuurprogramma is dat is gestart door de functie IOInitSystem ().</span><span class="sxs-lookup"><span data-stu-id="a9453-184">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="a9453-185">Deze waarde is alleen geldig voor apparaatstuurprogramma's.</span><span class="sxs-lookup"><span data-stu-id="a9453-185">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="a9453-186">De standaard waarde is **automatisch**.</span><span class="sxs-lookup"><span data-stu-id="a9453-186">The default value is **Automatic**.</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9453-187">-Status</span><span class="sxs-lookup"><span data-stu-id="a9453-187">-Status</span></span>

<span data-ttu-id="a9453-188">Hiermee geeft u de status van de service op.</span><span class="sxs-lookup"><span data-stu-id="a9453-188">Specifies the status for the service.</span></span>

<span data-ttu-id="a9453-189">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="a9453-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="a9453-190">**Onderbroken**.</span><span class="sxs-lookup"><span data-stu-id="a9453-190">**Paused**.</span></span> <span data-ttu-id="a9453-191">Hiermee wordt de service onderbroken.</span><span class="sxs-lookup"><span data-stu-id="a9453-191">Suspends the service.</span></span>
- <span data-ttu-id="a9453-192">**Wordt uitgevoerd**.</span><span class="sxs-lookup"><span data-stu-id="a9453-192">**Running**.</span></span> <span data-ttu-id="a9453-193">De service wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="a9453-193">Starts the service.</span></span>
- <span data-ttu-id="a9453-194">**Gestopt**.</span><span class="sxs-lookup"><span data-stu-id="a9453-194">**Stopped**.</span></span> <span data-ttu-id="a9453-195">Hiermee stopt u de service.</span><span class="sxs-lookup"><span data-stu-id="a9453-195">Stops the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9453-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a9453-196">-WhatIf</span></span>

<span data-ttu-id="a9453-197">Hier wordt weer gegeven wat er gebeurt als er `Set-Service` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a9453-197">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="a9453-198">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a9453-198">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="a9453-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9453-199">CommonParameters</span></span>

<span data-ttu-id="a9453-200">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a9453-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9453-201">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a9453-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9453-202">INVOER</span><span class="sxs-lookup"><span data-stu-id="a9453-202">INPUTS</span></span>

### <span data-ttu-id="a9453-203">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="a9453-203">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="a9453-204">U kunt de pijp lijn gebruiken om een service object of een teken reeks die een service naam bevat te verzenden naar `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="a9453-204">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="a9453-205">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a9453-205">OUTPUTS</span></span>

### <span data-ttu-id="a9453-206">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="a9453-206">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="a9453-207">Er worden standaard `Set-Service` geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a9453-207">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="a9453-208">Gebruik de para meter **PassThru** voor het uitvoeren van een **ServiceController** -object.</span><span class="sxs-lookup"><span data-stu-id="a9453-208">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="a9453-209">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a9453-209">NOTES</span></span>

<span data-ttu-id="a9453-210">`Set-Service` vereist verhoogde machtigingen.</span><span class="sxs-lookup"><span data-stu-id="a9453-210">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="a9453-211">Gebruik de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="a9453-211">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="a9453-212">`Set-Service` kan alleen services beheren wanneer de huidige gebruiker machtigingen heeft om services te beheren.</span><span class="sxs-lookup"><span data-stu-id="a9453-212">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="a9453-213">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="a9453-213">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="a9453-214">Als u de service naam of weergave naam van een service wilt zoeken, gebruikt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="a9453-214">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="a9453-215">De service namen bevinden zich in de kolom **naam** en de weergave namen bevinden zich in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="a9453-215">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="a9453-216">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a9453-216">RELATED LINKS</span></span>

[<span data-ttu-id="a9453-217">Get-Service</span><span class="sxs-lookup"><span data-stu-id="a9453-217">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="a9453-218">New-Service</span><span class="sxs-lookup"><span data-stu-id="a9453-218">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="a9453-219">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="a9453-219">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="a9453-220">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="a9453-220">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="a9453-221">Start-Service</span><span class="sxs-lookup"><span data-stu-id="a9453-221">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="a9453-222">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="a9453-222">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="a9453-223">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="a9453-223">Suspend-Service</span></span>](Suspend-Service.md)
