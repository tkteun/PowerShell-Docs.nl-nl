---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: De Windows Power Shell 2,0-engine gebruiken
description: De Windows Power Shell 2,0-engine is uitsluitend bedoeld om te worden gebruikt wanneer een bestaand script of hostprogramma niet kan worden uitgevoerd, omdat host-Program ma's die zijn geschreven voor Windows Power Shell 2,0 en die zijn gecompileerd met CLR 2,0, niet kunnen worden uitgevoerd zonder aanpassing.
ms.openlocfilehash: 214b87b7314f31974801bb07f98ddea3b68008f0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663999"
---
# <a name="using-the-windows-powershell-20-engine"></a><span data-ttu-id="9e54d-104">De Windows Power Shell 2,0-engine gebruiken</span><span class="sxs-lookup"><span data-stu-id="9e54d-104">Using the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="9e54d-105">Windows Power shell is ontworpen om achterwaarts compatibel te zijn met eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="9e54d-105">Windows PowerShell is designed to be backward compatible with previous versions.</span></span> <span data-ttu-id="9e54d-106">Cmdlets, providers, modules, modules en scripts die zijn geschreven voor Windows Power Shell 2,0, worden ongewijzigd uitgevoerd in nieuwere versies van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9e54d-106">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in newer versions Windows PowerShell.</span></span> <span data-ttu-id="9e54d-107">Microsoft .NET Framework 4 heeft echter het runtime-activerings beleid gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9e54d-107">However, Microsoft .NET Framework 4 changed the runtime activation policy.</span></span>
<span data-ttu-id="9e54d-108">Windows Power shell-host-Program ma's die zijn geschreven voor Windows Power Shell 2,0 en gecompileerd met common language runtime (CLR) 2,0 kunnen niet zonder aanpassing worden uitgevoerd in nieuwe versies van Windows Power shell die zijn gecompileerd met CLR 4,0 (of hoger).</span><span class="sxs-lookup"><span data-stu-id="9e54d-108">Windows PowerShell host programs written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in new versions Windows PowerShell that are compiled with CLR 4.0 (or higher).</span></span>

<span data-ttu-id="9e54d-109">De Windows Power Shell 2,0-engine is alleen bedoeld voor gebruik wanneer een bestaand script of hostprogramma niet kan worden uitgevoerd, omdat het niet compatibel is met Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="9e54d-109">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 5.1.</span></span> <span data-ttu-id="9e54d-110">Voor beelden hiervan zijn oudere versies van Exchange-of SQL Server-modules.</span><span class="sxs-lookup"><span data-stu-id="9e54d-110">Examples of this include older versions of Exchange or SQL Server modules.</span></span> <span data-ttu-id="9e54d-111">Dergelijke gevallen worden naar verwachting zeldzaam.</span><span class="sxs-lookup"><span data-stu-id="9e54d-111">Such cases are expected to be rare.</span></span>

<span data-ttu-id="9e54d-112">Veel Program ma's die de Windows Power Shell 2,0-engine nodig hebben, worden automatisch gestart.</span><span class="sxs-lookup"><span data-stu-id="9e54d-112">Many programs that require the Windows PowerShell 2.0 Engine start it automatically.</span></span> <span data-ttu-id="9e54d-113">Deze instructies zijn opgenomen in zeldzame gevallen waarin u de engine hand matig moet starten.</span><span class="sxs-lookup"><span data-stu-id="9e54d-113">These instructions are included for the rare situations in which you need to start the engine manually.</span></span>

## <a name="deprecation-and-security-concerns"></a><span data-ttu-id="9e54d-114">Problemen met afschaffing en beveiliging</span><span class="sxs-lookup"><span data-stu-id="9e54d-114">Deprecation and security concerns</span></span>

<span data-ttu-id="9e54d-115">Windows Power Shell 2,0 is afgeschaft in augustus 2017.</span><span class="sxs-lookup"><span data-stu-id="9e54d-115">Windows PowerShell 2.0 was deprecated in August, 2017.</span></span> <span data-ttu-id="9e54d-116">Zie de [aankondiging][] in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9e54d-116">For more information, see the [announcement][] on the PowerShell blog.</span></span>

<span data-ttu-id="9e54d-117">Er ontbreken in Windows Power Shell 2,0 een aanzienlijke hoeveelheid aan de functies voor beveiliging en beveiliging die zijn toegevoegd in versie 3, 4 en 5.</span><span class="sxs-lookup"><span data-stu-id="9e54d-117">Windows PowerShell 2.0 is missing a significant amount of the hardening and security features added in versions 3, 4, and 5.</span></span> <span data-ttu-id="9e54d-118">We raden u ten zeerste aan gebruikers niet te gebruiken als ze dit kunnen helpen.</span><span class="sxs-lookup"><span data-stu-id="9e54d-118">We highly, highly recommend that users not use it if they can help it.</span></span> <span data-ttu-id="9e54d-119">Zie voor meer informatie [een vergelijking van shell-en script taal beveiliging][] en [Power shell ♥ het blauwe team][blueteam].</span><span class="sxs-lookup"><span data-stu-id="9e54d-119">For more information, see [A Comparison of Shell and Scripting Language Security][] and [PowerShell ♥ the Blue Team][blueteam].</span></span>

