---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: 8c9e520f1f19444fd538fabee99a48ec08c69992
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705951"
---
# <span data-ttu-id="712a2-102">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="712a2-102">Stop-Process</span></span>

## <span data-ttu-id="712a2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="712a2-103">SYNOPSIS</span></span>
<span data-ttu-id="712a2-104">Hiermee stopt u een of meer actieve processen.</span><span class="sxs-lookup"><span data-stu-id="712a2-104">Stops one or more running processes.</span></span>

## <span data-ttu-id="712a2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="712a2-105">SYNTAX</span></span>

### <span data-ttu-id="712a2-106">Id (standaard)</span><span class="sxs-lookup"><span data-stu-id="712a2-106">Id (Default)</span></span>

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="712a2-107">Name</span><span class="sxs-lookup"><span data-stu-id="712a2-107">Name</span></span>

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="712a2-108">Input object</span><span class="sxs-lookup"><span data-stu-id="712a2-108">InputObject</span></span>

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="712a2-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="712a2-109">DESCRIPTION</span></span>

<span data-ttu-id="712a2-110">De cmdlet **Stop-process** stopt een of meer actieve processen.</span><span class="sxs-lookup"><span data-stu-id="712a2-110">The **Stop-Process** cmdlet stops one or more running processes.</span></span>
<span data-ttu-id="712a2-111">U kunt een proces opgeven op basis van de proces naam of proces-ID (PID) of een proces object door geven om het proces te **stoppen**.</span><span class="sxs-lookup"><span data-stu-id="712a2-111">You can specify a process by process name or process ID (PID), or pass a process object to **Stop-Process**.</span></span>
<span data-ttu-id="712a2-112">**Stop: het proces** werkt alleen voor processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="712a2-112">**Stop-Process** works only on processes running on the local computer.</span></span>

<span data-ttu-id="712a2-113">In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell starten met de optie als administrator uitvoeren om een proces te stoppen dat geen eigendom is van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="712a2-113">On Windows Vista and later versions of the Windows operating system, to stop a process that is not owned by the current user, you must start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="712a2-114">U wordt ook niet gevraagd om bevestiging tenzij u de para meter *confirm* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="712a2-114">Also, you are not prompted for confirmation unless you specify the *Confirm* parameter.</span></span>

## <span data-ttu-id="712a2-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="712a2-115">EXAMPLES</span></span>

### <span data-ttu-id="712a2-116">Voor beeld 1: alle exemplaren van een proces stoppen</span><span class="sxs-lookup"><span data-stu-id="712a2-116">Example 1: Stop all instances of a process</span></span>

```
PS C:\> Stop-Process -Name "notepad"
```

<span data-ttu-id="712a2-117">Met deze opdracht worden alle exemplaren van het klad blok-proces op de computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-117">This command stops all instances of the Notepad process on the computer.</span></span>
<span data-ttu-id="712a2-118">Elk exemplaar van Klad blok wordt uitgevoerd in een eigen proces.</span><span class="sxs-lookup"><span data-stu-id="712a2-118">Each instance of Notepad runs in its own process.</span></span>
<span data-ttu-id="712a2-119">Hierbij wordt de para meter *name* gebruikt voor het opgeven van de processen, die allemaal dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="712a2-119">It uses the *Name* parameter to specify the processes, all of which have the same name.</span></span>
<span data-ttu-id="712a2-120">Als u de *id-* para meter zou gebruiken om dezelfde processen te stoppen, moet u de proces-id's van elk exemplaar van Klad blok vermelden.</span><span class="sxs-lookup"><span data-stu-id="712a2-120">If you were to use the *Id* parameter to stop the same processes, you would have to list the process IDs of each instance of Notepad.</span></span>

### <span data-ttu-id="712a2-121">Voor beeld 2: een specifiek exemplaar van een proces stoppen</span><span class="sxs-lookup"><span data-stu-id="712a2-121">Example 2: Stop a specific instance of a process</span></span>

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

