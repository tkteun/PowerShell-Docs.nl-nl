---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 8ce2182117167d93c8f7abd86eeb2c79abdf09c8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705871"
---
# <span data-ttu-id="02628-102">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="02628-102">Resume-Service</span></span>

## <span data-ttu-id="02628-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="02628-103">SYNOPSIS</span></span>
<span data-ttu-id="02628-104">Hiermee worden een of meer onderbroken (onderbroken) Services hervat.</span><span class="sxs-lookup"><span data-stu-id="02628-104">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="02628-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="02628-105">SYNTAX</span></span>

### <span data-ttu-id="02628-106">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="02628-106">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="02628-107">Standaard</span><span class="sxs-lookup"><span data-stu-id="02628-107">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="02628-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="02628-108">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="02628-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="02628-109">DESCRIPTION</span></span>

<span data-ttu-id="02628-110">De `Resume-Service` cmdlet verzendt een resume-bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="02628-110">The `Resume-Service` cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="02628-111">Als een service wordt onderbroken, wordt deze hervat.</span><span class="sxs-lookup"><span data-stu-id="02628-111">If a service is suspended, it resumes.</span></span> <span data-ttu-id="02628-112">Als deze momenteel wordt uitgevoerd, wordt het bericht genegeerd.</span><span class="sxs-lookup"><span data-stu-id="02628-112">If it is currently running, the message is ignored.</span></span> <span data-ttu-id="02628-113">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object door te geven dat staat voor de services die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="02628-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="02628-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="02628-114">EXAMPLES</span></span>

### <span data-ttu-id="02628-115">Voor beeld 1: een service op de lokale computer hervatten</span><span class="sxs-lookup"><span data-stu-id="02628-115">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="02628-116">Met deze opdracht wordt de systeem gebeurtenis meldings service op de lokale computer hervat.</span><span class="sxs-lookup"><span data-stu-id="02628-116">This command resumes the System Event Notification service on the local computer.</span></span> <span data-ttu-id="02628-117">De service naam wordt weer gegeven in de opdracht door Sens.</span><span class="sxs-lookup"><span data-stu-id="02628-117">The service name is represented in the command by sens.</span></span> <span data-ttu-id="02628-118">De opdracht gebruikt de para meter **name** om de service naam van de service op te geven, maar de opdracht laat de parameter naam achterwege omdat de parameter naam optioneel is.</span><span class="sxs-lookup"><span data-stu-id="02628-118">The command uses the **Name** parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="02628-119">Voor beeld 2: alle onderbroken services hervatten</span><span class="sxs-lookup"><span data-stu-id="02628-119">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="02628-120">Met deze opdracht worden alle onderbroken services op de computer hervat.</span><span class="sxs-lookup"><span data-stu-id="02628-120">This command resumes all of the suspended services on the computer.</span></span> <span data-ttu-id="02628-121">De `Get-Service` cmdlet opdracht haalt alle services op de computer op.</span><span class="sxs-lookup"><span data-stu-id="02628-121">The `Get-Service` cmdlet command gets all of the services on the computer.</span></span> <span data-ttu-id="02628-122">De pijplijn operator ( `|` ) geeft de resultaten door aan de `Where-Object` cmdlet, die de Services selecteert waarvan de eigenschap **status** is onderbroken.</span><span class="sxs-lookup"><span data-stu-id="02628-122">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects the services that have a **Status** property of Paused.</span></span> <span data-ttu-id="02628-123">De volgende pijplijn operator verzendt de resultaten naar `Resume-Service` , waardoor de onderbroken services worden hervat.</span><span class="sxs-lookup"><span data-stu-id="02628-123">The next pipeline operator sends the results to `Resume-Service`, which resumes the paused services.</span></span>

<span data-ttu-id="02628-124">In de praktijk gebruikt u de para meter **WhatIf** om het effect van de opdracht te bepalen voordat u deze uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02628-124">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="02628-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="02628-125">PARAMETERS</span></span>

