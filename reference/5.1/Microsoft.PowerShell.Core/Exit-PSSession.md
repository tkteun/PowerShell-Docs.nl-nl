---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: efe0e6c9287b3595988aa3ffc520ce46699cafda
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249968"
---
# <span data-ttu-id="6a8b7-103">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="6a8b7-103">Exit-PSSession</span></span>

## <span data-ttu-id="6a8b7-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6a8b7-104">SYNOPSIS</span></span>
<span data-ttu-id="6a8b7-105">Hiermee beëindigt u een interactieve sessie met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-105">Ends an interactive session with a remote computer.</span></span>

## <span data-ttu-id="6a8b7-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6a8b7-106">SYNTAX</span></span>

```
Exit-PSSession [<CommonParameters>]
```

## <span data-ttu-id="6a8b7-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6a8b7-107">DESCRIPTION</span></span>
<span data-ttu-id="6a8b7-108">De **Exit-PSSession** -cmdlet beëindigt interactieve sessies die u hebt gestart met behulp van de cmdlet Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-108">The **Exit-PSSession** cmdlet ends interactive sessions that you started by using the Enter-PSSession cmdlet.</span></span>

<span data-ttu-id="6a8b7-109">U kunt ook het tref woord **Exit** gebruiken om een interactieve sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-109">You can also use the **Exit** keyword to end an interactive session.</span></span>
<span data-ttu-id="6a8b7-110">Het effect is hetzelfde als het gebruik van **Exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-110">The effect is the same as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="6a8b7-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6a8b7-111">EXAMPLES</span></span>

### <span data-ttu-id="6a8b7-112">Voor beeld 1: een interactieve sessie starten en stoppen</span><span class="sxs-lookup"><span data-stu-id="6a8b7-112">Example 1: Start and stop an interactive session</span></span>

```
PS C:\> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS C:\>
```

<span data-ttu-id="6a8b7-113">Met deze opdrachten wordt een interactieve sessie met de Server01 externe computer gestart en vervolgens gestopt.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-113">These commands start and then stop an interactive session with the Server01 remote computer.</span></span>

### <span data-ttu-id="6a8b7-114">Voor beeld 2: een interactieve sessie starten en stoppen met behulp van een PSSession-object</span><span class="sxs-lookup"><span data-stu-id="6a8b7-114">Example 2: Start and stop an interactive session by using a PSSession object</span></span>

```
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS C:\> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

<span data-ttu-id="6a8b7-115">Met deze opdrachten wordt een interactieve sessie gestart en gestopt met de Server01-computer die gebruikmaakt van een Windows Power shell-sessie ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="6a8b7-115">These commands start and stop an interactive session with the Server01 computer that uses a Windows PowerShell session ( **PSSession** ).</span></span>

<span data-ttu-id="6a8b7-116">Omdat de interactieve sessie is gestart met een Windows Power shell-sessie, is de **PSSession** nog steeds beschikbaar wanneer de interactieve sessie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-116">Because the interactive session was started by using a Windows PowerShell session, the **PSSession** is still available when the interactive session ends.</span></span>
<span data-ttu-id="6a8b7-117">Als u de para meter *ComputerName* gebruikt, wordt door **Enter-PSSession** een tijdelijke sessie gemaakt die wordt gesloten wanneer de interactieve sessie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-117">If you use the *ComputerName* parameter, **Enter-PSSession** creates a temporary session that it closes when the interactive session ends.</span></span>

<span data-ttu-id="6a8b7-118">De eerste opdracht maakt gebruik van de New-PSSession cmdlet om een **PSSession** te maken op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-118">The first command uses the New-PSSession cmdlet to create a **PSSession** on the Server01 computer.</span></span>
<span data-ttu-id="6a8b7-119">Met de opdracht slaat u de **PSSession** op in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-119">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="6a8b7-120">Met de tweede opdracht wordt **Enter-PSSession** gebruikt om een interactieve sessie te starten met behulp van de **PSSession** in $s.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-120">The second command uses **Enter-PSSession** to start an interactive session using the **PSSession** in $s.</span></span>

<span data-ttu-id="6a8b7-121">De derde opdracht maakt gebruik van **Exit-PSSession** om de interactieve sessie te beëindigen.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-121">The third command uses **Exit-PSSession** to stop the interactive session.</span></span>

<span data-ttu-id="6a8b7-122">Met de laatste opdracht wordt de **PSSession** weer gegeven in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-122">The final command displays the **PSSession** in the $s variable.</span></span>
<span data-ttu-id="6a8b7-123">De eigenschap **State** geeft aan dat de **PSSession** nog geopend is en beschikbaar is voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-123">The **State** property shows the **PSSession** is still open and available for use.</span></span>

### <span data-ttu-id="6a8b7-124">Voor beeld 3: het sleutel woord exit gebruiken om een sessie te stoppen</span><span class="sxs-lookup"><span data-stu-id="6a8b7-124">Example 3: Use the Exit keyword to stop a session</span></span>

```
PS C:\> Enter-PSSession -computername Server01
Server01\PS> exit
PS C:\>
```

<span data-ttu-id="6a8b7-125">In dit voor beeld wordt het sleutel woord **Exit** gebruikt om een interactieve sessie te stoppen die is gestart met **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-125">This example uses the **Exit** keyword to stop an interactive session started by using **Enter-PSSession**.</span></span>
<span data-ttu-id="6a8b7-126">Het sleutel woord **Exit** heeft hetzelfde effect als het gebruik van **Exit-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-126">The **Exit** keyword has the same effect as using **Exit-PSSession**.</span></span>

## <span data-ttu-id="6a8b7-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6a8b7-127">PARAMETERS</span></span>

### <span data-ttu-id="6a8b7-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a8b7-128">CommonParameters</span></span>
<span data-ttu-id="6a8b7-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a8b7-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a8b7-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="6a8b7-131">INPUTS</span></span>

### <span data-ttu-id="6a8b7-132">Geen</span><span class="sxs-lookup"><span data-stu-id="6a8b7-132">None</span></span>
<span data-ttu-id="6a8b7-133">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-133">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="6a8b7-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6a8b7-134">OUTPUTS</span></span>

### <span data-ttu-id="6a8b7-135">Geen</span><span class="sxs-lookup"><span data-stu-id="6a8b7-135">None</span></span>
<span data-ttu-id="6a8b7-136">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-136">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="6a8b7-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6a8b7-137">NOTES</span></span>

* <span data-ttu-id="6a8b7-138">Deze cmdlet heeft alleen de algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="6a8b7-138">This cmdlet takes only the common parameters.</span></span>


## <span data-ttu-id="6a8b7-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6a8b7-139">RELATED LINKS</span></span>

[<span data-ttu-id="6a8b7-140">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="6a8b7-140">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="6a8b7-141">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="6a8b7-141">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="6a8b7-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="6a8b7-142">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="6a8b7-143">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="6a8b7-143">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="6a8b7-144">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="6a8b7-144">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="6a8b7-145">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="6a8b7-145">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="6a8b7-146">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="6a8b7-146">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="6a8b7-147">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="6a8b7-147">Remove-PSSession</span></span>](Remove-PSSession.md)