<span data-ttu-id="712a2-122">Met deze opdracht wordt een bepaald exemplaar van het klad blok-proces gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-122">This command stops a particular instance of the Notepad process.</span></span>
<span data-ttu-id="712a2-123">De proces-ID, 3952, wordt gebruikt om het proces te identificeren.</span><span class="sxs-lookup"><span data-stu-id="712a2-123">It uses the process ID, 3952, to identify the process.</span></span>
<span data-ttu-id="712a2-124">De para meter *confirm* stuurt Power shell door om u te vragen voordat het proces wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-124">The *Confirm* parameter directs PowerShell to prompt you before it stops the process.</span></span>
<span data-ttu-id="712a2-125">Omdat de prompt de proces namein toevoegen aan de ID, is dit best practice.</span><span class="sxs-lookup"><span data-stu-id="712a2-125">Because the prompt includes the process namein addition to its ID, this is best practice.</span></span>
<span data-ttu-id="712a2-126">Met de para meter *PassThru* wordt het proces object door gegeven aan de formatter voor weer gave.</span><span class="sxs-lookup"><span data-stu-id="712a2-126">The *PassThru* parameter passes the process object to the formatter for display.</span></span>
<span data-ttu-id="712a2-127">Zonder deze para meter wordt er geen weer gegeven na de opdracht **Stop-process** .</span><span class="sxs-lookup"><span data-stu-id="712a2-127">Without this parameter, there would be no display after a **Stop-Process** command.</span></span>

### <span data-ttu-id="712a2-128">Voor beeld 3: een proces stoppen en detecteren dat het is gestopt</span><span class="sxs-lookup"><span data-stu-id="712a2-128">Example 3: Stop a process and detect that it has stopped</span></span>

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

<span data-ttu-id="712a2-129">Met deze reeks opdrachten wordt het proces voor het berekenen gestart en gestopt, waarna processen worden gedetecteerd die zijn gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-129">This series of commands starts and stops the Calc process, and then detects processes that have stopped.</span></span>

<span data-ttu-id="712a2-130">Met de eerste opdracht wordt een exemplaar van de reken machine gestart.</span><span class="sxs-lookup"><span data-stu-id="712a2-130">The first command starts an instance of the calculator.</span></span>

<span data-ttu-id="712a2-131">Met de tweede opdracht wordt **Get-process** gebruikt om een object op te halen dat het verwerkings proces vertegenwoordigt, en vervolgens opgeslagen in de variabele $p.</span><span class="sxs-lookup"><span data-stu-id="712a2-131">The second command uses **Get-Process** gets an object that represents the Calc process, and then stores it in the $p variable.</span></span>

<span data-ttu-id="712a2-132">Met de derde opdracht wordt het berekenen van het proces gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-132">The third command stops the Calc process.</span></span>
<span data-ttu-id="712a2-133">De para meter *input object* wordt gebruikt om het object door te geven om het **proces te stoppen**.</span><span class="sxs-lookup"><span data-stu-id="712a2-133">It uses the *InputObject* parameter to pass the object to **Stop-Process**.</span></span>

