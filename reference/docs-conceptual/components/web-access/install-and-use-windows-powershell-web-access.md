---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: installeren en gebruiken van windows powershell-webtoegang
ms.openlocfilehash: 53558f9be5065c7f630f06e535ddab4d7ad72d9e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058561"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Installeren en gebruiken van Windows PowerShell-internettoegang

Bijgewerkt: 5: november 2013 (bewerkt: 23 augustus 2017)

Van toepassing op: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Inleiding

Windows PowerShell-webtoegang, geïntroduceerd in Windows Server 2012, fungeert als een Windows PowerShell-gateway, die een web-console op basis van Windows PowerShell die is gericht op een externe computer. Hiermee kunnen IT-professionals Windows PowerShell-opdrachten en scripts uitvoeren vanuit een Windows PowerShell-console in een webbrowser, zonder Windows PowerShell, extern beheer van software of door de browser-invoegtoepassing installatie nodig op het clientapparaat. Het enige dat is vereist voor het uitvoeren van de website op basis van Windows PowerShell-console is een goed geconfigureerde Windows PowerShell Web Access-gateway en een browser op het clientapparaat die JavaScript ondersteunt en cookies accepteert.

Voorbeelden van clientapparaten zijn laptops, personal computers die niet wordt gewerkt, geleende computers, tablets, webkiosks, computers die niet met een Windows-besturingssystemen en browsers op mobiele telefoons. IT-professionals kunnen kritieke beheertaken uitvoeren op externe Windows-servers vanaf apparaten die toegang tot een internetverbinding en een webbrowser hebben.

Nadat de gateway is geïnstalleerd en geconfigureerd, kunnen gebruikers een Windows PowerShell-console openen via een webbrowser. Wanneer gebruikers de beveiligde website van Windows PowerShell-webtoegang opent, kunnen ze een Windows PowerShell web gebaseerde console uitgevoerd na een geslaagde authenticatie.

Windows PowerShell-webtoegang installatie en configuratie is een proces drie stappen:

