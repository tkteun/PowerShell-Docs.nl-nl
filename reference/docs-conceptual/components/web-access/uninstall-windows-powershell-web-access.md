---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: windows powershell-internettoegang verwijderen
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688159"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="1255d-103">Windows PowerShell-internettoegang verwijderen</span><span class="sxs-lookup"><span data-stu-id="1255d-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="1255d-104">Bijgewerkt: 24: juni 2013</span><span class="sxs-lookup"><span data-stu-id="1255d-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="1255d-105">Van toepassing op: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="1255d-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="1255d-106">De stappen in dit onderwerp worden de website van Windows PowerShell-webtoegang en de bijbehorende toepassing verwijderen van de gatewayserver waarop deze is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1255d-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="1255d-107">Gebruikers een melding ontvangen</span><span class="sxs-lookup"><span data-stu-id="1255d-107">Notify users</span></span>

<span data-ttu-id="1255d-108">Voordat u begint, moet u gebruikers van de webconsole laten weten dat u de website gaat verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1255d-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="1255d-109">Windows PowerShell-webtoegang verwijderen, worden IIS of andere onderdelen die automatisch zijn geïnstalleerd omdat de Windows PowerShell-webtoegang vereist is om uit te voeren niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1255d-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="1255d-110">De verwijdering blijven onderdelen geïnstalleerd waarop Windows PowerShell-webtoegang afhankelijke is; indien nodig, kunt u deze functies afzonderlijk verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1255d-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="1255d-111">Aanbevolen (snelle) verwijdering</span><span class="sxs-lookup"><span data-stu-id="1255d-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="1255d-112">Procedures in deze sectie kunt u beide verwijderen:</span><span class="sxs-lookup"><span data-stu-id="1255d-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="1255d-113">de web-App van Windows PowerShell-webtoegang en</span><span class="sxs-lookup"><span data-stu-id="1255d-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="1255d-114">de functie Windows PowerShell-webtoegang</span><span class="sxs-lookup"><span data-stu-id="1255d-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="1255d-115">met behulp van Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1255d-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="1255d-116">Stap 1: Verwijderen van de web-App met behulp van cmdlets</span><span class="sxs-lookup"><span data-stu-id="1255d-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="1255d-117">Doe het volgende om een Windows PowerShell-sessie te openen.</span><span class="sxs-lookup"><span data-stu-id="1255d-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="1255d-118">Op het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk.</span><span class="sxs-lookup"><span data-stu-id="1255d-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="1255d-119">Op de Windows **Start** scherm, klikt u op **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1255d-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="1255d-120">Type `Uninstall-PswaWebApplication`, en druk vervolgens op **Enter**.</span><span class="sxs-lookup"><span data-stu-id="1255d-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="1255d-121">Als u uw eigen aangepaste websitenaam hebt opgegeven, voegt u de parameter `-WebsiteName` toe aan de opdracht en geeft u de naam van de website op.</span><span class="sxs-lookup"><span data-stu-id="1255d-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="1255d-122">Als u een aangepaste webtoepassing hebt gebruikt (niet de standaardtoepassing, **pswa**, voeg de `-WebApplicationName` parameter aan de opdracht en geeft u de naam van de web-App.</span><span class="sxs-lookup"><span data-stu-id="1255d-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="1255d-123">Als u een testcertificaat gebruikt, voegt de parameter `DeleteTestCertificate` toe aan de cmdlet, zoals wordt aangegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="1255d-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="1255d-124">Stap 2: Windows PowerShell-internettoegang met behulp van cmdlets verwijderen</span><span class="sxs-lookup"><span data-stu-id="1255d-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="1255d-125">Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.</span><span class="sxs-lookup"><span data-stu-id="1255d-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="1255d-126">Als al een sessie is geopend, gaat u naar de volgende stap.</span><span class="sxs-lookup"><span data-stu-id="1255d-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="1255d-127">Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="1255d-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="1255d-128">Op de Windows **Start** met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als Administrator uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="1255d-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="1255d-129">Typ het volgende en druk vervolgens op **Enter**, waarbij *computer_name* vertegenwoordigt een externe server van waaruit u wilt verwijderen van Windows PowerShell-webtoegang.</span><span class="sxs-lookup"><span data-stu-id="1255d-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="1255d-130">Met de parameter `-Restart` worden de doelservers zo nodig automatisch opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="1255d-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="1255d-131">Als u functies en onderdelen van een offline-VHD wilt verwijderen, voegt u zowel de parameter `-ComputerName` als de parameter `-VHD` toe.</span><span class="sxs-lookup"><span data-stu-id="1255d-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="1255d-132">De parameter `-ComputerName` bevat de naam van de server waaraan de VHD moet worden gekoppeld en de parameter `-VHD` bevat het pad naar het VHD-bestand op de opgegeven server.</span><span class="sxs-lookup"><span data-stu-id="1255d-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="1255d-133">Nadat de verwijdering is voltooid, controleert u of u Windows PowerShell-webtoegang verwijderd door het openen van de **alle Servers** pagina in Serverbeheer, een server waarvan u de functie verwijderd te selecteren en weergeven van de **rollen en Functies** tegel op de pagina voor de geselecteerde server.</span><span class="sxs-lookup"><span data-stu-id="1255d-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="1255d-134">U kunt ook uitvoeren de `Get-WindowsFeature` cmdlet gericht op de geselecteerde server (Get-WindowsFeature - ComputerName &lt; *computer_name*&gt;) om een lijst met functies en onderdelen die zijn geïnstalleerd op de server weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1255d-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="1255d-135">Aangepaste verwijdering</span><span class="sxs-lookup"><span data-stu-id="1255d-135">Custom uninstallation</span></span>