<span data-ttu-id="712a2-134">De laatste opdracht haalt alle processen op de computer op die actief waren, maar die nu zijn gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-134">The last command gets all of the processes on the computer that were running but that are now stopped.</span></span>
<span data-ttu-id="712a2-135">Het gebruikt **Get-process** om alle processen op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="712a2-135">It uses **Get-Process** to get all of the processes on the computer.</span></span>
<span data-ttu-id="712a2-136">De pijplijn operator (|) geeft de resultaten door aan de cmdlet Where-Object, die de waarden selecteert waar de eigenschap **HasExited** is $True.</span><span class="sxs-lookup"><span data-stu-id="712a2-136">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the ones where the value of the **HasExited** property is $True.</span></span>
<span data-ttu-id="712a2-137">**HasExited** is slechts één eigenschap van proces objecten.</span><span class="sxs-lookup"><span data-stu-id="712a2-137">**HasExited** is just one property of process objects.</span></span>
<span data-ttu-id="712a2-138">Als u alle eigenschappen wilt zoeken, typt u `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="712a2-138">To find all the properties, type `Get-Process | Get-Member`.</span></span>

### <span data-ttu-id="712a2-139">Voor beeld 4: een proces stoppen dat niet het eigendom is van de huidige gebruiker</span><span class="sxs-lookup"><span data-stu-id="712a2-139">Example 4: Stop a process not owned by the current user</span></span>

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

<span data-ttu-id="712a2-140">Deze opdrachten tonen het effect van het gebruik van *Force* om een proces te stoppen dat geen eigendom is van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="712a2-140">These commands show the effect of using *Force* to stop a process that is not owned by the user.</span></span>

<span data-ttu-id="712a2-141">De eerste opdracht gebruikt **Get-process** om het Lsass-proces op te halen.</span><span class="sxs-lookup"><span data-stu-id="712a2-141">The first command uses **Get-Process** to get the Lsass process.</span></span>
<span data-ttu-id="712a2-142">Een pijplijn operator verzendt het proces om te **stoppen,** om het te stoppen.</span><span class="sxs-lookup"><span data-stu-id="712a2-142">A pipeline operator sends the process to **Stop-Process** to stop it.</span></span>
<span data-ttu-id="712a2-143">Zoals in de voorbeeld uitvoer wordt weer gegeven, mislukt de eerste opdracht met een bericht dat de toegang is geweigerd, omdat dit proces alleen kan worden gestopt door een lid van de groep Administrators op de computer.</span><span class="sxs-lookup"><span data-stu-id="712a2-143">As shown in the sample output, the first command fails with an Access denied message, because this process can be stopped only by a member of the Administrator group on the computer.</span></span>

<span data-ttu-id="712a2-144">Wanneer Power shell wordt geopend met de optie als administrator uitvoeren en de opdracht wordt herhaald, vraagt Power shell u om bevestiging.</span><span class="sxs-lookup"><span data-stu-id="712a2-144">When PowerShell is opened by using the Run as administrator option, and the command is repeated, PowerShell prompts you for confirmation.</span></span>

<span data-ttu-id="712a2-145">Met de tweede opdracht wordt *geforceerd* dat de prompt wordt onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="712a2-145">The second command specifies *Force* to suppress the prompt.</span></span>
<span data-ttu-id="712a2-146">Als gevolg hiervan wordt het proces zonder bevestiging gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-146">As a result, the process is stopped without confirmation.</span></span>

## <span data-ttu-id="712a2-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="712a2-147">PARAMETERS</span></span>

### <span data-ttu-id="712a2-148">-Force</span><span class="sxs-lookup"><span data-stu-id="712a2-148">-Force</span></span>

<span data-ttu-id="712a2-149">Hiermee worden de opgegeven processen gestopt zonder dat om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="712a2-149">Stops the specified processes without prompting for confirmation.</span></span>
<span data-ttu-id="712a2-150">Standaard vraagt **het Stop proces** om bevestiging voordat een proces wordt gestopt dat geen eigendom is van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="712a2-150">By default, **Stop-Process** prompts for confirmation before stopping any process that is not owned by the current user.</span></span>

<span data-ttu-id="712a2-151">Als u de eigenaar van een proces wilt vinden, gebruikt u de `Get-CimInstance` cmdlet om een **Win32_Process** -object op te halen dat het proces vertegenwoordigt, en gebruikt u vervolgens de methode **GetOwner** van het object.</span><span class="sxs-lookup"><span data-stu-id="712a2-151">To find the owner of a process, use the `Get-CimInstance` cmdlet to get a **Win32_Process** object that represents the process, and then use the **GetOwner** method of the object.</span></span>

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

### <span data-ttu-id="712a2-152">-Id</span><span class="sxs-lookup"><span data-stu-id="712a2-152">-Id</span></span>

<span data-ttu-id="712a2-153">Hiermee geeft u de proces-Id's op van de processen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-153">Specifies the process IDs of the processes to stop.</span></span>
<span data-ttu-id="712a2-154">Als u meerdere Id's wilt opgeven, gebruikt u komma's om de Id's van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="712a2-154">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="712a2-155">Als u de PID van een proces wilt vinden, typt u `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="712a2-155">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="712a2-156">-Input object</span><span class="sxs-lookup"><span data-stu-id="712a2-156">-InputObject</span></span>

<span data-ttu-id="712a2-157">Hiermee geeft u de proces objecten op die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-157">Specifies the process objects to stop.</span></span>
<span data-ttu-id="712a2-158">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="712a2-158">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="712a2-159">-Name</span><span class="sxs-lookup"><span data-stu-id="712a2-159">-Name</span></span>

