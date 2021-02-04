---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: c469a4e9cf17b03a33bc8b9ff9b06aa95773fc02
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705723"
---
# <span data-ttu-id="75477-102">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="75477-102">Wait-Process</span></span>

## <span data-ttu-id="75477-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="75477-103">SYNOPSIS</span></span>
<span data-ttu-id="75477-104">Er wordt gewacht tot de processen zijn gestopt voordat meer invoer wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="75477-104">Waits for the processes to be stopped before accepting more input.</span></span>

## <span data-ttu-id="75477-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="75477-105">SYNTAX</span></span>

### <span data-ttu-id="75477-106">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="75477-106">Name (Default)</span></span>

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="75477-107">Id</span><span class="sxs-lookup"><span data-stu-id="75477-107">Id</span></span>

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="75477-108">Input object</span><span class="sxs-lookup"><span data-stu-id="75477-108">InputObject</span></span>

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## <span data-ttu-id="75477-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="75477-109">DESCRIPTION</span></span>

<span data-ttu-id="75477-110">De **wacht-process-** cmdlet wacht totdat een of meer actieve processen worden gestopt voordat de invoer wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="75477-110">The **Wait-Process** cmdlet waits for one or more running processes to be stopped before accepting input.</span></span>
<span data-ttu-id="75477-111">In de Power shell-console onderdrukt deze cmdlet de opdracht prompt totdat de processen zijn gestopt.</span><span class="sxs-lookup"><span data-stu-id="75477-111">In the PowerShell console, this cmdlet suppresses the command prompt until the processes are stopped.</span></span>
<span data-ttu-id="75477-112">U kunt een proces naam of proces-ID (PID) opgeven, of een proces object pipeen dat moet worden **gewacht**.</span><span class="sxs-lookup"><span data-stu-id="75477-112">You can specify a process by process name or process ID (PID), or pipe a process object to **Wait-Process**.</span></span>

<span data-ttu-id="75477-113">Een **ogen blik geduld,** werkt alleen voor processen die worden uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="75477-113">**Wait-Process** works only on processes running on the local computer.</span></span>

## <span data-ttu-id="75477-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="75477-114">EXAMPLES</span></span>

### <span data-ttu-id="75477-115">Voor beeld 1: een proces stoppen en wachten</span><span class="sxs-lookup"><span data-stu-id="75477-115">Example 1: Stop a process and wait</span></span>

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

<span data-ttu-id="75477-116">In dit voor beeld wordt het klad blok-proces gestopt en wordt gewacht tot het proces wordt gestopt voordat de volgende opdracht wordt voortgezet.</span><span class="sxs-lookup"><span data-stu-id="75477-116">This example stops the Notepad process and then waits for the process to be stopped before it continues with the next command.</span></span>

<span data-ttu-id="75477-117">De eerste opdracht maakt gebruik van de cmdlet **Get-process** om de id van het klad blok-proces op te halen.</span><span class="sxs-lookup"><span data-stu-id="75477-117">The first command uses the **Get-Process** cmdlet to get the ID of the Notepad process.</span></span>
<span data-ttu-id="75477-118">De ID wordt opgeslagen in de variabele $nid.</span><span class="sxs-lookup"><span data-stu-id="75477-118">It stores the ID in the $nid variable.</span></span>

<span data-ttu-id="75477-119">De tweede opdracht gebruikt de cmdlet Stop-Process om het proces te stoppen met de ID die is opgeslagen in $nid.</span><span class="sxs-lookup"><span data-stu-id="75477-119">The second command uses the Stop-Process cmdlet to stop the process with the ID stored in $nid.</span></span>

<span data-ttu-id="75477-120">De derde opdracht gebruikt **wacht proces** om te wachten tot het klad blok-proces is gestopt.</span><span class="sxs-lookup"><span data-stu-id="75477-120">The third command uses **Wait-Process** to wait until the Notepad process is stopped.</span></span>
<span data-ttu-id="75477-121">De para meter *id* van **wacht proces** wordt gebruikt om het proces te identificeren.</span><span class="sxs-lookup"><span data-stu-id="75477-121">It uses the *Id* parameter of **Wait-Process** to identify the process.</span></span>

### <span data-ttu-id="75477-122">Voor beeld 2: een proces opgeven</span><span class="sxs-lookup"><span data-stu-id="75477-122">Example 2: Specifying a process</span></span>

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

<span data-ttu-id="75477-123">Met deze opdrachten worden drie verschillende methoden weer gegeven voor het opgeven van een proces dat moet worden **gewacht**.</span><span class="sxs-lookup"><span data-stu-id="75477-123">These commands show three different methods of specifying a process to **Wait-Process**.</span></span>
<span data-ttu-id="75477-124">Met de eerste opdracht wordt het klad blok-proces opgehaald en opgeslagen in de variabele $p.</span><span class="sxs-lookup"><span data-stu-id="75477-124">The first command gets the Notepad process and stores it in the $p variable.</span></span>

<span data-ttu-id="75477-125">De tweede opdracht gebruikt de *id-* para meter, de derde opdracht gebruikt de para meter *name* en de vierde opdracht maakt gebruik van de para meter *input object* .</span><span class="sxs-lookup"><span data-stu-id="75477-125">The second command uses the *Id* parameter, the third command uses the *Name* parameter, and the fourth command uses the *InputObject* parameter.</span></span>

<span data-ttu-id="75477-126">Deze opdrachten hebben dezelfde resultaten en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="75477-126">These commands have the same results and can be used interchangeably.</span></span>