<span data-ttu-id="1255d-136">Procedures in deze sectie kunt u verwijdert u de web-App voor Windows PowerShell-webtoegang en de Windows PowerShell Web Access-functie met behulp van de rollen verwijderen en onderdelen in Serverbeheer en de IIS-beheerconsole.</span><span class="sxs-lookup"><span data-stu-id="1255d-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="1255d-137">Stap 1: De web-App met behulp van IIS-beheer verwijderen</span><span class="sxs-lookup"><span data-stu-id="1255d-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="1255d-138">Open de IIS-beheerconsole op een van de volgende manieren.</span><span class="sxs-lookup"><span data-stu-id="1255d-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="1255d-139">Als de console al is geopend, gaat u naar de volgende stap.</span><span class="sxs-lookup"><span data-stu-id="1255d-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="1255d-140">Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows.</span><span class="sxs-lookup"><span data-stu-id="1255d-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="1255d-141">Op de **extra** menu in Serverbeheer, klikt u op **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="1255d-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="1255d-142">Op de Windows **Start** scherm, typt u een deel van de naam **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="1255d-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="1255d-143">Klik op de snelkoppeling wanneer deze wordt weergegeven de **Apps** resultaten.</span><span class="sxs-lookup"><span data-stu-id="1255d-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="1255d-144">Selecteer de website waarop de web-App voor Windows PowerShell-webtoegang in het structuurdeelvenster van IIS-beheer.</span><span class="sxs-lookup"><span data-stu-id="1255d-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="1255d-145">In de **acties** deelvenster onder **Website beheren**, klikt u op **stoppen**.</span><span class="sxs-lookup"><span data-stu-id="1255d-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="1255d-146">In het structuurdeelvenster met de rechtermuisknop op de web-App in de website waarop de web-App voor Windows PowerShell-webtoegang en klik vervolgens op **verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="1255d-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="1255d-147">Selecteer in het structuurdeelvenster **toepassingsgroepen**, selecteert u de map met de Windows PowerShell-webtoegang toepassingsgroep, klikt u op **stoppen** in de **acties** in het deelvenster en klik vervolgens op  **Verwijder** in het inhoudsvenster.</span><span class="sxs-lookup"><span data-stu-id="1255d-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="1255d-148">Sluit IIS-beheer.</span><span class="sxs-lookup"><span data-stu-id="1255d-148">Close IIS Manager.</span></span>

> <span data-ttu-id="1255d-149">![Waarschuwing Opmerking](images/SecurityNote.jpeg)**Opmerking**:</span><span class="sxs-lookup"><span data-stu-id="1255d-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="1255d-150">Het certificaat wordt hierbij niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1255d-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="1255d-151">Als u een zelfondertekend certificaat hebt gemaakt of een testcertificaat hebt gebruikt en dit wilt verwijderen, verwijdert u het certificaat in IIS-beheer.</span><span class="sxs-lookup"><span data-stu-id="1255d-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="1255d-152">Stap 2: Windows PowerShell-internettoegang met behulp van de verwijderen Wizard functies en onderdelen verwijderen</span><span class="sxs-lookup"><span data-stu-id="1255d-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="1255d-153">Als Serverbeheer al geopend is, gaat u naar de volgende stap.</span><span class="sxs-lookup"><span data-stu-id="1255d-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="1255d-154">Als Serverbeheer niet al geopend is, op een van de volgende manieren openen.</span><span class="sxs-lookup"><span data-stu-id="1255d-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="1255d-155">Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows.</span><span class="sxs-lookup"><span data-stu-id="1255d-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="1255d-156">Op de Windows **Start** scherm, klikt u op **Serverbeheer**.</span><span class="sxs-lookup"><span data-stu-id="1255d-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="1255d-157">Op de **beheren** menu, klikt u op **functies en onderdelen verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="1255d-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="1255d-158">Op de **Selecteer doelserver** pagina, selecteert u de server of offline-VHD waarvan u wilt verwijderen van de functie.</span><span class="sxs-lookup"><span data-stu-id="1255d-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="1255d-159">Als u een offline-VHD wilt selecteren, kiest u eerst de server waaraan u de VHD wilt koppelen en selecteert u vervolgens het VHD-bestand.</span><span class="sxs-lookup"><span data-stu-id="1255d-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="1255d-160">Nadat u de doelserver hebt geselecteerd, klikt u op **volgende**.</span><span class="sxs-lookup"><span data-stu-id="1255d-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="1255d-161">Klik op **volgende** opnieuw om over te slaan naar de **onderdelen verwijderen** pagina.</span><span class="sxs-lookup"><span data-stu-id="1255d-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="1255d-162">Schakel het selectievakje voor **Windows PowerShell-webtoegang**, en klik vervolgens op **volgende**.</span><span class="sxs-lookup"><span data-stu-id="1255d-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="1255d-163">Op de **verwijdering selecties bevestigen** pagina, klikt u op **verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="1255d-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1255d-164">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1255d-164">See Also</span></span>

- [<span data-ttu-id="1255d-165">Installeren en gebruiken van Windows PowerShell-internettoegang</span><span class="sxs-lookup"><span data-stu-id="1255d-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="1255d-166">IIS 7.0 Manager Help</span><span class="sxs-lookup"><span data-stu-id="1255d-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)