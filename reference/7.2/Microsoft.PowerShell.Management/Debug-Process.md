---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 660d2b4845df8091ff8b69b28c4e7695af557122
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705741"
---
# <span data-ttu-id="32583-102">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="32583-102">Debug-Process</span></span>

## <span data-ttu-id="32583-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="32583-103">SYNOPSIS</span></span>
<span data-ttu-id="32583-104">De uitvoering van een of meer processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="32583-104">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="32583-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="32583-105">SYNTAX</span></span>

### <span data-ttu-id="32583-106">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="32583-106">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="32583-107">Id</span><span class="sxs-lookup"><span data-stu-id="32583-107">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="32583-108">Input object</span><span class="sxs-lookup"><span data-stu-id="32583-108">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="32583-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="32583-109">DESCRIPTION</span></span>

<span data-ttu-id="32583-110">De `Debug-Process` cmdlet voegt een fout opsporingsprogramma toe aan een of meer actieve processen op een lokale computer.</span><span class="sxs-lookup"><span data-stu-id="32583-110">The `Debug-Process` cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="32583-111">U kunt de processen opgeven op basis van hun proces naam of proces-ID (PID), of u kunt proces objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32583-111">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="32583-112">Met deze cmdlet wordt het fout opsporingsprogramma dat momenteel is geregistreerd voor het proces, gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="32583-112">This cmdlet attaches the debugger that is currently registered for the process.</span></span> <span data-ttu-id="32583-113">Voordat u deze cmdlet kunt gebruiken, moet u controleren of een fout opsporingsprogramma is gedownload en correct is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="32583-113">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="32583-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="32583-114">EXAMPLES</span></span>

### <span data-ttu-id="32583-115">Voor beeld 1: een fout opsporingsprogramma koppelen aan een proces op de computer</span><span class="sxs-lookup"><span data-stu-id="32583-115">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="32583-116">Met deze opdracht koppelt u een fout opsporingsprogramma aan het Power Shell-proces op de computer.</span><span class="sxs-lookup"><span data-stu-id="32583-116">This command attaches a debugger to the PowerShell process on the computer.</span></span>

### <span data-ttu-id="32583-117">Voor beeld 2: een fout opsporingsprogramma koppelen aan alle processen die met de opgegeven teken reeks beginnen</span><span class="sxs-lookup"><span data-stu-id="32583-117">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="32583-118">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan alle processen met namen die met SQL beginnen.</span><span class="sxs-lookup"><span data-stu-id="32583-118">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="32583-119">Voor beeld 3: een fout opsporingsprogramma aan meerdere processen koppelen</span><span class="sxs-lookup"><span data-stu-id="32583-119">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="32583-120">Met deze opdracht koppelt u een fout opsporingsprogramma aan de Winlogon-, Explorer-en Outlook-processen.</span><span class="sxs-lookup"><span data-stu-id="32583-120">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="32583-121">Voor beeld 4: een fout opsporingsprogramma koppelen aan meerdere proces-Id's</span><span class="sxs-lookup"><span data-stu-id="32583-121">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="32583-122">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de processen met proces-id 1132 en 2028.</span><span class="sxs-lookup"><span data-stu-id="32583-122">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="32583-123">Voor beeld 5: Get-Process gebruiken om een proces te verkrijgen en vervolgens een fout opsporingsprogramma aan toe te voegen</span><span class="sxs-lookup"><span data-stu-id="32583-123">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="32583-124">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de Power shell-processen op de computer.</span><span class="sxs-lookup"><span data-stu-id="32583-124">This command attaches a debugger to the PowerShell processes on the computer.</span></span> <span data-ttu-id="32583-125">De cmdlet wordt gebruikt `Get-Process` om de Power shell-processen op de computer op te halen en maakt gebruik van een pijplijn operator ( `|` ) om de processen naar de cmdlet te verzenden `Debug-Process` .</span><span class="sxs-lookup"><span data-stu-id="32583-125">It uses the `Get-Process` cmdlet to get the PowerShell processes on the computer, and it uses a pipeline operator (`|`) to send the processes to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="32583-126">Als u een bepaald Power Shell-proces wilt opgeven, gebruikt u de para meter ID van `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="32583-126">To specify a particular PowerShell process, use the ID parameter of `Get-Process`.</span></span>

### <span data-ttu-id="32583-127">Voor beeld 6: een fout opsporingsprogramma koppelen aan een huidig proces op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="32583-127">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="32583-128">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de huidige Power shell-processen op de computer.</span><span class="sxs-lookup"><span data-stu-id="32583-128">This command attaches a debugger to the current PowerShell processes on the computer.</span></span>

<span data-ttu-id="32583-129">De opdracht maakt gebruik `$PID` van de automatische variabele, die de proces-id van het huidige Power Shell-proces bevat.</span><span class="sxs-lookup"><span data-stu-id="32583-129">The command uses the `$PID` automatic variable, which contains the process ID of the current PowerShell process.</span></span> <span data-ttu-id="32583-130">Vervolgens wordt een pijplijn operator ( `|` ) gebruikt om de proces-id naar de cmdlet te verzenden `Debug-Process` .</span><span class="sxs-lookup"><span data-stu-id="32583-130">Then, it uses a pipeline operator (`|`) to send the process ID to the `Debug-Process` cmdlet.</span></span>

<span data-ttu-id="32583-131">Zie about_Automatic_Variables voor meer informatie over de `$PID` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="32583-131">For more information about the `$PID` automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="32583-132">Voor beeld 7: een fout opsporingsprogramma koppelen aan een proces dat gebruikmaakt van de para meter input object</span><span class="sxs-lookup"><span data-stu-id="32583-132">Example 7: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="32583-133">Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de Power shell-processen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="32583-133">This command attaches a debugger to the PowerShell processes on the local computer.</span></span>

