---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: Windows PowerShell starten
ms.openlocfilehash: 32ed85510899ea239c9dc332a023554ce9b53e47
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810440"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="83733-103">Windows PowerShell starten</span><span class="sxs-lookup"><span data-stu-id="83733-103">Starting Windows PowerShell</span></span>

<span data-ttu-id="83733-104">Windows Power shell is een script engine `.DLL` die is inge sloten in meerdere hosts.</span><span class="sxs-lookup"><span data-stu-id="83733-104">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="83733-105">De meest voorkomende hosts die u start, zijn de interactieve opdracht regel **Power shell. exe** en de interactieve script omgeving **powershell_ise. exe**.</span><span class="sxs-lookup"><span data-stu-id="83733-105">The most common hosts you'll start are the interactive command-line **powershell.exe** and the Interactive Scripting Environment **powershell_ise.exe**.</span></span>

<span data-ttu-id="83733-106">Als u Windows Power shell® wilt starten op Windows Server® 2012 R2, Windows® 8,1, Windows Server 2012 en Windows 8, raadpleegt u [algemene beheer taken en navigatie in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="83733-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="83733-107">De naam van de Power shell Core is gewijzigd in binary</span><span class="sxs-lookup"><span data-stu-id="83733-107">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="83733-108">Power shell core, aangeduid als Power shell, is versie 6 en hoger van de open source en maakt gebruik van .NET core.</span><span class="sxs-lookup"><span data-stu-id="83733-108">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="83733-109">Ondersteunde versies zijn beschikbaar in Windows, macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="83733-109">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="83733-110">Vanaf Power shell 6 heette het binaire bestand van Power shell **pwsh. exe** voor Windows en **pwsh** voor macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="83733-110">Beginning in PowerShell 6, the PowerShell binary was renamed **pwsh.exe** for Windows and **pwsh** for macOS and Linux.</span></span> <span data-ttu-id="83733-111">U kunt Power shell Preview-versies starten met behulp van **pwsh-preview**.</span><span class="sxs-lookup"><span data-stu-id="83733-111">You can start PowerShell preview versions using **pwsh-preview**.</span></span> <span data-ttu-id="83733-112">Zie [What's New in Power shell Core 6,0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) en [about pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="83733-112">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span></span>

<span data-ttu-id="83733-113">Gebruik de volgende koppelingen om de cmdlet-Naslag informatie en de installatie documentatie voor Power shell 7 te vinden:</span><span class="sxs-lookup"><span data-stu-id="83733-113">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="83733-114">Document</span><span class="sxs-lookup"><span data-stu-id="83733-114">Document</span></span> | <span data-ttu-id="83733-115">Koppeling</span><span class="sxs-lookup"><span data-stu-id="83733-115">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="83733-116">Cmdlet-naslaginformatie</span><span class="sxs-lookup"><span data-stu-id="83733-116">Cmdlet reference</span></span> | [<span data-ttu-id="83733-117">PowerShell-modulebrowser</span><span class="sxs-lookup"><span data-stu-id="83733-117">PowerShell Module Browser</span></span>](/powershell/module/?view=powershell-7) |
| <span data-ttu-id="83733-118">Windows-installatie</span><span class="sxs-lookup"><span data-stu-id="83733-118">Windows installation</span></span> | [<span data-ttu-id="83733-119">PowerShell Core in Windows installeren</span><span class="sxs-lookup"><span data-stu-id="83733-119">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| <span data-ttu-id="83733-120">macOS-installatie</span><span class="sxs-lookup"><span data-stu-id="83733-120">macOS installation</span></span> | <span data-ttu-id="83733-121">[Installing PowerShell Core on macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) (PowerShell Core installeren in macOS)</span><span class="sxs-lookup"><span data-stu-id="83733-121">[Installing PowerShell Core on macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7)</span></span> |
| <span data-ttu-id="83733-122">Linux-installatie</span><span class="sxs-lookup"><span data-stu-id="83733-122">Linux installation</span></span> | <span data-ttu-id="83733-123">[Installing PowerShell Core on Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) (PowerShell Core installeren in Linux)</span><span class="sxs-lookup"><span data-stu-id="83733-123">[Installing PowerShell Core on Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7)</span></span> |

<span data-ttu-id="83733-124">Zie [de Power shell-documentatie gebruiken](../how-to-use-docs.md)om inhoud voor andere Power shell-versies weer te geven.</span><span class="sxs-lookup"><span data-stu-id="83733-124">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="83733-125">Windows Power shell starten op eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="83733-125">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="83733-126">In deze sectie wordt uitgelegd hoe u Windows Power shell en Windows Power shell Integrated Scripting Environment (ISE) start op Windows® 7, Windows Server® 2008 R2 en Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="83733-126">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="83733-127">Ook wordt uitgelegd hoe u de optionele functie inschakelt voor Windows PowerShell ISE in Windows Power Shell 2,0 op Windows Server® 2008 R2 en Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="83733-127">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="83733-128">Gebruik een van de volgende methoden om de geïnstalleerde versie van Windows Power Shell 3,0 of Windows Power Shell 4,0 te starten, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="83733-128">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="83733-129">Vanuit het menu Start</span><span class="sxs-lookup"><span data-stu-id="83733-129">From the Start Menu</span></span>

- <span data-ttu-id="83733-130">Klik op **Start**, typ **Power shell**en klik vervolgens op **Windows Power shell**.</span><span class="sxs-lookup"><span data-stu-id="83733-130">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="83733-131">Klik in het menu **Start** op **Start**, klik op **alle Program ma's**, klik op **accessoires**, klik op de **Windows Power shell** -map en klik vervolgens op **Windows Power shell**.</span><span class="sxs-lookup"><span data-stu-id="83733-131">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="83733-132">Bij de opdracht prompt</span><span class="sxs-lookup"><span data-stu-id="83733-132">At the Command Prompt</span></span>

<span data-ttu-id="83733-133">In **cmd. exe**, Windows Power shell of Windows PowerShell ISE om Windows Power shell te starten, typt u:</span><span class="sxs-lookup"><span data-stu-id="83733-133">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="83733-134">U kunt ook de para meters van het programma **Power shell. exe** gebruiken om de sessie aan te passen.</span><span class="sxs-lookup"><span data-stu-id="83733-134">You can also use the parameters of the **powershell.exe** program to customize the session.</span></span> <span data-ttu-id="83733-135">Zie de [Help bij de opdracht regel van Power shell. exe](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="83733-135">For more information, see [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="83733-136">Met beheerders bevoegdheden (als administrator uitvoeren)</span><span class="sxs-lookup"><span data-stu-id="83733-136">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="83733-137">Klik op **Start**, typ **Power shell**, klik met de rechter muisknop op **Windows Power shell**en klik vervolgens op **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="83733-137">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="83733-138">Windows PowerShell ISE starten op eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="83733-138">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="83733-139">Gebruik een van de volgende methoden om Windows PowerShell ISE te starten.</span><span class="sxs-lookup"><span data-stu-id="83733-139">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="83733-140">Vanuit het menu Start</span><span class="sxs-lookup"><span data-stu-id="83733-140">From the Start Menu</span></span>

- <span data-ttu-id="83733-141">Klik op **Start**, typ **ISE**en klik vervolgens op **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="83733-141">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="83733-142">Klik in het menu **Start** op **Start**, klik op **alle Program ma's**, klik op **accessoires**, klik op de **Windows Power shell** -map en klik vervolgens op **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="83733-142">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="83733-143">Bij de opdracht prompt</span><span class="sxs-lookup"><span data-stu-id="83733-143">At the Command Prompt</span></span>

<span data-ttu-id="83733-144">In **cmd. exe**, Windows Power shell of Windows PowerShell ISE om Windows Power shell te starten, typt u:</span><span class="sxs-lookup"><span data-stu-id="83733-144">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="83733-145">of</span><span class="sxs-lookup"><span data-stu-id="83733-145">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="83733-146">Met beheerders bevoegdheden (als administrator uitvoeren)</span><span class="sxs-lookup"><span data-stu-id="83733-146">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="83733-147">Klik op **Start**, typ **ISE**, klik met de rechter muisknop op **Windows PowerShell ISE**en klik vervolgens op **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="83733-147">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="83733-148">Windows PowerShell ISE inschakelen op eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="83733-148">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="83733-149">In Windows Power Shell 4,0 en Windows Power Shell 3,0 is Windows PowerShell ISE standaard ingeschakeld in alle versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="83733-149">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="83733-150">Als dit nog niet is ingeschakeld, wordt het door Windows Management Framework 4,0 of Windows Management Framework 3,0 ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="83733-150">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="83733-151">In Windows Power Shell 2,0 is Windows PowerShell ISE standaard ingeschakeld in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="83733-151">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="83733-152">In Windows Server 2008 R2 en Windows Server 2008 is het echter een optionele functie.</span><span class="sxs-lookup"><span data-stu-id="83733-152">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="83733-153">Gebruik de volgende procedure om Windows PowerShell ISE in te scha kelen in Windows Power Shell 2,0 op Windows Server 2008 R2 of Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="83733-153">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="83733-154">Windows Power shell Integrated Scripting Environment (ISE) inschakelen</span><span class="sxs-lookup"><span data-stu-id="83733-154">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="83733-155">Start Serverbeheer.</span><span class="sxs-lookup"><span data-stu-id="83733-155">Start Server Manager.</span></span>
2. <span data-ttu-id="83733-156">Klik op **functies** en klik vervolgens op **onderdelen toevoegen**.</span><span class="sxs-lookup"><span data-stu-id="83733-156">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="83733-157">In functies selecteren klikt u op Windows Power shell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="83733-157">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="83733-158">De 32-bits versie van Windows Power shell starten</span><span class="sxs-lookup"><span data-stu-id="83733-158">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="83733-159">Wanneer u Windows Power shell installeert op een 64-bits computer, wordt **Windows Power shell (x86)**, een 32-bits versie van Windows Power shell, naast de 64-bits versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="83733-159">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="83733-160">Wanneer u Windows Power shell uitvoert, wordt standaard de 64-bits versie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="83733-160">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="83733-161">Het kan echter ook voor komen dat u **Windows Power shell (x86)** moet uitvoeren, bijvoorbeeld wanneer u een module gebruikt waarvoor de 32-bits versie vereist is of wanneer u extern verbinding maakt met een 32-bits computer.</span><span class="sxs-lookup"><span data-stu-id="83733-161">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="83733-162">Als u een 32-bits versie van Windows Power shell wilt starten, gebruikt u een van de volgende procedures.</span><span class="sxs-lookup"><span data-stu-id="83733-162">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="83733-163">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="83733-163">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="83733-164">Typ **Windows Power shell (x86)** in het **Start** scherm.</span><span class="sxs-lookup"><span data-stu-id="83733-164">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="83733-165">Klik op de tegel **Windows Power shell x86** .</span><span class="sxs-lookup"><span data-stu-id="83733-165">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="83733-166">In **Serverbeheer**, in het menu **extra** , selecteert u **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-166">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-167">Verplaats de cursor op het bureau blad naar de rechter bovenhoek, klik op **zoeken**, typ **Power shell x86** en klik vervolgens op **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-167">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-168">Voer vanaf de opdracht regel het volgende in:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="83733-168">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="83733-169">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="83733-169">In Windows Server® 2012</span></span>

- <span data-ttu-id="83733-170">Typ **Power shell** in het **Start** scherm en klik vervolgens op **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-170">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-171">In **Serverbeheer**, in het menu **extra** , selecteert u **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-171">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-172">Verplaats de cursor op het bureau blad naar de rechter bovenhoek, klik op **zoeken**, typ **Power shell** en klik vervolgens op **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-172">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-173">Voer vanaf de opdracht regel het volgende in:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="83733-173">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="83733-174">In Windows® 8,1</span><span class="sxs-lookup"><span data-stu-id="83733-174">In Windows® 8.1</span></span>

- <span data-ttu-id="83733-175">Typ **Windows Power shell (x86)** in het **Start** scherm.</span><span class="sxs-lookup"><span data-stu-id="83733-175">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="83733-176">Klik op de tegel **Windows Power shell x86** .</span><span class="sxs-lookup"><span data-stu-id="83733-176">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="83733-177">Als u [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) uitvoert voor Windows 8,1, kunt u ook Windows Power shell x86 openen vanuit het menu van **Server beheer** .</span><span class="sxs-lookup"><span data-stu-id="83733-177">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="83733-178">Selecteer **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-178">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-179">Verplaats de cursor op het bureau blad naar de rechter bovenhoek, klik op **zoeken**, typ **Power shell x86** en klik vervolgens op **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-179">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-180">Voer vanaf de opdracht regel het volgende in:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="83733-180">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="83733-181">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="83733-181">In Windows® 8</span></span>

- <span data-ttu-id="83733-182">Verplaats de cursor in het **Start** scherm naar de rechter bovenhoek, klik op **instellingen**, klik op **tegels**en verplaats de schuif regelaar **systeem beheer weer geven** naar **Ja**.</span><span class="sxs-lookup"><span data-stu-id="83733-182">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="83733-183">Vervolgens typt u **Power shell** en klikt u op **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-183">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-184">Als u [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) voor Windows 8 uitvoert, kunt u ook Windows Power shell x86 openen vanuit het menu van **Server beheer** .</span><span class="sxs-lookup"><span data-stu-id="83733-184">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="83733-185">Selecteer **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-185">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-186">Typ **Power shell (x86)** op het **Start** scherm of op het bureau blad en klik vervolgens op **Windows Power shell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="83733-186">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="83733-187">Voer vanaf de opdracht regel het volgende in:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="83733-187">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
