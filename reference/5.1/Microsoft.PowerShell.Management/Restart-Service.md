---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: b5af4f55166993e54048dd76bb8345550718c170
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250563"
---
# <span data-ttu-id="6da1f-103">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="6da1f-103">Restart-Service</span></span>

## <span data-ttu-id="6da1f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6da1f-104">SYNOPSIS</span></span>
<span data-ttu-id="6da1f-105">Stopt en start een of meer services.</span><span class="sxs-lookup"><span data-stu-id="6da1f-105">Stops and then starts one or more services.</span></span>

## <span data-ttu-id="6da1f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6da1f-106">SYNTAX</span></span>

### <span data-ttu-id="6da1f-107">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="6da1f-107">InputObject (Default)</span></span>

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6da1f-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="6da1f-108">Default</span></span>

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6da1f-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6da1f-109">DisplayName</span></span>

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6da1f-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6da1f-110">DESCRIPTION</span></span>

<span data-ttu-id="6da1f-111">De cmdlet **restart-service** verzendt een Stop bericht en vervolgens een start bericht naar de Windows-service controller voor een opgegeven service.</span><span class="sxs-lookup"><span data-stu-id="6da1f-111">The **Restart-Service** cmdlet sends a stop message and then a start message to the Windows Service Controller for a specified service.</span></span>
<span data-ttu-id="6da1f-112">Als een service al is gestopt, wordt deze gestart zonder dat u wordt gewaarschuwd als er een fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="6da1f-112">If a service was already stopped, it is started without notifying you of an error.</span></span>
<span data-ttu-id="6da1f-113">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter *input object* gebruiken om een object door te geven dat elke service vertegenwoordigt die u opnieuw wilt opstarten.</span><span class="sxs-lookup"><span data-stu-id="6da1f-113">You can specify the services by their service names or display names, or you can use the *InputObject* parameter to pass an object that represents each service that you want to restart.</span></span>

## <span data-ttu-id="6da1f-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6da1f-114">EXAMPLES</span></span>

### <span data-ttu-id="6da1f-115">Voor beeld 1: een service opnieuw starten op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="6da1f-115">Example 1: Restart a service on the local computer</span></span>

```powershell
PS C:\> Restart-Service -Name winmgmt
```

<span data-ttu-id="6da1f-116">Met deze opdracht wordt de Windows Management Instrumentation service (WinMgmt) opnieuw gestart op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="6da1f-116">This command restarts the Windows Management Instrumentation service (WinMgmt) on the local computer.</span></span>

### <span data-ttu-id="6da1f-117">Voor beeld 2: een service uitsluiten</span><span class="sxs-lookup"><span data-stu-id="6da1f-117">Example 2: Exclude a service</span></span>

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

<span data-ttu-id="6da1f-118">Met deze opdracht worden de services die een weergave naam hebben die begint met net, met uitzonde ring van de Net Logon-service opnieuw gestart.</span><span class="sxs-lookup"><span data-stu-id="6da1f-118">This command restarts the services that have a display name that starts with Net, except for the Net Logon service.</span></span>

### <span data-ttu-id="6da1f-119">Voor beeld 3: alle gestopt netwerk services starten</span><span class="sxs-lookup"><span data-stu-id="6da1f-119">Example 3: Start all stopped network services</span></span>

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

<span data-ttu-id="6da1f-120">Met deze opdracht worden alle gestopte netwerk services op de computer gestart.</span><span class="sxs-lookup"><span data-stu-id="6da1f-120">This command starts all of the stopped network services on the computer.</span></span>

<span data-ttu-id="6da1f-121">Met deze opdracht wordt de cmdlet Get-Service gebruikt om objecten op te halen die de services vertegenwoordigen waarvan de service naam begint met net.</span><span class="sxs-lookup"><span data-stu-id="6da1f-121">This command uses the Get-Service cmdlet to get objects that represent the services whose service name starts with net.</span></span>
<span data-ttu-id="6da1f-122">De pijplijn operator (|) verzendt het object Services naar de cmdlet Where-Object, waarmee alleen de services worden geselecteerd die de status gestopt hebben.</span><span class="sxs-lookup"><span data-stu-id="6da1f-122">The pipeline operator (|) sends the services object to the Where-Object cmdlet, which selects only the services that have a status of stopped.</span></span>
<span data-ttu-id="6da1f-123">Een andere pijplijn operator verzendt de geselecteerde services om de **service opnieuw te starten**.</span><span class="sxs-lookup"><span data-stu-id="6da1f-123">Another pipeline operator sends the selected services to **Restart-Service**.</span></span>

<span data-ttu-id="6da1f-124">In de praktijk gebruikt u de para meter *WhatIf* om het effect van de opdracht te bepalen voordat u deze uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6da1f-124">In practice, you would use the *WhatIf* parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="6da1f-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6da1f-125">PARAMETERS</span></span>

### <span data-ttu-id="6da1f-126">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="6da1f-126">-DisplayName</span></span>

