---
ms.date: 08/23/2017
keywords: Power shell, cmdlet
title: Windows Power shell-webtoegang installeren en gebruiken
ms.openlocfilehash: a3207c859c4b93b07d4c1b41d7df5269daa39a7d
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "79407040"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Windows Power shell-webtoegang installeren en gebruiken

Bijgewerkt: 5 november 2013 (bewerkt: 23 augustus 2017)

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

## <a name="introduction"></a>Inleiding

Windows Power shell Web Access, dat voor het eerst werd geïntroduceerd in Windows Server 2012, fungeert als een Windows Power shell-gateway en biedt een Windows Power shell-console op het web die is gericht op een externe computer. IT-professionals kunnen Windows Power shell-opdrachten en-scripts uitvoeren vanaf een Windows Power shell-console in een webbrowser, zonder Windows Power shell, software voor extern beheer of installatie van een browser-invoeg toepassing vereist op het client apparaat. Alles wat u nodig hebt om de Windows Power shell-console op het web uit te voeren is een correct geconfigureerde Windows Power shell Web Access-Gateway en een browser voor client apparaten die Java script ondersteunt en cookies accepteert.

Voor beelden van client apparaten zijn laptops, niet-werkende persoonlijke computers, gelelijke computers, tablet-computers, webkiosken, computers waarop geen Windows-besturings systeem en mobiele telefoon browsers worden uitgevoerd. IT-professionals kunnen kritieke beheer taken uitvoeren op externe Windows-servers vanaf apparaten die toegang hebben tot een Internet verbinding en een webbrowser.

Nadat de gateway is geïnstalleerd en geconfigureerd, kunnen gebruikers toegang krijgen tot een Windows Power shell-console via een webbrowser. Wanneer gebruikers de beveiligde website van Windows Power shell Web Access openen, kunnen ze een op het web gebaseerde Windows Power shell-console uitvoeren na een geslaagde verificatie.

Setup en configuratie van Windows Power shell-webtoegang is een proces dat uit drie stappen bestaat:

