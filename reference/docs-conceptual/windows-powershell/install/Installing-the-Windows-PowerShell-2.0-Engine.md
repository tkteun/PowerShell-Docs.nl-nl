---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: De Windows PowerShell 2.0-engine installeren
ms.openlocfilehash: ca0e83209324b28bd41f65ced61bfe9003d98553
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810062"
---
# <a name="installing-the-windows-powershell-20-engine"></a><span data-ttu-id="32822-103">De Windows PowerShell 2.0-engine installeren</span><span class="sxs-lookup"><span data-stu-id="32822-103">Installing the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="32822-104">In dit onderwerp wordt uitgelegd hoe u de Windows Power Shell 2,0-engine installeert.</span><span class="sxs-lookup"><span data-stu-id="32822-104">This topic explains how to install the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="32822-105">Windows Power Shell 3,0 is ontworpen om achterwaarts compatibel te zijn met Windows Power Shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="32822-105">Windows PowerShell 3.0 is designed to be backwards compatible with Windows PowerShell 2.0.</span></span> <span data-ttu-id="32822-106">Cmdlets, providers, modules, modules en scripts die zijn geschreven voor Windows Power Shell 2,0, worden ongewijzigd uitgevoerd in Windows Power Shell 3,0 en Windows Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="32822-106">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in Windows PowerShell 3.0 and Windows PowerShell 4.0.</span></span> <span data-ttu-id="32822-107">Als gevolg van een wijziging in het runtime-activerings beleid in Microsoft .NET Framework 4, worden Windows Power shell-host-Program ma's die zijn geschreven voor Windows Power Shell 2,0 en gecompileerd met common language runtime (CLR) 2,0 niet uitgevoerd zonder aanpassing in latere versies van Windows Power shell, die zijn gecompileerd met CLR 4,0.</span><span class="sxs-lookup"><span data-stu-id="32822-107">However, due to a change in the runtime activation policy in Microsoft .NET Framework 4, Windows PowerShell host programs that were written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in later releases of Windows PowerShell, which is compiled with CLR 4.0.</span></span>

<span data-ttu-id="32822-108">Om achterwaartse compatibiliteit te behouden met opdrachten en host-Program ma's die worden beïnvloed door deze wijzigingen, zijn de Windows Power Shell 2,0-, Windows Power Shell 3,0-en Windows Power Shell 4,0-engines ontworpen om naast elkaar te worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32822-108">To maintain backward compatibility with commands and host programs that are affected by these changes, the Windows PowerShell 2.0, Windows PowerShell 3.0, and Windows PowerShell 4.0 engines are designed to run side-by-side.</span></span> <span data-ttu-id="32822-109">Daarnaast is de Windows Power Shell 2,0-engine opgenomen in Windows Server 2012 R2, Windows 8,1, Windows 8, Windows Server 2012 en Windows Management Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="32822-109">Also, the Windows PowerShell 2.0 Engine is included in Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012, and Windows Management Framework 3.0.</span></span> <span data-ttu-id="32822-110">De Windows Power Shell 2,0-engine is alleen bedoeld voor gebruik wanneer een bestaand script of hostprogramma niet kan worden uitgevoerd omdat het niet compatibel is met Windows Power Shell 3,0, Windows Power Shell 4,0 of Microsoft .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="32822-110">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 3.0, Windows PowerShell 4.0, or Microsoft .NET Framework 4.</span></span> <span data-ttu-id="32822-111">Dergelijke gevallen worden naar verwachting zeldzaam.</span><span class="sxs-lookup"><span data-stu-id="32822-111">Such cases are expected to be rare.</span></span>

<span data-ttu-id="32822-112">De Windows Power Shell 2,0-engine is een optionele functie van Windows Server 2012 R2, Windows 8,1, Windows® 8 en Windows Server® 2012.</span><span class="sxs-lookup"><span data-stu-id="32822-112">The Windows PowerShell 2.0 Engine is an optional feature of Windows Server 2012 R2, Windows 8.1, Windows® 8 and Windows Server® 2012.</span></span> <span data-ttu-id="32822-113">Bij eerdere versies van Windows wordt bij het installeren van Windows Management Framework 3,0 de Windows Power Shell 3,0-installatie volledig vervangen door de installatie van Windows Power Shell 2,0 in de installatiemap van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="32822-113">On earlier versions of Windows, when you install Windows Management Framework 3.0, the Windows PowerShell 3.0 installation completely replaces the Windows PowerShell 2.0 installation in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="32822-114">De Windows Power Shell 2,0-engine blijft echter behouden.</span><span class="sxs-lookup"><span data-stu-id="32822-114">However, the Windows PowerShell 2.0 Engine is retained.</span></span>

