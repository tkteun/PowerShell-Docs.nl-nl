---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250811"
---
# <span data-ttu-id="cf4e7-103">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="cf4e7-103">Get-ComputerRestorePoint</span></span>

## <span data-ttu-id="cf4e7-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cf4e7-104">SYNOPSIS</span></span>
<span data-ttu-id="cf4e7-105">Hiermee worden de herstel punten op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-105">Gets the restore points on the local computer.</span></span>

## <span data-ttu-id="cf4e7-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cf4e7-106">SYNTAX</span></span>

### <span data-ttu-id="cf4e7-107">ID (standaard)</span><span class="sxs-lookup"><span data-stu-id="cf4e7-107">ID (Default)</span></span>

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="cf4e7-108">LastStatus</span><span class="sxs-lookup"><span data-stu-id="cf4e7-108">LastStatus</span></span>

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## <span data-ttu-id="cf4e7-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cf4e7-109">DESCRIPTION</span></span>

<span data-ttu-id="cf4e7-110">De `Get-ComputerRestorePoint` cmdlet haalt de systeem herstel punten van de lokale computer op.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-110">The `Get-ComputerRestorePoint` cmdlet gets the local computer's system restore points.</span></span> <span data-ttu-id="cf4e7-111">En kan de status van de meest recente poging voor het herstellen van de computer weer geven.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-111">And, it can display the status of the most recent attempt to restore the computer.</span></span>

<span data-ttu-id="cf4e7-112">U kunt de informatie uit gebruiken `Get-ComputerRestorePoint` om een herstel punt te selecteren.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-112">You can use the information from `Get-ComputerRestorePoint` to select a restore point.</span></span> <span data-ttu-id="cf4e7-113">Gebruik bijvoorbeeld een Volg nummer om een herstel punt voor de cmdlet te identificeren `Restore-Computer` .</span><span class="sxs-lookup"><span data-stu-id="cf4e7-113">For example, use a sequence number to identify a restore point for the `Restore-Computer` cmdlet.</span></span>

<span data-ttu-id="cf4e7-114">Systeem herstel punten en de `Get-ComputerRestorePoint` cmdlet worden alleen ondersteund op client besturingssystemen zoals Windows 10, Windows 7, Windows Vista en Windows XP.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-114">System restore points and the `Get-ComputerRestorePoint` cmdlet are supported only on client operating systems such as Windows 10, Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="cf4e7-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cf4e7-115">EXAMPLES</span></span>

### <span data-ttu-id="cf4e7-116">Voor beeld 1: alle systeem herstel punten ophalen</span><span class="sxs-lookup"><span data-stu-id="cf4e7-116">Example 1: Get all system restore points</span></span>

<span data-ttu-id="cf4e7-117">In dit voor beeld worden `Get-ComputerRestorePoint` alle systeem herstel punten van de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-117">In this example, `Get-ComputerRestorePoint` gets all the local computer's system restore points.</span></span>

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### <span data-ttu-id="cf4e7-118">Voor beeld 2: specifieke Volg nummers ophalen</span><span class="sxs-lookup"><span data-stu-id="cf4e7-118">Example 2: Get specific sequence numbers</span></span>

<span data-ttu-id="cf4e7-119">In dit voor beeld worden systeem herstel punten voor specifieke Volg nummers opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-119">This example gets system restore points for specific sequence numbers.</span></span>

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

<span data-ttu-id="cf4e7-120">`Get-ComputerRestorePoint` maakt gebruik van de para meter **RestorePoint** om een door komma's gescheiden matrix met Volg nummers op te geven.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-120">`Get-ComputerRestorePoint` uses the **RestorePoint** parameter to specify a comma-separated array of sequence numbers.</span></span>

### <span data-ttu-id="cf4e7-121">Voor beeld 3: de status van een systeem herstel weer geven</span><span class="sxs-lookup"><span data-stu-id="cf4e7-121">Example 3: Display the status of a system restore</span></span>

<span data-ttu-id="cf4e7-122">In dit voor beeld wordt de status van de meest recente systeem herstel op de lokale computer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-122">This example displays the status of the most recent system restore on the local computer.</span></span>

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

<span data-ttu-id="cf4e7-123">`Get-ComputerRestorePoint` maakt gebruik van de para meter **LastStatus** om het resultaat van de meest recente systeem herstel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-123">`Get-ComputerRestorePoint` uses the **LastStatus** parameter to display the result of the most recent system restore.</span></span>

