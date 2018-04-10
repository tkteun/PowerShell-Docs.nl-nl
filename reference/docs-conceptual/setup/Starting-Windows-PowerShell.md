---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Windows PowerShell starten
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: b56ddc2f577225646729b99f3a2abcb8cc60d307
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="19afc-103">Windows PowerShell starten</span><span class="sxs-lookup"><span data-stu-id="19afc-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="19afc-104">PowerShell is een scripting engine dll die is ingesloten in meerdere hosts.</span><span class="sxs-lookup"><span data-stu-id="19afc-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="19afc-105">De meest voorkomende host die u wilt beginnen met zijn de interactieve opdrachtregel PowerShell.exe en de interactieve Scripting omgeving PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="19afc-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="19afc-106">Zie voor informatie over het starten van Windows PowerShell® op Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 en Windows 8 [Common Management Tasks and Navigation](http://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="19afc-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](http://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="19afc-107">Het starten van Windows PowerShell op oudere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="19afc-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="19afc-108">Deze sectie wordt uitgelegd hoe u Windows PowerShell en Windows PowerShell Integrated Scripting Environment (ISE) starten op Windows® 7, Windows Server® 2008 R2 en Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="19afc-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="19afc-109">Ook wordt uitgelegd hoe u de optionele functie inschakelt voor Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server® 2008 R2 en Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="19afc-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="19afc-110">Een van de volgende methoden gebruiken om te starten van de geïnstalleerde versie van Windows PowerShell 3.0 of 4.0 voor Windows PowerShell, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="19afc-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="19afc-111">Vanuit het startmenu</span><span class="sxs-lookup"><span data-stu-id="19afc-111">From the Start Menu</span></span>

- <span data-ttu-id="19afc-112">Klik op **Start**, type **PowerShell**, en klik vervolgens op **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="19afc-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="19afc-113">Van de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="19afc-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="19afc-114">Bij de opdrachtprompt</span><span class="sxs-lookup"><span data-stu-id="19afc-114">At the Command Prompt</span></span>

<span data-ttu-id="19afc-115">In Cmd.exe, Windows PowerShell of Windows PowerShell ISE voor het starten van Windows PowerShell typt u:</span><span class="sxs-lookup"><span data-stu-id="19afc-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="19afc-116">U kunt ook de parameters van het programma PowerShell.exe gebruiken voor het aanpassen van de sessie.</span><span class="sxs-lookup"><span data-stu-id="19afc-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="19afc-117">Zie voor meer informatie [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="19afc-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="19afc-118">Met Administrative bevoegdheden ('als administrator uitvoeren")</span><span class="sxs-lookup"><span data-stu-id="19afc-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="19afc-119">Klik op **Start**, type **PowerShell**, met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="19afc-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="19afc-120">Het starten van Windows PowerShell ISE voor eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="19afc-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="19afc-121">Gebruik een van de volgende methoden om te starten van Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="19afc-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="19afc-122">Vanuit het startmenu</span><span class="sxs-lookup"><span data-stu-id="19afc-122">From the Start Menu</span></span>

- <span data-ttu-id="19afc-123">Klik op **Start**, type **ISE**, en klik vervolgens op **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="19afc-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="19afc-124">Van de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="19afc-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="19afc-125">Bij de opdrachtprompt</span><span class="sxs-lookup"><span data-stu-id="19afc-125">At the Command Prompt</span></span>

<span data-ttu-id="19afc-126">In Cmd.exe, Windows PowerShell of Windows PowerShell ISE voor het starten van Windows PowerShell typt u:</span><span class="sxs-lookup"><span data-stu-id="19afc-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="19afc-127">of</span><span class="sxs-lookup"><span data-stu-id="19afc-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="19afc-128">Met Administrative bevoegdheden ('als administrator uitvoeren")</span><span class="sxs-lookup"><span data-stu-id="19afc-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="19afc-129">Klik op **Start**, type **ISE**, met de rechtermuisknop op **Windows PowerShell ISE**, en klik vervolgens op **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="19afc-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="19afc-130">Het inschakelen van Windows PowerShell ISE voor eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="19afc-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="19afc-131">In Windows PowerShell 4.0 en Windows PowerShell 3.0, is Windows PowerShell ISE standaard ingeschakeld op alle versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="19afc-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="19afc-132">Als deze nog niet is ingeschakeld, schakelt Windows Management Framework 4.0 of Windows Management Framework 3.0 deze.</span><span class="sxs-lookup"><span data-stu-id="19afc-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="19afc-133">In Windows PowerShell 2.0, is Windows PowerShell ISE standaard ingeschakeld op Windows 7.</span><span class="sxs-lookup"><span data-stu-id="19afc-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="19afc-134">Op Windows Server 2008 R2 en Windows Server 2008 is het echter een optionele functie.</span><span class="sxs-lookup"><span data-stu-id="19afc-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="19afc-135">Gebruik de volgende procedure om Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server 2008 R2 of Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="19afc-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="19afc-136">Windows PowerShell Integrated Scripting Environment (ISE) inschakelen</span><span class="sxs-lookup"><span data-stu-id="19afc-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="19afc-137">Start Serverbeheer.</span><span class="sxs-lookup"><span data-stu-id="19afc-137">Start Server Manager.</span></span>
2. <span data-ttu-id="19afc-138">Klik op **functies** en klik vervolgens op **onderdelen toevoegen**.</span><span class="sxs-lookup"><span data-stu-id="19afc-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="19afc-139">Klik in de onderdelen selecteren op Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="19afc-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="19afc-140">De 32-bits versie van Windows PowerShell starten</span><span class="sxs-lookup"><span data-stu-id="19afc-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="19afc-141">Wanneer u Windows PowerShell op een 64-bits computer installeert **Windows PowerShell (x86)**, een 32-bits versie van Windows PowerShell naast de 64-bits versie is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="19afc-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="19afc-142">Wanneer u Windows PowerShell uitvoert, wordt standaard de 64-bits versie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="19afc-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="19afc-143">Hoeft u wellicht van tijd tot tijd worden uitgevoerd **Windows PowerShell (x86)**, zoals wanneer u een module die vereist dat de 32-bits-versie of wanneer u extern verbinding met een 32-bits computer maakt.</span><span class="sxs-lookup"><span data-stu-id="19afc-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="19afc-144">Gebruik een van de volgende procedures voor het starten van een 32-bits versie van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19afc-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="19afc-145">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="19afc-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="19afc-146">Op de **Start** Typ **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="19afc-147">Klik op de **Windows PowerShell x86** tegel.</span><span class="sxs-lookup"><span data-stu-id="19afc-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="19afc-148">In **Serverbeheer**, uit de **extra** selecteert u **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-149">Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-150">Geef op via de opdrachtregel: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="19afc-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="19afc-151">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="19afc-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="19afc-152">Op de **Start** Typ **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-153">In **Serverbeheer**, uit de **extra** selecteert u **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-154">Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-155">Geef op via de opdrachtregel: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="19afc-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="19afc-156">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="19afc-156">In Windows® 8.1</span></span>

- <span data-ttu-id="19afc-157">Op de **Start** Typ **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="19afc-158">Klik op de **Windows PowerShell x86** tegel.</span><span class="sxs-lookup"><span data-stu-id="19afc-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="19afc-159">Als u werkt met [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) voor Windows 8.1, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="19afc-159">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="19afc-160">Selecteer **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-161">Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-162">Geef op via de opdrachtregel: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="19afc-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="19afc-163">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="19afc-163">In Windows® 8</span></span>

- <span data-ttu-id="19afc-164">Op de **Start** scherm, verplaatst de cursor naar de rechterbovenhoek en klik op **instellingen**, klikt u op **tegels**, en verplaats de **weergeven Systeembeheer** schuifregelaar op Ja.</span><span class="sxs-lookup"><span data-stu-id="19afc-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="19afc-165">Typ vervolgens **PowerShell** en klik op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-166">Als u werkt met [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) voor Windows 8, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="19afc-166">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="19afc-167">Selecteer **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-168">Op de **Start** scherm of het bureaublad, typt u **PowerShell (x86)** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="19afc-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="19afc-169">Geef op via de opdrachtregel: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="19afc-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>