1. [Windows Power shell-Internet toegang installeren](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [De gateway configureren](#configure-the-gateway)
1. [Een beperkende autorisatie regel configureren](#configure-a-restrictive-authorization-rule)

Voordat u Windows Power shell-webtoegang installeert en configureert, wordt u aangeraden deze volledige hand leiding te lezen. dit artikel bevat instructies voor het installeren, beveiligen en verwijderen van Windows Power shell-webtoegang. In het onderwerp [het webgebaseerde Windows Power shell-console gebruiken](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) wordt beschreven hoe gebruikers zich aanmelden bij de webconsole en worden beperkingen en verschillen tussen de op het web gebaseerde Windows Power shell-console en de **Power shell. exe** -console besproken. Eind gebruikers van de webconsole moeten [de Windows Power shell-console op basis van het web gebruiken](use-the-web-based-windows-powershell-console.md)lezen, maar hoeven de rest van deze hand leiding niet te lezen.

In dit onderwerp vindt u geen gedetailleerde richt lijnen voor IIS-webserver bewerkingen. in dit onderwerp worden alleen de stappen beschreven die nodig zijn om de Windows Power shell Web Access-Gateway te configureren. Zie de documentatie bronnen voor IIS in de sectie Zie ook voor meer informatie over het configureren en beveiligen van websites in IIS.

In het volgende diagram ziet u hoe Windows Power shell Web Access werkt.

![Windows Power shell-Web Access-diagram](media/install-and-use-windows-powershell-web-access/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Vereisten voor het uitvoeren van Windows Power shell-Internet toegang

Voor Windows Power shell Web Access zijn webserver (IIS), .NET Framework 4,5 en Windows Power Shell 3,0 of Windows Power Shell 4,0 vereist om te worden uitgevoerd op de server waarop u de gateway wilt uitvoeren. U kunt Windows Power shell-webtoegang installeren op een server met Windows Server 2012 R2 of Windows Server 2012 met behulp van de wizard functies en onderdelen toevoegen in Serverbeheer of cmdlets voor Windows Power shell-implementaties voor Serverbeheer. Wanneer u Windows Power shell-webtoegang installeert met behulp van Serverbeheer of de implementatie-cmdlets, worden de vereiste functies en onderdelen automatisch toegevoegd als onderdeel van het installatie proces.

Met Windows Power shell Web Access kunnen externe gebruikers toegang krijgen tot computers in uw organisatie met behulp van Windows Power shell in een webbrowser. Windows Power shell-webtoegang is een handig en krachtig beheer programma, de webtoegang vormt beveiligings Risico's en moet zo veilig mogelijk worden geconfigureerd. Het is raadzaam dat beheerders die de Windows Power shell Web Access-gateway configureren, gebruikmaken van beschik bare beveiligings lagen, zowel de op de cmdlet gebaseerde autorisatie regels die zijn opgenomen in Windows Power shell-webtoegang als beveiligings lagen die beschikbaar zijn in webserver (IIS) en toepassingen van derden. Deze documentatie bevat zowel onbeveiligde voor beelden die alleen worden aanbevolen voor test omgevingen, maar ook voor beelden die worden aanbevolen voor beveiligde implementaties.

## <a name="browser-and-client-device-support"></a>Ondersteuning voor browsers en client apparaten

Windows Power shell Web Access ondersteunt de volgende Internet browsers. Hoewel mobiele browsers niet officieel worden ondersteund, kunnen veel mogelijk de Windows Power shell-console van het web worden uitgevoerd.
Andere browsers die cookies accepteren, java script uitvoeren en HTTPS-websites uitvoeren, worden verwacht, maar zijn niet officieel getest.

### <a name="supported-desktop-computer-browsers"></a>Ondersteunde browsers voor desktop computers

- Windows Internet Explorer voor micro soft Windows 8,0, 9,0, 10,0 en 11,0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56 m voor Windows
- Apple Safari 5.1.2 voor Windows
- Apple Safari 5.1.2 voor Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Mini maal geteste mobiele apparaten of browsers

- Windows Phone 7 en 7,5
- Google Android WebKit 3,1 browser Android 2.2.1 (kernel 2,6)
- 5.0.1 van Apple Safari voor iPhone-besturings systeem
- 5.0.1 van Apple Safari voor iPad 2-besturings systeem

### <a name="browser-requirements"></a>Browservereisten

Browsers moeten het volgende doen om de webconsole van Windows Power shell Web Access te gebruiken.

- Cookies van de Windows Power shell Web Access-Gateway website toestaan.
- HTTPS-pagina's kunnen worden geopend en gelezen.
- Websites openen en uitvoeren die Java script gebruiken.

## <a name="recommended-quick-deployment"></a>Aanbevolen snelle implementatie

U kunt de Windows Power shell Web Access-gateway installeren op een server met Windows Server 2012 R2 of Windows Server 2012 met behulp van Windows Power shell-cmdlets of met behulp van de wizard functies en onderdelen toevoegen die vanuit Serverbeheer wordt geopend. Gebruik Windows Power shell-cmdlets, zoals beschreven in deze sectie voor snelle installatie en configuratie.

1. [Windows Power shell-Internet toegang installeren](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [De gateway configureren](#configure-the-gateway)
1. [Een beperkende autorisatie regel configureren](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>Windows Power shell-webtoegang installeren met Power shell-cmdlets

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Windows Power shell-webtoegang installeren met behulp van Windows Power shell-cmdlets

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

   - Klik op het bureaublad van Windows met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **Als administrator uitvoeren**.
   - Klik op het Windows- **Start** scherm met de rechter muisknop op **Windows Power shell**en klik vervolgens op **als administrator uitvoeren**.

   > [!NOTE]
   > In Windows Power Shell 3,0 en 4,0 is het niet nodig om de Serverbeheer cmdlet-module te importeren in de Windows Power shell-sessie voordat u cmdlets uitvoert die deel uitmaken van de module. Een module wordt automatisch geïmporteerd tijdens de eerste keer dat u de cmdlet die deel uitmaakt van de module uitvoert.
   > Ook zijn Windows Power shell-cmdlets niet hoofdletter gevoelig.

1. Typ het volgende en druk vervolgens op **Enter**, waarbij *computer_name* staat voor een externe computer waarop u Windows Power shell-Internet toegang wilt installeren, indien van toepassing. Met `-Restart` de para meter wordt de doel server automatisch opnieuw opgestart als dat nodig is.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > [!NOTE]
   > Als u Windows Power shell-webtoegang met Windows Power shell-cmdlets installeert, worden standaard geen beheer hulpprogramma's voor webserver (IIS) toegevoegd. Als u de beheer hulpprogramma's wilt installeren op dezelfde server als de Windows Power shell Web Access-Gateway, voegt u `-IncludeManagementTools` de para meter toe aan de installatie opdracht (zoals in deze stap wordt beschreven). Als u de website van Windows Power shell Web Access beheert vanaf een externe computer, installeert u de module IIS-beheer door [Remote Server Administration Tools voor windows 8,1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) of [Remote Server Administration Tools voor Windows 8](https://www.microsoft.com/en-us/download/details.aspx?id=28972) te installeren op de computer van waaruit u de gateway wilt beheren.

   Als u functies en onderdelen op een offline-VHD wilt installeren, moet u `-ComputerName` zowel de para `-VHD` meter als de para meter toevoegen. De parameter `-ComputerName` bevat de naam van de server waaraan de VHD moet worden gekoppeld en de parameter `-VHD` bevat het pad naar het VHD-bestand op de opgegeven server.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Als de installatie is voltooid, controleert u of Windows Power shell Web Access is geïnstalleerd op de doel `Get-WindowsFeature` servers door de cmdlet uit te voeren op een doel server, in een Windows Power shell-console die is geopend met verhoogde gebruikers rechten. U kunt ook controleren of Windows Power shell Web Access is geïnstalleerd in de Serverbeheer-console door een doel server te selecteren op de pagina **alle servers** en vervolgens de tegel **functies en onderdelen** voor de geselecteerde server weer te geven. U kunt ook het Leesmij-bestand voor Windows Power shell-Internet toegang weer geven.

1. Nadat Windows Power shell-webtoegang is geïnstalleerd, wordt u gevraagd het Leesmij-bestand te controleren, dat basis vereiste installatie-instructies voor de gateway bevat. Deze installatie-instructies bevinden zich ook in de volgende sectie: [Configureer de gateway](#configure-the-gateway). Het pad naar het Leesmij-bestand `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`is.

### <a name="configure-the-gateway"></a>De gateway configureren

De cmdlet **install-PswaWebApplication** is een snelle manier om Windows Power shell-webtoegang te laten configureren. Hoewel u de `UseTestCertificate` para meter aan de `Install-PswaWebApplication` cmdlet kunt toevoegen om een zelfondertekend SSL-certificaat te installeren voor test doeleinden, is dit niet veilig. gebruik voor een veilige productie omgeving altijd een geldig SSL-certificaat dat is ondertekend door een certificerings instantie (CA). Beheerders kunnen het test certificaat vervangen door een ondertekend certificaat van hun keuze met behulp van de IIS-beheer console.

U kunt de configuratie van webtoepassingen voor Windows Power shell-webtoegang volt ooien door de `Install-PswaWebApplication` cmdlet uit te voeren of door op GUI gebaseerde configuratie stappen in IIS-beheer uit te voeren.
De cmdlet installeert standaard de webtoepassing, **pswa** (en een groep van toepassingen voor de toepassing, **pswa_pool**), in de **standaard** website container, zoals weer gegeven in IIS-beheer. Desgewenst kunt u de cmdlet opdracht geven de standaard site container van de webtoepassing te wijzigen. IIS-beheer biedt configuratie opties die beschikbaar zijn voor webtoepassingen, zoals het wijzigen van het poort nummer of het certificaat van de Secure Sockets Layer (SSL).

> [!IMPORTANT]
> Het wordt ten zeerste aangeraden dat beheerders de gateway configureren voor het gebruik van een geldig certificaat dat is ondertekend door een CA.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>De gateway voor Windows Power shell-webtoegang configureren met een test certificaat met behulp van install-PswaWebApplication

1. Voer een van de volgende handelingen uit om een Windows Power shell-sessie te openen.

   - Klik op het Windows-bureau blad met de rechter muisknop op **Windows Power shell** op de taak balk.
   - Klik in het Windows- **Start** scherm op **Windows Power shell**.

2. Typ het volgende en druk op **Enter**.

   `Install-PswaWebApplication -UseTestCertificate`

   > [!IMPORTANT]
   > De `UseTestCertificate` para meter mag alleen worden gebruikt in een persoonlijke test omgeving. Voor een veilige productie omgeving kunt u het beste een geldig certificaat gebruiken dat is ondertekend door een certificerings instantie.

   Als u de cmdlet uitvoert, wordt de Windows Power shell Web Access-webtoepassing in de standaard website van de IIS-website geïnstalleerd. De cmdlet maakt de infra structuur die vereist is voor het uitvoeren van Windows Power shell- `https://<server_name>/pswa`Internet toegang op de standaard website. Als u de webtoepassing in een andere website wilt installeren, geeft u de naam van `WebSiteName` de website op door de para meter toe te voegen. Als u de naam van de webtoepassing wilt wijzigen (de `pswa`standaard instelling is) `WebApplicationName` , voegt u de para meter toe.

   De volgende instellingen worden geconfigureerd door de cmdlet uit te voeren. U kunt deze desgewenst hand matig wijzigen in de IIS-beheer console.

   - Pad:/pswa
   - Application Pool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath:% windir%/Web/PowerShellWebAccess/wwwroot

   **Voor beeld**:`Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

   In dit voor beeld is `https://<server_name>/myWebApp`de resulterende website voor Windows Power shell Web Access.

   > [!NOTE]
   > U kunt zich pas aanmelden nadat gebruikers toegang tot de website hebben gekregen door autorisatie regels toe te voegen. Zie [een beperkende autorisatie regel](#configure-a-restrictive-authorization-rule) en [autorisatie regels en beveiligings functies van Windows Power shell-Internet toegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md)configureren voor meer informatie.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>De gateway voor Windows Power shell-webtoegang configureren met een authentiek certificaat met behulp van install-PswaWebApplication en IIS-beheer

1. Voer een van de volgende handelingen uit om een Windows Power shell-sessie te openen.

   - Klik op het Windows-bureau blad met de rechter muisknop op **Windows Power shell** op de taak balk.
   - Klik in het Windows- **Start** scherm op **Windows Power shell**.

2. Typ het volgende en druk op **Enter**.

   `Install-PswaWebApplication`

   De volgende gateway-instellingen worden geconfigureerd door de cmdlet uit te voeren. U kunt deze desgewenst hand matig wijzigen in de IIS-beheer console. U kunt ook waarden voor de `WebsiteName` para meters en `WebApplicationName` opgeven `Install-PswaWebApplication` voor de cmdlet.

   - Pad:/pswa
   - Application Pool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath:% windir%/Web/PowerShellWebAccess/wwwroot

3. Open de IIS-beheer console door een van de volgende handelingen uit te voeren.

   - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Klik in het menu **extra** in Serverbeheer op **Internet Information Services (IIS) Manager**.
   - Klik op **Serverbeheer**in het **Start** scherm van Windows.

4. Vouw in het structuur deel venster van de IIS-beheerder het knoop punt uit voor de server waarop Windows Power shell-webtoegang is geïnstalleerd totdat de map **sites** zichtbaar is. Vouw de map **sites** uit.

5. Selecteer de website waarin u de Windows Power shell Web Access-webtoepassing hebt geïnstalleerd.
   Klik in het deel venster **acties** op **bindingen**.

6. Klik in het dialoog venster **site binding** op **toevoegen**.

7. In het dialoog venster **site binding toevoegen** in het veld **type** selecteert u **https**.

8. Selecteer uw ondertekende certificaat in het vervolg keuzemenu van het veld **SSL-certificaat** .
   Klik op **OK**. Zie [een SSL-certificaat configureren in IIS-beheer](#to-configure-an-ssl-certificate-in-iis-manager) in dit onderwerp voor meer informatie over het verkrijgen van een certificaat.

   De webtoepassing voor Windows Power shell Web Access is nu geconfigureerd voor het gebruik van uw ondertekend SSL-certificaat.

   U kunt toegang krijgen tot Windows Power shell- `https://<server_name>/pswa` Internet toegang door te openen in een browser venster.

   > [!NOTE]
   > U kunt zich pas aanmelden nadat gebruikers toegang tot de website hebben gekregen door autorisatie regels toe te voegen. Zie [Configure a beperkend Authorization Rule](#configure-a-restrictive-authorization-rule)(in dit onderwerp) en [autorisatie regels en beveiligings functies van Windows Power shell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md)voor meer informatie.

### <a name="configure-a-restrictive-authorization-rule"></a>Een beperkende autorisatie regel configureren

Nadat Windows Power shell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, kunnen gebruikers de aanmeldings pagina in een browser openen, maar ze kunnen zich niet aanmelden totdat de beheerder van Windows Power shell-webtoegang expliciet toegang verleent voor gebruikers. Toegangs beheer voor Windows Power shell-webtoegang wordt beheerd met behulp van de set Windows Power shell-cmdlets die in de volgende tabel worden beschreven. Er is geen vergelijk bare GUI voor het toevoegen of beheren van autorisatie regels. Zie de cmdlet-naslag onderwerpen voor [Windows Power shell Web Access cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)(Engelstalig) voor meer informatie over Windows Power shell Web Access-cmdlets.

Zie [autorisatie regels en beveiligings functies van Windows Power shell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md)voor meer informatie over de autorisatie regels en beveiliging voor Windows Power shell-webtoegang.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Een beperkende autorisatie regel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

   - Klik op het bureaublad van Windows met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **Als administrator uitvoeren**.
   - Klik op het Windows- **Start** scherm met de rechter muisknop op **Windows Power shell**en klik vervolgens op **als administrator uitvoeren**.

2. Optionele stap voor het beperken van gebruikers toegang met behulp van sessie configuraties: Controleer of de sessie configuraties die u in uw regels wilt gebruiken al bestaan. Als ze nog niet zijn gemaakt, gebruikt u de instructies voor het maken van sessie configuraties in [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Typ het volgende en druk op **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Met deze autorisatie regel kan een specifieke gebruiker toegang hebben tot één computer in het netwerk waartoe deze doorgaans toegang hebben, met toegang tot een specifieke sessie configuratie die wordt afgestemd op de typische scripting-en cmdlet-vereisten van de gebruiker.

   In het volgende voor beeld wordt een gebruiker `JSmith` met de `Contoso` naam in het domein toegang verleend voor het `Contoso_214`beheren van de computer en een sessie `NewAdminsOnly`configuratie met de naam.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Controleer of de regel is gemaakt door de `Get-PswaAuthorizationRule` cmdlet uit te voeren of`Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

   Bijvoorbeeld `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Nadat u een autorisatie regel hebt geconfigureerd, bent u er klaar voor dat geautoriseerde gebruikers zich kunnen aanmelden bij de webconsole en gebruikmaken van Windows Power shell-webtoegang.

## <a name="custom-deployment"></a>Aangepaste implementatie

U kunt de Windows Power shell Web Access-gateway installeren op een server met Windows Server 2012 R2 of Windows Server 2012 met behulp van de wizard functies en onderdelen toevoegen in Serverbeheer.
Nadat Windows Power shell Web Access is geïnstalleerd, kunt u de configuratie van de gateway in IIS-beheer aanpassen.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Windows Power shell-webtoegang installeren met behulp van de wizard functies en onderdelen toevoegen

1. Als Serverbeheer al geopend is, gaat u naar de volgende stap. Als Serverbeheer niet al geopend is, op een van de volgende manieren openen.

   - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows.
   - Klik op **Serverbeheer**in het **Start** scherm van Windows.

2. Op de **beheren** menu, klikt u op **functies en onderdelen toevoegen**.

3. Selecteer op de pagina **Type installatie selecteren** de optie **Installatie die op de functie of het onderdeel is gebaseerd**.
   Klik op **Volgende**.

4. Op de **Selecteer doelserver** pagina, selecteer een server uit de servergroep of Selecteer een offline-VHD. Als u een offline-VHD als de doelserver wilt selecteren, kiest u eerst de server waaraan u de VHD wilt koppelen en selecteert u vervolgens het VHD-bestand. Raadpleeg de Help van Serverbeheer voor informatie over het toevoegen van servers aan uw server groep. Nadat u de doelserver hebt geselecteerd, klikt u op **volgende**.

5. Op de pagina **onderdelen selecteren** van de wizard vouwt u **Windows Power shell**uit en selecteert u **Windows Power shell-webtoegang**.

6. U wordt gevraagd om vereiste onderdelen toe te voegen, zoals .NET Framework 4,5, en functie Services van web server (IIS). Voeg de vereiste onderdelen toe en ga door.

   > [!NOTE]
   > Windows Power shell-webtoegang installeren met behulp van de wizard functies en onderdelen toevoegen installeert ook webserver (IIS), met inbegrip van de module IIS-beheer. De module en andere IIS-beheer hulpprogramma's worden standaard geïnstalleerd als u de wizard functies en onderdelen toevoegen gebruikt. Als u Windows Power shell-Internet toegang installeert met behulp van Windows Power shell-cmdlets, zoals beschreven in de volgende procedure, worden er geen beheer hulpprogramma's standaard toegevoegd.

7. Als de onderdeel bestanden voor Windows Power shell-webtoegang op de pagina **installatie selecties bevestigen** niet zijn opgeslagen op de doel server die u hebt geselecteerd in stap 4, klikt u op **een alternatief bronpad opgeven**en geeft u het pad op naar de onderdeel bestanden. Klik anders op **installeren**.

8. Nadat u op **installeren**hebt geklikt, toont de pagina **installatie voortgang** de voortgang van de installatie, resultaten en berichten, zoals waarschuwingen, fouten of configuratie stappen na de installatie die vereist zijn voor Windows Power shell-Internet toegang. Nadat Windows Power shell-webtoegang is geïnstalleerd, wordt u gevraagd het Leesmij-bestand te controleren, dat basis vereiste installatie-instructies voor de gateway bevat. Deze instructies zijn ook opgenomen in dit onderwerp. Het pad naar het Leesmij-bestand `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`is.

### <a name="configure-the-gateway"></a>De gateway configureren

De instructies in deze sectie zijn voor het installeren van de Windows Power shell Web Access-webtoepassing in een submap en niet in de hoofdmap van uw website. Deze procedure is de op GUI gebaseerde equivalent van de acties die worden uitgevoerd `Install-PswaWebApplication` door de cmdlet. Deze sectie bevat ook instructies voor het gebruik van IIS-beheer voor het configureren van de Windows Power shell Web Access-Gateway als een basis website.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>IIS-beheer gebruiken om de gateway te configureren in een bestaande website

1. Open de IIS-beheer console door een van de volgende handelingen uit te voeren.

   - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Klik in het menu **extra** in Serverbeheer op **Internet Information Services (IIS) Manager**.
   - Typ op het **Start** scherm van Windows een deel van de naam **Internet Information Services (IIS) Manager**. Klik op de snelkoppeling wanneer deze wordt weer gegeven in de **apps** -resultaten.

2. Maak een nieuwe groep van toepassingen voor Windows Power shell-Internet toegang. Vouw het knoop punt van de gateway server uit in het structuur deel venster van de IIS-beheerder, selecteer **groepen van toepassingen**en klik op **groep van toepassingen toevoegen** in het deel venster **acties** .

3. Voeg een nieuwe groep van toepassingen toe met de naam **pswa_pool**of geef een andere naam op. Klik op **OK**.

4. Vouw in het structuur deel venster van de IIS-beheerder het knoop punt uit voor de server waarop Windows Power shell-webtoegang is geïnstalleerd totdat de map **sites** zichtbaar is. Selecteer de map **sites** .

5. Klik met de rechter muisknop op de website (bijvoorbeeld **standaard website**) waaraan u de website met Windows Power shell-webtoegang wilt toevoegen en klik vervolgens op **toepassing toevoegen**.

6. Typ pswa in het veld **alias** of geef een andere alias op. De alias wordt de naam van de virtuele map. **Pswa** in de volgende URL duidt bijvoorbeeld op de alias die is opgegeven in deze `https://<server-name>/pswa`stap:.

7. Selecteer in het veld **groep van toepassingen** de groep van toepassingen die u in stap 3 hebt gemaakt.

8. Blader in het veld **fysiek pad** naar de locatie van de toepassing. U kunt de standaard locatie gebruiken `$env:windir/Web/PowerShellWebAccess/wwwroot`. Klik op **OK**.

9. Volg de stappen in de procedure [voor het configureren van een SSL-certificaat in IIS-beheer](#to-configure-an-ssl-certificate-in-iis-manager) in dit onderwerp.

10. Optionele beveiligings stap:

    Selecteer de website die is geselecteerd in het structuur venster en dubbel klik op **SSL-instellingen** in het deel venster inhoud.
    Selecteer **SSL vereisen**en klik vervolgens in het deel venster **acties** op **Toep assen**. Desgewenst kunt u in het deel venster **SSL-instellingen** vereisen dat gebruikers die verbinding maken met de website Windows Power shell Web Access client certificaten hebben. Client certificaten helpen bij het verifiëren van de identiteit van een gebruiker van een client apparaat. Zie [autorisatie regels en beveiligings functies van Windows Power shell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md) in deze hand leiding voor meer informatie over hoe client certificaten de beveiliging van Windows Power shell-webtoegang kunnen verbeteren.

11. Open een browser sessie op een client apparaat. Zie voor meer informatie over ondersteunde browsers en apparaten [ondersteuning voor browsers en client apparaten](#browser-and-client-device-support) in dit onderwerp.

12. Open de nieuwe Windows Power shell Web Access-website, **https://\<*Gateway-server naam*\>/pswa**.

    De browser moet de aanmeldings pagina van Windows Power shell Web Access-console weer geven.

    > [!NOTE]
    > U kunt zich pas aanmelden nadat gebruikers toegang tot de website hebben gekregen door autorisatie regels toe te voegen. Zie [Configure a beperkend Authorization Rule](#configure-a-restrictive-authorization-rule)(in dit onderwerp) en [autorisatie regels en beveiligings functies van Windows Power shell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md)voor meer informatie.

13. In een Windows Power shell-sessie die is geopend met verhoogde gebruikers rechten (als administrator uitvoeren) voert u het volgende script uit, waarin *application_pool_name* staat voor de naam van de groep van toepassingen die u in stap 3 hebt gemaakt, om de groep toepassingen toegangs rechten tot het autorisatie bestand te geven.

    ```powershell
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Als u de bestaande toegangs rechten voor het autorisatie bestand wilt weer geven, voert u de volgende opdracht uit:

    ```powershell
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>IIS-beheer gebruiken om de gateway te configureren als een basis website met een test certificaat

1. Open de IIS-beheer console door een van de volgende handelingen uit te voeren.

   - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Klik in het menu **extra** in Serverbeheer op **Internet Information Services (IIS) Manager**.
   - Typ op het **Start** scherm van Windows een deel van de naam **Internet Information Services (IIS) Manager**. Klik op de snelkoppeling wanneer deze wordt weer gegeven in de **apps** -resultaten.

1. Vouw in het structuur deel venster van de IIS-beheerder het knoop punt uit voor de server waarop Windows Power shell-webtoegang is geïnstalleerd totdat de map **sites** zichtbaar is. Selecteer de map **sites** .

1. Klik in het deel venster **acties** op **website toevoegen**.

1. Typ een naam voor de website, zoals **Windows Power shell-webtoegang**.

1. Er wordt automatisch een groep van toepassingen gemaakt voor de nieuwe website. Als u een andere groep toepassingen wilt gebruiken, klikt u op **selecteren** om een groep toepassingen te selecteren die u wilt koppelen aan de nieuwe website. Selecteer de groep alternatieve toepassingen in het dialoog venster **groep van toepassingen selecteren** en klik vervolgens op **OK**.

1. Navigeer in het tekstvak **fysiek pad** naar% windir%/Web/PowerShellWebAccess/wwwroot.

1. Selecteer in het veld **type** van het gedeelte **binding** de optie **https**.

1. Wijs een poort nummer toe aan de website die nog niet wordt gebruikt door een andere site of toepassing.
   Als u open poorten wilt vinden, kunt u de opdracht **netstat** uitvoeren in een opdracht prompt venster. Het standaard poort nummer is 443.

   Wijzig de standaard poort als een andere website al gebruikmaakt van 443 of als u andere beveiligings redenen hebt om het poort nummer te wijzigen. Als een andere website op uw gateway server gebruikmaakt van de geselecteerde poort, wordt een waarschuwing weer gegeven wanneer u in het dialoog venster **website toevoegen** op **OK** klikt. U moet een niet-gebruikte poort gebruiken om Windows Power shell-Internet toegang uit te voeren.

1. Geef eventueel, indien nodig voor uw organisatie, een hostnaam op die zinvol is voor uw organisatie en gebruikers, zoals **`www.contoso.com`**. Klik op **OK**.

1. Voor een veiligere productie omgeving raden we u ten zeerste aan een geldig certificaat op te geven dat is ondertekend door een certificerings instantie. U moet een SSL-certificaat opgeven, omdat gebruikers alleen via een HTTPS-website verbinding kunnen maken met Windows Power shell-webtoegang. Zie [een SSL-certificaat configureren in IIS-beheer](#to-configure-an-ssl-certificate-in-iis-manager) in dit onderwerp voor meer informatie over het verkrijgen van een certificaat.

1. Klik op **OK** om het dialoog venster **website toevoegen** te sluiten.

1. In een Windows Power shell-sessie die is geopend met verhoogde gebruikers rechten (als administrator uitvoeren) voert u het volgende script uit, waarin _application_pool_name_ staat voor de naam van de groep van toepassingen die u in stap 4 hebt gemaakt, om de groep toepassingen toegangs rechten tot het autorisatie bestand te geven.

   ```powershell
   $applicationPoolName = "<application_pool_name>"
   $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
   c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
   ```

   Als u de bestaande toegangs rechten voor het autorisatie bestand wilt weer geven, voert u de volgende opdracht uit:

   ```powershell
   c:\windows\system32\icacls.exe $authorizationFile
   ```

1. Selecteer de nieuwe website in het structuur deel venster van de IIS-beheerder en klik op **starten** in het deel venster **acties** om de website te starten.

1. Open een browser sessie op een client apparaat. Zie voor meer informatie over ondersteunde browsers en apparaten [ondersteuning voor browsers en client apparaten](#browser-and-client-device-support) in dit document.

1. Open de nieuwe Windows Power shell-website voor webtoegang.

   Omdat de hoofd website naar de map Windows Power shell Web Access verwijst, moet de browser de aanmeldings pagina voor Windows Power shell-webtoegang weer geven `https://<gateway_server_name>`wanneer u opent. Het is niet nodig om **/pswa** toe te voegen aan de URL.

   > [!NOTE]
   > U kunt zich pas aanmelden nadat gebruikers toegang tot de website hebben gekregen door autorisatie regels toe te voegen. Zie [Configure a beperkend Authorization Rule](#configure-a-restrictive-authorization-rule)(in dit onderwerp) en [autorisatie regels en beveiligings functies van Windows Power shell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md)voor meer informatie.

### <a name="configuring-a-restrictive-authorization-rule"></a>Een beperkende autorisatie regel configureren

Nadat Windows Power shell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, kunnen gebruikers de aanmeldings pagina in een browser openen, maar ze kunnen zich niet aanmelden totdat de beheerder van Windows Power shell-webtoegang expliciet toegang verleent voor gebruikers. Toegangs beheer voor Windows Power shell-webtoegang wordt beheerd met behulp van de set Windows Power shell-cmdlets die in de volgende tabel worden beschreven. Er is geen vergelijk bare GUI voor het toevoegen of beheren van autorisatie regels. Zie de cmdlet-naslag onderwerpen voor [Windows Power shell Web Access cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)(Engelstalig) voor meer informatie over Windows Power shell Web Access-cmdlets.

Zie [autorisatie regels en beveiligings functies van Windows Power shell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md)voor meer informatie over de autorisatie regels en beveiliging voor Windows Power shell-webtoegang.

#### <a name="adding-a-restrictive-authorization-rule"></a>Een beperkende autorisatie regel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

   - Klik op het bureaublad van Windows met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **Als administrator uitvoeren**.
   - Klik op het Windows- **Start** scherm met de rechter muisknop op **Windows Power shell**en klik vervolgens op **als administrator uitvoeren**.

1. Optionele stap voor het beperken van gebruikers toegang met behulp van sessie configuraties:

   Controleer of de sessie configuraties die u in uw regels wilt gebruiken al bestaan. Als ze nog niet zijn gemaakt, gebruikt u de instructies voor het maken van sessie configuraties in [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Typ het volgende en druk op **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Met deze autorisatie regel kan een specifieke gebruiker toegang hebben tot één computer in het netwerk waartoe deze doorgaans toegang hebben, met toegang tot een specifieke sessie configuratie die is afgestemd op de&trade;standaard vereisten voor het uitvoeren van scripts en cmdlets van de gebruiker.

   In het volgende voor beeld wordt een gebruiker `JSmith` met de `Contoso` naam in het domein toegang verleend voor het `Contoso_214`beheren van de computer en een sessie `NewAdminsOnly`configuratie met de naam.

   `Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

1. Controleer of de regel is gemaakt door de `Get-PswaAuthorizationRule` cmdlet uit te voeren of. `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`

   Bijvoorbeeld `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   Nadat u een autorisatie regel hebt geconfigureerd, bent u er klaar voor dat geautoriseerde gebruikers zich kunnen aanmelden bij de webconsole en gebruikmaken van Windows Power shell-webtoegang.

## <a name="configure-a-genuine-certificate"></a>Een authentiek certificaat configureren

Gebruik voor een veilige productie omgeving altijd een geldig SSL-certificaat dat is ondertekend door een certificerings instantie (CA). In de procedure in deze sectie wordt beschreven hoe u een geldig SSL-certificaat van een CA kunt verkrijgen en Toep assen.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Een SSL-certificaat configureren in IIS-beheer

1. Selecteer in het structuur deel venster van IIS-beheer de server waarop Windows Power shell-webtoegang is geïnstalleerd.

1. Dubbel klik in het inhouds venster op **server certificaten**.

1. Voer een van de volgende handelingen uit in het deel venster **acties** . Zie [Configuring server certificates in IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10))(Engelstalig) voor meer informatie over het configureren van server certificaten in IIS.

   - Klik op **importeren** om een bestaand, geldig certificaat te importeren van een locatie in uw netwerk.
   - Klik op **certificaat aanvraag maken** om een certificaat aan te vragen bij een certificerings instantie zoals [VeriSign](https://www.verisign.com/), [Thawte](https://www.thawte.com/)of [GeoTrust](https://www.geotrust.com/). De algemene naam van het certificaat moet overeenkomen met de host-header in de aanvraag.

     Als de client browser bijvoorbeeld vraagt `http://www.contoso.com/`, moet de algemene naam ook zijn. `http://www.contoso.com/` Dit is de veiligste en aanbevolen optie voor het leveren van de Windows Power shell Web Access-gateway met een certificaat.

   - Klik op **een zelfondertekend certificaat maken** om een certificaat te maken dat u onmiddellijk kunt gebruiken en dat u later door een CA hebt ondertekend, indien gewenst. Geef een beschrijvende naam op voor het zelfondertekende certificaat, zoals **Windows Power shell-webtoegang**. Deze optie wordt niet als veilig beschouwd en wordt alleen aanbevolen voor een persoonlijke test omgeving.

1. Nadat u een certificaat hebt gemaakt of verkregen, selecteert u de website waarop het certificaat wordt toegepast (bijvoorbeeld **standaard website**) in het structuur venster van de IIS-beheerder en klikt u vervolgens op **bindingen** in het deel venster **acties** .

1. Voeg in het dialoog venster **site binding toevoegen** een **https** -binding voor de site toe als deze nog niet wordt weer gegeven. Als u geen zelfondertekend certificaat gebruikt, geeft u de hostnaam op uit stap 3 van deze procedure. Als u een zelfondertekend certificaat gebruikt, is deze stap niet vereist.

1. Selecteer het certificaat dat u in stap 3 van deze procedure hebt verkregen of gemaakt en klik vervolgens op **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>De Windows Power shell-console van het web gebruiken

Nadat Windows Power shell-webtoegang is geïnstalleerd en de configuratie van de gateway is voltooid, zoals wordt beschreven in dit onderwerp, is de op het web gebaseerde Windows Power shell-console klaar voor gebruik. Zie [de op het web gebaseerde Windows Power shell-console gebruiken](use-the-web-based-windows-powershell-console.md)voor meer informatie over het starten van de webconsole.

## <a name="see-also"></a>Zie ook

[Documentatie voor Internet Information Services (IIS) 7,0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[Help voor IIS-beheer 7,0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Webserver beveiliging configureren (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))

[IPsec-implementatie resources](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))
