---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: installeren en gebruiken van windows powershell-webtoegang
ms.openlocfilehash: 8f140e73ce833fd1cfadbe1d8ee0fe0bb2d08873
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="install-and-use-windows-powershell-web-access"></a>Windows PowerShell-webtoegang installeren en gebruiken

Bijgewerkte: 5 November 2013 (bewerkt: 23 augustus 2017)

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

## <a name="introduction"></a>Inleiding

Windows PowerShell-webtoegang, geïntroduceerd in Windows Server 2012 fungeert als een Windows PowerShell-gateway, een Windows PowerShell webconsole die is gericht op een externe computer te bieden. Hiermee kunnen IT-professionals Windows PowerShell-opdrachten en scripts uitvoeren vanuit een Windows PowerShell-console in een webbrowser, zonder Windows PowerShell, extern beheer van software of browser invoegtoepassing installatie nodig is op het clientapparaat. Het enige dat is vereist voor het uitvoeren van het web gebaseerde Windows PowerShell-console is een goed geconfigureerde Windows PowerShell Web Access-gateway en een browser op het clientapparaat die JavaScript ondersteunt en cookies accepteert.

Voorbeelden van clientapparaten zijn laptops, privé-pc's, geleende computers, tablets, webkiosks, computers zonder Windows-besturingssystemen en browsers op mobiele telefoons. IT-professionals kunnen kritieke beheertaken uitvoeren op externe Windows-servers vanaf apparaten die toegang tot internet bieden en over een webbrowser beschikken.

Nadat de gateway is geïnstalleerd en geconfigureerd, kunnen gebruikers een Windows PowerShell-console openen met een webbrowser. Wanneer gebruikers de beveiligde Windows PowerShell Web Access-website openen, kunnen ze een webgebaseerde Windows PowerShell-console worden uitgevoerd na een geslaagde authenticatie.

Windows PowerShell Web Access-installatie en configuratie is drie stappen:

