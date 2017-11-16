---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Windows PowerShell op oudere versies van Windows wordt gestart
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="0429c-103">Windows PowerShell op oudere versies van Windows wordt gestart</span><span class="sxs-lookup"><span data-stu-id="0429c-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="0429c-104">Deze sectie wordt uitgelegd hoe u Windows PowerShell en Windows PowerShell Integrated Scripting Environment (ISE) starten op Windows® 7, Windows Server® 2008 R2 en Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="0429c-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="0429c-105">Ook wordt uitgelegd hoe u de optionele functie inschakelt voor Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server® 2008 R2 en Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="0429c-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="0429c-106">Windows PowerShell 4.0 installeren op ondersteunde systemen, downloaden en installeren [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span><span class="sxs-lookup"><span data-stu-id="0429c-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="0429c-107">Zie voor meer informatie [Windows PowerShell installeren](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="0429c-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="0429c-108">Windows PowerShell 3.0 installeren op ondersteunde systemen, downloaden en installeren [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="0429c-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="0429c-109">Zie voor meer informatie [Windows PowerShell installeren](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="0429c-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="0429c-110">Het starten van Windows PowerShell op oudere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="0429c-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="0429c-111">Een van de volgende methoden gebruiken om te starten van de geïnstalleerde versie van Windows PowerShell 3.0 of 4.0 voor Windows PowerShell, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="0429c-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="0429c-112">Vanuit het startmenu</span><span class="sxs-lookup"><span data-stu-id="0429c-112">From the Start Menu</span></span>

- <span data-ttu-id="0429c-113">Klik op **Start**, type **PowerShell**, en klik vervolgens op **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0429c-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

- <span data-ttu-id="0429c-114">Van de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="0429c-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="0429c-115">Bij de opdrachtprompt</span><span class="sxs-lookup"><span data-stu-id="0429c-115">At the Command Prompt</span></span>

- <span data-ttu-id="0429c-116">In Cmd.exe, Windows PowerShell of Windows PowerShell ISE voor het starten van Windows PowerShell typt u:</span><span class="sxs-lookup"><span data-stu-id="0429c-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="0429c-117">U kunt ook de parameters van het programma PowerShell.exe gebruiken voor het aanpassen van de sessie.</span><span class="sxs-lookup"><span data-stu-id="0429c-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="0429c-118">Zie voor meer informatie [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="0429c-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="0429c-119">Met Administrative bevoegdheden ('als administrator uitvoeren")</span><span class="sxs-lookup"><span data-stu-id="0429c-119">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="0429c-120">Klik op **Start**, type **PowerShell**, met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="0429c-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="0429c-121">Het starten van Windows PowerShell ISE voor eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="0429c-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="0429c-122">Gebruik een van de volgende methoden om te starten van Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0429c-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="0429c-123">Vanuit het startmenu</span><span class="sxs-lookup"><span data-stu-id="0429c-123">From the Start Menu</span></span>

- <span data-ttu-id="0429c-124">Klik op **Start**, type **ISE**, en klik vervolgens op **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="0429c-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

- <span data-ttu-id="0429c-125">Van de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="0429c-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="0429c-126">Bij de opdrachtprompt</span><span class="sxs-lookup"><span data-stu-id="0429c-126">At the Command Prompt</span></span>

- <span data-ttu-id="0429c-127">In Cmd.exe, Windows PowerShell of Windows PowerShell ISE voor het starten van Windows PowerShell typt u:</span><span class="sxs-lookup"><span data-stu-id="0429c-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="0429c-128">of</span><span class="sxs-lookup"><span data-stu-id="0429c-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="0429c-129">Met Administrative bevoegdheden ('als administrator uitvoeren")</span><span class="sxs-lookup"><span data-stu-id="0429c-129">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="0429c-130">Klik op **Start**, type **ISE**, met de rechtermuisknop op **Windows PowerShell ISE**, en klik vervolgens op **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="0429c-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="0429c-131">Het inschakelen van Windows PowerShell ISE voor eerdere versies van Windows</span><span class="sxs-lookup"><span data-stu-id="0429c-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="0429c-132">In Windows PowerShell 4.0 en Windows PowerShell 3.0, is Windows PowerShell ISE standaard ingeschakeld op alle versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="0429c-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="0429c-133">Als deze nog niet is ingeschakeld, schakelt Windows Management Framework 4.0 of Windows Management Framework 3.0 deze.</span><span class="sxs-lookup"><span data-stu-id="0429c-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="0429c-134">In Windows PowerShell 2.0, is Windows PowerShell ISE standaard ingeschakeld op Windows 7.</span><span class="sxs-lookup"><span data-stu-id="0429c-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="0429c-135">Op Windows Server 2008 R2 en Windows Server 2008 is het echter een optionele functie.</span><span class="sxs-lookup"><span data-stu-id="0429c-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="0429c-136">Gebruik de volgende procedure om Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server 2008 R2 of Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="0429c-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="0429c-137">Windows PowerShell Integrated Scripting Environment (ISE) inschakelen</span><span class="sxs-lookup"><span data-stu-id="0429c-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="0429c-138">Start Serverbeheer.</span><span class="sxs-lookup"><span data-stu-id="0429c-138">Start Server Manager.</span></span>

2. <span data-ttu-id="0429c-139">Klik op **functies** en klik vervolgens op **onderdelen toevoegen**.</span><span class="sxs-lookup"><span data-stu-id="0429c-139">Click **Features** and then click **Add Features**.</span></span>

3. <span data-ttu-id="0429c-140">Klik in de onderdelen selecteren op Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="0429c-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

