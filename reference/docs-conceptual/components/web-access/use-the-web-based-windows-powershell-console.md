---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: de website op basis van windows powershell-console gebruiken
ms.openlocfilehash: 2bb9c6ef486ef32012a15f9890997cf2fa6a3a0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086634"
---
# <a name="use-the-web-based-windows-powershell-console"></a>De webgebaseerde Windows PowerShell-Console gebruiken

Bijgewerkt: 24: juni 2013

Van toepassing op: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web Access kunnen gebruikers zich aanmelden met een beveiligde website. Als u wilt gebruiken Windows PowerShell-sessies, cmdlets en scripts voor het beheren van een externe computer.

Omdat de Windows PowerShell-console wordt uitgevoerd in een webbrowser, kan deze worden geopend vanaf diverse clientapparaten; bijna alle apparaten met een webbrowser werken.

De webgebaseerde Windows PowerShell-console is gericht op een externe computer die is opgegeven door gebruikers als onderdeel van het aanmeldingsproces.

In dit onderwerp wordt beschreven hoe u zich aanmeldt bij en start met behulp van de Windows PowerShell-webtoegang op basis van een web-console.

In dit onderwerp wordt niet beschreven hoe u Windows PowerShell gebruiken of cmdlets of scripts worden uitgevoerd.
Zie voor meer informatie over het gebruik van Windows PowerShell en scripting resources de [Zie ook](#see-also) sectie aan het einde van dit onderwerp.

## <a name="supported-browsers-and-client-devices"></a>Ondersteunde browsers en clientapparaten

Windows PowerShell-webtoegang biedt ondersteuning voor de volgende internetbrowsers.
Hoewel mobiele browsers officieel niet worden ondersteund, is het mogelijk dat veel kunnen worden uitgevoerd van de website op basis van Windows PowerShell-console.
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

## <a name="signing-in-to-windows-powershell-web-access"></a>Aanmelden bij Windows PowerShell-internettoegang

De Windows PowerShell Web Access-beheerder moet u voorzien van een URL die is het adres van uw website organisaties Windows PowerShell Web Access-gateway.
Standaard is dit websiteadres *https://\<servernaam\>/pswa*.

Voordat u zich bij Windows PowerShell-webtoegang aanmelden, moet u dat u hebt de naam of IP-adres van de externe computer die u wilt beheren.
U moet een geautoriseerde gebruiker op de externe computer en deze moet worden geconfigureerd voor het toestaan van extern beheer.
Zie voor meer informatie over het configureren van uw computer zodat extern beheer [Enable and Use Remote Commands in Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting).

De eenvoudigste methode van het configureren van uw computer zodat extern beheer is om uit te voeren de **Enable-PSRemoting - force** cmdlet op de computer, in een Windows PowerShell-sessie die is geopend met verhoogde gebruikersrechten (**Als Administrator uitvoeren**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Aanmelden bij Windows PowerShell-webtoegang

1. Open de website van Windows PowerShell-webtoegang in een browservenster of tabblad.

1. Geef op de Windows PowerShell-webtoegang aanmelden pagina uw netwerk-gebruikersnaam, wachtwoord en de naam van de computer die u wilt beheren (en op waarvan u een geautoriseerde gebruiker bent). Als de Windows PowerShell Web Access-beheerder heeft u een URI met een aangepaste site of proxyserver gebruiken in plaats van een computernaam gevraagd, selecteert u **verbindings-URI** in de **verbindingstype** veld, en vervolgens Hiermee geeft u de URI.

    > ![Houd er rekening mee](images/Note.jpeg) **Opmerking**:
    >
    > - Als de doelcomputer zich in een werkgroep, gebruikt u de volgende syntaxis om te bieden uw gebruikersnaam en meld u aan bij de computer: `<workgroup_name>\<user_name>`
    > - Als de doelcomputer de gatewayserver is, kunt u opgeven `localhost` in het veld Computer
    > - Als de doelcomputer de gatewayserver is en de gatewayserver zich in een werkgroep bevindt, moet u `<workgroup name>\<user_name>` in de naam van de gebruiker opgeslagen. U kunt `localhost` in het veld Computer.

1. De **optionele verbindingsinstellingen** sectie heeft betrekking op de autorisatievereisten van de externe computer die u wilt beheren. Zie voor meer informatie over de parameters die equivalent aan de optionele instellingen zijn, de [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession) help van de cmdlet.

    De referenties die u gebruiken om door te geven via de Windows PowerShell Web Access-gateway zijn meestal hetzelfde die worden herkend door de externe computer die u wilt beheren. Echter, als u wilt gebruiken van andere referenties voor het beheren van de externe computer die u hebt opgegeven in stap 2 uit, vouw de **optionele verbindingsinstellingen** uit en geef de alternatieve referenties. Anders gaat u naar stap 6.

1. Als de Windows PowerShell Web Access-beheerder heeft gemaakt van een aangepaste sessieconfiguratie voor gebruikers van Windows PowerShell-webtoegang, typ de naam van de naam van de sessie-configuratie in de **configuratienaam** veld. Zie voor meer informatie over sessieconfiguraties [about_Session_Configurations](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Houd de **verificatietype** ingesteld op **standaard** , tenzij u anders doen door de Windows PowerShell Web Access-beheerder hebt gekregen.

1. Klik op **aanmelden**.

## <a name="signing-out-and-timing-out"></a>Afmelden en time-outs

Een van de volgende meldt u zich buiten een website op basis van Windows PowerShell-sessie.

- Te klikken op **Afmelden** in de rechterbenedenhoek van de console. (Alleen WindowsServer 2012)

- Te klikken op **opslaan** of **afsluiten** in de rechterbenedenhoek van de console (alleen Windows Server 2012 R2). Te klikken op **opslaan** opslaan en sluiten van de sessie van uw Windows PowerShell-webtoegang; u kunt verbinding maken met de sessie later opnieuw. Wanneer u opnieuw bij Windows PowerShell-webtoegang aanmelden, geeft Windows PowerShell-webtoegang een lijst van uw opgeslagen sessies. u kunt selecteren en opnieuw verbinding maken met een opgeslagen sessie of een nieuwe sessie starten. Het maximum aantal actieve sessies gebruikers zijn toegestaan, zowel opgeslagen als actief is, wordt geconfigureerd met de gatewaybeheerder.

    Te klikken op **afsluiten** u zich af bij de Windows PowerShell Web Access-sessie zonder op te slaan.

- Er wordt geprobeerd aan te melden voor het beheren van een andere externe computer in dezelfde browsersessie of in een nieuw tabblad van dezelfde browsersessie. (Dit is niet van toepassing als de gateway-server wordt uitgevoerd Windows Server 2012 R2; Windows PowerShell-webtoegang die worden uitgevoerd op Windows Server 2012 R2 staat toe dat meerdere sessies op nieuwe tabbladen in dezelfde browsersessie.) Zie voor meer informatie over het gebruik van meer dan één actieve sessies op dezelfde computer verbinding maken met meerdere doelcomputers tegelijkertijd in de [beperkingen van de webconsole](#limitations-of-the-web-based-console) sectie van dit onderwerp.

- twintig minuten van inactiviteit in de sessie. De gatewaybeheerder kan de time-outperiode voor inactiviteit; aanpassen Zie voor meer informatie, [sessiebeheer](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Als u een sessie in de webconsole zijn verbroken vanwege een netwerkfout of andere niet-gepland afsluiten of de fout, en niet omdat u de sessie hebt gesloten verbonden zelf, de Windows PowerShell-webtoegang sessie blijft om uit te voeren, met het doel computer, totdat de time-outperiode op de client-side-systeem. Standaard deze time-outperiode is 20 minuten, en wordt geconfigureerd door de gatewaybeheerder. De sessie wordt beëindigd na de standaardwaarde 20 minuten of na de time-outperiode is opgegeven door de gatewaybeheerder van de, afhankelijk van welke periode korter is.

        Als de gateway-server wordt uitgevoerd Windows Server 2012 R2, Windows PowerShell Web Access kunnen gebruikers opnieuw verbinding maken met opgeslagen sessies op een later tijdstip, maar u niet kunt zien of opnieuw verbinding maken met opgeslagen sessies pas na de time-outperiode die is opgegeven door de beheerder heeft verlopen.

- Sluit het browservenster of tabblad.

- Het uitschakelen van de client-apparaat waarop de browser wordt uitgevoerd, of vanaf het netwerk verbinding te verbreken.

- Met de **afsluiten** opdracht in de web-console. Met deze opdracht werkt niet als de sessieconfiguratie waarmee u met verbonden bent is geconfigureerd voor ondersteuning van [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) modus, of bevindt zich in een beperkte runspace.

Als u opnieuw aan te melden wilt, opent u de Windows PowerShell-webtoegang webpagina opnieuw en meld u aan met de volgende stappen in [aanmelden bij Windows PowerShell-webtoegang](#signing-in-to-windows-powershell-web-access) in dit onderwerp.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Verschillen in de Windows PowerShell web gebaseerde console

Na de aanmelding bij Windows PowerShell-internettoegang, is een webgebaseerde Windows PowerShell-console wordt geopend in het browservenster of tabblad. Omdat de-console is verbonden met de externe computer die u hebt opgegeven tijdens het aanmelden, kunnen alleen de Windows PowerShell-cmdlets of scripts die beschikbaar op de externe computer zijn worden gebruikt in de console. Deze sectie wordt beschreven andere beperkingen van Windows PowerShell-webtoegang consoles en verschillen tussen Windows PowerShell-webtoegang consoles en de geïnstalleerde **PowerShell.exe** console.

### <a name="functional-disparity-with-powershellexe"></a>Functionele verschillen met PowerShell.exe

Het merendeel van de Windows PowerShell-Hostfunctionaliteit is beschikbaar in de Windows PowerShell-webtoegang op basis van een web-console, maar er zijn enkele functies die niet beschikbaar.

- Geneste voortgang wordt weergegeven.

  Windows PowerShell-webtoegang geeft een Voortgangs-GUI voor cmdlets weer dat rapport wordt uitgevoerd, maar alleen gegevens over de voortgang op het hoogste niveau wordt weergegeven.

- Invoerkleur.

  De invoerkleur (zowel de voorgrond en achtergrond) kan niet worden gewijzigd. De stijl van uitvoer, waarschuwingen, uitgebreide en foutberichten kan worden gewijzigd door een script is uitgevoerd.

- PSHostRawUserInterface.

  Windows PowerShell-webtoegang is geïmplementeerd via Extern beheer van Windows PowerShell en maakt gebruik van een externe runspace. Windows PowerShell-webtoegang implementeert sommige methoden niet in deze interface; bijvoorbeeld, alle opdrachten die worden geschreven naar de Windows-console. Opdrachten, zoals **PowerTab** werken niet in Windows PowerShell-webtoegang.

- Functietoetsen.

  Windows PowerShell-webtoegang biedt geen ondersteuning voor bepaalde functietoetsen in veel gevallen omdat de opdrachten zijn gereserveerd door de browser.

### <a name="unsupported-shortcut-keys"></a>Niet-ondersteunde sneltoetsen

Functietoets | Actie
-- | --
Ctrl+C | In Windows PowerShell-webtoegang, **Ctrl + C** wordt gebruikt door de browser om inhoud te kopiëren. De console bevat een **annuleren** knop gebruikers kunnen ook worden gebruikt en **Ctrl + Q** opdrachten annuleren.
ALT + SPATIEBALK, e, l | Blader door de schermbuffer
ALT + SPATIEBALK, e, f | Zoeken naar tekst in de schermbuffer
ALT + SPATIEBALK, e, k | Selecteer tekst die moet worden gekopieerd uit de schermbuffer
ALT + SPATIEBALK, e, p | Plak de inhoud van Klembord in de Windows PowerShell-console
ALT + SPATIEBALK, c | Sluit de Windows PowerShell-console
Ctrl+Break | Afdwingen dat de Windows PowerShell-venster te sluiten
Ctrl+Home | Hiermee verwijdert u vanaf het begin van de huidige opdrachtregel
Ctrl+End | Verwijderen tot het einde van de opdrachtregel
F1 | De cursor één teken naar rechts verplaatsen op de opdrachtregel
F2 | Een nieuwe opdracht maken door te kopiëren van de laatste opdracht, tot aan het teken dat u typt
F3 | De opdrachtregel met inhoud van de laatste opdrachtregel vullen
F4 | Tekens verwijderen vanaf de cursorpositie
F5 | Achterwaarts door de opdrachtgeschiedenis scannen. Voor toegang tot de opdrachten in de opdrachtgeschiedenis in Windows PowerShell-webtoegang, klikt u op de **geschiedenis** schuifknoppen in de webconsole.
F7 | Interactief een opdracht in de opdrachtgeschiedenis selecteren
F8 | Scanoverzicht opdrachten die overeenkomen met de huidige tekst weergeven
F9 | Een specifieke genummerde opdracht van de geschiedenis uitvoeren
Page Up | De eerste opdracht in de geschiedenis uitvoeren
Page Down | De laatste opdracht in de geschiedenis uitvoeren
Alt+F7 | De opdrachtgeschiedenislijst wissen

### <a name="limitations-of-the-web-based-console"></a>Beperkingen van de webconsole

- Dubbele-hopbeperking

    De dubbele-hopbeperking (of het maken van verbinding met een tweede computer vanaf de eerste verbinding) kan optreden als u probeert te maken of een nieuwe sessie werken met behulp van Windows PowerShell-webtoegang hieraan. Windows PowerShell-webtoegang maakt gebruik van een externe runspace en op dit moment **PowerShell.exe** biedt geen ondersteuning voor het tot stand brengen van een externe verbinding met een tweede computer vanuit een externe runspace. Als u probeert verbinding maken met een tweede externe computer via een bestaande verbinding met behulp van de **Enter-PSSession** cmdlet, bijvoorbeeld, u kunt er diverse fouten optreden, zoals €œCannot netwerkbronnen ophalen.

    Dubbele-hopbeperking om fouten te voorkomen, moet de beheerder CredSSP-verificatie configureren in uw netwerkomgeving organisaties. Zie voor meer informatie over het configureren van CredSSP-authenticatie [CredSSP for second-hop remoting](https://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) op de website van Microsoft. U kunt ook expliciete referenties opgeven wanneer u wilt beheren een tweede externe computer. om toe te staan van de tweede hop waarschijnlijk geen impliciete referenties.

- Externe toegang

    Windows PowerShell-webtoegang gebruikt en heeft dezelfde beperkingen als een externe Windows PowerShell-sessie. Opdrachten die rechtstreeks aanroepen van Windows-console-API's, zoals die voor console-editors of tekstmenuprogramma programma's, werken niet omdat de opdrachten niet lezen of naar de standaard invoer, uitvoer en -foutpipes schrijven. Daarom opdrachten die een uitvoerbaar bestand starten het bestand, zoals **notepad.exe**, of een GUI, zoals wordt weergegeven `OpenGridView` of `ogv`, werken niet. Uw ervaring wordt beïnvloed door dit gedrag; voor u verschijnt deze Windows PowerShell-webtoegang reageert niet op uw opdracht.

- Tab-aanvulling

    Tab-Aanvulling werkt niet in een sessieconfiguratie met een beperkte runspace of een die zich in **NoLanguage** modus. Hoewel beheerders dat een sessie configureren kunnen ter ondersteuning van tab-aanvulling, wordt het afgeraden uit veiligheidsoverwegingen, omdat de volgende informatie voor onbevoegde gebruikers kan worden weergegeven.

    - Interne bestandssysteempaden

    - Gedeelde mappen op interne computers

    - Variabelen in de runspace

    - Geladen typen of.NET Framework-naamruimten

    - Omgevingsvariabelen

- **NoLanguage** sessie of een beperkte runspace

    Gebruikers die zijn aangemeld bij een **NoLanguage** sessieconfiguratie of een beperkte runspace in Windows PowerShell-webtoegang kan niet worden uitgevoerd de **afsluiten** opdracht om de sessie te beëindigen. Als u wilt afmelden, moeten gebruikers klikken op **Afmelden** op de pagina van de console.

- Verbinding maken met meerdere doelcomputers tegelijk.

    Als de gateway-server wordt uitgevoerd Windows Server 2012, kan Windows PowerShell-webtoegang slechts één externe computerverbinding per browsersessie Deze staat niet toe dat gebruikers zich één keer aanmelden en verbinding maken met meerdere externe computers via afzonderlijke browsertabbladen. Wanneer u een nieuw tabblad of browservenster opent, Windows PowerShell Web Access wordt u gevraagd naar uw huidige sessie verbreken en een nieuwe sessie starten zodat u verbinding met de nieuwe (of dezelfde maken kunt) externe computer. Als twee of meer afzonderlijke sessies op verschillende externe computers zijn gewenst is, maar een functie in Internet Explorer kunt u een nieuwe sessie maken. Voor het starten van een nieuwe browsersessie in Internet Explorer, drukt u op **ALT**, open de **bestand** menu en selecteer vervolgens **nieuwe sessie**. Vervolgens opent u de website van Windows PowerShell-webtoegang in de nieuwe sessie en meld u aan voor toegang tot een andere externe computer.

    Wanneer de Windows PowerShell Web Access-gateway op Windows Server 2012 R2 wordt uitgevoerd, kunnen gebruikers meerdere verbindingen met externe computers op verschillende browsertabbladen openen. Als u meer dan één verbinding met een externe computer openen wilt via het web gebaseerde Windows PowerShell-console, neem contact op met uw Windows PowerShell Web Access-gateway-beheerder om te controleren of deze functie wordt ondersteund door de gatewayserver.

- Permanente Windows PowerShell-sessies (opnieuw verbinding maken).

    Nadat u time-out van de Windows PowerShell Web Access-gateway, is de externe verbinding tussen de gateway en de doelcomputer gesloten. Deze stopt cmdlets of scripts die zich momenteel in het proces. U wordt aangeraden het gebruik van Windows PowerShell **-taak** infrastructuur bij het uitvoeren van langlopende taken, zodat u kunt taken starten, van de computer verbreken later opnieuw verbinding te maken en taken kunt blijven uitvoeren. Een ander voordeel van het gebruik van **-taak** cmdlets is dat u kunt beginnen met behulp van Windows PowerShell-webtoegang, meld u af en later opnieuw door actieve Windows PowerShell Web Access of een andere host (zoals Windows PowerShell Integrated Scripting Environment (ISE)).

- Consoleformaat wijzigen.

    De **PowerShell.exe** consolevenster kunt in de volgende drie manieren worden gewijzigd.

    - Sleep en pas de grootte van de console-venster met een muis

    - De hoogte en breedte-eigenschappen wijzigen met behulp van een GUI voor console-eigenschappen

    - Wijzigen van de hoogte en breedte van consolevensters met een cmdlet

        Het consolevenster voor Windows PowerShell-webtoegang kan worden geconfigureerd met behulp van de cmdlets als volgt. In het volgende voorbeeld wordt een gebruiker de breedte van console Windows PowerShell-webtoegang **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        U kunt de hoogte van de console op een vergelijkbare manier wijzigen.

        Meer voorbeelden voor het aanpassen van de consoleweergave zijn beschikbaar in de [Windows PowerShell-teamblog](https://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Zie ook

- [Naslaginformatie over Windows PowerShell-cmdlets](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Windows PowerShell op Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
- [TechNet Script Center Repository](https://gallery.technet.microsoft.com/scriptcenter)
- [Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
- [Windows PowerShell-teamblog](https://blogs.msdn.com/b/powershell/)