1. [Windows PowerShell-webtoegang installeren](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [De Gateway configureren](#configure-the-gateway)
1. [Configureren van een beperkende autorisatieregel toevoegen](#configure-a-restrictive-authorization-rule)

Voordat u installeert en Windows PowerShell-webtoegang configureert, wordt aangeraden dat u deze volledige handleiding, inclusief instructies over het installeren, beveiligen en Windows PowerShell-internettoegang verwijderen. De [via de Console Windows PowerShell Web gebaseerde](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) onderwerp wordt beschreven hoe gebruikers aanmelden bij de webconsole, en bevat informatie over de beperkingen en verschillen tussen de Windows PowerShell web gebaseerde beheerconsole en de  **PowerShell.exe** console. Eindgebruikers van de webconsole moet lezen [gebruik het Web op basis van Windows PowerShell-Console](use-the-web-based-windows-powershell-console.md), maar hoeft niet te lezen van de rest van deze handleiding.

In dit onderwerp biedt geen gedetailleerde richtlijnen voor IIS-webserver-bewerkingen; alleen de stappen die zijn vereist voor het configureren van de Windows PowerShell Web Access-gateway worden beschreven in dit onderwerp. Zie voor meer informatie over het configureren en beveiligen van websites in IIS, de IIS-documentatie in de sectie Zie ook.

Het volgende diagram laat zien hoe Windows PowerShell-webtoegang werkt.

![Diagram van Windows PowerShell-webtoegang](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Vereisten voor het uitvoeren van Windows PowerShell-webtoegang

Windows PowerShell-webtoegang vereist webserver (IIS), .NET Framework 4.5 en Windows PowerShell 3.0 of Windows PowerShell 4.0 worden uitgevoerd op de server waarop u wilt uitvoeren van de gateway. U kunt Windows PowerShell-webtoegang installeren op een server waarop Windows Server 2012 R2 of Windows Server 2012 met behulp van hetzij de toevoegen Wizard functies en onderdelen in Serverbeheer of Windows PowerShell-implementatie-cmdlets voor Server Manager. Wanneer u Windows PowerShell-webtoegang installeren met behulp van Serverbeheer of de implementatie-cmdlets, worden vereiste functies en onderdelen automatisch toegevoegd als onderdeel van het installatieproces.

Windows PowerShell Web Access kunnen externe gebruikers toegang krijgen tot computers in uw organisatie met behulp van Windows PowerShell in een webbrowser. Hoewel Windows PowerShell-webtoegang een handig en krachtige beheerprogramma is, het web gebaseerde toegang beveiligingsrisico met zich meebrengt, en zo veilig mogelijk moet worden geconfigureerd. We raden aan dat beheerders die de Windows PowerShell Web Access-gateway configureren gebruiken beschikbare beveiligingslagen, zowel de cmdlets gebaseerde autorisatieregels opgenomen met Windows PowerShell-webtoegang en beveiliging lagen die beschikbaar in webserver zijn ( IIS) en toepassingen van derden. Deze documentatie bevat zowel onveilige voorbeelden die alleen voor testomgevingen worden aanbevolen, als voorbeelden die worden aanbevolen voor beveiligde implementaties.

## <a name="browser-and-client-device-support"></a>Ondersteuning voor browsers en clientapparaten apparaten

Windows PowerShell-webtoegang biedt ondersteuning voor de volgende internetbrowsers. Hoewel mobiele browsers officieel niet worden ondersteund, is het mogelijk dat veel kunnen worden uitgevoerd van de website op basis van Windows PowerShell-console.
Andere browsers die cookies, run JavaScript en HTTPS-websites uitvoeren naar verwachting werken, maar zijn niet officieel getest.

### <a name="supported-desktop-computer-browsers"></a>Ondersteunde browsers voor desktopcomputers

- Windows Internet Explorer voor Microsoft Windows 8.0, 9.0, 10.0 en 11.0
- Mozilla Firefox 10.0.2
- Google Chrome-17.0.963.56m voor Windows
- Apple Safari 5.1.2 voor Windows
- Apple Safari 5.1.2 voor Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Minimaal zijn getest met mobiele apparaten of browsers

- Windows Phone 7 en 7.5
- Google Android via WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- Apple Safari voor iPhone-besturingssysteem 5.0.1
- Apple Safari voor iPad 2-besturingssysteem 5.0.1

### <a name="browser-requirements"></a>Browservereisten

Voor het gebruik van de Windows PowerShell-webtoegang op basis van een web-console, moeten de browsers het volgende doen.

- Cookies van de website van Windows PowerShell Web Access-gateway.
- Mogelijk om te openen en HTTPS-pagina's te lezen.
- Open en voer de websites die gebruikmaken van JavaScript.

## <a name="recommended-quick-deployment"></a>Aanbevolen snelle implementatie

U kunt de Windows PowerShell Web Access-gateway installeren op een server waarop Windows Server 2012 R2 of Windows Server 2012 met behulp van een Windows PowerShell-cmdlets, of met behulp van de toevoegen Wizard functies en onderdelen die is geopend vanuit binnen Server Manager. Voor snelle installatie en configuratie, gebruikt u Windows PowerShell-cmdlets, zoals beschreven in deze sectie.

1. [Windows PowerShell-webtoegang installeren](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [De Gateway configureren](#configure-the-gateway)
1. [Configureren van een beperkende autorisatieregel toevoegen](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>Windows PowerShell-webtoegang met behulp van PowerShell-cmdlets installeren

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Windows PowerShell-webtoegang installeren met behulp van Windows PowerShell-cmdlets

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

   - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.
   - Op de Windows **Start** met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als Administrator uitvoeren**.

   > [!NOTE]
   > In Windows PowerShell 3.0 en 4.0: Er is niet nodig de module Serverbeheer cmdlet importeren in de Windows PowerShell-sessie voordat u cmdlets die deel van de module uitmaken uitvoert. Een module wordt automatisch geïmporteerd de eerste keer dat u een cmdlet die deel uitmaakt van de module uitvoert.
   > Windows PowerShell-cmdlets zijn ook niet hoofdlettergevoelig.

1. Typ het volgende en druk vervolgens op **Enter**, waarbij *computer_name* staat voor een externe computer waarop u wilt installeren van Windows PowerShell-webtoegang, indien van toepassing. De `-Restart` parameter doelservers automatisch opnieuw opgestart als vereist.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > [!NOTE]
   > Windows PowerShell-webtoegang installeren met behulp van Windows PowerShell-cmdlets, wordt Web Server (IIS)-beheerhulpprogramma's standaard niet toegevoegd. Als u de beheerhulpprogramma's installeren op dezelfde server als de Windows PowerShell Web Access-gateway wilt, voegt u toe de `-IncludeManagementTools` parameter aan de installatieopdracht (zoals omschreven in deze stap). Als u de Windows PowerShell Web Access-website vanaf een externe computer beheert, installeert u de module IIS-beheer door het installeren van [Remote Server Administration Tools voor Windows 8.1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) of [Remote Server Administration Hulpprogramma's voor Windows 8](https://www.microsoft.com/en-us/download/details.aspx?id=28972) op de computer van waaruit u wilt beheren van de gateway.

   Voor het installeren van functies en onderdelen op een offline-VHD, voegt u zowel de `-ComputerName` parameter en de `-VHD` parameter. De `-ComputerName` parameter bevat de naam van de server waarop u de VHD wilt koppelen en de `-VHD` parameter bevat het pad naar het VHD-bestand op de gespecificeerde server.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Wanneer de installatie is voltooid, controleert u of Windows PowerShell-webtoegang is geïnstalleerd op de doelservers met de `Get-WindowsFeature` cmdlet op een doelserver in een Windows PowerShell-console die is geopend met verhoogde gebruikersrechten. U kunt ook controleren dat Windows PowerShell-webtoegang in de Serverbeheer-console is geïnstalleerd door het selecteren van een server op de **alle Servers** pagina en weer te geven de **functies en onderdelen** de tegel voor de geselecteerde server. U kunt ook het Leesmij-bestand voor Windows PowerShell-webtoegang weergeven.

1. Nadat u Windows PowerShell-webtoegang is geïnstalleerd, wordt u gevraagd om te controleren van het bestand Leesmij-bestand, dat vereiste basisinstallatie-instructies voor de gateway bevat. Deze installatie-instructies zijn ook in de volgende sectie [configureren van de Gateway](#configure-the-gateway). Het pad naar het bestand Leesmij is `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>De Gateway configureren

De **Install-PswaWebApplication** cmdlet is een snelle manier om Windows PowerShell-webtoegang is geconfigureerd. Hoewel u kunt toevoegen aan de `UseTestCertificate` parameter voor de `Install-PswaWebApplication` cmdlet voor het installeren van een zelf-ondertekend SSL-certificaat voor test-doeleinden, dit is geen beveiligd; voor een veilige productieomgeving gebruik altijd een geldig SSL-certificaat dat is ondertekend door een certificeringsinstantie (CA). Beheerders kunnen het testcertificaat vervangen met een ondertekend certificaat van hun keuze met behulp van de IIS-beheerconsole.

U kunt Windows PowerShell-webtoegang webtoepassingsconfiguratie door waarop voltooien de `Install-PswaWebApplication` cmdlet of door te voeren op basis van GUI-configuratiestappen in IIS-beheer.
De cmdlet installeert standaard de webtoepassing **pswa** (en een groep van toepassingen, **pswa_pool**) in de **standaardwebsite** container, zoals wordt weergegeven in IIS-beheer; als gewenst is, kunt u opdracht geven de cmdlet om te wijzigen van de standaardcontainer van de site van de web-App. IIS-beheer biedt configuratieopties die beschikbaar voor webtoepassingen zijn, zoals het wijzigen van het poortnummer of het certificaat voor Secure Sockets Layer (SSL).

> **![Opmerking over beveiliging](images/securitynote.jpeg) opmerking over beveiliging** wordt aangeraden dat beheerders de gateway voor het gebruik van een geldig certificaat dat is ondertekend door een CA configureren.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Aan de Windows PowerShell Web Access-gateway configureren met een testcertificaat door middel van Install-PswaWebApplication

1. Doe het volgende om een Windows PowerShell-sessie te openen.

   - Op het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk.
   - Op de Windows **Start** scherm, klikt u op **Windows PowerShell**.

2. Typ het volgende en druk vervolgens op **Enter**.

   `Install-PswaWebApplication -UseTestCertificate`

   > **![Opmerking over beveiliging](images/securitynote.jpeg) opmerking over beveiliging** de `UseTestCertificate` parameter moet alleen worden gebruikt in een persoonlijke testomgeving. Voor een veilige productieomgeving, wordt u aangeraden een geldig certificaat dat is ondertekend door een Certificeringsinstantie.

   De cmdlet uit te voeren, installeert de web-App voor Windows PowerShell-webtoegang in de standaardwebsite voor IIS-container. De cmdlet maakt de infrastructuur die is vereist voor het uitvoeren van Windows PowerShell-webtoegang op de standaardwebsite `https://<server_name>/pswa`. Voor het installeren van de web-App in een andere website, bieden u de naam van de website door toe te voegen de `WebSiteName` parameter. De naam van de web-App te wijzigen (de standaardwaarde is `pswa`), voeg de `WebApplicationName` parameter.

   De volgende instellingen worden geconfigureerd door de cmdlet uit te voeren. Indien gewenst, kunt u deze handmatig op in de console IIS-beheer wijzigen.

   - Pad: / pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

   **Voorbeeld**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

   In dit voorbeeld wordt de resulterende website voor Windows PowerShell-webtoegang is `https://<server_name>/myWebApp`.

   > [!NOTE]
   > U kunt zich niet totdat gebruikers hebben toegang tot de website is verleend door autorisatieregels toe te voegen. Zie voor meer informatie, [configureren van een beperkende autorisatieregel](#configure-a-restrictive-authorization-rule) en [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>De Windows PowerShell Web Access-gateway configureren met een geldig certificaat met behulp van Install-PswaWebApplication en IIS-beheer

1. Doe het volgende om een Windows PowerShell-sessie te openen.

   - Op het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk.
   - Op de Windows **Start** scherm, klikt u op **Windows PowerShell**.

2. Typ het volgende en druk vervolgens op **Enter**.

   `Install-PswaWebApplication`

   De volgende gatewayinstellingen worden geconfigureerd door de cmdlet uit te voeren. Indien gewenst, kunt u deze handmatig op in de console IIS-beheer wijzigen. U kunt ook waarden opgeven voor de `WebsiteName` en `WebApplicationName` parameters van de `Install-PswaWebApplication` cmdlet.

   - Pad: / pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

3. Open de IIS-beheer-console op een van de volgende manieren.

   - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Op de **extra** menu in Serverbeheer, klikt u op **Internet Information Services (IIS) Manager**.
   - Op de Windows **Start** scherm, klikt u op **Serverbeheer**.

4. In het structuurdeelvenster van IIS-beheer, vouw het knooppunt voor de server waarop Windows PowerShell-webtoegang is geïnstalleerd totdat de **Sites** map zichtbaar is. Vouw de **Sites** map.

5. Selecteer de website waarop u de Windows PowerShell-webtoegang web-App hebt geïnstalleerd.
   In de **acties** deelvenster, klikt u op **bindingen**.

6. In de **sitebinding** in het dialoogvenster, klikt u op **toevoegen**.

7. In de **sitebinding toevoegen** in het dialoogvenster de **Type** veld **https**.

8. In de **SSL-certificaat** veld, selecteert u uw ondertekend certificaat in de vervolgkeuzelijst.
   Klik op **OK**. Zie [het configureren van een SSL-certificaat in IIS-beheer](#to-configure-an-ssl-certificate-in-iis-manager) in dit onderwerp voor meer informatie over het verkrijgen van een certificaat.

   De web-App voor Windows PowerShell-webtoegang is nu geconfigureerd voor het gebruik van uw ondertekend SSL-certificaat.

   U kunt Windows PowerShell-webtoegang openen door het openen van `https://<server_name>/pswa` in een browservenster.

   > [!NOTE]
   > U kunt zich niet totdat gebruikers hebben toegang tot de website is verleend door autorisatieregels toe te voegen. Zie voor meer informatie, [configureren van een beperkende autorisatieregel](#configure-a-restrictive-authorization-rule), in dit onderwerp en [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Configureren van een beperkende autorisatieregel toevoegen

Nadat Windows PowerShell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, wordt gebruikers de aanmeldingspagina in een browser kunnen openen, maar ze pas aanmelden nadat de Windows PowerShell Web Access-beheerder gebruikers toegang expliciet verleent. Windows PowerShell-webtoegang toegangsbeheer wordt beheerd met behulp van de set Windows PowerShell-cmdlets die in de volgende tabel beschreven. Er is geen vergelijkbare grafische gebruikersinterface voor het toevoegen of beheren van autorisatieregels. Zie voor meer informatie over Windows PowerShell Web Access cmdlets, de cmdlet-naslaginformatie [Windows PowerShell Web Access Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Zie voor meer informatie over Windows PowerShell-webtoegang autorisatieregels en beveiliging [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Een beperkende autorisatieregel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

   - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.
   - Op de Windows **Start** met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als Administrator uitvoeren**.

2. Optionele stap voor het beperken van toegang voor gebruikers met behulp van sessieconfiguraties: Controleer of de sessieconfiguraties die u wilt gebruiken in uw regels al bestaan. Als ze zijn nog geen is gemaakt, gebruikt u instructies voor het maken van sessieconfiguraties in [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Typ het volgende en druk vervolgens op **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Deze autorisatieregel verleent een bepaalde gebruikerstoegang tot een computer op het netwerk waartoe ze gewoonlijk toegang hebben, met toegang tot een bepaalde sessieconfiguratie die is afgestemd op van de gebruiker gemiddelde scripting en cmdlet-behoeften.

   In het volgende voorbeeld wordt een gebruiker met de naam `JSmith` in de `Contoso` domein krijgt toegangsrechten voor het beheren van de computer `Contoso_214`, en gebruikt een sessieconfiguratie genaamd `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Controleer of dat de regel is gemaakt door de `Get-PswaAuthorizationRule` cmdlet, of `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

   Voorbeeld: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Nadat u een autorisatieregel hebt geconfigureerd, bent u klaar voor geautoriseerde gebruikers zich aanmelden bij de webconsole en beginnen met Windows PowerShell-webtoegang.

## <a name="custom-deployment"></a>Aangepaste implementatie

U kunt de Windows PowerShell Web Access-gateway installeren op een server waarop Windows Server 2012 R2 of Windows Server 2012 met behulp van de toevoegen Wizard functies en onderdelen in Serverbeheer.
Nadat u Windows PowerShell-webtoegang is geïnstalleerd, kunt u de configuratie van de gateway in IIS-beheer kunt aanpassen.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Windows PowerShell-webtoegang met behulp van de toevoegen Wizard functies en onderdelen installeren

1. Als Serverbeheer al geopend is, gaat u naar de volgende stap. Als Serverbeheer niet al geopend is, op een van de volgende manieren openen.

   - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows.
   - Op de Windows **Start** scherm, klikt u op **Serverbeheer**.

2. Op de **beheren** menu, klikt u op **functies en onderdelen toevoegen**.

3. Op de **installatietype selecteren** pagina, selecteert u **op basis van functie of onderdeel gebaseerde installatie**.
   Klik op **Volgende**.

4. Op de **Selecteer doelserver** pagina, selecteer een server uit de servergroep of Selecteer een offline-VHD. Selecteer een offline-VHD als de doelserver, selecteert u eerst de server waarop u de VHD wilt koppelen en selecteer vervolgens het VHD-bestand. Zie de Help van de Server Manager voor meer informatie over het toevoegen van servers aan uw servergroep. Nadat u de doelserver hebt geselecteerd, klikt u op **volgende**.

5. Op de **functies selecteren** pagina van de wizard, vouw **Windows PowerShell**, en selecteer vervolgens **Windows PowerShell-webtoegang**.

6. Houd er rekening mee dat u wordt gevraagd vereiste onderdelen, zoals .NET Framework 4.5 en functieservices van webserver (IIS) toevoegen. Vereiste onderdelen toevoegen en doorgaan.

   > [!NOTE]
   > Windows PowerShell-webtoegang installeren met behulp van de toevoegen Wizard functies en onderdelen installeert ook webserver (IIS), met inbegrip van de module IIS-beheer. De module en andere IIS-beheerhulpprogramma's zijn standaard geïnstalleerd als u de Wizard Functies toevoegen en onderdelen. Als u Windows PowerShell-webtoegang installeren met behulp van Windows PowerShell-cmdlets, zoals beschreven in de volgende procedure, worden standaard niet-beheerhulpprogramma's toegevoegd.

7. Op de **installatie-instellingen bevestigen** pagina als de onderdeelbestanden voor Windows PowerShell-webtoegang worden niet opgeslagen op de doelserver die u hebt geselecteerd in stap 4, klikt u op **eenalternatiefbronpadopgeven**, en geef het pad naar de onderdeelbestanden. Klik anders op **installeren**.

8. Nadat u op **installeren**, wordt de **installatievoortgang** pagina Voortgang van de installatie, resultaten en berichten, zoals waarschuwingen, fouten of na de installatie configuratiestappen die worden weergegeven vereist voor Windows PowerShell-webtoegang. Nadat u Windows PowerShell-webtoegang is geïnstalleerd, wordt u gevraagd om te controleren van het bestand Leesmij-bestand, dat vereiste basisinstallatie-instructies voor de gateway bevat. Deze instructies zijn ook opgenomen in dit onderwerp. Het pad naar het bestand Leesmij is `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>De gateway configureren

Instructies in deze sectie zijn voor het installeren van de web-App voor Windows PowerShell-webtoegang in een submap en niet in de hoofdmap van uw website. Deze procedure is de grafische interface gebaseerde equivalent van de acties die worden uitgevoerd door de `Install-PswaWebApplication` cmdlet. Deze sectie bevat ook instructies voor het IIS-beheer gebruiken om te configureren van de Windows PowerShell Web Access-gateway als primaire website.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>IIS-beheer gebruiken om te configureren van de gateway in een bestaande website

1. Open de IIS-beheer-console op een van de volgende manieren.

   - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Op de **extra** menu in Serverbeheer, klikt u op **Internet Information Services (IIS) Manager**.
   - Op de Windows **Start** scherm, typt u een deel van de naam **Internet Information Services (IIS) Manager**. Klik op de snelkoppeling wanneer deze wordt weergegeven de **Apps** resultaten.

2. Maak een nieuwe groep van toepassingen voor Windows PowerShell-webtoegang. Vouw het knooppunt van de gatewayserver in het structuurdeelvenster IIS-beheer, dat u selecteert **toepassingsgroepen**, en klikt u op **groep van toepassingen toevoegen** in de **acties** deelvenster.

3. Toevoegen van een nieuwe groep van toepassingen met de naam van de **pswa_pool**, of geef een andere naam. Klik op **OK**.

4. In het structuurdeelvenster van IIS-beheer, vouw het knooppunt voor de server waarop Windows PowerShell-webtoegang is geïnstalleerd totdat de **Sites** map zichtbaar is. Selecteer de **Sites** map.

5. Met de rechtermuisknop op de website (bijvoorbeeld **Default Web Site**) op die u wilt toevoegen van de website van Windows PowerShell-webtoegang en klik vervolgens op **toepassing toevoegen**.

6. In de **Alias** veld, typt u pswa of geef een andere alias. De alias wordt de naam van de virtuele map. Bijvoorbeeld, **pswa** vertegenwoordigt de alias die in deze stap in de volgende URL: `https://<server-name>/pswa`.

7. In de **groep van toepassingen** veld, selecteert u de groep van toepassingen die u hebt gemaakt in stap 3.

8. In de **fysiek pad** veld, blader naar de locatie van de toepassing. U kunt de standaardlocatie bevindt, `$env:windir/Web/PowerShellWebAccess/wwwroot`. Klik op **OK**.

9. Volg de stappen in de procedure [het configureren van een SSL-certificaat in IIS-beheer](#to-configure-an-ssl-certificate-in-iis-manager) in dit onderwerp.

10. ![](images/SecurityNote.jpeg) Optionele beveiligingsstap:

    Dubbelklik op de website is geselecteerd in het structuurdeelvenster, **SSL-instellingen** in het inhoudsvenster.
    Selecteer **SSL vereisen**, en klik vervolgens in de **acties** deelvenster, klikt u op **toepassen**. (Optioneel) in de **SSL-instellingen** deelvenster kunt u vereisen dat gebruikers verbinding maken met de Windows PowerShell Web Access-website over clientcertificaten beschikken. Clientcertificaten te controleren of de identiteit van de gebruiker van een client-apparaat. Zie voor meer informatie over hoe clientcertificaten de beveiliging van Windows PowerShell Web Access kan verbeteren, [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md) in deze handleiding.

11. Open een browsersessie op een clientapparaat. Zie voor meer informatie over ondersteunde browsers en apparaten, [Browser en client-apparaat ondersteunt](#browser-and-client-device-support) in dit onderwerp.

12. Open de website van de nieuwe Windows PowerShell-webtoegang, **https://\<*gateway servernaam*\>/pswa**.

    De Windows PowerShell-webtoegang aanmelden pagina van de console moet worden weergegeven in de browser.

    > [!NOTE]
    > U kunt zich niet totdat gebruikers hebben toegang tot de website is verleend door autorisatieregels toe te voegen. Zie voor meer informatie, [configureren van een beperkende autorisatieregel](#configure-a-restrictive-authorization-rule), in dit onderwerp en [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. In een Windows PowerShell-sessie die is geopend met verhoogde gebruikersrechten (als Administrator uitvoeren) voert u het volgende script uit waarin *application_pool_name* vertegenwoordigt de naam van de groep van toepassingen die u hebt gemaakt in stap 3 de groep van toepassingen toegangsrechten tot het autorisatiebestand geven.

    ```powershell
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Als u wilt weergeven van bestaande toegangsrechten voor het autorisatiebestand, voer de volgende opdracht:

    ```powershell
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>IIS-beheer gebruiken om te configureren van de gateway als primaire website met een testcertificaat

1. Open de IIS-beheer-console op een van de volgende manieren.

   - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Op de **extra** menu in Serverbeheer, klikt u op **Internet Information Services (IIS) Manager**.
   - Op de Windows **Start** scherm, typt u een deel van de naam **Internet Information Services (IIS) Manager**. Klik op de snelkoppeling wanneer deze wordt weergegeven de **Apps** resultaten.

1. In het structuurdeelvenster van IIS-beheer, vouw het knooppunt voor de server waarop Windows PowerShell-webtoegang is geïnstalleerd totdat de **Sites** map zichtbaar is. Selecteer de **Sites** map.

1. In de **acties** deelvenster, klikt u op **Website toevoegen**.

1. Typ een naam voor de website, zoals **Windows PowerShell-webtoegang**.

1. Een groep van toepassingen wordt automatisch gemaakt voor de nieuwe website. Voor het gebruik van een andere groep van toepassingen, klikt u op **Selecteer** om te selecteren van een groep van toepassingen om te koppelen aan de nieuwe website. Selecteer de alternatieve groep van toepassingen in de **groep van toepassingen selecteren** in het dialoogvenster en klik vervolgens op **OK**.

1. In de **fysiek pad** tekst vak, gaat u naar % windir%/Web/PowerShellWebAccess/wwwroot.

1. In de **Type** veld van de **Binding** gedeelte **https**.

1. Een poortnummer toewijzen aan de website die nog niet wordt gebruikt door een andere site of toepassing.
   Openstaande poorten vinden, kunt u uitvoeren de **netstat** opdracht in een opdrachtpromptvenster. Het standaardpoortnummer is 443.

   Als een andere website al gebruikmaakt van 443 of als u andere veiligheidsredenen het poortnummer wijzigen hebt, kunt u de standaardpoort wijzigen. Als een andere website die wordt uitgevoerd op de gatewayserver van de geselecteerde poort gebruikmaakt, een waarschuwing wordt weergegeven wanneer u klikt op **OK** in de **Website toevoegen** in het dialoogvenster. U moet een niet-gebruikte poort gebruiken voor het uitvoeren van Windows PowerShell-webtoegang.

1. (Optioneel) Geef de naam van een host die zinvol is voor uw organisatie en gebruikers, zoals zo nodig voor uw organisatie **`www.contoso.com`**. Klik op **OK**.

1. Voor een veiliger productieomgeving, wordt aangeraden een geldig certificaat dat is ondertekend door een Certificeringsinstantie bieden. Omdat gebruikers alleen verbinding met Windows PowerShell-internettoegang via een HTTPS-website maken kunnen, moet u een SSL-certificaat opgeven. Zie [het configureren van een SSL-certificaat in IIS-beheer](#to-configure-an-ssl-certificate-in-iis-manager) in dit onderwerp voor meer informatie over het verkrijgen van een certificaat.

1. Klik op **OK** sluiten de **Website toevoegen** in het dialoogvenster.

1. In een Windows PowerShell-sessie die is geopend met verhoogde gebruikersrechten (als Administrator uitvoeren) voert u het volgende script uit waarin _application_pool_name_ vertegenwoordigt de naam van de groep van toepassingen die u hebt gemaakt in stap 4 de groep van toepassingen toegangsrechten tot het autorisatiebestand geven.

   ```powershell
   $applicationPoolName = "<application_pool_name>"
   $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
   c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
   ```

   Als u wilt weergeven van bestaande toegangsrechten voor het autorisatiebestand, voer de volgende opdracht:

   ```powershell
   c:\windows\system32\icacls.exe $authorizationFile
   ```

1. Met de nieuwe website in het structuurdeelvenster van IIS-beheer hebt geselecteerd, klikt u op **Start** in de **acties** deelvenster starten van de website.

1. Open een browsersessie op een clientapparaat. Zie voor meer informatie over ondersteunde browsers en apparaten, [Browser en client-apparaat ondersteunt](#browser-and-client-device-support) in dit document.

1. Open de nieuwe Windows PowerShell Web Access-website.

   Omdat de primaire-website naar de map Windows PowerShell-webtoegang verwijst, de aanmeldingspagina van Windows PowerShell-webtoegang in de browser moet worden weergegeven bij het openen van `https://<gateway_server_name>`. U hoeft niet om toe te voegen **/pswa** naar de URL.

   > [!NOTE]
   > U kunt zich niet totdat gebruikers hebben toegang tot de website is verleend door autorisatieregels toe te voegen. Zie voor meer informatie, [configureren van een beperkende autorisatieregel](#configure-a-restrictive-authorization-rule), in dit onderwerp en [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configuring-a-restrictive-authorization-rule"></a>Configureren van een beperkende autorisatieregel toevoegen

Nadat Windows PowerShell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, wordt gebruikers de aanmeldingspagina in een browser kunnen openen, maar ze pas aanmelden nadat de Windows PowerShell Web Access-beheerder gebruikers toegang expliciet verleent. Windows PowerShell-webtoegang toegangsbeheer wordt beheerd met behulp van de set Windows PowerShell-cmdlets die in de volgende tabel beschreven. Er is geen vergelijkbare grafische gebruikersinterface voor het toevoegen of beheren van autorisatieregels. Zie voor meer informatie over Windows PowerShell Web Access cmdlets, de cmdlet-naslaginformatie [Windows PowerShell Web Access Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Zie voor meer informatie over Windows PowerShell-webtoegang autorisatieregels en beveiliging [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="adding-a-restrictive-authorization-rule"></a>Een beperkende autorisatieregel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

   - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.
   - Op de Windows **Start** met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als Administrator uitvoeren**.

1. ![Opmerking over beveiliging](images/SecurityNote.jpeg) Optionele stap voor het beperken van toegang voor gebruikers met behulp van sessieconfiguraties:

   Controleer of de sessieconfiguraties die u wilt gebruiken in uw regels al bestaan. Als ze zijn nog geen is gemaakt, gebruikt u instructies voor het maken van sessieconfiguraties in [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Typ het volgende en druk vervolgens op **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Deze autorisatieregel verleent een bepaalde gebruikerstoegang tot een computer op het netwerk waartoe ze gewoonlijk toegang hebben, met toegang tot een bepaalde sessieconfiguratie die is afgestemd op de gebruiker '™ s typische scripting en cmdlet-behoeften.

   In het volgende voorbeeld wordt een gebruiker met de naam `JSmith` in de `Contoso` domein krijgt toegangsrechten voor het beheren van de computer `Contoso_214`, en gebruikt een sessieconfiguratie genaamd `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

1. Controleer of dat de regel is gemaakt door de `Get-PswaAuthorizationRule` -cmdlet of `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

   Voorbeeld: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   Nadat u een autorisatieregel hebt geconfigureerd, bent u klaar voor geautoriseerde gebruikers zich aanmelden bij de webconsole en beginnen met Windows PowerShell-webtoegang.

## <a name="configure-a-genuine-certificate"></a>Een legitiem certificaat configureren

Gebruik voor een veilige productieomgeving altijd een geldig SSL-certificaat dat is ondertekend door een certificeringsinstantie (CA). De procedure in deze sectie wordt beschreven hoe u verkrijgen en toepassen van een geldig SSL-certificaat van een CA.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Het configureren van een SSL-certificaat in IIS-beheer

1. Selecteer de server waarop Windows PowerShell-webtoegang is geïnstalleerd in het structuurdeelvenster van IIS-beheer.

1. In het inhoudsvenster, dubbelklikt u op **servercertificaten**.

1. In de **acties** deelvenster, een van de volgende handelingen uit. Zie voor meer informatie over het configureren van servercertificaten in IIS [Configuring Server Certificates in IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).

   - Klik op **importeren** aan een bestaand en geldig certificaat importeren vanaf een locatie op uw netwerk.
   - Klik op **certificaataanvraag maken** , zoals een certificaat aanvragen bij een Certificeringsinstantie [VeriSign](https://www.verisign.com/), [Thawte](https://www.thawte.com/), of [GeoTrust](https://www.geotrust.com/). Algemene naam van het certificaat moet overeenkomen met de host-header in de aanvraag.

     Bijvoorbeeld, als de clientbrowser aanvragen `http://www.contoso.com/`, de algemene naam moet ook `http://www.contoso.com/`. Dit is de veiligste en aanbevolen optie voor het leveren van de Windows PowerShell Web Access-gateway met een certificaat.

   - Klik op **een zelfondertekend certificaat maken** te maken van een certificaat dat u direct gebruiken kunt en later door een CA hebt ondertekend indien gewenst. Geef een beschrijvende naam voor de zelf-ondertekend certificaat, bijvoorbeeld **Windows PowerShell-webtoegang**. Deze optie is niet als veilig beschouwd en wordt alleen aanbevolen voor een persoonlijke testomgeving.

1. Na het maken of een certificaat aanvragen, selecteert u de website waarop het certificaat wordt toegepast (bijvoorbeeld **Default Web Site**) in de IIS-beheer in het deelvenster met de boomstructuur en klik vervolgens op **bindingen** in de **Acties** deelvenster.

1. In de **sitebinding toevoegen** dialoogvenster vak, toe te voegen een **https** binding voor de site als een nog niet wordt weergegeven. Als u niet een zelfondertekend certificaat gebruikt, geeft u de naam van de host uit stap 3 van deze procedure. Als u een zelfondertekend certificaat gebruikt, is deze stap niet vereist.

1. Selecteer het certificaat dat u hebt gemaakt in stap 3 van deze procedure of verkregen en klik vervolgens op **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Met behulp van de website op basis van Windows PowerShell-console

Nadat u Windows PowerShell-webtoegang is geïnstalleerd en configuratie van de gateway is voltooid zoals beschreven in dit onderwerp, is de Windows PowerShell-webconsole klaar voor gebruik. Zie voor meer informatie over het ophalen van in de webconsole gestart, [via de Console Windows PowerShell Web gebaseerde](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Zie ook

[Internet informatieservices (IIS) 7.0 documentatie](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[IIS 7.0 Manager Help](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Configure Web Server Security (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10))

[IPsec Deployment Resources](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))
