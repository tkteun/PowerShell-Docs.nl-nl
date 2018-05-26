---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: de website op basis van windows powershell-console gebruiken
ms.openlocfilehash: 5d29a6f97fddf4b329fcc7097cf7d40d47d22cca
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/25/2018
---
# <a name="use-the-web-based-windows-powershell-console"></a>De webconsole voor Windows PowerShell gebruiken

Bijgewerkte: 24 juni 2013

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

Windows PowerShell Web Access kunnen gebruikers zich aanmelden bij een beveiligde website; Als u wilt gebruiken Windows PowerShell-sessies, -cmdlets en -scripts voor het beheren van een externe computer.

Omdat de Windows PowerShell-console wordt uitgevoerd in een webbrowser, kan worden geopend vanaf een groot aantal clientapparaten; bijna alle apparaten met een webbrowser werken.

Het web gebaseerde Windows PowerShell-console is gericht op een externe computer die is opgegeven door gebruikers als onderdeel van het proces aanmelden.

Dit onderwerp wordt beschreven hoe u zich aanmeldt bij en aan de slag met de webconsole voor Windows PowerShell Web Access.

In dit onderwerp wordt niet beschreven hoe u Windows PowerShell gebruiken of cmdlets of scripts worden uitgevoerd.
Zie voor meer informatie over het gebruik van Windows PowerShell en scripting resources de [Zie ook](#see-also) sectie aan het einde van dit onderwerp.

## <a name="supported-browsers-and-client-devices"></a>Ondersteunde browsers en clientapparaten

Windows PowerShell-webtoegang ondersteunt de volgende internetbrowsers.
Hoewel mobiele browsers officieel niet worden ondersteund, is het mogelijk dat veel kunnen worden uitgevoerd van het web gebaseerde Windows PowerShell-console.
Andere browsers die cookies accepteren en waarop JavaScript en HTTPS-websites kunnen worden uitgevoerd, werken waarschijnlijk wel, maar zijn niet officieel getest.

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

## <a name="signing-in-to-windows-powershell-web-access"></a>Aanmelden bij Windows PowerShell-internettoegang

De Windows PowerShell Web Access-beheerder moet u voorzien van een URL die is het adres van uw website organisaties Windows PowerShell Web Access-gateway.
Dit websiteadres is standaard *https://\<servernaam\>/pswa*.

Voordat u zich aanmeldt bij Windows PowerShell-webtoegang, moet u dat u hebt de naam of IP-adres van de externe computer die u wilt beheren.
U moet een geautoriseerde gebruiker zijn op de externe computer en deze moet zo zijn geconfigureerd dat extern beheer is toegestaan.
Zie voor meer informatie over het configureren van uw computer voor extern beheer toestaan [Enable and Use Remote Commands in Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting).

De eenvoudigste methode van de configuratie van de computer zodat extern beheer is het uitvoeren van de **Enable-PSRemoting - force** cmdlet uit op de computer, in een Windows PowerShell-sessie die is geopend met verhoogde gebruikersrechten (**Als Administrator uitvoeren**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Aanmelden bij Windows PowerShell-internettoegang

1. Open de Windows PowerShell Web Access-website in een browservenster of tabblad.

1. Geef op de pagina Windows PowerShell Web Access-in uw netwerk-gebruikersnaam, wachtwoord en de naam van de computer die u wilt beheren (en op waarvan u een geautoriseerde gebruiker bent). Als de Windows PowerShell Web Access-beheerder laten dat u een URI naar een aangepaste site of een proxyserver gebruiken in plaats van een computernaam weten heeft, selecteert u **verbindings-URI** in de **verbindingstype** veld en vervolgens Hiermee geeft u de URI.

    > ![Opmerking](images/Note.jpeg) **Opmerking**:
    >
    > - Als de doelcomputer zich in een werkgroep, gebruikt u de volgende syntaxis om te bieden uw gebruikersnaam en meld u bij de computer: `<workgroup_name>\<user_name>`
    > - Als de doelcomputer de gatewayserver is, kunt u `localhost` in het veld voor de Computer
    > - Als de doelcomputer de gatewayserver is en de gatewayserver zich in een werkgroep, moet u `<workgroup name>\<user_name>` opgeslagen in de gebruikersnaam van de. U kunt `localhost` in het veld voor de Computer.

1. De **optionele verbindingsinstellingen** sectie heeft betrekking op de autorisatievereisten van de externe computer die u wilt beheren. Zie voor meer informatie over de parameters die equivalent aan optionele verbindingsinstellingen zijn de [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession) help van cmdlet.

    De gebruikte referenties om door te geven via de Windows PowerShell Web Access-gateway zijn meestal hetzelfde die worden herkend door de externe computer die u wilt beheren. Als u verschillende referenties gebruikt voor het beheren van de externe computer die u hebt opgegeven in stap 2, vouw de **optionele verbindingsinstellingen** sectie en de alternatieve referenties opgeven. Ga anders verder met stap 6.

1. Als de Windows PowerShell Web Access-beheerder een aangepaste sessieconfiguratie voor gebruikers van Windows PowerShell-webtoegang gemaakt heeft, typ de naam van de naam van de sessie-configuratie in de **configuratienaam** veld. Zie voor meer informatie over sessieconfiguraties [about_Session_Configurations](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Houd de **verificatietype** ingesteld op **standaard** tenzij u iets anders door de Windows PowerShell Web Access-beheerder hebt gekregen.

1. Klik op **aanmelden**.

## <a name="signing-out-and-timing-out"></a>Afmelden en time-outs

Het volgende wordt u afgemeld bij een webgebaseerde Windows PowerShell-sessie.

- Te klikken op **Afmelden** in de rechterbenedenhoek van de console. (Alleen WindowsServer 2012)

- Te klikken op **opslaan** of **afsluiten** in de rechterbenedenhoek van de console (alleen Windows Server 2012 R2). Te klikken op **opslaan** opslaan en sluiten van de Windows PowerShell Web Access-sessie; u kunt de verbinding met de sessie later. Wanneer u opnieuw aan te bij Windows PowerShell-internettoegang melden, geeft Windows PowerShell-webtoegang een lijst met uw opgeslagen sessies. u kunt selecteren en opnieuw verbinding maken met een opgeslagen sessie of een nieuwe sessie starten. Het maximum aantal toegestane actieve sessies, zowel opgeslagen als actief, wordt geconfigureerd door de gatewaybeheerder.

    Te klikken op **afsluiten** u afgemeld bij de Windows PowerShell Web Access-sessie zonder op te slaan.

- U wilt zich aanmelden om een andere externe computer te beheren in dezelfde browsersessie of op een nieuw tabblad van dezelfde browsersessie. (Dit geldt niet als de gateway-server wordt uitgevoerd Windows Server 2012 R2; Windows PowerShell-webtoegang is uitgevoerd op Windows Server 2012 R2 meerdere sessies toegestaan op nieuwe tabbladen in dezelfde browsersessie.) Zie voor meer informatie over het gebruik van meer dan één actieve sessies op dezelfde computer verbinding maken met meerdere doelcomputers tegelijkertijd in de [beperkingen van de webconsole](#limitations-of-the-web-based-console) sectie van dit onderwerp.

- De sessie is 20 minuten inactief. De gatewaybeheerder kan de time-outperiode voor inactiviteit aanpassen Zie voor meer informatie [sessiebeheer](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management).

    - Als u niet verbonden met een sessie in de webconsole vanwege een netwerkfout of andere niet-geplande afsluiting of mislukken, en niet omdat u de sessie hebt gesloten verbonden uzelf, de Windows PowerShell-webtoegang sessie uitvoeren blijft, met het doel de computer, totdat de time-outperiode op de client is verstreken. De time-outperiode is standaard 20 minuten. Dit wordt geconfigureerd door de gatewaybeheerder. De sessie wordt beëindigd na de standaardperiode van 20 minuten of na de time-outperiode die is opgegeven door de beheerder van de gateway, afhankelijk van welke periode korter is.

        Als de gateway-server wordt uitgevoerd van Windows Server 2012 R2, Windows PowerShell Web Access kunnen gebruikers opnieuw verbinding maken met opgeslagen sessies op een later tijdstip, maar u niet kunt zien of opnieuw verbinding maken met opgeslagen sessies pas na de time-outperiode die is opgegeven door de beheerder heeft verstreken.

- Sluit het browservenster of -tabblad.

- Schakel het clientapparaat uit waarop de browser wordt uitgevoerd of verbreek de verbinding met het netwerk.

- Met de **afsluiten** opdracht in de webconsole. Met deze opdracht werkt niet als de sessieconfiguratie waarmee u met verbonden bent is geconfigureerd voor ondersteuning [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) modus, of bevindt zich in een beperkte runspace.

Als u wilt opnieuw aanmelden, opent u de Windows PowerShell-webtoegang webpagina opnieuw en meld u aan de stappen in [aanmelden bij Windows PowerShell-webtoegang](#signing-in-to-windows-powershell-web-access) in dit onderwerp.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Verschillen in de webconsole voor Windows PowerShell

Na het aanmelden bij Windows PowerShell-internettoegang, is een webgebaseerde Windows PowerShell-console wordt geopend in uw browservenster of tabblad. Omdat de console is verbonden met de externe computer die u hebt opgegeven tijdens het aanmelden, kunnen alleen de Windows PowerShell-cmdlets of scripts die beschikbaar op de externe computer zijn worden gebruikt in de console. Deze sectie beschrijft de andere beperkingen van Windows PowerShell Web Access-consoles en verschillen tussen Windows PowerShell Web Access-consoles en de geïnstalleerde **PowerShell.exe** console.

### <a name="functional-disparity-with-powershellexe"></a>Functionele verschillen met PowerShell.exe

Het merendeel van de Windows PowerShell-Hostfunctionaliteit is beschikbaar in de webconsole voor Windows PowerShell-webtoegang, maar sommige functies die niet beschikbaar.

- Geneste voortgang wordt weergegeven.

  Windows PowerShell-webtoegang geeft een Voortgangs-GUI voor cmdlets die voortgang rapport, maar alleen gegevens over de voortgang op het hoogste niveau wordt weergegeven.

- Wijziging in invoerkleur.

  De invoerkleur (zowel de voorgrond- als achtergrondkleur) kan niet worden gewijzigd. De stijl van de uitvoer, waarschuwingen, uitgebreide uitvoer en foutberichten kan worden gewijzigd door een script uit te voeren.

- PSHostRawUserInterface.

  Windows PowerShell-webtoegang is geïmplementeerd via Extern beheer van Windows PowerShell en een externe runspace gebruikt. Windows PowerShell Web Access implementeert sommige methoden niet in deze interface; bijvoorbeeld alle opdrachten die naar de Windows-console wordt geschreven. Opdrachten, zoals **PowerTab** werken niet in Windows PowerShell Web Access.

- Functietoetsen.

  Windows PowerShell-webtoegang biedt geen ondersteuning voor bepaalde functietoetsen in veel gevallen omdat de opdrachten zijn gereserveerd door de browser.

### <a name="unsupported-shortcut-keys"></a>Niet-ondersteunde sneltoetsen

Functietoets | Actie
-- | --
Ctrl+C | In Windows PowerShell Web Access **Ctrl + C** wordt gebruikt door de browser om inhoud te kopiëren. De-console biedt een **annuleren** knop gebruikers kunnen ook worden gebruikt en **Ctrl + Q** opdrachten annuleren.
Alt+spatiebalk, e, l | Door de schermbuffer bladeren
Alt+spatiebalk, e, f | Zoeken naar tekst in de schermbuffer
Alt+spatiebalk, e, k | Tekst selecteren die u wilt kopiëren uit de schermbuffer
Alt+spatiebalk, e, p | Inhoud van het Klembord plakken in de Windows PowerShell-console
Alt+spatiebalk, c | Sluit de console Windows PowerShell
Ctrl+Break | Afdwingen van de Windows PowerShell-venster te sluiten
Ctrl+Home | Verwijderen vanaf het begin van de huidige opdrachtregel
Ctrl+End | Verwijderen tot het einde van de opdrachtregel
F1 | De cursor één teken naar rechts verplaatsen op de opdrachtregel
F2 | Een nieuwe opdracht maken door de laatste opdracht te kopiëren tot aan het teken dat u typt
F3 | De opdrachtregel vullen met inhoud van de laatste opdrachtregel
F4 | Tekens verwijderen vanaf de cursorpositie
F5 | Achterwaarts door de opdrachtgeschiedenis scannen. Voor toegang tot de opdrachten in de opdrachtgeschiedenis in Windows PowerShell-webtoegang, klikt u op de **geschiedenis** schuifknoppen in de webconsole.
F7 | Interactief een opdracht in de opdrachtgeschiedenis selecteren
F8 | De geschiedenis scannen en opdrachten weergeven die overeenkomen met de huidige tekst
F9 | Een specifieke genummerde opdracht in de geschiedenis uitvoeren
Page Up | De eerste opdracht in de geschiedenis uitvoeren
Page Down | De laatste opdracht in de geschiedenis uitvoeren
Alt+F7 | De opdrachtgeschiedenislijst wissen

### <a name="limitations-of-the-web-based-console"></a>Beperkingen van de webconsole

- Dubbele hop

    De dubbele-hopbeperking (of verbinding maakt met een tweede computer vanaf de eerste verbinding) kan optreden als u probeert te maken of een nieuwe sessie gewerkt met behulp van Windows PowerShell Web Access. Windows PowerShell-webtoegang maakt gebruik van een externe runspace en op dit moment **PowerShell.exe** biedt geen ondersteuning voor het maken van een externe verbinding met een tweede computer vanuit een externe runspace. Als u probeert verbinding maken met een tweede externe computer via een bestaande verbinding met behulp van de **Enter-PSSession** cmdlet, bijvoorbeeld, krijgt u diverse fouten optreden, zoals €œCannot netwerkbronnen ophalen.

    Double-hop om fouten te voorkomen, moet de beheerder CredSSP-verificatie configureren in uw netwerkomgeving organisaties. Zie voor meer informatie over het configureren van CredSSP-verificatie [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) op de website van Microsoft. U kunt ook expliciete referenties opgeven wanneer u een tweede externe computer wilt beheren. Met impliciete referenties is de tweede hop waarschijnlijk niet toegestaan.

- Externe toegang

    Windows PowerShell Web Access gebruikt en heeft dezelfde beperkingen als een externe Windows PowerShell-sessie. Opdrachten die rechtstreeks API's voor de Windows-console aanroepen, zoals opdrachten voor console-editors of tekstmenuprogramma's, werken niet omdat de opdrachten niet worden gelezen of geschreven naar standaardinvoer, -uitvoer en -foutpipes. Daarom opdrachten die een uitvoerbaar bestand starten-bestand, zoals **notepad.exe**, zoals een GUI weergeven of `OpenGridView` of `ogv`, werken niet. Uw ervaring wordt beïnvloed door dit gedrag; voor u zijn verschijnt het Windows PowerShell Web Access reageert niet op uw opdracht.

- Tab-aanvulling

    Tab-Aanvulling werkt niet in een sessieconfiguratie met een beperkte runspace of een in **NoLanguage** modus. Hoewel beheerders een sessie met ondersteuning van Tab-aanvulling kunnen configureren, wordt dit om veiligheidsredenen afgeraden omdat de volgende informatie kan worden weergegeven voor onbevoegde gebruikers.

    - Interne bestandssysteempaden

    - Gedeelde mappen op interne computers

    - Variabelen in de runspace

    - Geladen typen of .NET Framework-naamruimten

    - Omgevingsvariabelen

- **NoLanguage** sessie of een beperkte runspace

    Gebruikers die zijn aangemeld bij een **NoLanguage** sessieconfiguratie of een beperkte runspace in Windows PowerShell Web Access kan niet worden uitgevoerd de **afsluiten** opdracht om de sessie te beëindigen. Als u wilt afmelden, moeten gebruikers klikken op **Afmelden** op de pagina van de console.

- Tegelijk verbinding maken met meerdere doelcomputers.

    Als de gateway-server wordt uitgevoerd van Windows Server 2012, kunnen Windows PowerShell Web Access slechts één externe computerverbinding per browsersessie; Er mag geen gebruikers eenmalig aanmelden en verbinding maken met meerdere externe computers via afzonderlijke browsertabbladen. Wanneer u een nieuw tabblad of browservenster opent, Windows PowerShell-webtoegang wordt u gevraagd de huidige sessie te verbreken en een nieuwe sessie starten zodat u verbinding met de nieuwe (of dezelfde maken kunt) externe computer. Als u twee of meer afzonderlijke sessies op verschillende externe computers, zijn echter kunt een functie in Internet Explorer u een nieuwe sessie maken. Voor het starten van een nieuwe browsersessie in Internet Explorer, drukt u op **ALT**, open de **bestand** menu en selecteer vervolgens **nieuwe sessie**. Vervolgens opent u de Windows PowerShell Web Access-website in de nieuwe sessie en meld u aan voor toegang tot een andere externe computer.

    Wanneer de Windows PowerShell Web Access-gateway wordt uitgevoerd op Windows Server 2012 R2, kunnen gebruikers meerdere verbindingen met externe computers op verschillende browsertabbladen openen. Als u meer dan één verbinding met een externe computer wilt via het web gebaseerde Windows PowerShell-console te openen, controleert u met uw Windows PowerShell Web Access-gateway-beheerder om te controleren of deze functie wordt ondersteund door de gatewayserver.

- Permanente Windows PowerShell-sessies (opnieuw verbinding maken).

    Nadat u time-out van de Windows PowerShell Web Access-gateway, is de externe verbinding tussen de gateway en de doelcomputer gesloten. Hierdoor worden de actieve cmdlets of scripts stopgezet. U wordt aangeraden de Windows PowerShell gebruiken **-taak** infrastructuur wanneer u langdurige taken uitvoert, zodat u kunt taken starten, Verbreek de verbinding de computer tussen later opnieuw verbinding te maken en taken kunt blijven. Een ander voordeel van het gebruik van **-taak** cmdlets is dat u kunt ze worden gestart met behulp van Windows PowerShell-webtoegang, meldt u zich af en later opnieuw door het actieve Windows PowerShell-webtoegang of een andere host (zoals Windows PowerShell Integrated Scripting Environment (ISE)).

- Consoleformaat wijzigen.

    De **PowerShell.exe** consolevenster kan worden gewijzigd in de volgende drie manieren.

    - Het formaat van het consolevenster slepen en aanpassen met de muis

    - De hoogte- en breedte-eigenschappen wijzigen via een GUI voor console-eigenschappen

    - De hoogte en breedte van consolevensters wijzigen met een cmdlet

        Het consolevenster voor Windows PowerShell Web Access kan worden geconfigureerd met behulp van de cmdlets als volgt. In het volgende voorbeeld wordt een gebruiker de breedte van de Windows PowerShell Web Access-console naar **20**.

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        U kunt de hoogte van de console op dezelfde manier wijzigen.

        Aanvullende voorbeelden gegeven voor het aanpassen van de consoleweergave zijn beschikbaar in de [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/).

## <a name="see-also"></a>Zie ook

- [Windows PowerShell-Cmdlet-verwijzing](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Windows PowerShell op Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
- [TechNet Script Center Repository](http://gallery.technet.microsoft.com/scriptcenter)
- [Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
- [Windows PowerShell-teamblog](http://blogs.msdn.com/b/powershell/)