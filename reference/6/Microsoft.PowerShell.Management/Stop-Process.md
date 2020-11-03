---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: a2f340f0119823ddc0876d86fc38e49edc51fe5d
ms.sourcegitcommit: 11abf355ac545531c2b04217a08ebe6be609c0bb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/18/2020
ms.locfileid: "93251933"
---
# <span data-ttu-id="2d697-103">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="2d697-103">Stop-Process</span></span>

## <span data-ttu-id="2d697-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2d697-104">SYNOPSIS</span></span>
<span data-ttu-id="2d697-105">Hiermee stopt u een of meer actieve processen.</span><span class="sxs-lookup"><span data-stu-id="2d697-105">Stops one or more running processes.</span></span>

## <span data-ttu-id="2d697-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2d697-106">SYNTAX</span></span>

### <span data-ttu-id="2d697-107">Id (standaard)</span><span class="sxs-lookup"><span data-stu-id="2d697-107">Id (Default)</span></span>

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2d697-108">Naam</span><span class="sxs-lookup"><span data-stu-id="2d697-108">Name</span></span>

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2d697-109">Input object</span><span class="sxs-lookup"><span data-stu-id="2d697-109">InputObject</span></span>

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2d697-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2d697-110">DESCRIPTION</span></span>

<span data-ttu-id="2d697-111">De cmdlet **Stop-process** stopt een of meer actieve processen.</span><span class="sxs-lookup"><span data-stu-id="2d697-111">The **Stop-Process** cmdlet stops one or more running processes.</span></span>
<span data-ttu-id="2d697-112">U kunt een proces opgeven op basis van de proces naam of proces-ID (PID) of een proces object door geven om het proces te **stoppen**.</span><span class="sxs-lookup"><span data-stu-id="2d697-112">You can specify a process by process name or process ID (PID), or pass a process object to **Stop-Process**.</span></span>
<span data-ttu-id="2d697-113">**Stop: het proces** werkt alleen voor processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2d697-113">**Stop-Process** works only on processes running on the local computer.</span></span>

<span data-ttu-id="2d697-114">In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell starten met de optie als administrator uitvoeren om een proces te stoppen dat geen eigendom is van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2d697-114">On Windows Vista and later versions of the Windows operating system, to stop a process that is not owned by the current user, you must start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="2d697-115">U wordt ook niet gevraagd om bevestiging tenzij u de para meter *confirm* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="2d697-115">Also, you are not prompted for confirmation unless you specify the *Confirm* parameter.</span></span>

## <span data-ttu-id="2d697-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2d697-116">EXAMPLES</span></span>

### <span data-ttu-id="2d697-117">Voor beeld 1: alle exemplaren van een proces stoppen</span><span class="sxs-lookup"><span data-stu-id="2d697-117">Example 1: Stop all instances of a process</span></span>

```
PS C:\> Stop-Process -Name "notepad"
```

<span data-ttu-id="2d697-118">Met deze opdracht worden alle exemplaren van het klad blok-proces op de computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-118">This command stops all instances of the Notepad process on the computer.</span></span>
<span data-ttu-id="2d697-119">Elk exemplaar van Klad blok wordt uitgevoerd in een eigen proces.</span><span class="sxs-lookup"><span data-stu-id="2d697-119">Each instance of Notepad runs in its own process.</span></span>
<span data-ttu-id="2d697-120">Hierbij wordt de para meter *name* gebruikt voor het opgeven van de processen, die allemaal dezelfde naam hebben.</span><span class="sxs-lookup"><span data-stu-id="2d697-120">It uses the *Name* parameter to specify the processes, all of which have the same name.</span></span>
<span data-ttu-id="2d697-121">Als u de *id-* para meter zou gebruiken om dezelfde processen te stoppen, moet u de proces-id's van elk exemplaar van Klad blok vermelden.</span><span class="sxs-lookup"><span data-stu-id="2d697-121">If you were to use the *Id* parameter to stop the same processes, you would have to list the process IDs of each instance of Notepad.</span></span>

### <span data-ttu-id="2d697-122">Voor beeld 2: een specifiek exemplaar van een proces stoppen</span><span class="sxs-lookup"><span data-stu-id="2d697-122">Example 2: Stop a specific instance of a process</span></span>

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

