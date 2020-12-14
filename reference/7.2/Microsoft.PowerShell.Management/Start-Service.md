---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: b1df4490da501111ccb44dea2645a333fdf5c27e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706024"
---
# <span data-ttu-id="fbfe0-102">Start-Service</span><span class="sxs-lookup"><span data-stu-id="fbfe0-102">Start-Service</span></span>

## <span data-ttu-id="fbfe0-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fbfe0-103">SYNOPSIS</span></span>
<span data-ttu-id="fbfe0-104">Start een of meer gestopt Services.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-104">Starts one or more stopped services.</span></span>

## <span data-ttu-id="fbfe0-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fbfe0-105">SYNTAX</span></span>

### <span data-ttu-id="fbfe0-106">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="fbfe0-106">InputObject (Default)</span></span>

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fbfe0-107">Standaard</span><span class="sxs-lookup"><span data-stu-id="fbfe0-107">Default</span></span>

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="fbfe0-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fbfe0-108">DisplayName</span></span>

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fbfe0-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fbfe0-109">DESCRIPTION</span></span>

<span data-ttu-id="fbfe0-110">De `Start-Service` cmdlet verzendt een start bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-110">The `Start-Service` cmdlet sends a start message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="fbfe0-111">Als er al een service wordt uitgevoerd, wordt het bericht genegeerd zonder dat er een fout is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-111">If a service is already running, the message is ignored without error.</span></span> <span data-ttu-id="fbfe0-112">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object op te geven dat staat voor de services die u wilt starten.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to supply a service object that represents the services that you want to start.</span></span>

## <span data-ttu-id="fbfe0-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fbfe0-113">EXAMPLES</span></span>

### <span data-ttu-id="fbfe0-114">Voor beeld 1: een service starten met behulp van de naam</span><span class="sxs-lookup"><span data-stu-id="fbfe0-114">Example 1: Start a service by using its name</span></span>

<span data-ttu-id="fbfe0-115">In dit voor beeld wordt de EventLog-service op de lokale computer gestart.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-115">This example starts the EventLog service on the local computer.</span></span> <span data-ttu-id="fbfe0-116">De **naam** parameter identificeert de service op basis van de service naam.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-116">The **Name** parameter identifies the service by its service name.</span></span>

```powershell
Start-Service -Name "eventlog"
```

### <span data-ttu-id="fbfe0-117">Voor beeld 2: gegevens weer geven zonder een service te starten</span><span class="sxs-lookup"><span data-stu-id="fbfe0-117">Example 2: Display information without starting a service</span></span>

<span data-ttu-id="fbfe0-118">In dit voor beeld ziet u wat er zou gebeuren als u de services hebt gestart met een weergave naam die ' Extern ' bevat.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-118">This example shows what would occur if you started the services that have a display name that includes "remote".</span></span>

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

<span data-ttu-id="fbfe0-119">Met de para meter **DisplayName** worden de services geïdentificeerd op basis van de weergave naam in plaats van de service naam.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-119">The **DisplayName** parameter identifies the services by their display name instead of their service name.</span></span> <span data-ttu-id="fbfe0-120">De para meter **WhatIf** zorgt ervoor dat de cmdlet weergeeft wat er zou gebeuren wanneer u de opdracht uitvoert, maar geen wijzigingen aanbrengt.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-120">The **WhatIf** parameter causes the cmdlet to display what would happen when you run the command but does not make changes.</span></span>

### <span data-ttu-id="fbfe0-121">Voor beeld 3: een service starten en de actie vastleggen in een tekst bestand</span><span class="sxs-lookup"><span data-stu-id="fbfe0-121">Example 3: Start a service and record the action in a text file</span></span>

<span data-ttu-id="fbfe0-122">In dit voor beeld wordt de Windows Management Instrumentation (WMI)-service op de computer gestart en wordt een record van de actie toegevoegd aan het services.txt bestand.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-122">This example starts the Windows Management Instrumentation (WMI) service on the computer and adds a record of the action to the services.txt file.</span></span>

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

<span data-ttu-id="fbfe0-123">Eerst wordt gebruikt `Get-Service` om een object op te halen dat de WMI-service vertegenwoordigt en op te slaan in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-123">First we use `Get-Service` to get an object that represent the WMI service and store it in the `$s` variable.</span></span> <span data-ttu-id="fbfe0-124">Vervolgens wordt de service gestart.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-124">Next, we start the service.</span></span> <span data-ttu-id="fbfe0-125">Zonder de  para meter PassThru `Start-Service` wordt geen uitvoer gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-125">Without the **PassThru** parameter, `Start-Service` does not create any output.</span></span> <span data-ttu-id="fbfe0-126">De pijplijn operator (|) geeft de object uitvoer door `Start-Service` aan de `Format-List` cmdlet om het object op te maken als een lijst met eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-126">The pipeline operator (|) passes the object output by `Start-Service` to the `Format-List` cmdlet to format the object as a list of its properties.</span></span> <span data-ttu-id="fbfe0-127">Met de operator voor het omleiden van toevoeg bewerkingen ( \> \> ) wordt de uitvoer omgeleid naar het services.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-127">The append redirection operator (\>\>) redirects the output to the services.txt file.</span></span> <span data-ttu-id="fbfe0-128">De uitvoer wordt toegevoegd aan het einde van het bestaande bestand.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-128">The output is added to the end of the existing file.</span></span>

