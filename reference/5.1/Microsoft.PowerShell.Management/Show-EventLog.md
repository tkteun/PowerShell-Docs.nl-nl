---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250545"
---
# <span data-ttu-id="d4994-103">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="d4994-103">Show-EventLog</span></span>

## <span data-ttu-id="d4994-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d4994-104">SYNOPSIS</span></span>
<span data-ttu-id="d4994-105">Hiermee worden de gebeurtenis logboeken van de lokale of externe computer in Logboeken weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d4994-105">Displays the event logs of the local or a remote computer in Event Viewer.</span></span>

## <span data-ttu-id="d4994-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d4994-106">SYNTAX</span></span>

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="d4994-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d4994-107">DESCRIPTION</span></span>
<span data-ttu-id="d4994-108">De cmdlet **Show-Eventlog** wordt geopend logboeken op de lokale computer en wordt weer gegeven in alle klassieke gebeurtenis logboeken op de lokale computer of een externe computer.</span><span class="sxs-lookup"><span data-stu-id="d4994-108">The **Show-EventLog** cmdlet opens Event Viewer on the local computer and displays in it all of the classic event logs on the local computer or a remote computer.</span></span>

<span data-ttu-id="d4994-109">Als u Logboeken wilt openen op Windows Vista en latere versies van het Windows-besturings systeem, moet de huidige gebruiker lid zijn van de groep Administrators op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d4994-109">To open Event Viewer on Windows Vista and later versions of the Windows operating system, the current user must be a member of the Administrators group on the local computer.</span></span>

<span data-ttu-id="d4994-110">De cmdlets die het zelfstandig naam woord van het **gebeurtenissen logboek** bevatten (de **Eventlog** -cmdlets) werken alleen in klassieke gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="d4994-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="d4994-111">Als u gebeurtenissen wilt ophalen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van het Windows-besturings systeem, gebruikt u de cmdlet Get-WinEvent.</span><span class="sxs-lookup"><span data-stu-id="d4994-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="d4994-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d4994-112">EXAMPLES</span></span>

### <span data-ttu-id="d4994-113">Voor beeld 1: gebeurtenis logboeken voor de lokale computer weer geven</span><span class="sxs-lookup"><span data-stu-id="d4994-113">Example 1: Display event logs for the local computer</span></span>

```
PS C:\> Show-EventLog
```

<span data-ttu-id="d4994-114">Met deze opdracht wordt Logboeken geopend en weer gegeven in de klassieke gebeurtenis logboeken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d4994-114">This command opens Event Viewer and displays in it the classic event logs on the local computer.</span></span>

### <span data-ttu-id="d4994-115">Voor beeld 2: gebeurtenis logboeken weer geven voor een externe computer</span><span class="sxs-lookup"><span data-stu-id="d4994-115">Example 2: Display event logs for a remote computer</span></span>

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

<span data-ttu-id="d4994-116">Met deze opdracht wordt Logboeken geopend en weer gegeven in de klassieke gebeurtenis logboeken op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="d4994-116">This command opens Event Viewer and displays in it the classic event logs on the Server01 computer.</span></span>

## <span data-ttu-id="d4994-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d4994-117">PARAMETERS</span></span>

### <span data-ttu-id="d4994-118">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d4994-118">-ComputerName</span></span>
<span data-ttu-id="d4994-119">Hiermee geeft u een externe computer.</span><span class="sxs-lookup"><span data-stu-id="d4994-119">Specifies a remote computer.</span></span>
<span data-ttu-id="d4994-120">**Show-Eventlog** worden de gebeurtenis logboeken van de opgegeven computer in Logboeken op de lokale computer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d4994-120">**Show-EventLog** displays the event logs from the specified computer in Event Viewer on the local computer.</span></span>
<span data-ttu-id="d4994-121">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d4994-121">The default is the local computer.</span></span>

<span data-ttu-id="d4994-122">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.</span><span class="sxs-lookup"><span data-stu-id="d4994-122">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="d4994-123">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="d4994-123">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="d4994-124">U kunt de para meter *ComputerName* ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d4994-124">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d4994-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d4994-125">CommonParameters</span></span>
<span data-ttu-id="d4994-126">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d4994-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d4994-127">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d4994-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d4994-128">INVOER</span><span class="sxs-lookup"><span data-stu-id="d4994-128">INPUTS</span></span>

### <span data-ttu-id="d4994-129">Geen</span><span class="sxs-lookup"><span data-stu-id="d4994-129">None</span></span>
<span data-ttu-id="d4994-130">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d4994-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d4994-131">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d4994-131">OUTPUTS</span></span>

### <span data-ttu-id="d4994-132">Geen</span><span class="sxs-lookup"><span data-stu-id="d4994-132">None</span></span>
<span data-ttu-id="d4994-133">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="d4994-133">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d4994-134">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d4994-134">NOTES</span></span>

* <span data-ttu-id="d4994-135">De Windows Power shell-opdracht prompt wordt weer gegeven zodra Logboeken wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="d4994-135">The Windows PowerShell command prompt returns as soon as Event Viewer opens.</span></span> <span data-ttu-id="d4994-136">U kunt in de huidige sessie werken terwijl Logboeken is geopend.</span><span class="sxs-lookup"><span data-stu-id="d4994-136">You can work in the current session while Event Viewer is open.</span></span>

  <span data-ttu-id="d4994-137">Omdat deze cmdlet een gebruikers interface vereist, werkt deze niet op Server Core-installaties van Windows Server.</span><span class="sxs-lookup"><span data-stu-id="d4994-137">Because this cmdlet requires a user interface, it does not work on Server Core installations of Windows Server.</span></span>

*

## <span data-ttu-id="d4994-138">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d4994-138">RELATED LINKS</span></span>

[<span data-ttu-id="d4994-139">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="d4994-139">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="d4994-140">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="d4994-140">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="d4994-141">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="d4994-141">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="d4994-142">Nieuw-gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="d4994-142">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="d4994-143">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="d4994-143">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="d4994-144">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="d4994-144">Write-EventLog</span></span>](Write-EventLog.md)