<span data-ttu-id="32583-134">De eerste opdracht gebruikt de `Get-Process` cmdlet om de Power shell-processen op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="32583-134">The first command uses the `Get-Process` cmdlet to get the PowerShell processes on the computer.</span></span> <span data-ttu-id="32583-135">Het resulterende proces object wordt opgeslagen in de variabele met de naam `$P` .</span><span class="sxs-lookup"><span data-stu-id="32583-135">It saves the resulting process object in the variable named `$P`.</span></span>

<span data-ttu-id="32583-136">De tweede opdracht maakt gebruik van de para meter **input object** van de `Debug-Process` cmdlet om het proces object in de variabele in te dienen `$P` .</span><span class="sxs-lookup"><span data-stu-id="32583-136">The second command uses the **InputObject** parameter of the `Debug-Process` cmdlet to submit the process object in the `$P` variable.</span></span>

## <span data-ttu-id="32583-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32583-137">PARAMETERS</span></span>

### <span data-ttu-id="32583-138">-Id</span><span class="sxs-lookup"><span data-stu-id="32583-138">-Id</span></span>

<span data-ttu-id="32583-139">Hiermee geeft u de proces-Id's op van de processen waarvoor u fouten wilt opsporen.</span><span class="sxs-lookup"><span data-stu-id="32583-139">Specifies the process IDs of the processes to be debugged.</span></span> <span data-ttu-id="32583-140">De **id-** parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="32583-140">The **Id** parameter name is optional.</span></span>

<span data-ttu-id="32583-141">Als u de proces-ID van een proces wilt zoeken, typt u `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="32583-141">To find the process ID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="32583-142">-Input object</span><span class="sxs-lookup"><span data-stu-id="32583-142">-InputObject</span></span>

<span data-ttu-id="32583-143">Hiermee geeft u de proces objecten op die processen vertegenwoordigen waarvoor fouten worden opgespoord.</span><span class="sxs-lookup"><span data-stu-id="32583-143">Specifies the process objects that represent processes to be debugged.</span></span> <span data-ttu-id="32583-144">Voer een variabele in die de proces objecten bevat of een opdracht die de proces objecten, zoals de- `Get-Process` cmdlet, ophalen.</span><span class="sxs-lookup"><span data-stu-id="32583-144">Enter a variable that contains the process objects or a command that gets the process objects, such as the `Get-Process` cmdlet.</span></span> <span data-ttu-id="32583-145">U kunt ook proces objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="32583-145">You can also pipe process objects to this cmdlet.</span></span>

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

### <span data-ttu-id="32583-146">-Name</span><span class="sxs-lookup"><span data-stu-id="32583-146">-Name</span></span>

<span data-ttu-id="32583-147">Hiermee geeft u de namen van de processen waarvoor u fouten wilt opsporen.</span><span class="sxs-lookup"><span data-stu-id="32583-147">Specifies the names of the processes to be debugged.</span></span> <span data-ttu-id="32583-148">Als er meer dan één proces met dezelfde naam is, voegt deze cmdlet een fout opsporingsprogramma toe aan alle processen met die naam.</span><span class="sxs-lookup"><span data-stu-id="32583-148">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span> <span data-ttu-id="32583-149">De para meter **name** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="32583-149">The **Name** parameter is optional.</span></span>

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

### <span data-ttu-id="32583-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="32583-150">-Confirm</span></span>

<span data-ttu-id="32583-151">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="32583-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="32583-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="32583-152">-WhatIf</span></span>

<span data-ttu-id="32583-153">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="32583-153">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="32583-154">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32583-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="32583-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32583-155">CommonParameters</span></span>

<span data-ttu-id="32583-156">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32583-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32583-157">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="32583-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="32583-158">INVOER</span><span class="sxs-lookup"><span data-stu-id="32583-158">INPUTS</span></span>

### <span data-ttu-id="32583-159">System. Int32, System. Diagnostics. proces, System. String</span><span class="sxs-lookup"><span data-stu-id="32583-159">System.Int32, System.Diagnostics.Process, System.String</span></span>

<span data-ttu-id="32583-160">U kunt een proces-ID (INT32), een proces object (System. Diagnostics. process) of een proces naam (teken reeks) door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32583-160">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="32583-161">UITVOER</span><span class="sxs-lookup"><span data-stu-id="32583-161">OUTPUTS</span></span>

### <span data-ttu-id="32583-162">Geen</span><span class="sxs-lookup"><span data-stu-id="32583-162">None</span></span>

<span data-ttu-id="32583-163">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="32583-163">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="32583-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="32583-164">NOTES</span></span>

<span data-ttu-id="32583-165">Deze cmdlet maakt gebruik van de methode AttachDebugger van de klasse Windows Management Instrumentation (WMI) Win32_Process.</span><span class="sxs-lookup"><span data-stu-id="32583-165">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="32583-166">Zie [AttachDebugger-methode](https://go.microsoft.com/fwlink/?LinkId=143640) in de MSDN-bibliotheek voor meer informatie over deze methode.</span><span class="sxs-lookup"><span data-stu-id="32583-166">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="32583-167">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="32583-167">RELATED LINKS</span></span>

[<span data-ttu-id="32583-168">Debug-proces</span><span class="sxs-lookup"><span data-stu-id="32583-168">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="32583-169">Get-Process</span><span class="sxs-lookup"><span data-stu-id="32583-169">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="32583-170">Start-process</span><span class="sxs-lookup"><span data-stu-id="32583-170">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="32583-171">Stoppen-proces</span><span class="sxs-lookup"><span data-stu-id="32583-171">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="32583-172">Wacht proces</span><span class="sxs-lookup"><span data-stu-id="32583-172">Wait-Process</span></span>](Wait-Process.md)
