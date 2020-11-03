---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/disable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ComputerRestore
ms.openlocfilehash: 941829c3caa0f6bb2f5712dda9eb7d8c36908062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250815"
---
# <span data-ttu-id="77c75-103">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="77c75-103">Disable-ComputerRestore</span></span>

## <span data-ttu-id="77c75-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="77c75-104">SYNOPSIS</span></span>
<span data-ttu-id="77c75-105">Hiermee schakelt u de functie systeem herstel uit op het opgegeven bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="77c75-105">Disables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="77c75-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="77c75-106">SYNTAX</span></span>

```
Disable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="77c75-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="77c75-107">DESCRIPTION</span></span>
<span data-ttu-id="77c75-108">De cmdlet **Disable-ComputerRestore** schakelt de functie systeem herstel uit op een of meer bestandssysteem stations.</span><span class="sxs-lookup"><span data-stu-id="77c75-108">The **Disable-ComputerRestore** cmdlet turns off the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="77c75-109">Als gevolg hiervan worden pogingen om de computer te herstellen niet van invloed op het opgegeven station.</span><span class="sxs-lookup"><span data-stu-id="77c75-109">As a result, attempts to restore the computer do not affect the specified drive.</span></span>

<span data-ttu-id="77c75-110">Als u systeem herstel op een wille keurig station wilt uitschakelen, moet dit worden uitgeschakeld op het systeem station, hetzij eerst, hetzij gelijktijdig.</span><span class="sxs-lookup"><span data-stu-id="77c75-110">To disable System Restore on any drive, it must be disabled on the system drive, either first or concurrently.</span></span>

<span data-ttu-id="77c75-111">Gebruik de cmdlet Enable-ComputerRestore om systeem herstel opnieuw in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="77c75-111">To re-enable System Restore, use the Enable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="77c75-112">Gebruik Rstrui.exe om de status van systeem herstel voor elk station te vinden.</span><span class="sxs-lookup"><span data-stu-id="77c75-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="77c75-113">Systeem herstel punten en de ComputerRestore-cmdlets worden alleen ondersteund op client besturingssystemen, zoals Windows 7, Windows Vista en Windows XP.</span><span class="sxs-lookup"><span data-stu-id="77c75-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="77c75-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="77c75-114">EXAMPLES</span></span>

### <span data-ttu-id="77c75-115">Voor beeld 1: systeem herstel op het opgegeven station uitschakelen</span><span class="sxs-lookup"><span data-stu-id="77c75-115">Example 1: Disable System Restore on the specified drive</span></span>

```
PS C:\> Disable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="77c75-116">Met deze opdracht wordt systeem herstel op station C: uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="77c75-116">This command disables System Restore on the C: drive.</span></span>

### <span data-ttu-id="77c75-117">Voor beeld 2: systeem herstel op meerdere stations uitschakelen</span><span class="sxs-lookup"><span data-stu-id="77c75-117">Example 2: Disable System Restore on multiple drives</span></span>

```
PS C:\> Disable-ComputerRestore "C:\", "D:\"
```

<span data-ttu-id="77c75-118">Met deze opdracht wordt systeem herstel op de stations C: en D: uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="77c75-118">This command disables System Restore on the C: and D: drives.</span></span>
<span data-ttu-id="77c75-119">Met de opdracht wordt de para meter *Drive* gebruikt, maar wordt de parameter naam van de station wegge laten.</span><span class="sxs-lookup"><span data-stu-id="77c75-119">The command uses the *Drive* parameter, but it omits the Drive parameter name.</span></span>

## <span data-ttu-id="77c75-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="77c75-120">PARAMETERS</span></span>

### <span data-ttu-id="77c75-121">-Station</span><span class="sxs-lookup"><span data-stu-id="77c75-121">-Drive</span></span>
<span data-ttu-id="77c75-122">Hiermee geeft u de stations met het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="77c75-122">Specifies the file system drives.</span></span>
<span data-ttu-id="77c75-123">Voer een of meer bestandssysteem stationsletters in, gevolgd door een dubbele punt en een back slash en tussen aanhalings tekens, zoals C:\ of D:\.</span><span class="sxs-lookup"><span data-stu-id="77c75-123">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="77c75-124">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="77c75-124">This parameter is required.</span></span>

<span data-ttu-id="77c75-125">U kunt deze cmdlet niet gebruiken om systeem herstel uit te scha kelen op een extern netwerk station, zelfs als het station is toegewezen aan de lokale computer en u geen systeem herstel kunt uitschakelen op stations die niet in aanmerking komen voor systeem herstel, zoals externe schijven.</span><span class="sxs-lookup"><span data-stu-id="77c75-125">You cannot use this cmdlet to disable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot disable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="77c75-126">Als u systeem herstel op een wille keurig station wilt uitschakelen, moet systeem herstel worden uitgeschakeld op het systeem station, hetzij voor of gelijktijdig.</span><span class="sxs-lookup"><span data-stu-id="77c75-126">To disable System Restore on any drive, System Restore must be disabled on the system drive, either before or concurrently.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77c75-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="77c75-127">-Confirm</span></span>
<span data-ttu-id="77c75-128">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="77c75-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="77c75-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="77c75-129">-WhatIf</span></span>
<span data-ttu-id="77c75-130">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="77c75-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="77c75-131">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="77c75-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="77c75-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="77c75-132">CommonParameters</span></span>
<span data-ttu-id="77c75-133">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="77c75-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="77c75-134">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="77c75-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="77c75-135">INVOER</span><span class="sxs-lookup"><span data-stu-id="77c75-135">INPUTS</span></span>

### <span data-ttu-id="77c75-136">Geen</span><span class="sxs-lookup"><span data-stu-id="77c75-136">None</span></span>
<span data-ttu-id="77c75-137">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="77c75-137">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="77c75-138">UITVOER</span><span class="sxs-lookup"><span data-stu-id="77c75-138">OUTPUTS</span></span>

### <span data-ttu-id="77c75-139">Geen</span><span class="sxs-lookup"><span data-stu-id="77c75-139">None</span></span>
<span data-ttu-id="77c75-140">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="77c75-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="77c75-141">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="77c75-141">NOTES</span></span>

* <span data-ttu-id="77c75-142">Als u deze cmdlet wilt uitvoeren op Windows Vista en latere versies van Windows, opent u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="77c75-142">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="77c75-143">Als u de bestandssysteem stations wilt vinden die in aanmerking komen voor systeem herstel, gaat u naar het tabblad systeem beveiliging in het onderdeel systeem in het configuratie scherm. Als u dit tabblad in Windows Power shell wilt openen, typt u `SystemPropertiesProtection` .</span><span class="sxs-lookup"><span data-stu-id="77c75-143">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="77c75-144">Deze cmdlet maakt gebruik van de Windows Management Instrumentation klasse **SystemRestore** (WMI).</span><span class="sxs-lookup"><span data-stu-id="77c75-144">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="77c75-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="77c75-145">RELATED LINKS</span></span>

[<span data-ttu-id="77c75-146">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="77c75-146">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="77c75-147">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="77c75-147">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="77c75-148">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="77c75-148">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="77c75-149">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="77c75-149">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="77c75-150">Herstellen-computer</span><span class="sxs-lookup"><span data-stu-id="77c75-150">Restore-Computer</span></span>](Restore-Computer.md)
