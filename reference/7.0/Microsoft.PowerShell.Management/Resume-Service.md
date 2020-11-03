---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: a799326c943b09b5b9c0f9cecfdae3b64e6af409
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249770"
---
# <span data-ttu-id="45ae9-103">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="45ae9-103">Resume-Service</span></span>

## <span data-ttu-id="45ae9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="45ae9-104">SYNOPSIS</span></span>
<span data-ttu-id="45ae9-105">Hiermee worden een of meer onderbroken (onderbroken) Services hervat.</span><span class="sxs-lookup"><span data-stu-id="45ae9-105">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="45ae9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="45ae9-106">SYNTAX</span></span>

### <span data-ttu-id="45ae9-107">Input object (standaard)</span><span class="sxs-lookup"><span data-stu-id="45ae9-107">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="45ae9-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="45ae9-108">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="45ae9-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="45ae9-109">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="45ae9-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="45ae9-110">DESCRIPTION</span></span>

<span data-ttu-id="45ae9-111">De cmdlet **Resume-service** stuurt een resume-bericht naar de Windows-service controller voor elk van de opgegeven services.</span><span class="sxs-lookup"><span data-stu-id="45ae9-111">The **Resume-Service** cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="45ae9-112">Als een service wordt onderbroken, wordt deze hervat.</span><span class="sxs-lookup"><span data-stu-id="45ae9-112">If a service is suspended, it resumes.</span></span>
<span data-ttu-id="45ae9-113">Als deze momenteel wordt uitgevoerd, wordt het bericht genegeerd.</span><span class="sxs-lookup"><span data-stu-id="45ae9-113">If it is currently running, the message is ignored.</span></span>
<span data-ttu-id="45ae9-114">U kunt de services opgeven met hun service namen of weergave namen, of u kunt de para meter *input object* gebruiken om een service object door te geven dat staat voor de services die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="45ae9-114">You can specify the services by their service names or display names, or you can use the *InputObject* parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="45ae9-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="45ae9-115">EXAMPLES</span></span>

### <span data-ttu-id="45ae9-116">Voor beeld 1: een service op de lokale computer hervatten</span><span class="sxs-lookup"><span data-stu-id="45ae9-116">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="45ae9-117">Met deze opdracht wordt de systeem gebeurtenis meldings service op de lokale computer hervat.</span><span class="sxs-lookup"><span data-stu-id="45ae9-117">This command resumes the System Event Notification service  on the local computer.</span></span>
<span data-ttu-id="45ae9-118">De service naam wordt weer gegeven in de opdracht door Sens.</span><span class="sxs-lookup"><span data-stu-id="45ae9-118">The service name is represented in the command by sens.</span></span>
<span data-ttu-id="45ae9-119">De opdracht gebruikt de para meter *name* om de service naam van de service op te geven, maar de opdracht laat de parameter naam achterwege omdat de parameter naam optioneel is.</span><span class="sxs-lookup"><span data-stu-id="45ae9-119">The command uses the *Name* parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="45ae9-120">Voor beeld 2: alle onderbroken services hervatten</span><span class="sxs-lookup"><span data-stu-id="45ae9-120">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="45ae9-121">Met deze opdracht worden alle onderbroken services op de computer hervat.</span><span class="sxs-lookup"><span data-stu-id="45ae9-121">This command resumes all of the suspended  services on the computer.</span></span>
<span data-ttu-id="45ae9-122">Met de opdracht cmdlet Get-Service worden alle services op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="45ae9-122">The Get-Service cmdlet command gets all of the services on the computer.</span></span>
<span data-ttu-id="45ae9-123">De pijplijn operator (|) geeft de resultaten door aan de cmdlet Where-Object, die de Services selecteert waarvan de eigenschap **status** is onderbroken.</span><span class="sxs-lookup"><span data-stu-id="45ae9-123">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the services that have a **Status** property of Paused.</span></span>
<span data-ttu-id="45ae9-124">De volgende pijplijn operator verzendt de resultaten naar **hervatten-service** , waardoor de onderbroken services worden hervat.</span><span class="sxs-lookup"><span data-stu-id="45ae9-124">The next pipeline operator sends the results to **Resume-Service** , which resumes the paused services.</span></span>

<span data-ttu-id="45ae9-125">In de praktijk gebruikt u de para meter *WhatIf* om het effect van de opdracht te bepalen voordat u deze uitvoert.</span><span class="sxs-lookup"><span data-stu-id="45ae9-125">In practice, you would use the *WhatIf* parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="45ae9-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="45ae9-126">PARAMETERS</span></span>

### <span data-ttu-id="45ae9-127">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="45ae9-127">-DisplayName</span></span>

<span data-ttu-id="45ae9-128">Hiermee geeft u de weergave namen op van de services die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="45ae9-128">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="45ae9-129">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="45ae9-129">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="45ae9-130">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="45ae9-130">-Exclude</span></span>