### <span data-ttu-id="cf4e7-124">Voor beeld 4: een expressie gebruiken om de CreationTime te converteren</span><span class="sxs-lookup"><span data-stu-id="cf4e7-124">Example 4: Use an expression to convert the CreationTime</span></span>

<span data-ttu-id="cf4e7-125">`Get-ComputerRestorePoint` Hiermee wordt de **CreationTime** uitgevoerd als een datum-en tijd teken reeks van het Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="cf4e7-125">`Get-ComputerRestorePoint` outputs the **CreationTime** as a Windows Management Instrumentation (WMI) date and time string.</span></span>

<span data-ttu-id="cf4e7-126">In dit voor beeld slaat een variabele een expressie op die de **CreationTime** -teken reeks converteert naar een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-126">In this example, a variable stores an expression that converts the **CreationTime** string to a **DateTime** object.</span></span> <span data-ttu-id="cf4e7-127">Als u **CreationTime** -teken reeksen wilt bekijken voordat ze worden geconverteerd, gebruikt u een opdracht zoals `((Get-ComputerRestorePoint).CreationTime)` .</span><span class="sxs-lookup"><span data-stu-id="cf4e7-127">To view **CreationTime** strings before they're converted, use a command such as `((Get-ComputerRestorePoint).CreationTime)`.</span></span> <span data-ttu-id="cf4e7-128">Zie [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime)voor meer informatie over de datum en tijd van de WMI-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-128">For more information about the WMI date and time string, see [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime).</span></span>

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

<span data-ttu-id="cf4e7-129">De `$date` variabele bevat een hash-tabel met de expressie die gebruikmaakt van de methode **ConvertToDateTime** .</span><span class="sxs-lookup"><span data-stu-id="cf4e7-129">The `$date` variable stores a hash table with the expression that uses the **ConvertToDateTime** method.</span></span> <span data-ttu-id="cf4e7-130">Met de expressie wordt de waarde van de eigenschap **CreationTime** van een WMI-teken reeks geconverteerd naar een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-130">The expression converts the **CreationTime** property's value from a WMI string to a **DateTime** object.</span></span>

<span data-ttu-id="cf4e7-131">`Get-ComputerRestorePoint` Hiermee verzendt u de systeem herstel punt objecten omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-131">`Get-ComputerRestorePoint` sends the system restore point objects down the pipeline.</span></span> <span data-ttu-id="cf4e7-132">`Select-Object` gebruikt de para meter **Property** om de eigenschappen op te geven die moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-132">`Select-Object` uses the **Property** parameter to specify the properties to display.</span></span> <span data-ttu-id="cf4e7-133">Voor elk object in de pijp lijn wordt met de expressie in de `$date` **CreationTime** geconverteerd en wordt het resultaat in de **datum** eigenschap uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-133">For each object in the pipeline, the expression in `$date` converts the **CreationTime** and outputs the result in the **Date** property.</span></span>

### <span data-ttu-id="cf4e7-134">Voor beeld 5: een eigenschap gebruiken om een Volg nummer op te halen</span><span class="sxs-lookup"><span data-stu-id="cf4e7-134">Example 5: Use a property to get a sequence number</span></span>

<span data-ttu-id="cf4e7-135">In dit voor beeld wordt een Volg nummer opgehaald met behulp van de eigenschap **SequenceNumber** en een matrix index.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-135">This example gets a sequence number by using the **SequenceNumber** property and an array index.</span></span> <span data-ttu-id="cf4e7-136">De uitvoer bevat alleen het volgorde nummer.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-136">The output only contains the sequence number.</span></span>

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

<span data-ttu-id="cf4e7-137">`Get-ComputerRestorePoint` maakt gebruik van de eigenschap **SequenceNumber** met een matrix index.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-137">`Get-ComputerRestorePoint` uses the **SequenceNumber** property with an array index.</span></span> <span data-ttu-id="cf4e7-138">De matrix index van `-1` haalt het meest recente volgorde nummer op in de matrix.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-138">The array index of `-1` gets the most recent sequence number in the array.</span></span>

## <span data-ttu-id="cf4e7-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cf4e7-139">PARAMETERS</span></span>