<span data-ttu-id="6da1f-127">Hiermee geeft u de weergave namen op van de services die opnieuw moeten worden gestart.</span><span class="sxs-lookup"><span data-stu-id="6da1f-127">Specifies the display names of services to restarted.</span></span>
<span data-ttu-id="6da1f-128">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6da1f-128">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="6da1f-129">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="6da1f-129">-Exclude</span></span>

<span data-ttu-id="6da1f-130">Hiermee geeft u de services die door deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="6da1f-130">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="6da1f-131">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="6da1f-131">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="6da1f-132">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="6da1f-132">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="6da1f-133">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6da1f-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="6da1f-134">-Force</span><span class="sxs-lookup"><span data-stu-id="6da1f-134">-Force</span></span>

<span data-ttu-id="6da1f-135">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="6da1f-135">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="6da1f-136">-Include</span><span class="sxs-lookup"><span data-stu-id="6da1f-136">-Include</span></span>

<span data-ttu-id="6da1f-137">Hiermee geeft u de services op die met deze cmdlet opnieuw worden gestart.</span><span class="sxs-lookup"><span data-stu-id="6da1f-137">Specifies services that this cmdlet restarts.</span></span>
<span data-ttu-id="6da1f-138">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="6da1f-138">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="6da1f-139">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="6da1f-139">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="6da1f-140">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6da1f-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="6da1f-141">-Input object</span><span class="sxs-lookup"><span data-stu-id="6da1f-141">-InputObject</span></span>

<span data-ttu-id="6da1f-142">Hiermee geeft u **ServiceController** -objecten op die de services vertegenwoordigen die opnieuw moeten worden gestart.</span><span class="sxs-lookup"><span data-stu-id="6da1f-142">Specifies **ServiceController** objects that represent the services to restart.</span></span>
<span data-ttu-id="6da1f-143">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6da1f-143">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="6da1f-144">-Name</span><span class="sxs-lookup"><span data-stu-id="6da1f-144">-Name</span></span>

<span data-ttu-id="6da1f-145">Hiermee geeft u de service namen op van de services die opnieuw moeten worden gestart.</span><span class="sxs-lookup"><span data-stu-id="6da1f-145">Specifies the service names of the services to restart.</span></span>

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

### <span data-ttu-id="6da1f-146">-PassThru</span><span class="sxs-lookup"><span data-stu-id="6da1f-146">-PassThru</span></span>

<span data-ttu-id="6da1f-147">Retourneert een object dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="6da1f-147">Returns an object that represents the service.</span></span>
<span data-ttu-id="6da1f-148">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="6da1f-148">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="6da1f-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6da1f-149">-Confirm</span></span>

<span data-ttu-id="6da1f-150">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6da1f-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6da1f-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6da1f-151">-WhatIf</span></span>

<span data-ttu-id="6da1f-152">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6da1f-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6da1f-153">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6da1f-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6da1f-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6da1f-154">CommonParameters</span></span>

<span data-ttu-id="6da1f-155">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6da1f-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6da1f-156">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6da1f-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6da1f-157">INVOER</span><span class="sxs-lookup"><span data-stu-id="6da1f-157">INPUTS</span></span>

### <span data-ttu-id="6da1f-158">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="6da1f-158">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="6da1f-159">U kunt een service object of een teken reeks die een service naam bevat door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6da1f-159">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="6da1f-160">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6da1f-160">OUTPUTS</span></span>

### <span data-ttu-id="6da1f-161">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="6da1f-161">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="6da1f-162">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de opnieuw gestarte service vertegenwoordigt als u de para meter *PassThru* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="6da1f-162">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the restarted service, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="6da1f-163">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="6da1f-163">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6da1f-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6da1f-164">NOTES</span></span>

* <span data-ttu-id="6da1f-165">**Restart: Service** kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6da1f-165">**Restart-Service** can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="6da1f-166">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="6da1f-166">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="6da1f-167">Typ **Get-service** om de service namen te vinden en de namen van de services op uw systeem weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6da1f-167">To find the service names and display names of the services on your system, type **Get-Service** ".</span></span> <span data-ttu-id="6da1f-168">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="6da1f-168">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="6da1f-169">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6da1f-169">RELATED LINKS</span></span>

[<span data-ttu-id="6da1f-170">Get-Service</span><span class="sxs-lookup"><span data-stu-id="6da1f-170">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="6da1f-171">New-Service</span><span class="sxs-lookup"><span data-stu-id="6da1f-171">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="6da1f-172">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="6da1f-172">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="6da1f-173">Set-Service</span><span class="sxs-lookup"><span data-stu-id="6da1f-173">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="6da1f-174">Start-Service</span><span class="sxs-lookup"><span data-stu-id="6da1f-174">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="6da1f-175">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="6da1f-175">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="6da1f-176">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="6da1f-176">Suspend-Service</span></span>](Suspend-Service.md)
