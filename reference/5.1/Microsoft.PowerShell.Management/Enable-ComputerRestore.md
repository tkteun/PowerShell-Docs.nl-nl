---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/enable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ComputerRestore
ms.openlocfilehash: f9616a7f9af4dd2fa45e150bb64eef65427b4947
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250814"
---
# <span data-ttu-id="5aad8-103">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="5aad8-103">Enable-ComputerRestore</span></span>

## <span data-ttu-id="5aad8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5aad8-104">SYNOPSIS</span></span>
<span data-ttu-id="5aad8-105">Hiermee schakelt u de functie systeem herstel op het opgegeven bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="5aad8-105">Enables the System Restore feature on the specified file system drive.</span></span>

## <span data-ttu-id="5aad8-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5aad8-106">SYNTAX</span></span>

```
Enable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5aad8-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5aad8-107">DESCRIPTION</span></span>
<span data-ttu-id="5aad8-108">Met de cmdlet **Enable-ComputerRestore** wordt de functie systeem herstel op een of meer bestandssysteem stations ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="5aad8-108">The **Enable-ComputerRestore** cmdlet turns on the System Restore feature on one or more file system drives.</span></span>
<span data-ttu-id="5aad8-109">Als gevolg hiervan kunt u hulpprogram ma's, zoals de cmdlet Restore-Computer, gebruiken om de computer terug te zetten naar een eerdere status.</span><span class="sxs-lookup"><span data-stu-id="5aad8-109">As a result, you can use tools, such as the Restore-Computer cmdlet, to restore the computer to a previous state.</span></span>

<span data-ttu-id="5aad8-110">Systeem herstel is standaard ingeschakeld op alle in aanmerking komende stations, maar u kunt dit uitschakelen, bijvoorbeeld met behulp van de cmdlet Disable-ComputerRestore.</span><span class="sxs-lookup"><span data-stu-id="5aad8-110">By default, System Restore is enabled on all eligible drives, but you can disable it, such as by using the Disable-ComputerRestore cmdlet.</span></span>
<span data-ttu-id="5aad8-111">Om systeem herstel op een wille keurige schijf in of uit te scha kelen, moet dit op het systeem station worden ingeschakeld, hetzij eerst, hetzij gelijktijdig.</span><span class="sxs-lookup"><span data-stu-id="5aad8-111">To enable (or re-enable) System Restore on any drive, it must be enabled on the system drive, either first or concurrently.</span></span>
<span data-ttu-id="5aad8-112">Gebruik Rstrui.exe om de status van systeem herstel voor elk station te vinden.</span><span class="sxs-lookup"><span data-stu-id="5aad8-112">To find the state of System Restore for each drive, use Rstrui.exe.</span></span>

<span data-ttu-id="5aad8-113">Systeem herstel punten en de ComputerRestore-cmdlets worden alleen ondersteund op client besturingssystemen, zoals Windows 7, Windows Vista en Windows XP.</span><span class="sxs-lookup"><span data-stu-id="5aad8-113">System restore points and the ComputerRestore cmdlets are supported only on client operating systems, such as Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="5aad8-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5aad8-114">EXAMPLES</span></span>

### <span data-ttu-id="5aad8-115">Voor beeld 1: systeem herstel inschakelen op het opgegeven station</span><span class="sxs-lookup"><span data-stu-id="5aad8-115">Example 1: Enable System Restore on the specified drive</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\"
```

<span data-ttu-id="5aad8-116">Met deze opdracht wordt systeem herstel ingeschakeld op station C: van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5aad8-116">This command enables System Restore on the C: drive of the local computer.</span></span>

### <span data-ttu-id="5aad8-117">Voor beeld 2: systeem herstel op meerdere stations inschakelen</span><span class="sxs-lookup"><span data-stu-id="5aad8-117">Example 2: Enable System Restore on multiple drives</span></span>

```
PS C:\> Enable-ComputerRestore -Drive "C:\", "D:\"
```

<span data-ttu-id="5aad8-118">Met deze opdracht wordt systeem herstel ingeschakeld op de stations C: en D: van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="5aad8-118">This command enables System Restore on the C: and D: drives of the local computer.</span></span>

## <span data-ttu-id="5aad8-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5aad8-119">PARAMETERS</span></span>

