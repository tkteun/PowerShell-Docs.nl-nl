---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250562"
---
# <span data-ttu-id="c2a6e-103">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="c2a6e-103">Restore-Computer</span></span>

## <span data-ttu-id="c2a6e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c2a6e-104">SYNOPSIS</span></span>
<span data-ttu-id="c2a6e-105">Start een systeem herstel op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-105">Starts a system restore on the local computer.</span></span>

## <span data-ttu-id="c2a6e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c2a6e-106">SYNTAX</span></span>

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c2a6e-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c2a6e-107">DESCRIPTION</span></span>
<span data-ttu-id="c2a6e-108">Met de cmdlet Restore **-computer** wordt de lokale computer teruggezet naar het opgegeven systeem herstel punt.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-108">The **Restore-Computer** cmdlet restores the local computer to the specified system restore point.</span></span>

<span data-ttu-id="c2a6e-109">**Herstellen:** de computer wordt opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-109">**Restore-Computer** restarts the computer.</span></span>
<span data-ttu-id="c2a6e-110">De herstel bewerking is voltooid tijdens het opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-110">The restore is completed during the restart operation.</span></span>

<span data-ttu-id="c2a6e-111">Systeem herstel punten en **herstel-computer** worden alleen ondersteund op client besturingssystemen, zoals Windows 7, Windows Vista en Windows XP.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-111">System restore points and **Restore-Computer** are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="c2a6e-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c2a6e-112">EXAMPLES</span></span>

### <span data-ttu-id="c2a6e-113">Voor beeld 1: de lokale computer herstellen</span><span class="sxs-lookup"><span data-stu-id="c2a6e-113">Example 1: Restore the local computer</span></span>

```
PS C:\> Restore-Computer -RestorePoint 253
```

<span data-ttu-id="c2a6e-114">Met deze opdracht wordt de lokale computer teruggezet naar het herstel punt met het Volg nummer 253.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-114">This command restores the local computer to the restore point that has sequence number 253.</span></span>

### <span data-ttu-id="c2a6e-115">Voor beeld 2: de lokale computer herstellen met bevestiging</span><span class="sxs-lookup"><span data-stu-id="c2a6e-115">Example 2: Restore the local computer with confirmation</span></span>

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="c2a6e-116">Met deze opdracht wordt de lokale computer teruggezet naar het herstel punt met het Volg nummer 255.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-116">This command restores the local computer to the restore point that has sequence number 255.</span></span>
<span data-ttu-id="c2a6e-117">De para meter *confirm* wordt gebruikt om de gebruiker te vragen voordat de bewerking daad werkelijk wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-117">It uses the *Confirm* parameter to prompt the user before actually performing the operation.</span></span>

### <span data-ttu-id="c2a6e-118">Voor beeld 3: een computer herstellen en de status controleren</span><span class="sxs-lookup"><span data-stu-id="c2a6e-118">Example 3: Restore a computer and check the status</span></span>

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

<span data-ttu-id="c2a6e-119">Met deze opdrachten wordt een systeem herstel uitgevoerd en wordt de status ervan gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-119">These commands run a system restore and then check its status.</span></span>

<span data-ttu-id="c2a6e-120">De eerste opdracht gebruikt **Get-ComputerRestorePoint** om de herstel punten op de lokale computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-120">The first command uses **Get-ComputerRestorePoint** to get the restore points on the local computer.</span></span>

<span data-ttu-id="c2a6e-121">Met de tweede opdracht wordt de computer teruggezet naar het herstel punt met het Volg nummer 255.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-121">The second command restores the computer to the restore point with sequence number 255.</span></span>

<span data-ttu-id="c2a6e-122">De derde opdracht maakt gebruik van de para meter *LastStatus* van de cmdlet *Get-ComputerRestorePoint* om de status van de herstel bewerking te controleren.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-122">The third command uses the *LastStatus* parameter of *Get-ComputerRestorePoint* cmdlet to check the status of the restore operation.</span></span>
<span data-ttu-id="c2a6e-123">Omdat **Restore-computer** geforceerd opnieuw moet worden opgestart, wordt deze opdracht ingevoerd nadat de computer opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-123">Because **Restore-Computer** forces a restart, this command would be entered after the computer restarts.</span></span>

## <span data-ttu-id="c2a6e-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c2a6e-124">PARAMETERS</span></span>

### <span data-ttu-id="c2a6e-125">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="c2a6e-125">-RestorePoint</span></span>
<span data-ttu-id="c2a6e-126">Hiermee geeft u het Volg nummer van het herstel punt op.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-126">Specifies the sequence number of the restore point.</span></span>
<span data-ttu-id="c2a6e-127">Gebruik de cmdlet Get-ComputerRestorePoint om het Volg nummer te vinden.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-127">To find the sequence number, use the Get-ComputerRestorePoint cmdlet.</span></span>
<span data-ttu-id="c2a6e-128">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-128">This parameter is required.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c2a6e-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c2a6e-129">-Confirm</span></span>
<span data-ttu-id="c2a6e-130">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c2a6e-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c2a6e-131">-WhatIf</span></span>
<span data-ttu-id="c2a6e-132">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c2a6e-133">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c2a6e-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c2a6e-134">CommonParameters</span></span>
<span data-ttu-id="c2a6e-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c2a6e-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c2a6e-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="c2a6e-137">INPUTS</span></span>

### <span data-ttu-id="c2a6e-138">Geen</span><span class="sxs-lookup"><span data-stu-id="c2a6e-138">None</span></span>
<span data-ttu-id="c2a6e-139">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-139">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c2a6e-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c2a6e-140">OUTPUTS</span></span>

### <span data-ttu-id="c2a6e-141">Geen</span><span class="sxs-lookup"><span data-stu-id="c2a6e-141">None</span></span>
<span data-ttu-id="c2a6e-142">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c2a6e-143">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c2a6e-143">NOTES</span></span>

* <span data-ttu-id="c2a6e-144">Als u een Restore-Computer-opdracht wilt uitvoeren in Windows Vista en latere versies van het Windows-besturings systeem, opent u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c2a6e-144">To run a Restore-Computer command on Windows Vista and later versions of the Windows operating system, open Windows PowerShell by using the Run as administrator option.</span></span>
* <span data-ttu-id="c2a6e-145">Deze cmdlet maakt gebruik van de Windows Management Instrumentation klasse **SystemRestore** (WMI).</span><span class="sxs-lookup"><span data-stu-id="c2a6e-145">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

## <span data-ttu-id="c2a6e-146">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c2a6e-146">RELATED LINKS</span></span>

[<span data-ttu-id="c2a6e-147">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="c2a6e-147">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="c2a6e-148">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="c2a6e-148">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="c2a6e-149">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="c2a6e-149">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="c2a6e-150">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="c2a6e-150">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="c2a6e-151">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="c2a6e-151">Restart-Computer</span></span>](Restart-Computer.md)