### <span data-ttu-id="75477-127">Voor beeld 3: wachten op processen gedurende een opgegeven periode</span><span class="sxs-lookup"><span data-stu-id="75477-127">Example 3: Wait for processes for a specified time</span></span>

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

<span data-ttu-id="75477-128">Met deze opdracht wordt 30 seconden gewacht totdat de processen van Outlook en Winword worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="75477-128">This command waits 30 seconds for the Outlook and Winword processes to stop.</span></span>
<span data-ttu-id="75477-129">Als beide processen niet worden gestopt, wordt in de cmdlet een niet-afsluit fout weer gegeven en de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="75477-129">If both processes are not stopped, the cmdlet displays a non-terminating error and the command prompt.</span></span>

## <span data-ttu-id="75477-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="75477-130">PARAMETERS</span></span>

### <span data-ttu-id="75477-131">-Id</span><span class="sxs-lookup"><span data-stu-id="75477-131">-Id</span></span>

<span data-ttu-id="75477-132">Hiermee geeft u de proces-Id's van de processen.</span><span class="sxs-lookup"><span data-stu-id="75477-132">Specifies the process IDs of the processes.</span></span>
<span data-ttu-id="75477-133">Als u meerdere Id's wilt opgeven, gebruikt u komma's om de Id's van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="75477-133">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="75477-134">Als u de PID van een proces wilt vinden, typt u `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="75477-134">To find the PID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="75477-135">-Input object</span><span class="sxs-lookup"><span data-stu-id="75477-135">-InputObject</span></span>

<span data-ttu-id="75477-136">Hiermee geeft u de processen aan door proces objecten te verzenden.</span><span class="sxs-lookup"><span data-stu-id="75477-136">Specifies the processes by submitting process objects.</span></span>
<span data-ttu-id="75477-137">Voer een variabele in die de proces objecten bevat, of typ een opdracht of expressie waarmee de proces objecten worden opgehaald, zoals de cmdlet Get-Process.</span><span class="sxs-lookup"><span data-stu-id="75477-137">Enter a variable that contains the process objects, or type a command or expression that gets the process objects, such as the Get-Process cmdlet.</span></span>

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

### <span data-ttu-id="75477-138">-Name</span><span class="sxs-lookup"><span data-stu-id="75477-138">-Name</span></span>

<span data-ttu-id="75477-139">Hiermee geeft u de proces namen van de processen.</span><span class="sxs-lookup"><span data-stu-id="75477-139">Specifies the process names of the processes.</span></span>
<span data-ttu-id="75477-140">Als u meerdere namen wilt opgeven, gebruikt u komma's om de namen van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="75477-140">To specify multiple names, use commas to separate the names.</span></span>
<span data-ttu-id="75477-141">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="75477-141">Wildcard characters are not supported.</span></span>

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

### <span data-ttu-id="75477-142">-Time-out</span><span class="sxs-lookup"><span data-stu-id="75477-142">-Timeout</span></span>

<span data-ttu-id="75477-143">Hiermee geeft u de maximum tijd, in seconden, op dat met deze cmdlet wordt gewacht tot de opgegeven processen worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="75477-143">Specifies the maximum time, in seconds, that this cmdlet waits for the specified processes to stop.</span></span>
<span data-ttu-id="75477-144">Als dit interval is verlopen, wordt de opdracht weer gegeven met een niet-afsluit fout die de processen vermeld die nog worden uitgevoerd, en eindigt de wacht tijd.</span><span class="sxs-lookup"><span data-stu-id="75477-144">When this interval expires, the command displays a non-terminating error that lists the processes that are still running, and ends the wait.</span></span>
<span data-ttu-id="75477-145">Standaard is er geen time-out.</span><span class="sxs-lookup"><span data-stu-id="75477-145">By default, there is no time-out.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75477-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75477-146">CommonParameters</span></span>

<span data-ttu-id="75477-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75477-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75477-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75477-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75477-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="75477-149">INPUTS</span></span>

### <span data-ttu-id="75477-150">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="75477-150">System.Diagnostics.Process</span></span>

<span data-ttu-id="75477-151">U kunt een proces object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="75477-151">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="75477-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="75477-152">OUTPUTS</span></span>

### <span data-ttu-id="75477-153">Geen</span><span class="sxs-lookup"><span data-stu-id="75477-153">None</span></span>

<span data-ttu-id="75477-154">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="75477-154">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="75477-155">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="75477-155">NOTES</span></span>

<span data-ttu-id="75477-156">De cmdlet wordt alleen ondersteund op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="75477-156">The cmdlet is only supported on Windows platforms.</span></span>

<span data-ttu-id="75477-157">Deze cmdlet maakt gebruik van de methode **WaitForExit** van de klasse **System. Diagnostics. process** .</span><span class="sxs-lookup"><span data-stu-id="75477-157">This cmdlet uses the **WaitForExit** method of the **System.Diagnostics.Process** class.</span></span>

## <span data-ttu-id="75477-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="75477-158">RELATED LINKS</span></span>

[<span data-ttu-id="75477-159">Debug-proces</span><span class="sxs-lookup"><span data-stu-id="75477-159">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="75477-160">Get-Process</span><span class="sxs-lookup"><span data-stu-id="75477-160">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="75477-161">Start-process</span><span class="sxs-lookup"><span data-stu-id="75477-161">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="75477-162">Stoppen-proces</span><span class="sxs-lookup"><span data-stu-id="75477-162">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="75477-163">Wacht proces</span><span class="sxs-lookup"><span data-stu-id="75477-163">Wait-Process</span></span>](Wait-Process.md)