### <span data-ttu-id="5aad8-120">-Station</span><span class="sxs-lookup"><span data-stu-id="5aad8-120">-Drive</span></span>
<span data-ttu-id="5aad8-121">Hiermee geeft u de stations met het bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="5aad8-121">Specifies the file system drives.</span></span>
<span data-ttu-id="5aad8-122">Voer een of meer bestandssysteem stationsletters in, gevolgd door een dubbele punt en een back slash en tussen aanhalings tekens, zoals C:\ of D:\.</span><span class="sxs-lookup"><span data-stu-id="5aad8-122">Enter one or more file system drive letters, each followed by a colon and a backslash and enclosed in quotation marks, such as C:\ or D:\.</span></span>
<span data-ttu-id="5aad8-123">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="5aad8-123">This parameter is required.</span></span>

<span data-ttu-id="5aad8-124">U kunt deze cmdlet niet gebruiken om systeem herstel in te scha kelen op een extern netwerk station, zelfs als het station is toegewezen aan de lokale computer en u geen systeem herstel kunt inschakelen op stations die niet in aanmerking komen voor systeem herstel, zoals externe schijven.</span><span class="sxs-lookup"><span data-stu-id="5aad8-124">You cannot use this cmdlet to enable System Restore on a remote network drive, even if the drive is mapped to the local computer, and you cannot enable System Restore on drives that are not eligible for System Restore, such as external drives.</span></span>

<span data-ttu-id="5aad8-125">Systeem herstel moet zijn ingeschakeld op het systeem station, hetzij voor of gelijktijdig, om systeem herstel op elk station in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="5aad8-125">To enable System Restore on any drive, System Restore must be enabled on the system drive, either before or concurrently.</span></span>

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

### <span data-ttu-id="5aad8-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5aad8-126">-Confirm</span></span>
<span data-ttu-id="5aad8-127">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5aad8-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5aad8-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5aad8-128">-WhatIf</span></span>
<span data-ttu-id="5aad8-129">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5aad8-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5aad8-130">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5aad8-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5aad8-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5aad8-131">CommonParameters</span></span>
<span data-ttu-id="5aad8-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5aad8-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5aad8-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5aad8-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5aad8-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="5aad8-134">INPUTS</span></span>

### <span data-ttu-id="5aad8-135">Geen</span><span class="sxs-lookup"><span data-stu-id="5aad8-135">None</span></span>
<span data-ttu-id="5aad8-136">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="5aad8-136">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="5aad8-137">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5aad8-137">OUTPUTS</span></span>

### <span data-ttu-id="5aad8-138">Geen</span><span class="sxs-lookup"><span data-stu-id="5aad8-138">None</span></span>
<span data-ttu-id="5aad8-139">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="5aad8-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5aad8-140">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5aad8-140">NOTES</span></span>

* <span data-ttu-id="5aad8-141">Als u deze cmdlet wilt uitvoeren op Windows Vista en latere versies van Windows, opent u Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="5aad8-141">To run this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="5aad8-142">Als u de bestandssysteem stations wilt vinden die in aanmerking komen voor systeem herstel, gaat u naar het tabblad systeem beveiliging in het onderdeel systeem in het configuratie scherm. Als u dit tabblad in Windows Power shell wilt openen, typt u `SystemPropertiesProtection` .</span><span class="sxs-lookup"><span data-stu-id="5aad8-142">To find the file system drives that are eligible for system restore, in System in Control Panel, see the System Protection tab. To open this tab in Windows PowerShell, type `SystemPropertiesProtection`.</span></span>

  <span data-ttu-id="5aad8-143">Deze cmdlet maakt gebruik van de Windows Management Instrumentation klasse **SystemRestore** (WMI).</span><span class="sxs-lookup"><span data-stu-id="5aad8-143">This cmdlet uses the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

*

## <span data-ttu-id="5aad8-144">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5aad8-144">RELATED LINKS</span></span>

[<span data-ttu-id="5aad8-145">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="5aad8-145">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="5aad8-146">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="5aad8-146">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="5aad8-147">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="5aad8-147">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="5aad8-148">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="5aad8-148">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="5aad8-149">Herstellen-computer</span><span class="sxs-lookup"><span data-stu-id="5aad8-149">Restore-Computer</span></span>](Restore-Computer.md)