<span data-ttu-id="712a2-160">Hiermee geeft u de proces namen op van de processen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-160">Specifies the process names of the processes to stop.</span></span>
<span data-ttu-id="712a2-161">U kunt meerdere proces namen typen, gescheiden door komma's of joker tekens gebruiken.</span><span class="sxs-lookup"><span data-stu-id="712a2-161">You can type multiple process names, separated by commas, or use wildcard characters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="712a2-162">-PassThru</span><span class="sxs-lookup"><span data-stu-id="712a2-162">-PassThru</span></span>

<span data-ttu-id="712a2-163">Retourneert een object dat het proces vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="712a2-163">Returns an object that represents the process.</span></span>
<span data-ttu-id="712a2-164">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="712a2-164">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="712a2-165">-Confirm</span><span class="sxs-lookup"><span data-stu-id="712a2-165">-Confirm</span></span>

<span data-ttu-id="712a2-166">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="712a2-166">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="712a2-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="712a2-167">-WhatIf</span></span>

<span data-ttu-id="712a2-168">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="712a2-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="712a2-169">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="712a2-169">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="712a2-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="712a2-170">CommonParameters</span></span>
<span data-ttu-id="712a2-171">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="712a2-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="712a2-172">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="712a2-172">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="712a2-173">INVOER</span><span class="sxs-lookup"><span data-stu-id="712a2-173">INPUTS</span></span>

### <span data-ttu-id="712a2-174">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="712a2-174">System.Diagnostics.Process</span></span>

<span data-ttu-id="712a2-175">U kunt een proces object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="712a2-175">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="712a2-176">UITVOER</span><span class="sxs-lookup"><span data-stu-id="712a2-176">OUTPUTS</span></span>

### <span data-ttu-id="712a2-177">Geen, System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="712a2-177">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="712a2-178">Deze cmdlet retourneert een **System. Diagnostics. process** -object dat het gestopte proces vertegenwoordigt, als u de para meter *PassThru* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="712a2-178">This cmdlet returns a **System.Diagnostics.Process** object that represents the stopped process, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="712a2-179">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="712a2-179">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="712a2-180">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="712a2-180">NOTES</span></span>

* <span data-ttu-id="712a2-181">U kunt ook verwijzen naar **Stop-process** door de ingebouwde aliassen, **Kill** en **spps**.</span><span class="sxs-lookup"><span data-stu-id="712a2-181">You can also refer to **Stop-Process** by its built-in aliases, **kill** and **spps**.</span></span> <span data-ttu-id="712a2-182">Zie about_Aliases voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="712a2-182">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="712a2-183">U kunt ook de eigenschappen en methoden van het **Win32_Process** -object Windows Management Instrumentation (WMI) in Windows Power shell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="712a2-183">You can also use the properties and methods of the Windows Management Instrumentation (WMI) **Win32_Process** object in Windows PowerShell.</span></span>
<span data-ttu-id="712a2-184">Zie `Get-CimInstance` en de WMI-SDK voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="712a2-184">For more information, see `Get-CimInstance` and the WMI SDK.</span></span>

* <span data-ttu-id="712a2-185">Bij het stoppen van processen kan het stoppen van het proces en de services die afhankelijk zijn van het proces, worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="712a2-185">When stopping processes, realize that stopping a process can stop process and services that depend on the process.</span></span>
<span data-ttu-id="712a2-186">In een extreem geval kan Windows stoppen met het stoppen van een proces.</span><span class="sxs-lookup"><span data-stu-id="712a2-186">In an extreme case, stopping a process can stop Windows.</span></span>

## <span data-ttu-id="712a2-187">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="712a2-187">RELATED LINKS</span></span>

[<span data-ttu-id="712a2-188">Debug-proces</span><span class="sxs-lookup"><span data-stu-id="712a2-188">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="712a2-189">Get-Process</span><span class="sxs-lookup"><span data-stu-id="712a2-189">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="712a2-190">Start-process</span><span class="sxs-lookup"><span data-stu-id="712a2-190">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="712a2-191">Stoppen-proces</span><span class="sxs-lookup"><span data-stu-id="712a2-191">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="712a2-192">Wacht proces</span><span class="sxs-lookup"><span data-stu-id="712a2-192">Wait-Process</span></span>](Wait-Process.md)

