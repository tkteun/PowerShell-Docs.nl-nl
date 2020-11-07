---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 2d627625dec5afe6397a3fb346716adfd3fdb31c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342906"
---
# <span data-ttu-id="9ef79-103">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="9ef79-103">Resume-Service</span></span>

## <span data-ttu-id="9ef79-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9ef79-104">SYNOPSIS</span></span>
<span data-ttu-id="9ef79-105">Hiermee worden een of meer onderbroken (onderbroken) Services hervat.</span><span class="sxs-lookup"><span data-stu-id="9ef79-105">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="9ef79-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9ef79-106">SYNTAX</span></span>

### <span data-ttu-id="9ef79-107">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="9ef79-107">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9ef79-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="9ef79-108">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="9ef79-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9ef79-109">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9ef79-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9ef79-110">DESCRIPTION</span></span>

<span data-ttu-id="9ef79-111">De `Resume-Service` cmdlet verzendt een resume-bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="9ef79-111">The `Resume-Service` cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="9ef79-112">Als een service wordt onderbroken, wordt deze hervat.</span><span class="sxs-lookup"><span data-stu-id="9ef79-112">If a service is suspended, it resumes.</span></span> <span data-ttu-id="9ef79-113">Als deze momenteel wordt uitgevoerd, wordt het bericht genegeerd.</span><span class="sxs-lookup"><span data-stu-id="9ef79-113">If it is currently running, the message is ignored.</span></span> <span data-ttu-id="9ef79-114">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter **input object** gebruiken om een service object door te geven dat staat voor de services die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="9ef79-114">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="9ef79-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9ef79-115">EXAMPLES</span></span>

### <span data-ttu-id="9ef79-116">Voor beeld 1: een service op de lokale computer hervatten</span><span class="sxs-lookup"><span data-stu-id="9ef79-116">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="9ef79-117">Met deze opdracht wordt de systeem gebeurtenis meldings service op de lokale computer hervat.</span><span class="sxs-lookup"><span data-stu-id="9ef79-117">This command resumes the System Event Notification service on the local computer.</span></span> <span data-ttu-id="9ef79-118">De service naam wordt weer gegeven in de opdracht door Sens.</span><span class="sxs-lookup"><span data-stu-id="9ef79-118">The service name is represented in the command by sens.</span></span> <span data-ttu-id="9ef79-119">De opdracht gebruikt de para meter **name** om de service naam van de service op te geven, maar de opdracht laat de parameter naam achterwege omdat de parameter naam optioneel is.</span><span class="sxs-lookup"><span data-stu-id="9ef79-119">The command uses the **Name** parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="9ef79-120">Voor beeld 2: alle onderbroken services hervatten</span><span class="sxs-lookup"><span data-stu-id="9ef79-120">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="9ef79-121">Met deze opdracht worden alle onderbroken services op de computer hervat.</span><span class="sxs-lookup"><span data-stu-id="9ef79-121">This command resumes all of the suspended services on the computer.</span></span> <span data-ttu-id="9ef79-122">De `Get-Service` cmdlet opdracht haalt alle services op de computer op.</span><span class="sxs-lookup"><span data-stu-id="9ef79-122">The `Get-Service` cmdlet command gets all of the services on the computer.</span></span> <span data-ttu-id="9ef79-123">De pijplijn operator ( `|` ) geeft de resultaten door aan de `Where-Object` cmdlet, die de Services selecteert waarvan de eigenschap **status** is onderbroken.</span><span class="sxs-lookup"><span data-stu-id="9ef79-123">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects the services that have a **Status** property of Paused.</span></span> <span data-ttu-id="9ef79-124">De volgende pijplijn operator verzendt de resultaten naar `Resume-Service` , waardoor de onderbroken services worden hervat.</span><span class="sxs-lookup"><span data-stu-id="9ef79-124">The next pipeline operator sends the results to `Resume-Service`, which resumes the paused services.</span></span>

<span data-ttu-id="9ef79-125">In de praktijk gebruikt u de para meter **WhatIf** om het effect van de opdracht te bepalen voordat u deze uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9ef79-125">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="9ef79-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9ef79-126">PARAMETERS</span></span>

### <span data-ttu-id="9ef79-127">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="9ef79-127">-DisplayName</span></span>