<span data-ttu-id="32822-115">Zie [Start the Windows Power shell 2,0 engine](../Starting-the-Windows-PowerShell-2.0-Engine.md)(Engelstalig) voor meer informatie over het starten van de Windows power Shell 2,0-engine.</span><span class="sxs-lookup"><span data-stu-id="32822-115">For information about starting the Windows PowerShell 2.0 Engine, see [Starting the Windows PowerShell 2.0 Engine](../Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="on-windows-81-and-windows-8"></a><span data-ttu-id="32822-116">In Windows 8,1 en Windows 8</span><span class="sxs-lookup"><span data-stu-id="32822-116">On Windows 8.1 and Windows 8</span></span>

<span data-ttu-id="32822-117">In Windows 8,1 en Windows 8 is de functie Windows Power Shell 2,0 engine standaard ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="32822-117">On Windows 8.1 and Windows 8, the Windows PowerShell 2.0 Engine feature is turned on by default.</span></span>
<span data-ttu-id="32822-118">Om het te gebruiken, moet u echter de optie inschakelen voor Microsoft .NET Framework 3,5, dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="32822-118">However, to use it, you need to turn on the option for Microsoft .NET Framework 3.5, which it requires.</span></span> <span data-ttu-id="32822-119">In deze sectie wordt ook uitgelegd hoe u de Windows Power Shell 2,0 engine-functie in-of uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="32822-119">This section also explains how to turn the Windows PowerShell 2.0 Engine feature on and off.</span></span>

#### <a name="to-turn-on-net-framework-35"></a><span data-ttu-id="32822-120">Om .NET Framework 3,5 in te scha kelen</span><span class="sxs-lookup"><span data-stu-id="32822-120">To turn on .NET Framework 3.5</span></span>

1. <span data-ttu-id="32822-121">Op de **Start** scherm, typt u **Windows-onderdelen**.</span><span class="sxs-lookup"><span data-stu-id="32822-121">On the **Start** screen, type **Windows Features**.</span></span>
2. <span data-ttu-id="32822-122">Klik op de balk **apps** op **instellingen**en klik vervolgens op **Windows-onderdelen in-of uitschakelen**.</span><span class="sxs-lookup"><span data-stu-id="32822-122">On the **Apps** bar, click **Settings**, and then click **Turn Windows features on or off**.</span></span>
3. <span data-ttu-id="32822-123">Klik in het vak **Windows-functies** op **.NET Framework 3,5 (inclusief .net 2,0 en 3,0** om het te selecteren.</span><span class="sxs-lookup"><span data-stu-id="32822-123">In the **Windows Features** box, click **.NET Framework 3.5 (includes .NET 2.0 and 3.0** to select it.</span></span>

   <span data-ttu-id="32822-124">Wanneer u **.NET Framework 3,5 (inclusief .net 2,0 en 3,0**) selecteert, wordt in het vak gevuld om aan te geven dat slechts een deel van de functie is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="32822-124">When you select **.NET Framework 3.5 (includes .NET 2.0 and 3.0**, the box fills to indicate that only part of the feature is selected.</span></span> <span data-ttu-id="32822-125">Dit is echter wel voldoende voor de Windows Power Shell 2,0-engine.</span><span class="sxs-lookup"><span data-stu-id="32822-125">However, this is sufficient for the Windows PowerShell 2.0 Engine.</span></span>

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a><span data-ttu-id="32822-126">De Windows Power Shell 2,0-engine inschakelen en uitschakelen</span><span class="sxs-lookup"><span data-stu-id="32822-126">To turn the Windows PowerShell 2.0 Engine on and off</span></span>

1. <span data-ttu-id="32822-127">Op de **Start** scherm, typt u **Windows-onderdelen**.</span><span class="sxs-lookup"><span data-stu-id="32822-127">On the **Start** screen, type **Windows Features**.</span></span>

2. <span data-ttu-id="32822-128">Klik op de balk **apps** op **instellingen**en klik vervolgens op **Windows-onderdelen in-of uitschakelen**.</span><span class="sxs-lookup"><span data-stu-id="32822-128">On the **Apps** bar, click **Settings**, and then click **Turn Windows features on or off**.</span></span>

3. <span data-ttu-id="32822-129">Vouw in het dialoog venster **Windows-functies** het knoop punt **windows Power Shell 2,0** uit en klik op het vak **Windows Power Shell 2,0-engine** om het in of uit te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="32822-129">In the **Windows Features** box, expand the **Windows PowerShell 2.0** node, and click the **Windows PowerShell 2.0 Engine** box to select or clear it.</span></span>

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a><span data-ttu-id="32822-130">In Windows Server 2012 R2 en Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="32822-130">On Windows Server 2012 R2 and Windows Server 2012</span></span>

<span data-ttu-id="32822-131">Gebruik de volgende procedures om de Windows Power Shell 2,0-engine en Microsoft .NET Framework 3,5-functies toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="32822-131">Use the following procedures to add the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 features.</span></span> <span data-ttu-id="32822-132">De Windows Power Shell 2,0-engine vereist Microsoft .NET Framework 2.0.50727 mini maal.</span><span class="sxs-lookup"><span data-stu-id="32822-132">The Windows PowerShell 2.0 Engine requires Microsoft .NET Framework 2.0.50727 at a minimum.</span></span> <span data-ttu-id="32822-133">Aan deze eis wordt voldaan door Microsoft .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="32822-133">This requirement is fulfilled by Microsoft .NET Framework 3.5.</span></span>

#### <a name="to-add-the-net-framework-35-feature"></a><span data-ttu-id="32822-134">De functie .NET Framework 3,5 toevoegen</span><span class="sxs-lookup"><span data-stu-id="32822-134">To add the .NET Framework 3.5 feature</span></span>

1. <span data-ttu-id="32822-135">In **Serverbeheer**klikt u in het menu **beheren** op **functies en onderdelen toevoegen**.</span><span class="sxs-lookup"><span data-stu-id="32822-135">In **Server Manager**, from the **Manage** menu, select **Add Roles and Features**.</span></span>

    <span data-ttu-id="32822-136">Of in **Serverbeheer**op **alle servers**, klik met de rechter muisknop op een server naam en selecteer vervolgens **functies en onderdelen toevoegen**.</span><span class="sxs-lookup"><span data-stu-id="32822-136">Or in **Server Manager**, click **All Servers**, right-click a server name, and then select  **Add Roles and Features**.</span></span>

2. <span data-ttu-id="32822-137">Selecteer op de pagina **installatie type** de optie installatie die op de **functie of het onderdeel is gebaseerd**.</span><span class="sxs-lookup"><span data-stu-id="32822-137">On the **Installation Type** page, select **Role-based or feature-based installation**.</span></span>

3. <span data-ttu-id="32822-138">Vouw op de pagina **functies** het knoop punt **.net 3,5 Framework-functies** uit en selecteer **.NET Framework 3,5 (inclusief .net 2,0 en 3,0)**.</span><span class="sxs-lookup"><span data-stu-id="32822-138">On the **Features** page, expand the **.NET 3.5 Framework Features** node and select **.NET Framework 3.5 (includes .NET 2.0 and 3.0)**.</span></span>

   <span data-ttu-id="32822-139">De andere opties onder dat knoop punt zijn niet vereist voor de Windows Power Shell 2,0-engine.</span><span class="sxs-lookup"><span data-stu-id="32822-139">The other options under that node are not required for the Windows PowerShell 2.0 Engine.</span></span>

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a><span data-ttu-id="32822-140">De functie Windows Power Shell 2,0 engine toevoegen</span><span class="sxs-lookup"><span data-stu-id="32822-140">To add the Windows PowerShell 2.0 Engine feature</span></span>

- <span data-ttu-id="32822-141">In **Serverbeheer**klikt u in het menu **beheren** op **functies en onderdelen toevoegen**.</span><span class="sxs-lookup"><span data-stu-id="32822-141">In **Server Manager**, from the **Manage** menu, select **Add Roles and Features**.</span></span>

  <span data-ttu-id="32822-142">Of **Serverbeheer**op **alle servers**, klik met de rechter muisknop op een server naam en selecteer vervolgens **functies en onderdelen toevoegen**.</span><span class="sxs-lookup"><span data-stu-id="32822-142">Or **Server Manager**, click **All Servers**, right-click a server name, and then select **Add Roles and Features**.</span></span>

- <span data-ttu-id="32822-143">Selecteer op de pagina **installatie type** de optie installatie die op de **functie of het onderdeel is gebaseerd**.</span><span class="sxs-lookup"><span data-stu-id="32822-143">On the **Installation Type** page, select **Role-based or feature-based installation**.</span></span>

- <span data-ttu-id="32822-144">Vouw op de pagina **functies** het knoop punt **Windows Power shell (geïnstalleerd)** uit en selecteer **Windows Power Shell 2,0 engine**.</span><span class="sxs-lookup"><span data-stu-id="32822-144">On the **Features** page, expand the **Windows PowerShell (Installed)** node and select **Windows PowerShell 2.0 Engine**.</span></span>

<span data-ttu-id="32822-145">Zie [Start the Windows Power shell 2,0 engine](../Starting-the-Windows-PowerShell-2.0-Engine.md)(Engelstalig) voor meer informatie over het starten van de Windows power Shell 2,0-engine.</span><span class="sxs-lookup"><span data-stu-id="32822-145">For information about starting the Windows PowerShell 2.0 Engine, see [Starting the Windows PowerShell 2.0 Engine](../Starting-the-Windows-PowerShell-2.0-Engine.md).</span></span>

## <a name="on-earlier-systems"></a><span data-ttu-id="32822-146">Op eerdere systemen</span><span class="sxs-lookup"><span data-stu-id="32822-146">On Earlier Systems</span></span>

<span data-ttu-id="32822-147">Het [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/?LinkID=293881) -pakket dat Windows power Shell 4,0 installeert op Windows 7, windows server 2008 R2 en windows server 2012, bevat de Windows power Shell 2,0-engine.</span><span class="sxs-lookup"><span data-stu-id="32822-147">The [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) package that installs Windows PowerShell 4.0 on Windows 7, Windows Server 2008 R2, and Windows Server 2012, includes the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="32822-148">De Windows Power Shell 2,0-engine is ingeschakeld en klaar voor gebruik, indien nodig, zonder aanvullende installatie, configuratie of configuratie.</span><span class="sxs-lookup"><span data-stu-id="32822-148">The Windows PowerShell 2.0 Engine is enabled and ready to use, if necessary, without additional installation, setup, or configuration.</span></span>

<span data-ttu-id="32822-149">Het Windows Management Framework 3,0-pakket dat Windows Power Shell 3,0 installeert op Windows 7, Windows Server 2008 R2 en Windows Server 2008, bevat de Windows Power Shell 2,0-engine.</span><span class="sxs-lookup"><span data-stu-id="32822-149">The Windows Management Framework 3.0 package that installs Windows PowerShell 3.0 on Windows 7, Windows Server 2008 R2, and Windows Server 2008, includes the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="32822-150">De Windows Power Shell 2,0-engine is ingeschakeld en klaar voor gebruik, indien nodig, zonder aanvullende installatie, configuratie of configuratie.</span><span class="sxs-lookup"><span data-stu-id="32822-150">The Windows PowerShell 2.0 Engine is enabled and ready to use, if necessary, without additional installation, setup, or configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="32822-151">Zie ook</span><span class="sxs-lookup"><span data-stu-id="32822-151">See Also</span></span>

- [<span data-ttu-id="32822-152">Windows PowerShell-systeemvereisten</span><span class="sxs-lookup"><span data-stu-id="32822-152">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="32822-153">Windows PowerShell installeren</span><span class="sxs-lookup"><span data-stu-id="32822-153">Installing Windows PowerShell</span></span>](Installing-Windows-PowerShell.md)
- <span data-ttu-id="32822-154">[Windows PowerShell starten](/previous-versions/ms714415(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="32822-154">[Starting Windows PowerShell](/previous-versions/ms714415(v=vs.85))</span></span>
- [<span data-ttu-id="32822-155">De Windows PowerShell 2.0-engine starten</span><span class="sxs-lookup"><span data-stu-id="32822-155">Starting the Windows PowerShell 2.0 Engine</span></span>](../Starting-the-Windows-PowerShell-2.0-Engine.md)