### <span data-ttu-id="fbfe0-129">Voor beeld 4: een uitgeschakelde service starten</span><span class="sxs-lookup"><span data-stu-id="fbfe0-129">Example 4: Start a disabled service</span></span>

<span data-ttu-id="fbfe0-130">In dit voor beeld ziet u hoe u een service start wanneer het opstart type van de service wordt **uitgeschakeld**.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-130">This example shows how to start a service when the start type of the service is **Disabled**.</span></span>

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

<span data-ttu-id="fbfe0-131">De eerste poging om de Telnet-service (TlntSvr) te starten, mislukt.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-131">The first attempt to start the Telnet service (tlntsvr) fails.</span></span> <span data-ttu-id="fbfe0-132">De `Get-CimInstance` opdracht geeft aan dat de eigenschap **Start** modus van de TlntSvr-service is **uitgeschakeld**.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-132">The `Get-CimInstance` command shows that the **StartMode** property of the Tlntsvr service is **Disabled**.</span></span> <span data-ttu-id="fbfe0-133">`Set-Service`Met de cmdlet wordt het type start gewijzigd in **hand matig**.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-133">The `Set-Service` cmdlet changes the start type to **Manual**.</span></span> <span data-ttu-id="fbfe0-134">Nu kunnen we de opdracht opnieuw verzenden `Start-Service` .</span><span class="sxs-lookup"><span data-stu-id="fbfe0-134">Now, we can resubmit the `Start-Service` command.</span></span> <span data-ttu-id="fbfe0-135">Deze keer is de opdracht geslaagd.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-135">This time, the command succeeds.</span></span> <span data-ttu-id="fbfe0-136">Voer uit om te controleren of de opdracht is geslaagd `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="fbfe0-136">To verify that the command succeeded, run `Get-Service`.</span></span>

## <span data-ttu-id="fbfe0-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fbfe0-137">PARAMETERS</span></span>

### <span data-ttu-id="fbfe0-138">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="fbfe0-138">-DisplayName</span></span>

<span data-ttu-id="fbfe0-139">Hiermee geeft u de weergave namen op van de services die moeten worden gestart.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-139">Specifies the display names of the services to start.</span></span> <span data-ttu-id="fbfe0-140">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="fbfe0-141">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="fbfe0-141">-Exclude</span></span>

<span data-ttu-id="fbfe0-142">Hiermee geeft u de services die door deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-142">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="fbfe0-143">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="fbfe0-143">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="fbfe0-144">Voer een naam element of patroon in, bijvoorbeeld `s*` .</span><span class="sxs-lookup"><span data-stu-id="fbfe0-144">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="fbfe0-145">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="fbfe0-146">-Include</span><span class="sxs-lookup"><span data-stu-id="fbfe0-146">-Include</span></span>

<span data-ttu-id="fbfe0-147">Hiermee geeft u de services op die met deze cmdlet worden gestart.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-147">Specifies services that this cmdlet starts.</span></span> <span data-ttu-id="fbfe0-148">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="fbfe0-148">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="fbfe0-149">Voer een naam element of patroon in, bijvoorbeeld `s*` .</span><span class="sxs-lookup"><span data-stu-id="fbfe0-149">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="fbfe0-150">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-150">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="fbfe0-151">-Input object</span><span class="sxs-lookup"><span data-stu-id="fbfe0-151">-InputObject</span></span>

<span data-ttu-id="fbfe0-152">Hiermee geeft u **ServiceController** -objecten op die de services vertegenwoordigen die moeten worden gestart.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-152">Specifies **ServiceController** objects representing the services to be started.</span></span> <span data-ttu-id="fbfe0-153">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-153">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="fbfe0-154">-Name</span><span class="sxs-lookup"><span data-stu-id="fbfe0-154">-Name</span></span>

<span data-ttu-id="fbfe0-155">Hiermee geeft u de service namen voor de service moet worden gestart.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-155">Specifies the service names for the service to be started.</span></span>

<span data-ttu-id="fbfe0-156">De parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-156">The parameter name is optional.</span></span> <span data-ttu-id="fbfe0-157">U kunt de **naam** of de alias ervan **gebruiken, of** u kunt de parameter naam weglaten.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-157">You can use **Name** or its alias, **ServiceName**, or you can omit the parameter name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fbfe0-158">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fbfe0-158">-PassThru</span></span>

<span data-ttu-id="fbfe0-159">Retourneert een object dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-159">Returns an object that represents the service.</span></span> <span data-ttu-id="fbfe0-160">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="fbfe0-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fbfe0-161">-Confirm</span></span>

<span data-ttu-id="fbfe0-162">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fbfe0-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fbfe0-163">-WhatIf</span></span>

<span data-ttu-id="fbfe0-164">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fbfe0-165">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fbfe0-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fbfe0-166">CommonParameters</span></span>

<span data-ttu-id="fbfe0-167">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fbfe0-168">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fbfe0-169">INVOER</span><span class="sxs-lookup"><span data-stu-id="fbfe0-169">INPUTS</span></span>

### <span data-ttu-id="fbfe0-170">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="fbfe0-170">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="fbfe0-171">U kunt objecten pipeen die de services of teken reeksen vertegenwoordigen die de service namen bevatten voor deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-171">You can pipe objects that represent the services or strings that contain the service names to this cmdlet.</span></span>

## <span data-ttu-id="fbfe0-172">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fbfe0-172">OUTPUTS</span></span>

### <span data-ttu-id="fbfe0-173">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="fbfe0-173">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="fbfe0-174">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de service vertegenwoordigt, als u **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-174">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify **PassThru**.</span></span> <span data-ttu-id="fbfe0-175">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-175">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="fbfe0-176">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fbfe0-176">NOTES</span></span>

<span data-ttu-id="fbfe0-177">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-177">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="fbfe0-178">U kunt ook verwijzen naar `Start-Service` de ingebouwde alias `sasv` .</span><span class="sxs-lookup"><span data-stu-id="fbfe0-178">You can also refer to `Start-Service` by its built-in alias, `sasv`.</span></span> <span data-ttu-id="fbfe0-179">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-179">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="fbfe0-180">`Start-Service` Hiermee kunnen alleen services worden beheerd als de huidige gebruiker gemachtigd is om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-180">`Start-Service` can control services only if the current user has permission to do this.</span></span> <span data-ttu-id="fbfe0-181">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-181">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="fbfe0-182">Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="fbfe0-182">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="fbfe0-183">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="fbfe0-183">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>
- <span data-ttu-id="fbfe0-184">U kunt alleen de services starten die het begin type hand matig, automatisch of automatisch hebben (vertraagd starten).</span><span class="sxs-lookup"><span data-stu-id="fbfe0-184">You can start only the services that have a start type of Manual, Automatic, or Automatic (Delayed Start).</span></span> <span data-ttu-id="fbfe0-185">U kunt de services die het begin type uitgeschakeld hebben niet starten.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-185">You cannot start the services that have a start type of Disabled.</span></span> <span data-ttu-id="fbfe0-186">Als een `Start-Service` opdracht mislukt met het bericht `Cannot start service \<service-name\> on computer` , gebruikt `Get-CimInstance` u om het start type van de service te vinden. Als u dat wilt, gebruikt u de `Set-Service` cmdlet om het start type van de service te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-186">If a `Start-Service` command fails with the message `Cannot start service \<service-name\> on computer`, use `Get-CimInstance` to find the start type of the service and, if you have to, use the `Set-Service` cmdlet to change the start type of the service.</span></span>
- <span data-ttu-id="fbfe0-187">Sommige services, zoals Performance Logs and Alerts (SysmonLog), worden automatisch gestopt als ze geen werk hebben.</span><span class="sxs-lookup"><span data-stu-id="fbfe0-187">Some services, such as Performance Logs and Alerts (SysmonLog) stop automatically if they have no work to do.</span></span> <span data-ttu-id="fbfe0-188">Wanneer Power shell een service start die zichzelf bijna onmiddellijk stopt, wordt het volgende bericht weer gegeven: `Service \<display-name\> start failed.`</span><span class="sxs-lookup"><span data-stu-id="fbfe0-188">When PowerShell starts a service that stops itself almost immediately, it displays the following message: `Service \<display-name\> start failed.`</span></span>

## <span data-ttu-id="fbfe0-189">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fbfe0-189">RELATED LINKS</span></span>

[<span data-ttu-id="fbfe0-190">Get-Service</span><span class="sxs-lookup"><span data-stu-id="fbfe0-190">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="fbfe0-191">New-Service</span><span class="sxs-lookup"><span data-stu-id="fbfe0-191">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="fbfe0-192">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="fbfe0-192">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="fbfe0-193">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="fbfe0-193">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="fbfe0-194">Set-Service</span><span class="sxs-lookup"><span data-stu-id="fbfe0-194">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="fbfe0-195">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="fbfe0-195">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="fbfe0-196">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="fbfe0-196">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="fbfe0-197">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="fbfe0-197">Remove-Service</span></span>](Remove-Service.md)