<span data-ttu-id="2d697-123">Met deze opdracht wordt een bepaald exemplaar van het klad blok-proces gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-123">This command stops a particular instance of the Notepad process.</span></span>
<span data-ttu-id="2d697-124">De proces-ID, 3952, wordt gebruikt om het proces te identificeren.</span><span class="sxs-lookup"><span data-stu-id="2d697-124">It uses the process ID, 3952, to identify the process.</span></span>
<span data-ttu-id="2d697-125">De para meter *confirm* stuurt Power shell door om u te vragen voordat het proces wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-125">The *Confirm* parameter directs PowerShell to prompt you before it stops the process.</span></span>
<span data-ttu-id="2d697-126">Omdat de prompt de proces namein toevoegen aan de ID, is dit best practice.</span><span class="sxs-lookup"><span data-stu-id="2d697-126">Because the prompt includes the process namein addition to its ID, this is best practice.</span></span>
<span data-ttu-id="2d697-127">Met de para meter *PassThru* wordt het proces object door gegeven aan de formatter voor weer gave.</span><span class="sxs-lookup"><span data-stu-id="2d697-127">The *PassThru* parameter passes the process object to the formatter for display.</span></span>
<span data-ttu-id="2d697-128">Zonder deze para meter wordt er geen weer gegeven na de opdracht **Stop-process** .</span><span class="sxs-lookup"><span data-stu-id="2d697-128">Without this parameter, there would be no display after a **Stop-Process** command.</span></span>

### <span data-ttu-id="2d697-129">Voor beeld 3: een proces stoppen en detecteren dat het is gestopt</span><span class="sxs-lookup"><span data-stu-id="2d697-129">Example 3: Stop a process and detect that it has stopped</span></span>

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

<span data-ttu-id="2d697-130">Met deze reeks opdrachten wordt het proces voor het berekenen gestart en gestopt, waarna processen worden gedetecteerd die zijn gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-130">This series of commands starts and stops the Calc process, and then detects processes that have stopped.</span></span>

<span data-ttu-id="2d697-131">Met de eerste opdracht wordt een exemplaar van de reken machine gestart.</span><span class="sxs-lookup"><span data-stu-id="2d697-131">The first command starts an instance of the calculator.</span></span>

<span data-ttu-id="2d697-132">Met de tweede opdracht wordt **Get-process** gebruikt om een object op te halen dat het verwerkings proces vertegenwoordigt, en vervolgens opgeslagen in de variabele $p.</span><span class="sxs-lookup"><span data-stu-id="2d697-132">The second command uses **Get-Process** gets an object that represents the Calc process, and then stores it in the $p variable.</span></span>

<span data-ttu-id="2d697-133">Met de derde opdracht wordt het berekenen van het proces gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-133">The third command stops the Calc process.</span></span>
<span data-ttu-id="2d697-134">De para meter *input object* wordt gebruikt om het object door te geven om het **proces te stoppen**.</span><span class="sxs-lookup"><span data-stu-id="2d697-134">It uses the *InputObject* parameter to pass the object to **Stop-Process**.</span></span>