1. [Windows PowerShell-webtoegang installeren](#install-windows-powershell-web-access)
1. [De Gateway configureren](#configure-the-gateway)
1. [Configureer een beperkende autorisatieregel toevoegen](#configure-a-restrictive-authorization-rule)

Voordat u installeren en configureren van Windows PowerShell-webtoegang, wordt aangeraden dat u deze volledige handleiding die instructies over het installeren bevat, beveiligen en Windows PowerShell-internettoegang verwijderen.
De [via de Console Windows PowerShell Web gebaseerde](https://technet.microsoft.com/library/hh831417(v=ws.11).aspx) onderwerp wordt beschreven hoe gebruikers aanmelden bij de webconsole en bevat informatie over de beperkingen en verschillen tussen de Windows PowerShell webconsole en de  **PowerShell.exe** console. Eindgebruikers van de webconsole moet worden gelezen [gebruik het Web op basis van Windows PowerShell-Console](use-the-web-based-windows-powershell-console.md), maar hoeven niet lezen van de rest van deze handleiding.

In dit onderwerp biedt geen gedetailleerde richtlijnen voor IIS-webserver-bewerkingen; alleen de stappen die zijn vereist voor het configureren van de Windows PowerShell Web Access-gateway worden beschreven in dit onderwerp. Zie de IIS-documentatie in de sectie Zie ook voor meer informatie over het configureren en beveiligen van websites in IIS.

Het volgende diagram toont de werking van Windows PowerShell Web Access.

![Diagram van Windows PowerShell-webtoegang](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Vereisten voor het uitvoeren van Windows PowerShell-webtoegang

Windows PowerShell-webtoegang vereist webserver (IIS), .NET Framework 4.5 en Windows PowerShell 3.0 of Windows PowerShell 4.0 worden uitgevoerd op de server waarop u wilt uitvoeren van de gateway. U kunt Windows PowerShell-webtoegang installeren op een server waarop Windows Server 2012 R2 of Windows Server 2012 met behulp van de functies en de Wizard in Serverbeheer of Windows PowerShell-cmdlets voor implementatie van functies voor Server Manager. Wanneer u Windows PowerShell-webtoegang installeren met behulp van Serverbeheer of de implementatie-cmdlets, worden vereiste functies en onderdelen automatisch toegevoegd als onderdeel van het installatieproces.

Windows PowerShell Web Access kunnen externe gebruikers toegang krijgen tot computers in uw organisatie met behulp van Windows PowerShell in een webbrowser. Hoewel Windows PowerShell-webtoegang een handig en krachtige beheerprogramma is, de webtoegang veiligheidsrisico's en zo veilig mogelijk moet worden geconfigureerd. We raden aan beheerders die de Windows PowerShell Web Access-gateway configureren gebruiken beschikbare beveiligingslagen, zowel de cmdlets gebaseerde autorisatieregels die zijn opgenomen in Windows PowerShell-webtoegang en beveiliging lagen die beschikbaar in webserver zijn ( IIS) en toepassingen van derden. Deze documentatie bevat zowel onveilige voorbeelden die alleen voor testomgevingen worden aanbevolen, als voorbeelden die worden aanbevolen voor beveiligde implementaties.

## <a name="browser-and-client-device-support"></a>Ondersteuning voor browsers en clientapparaten

Windows PowerShell-webtoegang ondersteunt de volgende internetbrowsers.
Hoewel mobiele browsers officieel niet worden ondersteund, is het mogelijk dat veel kunnen worden uitgevoerd van het web gebaseerde Windows PowerShell-console. Andere browsers die cookies accepteren en waarop JavaScript en HTTPS-websites kunnen worden uitgevoerd, werken waarschijnlijk wel, maar zijn niet officieel getest.

### <a name="supported-desktop-computer-browsers"></a>Ondersteunde browsers voor desktopcomputers

- Windows Internet Explorer voor Microsoft Windows 8.0, 9.0, 10.0 en 11.0
- Mozilla Firefox 10.0.2
- Google Chrome-17.0.963.56m voor Windows
- Apple Safari 5.1.2 voor Windows
- Apple Safari 5.1.2 voor Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Mobiele apparaten of browsers die minimaal zijn getest

- Windows Phone 7 en 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- Apple Safari voor iPhone-besturingssysteem 5.0.1
- Apple Safari voor iPad 2-besturingssysteem 5.0.1

### <a name="browser-requirements"></a>Browservereisten

Voor het gebruik van de webconsole voor Windows PowerShell-webtoegang moeten de browsers het volgende doen.

- Toestaan dat cookies van de website van Windows PowerShell Web Access-gateway.
- HTTPS-pagina's moeten kunnen worden geopend en gelezen.
- Websites die gebruikmaken van JavaScript, moeten kunnen worden geopend en uitgevoerd.

## <a name="recommended-quick-deployment"></a>Aanbevolen snelle implementatie

U kunt de Windows PowerShell Web Access-gateway installeren op een server waarop Windows Server 2012 R2 of Windows Server 2012 met behulp van de Windows PowerShell-cmdlets of via de toevoegen Wizard functies en onderdelen die wordt geopend vanuit binnen Server Manager. Gebruik voor snelle installatie en configuratie Windows PowerShell-cmdlets, zoals beschreven in deze sectie.

1. [Windows PowerShell-webtoegang installeren](#install-Windows-powershell-web-access)
1. [De Gateway configureren](#configure-the-gateway)
1. [Configureer een beperkende autorisatieregel toevoegen](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access"></a>Windows PowerShell-webtoegang installeren

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Windows PowerShell-webtoegang installeren met behulp van Windows PowerShell-cmdlets

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.
    - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.
    - Windows **Start** scherm, met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als Administrator uitvoeren**.

    >**![Opmerking](images/note.jpeg) Opmerking** In Windows PowerShell 3.0 en 4.0 hoeft niet de Serverbeheer-cmdlet-module importeren in de Windows PowerShell-sessie voordat u de cmdlets die deel van de module uitmaken uitvoert. Een module wordt automatisch geïmporteerd tijdens de eerste keer dat u de cmdlet die deel uitmaakt van de module uitvoert. Windows PowerShell-cmdlets zijn ook niet hoofdlettergevoelig.

1. Typ het volgende en druk vervolgens op **Enter**, waarbij *computer_name* staat voor een externe computer waarop u wilt installeren van Windows PowerShell-webtoegang, indien van toepassing. Met de parameter `-Restart` worden zo nodig de doelservers automatisch opnieuw opgestart.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   >**![Opmerking](images/note.jpeg) Opmerking**
   >
   >Windows PowerShell-webtoegang installeren met behulp van Windows PowerShell-cmdlets voegt geen webserver (IIS)-beheerhulpprogramma's standaard. Als u de beheerhulpprogramma's op dezelfde server als de Windows PowerShell Web Access-gateway installeren wilt, voegt u de `-IncludeManagementTools` parameter aan de installatieopdracht (zoals omschreven in deze stap). Als u de Windows PowerShell Web Access-website vanaf een externe computer beheert, installeert u de module IIS-beheer door het installeren van [Remote Server Administration Toolsfor Windows 8.1](http://go.microsoft.com/fwlink/?LinkID=304145) of [Remote Server Administration Hulpprogramma's voor Windows 8](http://go.microsoft.com/fwlink/p/?LinkID=238560) op de computer van waaruit u wilt beheren van de gateway.

   Als u functies en onderdelen op een offline-VHD wilt installeren, dient u de parameter `-ComputerName` en de parameter `-VHD` toe te voegen. De parameter `-ComputerName` bevat de naam van de server waaraan de VHD moet worden gekoppeld en de parameter `-VHD` bevat het pad naar het VHD-bestand op de opgegeven server.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Wanneer de installatie is voltooid, controleert u of Windows PowerShell-webtoegang is geïnstalleerd op de doelservers door het uitvoeren van de **Get-WindowsFeature** cmdlet uit op een doelserver in een Windows PowerShell-console die is geopend met verhoogde gebruikersrechten. U kunt ook controleren dat Windows PowerShell-webtoegang in de Serverbeheer-console is geïnstalleerd door een doelserver selecteren op de **alle Servers** pagina en weer te geven de **functies en onderdelen** de tegel voor de geselecteerde server. U kunt ook het Leesmij-bestand voor Windows PowerShell Web Access weergeven.

1. Nadat u Windows PowerShell-webtoegang is geïnstalleerd, wordt u gevraagd om te controleren van het bestand Leesmij-bestand, dat vereiste basisinstallatie-instructies voor de gateway bevat. Deze installatie-instructies zijn ook in de volgende sectie [Gateway configureren](#configure-the-gateway). Het pad naar het bestand Leesmij is **C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\Leesmij**.

### <a name="configure-the-gateway"></a>De Gateway configureren

De **Install-PswaWebApplication** cmdlet is een snelle manier om Windows PowerShell Web Access is geconfigureerd. Hoewel u de parameter `UseTestCertificate` aan de cmdlet `Install-PswaWebApplication` kunt toevoegen om een zelfondertekend SSL-certificaat voor testdoeleinden te installeren, is dit niet veilig. Voor een veilige productieomgeving moet u altijd een geldig SSL-certificaat gebruiken dat door een certificeringsinstantie (CA) is ondertekend.
Administrators kunnen het testcertificaat vervangen door een ondertekend certificaat naar keuze met behulp van de IIS-beheerconsole.

U kunt Windows PowerShell-webtoegang webtoepassingsconfiguratie door waarop voltooien de `Install-PswaWebApplication` cmdlet of door te voeren op basis van GUI-configuratiestappen in IIS-beheer. De cmdlet installeert standaard de webtoepassing **pswa** (en een groep van toepassingen, **pswa_pool**) in de **standaardwebsite** container, zoals wordt weergegeven in IIS-beheer; als gewenst, kunt u opdracht geven de cmdlet de standaardsitecontainer van de webtoepassing wijzigen. IIS-beheer biedt configuratieopties voor webtoepassingen, zoals opties voor het wijzigen van het poortnummer of het SSL-certificaat (Secure Sockets Layer).

>**![Opmerking over beveiliging](images/securitynote.jpeg) opmerking over beveiliging**
>
>Administrators wordt ten sterkste aangeraden de gateway zodanig te configureren dat gebruik wordt gemaakt van een geldig certificaat dat is ondertekend door een CA.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>De gateway voor Windows PowerShell-webtoegang configureren met een testcertificaat door middel van Install-PswaWebApplication

1. Voer een van de volgende Windows PowerShell-sessie te openen.

    - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk.

    - Windows **Start** scherm, klikt u op **Windows PowerShell**.

2. Typ het volgende en druk vervolgens op **Enter**.

    **Install-PswaWebApplication - UseTestCertificate**

  >**![Opmerking over beveiliging](images/securitynote.jpeg) opmerking over beveiliging**
  >
  >De parameter `UseTestCertificate` mag alleen worden gebruikt in een persoonlijke testomgeving. Voor een veilige productieomgeving raden we u aan een geldig certificaat te gebruiken dat is ondertekend door een CA.

De cmdlet wordt uitgevoerd, installeert de Windows PowerShell Web Access-webtoepassing in de container standaardwebsite. De cmdlet maakt de infrastructuur die vereist zijn voor het uitvoeren van Windows PowerShell Web Access op de standaardwebsite `https://<server_name>/pswa`. Als u de webtoepassing op een andere website wilt installeren, geeft u de websitenaam op door de parameter `WebSiteName` toe te voegen. Als u de naam van de webtoepassing wilt wijzigen (de standaardnaam is `pswa`), voegt u de parameter `WebApplicationName` toe.

De volgende instellingen worden geconfigureerd door de cmdlet uit te voeren. U kunt deze desgewenst handmatig wijzigen in de IIS-beheerconsole.

- Pad: / pswa
- ApplicationPool: pswa_pool
- EnabledProtocols: http
- PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

**Voorbeeld**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

In dit voorbeeld is de resulterende website voor Windows PowerShell-webtoegang https://\<*servernaam*\>/myWebApp.

>**![Opmerking](images/note.jpeg) Opmerking**
>
>U kunt zich pas aanmelden nadat gebruikers toegang tot de website is verleend door autorisatieregels toe te voegen. Zie voor meer informatie [configureren van een beperkende autorisatieregel](#configure-a-restrictive-authorization-rule) en [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>De gateway voor Windows PowerShell-webtoegang configureren met een geldig certificaat door middel van Install-PswaWebApplication en IIS-beheer

1. Voer een van de volgende Windows PowerShell-sessie te openen.

    - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk.

    - Windows **Start** scherm, klikt u op **Windows PowerShell**.

2. Typ het volgende en druk vervolgens op **Enter**.

    **Install-PswaWebApplication**

    De volgende instellingen voor de gateway worden geconfigureerd door de cmdlet uit te voeren.
    U kunt deze desgewenst handmatig wijzigen in de IIS-beheerconsole.
    U kunt ook waarden opgeven voor de parameters `WebsiteName` en `WebApplicationName` van de cmdlet `Install-PswaWebApplication`.

    - Pad: / pswa

    - ApplicationPool: pswa_pool

    - EnabledProtocols: http

    - PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

3. Open de IIS-beheerconsole op een van de volgende manieren.

    - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Op de **extra** menu in Serverbeheer klikt u op **Internet Information Services (IIS) Manager**.

    - Windows **Start** scherm, klikt u op **Serverbeheer**.

4. In het structuurdeelvenster van IIS-beheer, vouw het knooppunt voor de server waarop Windows PowerShell-webtoegang is geïnstalleerd totdat de **Sites** map zichtbaar is. Vouw de **Sites** map.

5. Selecteer de website waarop u de Windows PowerShell Web Access-webtoepassing hebt geïnstalleerd. In de **acties** deelvenster, klikt u op **bindingen**.

6. In de **sitebinding** in het dialoogvenster, klikt u op **toevoegen**.

7. In de **sitebinding toevoegen** het dialoogvenster de **Type** optie **https**.

8. In de **SSL-certificaat** veld, selecteert u uw ondertekend certificaat in de vervolgkeuzelijst. Klik op **OK**. Zie [voor het configureren van een SSL-certificaat in IIS-beheer](#to-configure-an-ssl-certificate-in-iis-Manager) in dit onderwerp voor meer informatie over het verkrijgen van een certificaat.

    De Windows PowerShell Web Access-webtoepassing is nu geconfigureerd voor het gebruik van uw ondertekend SSL-certificaat.

    U kunt Windows PowerShell-webtoegang openen door te openen **https://\<servernaam\>/pswa** in een browservenster.

>**![Opmerking](images/note.jpeg) Opmerking**
>
>U kunt zich pas aanmelden nadat gebruikers toegang tot de website is verleend door autorisatieregels toe te voegen.
>Zie voor meer informatie [configureren van een beperkende autorisatieregel](#configure-a-restrictive-authorization-rule), in dit onderwerp en [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Configureer een beperkende autorisatieregel toevoegen

Nadat Windows PowerShell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, kunnen gebruikers de aanmeldingspagina openen in een browser, maar ze zich niet aanmelden totdat de Windows PowerShell Web Access-beheerder gebruikers toegang expliciet verleent. Windows PowerShell Web Access-toegangsbeheer wordt beheerd met behulp van de set Windows PowerShell-cmdlets in de volgende tabel beschreven. Er is geen vergelijkbare grafische gebruikersinterface voor het toevoegen of beheren van autorisatieregels. Voor meer informatie over Windows PowerShell Web Access cmdlets gedetailleerde, raadpleegt u de cmdlet-naslaginformatie [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md).

Zie voor meer informatie over Windows PowerShell-webtoegang autorisatieregels en beveiliging [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Een beperkende autorisatieregel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

    - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.

    - Windows **Start** scherm, met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als Administrator uitvoeren**.

2. Optionele stap voor het beperken van gebruikerstoegang met behulp van sessieconfiguraties: Controleer of de sessieconfiguraties die u wilt gebruiken in uw eigen regels al bestaan. Als ze nog geen hebt is gemaakt, gebruikt u instructies voor het maken van sessieconfiguraties in [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Typ het volgende en druk vervolgens op **Enter**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Deze autorisatieregel verleent een bepaalde gebruikerstoegang tot een computer op het netwerk waartoe ze gewoonlijk toegang hebben, met toegang tot een bepaalde sessieconfiguratie die is afgestemd op de gebruiker gemiddelde scripting en cmdlet-behoeften.

   In het volgende voorbeeld krijgt een gebruiker met de naam `JSmith` in het domein `Contoso` toegang om de computer `Contoso_214` te beheren en een sessieconfiguratie genaamd `NewAdminsOnly` te gebruiken.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Controleer of dat de regel is gemaakt door de `Get-PswaAuthorizationRule` -cmdlet of `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>`

5. Voorbeeld: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Nadat u een autorisatieregel hebt geconfigureerd, bent u klaar voor geautoriseerde gebruikers zich aanmelden bij de webconsole en beginnen met Windows PowerShell-webtoegang.

## <a name="custom-deployment"></a>Aangepaste implementatie

U kunt de Windows PowerShell Web Access-gateway installeren op een server waarop Windows Server 2012 R2 of Windows Server 2012 met behulp van de functies en onderdelen in Serverbeheer. Nadat u Windows PowerShell-webtoegang is geïnstalleerd, kunt u de configuratie van de gateway in IIS-beheer kunt aanpassen.

### <a name="install-windows-powershell-web-access"></a>Windows PowerShell-webtoegang installeren

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a>Windows PowerShell-webtoegang installeren met behulp van de wizard Functies en onderdelen toevoegen

1. Als Serverbeheer al geopend is, gaat u naar de volgende stap. Als Serverbeheer niet al geopend is, op een van de volgende manieren openen.

    - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows.

    - Windows **Start** scherm, klikt u op **Serverbeheer**.

2. Op de **beheren** menu, klikt u op **functies en onderdelen toevoegen**.

3. Op de **installatietype selecteren** pagina **op basis van functie of onderdeel gebaseerde installatie**. Klik op **Volgende**.

4. Op de **Selecteer doelserver** pagina, selecteer een server uit de servergroep of Selecteer een offline-VHD. Als u een offline-VHD als de doelserver wilt selecteren, kiest u eerst de server waaraan u de VHD wilt koppelen en selecteert u vervolgens het VHD-bestand. Zie de Serverbeheer-Help voor meer informatie over het toevoegen van servers aan uw servergroep. Nadat u de doelserver hebt geselecteerd, klikt u op **volgende**.

5. Op de **functies selecteren** pagina van de wizard, vouw **Windows PowerShell**, en selecteer vervolgens **Windows PowerShell-webtoegang**.

6. U wordt gevraagd vereiste onderdelen toe te voegen, zoals .NET Framework 4.5 en functieservices van Webserver (IIS). Voeg de vereiste onderdelen toe en ga door.

    >**![Opmerking](images/note.jpeg) Opmerking**
    >
    >Windows PowerShell-webtoegang installeren met behulp van de functies en onderdelen installeert ook webserver (IIS), met inbegrip van de module IIS-beheer. Als u de Wizard Functies toevoegen en onderdelen gebruikt worden standaard de invoegtoepassing en andere IIS-beheerprogramma's geïnstalleerd. Als u Windows PowerShell-webtoegang installeren met behulp van Windows PowerShell-cmdlets, zoals beschreven in de volgende procedure, worden standaard geen beheerhulpprogramma's toegevoegd.

7. Op de **installatieselecties bevestigen** als de onderdeelbestanden voor Windows PowerShell Web Access zijn niet opgeslagen op de doelserver die u hebt geselecteerd in stap 4, klikt u op pagina **eenalternatiefbronpadopgeven**, en geef het pad naar de onderdeelbestanden. Klik anders op **installeren**.

8. Nadat u op **installeren**, wordt de **installatievoortgang** pagina Voortgang van de installatie, resultaten en berichten, zoals waarschuwingen, fouten of configuratiestappen zijn na de installatie die worden weergegeven vereist voor Windows PowerShell Web Access. Nadat u Windows PowerShell-webtoegang is geïnstalleerd, wordt u gevraagd om te controleren van het bestand Leesmij-bestand, dat vereiste basisinstallatie-instructies voor de gateway bevat. Deze instructies zijn ook opgenomen in dit onderwerp. Het pad naar het bestand Leesmij is `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>De gateway configureren

Instructies in deze sectie zijn voor het installeren van de Windows PowerShell Web Access-webtoepassing in een submap zijn en niet in de hoofdmap van uw website. Deze procedure is het op de grafische interface gebaseerde equivalent van de acties die door de cmdlet `Install-PswaWebApplication` worden uitgevoerd. Deze sectie bevat ook instructies voor het gebruik van IIS-beheer voor het configureren van de Windows PowerShell Web Access-gateway als primaire website.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>IIS-beheer gebruiken om de gateway te configureren in een bestaande website

1. Open de IIS-beheerconsole op een van de volgende manieren.

    - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Op de **extra** menu in Serverbeheer klikt u op **Internet Information Services (IIS) Manager**.

    - Windows **Start** scherm, typt u een deel van de naam **Internet Information Services (IIS) Manager**. Klik op de snelkoppeling wanneer deze wordt weergegeven de **Apps** resultaten.

2. Maak een nieuwe groep van toepassingen voor Windows PowerShell Web Access. Vouw het knooppunt van de gatewayserver in het structuurdeelvenster van IIS, dat u selecteert **toepassingsgroepen**, en klik op **groep van toepassingen toevoegen** in de **acties** deelvenster.

3. Voeg een nieuwe groep van toepassingen met de naam **pswa_pool**, of geef een andere naam. Klik op **OK**.

4. In het structuurdeelvenster van IIS-beheer, vouw het knooppunt voor de server waarop Windows PowerShell-webtoegang is geïnstalleerd totdat de **Sites** map zichtbaar is. Selecteer de **Sites** map.

5. Met de rechtermuisknop op de website (bijvoorbeeld **standaardwebsite**) op die u wilt toevoegen, de Windows PowerShell Web Access-website en klik vervolgens op **toepassing toevoegen**.

6. In de **Alias** veld, typt u pswa of geef een andere alias. De alias wordt de naam van de virtuele map. Bijvoorbeeld: **pswa** vertegenwoordigt de alias die in deze stap hebt opgegeven in de volgende URL: **https://\<servernaam\>/pswa**.

7. In de **toepassingsgroep** veld, selecteert u de groep van toepassingen die u in stap 3 hebt gemaakt.

8. In de **fysiek pad** veld, blader naar de locatie van de toepassing. U kunt gebruikmaken van de standaardlocatie: %windir%/Web/PowerShellWebAccess/wwwroot. Klik op **OK**.

9. Volg de stappen in de procedure voor het configureren van een SSL-certificaat in IIS manager](#to-configure-an-ssl-certificate-in-iis-Manager) in dit onderwerp.

10. ![](images/SecurityNote.jpeg) Optionele beveiligingsstap:

    Met de website in het deelvenster voor structuurweergave is geselecteerd, dubbelklikt u op **SSL-instellingen** in het inhoudsvenster.
Selecteer **SSL vereisen**, en klik vervolgens in de **acties** deelvenster, klikt u op **toepassen**.
Typ in het **SSL-instellingen** deelvenster kunt u vereisen dat gebruikers verbinding maken met de Windows PowerShell Web Access-website over clientcertificaten beschikken. Aan de hand van een clientcertificaat kan de identiteit van de gebruiker van een clientapparaat worden geverifieerd.
Zie voor meer informatie over hoe clientcertificaten de beveiliging van Windows PowerShell Web Access kan verbeteren, [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md) in deze handleiding.

11. Open een browsersessie op een clientapparaat. Zie voor meer informatie over ondersteunde browsers en apparaten, [Browser en clientapparaat ondersteunen](#browser-and-client-device-support) in dit onderwerp.

12. Open de nieuwe Windows PowerShell Web Access-website **https://\<*gateway servernaam*\>/pswa**.

    De Windows PowerShell Web Access-console aanmeldingspagina moet worden weergegeven in de browser.

    >**![Opmerking](images/note.jpeg) Opmerking**
    >
    >U kunt zich pas aanmelden nadat gebruikers toegang tot de website is verleend door autorisatieregels toe te voegen.
    >Zie voor meer informatie [configureren van een beperkende autorisatieregel](#configure-a-restrictive-authorization-rule), in dit onderwerp en [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. In een Windows PowerShell-sessie die is geopend met verhoogde gebruikersrechten (als Administrator uitvoeren) voert u het volgende script waarin *application_pool_name* vertegenwoordigt de naam van de groep van toepassingen die u hebt gemaakt in stap 3 de groep van toepassingen om toegangsrechten te geven tot het autorisatiebestand.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Voer de volgende opdracht uit om de bestaande toegangsrechten voor het autorisatiebestand weer te geven:

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>IIS-beheer gebruiken om de gateway te configureren als een primaire website met een testcertificaat

1. Open de IIS-beheerconsole op een van de volgende manieren.

    - Start op het bureaublad van Windows Server Manager door te klikken op **Serverbeheer** in de taakbalk van Windows. Op de **extra** menu in Serverbeheer klikt u op **Internet Information Services (IIS) Manager**.

    - Windows **Start** scherm, typt u een deel van de naam **Internet Information Services (IIS) Manager**. Klik op de snelkoppeling wanneer deze wordt weergegeven de **Apps** resultaten.

2. In het structuurdeelvenster van IIS-beheer, vouw het knooppunt voor de server waarop Windows PowerShell-webtoegang is geïnstalleerd totdat de **Sites** map zichtbaar is. Selecteer de **Sites** map.

3. In de **acties** deelvenster, klikt u op **Website toevoegen**.

4. Typ een naam voor de website, zoals **Windows PowerShell-webtoegang**.

5. Er wordt automatisch een groep toepassingen gemaakt voor de nieuwe website. Met een andere groep van toepassingen, klikt u op **Selecteer** selecteren van een groep van toepassingen om te koppelen aan de nieuwe website. Selecteer de alternatieve groep toepassingen in de **groep van toepassingen selecteren** in het dialoogvenster en klik vervolgens op **OK**.

6. In de **fysiek pad** tekst Ga naar %*windir*% / Web/PowerShellWebAccess/wwwroot.

7. In de **Type** veld van de **Binding** gebied, selecteer **https**.

8. Wijs aan de website een poortnummer toe dat nog niet wordt gebruikt door een andere site of toepassing. U kunt openstaande poorten vinden, uitvoeren de **netstat** opdracht in een opdrachtpromptvenster. Het standaardpoortnummer is 443.

    Wijzig de standaardpoort als een andere website al gebruikmaakt van nummer 443 of als u andere veiligheidsredenen hebt om het poortnummer te wijzigen. Als een andere website die wordt uitgevoerd op de gatewayserver van de geselecteerde poort gebruikmaakt, een waarschuwing wordt weergegeven wanneer u klikt op **OK** in de **Website toevoegen** in het dialoogvenster. U moet een niet-gebruikte poort gebruiken om uit te voeren van Windows PowerShell Web Access.

9. Indien nodig voor uw organisatie, Geef eventueel een hostnaam die zinvol is voor uw organisatie en gebruikers, zoals **www.contoso.com**. Klik op **OK**.

10. Voor een veiliger productieomgeving raden we u ten sterkste aan een geldig certificaat op te geven dat is ondertekend door een CA. Omdat gebruikers alleen verbinding met Windows PowerShell-internettoegang via een HTTPS-website maken kunnen, moet u een SSL-certificaat opgeven. Zie [voor het configureren van een SSL-certificaat in IIS-beheer](#to-configure-an-ssl-certificate-in-iis-Manager) in dit onderwerp voor meer informatie over het verkrijgen van een certificaat.

11. Klik op **OK** sluiten de **Website toevoegen** in het dialoogvenster.

12. In een Windows PowerShell-sessie die is geopend met verhoogde gebruikersrechten (als Administrator uitvoeren) voert u het volgende script waarin *application_pool_name* vertegenwoordigt de naam van de groep van toepassingen die u hebt gemaakt in stap 4. de groep van toepassingen om toegangsrechten te geven tot het autorisatiebestand.

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Voer de volgende opdracht uit om de bestaande toegangsrechten voor het autorisatiebestand weer te geven:

        c:\windows\system32\icacls.exe $authorizationFile

13. Met de nieuwe website in het structuurdeelvenster van IIS-beheer zijn geselecteerd, klikt u op **Start** in de **acties** deelvenster starten van de website.

14. Open een browsersessie op een clientapparaat. Zie voor meer informatie over ondersteunde browsers en apparaten, [Browser en clientapparaat ondersteunen](#browser-and-client-device-support) in dit document.

15. Open de nieuwe Windows PowerShell Web Access-website.

    Omdat de primaire website naar de map Windows PowerShell-webtoegang verwijst, de aanmeldingspagina van Windows PowerShell-webtoegang in de browser moet worden weergegeven wanneer u opent **https://\<*gateway_server_name* \>**. U hoeft niet om toe te voegen **/pswa** naar de URL.

    >**![Opmerking](images/note.jpeg) Opmerking**
    >
    >U kunt zich pas aanmelden nadat gebruikers toegang tot de website is verleend door autorisatieregels toe te voegen.
    >Zie voor meer informatie [configureren van een beperkende autorisatieregel](#configure-a-restrictive-authorization-rule), in dit onderwerp en [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Configureer een beperkende autorisatieregel toevoegen

Nadat Windows PowerShell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, kunnen gebruikers de aanmeldingspagina openen in een browser, maar ze zich niet aanmelden totdat de Windows PowerShell Web Access-beheerder gebruikers toegang expliciet verleent. Windows PowerShell Web Access-toegangsbeheer wordt beheerd met behulp van de set Windows PowerShell-cmdlets in de volgende tabel beschreven. Er is geen vergelijkbare grafische gebruikersinterface voor het toevoegen of beheren van autorisatieregels. Voor meer informatie over Windows PowerShell Web Access cmdlets gedetailleerde, raadpleegt u de cmdlet-naslaginformatie [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md).

Zie voor meer informatie over Windows PowerShell-webtoegang autorisatieregels en beveiliging [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Een beperkende autorisatieregel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

    - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.

    - Windows **Start** scherm, met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als Administrator uitvoeren**.

2. ![Opmerking over beveiliging](images/SecurityNote.jpeg) Optionele stap voor het beperken van gebruikerstoegang met behulp van sessieconfiguraties:

    Controleer of de sessieconfiguraties die u in uw regels wilt gebruiken al bestaan. Als ze nog geen hebt is gemaakt, gebruikt u instructies voor het maken van sessieconfiguraties in [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Typ het volgende en druk vervolgens op **Enter**.

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Deze autorisatieregel verleent een bepaalde gebruikerstoegang tot een computer op het netwerk waartoe ze gewoonlijk toegang hebben, met toegang tot een bepaalde sessieconfiguratie die is afgestemd op de gebruiker '™ s typische scripting- en cmdlet-behoeften.

    In het volgende voorbeeld krijgt een gebruiker met de naam `JSmith` in het domein `Contoso` toegang om de computer `Contoso_214` te beheren en een sessieconfiguratie genaamd `NewAdminsOnly` te gebruiken.

        Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4. Controleer of dat de regel is gemaakt door de `Get-PswaAuthorizationRule` -cmdlet of `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>`.

    Voorbeeld: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Nadat u een autorisatieregel hebt geconfigureerd, bent u klaar voor geautoriseerde gebruikers zich aanmelden bij de webconsole en beginnen met Windows PowerShell-webtoegang.

## <a name="configure-a-genuine-certificate"></a>Een legitiem certificaat configureren

Gebruik voor een veilige productieomgeving altijd een geldig SSL-certificaat dat is ondertekend door een certificeringsinstantie (CA). De procedure in deze sectie beschrijft hoe u een geldig SSL-certificaat van een CA kunt verkrijgen en toepassen.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Een SSL-certificaat configureren in IIS-beheer

1. Selecteer de server waarop Windows PowerShell-webtoegang is geïnstalleerd in het structuurdeelvenster van IIS-beheer.

2. In het inhoudsvenster dubbelklikken **servercertificaten**.

3. In de **acties** deelvenster, een van de volgende handelingen uit. Zie voor meer informatie over het configureren van servercertificaten in IIS [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).

    - Klik op **importeren** een bestaand en geldig certificaat importeren vanaf een locatie op uw netwerk.

    - Klik op **certificaataanvraag maken** , zoals een certificaat aanvragen bij een Certificeringsinstantie [VeriSign](http://www.verisign.com/), [Thawte](https://www.thawte.com/), of [GeoTrust](https://www.geotrust.com/). De algemene naam van het certificaat moet overeenkomen met de host-header in de aanvraag.

      Bijvoorbeeld, als de clientbrowser aanvragen http://www.contoso.com/, moet de algemene naam ook http://www.contoso.com/. Dit is de veiligste en aanbevolen optie voor het ontwikkelen van de Windows PowerShell Web Access-gateway met een certificaat.

    - Klik op **een zelfondertekend certificaat maken** voor het maken van een certificaat dat u direct gebruiken kunt en later door een CA hebt ondertekend indien gewenst. Geef een beschrijvende naam voor het zelfondertekend certificaat, zoals **Windows PowerShell-webtoegang**. Deze optie wordt niet als veilig beschouwd en wordt alleen aanbevolen voor een persoonlijke testomgeving.

4. Na het maken of een certificaat aanvragen, selecteert u de website waarop het certificaat wordt toegepast (bijvoorbeeld **standaardwebsite**) in de IIS-beheer in het deelvenster met de boomstructuur en klik vervolgens op **bindingen** in de **Acties** deelvenster.

5. In de **sitebinding toevoegen** dialoogvenster Voeg een **https** binding voor de site als een nog niet wordt weergegeven. Als u geen zelfondertekend certificaat gebruikt, geeft u de hostnaam op uit stap 3 van deze procedure. Als u een zelfondertekend certificaat gebruikt, is deze stap niet vereist.

6. Selecteer het certificaat dat u hebt gemaakt in stap 3 van deze procedure of verkregen en klik vervolgens op **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>De Windows PowerShell-webconsole gebruiken

Nadat u Windows PowerShell-webtoegang is geïnstalleerd en de gateway-configuratie is voltooid zoals beschreven in dit onderwerp, is de Windows PowerShell-webconsole klaar voor gebruik. Zie voor meer informatie over het ophalen van in de webconsole gestart, [via de Console Windows PowerShell Web gebaseerde](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Zie ook

- [Internet informatieservices (IIS) 7.0 documentatie](https://technet.microsoft.com/library/cc753433.aspx)
- [IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)
- [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
- [IPsec Deployment Resources](https://technet.microsoft.com/network/bb531150)