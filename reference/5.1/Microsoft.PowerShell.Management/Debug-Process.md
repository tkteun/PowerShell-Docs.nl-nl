---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 98bd72901339d040748fc0d99b14bc1404ea1465
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388311"
---
# <span data-ttu-id="c5622-103">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="c5622-103">Debug-Process</span></span>

## <span data-ttu-id="c5622-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c5622-104">SYNOPSIS</span></span>
<span data-ttu-id="c5622-105">De uitvoering van een of meer processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c5622-105">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="c5622-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c5622-106">SYNTAX</span></span>

### <span data-ttu-id="c5622-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="c5622-107">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c5622-108">Id</span><span class="sxs-lookup"><span data-stu-id="c5622-108">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c5622-109">Input object</span><span class="sxs-lookup"><span data-stu-id="c5622-109">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c5622-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c5622-110">DESCRIPTION</span></span>

<span data-ttu-id="c5622-111">De `Debug-Process` cmdlet voegt een fout opsporingsprogramma toe aan een of meer actieve processen op een lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c5622-111">The `Debug-Process` cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="c5622-112">U kunt de processen opgeven op basis van hun proces naam of proces-ID (PID), of u kunt proces objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5622-112">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="c5622-113">Met deze cmdlet wordt het fout opsporingsprogramma dat momenteel is geregistreerd voor het proces, gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="c5622-113">This cmdlet attaches the debugger that is currently registered for the process.</span></span> <span data-ttu-id="c5622-114">Voordat u deze cmdlet kunt gebruiken, moet u controleren of een fout opsporingsprogramma is gedownload en correct is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="c5622-114">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="c5622-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c5622-115">EXAMPLES</span></span>

### <span data-ttu-id="c5622-116">Voor beeld 1: een fout opsporingsprogramma koppelen aan een proces op de computer</span><span class="sxs-lookup"><span data-stu-id="c5622-116">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="c5622-117">Met deze opdracht koppelt u een fout opsporingsprogramma aan het Power Shell-proces op de computer.</span><span class="sxs-lookup"><span data-stu-id="c5622-117">This command attaches a debugger to the PowerShell process on the computer.</span></span>

### <span data-ttu-id="c5622-118">Voor beeld 2: een fout opsporingsprogramma koppelen aan alle processen die met de opgegeven teken reeks beginnen</span><span class="sxs-lookup"><span data-stu-id="c5622-118">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="c5622-119">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan alle processen met namen die met SQL beginnen.</span><span class="sxs-lookup"><span data-stu-id="c5622-119">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="c5622-120">Voor beeld 3: een fout opsporingsprogramma aan meerdere processen koppelen</span><span class="sxs-lookup"><span data-stu-id="c5622-120">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="c5622-121">Met deze opdracht koppelt u een fout opsporingsprogramma aan de Winlogon-, Explorer-en Outlook-processen.</span><span class="sxs-lookup"><span data-stu-id="c5622-121">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="c5622-122">Voor beeld 4: een fout opsporingsprogramma koppelen aan meerdere proces-Id's</span><span class="sxs-lookup"><span data-stu-id="c5622-122">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="c5622-123">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de processen met proces-id 1132 en 2028.</span><span class="sxs-lookup"><span data-stu-id="c5622-123">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="c5622-124">Voor beeld 5: Get-Process gebruiken om een proces te verkrijgen en vervolgens een fout opsporingsprogramma aan toe te voegen</span><span class="sxs-lookup"><span data-stu-id="c5622-124">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="c5622-125">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de Power shell-processen op de computer.</span><span class="sxs-lookup"><span data-stu-id="c5622-125">This command attaches a debugger to the PowerShell processes on the computer.</span></span> <span data-ttu-id="c5622-126">De cmdlet wordt gebruikt `Get-Process` om de Power shell-processen op de computer op te halen en maakt gebruik van een pijplijn operator ( `|` ) om de processen naar de cmdlet te verzenden `Debug-Process` .</span><span class="sxs-lookup"><span data-stu-id="c5622-126">It uses the `Get-Process` cmdlet to get the PowerShell processes on the computer, and it uses a pipeline operator (`|`) to send the processes to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="c5622-127">Als u een bepaald Power Shell-proces wilt opgeven, gebruikt u de para meter ID van `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="c5622-127">To specify a particular PowerShell process, use the ID parameter of `Get-Process`.</span></span>

