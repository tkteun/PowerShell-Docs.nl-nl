---
ms.date: 08/23/2017
keywords: Power shell, cmdlet
title: Windows Power shell-Internet toegang verwijderen
ms.openlocfilehash: 3c2c83525f5a240976eef215b5eac939796c91e8
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279007"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="b1bc1-103">Windows PowerShell-internettoegang verwijderen</span><span class="sxs-lookup"><span data-stu-id="b1bc1-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="b1bc1-104">Bijgewerkt: 24 juni 2013</span><span class="sxs-lookup"><span data-stu-id="b1bc1-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="b1bc1-105">Van toepassing op: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="b1bc1-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="b1bc1-106">Met de stappen in dit onderwerp wordt de Windows Power shell-website voor webtoegang en de bijbehorende toepassing verwijderd van de gateway server waarop deze is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="b1bc1-107">Gebruikers op de hoogte stellen</span><span class="sxs-lookup"><span data-stu-id="b1bc1-107">Notify users</span></span>

<span data-ttu-id="b1bc1-108">Voordat u begint, moet u gebruikers van de webconsole laten weten dat u de website gaat verwijderen.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="b1bc1-109">Als u Windows Power shell-webtoegang verwijdert, worden IIS of andere functies die automatisch zijn geïnstalleerd, niet verwijderd omdat deze door Windows Power shell Web Access moeten worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="b1bc1-110">Het verwijderings proces verlaat de functies die zijn geïnstalleerd waarbij Windows Power shell-webtoegang afhankelijk is. u kunt deze functies afzonderlijk verwijderen, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="b1bc1-111">Aanbevolen (snelle) verwijdering</span><span class="sxs-lookup"><span data-stu-id="b1bc1-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="b1bc1-112">In de procedures in deze sectie wordt beschreven hoe u beide kunt verwijderen:</span><span class="sxs-lookup"><span data-stu-id="b1bc1-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="b1bc1-113">de Web Access-webtoepassing voor Windows Power shell en</span><span class="sxs-lookup"><span data-stu-id="b1bc1-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="b1bc1-114">de functie voor Internet toegang van Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="b1bc1-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="b1bc1-115">met behulp van Windows Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="b1bc1-116">Stap 1: de webtoepassing verwijderen met behulp van cmdlets</span><span class="sxs-lookup"><span data-stu-id="b1bc1-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="b1bc1-117">Voer een van de volgende handelingen uit om een Windows Power shell-sessie te openen.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-117">Do one of the following to open a Windows PowerShell session.</span></span>

   - <span data-ttu-id="b1bc1-118">Klik op het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>
   - <span data-ttu-id="b1bc1-119">Klik in het Windows-**startscherm** op **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="b1bc1-120">Typ `Uninstall-PswaWebApplication`en druk vervolgens op **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>

   1. <span data-ttu-id="b1bc1-121">Als u uw eigen aangepaste websitenaam hebt opgegeven, voegt u de parameter `-WebsiteName` toe aan de opdracht en geeft u de naam van de website op.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

      `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`

   1. <span data-ttu-id="b1bc1-122">Als u een aangepaste webtoepassing hebt gebruikt (niet de standaard toepassing, **pswa**, voegt u de para meter `-WebApplicationName` toe aan de opdracht en geeft u de naam van de webtoepassing op.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

      `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`

   1. <span data-ttu-id="b1bc1-123">Als u een testcertificaat gebruikt, voegt de parameter `DeleteTestCertificate` toe aan de cmdlet, zoals wordt aangegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

      `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="b1bc1-124">Stap 2: Windows Power shell-Internet toegang verwijderen met behulp van cmdlets</span><span class="sxs-lookup"><span data-stu-id="b1bc1-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="b1bc1-125">Voer een van de volgende handelingen uit om een Windows Power shell-sessie met verhoogde gebruikers rechten te openen.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="b1bc1-126">Als al een sessie is geopend, gaat u naar de volgende stap.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-126">If a session is already open, go on to the next step.</span></span>

    - <span data-ttu-id="b1bc1-127">Klik op het Windows-bureau blad met de rechter muisknop op **Windows Power shell** op de taak balk en klik vervolgens op **als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>
    - <span data-ttu-id="b1bc1-128">Klik in het **startscherm** van Windows met de rechtermuisknop op **Windows PowerShell** en klik vervolgens op **Als administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="b1bc1-129">Typ het volgende en druk vervolgens op **Enter**, waarbij *computer_name* staat voor een externe server waarvan u Windows Power shell-Internet toegang wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="b1bc1-130">Met de parameter `-Restart` worden de doelservers zo nodig automatisch opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart`

    <span data-ttu-id="b1bc1-131">Als u functies en onderdelen van een offline-VHD wilt verwijderen, voegt u zowel de parameter `-ComputerName` als de parameter `-VHD` toe.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="b1bc1-132">De `-ComputerName`-parameter bevat de naam van de server waaraan de VHD moet worden gekoppeld en de `-VHD`-parameter bevat het pad naar het VHD-bestand op de opgegeven server.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart`

1. <span data-ttu-id="b1bc1-133">Als het verwijderen is voltooid, controleert u of u Windows Power shell-Internet toegang hebt verwijderd door de pagina **alle servers** in Serverbeheer te openen, een server te selecteren waarvan u de functie hebt verwijderd en de tegel **functies en onderdelen** op de pagina voor de geselecteerde server weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="b1bc1-134">U kunt ook de `Get-WindowsFeature`-cmdlet uitvoeren die gericht is op de geselecteerde server (Get-WindowsFeature-ComputerName &lt;*computer_name*&gt;) om een lijst weer te geven met functies en onderdelen die op de server zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server  (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features  that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="b1bc1-135">Aangepaste verwijdering</span><span class="sxs-lookup"><span data-stu-id="b1bc1-135">Custom uninstallation</span></span>

<span data-ttu-id="b1bc1-136">Met de procedures in deze sectie kunt u zowel de Windows Power shell Web Access-webtoepassing als de Windows Power shell Web Access-functie verwijderen met de wizard functies en onderdelen verwijderen in Serverbeheer en de IIS-beheer console.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="b1bc1-137">Stap 1: de webtoepassing verwijderen met IIS-beheer</span><span class="sxs-lookup"><span data-stu-id="b1bc1-137">Step 1: Delete the web application using IIS Manager</span></span>

1. <span data-ttu-id="b1bc1-138">Open de IIS-beheerconsole op een van de volgende manieren.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="b1bc1-139">Als de console al is geopend, gaat u naar de volgende stap.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-139">If it is already open, go on to the next step.</span></span>

   - <span data-ttu-id="b1bc1-140">Start Serverbeheer op het Windows-bureau blad door te klikken op **Serverbeheer** in de Windows-taak balk.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="b1bc1-141">Klik in het menu **extra** in Serverbeheer op **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

   - <span data-ttu-id="b1bc1-142">Typ in het Windows-**startscherm** een deel van de naam **IIS-beheer (Internet Information Services)** .</span><span class="sxs-lookup"><span data-stu-id="b1bc1-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="b1bc1-143">Klik op de snelkoppeling wanneer deze wordt weergegeven in de **Apps**-resultaten.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="b1bc1-144">Selecteer in het structuur deel venster van de IIS-beheerder de website waarop de webtoepassing Windows Power shell Web Access wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="b1bc1-145">Klik in het deelvenster **Acties** onder **Website beheren** op **Stoppen**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="b1bc1-146">Klik in het structuur deel venster met de rechter muisknop op de webtoepassing op de website met de webtoepassing Windows Power shell Web Access en klik vervolgens op **verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="b1bc1-147">Selecteer **toepassings groepen**in het structuur venster, selecteer de map Windows Power shell Web Access-toepassings groep, klik op **stoppen** in het deel venster **acties** en klik vervolgens op **verwijderen** in het inhouds venster.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="b1bc1-148">Sluit IIS-beheer.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-148">Close IIS Manager.</span></span>

   > [!WARNING]
   > <span data-ttu-id="b1bc1-149">Het certificaat wordt hierbij niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-149">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="b1bc1-150">Als u een zelfondertekend certificaat hebt gemaakt of een testcertificaat hebt gebruikt en dit wilt verwijderen, verwijdert u het certificaat in IIS-beheer.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-150">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="b1bc1-151">Stap 2: Windows Power shell-Internet toegang verwijderen met de wizard functies en onderdelen verwijderen</span><span class="sxs-lookup"><span data-stu-id="b1bc1-151">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="b1bc1-152">Als Serverbeheer al is geopend, gaat u naar de volgende stap.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-152">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="b1bc1-153">Als Serverbeheer nog niet is geopend, opent u het door een van de volgende handelingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-153">If Server Manager is not already open, open it by doing one of the following.</span></span>

    - <span data-ttu-id="b1bc1-154">Start Serverbeheer op het Windows-bureau blad door te klikken op **Serverbeheer** in de Windows-taak balk.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-154">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>
    - <span data-ttu-id="b1bc1-155">Klik in het Windows-**startscherm** op **Serverbeheer**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-155">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="b1bc1-156">Klik in het menu **Beheren** op **Functies en onderdelen verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-156">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="b1bc1-157">Selecteer op de pagina **Doelserver selecteren** de server of offline-VHD waarvan u het onderdeel wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-157">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="b1bc1-158">Als u een offline-VHD wilt selecteren, selecteert u eerst de server waaraan u de VHD wilt koppelen en selecteert u vervolgens het VHD-bestand.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-158">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="b1bc1-159">Klik op **Volgende** nadat u de doelserver hebt geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-159">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="b1bc1-160">Klik nogmaals op **Volgende** om naar de pagina **Onderdelen verwijderen** te gaan.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-160">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="b1bc1-161">Schakel het selectievakje voor **Windows PowerShell-webtoegang** in en klik op **Volgende**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-161">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="b1bc1-162">Klik op de pagina **geselecteerde items voor verwijderen bevestigen** op **verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="b1bc1-162">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1bc1-163">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b1bc1-163">See Also</span></span>

- [<span data-ttu-id="b1bc1-164">Windows Power shell-webtoegang installeren en gebruiken</span><span class="sxs-lookup"><span data-stu-id="b1bc1-164">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="b1bc1-165">Help voor IIS-beheer 7,0</span><span class="sxs-lookup"><span data-stu-id="b1bc1-165">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)