<span data-ttu-id="9ef79-128">Hiermee geeft u de weergave namen op van de services die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="9ef79-128">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="9ef79-129">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9ef79-129">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="9ef79-130">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="9ef79-130">-Exclude</span></span>

<span data-ttu-id="9ef79-131">Hiermee geeft u de services die door deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="9ef79-131">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="9ef79-132">De waarde van deze para meter komt in aanmerking voor de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="9ef79-132">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="9ef79-133">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="9ef79-133">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="9ef79-134">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9ef79-134">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="9ef79-135">-Include</span><span class="sxs-lookup"><span data-stu-id="9ef79-135">-Include</span></span>

<span data-ttu-id="9ef79-136">Hiermee geeft u de services op die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="9ef79-136">Specifies services to resume.</span></span> <span data-ttu-id="9ef79-137">Met de waarde van deze para meter wordt de para meter **name** gekwalificeerd.</span><span class="sxs-lookup"><span data-stu-id="9ef79-137">The value of this parameter qualifies **Name** parameter.</span></span> <span data-ttu-id="9ef79-138">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="9ef79-138">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="9ef79-139">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9ef79-139">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="9ef79-140">-Input object</span><span class="sxs-lookup"><span data-stu-id="9ef79-140">-InputObject</span></span>

<span data-ttu-id="9ef79-141">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen om te hervatten.</span><span class="sxs-lookup"><span data-stu-id="9ef79-141">Specifies **ServiceController** objects that represent the services to resumed.</span></span> <span data-ttu-id="9ef79-142">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9ef79-142">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="9ef79-143">-Name</span><span class="sxs-lookup"><span data-stu-id="9ef79-143">-Name</span></span>

<span data-ttu-id="9ef79-144">Hiermee geeft u de service namen op van de services die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="9ef79-144">Specifies the service names of the services to be resumed.</span></span>

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

### <span data-ttu-id="9ef79-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9ef79-145">-PassThru</span></span>

<span data-ttu-id="9ef79-146">Retourneert een object dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="9ef79-146">Returns an object that represents the service.</span></span> <span data-ttu-id="9ef79-147">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="9ef79-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="9ef79-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9ef79-148">-Confirm</span></span>

<span data-ttu-id="9ef79-149">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9ef79-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9ef79-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9ef79-150">-WhatIf</span></span>

<span data-ttu-id="9ef79-151">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9ef79-151">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9ef79-152">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9ef79-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9ef79-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ef79-153">CommonParameters</span></span>

<span data-ttu-id="9ef79-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9ef79-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9ef79-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9ef79-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ef79-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="9ef79-156">INPUTS</span></span>

### <span data-ttu-id="9ef79-157">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="9ef79-157">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="9ef79-158">U kunt een service object of een teken reeks die een service naam bevat door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9ef79-158">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="9ef79-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9ef79-159">OUTPUTS</span></span>

### <span data-ttu-id="9ef79-160">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="9ef79-160">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="9ef79-161">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de hervatde service vertegenwoordigt, als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="9ef79-161">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="9ef79-162">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9ef79-162">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9ef79-163">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9ef79-163">NOTES</span></span>

<span data-ttu-id="9ef79-164">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="9ef79-164">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="9ef79-165">De status van de services die zijn onderbroken, wordt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="9ef79-165">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="9ef79-166">Wanneer Services worden hervat, wordt de status ervan uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9ef79-166">When services are resumed, their status is Running.</span></span>
- <span data-ttu-id="9ef79-167">`Resume-Service` kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="9ef79-167">`Resume-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="9ef79-168">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="9ef79-168">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="9ef79-169">Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="9ef79-169">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="9ef79-170">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="9ef79-170">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="9ef79-171">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9ef79-171">RELATED LINKS</span></span>

[<span data-ttu-id="9ef79-172">Get-Service</span><span class="sxs-lookup"><span data-stu-id="9ef79-172">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="9ef79-173">New-Service</span><span class="sxs-lookup"><span data-stu-id="9ef79-173">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="9ef79-174">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="9ef79-174">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="9ef79-175">Set-Service</span><span class="sxs-lookup"><span data-stu-id="9ef79-175">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="9ef79-176">Start-Service</span><span class="sxs-lookup"><span data-stu-id="9ef79-176">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="9ef79-177">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="9ef79-177">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="9ef79-178">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="9ef79-178">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="9ef79-179">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="9ef79-179">Remove-Service</span></span>](Remove-Service.md)