### <span data-ttu-id="c5622-128">Voor beeld 6: een fout opsporingsprogramma koppelen aan een huidig proces op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="c5622-128">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="c5622-129">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de huidige Power shell-processen op de computer.</span><span class="sxs-lookup"><span data-stu-id="c5622-129">This command attaches a debugger to the current PowerShell processes on the computer.</span></span>

<span data-ttu-id="c5622-130">De opdracht maakt gebruik `$PID` van de automatische variabele, die de proces-id van het huidige Power Shell-proces bevat.</span><span class="sxs-lookup"><span data-stu-id="c5622-130">The command uses the `$PID` automatic variable, which contains the process ID of the current PowerShell process.</span></span> <span data-ttu-id="c5622-131">Vervolgens wordt een pijplijn operator ( `|` ) gebruikt om de proces-id naar de cmdlet te verzenden `Debug-Process` .</span><span class="sxs-lookup"><span data-stu-id="c5622-131">Then, it uses a pipeline operator (`|`) to send the process ID to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="c5622-132">Zie about_Automatic_Variables voor meer informatie over de `$PID` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="c5622-132">For more information about the `$PID` automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="c5622-133">Voor beeld 7: een fout opsporingsprogramma koppelen aan het opgegeven proces op meerdere computers</span><span class="sxs-lookup"><span data-stu-id="c5622-133">Example 7: Attach a debugger to the specified process on multiple computers</span></span>

```
PS C:\> Get-Process -ComputerName "Server01", "Server02" -Name "MyApp" | Debug-Process
```

<span data-ttu-id="c5622-134">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de Mijntoep-processen op de Server01-en Server02-computers.</span><span class="sxs-lookup"><span data-stu-id="c5622-134">This command attaches a debugger to the MyApp processes on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="c5622-135">De opdracht gebruikt de `Get-Process` cmdlet om de Mijntoep-processen op de Server01-en Server02-computers op te halen.</span><span class="sxs-lookup"><span data-stu-id="c5622-135">The command uses the `Get-Process` cmdlet to get the MyApp processes on the Server01 and Server02 computers.</span></span> <span data-ttu-id="c5622-136">Er wordt een pijplijn operator gebruikt voor het verzenden van de processen naar de `Debug-Process` cmdlet, waarmee de debuggers worden gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="c5622-136">It uses a pipeline operator to send the processes to the `Debug-Process` cmdlet, which attaches the debuggers.</span></span>

### <span data-ttu-id="c5622-137">Voor beeld 8: een fout opsporingsprogramma koppelen aan een proces dat gebruikmaakt van de para meter input object</span><span class="sxs-lookup"><span data-stu-id="c5622-137">Example 8: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="c5622-138">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de Power shell-processen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c5622-138">This command attaches a debugger to the PowerShell processes on the local computer.</span></span>

<span data-ttu-id="c5622-139">De eerste opdracht gebruikt de `Get-Process` cmdlet om de Power shell-processen op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="c5622-139">The first command uses the `Get-Process` cmdlet to get the PowerShell processes on the computer.</span></span> <span data-ttu-id="c5622-140">Het resulterende proces object wordt opgeslagen in de variabele met de naam `$P` .</span><span class="sxs-lookup"><span data-stu-id="c5622-140">It saves the resulting process object in the variable named `$P`.</span></span>

<span data-ttu-id="c5622-141">De tweede opdracht maakt gebruik van de para meter **input object** van de `Debug-Process` cmdlet om het proces object in de variabele in te dienen `$P` .</span><span class="sxs-lookup"><span data-stu-id="c5622-141">The second command uses the **InputObject** parameter of the `Debug-Process` cmdlet to submit the process object in the `$P` variable.</span></span>

## <span data-ttu-id="c5622-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c5622-142">PARAMETERS</span></span>

### <span data-ttu-id="c5622-143">-Id</span><span class="sxs-lookup"><span data-stu-id="c5622-143">-Id</span></span>

<span data-ttu-id="c5622-144">Hiermee geeft u de proces-Id's op van de processen waarvoor u fouten wilt opsporen.</span><span class="sxs-lookup"><span data-stu-id="c5622-144">Specifies the process IDs of the processes to be debugged.</span></span> <span data-ttu-id="c5622-145">De **id-** parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="c5622-145">The **Id** parameter name is optional.</span></span>