### <span data-ttu-id="cf4e7-140">-LastStatus</span><span class="sxs-lookup"><span data-stu-id="cf4e7-140">-LastStatus</span></span>

<span data-ttu-id="cf4e7-141">Hiermee wordt aangegeven dat `Get-ComputerRestorePoint` de status van de meest recente systeem herstel bewerking wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-141">Indicates that `Get-ComputerRestorePoint` gets the status of the most recent system restore operation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf4e7-142">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="cf4e7-142">-RestorePoint</span></span>

<span data-ttu-id="cf4e7-143">Hiermee geeft u de Volg nummers van de systeem herstel punten.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-143">Specifies the sequence numbers of the system restore points.</span></span> <span data-ttu-id="cf4e7-144">U kunt een enkel volg nummer of een door komma's gescheiden matrix met Volg nummers opgeven.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-144">You can specify either a single sequence number or a comma-separated array of sequence numbers.</span></span>

<span data-ttu-id="cf4e7-145">Als de para meter **RestorePoint** niet is opgegeven, `Get-ComputerRestorePoint` retourneert alle systeem herstel punten van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-145">If the **RestorePoint** parameter isn't specified, `Get-ComputerRestorePoint` returns all the local computer's system restore points.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf4e7-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cf4e7-146">CommonParameters</span></span>

<span data-ttu-id="cf4e7-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cf4e7-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cf4e7-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="cf4e7-149">INPUTS</span></span>

### <span data-ttu-id="cf4e7-150">Geen</span><span class="sxs-lookup"><span data-stu-id="cf4e7-150">None</span></span>

<span data-ttu-id="cf4e7-151">U kunt geen objecten naar beneden verplaatsen in de pijp lijn `Get-ComputerRestorePoint` .</span><span class="sxs-lookup"><span data-stu-id="cf4e7-151">You can't send objects down the pipeline to `Get-ComputerRestorePoint`.</span></span>

## <span data-ttu-id="cf4e7-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cf4e7-152">OUTPUTS</span></span>

### <span data-ttu-id="cf4e7-153">System. Management. ManagementObject # root\default\SystemRestore of String</span><span class="sxs-lookup"><span data-stu-id="cf4e7-153">System.Management.ManagementObject#root\default\SystemRestore or String</span></span>

<span data-ttu-id="cf4e7-154">`Get-ComputerRestorePoint` retourneert een **SystemRestore** -object, een exemplaar van de klasse Windows Management INSTRUMENTATION (WMI) **SystemRestore** .</span><span class="sxs-lookup"><span data-stu-id="cf4e7-154">`Get-ComputerRestorePoint` returns a **SystemRestore** object, which is an instance of the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

<span data-ttu-id="cf4e7-155">Wanneer u de para meter **LastStatus** gebruikt, `Get-ComputerRestorePoint` retourneert een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-155">When you use the **LastStatus** parameter, `Get-ComputerRestorePoint` returns a string.</span></span>

## <span data-ttu-id="cf4e7-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cf4e7-156">NOTES</span></span>

<span data-ttu-id="cf4e7-157">Als u een `Get-ComputerRestorePoint` opdracht wilt uitvoeren in Windows Vista en latere versies van Windows, opent u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="cf4e7-157">To run a `Get-ComputerRestorePoint` command on Windows Vista and later versions of Windows, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="cf4e7-158">`Get-ComputerRestorePoint` maakt gebruik van de WMI-klasse **SystemRestore** .</span><span class="sxs-lookup"><span data-stu-id="cf4e7-158">`Get-ComputerRestorePoint` uses the WMI **SystemRestore** class.</span></span>

## <span data-ttu-id="cf4e7-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cf4e7-159">RELATED LINKS</span></span>

[<span data-ttu-id="cf4e7-160">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="cf4e7-160">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="cf4e7-161">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="cf4e7-161">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="cf4e7-162">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="cf4e7-162">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="cf4e7-163">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="cf4e7-163">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="cf4e7-164">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="cf4e7-164">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="cf4e7-165">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="cf4e7-165">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="cf4e7-166">Herstellen-computer</span><span class="sxs-lookup"><span data-stu-id="cf4e7-166">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="cf4e7-167">SystemRestore</span><span class="sxs-lookup"><span data-stu-id="cf4e7-167">SystemRestore</span></span>](/windows/win32/sr/systemrestore)
