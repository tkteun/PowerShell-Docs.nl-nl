---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: fb6c0f930536e7a32d83c9f390a0e351a6952550
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249295"
---
# <span data-ttu-id="cd82d-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="cd82d-103">Exit-PSSession</span></span>

## <span data-ttu-id="cd82d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cd82d-104">SYNOPSIS</span></span>
<span data-ttu-id="cd82d-105">Hiermee beëindigt u een interactieve sessie met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="cd82d-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="cd82d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cd82d-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="cd82d-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cd82d-107">DESCRIPTION</span></span>

<span data-ttu-id="cd82d-108">De **Exit-PSSession** -cmdlet beëindigt interactieve sessies die u hebt gestart met behulp van de cmdlet Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="cd82d-108">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="cd82d-109">U kunt ook het tref woord **Exit** gebruiken om een interactieve sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="cd82d-109">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="cd82d-110">Het effect is hetzelfde als het gebruik van **Exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="cd82d-110">The effect is the same as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="cd82d-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cd82d-111">EXAMPLES</span></span>

### <span data-ttu-id="cd82d-112">Voor beeld 1: een interactieve sessie starten en stoppen</span><span class="sxs-lookup"><span data-stu-id="cd82d-112">Example 1: Start and stop an interactive session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS>
```

<span data-ttu-id="cd82d-113">Met deze opdrachten wordt een interactieve sessie met de Server01 externe computer gestart en vervolgens gestopt.</span><span class="sxs-lookup"><span data-stu-id="cd82d-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="cd82d-114">Voor beeld 2: een interactieve sessie starten en stoppen met behulp van een PSSession-object</span><span class="sxs-lookup"><span data-stu-id="cd82d-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="cd82d-115">Met deze opdrachten wordt een interactieve sessie gestart en gestopt met de Server01-computer die gebruikmaakt van een Power shell-sessie ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="cd82d-115">These commands start and stop an interactive session with the Server01 computer that uses a PowerShell session ( **PSSession** ).</span></span>

<span data-ttu-id="cd82d-116">Omdat de interactieve sessie is gestart met een Power shell-sessie, is de **PSSession** nog steeds beschikbaar wanneer de interactieve sessie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="cd82d-116">Because the interactive session was started by using a PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="cd82d-117">Als u de para meter *ComputerName* gebruikt, wordt door **Enter-PSSession** een tijdelijke sessie gemaakt die wordt gesloten wanneer de interactieve sessie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="cd82d-117">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="cd82d-118">De eerste opdracht maakt gebruik van de New-PSSession cmdlet om een **PSSession** te maken op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="cd82d-118">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="cd82d-119">Met de opdracht slaat u de **PSSession** op in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="cd82d-119">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="cd82d-120">Met de tweede opdracht wordt **Enter-PSSession** gebruikt om een interactieve sessie te starten met behulp van de **PSSession** in $s.</span><span class="sxs-lookup"><span data-stu-id="cd82d-120">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="cd82d-121">De derde opdracht maakt gebruik van **Exit-PSSession** om de interactieve sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="cd82d-121">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="cd82d-122">Met de laatste opdracht wordt de **PSSession** weer gegeven in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="cd82d-122">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="cd82d-123">De eigenschap **State** geeft aan dat de **PSSession** nog geopend is en beschikbaar is voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="cd82d-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="cd82d-124">Voor beeld 3: het sleutel woord exit gebruiken om een sessie te stoppen</span><span class="sxs-lookup"><span data-stu-id="cd82d-124">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS> Enter-PSSession -computername Server01
Server01\PS> exit
PS>
```

<span data-ttu-id="cd82d-125">In dit voor beeld wordt het sleutel woord **Exit** gebruikt om een interactieve sessie te stoppen die is gestart met **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="cd82d-125">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession**.</span></span>
<span data-ttu-id="cd82d-126">Het sleutel woord **Exit** heeft hetzelfde effect als het gebruik van **Exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="cd82d-126">The **Exit** keyword has the same effect as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="cd82d-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cd82d-127">PARAMETERS</span></span>

### <span data-ttu-id="cd82d-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd82d-128">CommonParameters</span></span>

<span data-ttu-id="cd82d-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cd82d-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cd82d-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cd82d-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cd82d-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="cd82d-131">INPUTS</span></span>

### <span data-ttu-id="cd82d-132">Geen</span><span class="sxs-lookup"><span data-stu-id="cd82d-132">None</span></span>

<span data-ttu-id="cd82d-133">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="cd82d-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="cd82d-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cd82d-134">OUTPUTS</span></span>

### <span data-ttu-id="cd82d-135">Geen</span><span class="sxs-lookup"><span data-stu-id="cd82d-135">None</span></span>

<span data-ttu-id="cd82d-136">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cd82d-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="cd82d-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cd82d-137">NOTES</span></span>

* <span data-ttu-id="cd82d-138">Deze cmdlet heeft alleen de algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="cd82d-138">This cmdlet takes only the common parameters.</span></span>

*

## <span data-ttu-id="cd82d-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cd82d-139">RELATED LINKS</span></span>

[<span data-ttu-id="cd82d-140">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="cd82d-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="cd82d-141">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="cd82d-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="cd82d-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="cd82d-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="cd82d-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="cd82d-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="cd82d-144">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="cd82d-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="cd82d-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="cd82d-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="cd82d-146">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="cd82d-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="cd82d-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="cd82d-147">Remove-PSSession</span></span>](Remove-PSSession.md)