<span data-ttu-id="45ae9-131">Hiermee geeft u de services die door deze cmdlet worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="45ae9-131">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="45ae9-132">De waarde van deze para meter komt in aanmerking voor de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="45ae9-132">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="45ae9-133">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="45ae9-133">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="45ae9-134">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="45ae9-134">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="45ae9-135">-Include</span><span class="sxs-lookup"><span data-stu-id="45ae9-135">-Include</span></span>

<span data-ttu-id="45ae9-136">Hiermee geeft u de services op die u wilt hervatten.</span><span class="sxs-lookup"><span data-stu-id="45ae9-136">Specifies services to resume.</span></span>
<span data-ttu-id="45ae9-137">Met de waarde van deze para meter wordt de para meter *name* gekwalificeerd.</span><span class="sxs-lookup"><span data-stu-id="45ae9-137">The value of this parameter qualifies *Name* parameter.</span></span>
<span data-ttu-id="45ae9-138">Voer een naam element of patroon in, zoals s \*.</span><span class="sxs-lookup"><span data-stu-id="45ae9-138">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="45ae9-139">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="45ae9-139">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="45ae9-140">-Input object</span><span class="sxs-lookup"><span data-stu-id="45ae9-140">-InputObject</span></span>

<span data-ttu-id="45ae9-141">Hiermee geeft u de **ServiceController** -objecten op die de services vertegenwoordigen om te hervatten.</span><span class="sxs-lookup"><span data-stu-id="45ae9-141">Specifies **ServiceController** objects that represent the services to resumed.</span></span>
<span data-ttu-id="45ae9-142">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="45ae9-142">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="45ae9-143">-Name</span><span class="sxs-lookup"><span data-stu-id="45ae9-143">-Name</span></span>

<span data-ttu-id="45ae9-144">Hiermee geeft u de service namen op van de services die moeten worden hervat.</span><span class="sxs-lookup"><span data-stu-id="45ae9-144">Specifies the service names of the services to be resumed.</span></span>

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

### <span data-ttu-id="45ae9-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="45ae9-145">-PassThru</span></span>

<span data-ttu-id="45ae9-146">Retourneert een object dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="45ae9-146">Returns an object that represents the service.</span></span>
<span data-ttu-id="45ae9-147">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="45ae9-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="45ae9-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="45ae9-148">-Confirm</span></span>

<span data-ttu-id="45ae9-149">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="45ae9-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="45ae9-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="45ae9-150">-WhatIf</span></span>

<span data-ttu-id="45ae9-151">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="45ae9-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="45ae9-152">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="45ae9-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="45ae9-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45ae9-153">CommonParameters</span></span>

<span data-ttu-id="45ae9-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="45ae9-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45ae9-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="45ae9-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45ae9-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="45ae9-156">INPUTS</span></span>

### <span data-ttu-id="45ae9-157">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="45ae9-157">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="45ae9-158">U kunt een service object of een teken reeks die een service naam bevat door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45ae9-158">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="45ae9-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="45ae9-159">OUTPUTS</span></span>

### <span data-ttu-id="45ae9-160">Geen, System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="45ae9-160">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="45ae9-161">Met deze cmdlet wordt een **System. ServiceProcess. ServiceController** -object gegenereerd dat de hervatde service vertegenwoordigt, als u de para meter *PassThru* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="45ae9-161">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="45ae9-162">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="45ae9-162">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="45ae9-163">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="45ae9-163">NOTES</span></span>

* <span data-ttu-id="45ae9-164">De status van de services die zijn onderbroken, wordt onderbroken.</span><span class="sxs-lookup"><span data-stu-id="45ae9-164">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="45ae9-165">Wanneer Services worden hervat, wordt de status ervan uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="45ae9-165">When services are resumed, their status is Running.</span></span>
* <span data-ttu-id="45ae9-166">**Resume-service** kan alleen services bepalen wanneer de huidige gebruiker gemachtigd is om dit uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="45ae9-166">**Resume-Service** can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="45ae9-167">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="45ae9-167">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="45ae9-168">Als u de service namen wilt zoeken en de namen van de services op uw systeem wilt weer geven, typt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="45ae9-168">To find the service names and display names of the services on your system, type `Get-Service`.</span></span> <span data-ttu-id="45ae9-169">De service namen worden weer gegeven in de kolom **naam** en de weergave namen worden weer gegeven in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="45ae9-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="45ae9-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="45ae9-170">RELATED LINKS</span></span>

[<span data-ttu-id="45ae9-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="45ae9-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="45ae9-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="45ae9-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="45ae9-173">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="45ae9-173">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="45ae9-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="45ae9-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="45ae9-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="45ae9-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="45ae9-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="45ae9-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="45ae9-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="45ae9-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="45ae9-178">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="45ae9-178">Remove-Service</span></span>](Remove-Service.md)
