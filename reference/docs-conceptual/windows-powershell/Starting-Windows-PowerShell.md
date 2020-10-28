---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: Windows PowerShell starten
description: In dit artikel wordt uitgelegd hoe u verschillende versies van Power shell kunt starten.
ms.openlocfilehash: 47da7d85c9f7e6966a7f7e809c77979cd24cf129
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664018"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="8835b-104">Windows PowerShell starten</span><span class="sxs-lookup"><span data-stu-id="8835b-104">Starting Windows PowerShell</span></span>

<span data-ttu-id="8835b-105">Windows Power shell is een script engine `.DLL` die is inge sloten in meerdere hosts.</span><span class="sxs-lookup"><span data-stu-id="8835b-105">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="8835b-106">De meest voorkomende hosts die u start, zijn de interactieve opdracht regel `powershell.exe` en de interactieve script omgeving `powershell_ise.exe` .</span><span class="sxs-lookup"><span data-stu-id="8835b-106">The most common hosts you'll start are the interactive command-line `powershell.exe` and the Interactive Scripting Environment `powershell_ise.exe`.</span></span>

<span data-ttu-id="8835b-107">Als u Windows Power shell wilt starten &reg; op Windows server &reg; 2012 R2, Windows &reg; 8,1, Windows Server 2012 en Windows 8, raadpleegt u [algemene beheer taken en navigatie in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="8835b-107">To start Windows PowerShell&reg; on Windows Server&reg; 2012 R2, Windows&reg; 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="8835b-108">De naam van de Power shell Core is gewijzigd in binary</span><span class="sxs-lookup"><span data-stu-id="8835b-108">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="8835b-109">Power shell core, aangeduid als Power shell, is versie 6 en hoger van de open source en maakt gebruik van .NET core.</span><span class="sxs-lookup"><span data-stu-id="8835b-109">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="8835b-110">Ondersteunde versies zijn beschikbaar in Windows, macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="8835b-110">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="8835b-111">Vanaf Power shell 6 heette het binaire bestand van Power shell een andere naam gekregen `pwsh.exe` voor Windows en `pwsh` voor MacOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="8835b-111">Beginning in PowerShell 6, the PowerShell binary was renamed `pwsh.exe` for Windows and `pwsh` for macOS and Linux.</span></span> <span data-ttu-id="8835b-112">U kunt Power shell Preview-versies starten met `pwsh-preview` .</span><span class="sxs-lookup"><span data-stu-id="8835b-112">You can start PowerShell preview versions using `pwsh-preview`.</span></span> <span data-ttu-id="8835b-113">Zie [What's New in Power shell Core 6,0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) en [about pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8835b-113">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh).</span></span>

<span data-ttu-id="8835b-114">Gebruik de volgende koppelingen om de cmdlet-Naslag informatie en de installatie documentatie voor Power shell 7 te vinden:</span><span class="sxs-lookup"><span data-stu-id="8835b-114">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="8835b-115">Document</span><span class="sxs-lookup"><span data-stu-id="8835b-115">Document</span></span> | <span data-ttu-id="8835b-116">Koppeling</span><span class="sxs-lookup"><span data-stu-id="8835b-116">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="8835b-117">Cmdlet-naslaginformatie</span><span class="sxs-lookup"><span data-stu-id="8835b-117">Cmdlet reference</span></span> | [<span data-ttu-id="8835b-118">PowerShell-modulebrowser</span><span class="sxs-lookup"><span data-stu-id="8835b-118">PowerShell Module Browser</span></span>](/powershell/module/) |
| <span data-ttu-id="8835b-119">Windows-installatie</span><span class="sxs-lookup"><span data-stu-id="8835b-119">Windows installation</span></span> | [<span data-ttu-id="8835b-120">PowerShell Core in Windows installeren</span><span class="sxs-lookup"><span data-stu-id="8835b-120">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows) |
| <span data-ttu-id="8835b-121">macOS-installatie</span><span class="sxs-lookup"><span data-stu-id="8835b-121">macOS installation</span></span> | <span data-ttu-id="8835b-122">[Installing PowerShell Core on macOS](/powershell/scripting/install/installing-powershell-core-on-macos) (PowerShell Core installeren in macOS)</span><span class="sxs-lookup"><span data-stu-id="8835b-122">[Installing PowerShell Core on macOS](/powershell/scripting/install/installing-powershell-core-on-macos)</span></span> |
| <span data-ttu-id="8835b-123">Linux-installatie</span><span class="sxs-lookup"><span data-stu-id="8835b-123">Linux installation</span></span> | <span data-ttu-id="8835b-124">[Installing PowerShell Core on Linux](/powershell/scripting/install/installing-powershell-core-on-linux) (PowerShell Core installeren in Linux)</span><span class="sxs-lookup"><span data-stu-id="8835b-124">[Installing PowerShell Core on Linux](/powershell/scripting/install/installing-powershell-core-on-linux)</span></span> |

<span data-ttu-id="8835b-125">Zie [de Power shell-documentatie gebruiken](../how-to-use-docs.md)om inhoud voor andere Power shell-versies weer te geven.</span><span class="sxs-lookup"><span data-stu-id="8835b-125">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="8835b-126">Windows Power shell starten op eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="8835b-126">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="8835b-127">In deze sectie wordt uitgelegd hoe u Windows Power shell en Windows Power shell Integrated Scripting Environment (ISE) start op Windows &reg; 7, Windows Server &reg; 2008 R2 en Windows Server &reg; 2008.</span><span class="sxs-lookup"><span data-stu-id="8835b-127">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows&reg; 7, Windows Server&reg; 2008 R2, and Windows Server&reg; 2008.</span></span> <span data-ttu-id="8835b-128">Ook wordt uitgelegd hoe u de optionele functie inschakelt voor Windows PowerShell ISE in Windows Power Shell 2,0 op Windows Server &reg; 2008 R2 en Windows server &reg; 2008.</span><span class="sxs-lookup"><span data-stu-id="8835b-128">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server&reg; 2008 R2 and Windows Server&reg; 2008.</span></span>

<span data-ttu-id="8835b-129">Gebruik een van de volgende methoden om de geïnstalleerde versie van Windows Power Shell 3,0 of Windows Power Shell 4,0 te starten, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="8835b-129">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="8835b-130">Vanuit het menu Start</span><span class="sxs-lookup"><span data-stu-id="8835b-130">From the Start Menu</span></span>

- <span data-ttu-id="8835b-131">Klik op **Start** , typ **Power shell** en klik vervolgens op **Windows Power shell** .</span><span class="sxs-lookup"><span data-stu-id="8835b-131">Click **Start** , type **PowerShell** , and then click **Windows PowerShell** .</span></span>
- <span data-ttu-id="8835b-132">Klik in het menu **Start** op **Start** , klik op **alle Program ma's** , klik op **accessoires** , klik op de **Windows Power shell** -map en klik vervolgens op **Windows Power shell** .</span><span class="sxs-lookup"><span data-stu-id="8835b-132">From the **Start** menu, click **Start** , click **All Programs** , click **Accessories** , click the **Windows PowerShell** folder, and then click **Windows PowerShell** .</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="8835b-133">Bij de opdracht prompt</span><span class="sxs-lookup"><span data-stu-id="8835b-133">At the Command Prompt</span></span>

<span data-ttu-id="8835b-134">In **cmd.exe** , Windows Power shell of Windows PowerShell ISE om Windows Power shell te starten, typt u:</span><span class="sxs-lookup"><span data-stu-id="8835b-134">In **cmd.exe** , Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="8835b-135">U kunt ook de para meters van het `powershell.exe` programma gebruiken om de sessie aan te passen.</span><span class="sxs-lookup"><span data-stu-id="8835b-135">You can also use the parameters of the `powershell.exe` program to customize the session.</span></span> <span data-ttu-id="8835b-136">Zie [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8835b-136">For more information, see [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="8835b-137">Met beheerders bevoegdheden (als administrator uitvoeren)</span><span class="sxs-lookup"><span data-stu-id="8835b-137">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="8835b-138">Klik op **Start** , typ **Power shell** , klik met de rechter muisknop op **Windows Power shell** en klik vervolgens op **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="8835b-138">Click **Start** , type **PowerShell** , right-click **Windows PowerShell** , and then click **Run as administrator** .</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="8835b-139">Windows PowerShell ISE starten op eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="8835b-139">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="8835b-140">Gebruik een van de volgende methoden om Windows PowerShell ISE te starten.</span><span class="sxs-lookup"><span data-stu-id="8835b-140">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="8835b-141">Vanuit het menu Start</span><span class="sxs-lookup"><span data-stu-id="8835b-141">From the Start Menu</span></span>

- <span data-ttu-id="8835b-142">Klik op **Start** , typ **ISE** en klik vervolgens op **Windows PowerShell ISE** .</span><span class="sxs-lookup"><span data-stu-id="8835b-142">Click **Start** , type **ISE** , and then click **Windows PowerShell ISE** .</span></span>
- <span data-ttu-id="8835b-143">Klik in het menu **Start** op **Start** , klik op **alle Program ma's** , klik op **accessoires** , klik op de **Windows Power shell** -map en klik vervolgens op **Windows PowerShell ISE** .</span><span class="sxs-lookup"><span data-stu-id="8835b-143">From the **Start** menu, click **Start** , click **All Programs** , click **Accessories** , click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE** .</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="8835b-144">Bij de opdracht prompt</span><span class="sxs-lookup"><span data-stu-id="8835b-144">At the Command Prompt</span></span>

<span data-ttu-id="8835b-145">In `cmd.exe` , Windows Power shell of Windows PowerShell ISE om Windows Power shell te starten, typt u:</span><span class="sxs-lookup"><span data-stu-id="8835b-145">In `cmd.exe`, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="8835b-146">of</span><span class="sxs-lookup"><span data-stu-id="8835b-146">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="8835b-147">Met beheerders bevoegdheden (als administrator uitvoeren)</span><span class="sxs-lookup"><span data-stu-id="8835b-147">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="8835b-148">Klik op **Start** , typ **ISE** , klik met de rechter muisknop op **Windows PowerShell ISE** en klik vervolgens op **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="8835b-148">Click **Start** , type **ISE** , right-click **Windows PowerShell ISE** , and then click **Run as administrator** .</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="8835b-149">Windows PowerShell ISE inschakelen op eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="8835b-149">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="8835b-150">In Windows Power Shell 4,0 en Windows Power Shell 3,0 is Windows PowerShell ISE standaard ingeschakeld in alle versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="8835b-150">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="8835b-151">Als dit nog niet is ingeschakeld, wordt het door Windows Management Framework 4,0 of Windows Management Framework 3,0 ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="8835b-151">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="8835b-152">In Windows Power Shell 2,0 is Windows PowerShell ISE standaard ingeschakeld in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="8835b-152">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="8835b-153">In Windows Server 2008 R2 en Windows Server 2008 is het echter een optionele functie.</span><span class="sxs-lookup"><span data-stu-id="8835b-153">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="8835b-154">Gebruik de volgende procedure om Windows PowerShell ISE in te scha kelen in Windows Power Shell 2,0 op Windows Server 2008 R2 of Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="8835b-154">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="8835b-155">Windows Power shell Integrated Scripting Environment (ISE) inschakelen</span><span class="sxs-lookup"><span data-stu-id="8835b-155">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="8835b-156">Start Serverbeheer.</span><span class="sxs-lookup"><span data-stu-id="8835b-156">Start Server Manager.</span></span>
2. <span data-ttu-id="8835b-157">Klik op **functies** en klik vervolgens op **onderdelen toevoegen** .</span><span class="sxs-lookup"><span data-stu-id="8835b-157">Click **Features** and then click **Add Features** .</span></span>
3. <span data-ttu-id="8835b-158">In functies selecteren klikt u op Windows Power shell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="8835b-158">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="8835b-159">De 32-bits versie van Windows Power shell starten</span><span class="sxs-lookup"><span data-stu-id="8835b-159">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="8835b-160">Wanneer u Windows Power shell installeert op een 64-bits computer, wordt **Windows Power shell (x86)** , een 32-bits versie van Windows Power shell, naast de 64-bits versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8835b-160">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)** , a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="8835b-161">Wanneer u Windows Power shell uitvoert, wordt standaard de 64-bits versie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8835b-161">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="8835b-162">Het kan echter ook voor komen dat u **Windows Power shell (x86)** moet uitvoeren, bijvoorbeeld wanneer u een module gebruikt waarvoor de 32-bits versie vereist is of wanneer u extern verbinding maakt met een 32-bits computer.</span><span class="sxs-lookup"><span data-stu-id="8835b-162">However, you might occasionally need to run **Windows PowerShell (x86)** , such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="8835b-163">Als u een 32-bits versie van Windows Power shell wilt starten, gebruikt u een van de volgende procedures.</span><span class="sxs-lookup"><span data-stu-id="8835b-163">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-serverreg-2012-r2"></a><span data-ttu-id="8835b-164">In Windows Server &reg; 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8835b-164">In Windows Server&reg; 2012 R2</span></span>

- <span data-ttu-id="8835b-165">Typ **Windows Power shell (x86)** in het **Start** scherm.</span><span class="sxs-lookup"><span data-stu-id="8835b-165">On the **Start** screen, type **Windows PowerShell (x86)** .</span></span> <span data-ttu-id="8835b-166">Klik op de tegel **Windows Power shell x86** .</span><span class="sxs-lookup"><span data-stu-id="8835b-166">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="8835b-167">In **Serverbeheer** , in het menu **extra** , selecteert u **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-167">In **Server Manager** , from the **Tools** menu, select **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-168">Verplaats de cursor op het bureau blad naar de rechter bovenhoek, klik op **zoeken** , typ **Power shell x86** en klik vervolgens op **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-168">On the desktop, move the cursor to the upper right corner, click **Search** , type **PowerShell x86** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-169">Voer vanaf de opdracht regel het volgende in: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="8835b-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-serverreg-2012"></a><span data-ttu-id="8835b-170">In Windows Server &reg; 2012</span><span class="sxs-lookup"><span data-stu-id="8835b-170">In Windows Server&reg; 2012</span></span>

- <span data-ttu-id="8835b-171">Typ **Power shell** in het **Start** scherm en klik vervolgens op **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-171">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-172">In **Serverbeheer** , in het menu **extra** , selecteert u **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-172">In **Server Manager** , from the **Tools** menu, select **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-173">Verplaats de cursor op het bureau blad naar de rechter bovenhoek, klik op **zoeken** , typ **Power shell** en klik vervolgens op **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-173">On the desktop, move the cursor to the upper right corner, click **Search** , type **PowerShell** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-174">Voer vanaf de opdracht regel het volgende in: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="8835b-174">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windowsreg-81"></a><span data-ttu-id="8835b-175">In Windows &reg; 8,1</span><span class="sxs-lookup"><span data-stu-id="8835b-175">In Windows&reg; 8.1</span></span>

- <span data-ttu-id="8835b-176">Typ **Windows Power shell (x86)** in het **Start** scherm.</span><span class="sxs-lookup"><span data-stu-id="8835b-176">On the **Start** screen, type **Windows PowerShell (x86)** .</span></span> <span data-ttu-id="8835b-177">Klik op de tegel **Windows Power shell x86** .</span><span class="sxs-lookup"><span data-stu-id="8835b-177">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="8835b-178">Als u [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) uitvoert voor Windows 8,1, kunt u ook Windows Power shell x86 openen vanuit het menu van **Server beheer** .</span><span class="sxs-lookup"><span data-stu-id="8835b-178">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="8835b-179">Selecteer **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-179">Select **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-180">Verplaats de cursor op het bureau blad naar de rechter bovenhoek, klik op **zoeken** , typ **Power shell x86** en klik vervolgens op **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-180">On the desktop, move the cursor to the upper right corner, click **Search** , type **PowerShell x86** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-181">Voer vanaf de opdracht regel het volgende in: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="8835b-181">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windowsreg-8"></a><span data-ttu-id="8835b-182">In Windows &reg; 8</span><span class="sxs-lookup"><span data-stu-id="8835b-182">In Windows&reg; 8</span></span>

- <span data-ttu-id="8835b-183">Verplaats de cursor in het **Start** scherm naar de rechter bovenhoek, klik op **instellingen** , klik op **tegels** en verplaats de schuif regelaar **systeem beheer weer geven** naar **Ja** .</span><span class="sxs-lookup"><span data-stu-id="8835b-183">On the **Start** screen, move the cursor to the upper right corner, click **Settings** , click **Tiles** , and then move the **Show Administrative Tools** slider to **Yes** .</span></span> <span data-ttu-id="8835b-184">Vervolgens typt u **Power shell** en klikt u op **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-184">Then, type **PowerShell** and click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-185">Als u [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) voor Windows 8 uitvoert, kunt u ook Windows Power shell x86 openen vanuit het menu van **Server beheer** .</span><span class="sxs-lookup"><span data-stu-id="8835b-185">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="8835b-186">Selecteer **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-186">Select **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-187">Typ **Power shell (x86)** op het **Start** scherm of op het bureau blad en klik vervolgens op **Windows Power shell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="8835b-187">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="8835b-188">Voer vanaf de opdracht regel het volgende in: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="8835b-188">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