<span data-ttu-id="c5622-146">Als u de proces-ID van een proces wilt zoeken, typt u `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="c5622-146">To find the process ID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c5622-147">-Input object</span><span class="sxs-lookup"><span data-stu-id="c5622-147">-InputObject</span></span>

<span data-ttu-id="c5622-148">Hiermee geeft u de proces objecten op die processen vertegenwoordigen waarvoor fouten worden opgespoord.</span><span class="sxs-lookup"><span data-stu-id="c5622-148">Specifies the process objects that represent processes to be debugged.</span></span> <span data-ttu-id="c5622-149">Voer een variabele in die de proces objecten bevat of een opdracht die de proces objecten, zoals de- `Get-Process` cmdlet, ophalen.</span><span class="sxs-lookup"><span data-stu-id="c5622-149">Enter a variable that contains the process objects or a command that gets the process objects, such as the `Get-Process` cmdlet.</span></span> <span data-ttu-id="c5622-150">U kunt ook proces objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="c5622-150">You can also pipe process objects to this cmdlet.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c5622-151">-Name</span><span class="sxs-lookup"><span data-stu-id="c5622-151">-Name</span></span>

<span data-ttu-id="c5622-152">Hiermee geeft u de namen van de processen waarvoor u fouten wilt opsporen.</span><span class="sxs-lookup"><span data-stu-id="c5622-152">Specifies the names of the processes to be debugged.</span></span> <span data-ttu-id="c5622-153">Als er meer dan één proces met dezelfde naam is, voegt deze cmdlet een fout opsporingsprogramma toe aan alle processen met die naam.</span><span class="sxs-lookup"><span data-stu-id="c5622-153">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span> <span data-ttu-id="c5622-154">De para meter **name** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="c5622-154">The **Name** parameter is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c5622-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c5622-155">-Confirm</span></span>

<span data-ttu-id="c5622-156">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c5622-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c5622-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c5622-157">-WhatIf</span></span>

<span data-ttu-id="c5622-158">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c5622-158">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="c5622-159">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c5622-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c5622-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c5622-160">CommonParameters</span></span>

<span data-ttu-id="c5622-161">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c5622-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c5622-162">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c5622-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c5622-163">INVOER</span><span class="sxs-lookup"><span data-stu-id="c5622-163">INPUTS</span></span>

### <span data-ttu-id="c5622-164">System. Int32, System. Diagnostics. proces, System. String</span><span class="sxs-lookup"><span data-stu-id="c5622-164">System.Int32, System.Diagnostics.Process, System.String</span></span>

<span data-ttu-id="c5622-165">U kunt een proces-ID (INT32), een proces object (System. Diagnostics. process) of een proces naam (teken reeks) door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5622-165">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="c5622-166">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c5622-166">OUTPUTS</span></span>

### <span data-ttu-id="c5622-167">Geen</span><span class="sxs-lookup"><span data-stu-id="c5622-167">None</span></span>

<span data-ttu-id="c5622-168">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c5622-168">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c5622-169">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c5622-169">NOTES</span></span>

<span data-ttu-id="c5622-170">Deze cmdlet maakt gebruik van de methode AttachDebugger van de klasse Windows Management Instrumentation (WMI) Win32_Process.</span><span class="sxs-lookup"><span data-stu-id="c5622-170">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="c5622-171">Zie [AttachDebugger-methode](https://go.microsoft.com/fwlink/?LinkId=143640) in de MSDN-bibliotheek voor meer informatie over deze methode.</span><span class="sxs-lookup"><span data-stu-id="c5622-171">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="c5622-172">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c5622-172">RELATED LINKS</span></span>

[<span data-ttu-id="c5622-173">Debug-proces</span><span class="sxs-lookup"><span data-stu-id="c5622-173">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="c5622-174">Get-Process</span><span class="sxs-lookup"><span data-stu-id="c5622-174">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="c5622-175">Start-process</span><span class="sxs-lookup"><span data-stu-id="c5622-175">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="c5622-176">Stoppen-proces</span><span class="sxs-lookup"><span data-stu-id="c5622-176">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="c5622-177">Wacht proces</span><span class="sxs-lookup"><span data-stu-id="c5622-177">Wait-Process</span></span>](Wait-Process.md)