## <a name="installing-and-enabling-required-programs"></a><span data-ttu-id="9e54d-120">Vereiste Program Ma's installeren en inschakelen</span><span class="sxs-lookup"><span data-stu-id="9e54d-120">Installing and Enabling Required Programs</span></span>

<span data-ttu-id="9e54d-121">Voordat u de Windows Power Shell 2,0-Engine start, schakelt u de Windows Power Shell 2,0-engine in en Microsoft .NET Framework 3,5 met Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="9e54d-121">Before starting the Windows PowerShell 2.0 Engine, enable the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 with Service Pack 1.</span></span> <span data-ttu-id="9e54d-122">Zie [Windows Power Shell installeren][]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="9e54d-122">For instructions, see [Installing Windows PowerShell][].</span></span>

<span data-ttu-id="9e54d-123">Systemen waarop Windows Management Framework 3,0 of hoger is geïnstalleerd, hebben alle vereiste onderdelen.</span><span class="sxs-lookup"><span data-stu-id="9e54d-123">Systems on which Windows Management Framework 3.0 or higher is installed have all of the required components.</span></span> <span data-ttu-id="9e54d-124">U hoeft verder niets te configureren.</span><span class="sxs-lookup"><span data-stu-id="9e54d-124">No further configuration is necessary.</span></span> <span data-ttu-id="9e54d-125">Zie [WMF installeren en configureren][]voor meer informatie over het installeren van Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="9e54d-125">For information about installing Windows Management Framework, see [Install and configure WMF][].</span></span>

## <a name="how-to-start-the-windows-powershell-20-engine"></a><span data-ttu-id="9e54d-126">De Windows Power Shell 2,0-engine starten</span><span class="sxs-lookup"><span data-stu-id="9e54d-126">How to start the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="9e54d-127">Wanneer u Windows Power shell start, wordt standaard de nieuwste versie gestart.</span><span class="sxs-lookup"><span data-stu-id="9e54d-127">When you start Windows PowerShell the newest version starts by default.</span></span> <span data-ttu-id="9e54d-128">Als u Windows Power shell met de Windows Power Shell 2,0-engine wilt starten, gebruikt u de versie parameter van `PowerShell.exe` .</span><span class="sxs-lookup"><span data-stu-id="9e54d-128">To start Windows PowerShell with the Windows PowerShell 2.0 Engine, use the Version parameter of `PowerShell.exe`.</span></span> <span data-ttu-id="9e54d-129">U kunt de opdracht uitvoeren vanaf een opdracht prompt, waaronder Windows Power shell en Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="9e54d-129">You can run the command at any command prompt, including Windows PowerShell and Cmd.exe.</span></span>

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a><span data-ttu-id="9e54d-130">Een externe sessie starten met de Windows Power Shell 2,0-engine</span><span class="sxs-lookup"><span data-stu-id="9e54d-130">How to start a remote session with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="9e54d-131">Als u de Windows Power Shell 2,0-engine wilt uitvoeren in een externe sessie, maakt u een sessie configuratie (ook wel een _eind punt_ genoemd) op de externe computer die de Windows power Shell 2,0-engine laadt.</span><span class="sxs-lookup"><span data-stu-id="9e54d-131">To run the Windows PowerShell 2.0 Engine in a remote session, create a session configuration (also known as an _endpoint_ ) on the remote computer that loads the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="9e54d-132">De sessie configuratie wordt opgeslagen op de externe computer en kan worden gebruikt door een geautoriseerde gebruiker om sessies te maken die gebruikmaken van de Windows Power Shell 2,0-engine.</span><span class="sxs-lookup"><span data-stu-id="9e54d-132">The session configuration is saved on the remote computer and can be used by any authorized user to create sessions that use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="9e54d-133">Dit is een geavanceerde taak die meestal wordt uitgevoerd door een systeem beheerder.</span><span class="sxs-lookup"><span data-stu-id="9e54d-133">This is an advanced task that is typically performed by a system administrator.</span></span>

<span data-ttu-id="9e54d-134">In de volgende procedure wordt de para meter **PSVersion** van de cmdlet [REGI ster-PSSessionConfiguration][] gebruikt om een sessie configuratie te maken die gebruikmaakt van de Windows Power Shell 2,0-engine.</span><span class="sxs-lookup"><span data-stu-id="9e54d-134">The following procedure uses the **PSVersion** parameter of the [Register-PSSessionConfiguration][] cmdlet to create a session configuration that uses the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="9e54d-135">U kunt ook de para meter **PowerShellVersion** van de cmdlet [New-PSSessionConfigurationFile][] gebruiken om een sessie configuratie bestand te maken voor een sessie die de Windows Power Shell 2,0-engine laadt en u kunt de **PSVersion** -para meter van de para meter [set-PSSessionConfiguration][] gebruiken om een sessie configuratie te wijzigen voor het gebruik van de Windows Power Shell 2,0-engine.</span><span class="sxs-lookup"><span data-stu-id="9e54d-135">You can also use the **PowerShellVersion** parameter of the [New-PSSessionConfigurationFile][] cmdlet to create a session configuration file for a session that loads the Windows PowerShell 2.0 Engine and you can use the **PSVersion** parameter of the [Set-PSSessionConfiguration][] parameter to change a session configuration to use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="9e54d-136">Zie [about_Session_Configuration_Files][]voor meer informatie over sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="9e54d-136">For more information about session configuration files, see [about_Session_Configuration_Files][].</span></span>
<span data-ttu-id="9e54d-137">Zie [about_Session_Configurations][]voor meer informatie over de configuratie van sessies, met inbegrip van Setup en beveiliging.</span><span class="sxs-lookup"><span data-stu-id="9e54d-137">For information about session configurations, including setup and security, see [about_Session_Configurations][].</span></span>

