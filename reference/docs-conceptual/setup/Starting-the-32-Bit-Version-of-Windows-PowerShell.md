---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: De 32-bitsversie van Windows PowerShell starten
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/08/2018
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="a0a1a-103">De 32-bits versie van Windows PowerShell starten</span><span class="sxs-lookup"><span data-stu-id="a0a1a-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="a0a1a-104">Wanneer u Windows PowerShell op een 64-bits computer installeert **Windows PowerShell (x86)**, een 32-bits versie van Windows PowerShell naast de 64-bits versie is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="a0a1a-105">Wanneer u Windows PowerShell uitvoert, wordt standaard de 64-bits versie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="a0a1a-106">Hoeft u wellicht van tijd tot tijd worden uitgevoerd **Windows PowerShell (x86)**, zoals wanneer u een module die vereist dat de 32-bits-versie of wanneer u extern verbinding met een 32-bits computer maakt.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="a0a1a-107">Gebruik een van de volgende procedures voor het starten van een 32-bits versie van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="a0a1a-108">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a0a1a-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="a0a1a-109">Op de **Start** Typ **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="a0a1a-110">Klik op de **Windows PowerShell x86** tegel.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="a0a1a-111">In **Serverbeheer**, uit de **extra** selecteert u **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="a0a1a-112">Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="a0a1a-113">Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a0a1a-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="a0a1a-114">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="a0a1a-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="a0a1a-115">Op de **Start** Typ **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="a0a1a-116">In **Serverbeheer**, uit de **extra** selecteert u **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="a0a1a-117">Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="a0a1a-118">Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a0a1a-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="a0a1a-119">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="a0a1a-119">In Windows® 8.1</span></span>

- <span data-ttu-id="a0a1a-120">Op de **Start** Typ **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="a0a1a-121">Klik op de **Windows PowerShell x86** tegel.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="a0a1a-122">Als u werkt met [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) voor Windows 8.1, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="a0a1a-123">Selecteer **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="a0a1a-124">Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="a0a1a-125">Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a0a1a-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="a0a1a-126">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="a0a1a-126">In Windows® 8</span></span>

- <span data-ttu-id="a0a1a-127">Op de **Start** scherm, verplaatst de cursor naar de rechterbovenhoek en klik op **instellingen**, klikt u op **tegels**, en verplaats de **weergeven Systeembeheer** schuifregelaar op Ja.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="a0a1a-128">Typ vervolgens **PowerShell** en klik op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="a0a1a-129">Als u werkt met [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) voor Windows 8, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="a0a1a-130">Selecteer **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="a0a1a-131">Op de **Start** scherm of het bureaublad, typt u **PowerShell (x86)** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="a0a1a-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="a0a1a-132">Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a0a1a-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

