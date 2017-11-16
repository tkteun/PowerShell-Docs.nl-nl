---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: De 32-bits versie van Windows PowerShell starten
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="d4023-103">De 32-bits versie van Windows PowerShell starten</span><span class="sxs-lookup"><span data-stu-id="d4023-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="d4023-104">Wanneer u Windows PowerShell op een 64-bits computer installeert **Windows PowerShell (x86)**, een 32-bits versie van Windows PowerShell naast de 64-bits versie is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="d4023-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="d4023-105">Wanneer u Windows PowerShell uitvoert, wordt standaard de 64-bits versie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d4023-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="d4023-106">Hoeft u wellicht van tijd tot tijd worden uitgevoerd **Windows PowerShell (x86)**, zoals wanneer u een module die vereist dat de 32-bits-versie of wanneer u extern verbinding met een 32-bits computer maakt.</span><span class="sxs-lookup"><span data-stu-id="d4023-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="d4023-107">Gebruik een van de volgende procedures voor het starten van een 32-bits versie van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4023-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="d4023-108">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d4023-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="d4023-109">Op de **Start** Typ **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="d4023-110">Klik op de **Windows PowerShell x86** tegel.</span><span class="sxs-lookup"><span data-stu-id="d4023-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="d4023-111">In **Serverbeheer**, uit de **extra** selecteert u **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4023-112">Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4023-113">Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d4023-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="d4023-114">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="d4023-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="d4023-115">Op de **Start** Typ **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4023-116">In **Serverbeheer**, uit de **extra** selecteert u **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4023-117">Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4023-118">Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d4023-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="d4023-119">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="d4023-119">In Windows® 8.1</span></span>

- <span data-ttu-id="d4023-120">Op de **Start** Typ **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="d4023-121">Klik op de **Windows PowerShell x86** tegel.</span><span class="sxs-lookup"><span data-stu-id="d4023-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="d4023-122">Als u werkt met [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) voor Windows 8.1, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="d4023-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="d4023-123">Selecteer **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4023-124">Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="d4023-125">Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d4023-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="d4023-126">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="d4023-126">In Windows® 8</span></span>

- <span data-ttu-id="d4023-127">Op de **Start** scherm, verplaatst de cursor naar de rechterbovenhoek en klik op **instellingen**, klikt u op **tegels**, en verplaats de **weergeven Systeembeheer** schuifregelaar op Ja.</span><span class="sxs-lookup"><span data-stu-id="d4023-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="d4023-128">Typ vervolgens **PowerShell** en klik op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4023-129">Als u werkt met [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) voor Windows 8, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu.</span><span class="sxs-lookup"><span data-stu-id="d4023-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="d4023-130">Selecteer **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4023-131">Op de **Start** scherm of het bureaublad, typt u **PowerShell (x86)** en klik vervolgens op **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d4023-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="d4023-132">Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d4023-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