### <span data-ttu-id="02628-126">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="02628-126">-DisplayName</span></span>

<span data-ttu-id="02628-127">Hiermee geeft u de weergave namen op van de services die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="02628-127">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="02628-128">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="02628-128">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="02628-129">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="02628-129">-Exclude</span></span>

<span data-ttu-id="02628-130">Hiermee geeft u de services die door deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="02628-130">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="02628-131">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="02628-131">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="02628-132">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="02628-132">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="02628-133">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="02628-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="02628-134">-Include</span><span class="sxs-lookup"><span data-stu-id="02628-134">-Include</span></span>

<span data-ttu-id="02628-135">Hiermee geeft u de services op die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="02628-135">Specifies services to resume.</span></span> <span data-ttu-id="02628-136">Met de waarde van deze para meter wordt de para meter **name** gekwalificeerd.</span><span class="sxs-lookup"><span data-stu-id="02628-136">The value of this parameter qualifies **Name** parameter.</span></span> <span data-ttu-id="02628-137">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="02628-137">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="02628-138">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="02628-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="02628-139">-Input object</span><span class="sxs-lookup"><span data-stu-id="02628-139">-InputObject</span></span>

<span data-ttu-id="02628-140">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen om te hervatten.</span><span class="sxs-lookup"><span data-stu-id="02628-140">Specifies **ServiceController** objects that represent the services to resumed.</span></span> <span data-ttu-id="02628-141">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="02628-141">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="02628-142">-Name</span><span class="sxs-lookup"><span data-stu-id="02628-142">-Name</span></span>

<span data-ttu-id="02628-143">Hiermee geeft u de service namen op van de services die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="02628-143">Specifies the service names of the services to be resumed.</span></span>

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

### <span data-ttu-id="02628-144">-PassThru</span><span class="sxs-lookup"><span data-stu-id="02628-144">-PassThru</span></span>

<span data-ttu-id="02628-145">Retourneert een object dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="02628-145">Returns an object that represents the service.</span></span> <span data-ttu-id="02628-146">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="02628-146">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="02628-147">-Confirm</span><span class="sxs-lookup"><span data-stu-id="02628-147">-Confirm</span></span>

<span data-ttu-id="02628-148">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02628-148">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="02628-149">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="02628-149">-WhatIf</span></span>

<span data-ttu-id="02628-150">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02628-150">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="02628-151">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="02628-151">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="02628-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="02628-152">CommonParameters</span></span>

<span data-ttu-id="02628-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="02628-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="02628-154">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02628-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="02628-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="02628-155">INPUTS</span></span>

### <span data-ttu-id="02628-156">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="02628-156">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="02628-157">U kunt een service object of een teken reeks die een service naam bevat door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02628-157">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="02628-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="02628-158">OUTPUTS</span></span>

### <span data-ttu-id="02628-159">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="02628-159">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="02628-160">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de hervatde service vertegenwoordigt, als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="02628-160">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="02628-161">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="02628-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="02628-162">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="02628-162">NOTES</span></span>

<span data-ttu-id="02628-163">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="02628-163">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="02628-164">De status van de services die zijn onderbroken, wordt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="02628-164">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="02628-165">Wanneer Services worden hervat, wordt de status ervan uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="02628-165">When services are resumed, their status is Running.</span></span>
- <span data-ttu-id="02628-166">`Resume-Service` kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="02628-166">`Resume-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="02628-167">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="02628-167">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="02628-168">Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="02628-168">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="02628-169">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="02628-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="02628-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="02628-170">RELATED LINKS</span></span>

[<span data-ttu-id="02628-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="02628-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="02628-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="02628-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="02628-173">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="02628-173">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="02628-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="02628-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="02628-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="02628-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="02628-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="02628-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="02628-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="02628-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="02628-178">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="02628-178">Remove-Service</span></span>](Remove-Service.md)