### <a name="to-start-a-remote-windows-powershell-20-session"></a><span data-ttu-id="9e54d-138">Een externe Windows Power Shell 2,0-sessie starten</span><span class="sxs-lookup"><span data-stu-id="9e54d-138">To start a remote Windows PowerShell 2.0 session</span></span>

1. <span data-ttu-id="9e54d-139">Als u een sessie configuratie wilt maken waarvoor de Windows Power Shell 2,0-engine vereist is, gebruikt u de para meter **PSVersion** van de `Register-PSSessionConfiguration` cmdlet met de waarde `2.0` .</span><span class="sxs-lookup"><span data-stu-id="9e54d-139">To create a session configuration that requires the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet with a value of `2.0`.</span></span>
   <span data-ttu-id="9e54d-140">Voer deze opdracht uit op de computer aan de server zijde of het ontvangende einde van de verbinding.</span><span class="sxs-lookup"><span data-stu-id="9e54d-140">Run this command on the computer at the "server side" or receiving end of the connection.</span></span>

   <span data-ttu-id="9e54d-141">Met de volgende voorbeeld opdracht wordt de PS2-sessie configuratie op de Server01-computer gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9e54d-141">The following sample command creates the PS2 session configuration on the Server01 computer.</span></span> <span data-ttu-id="9e54d-142">Als u deze opdracht wilt uitvoeren, start u Windows Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="9e54d-142">To run this command, start Windows PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. <span data-ttu-id="9e54d-143">Als u een sessie op de Server01-computer wilt maken die gebruikmaakt van de PS2-sessie configuratie, gebruikt u de para meter **configuratiepad** van cmdlets die een externe sessie maken, zoals de cmdlet New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="9e54d-143">To create a session on the Server01 computer that uses the PS2 session configuration, use the **ConfigurationName** parameter of cmdlets that create a remote session, such as the \`New-PSSession cmdlet.</span></span>

   <span data-ttu-id="9e54d-144">Wanneer een sessie die gebruikmaakt van de sessie configuratie wordt gestart, wordt de Windows Power Shell 2,0-engine automatisch in de sessie geladen.</span><span class="sxs-lookup"><span data-stu-id="9e54d-144">When a session that uses the session configuration starts, the Windows PowerShell 2.0 Engine is automatically loaded into the session.</span></span>

   <span data-ttu-id="9e54d-145">Met de volgende opdracht wordt een sessie gestart op de Server01-computer die gebruikmaakt van de PS2-sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="9e54d-145">The following command starts a session on the Server01 computer that uses the PS2 session configuration.</span></span> <span data-ttu-id="9e54d-146">Met de opdracht wordt de sessie opgeslagen in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="9e54d-146">The command saves the session in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a><span data-ttu-id="9e54d-147">Een achtergrond taak starten met de Windows Power Shell 2,0-engine</span><span class="sxs-lookup"><span data-stu-id="9e54d-147">How to start a background job with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="9e54d-148">Als u een achtergrond taak wilt starten met de Windows Power Shell 2,0-engine, gebruikt u de para meter **PSVersion** van de cmdlet [Start-job][] .</span><span class="sxs-lookup"><span data-stu-id="9e54d-148">To start a background job with the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Start-Job][] cmdlet.</span></span>

<span data-ttu-id="9e54d-149">Met de volgende opdracht wordt een achtergrond taak gestart met de Windows Power Shell 2,0-engine</span><span class="sxs-lookup"><span data-stu-id="9e54d-149">The following command starts a background job with the Windows PowerShell 2.0 Engine</span></span>

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

<span data-ttu-id="9e54d-150">Zie [about_Jobs][]voor meer informatie over achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="9e54d-150">For more information about background jobs, see [about_Jobs][].</span></span>

<!-- link references -->
[Announcement]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[announcement]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Een vergelijking van de beveiliging van shell-en script taal]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[A Comparison of Shell and Scripting Language Security]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Windows PowerShell installeren]: install/Installing-Windows-PowerShell.md
[Installing Windows PowerShell]: install/Installing-Windows-PowerShell.md
[WMF installeren en configureren]: wmf/setup/install-configure.md
[Install and configure WMF]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfigurationFile
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Begin taak]: /powershell/module/microsoft.powershell.core/start-job
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