<span data-ttu-id="2d697-135">De laatste opdracht haalt alle processen op de computer op die actief waren, maar die nu zijn gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-135">The last command gets all of the processes on the computer that were running but that are now stopped.</span></span>
<span data-ttu-id="2d697-136">Het gebruikt **Get-process** om alle processen op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="2d697-136">It uses **Get-Process** to get all of the processes on the computer.</span></span>
<span data-ttu-id="2d697-137">De pijplijn operator (|) geeft de resultaten door aan de cmdlet Where-Object, die de waarden selecteert waar de eigenschap **HasExited** is $True.</span><span class="sxs-lookup"><span data-stu-id="2d697-137">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the ones where the value of the **HasExited** property is $True.</span></span>
<span data-ttu-id="2d697-138">**HasExited** is slechts één eigenschap van proces objecten.</span><span class="sxs-lookup"><span data-stu-id="2d697-138">**HasExited** is just one property of process objects.</span></span>
<span data-ttu-id="2d697-139">Als u alle eigenschappen wilt zoeken, typt u `Get-Process | Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="2d697-139">To find all the properties, type `Get-Process | Get-Member`.</span></span>

### <span data-ttu-id="2d697-140">Voor beeld 4: een proces stoppen dat niet het eigendom is van de huidige gebruiker</span><span class="sxs-lookup"><span data-stu-id="2d697-140">Example 4: Stop a process not owned by the current user</span></span>

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

<span data-ttu-id="2d697-141">Deze opdrachten tonen het effect van het gebruik van *Force* om een proces te stoppen dat geen eigendom is van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2d697-141">These commands show the effect of using *Force* to stop a process that is not owned by the user.</span></span>

<span data-ttu-id="2d697-142">De eerste opdracht gebruikt **Get-process** om het Lsass-proces op te halen.</span><span class="sxs-lookup"><span data-stu-id="2d697-142">The first command uses **Get-Process** to get the Lsass process.</span></span>
<span data-ttu-id="2d697-143">Een pijplijn operator verzendt het proces om te **stoppen,** om het te stoppen.</span><span class="sxs-lookup"><span data-stu-id="2d697-143">A pipeline operator sends the process to **Stop-Process** to stop it.</span></span>
<span data-ttu-id="2d697-144">Zoals in de voorbeeld uitvoer wordt weer gegeven, mislukt de eerste opdracht met een bericht dat de toegang is geweigerd, omdat dit proces alleen kan worden gestopt door een lid van de groep Administrators op de computer.</span><span class="sxs-lookup"><span data-stu-id="2d697-144">As shown in the sample output, the first command fails with an Access denied message, because this process can be stopped only by a member of the Administrator group on the computer.</span></span>

<span data-ttu-id="2d697-145">Wanneer Power shell wordt geopend met de optie als administrator uitvoeren en de opdracht wordt herhaald, vraagt Power shell u om bevestiging.</span><span class="sxs-lookup"><span data-stu-id="2d697-145">When PowerShell is opened by using the Run as administrator option, and the command is repeated, PowerShell prompts you for confirmation.</span></span>

<span data-ttu-id="2d697-146">Met de tweede opdracht wordt *geforceerd* dat de prompt wordt onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="2d697-146">The second command specifies *Force* to suppress the prompt.</span></span>
<span data-ttu-id="2d697-147">Als gevolg hiervan wordt het proces zonder bevestiging gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-147">As a result, the process is stopped without confirmation.</span></span>

## <span data-ttu-id="2d697-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2d697-148">PARAMETERS</span></span>

### <span data-ttu-id="2d697-149">-Force</span><span class="sxs-lookup"><span data-stu-id="2d697-149">-Force</span></span>

<span data-ttu-id="2d697-150">Hiermee worden de opgegeven processen gestopt zonder dat om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="2d697-150">Stops the specified processes without prompting for confirmation.</span></span>
<span data-ttu-id="2d697-151">Standaard vraagt **het Stop proces** om bevestiging voordat een proces wordt gestopt dat geen eigendom is van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2d697-151">By default, **Stop-Process** prompts for confirmation before stopping any process that is not owned by the current user.</span></span>

<span data-ttu-id="2d697-152">Als u de eigenaar van een proces wilt vinden, gebruikt u de `Get-CimInstance` cmdlet om een **Win32_Process** -object op te halen dat het proces vertegenwoordigt, en gebruikt u vervolgens de methode **GetOwner** van het object.</span><span class="sxs-lookup"><span data-stu-id="2d697-152">To find the owner of a process, use the `Get-CimInstance` cmdlet to get a **Win32_Process** object that represents the process, and then use the **GetOwner** method of the object.</span></span>

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

### <span data-ttu-id="2d697-153">-Id</span><span class="sxs-lookup"><span data-stu-id="2d697-153">-Id</span></span>

<span data-ttu-id="2d697-154">Hiermee geeft u de proces-Id's op van de processen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-154">Specifies the process IDs of the processes to stop.</span></span>
<span data-ttu-id="2d697-155">Als u meerdere Id's wilt opgeven, gebruikt u komma's om de Id's van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="2d697-155">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="2d697-156">Als u de PID van een proces wilt vinden, typt u `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="2d697-156">To find the PID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="2d697-157">-Input object</span><span class="sxs-lookup"><span data-stu-id="2d697-157">-InputObject</span></span>

<span data-ttu-id="2d697-158">Hiermee geeft u de proces objecten op die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-158">Specifies the process objects to stop.</span></span>
<span data-ttu-id="2d697-159">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2d697-159">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="2d697-160">-Name</span><span class="sxs-lookup"><span data-stu-id="2d697-160">-Name</span></span>

<span data-ttu-id="2d697-161">Hiermee geeft u de proces namen op van de processen die moeten worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-161">Specifies the process names of the processes to stop.</span></span>
<span data-ttu-id="2d697-162">U kunt meerdere proces namen typen, gescheiden door komma's of joker tekens gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2d697-162">You can type multiple process names, separated by commas, or use wildcard characters.</span></span>

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

### <span data-ttu-id="2d697-163">-PassThru</span><span class="sxs-lookup"><span data-stu-id="2d697-163">-PassThru</span></span>

<span data-ttu-id="2d697-164">Retourneert een object dat het proces vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="2d697-164">Returns an object that represents the process.</span></span>
<span data-ttu-id="2d697-165">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2d697-165">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="2d697-166">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2d697-166">-Confirm</span></span>

<span data-ttu-id="2d697-167">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2d697-167">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2d697-168">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2d697-168">-WhatIf</span></span>

<span data-ttu-id="2d697-169">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2d697-169">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2d697-170">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2d697-170">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2d697-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2d697-171">CommonParameters</span></span>

<span data-ttu-id="2d697-172">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2d697-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2d697-173">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2d697-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2d697-174">INVOER</span><span class="sxs-lookup"><span data-stu-id="2d697-174">INPUTS</span></span>

### <span data-ttu-id="2d697-175">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="2d697-175">System.Diagnostics.Process</span></span>

<span data-ttu-id="2d697-176">U kunt een proces object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2d697-176">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="2d697-177">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2d697-177">OUTPUTS</span></span>

### <span data-ttu-id="2d697-178">Geen, System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="2d697-178">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="2d697-179">Deze cmdlet retourneert een **System. Diagnostics. process** -object dat het gestopte proces vertegenwoordigt, als u de para meter *PassThru* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="2d697-179">This cmdlet returns a **System.Diagnostics.Process** object that represents the stopped process, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="2d697-180">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2d697-180">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2d697-181">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2d697-181">NOTES</span></span>

* <span data-ttu-id="2d697-182">U kunt ook verwijzen naar **Stop-process** door de ingebouwde aliassen, **Kill** en **spps**.</span><span class="sxs-lookup"><span data-stu-id="2d697-182">You can also refer to **Stop-Process** by its built-in aliases, **kill** and **spps**.</span></span> <span data-ttu-id="2d697-183">Zie about_Aliases voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2d697-183">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="2d697-184">U kunt ook de eigenschappen en methoden van het **Win32_Process** -object Windows Management Instrumentation (WMI) in Windows Power shell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2d697-184">You can also use the properties and methods of the Windows Management Instrumentation (WMI) **Win32_Process** object in Windows PowerShell.</span></span>
<span data-ttu-id="2d697-185">Zie `Get-CimInstance` en de WMI-SDK voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2d697-185">For more information, see `Get-CimInstance` and the WMI SDK.</span></span>

* <span data-ttu-id="2d697-186">Bij het stoppen van processen kan het stoppen van het proces en de services die afhankelijk zijn van het proces, worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="2d697-186">When stopping processes, realize that stopping a process can stop process and services that depend on the process.</span></span>
<span data-ttu-id="2d697-187">In een extreem geval kan Windows stoppen met het stoppen van een proces.</span><span class="sxs-lookup"><span data-stu-id="2d697-187">In an extreme case, stopping a process can stop Windows.</span></span>

## <span data-ttu-id="2d697-188">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2d697-188">RELATED LINKS</span></span>

[<span data-ttu-id="2d697-189">Debug-proces</span><span class="sxs-lookup"><span data-stu-id="2d697-189">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="2d697-190">Get-Process</span><span class="sxs-lookup"><span data-stu-id="2d697-190">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="2d697-191">Start-process</span><span class="sxs-lookup"><span data-stu-id="2d697-191">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="2d697-192">Stoppen-proces</span><span class="sxs-lookup"><span data-stu-id="2d697-192">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="2d697-193">Wacht proces</span><span class="sxs-lookup"><span data-stu-id="2d697-193">Wait-Process</span></span>](Wait-Process.md)
