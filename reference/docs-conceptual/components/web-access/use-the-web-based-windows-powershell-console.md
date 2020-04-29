---
ms.date: 08/23/2017
keywords: Power shell, cmdlet
title: de Windows Power shell-console op basis van het web gebruiken
ms.openlocfilehash: 9a5d6d825dc82710466768bc612b012dd80937da
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978658"
---
# <a name="use-the-web-based-windows-powershell-console"></a>De Windows Power shell-console van het web gebruiken

Bijgewerkt: 24 juni 2013

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

Met Windows Power shell Web Access kunnen gebruikers zich aanmelden bij een beveiligde website. Als u Windows Power shell-sessies,-cmdlets en-scripts wilt gebruiken om een externe computer te beheren.

Omdat de Windows Power shell-console wordt uitgevoerd in een webbrowser, kan deze worden geopend vanuit een groot aantal verschillende client apparaten. bijna alle apparaten met een webbrowser werken.

De webgebaseerde Windows Power shell-console is gericht op een externe computer die wordt opgegeven door gebruikers als onderdeel van het aanmeldings proces.

In dit onderwerp wordt beschreven hoe u zich aanmeldt bij en aan de slag gaat met de webconsole van Windows Power shell Web Access.

In dit onderwerp wordt niet beschreven hoe u Windows Power shell gebruikt of cmdlets of scripts uitvoert. Zie de sectie [Zie ook](#see-also) aan het einde van dit onderwerp voor informatie over het gebruik van Windows Power shell en het uitvoeren van scripts.

## <a name="supported-browsers-and-client-devices"></a>Ondersteunde browsers en client apparaten

Windows Power shell Web Access ondersteunt de volgende Internet browsers. Hoewel mobiele browsers niet officieel worden ondersteund, kunnen veel mogelijk de Windows Power shell-console van het web worden uitgevoerd. Andere browsers die cookies accepteren, java script uitvoeren en HTTPS-websites uitvoeren, worden verwacht, maar zijn niet officieel getest.

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

## <a name="signing-in-to-windows-powershell-web-access"></a>Aanmelden bij Windows Power shell-Internet toegang

De beheerder van Windows Power shell-webtoegang moet u een URL geven die het adres is van uw organisaties Windows Power shell Web Access Gateway-website. Dit website adres is `https://<server_name>/pswa`standaard.

Voordat u zich aanmeldt bij Windows Power shell-Internet toegang, moet u ervoor zorgen dat u de naam of het IP-adres hebt van de externe computer die u wilt beheren. U moet een geautoriseerde gebruiker zijn op de externe computer en deze moet zo zijn geconfigureerd dat extern beheer is toegestaan. Zie [Enable and use Remote commands in Windows Power shell](/powershell/module/microsoft.powershell.core/enable-psremoting)(Engelstalig) voor meer informatie over het configureren van uw computer om extern beheer toe te staan.

De eenvoudigste methode voor het configureren van uw computer om extern beheer toe te staan `Enable-PSRemoting -force` , is het uitvoeren van de cmdlet op de computer, in een Windows Power shell-sessie die is geopend met verhoogde gebruikers rechten (**als administrator uitvoeren**).

### <a name="to-sign-in-to-windows-powershell-web-access"></a>Aanmelden bij Windows Power shell-Internet toegang

1. Open de website Windows Power shell-webtoegang in een browser venster of tabblad van Internet.

1. Geef op de aanmeldings pagina voor Windows Power shell-webtoegang de gebruikers naam, het wacht woord en de naam van de computer op die u wilt beheren (en waarop u een geautoriseerde gebruiker bent). Als de beheerder van Windows Power shell-webtoegang heeft geadviseerd om een URI naar een aangepaste site of proxy server te gebruiken in plaats van een computer naam, selecteert u **verbindings-URI** in het veld **verbindings type** en geeft u vervolgens de URI op.

   > [!NOTE]
   > - Als de doel computer zich in een werk groep bevindt, gebruikt u de volgende syntaxis om uw gebruikers naam op te geven en u aan te melden bij de computer:`<workgroup_name>\<user_name>`
   > - Als de doel computer de gateway server is, kunt u in `localhost` het veld computer naam opgeven
   > - Als de doel computer de gateway server is en de gateway server zich in een werk groep bevindt, `<workgroup name>\<user_name>` moet u gebruiken in de naam van de gebruiker. U kunt gebruiken `localhost` in het veld computer naam.

1. De sectie **optionele Verbindings instellingen** heeft betrekking op de autorisatie vereisten van de externe computer die u wilt beheren. Zie de Help van de [Enter-PSSession-](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet voor meer informatie over de para meters die gelijk zijn aan de optionele Verbindings instellingen.

   Normaal gesp roken worden de referenties die u gebruikt om de Windows Power shell Web Access-Gateway door te geven, dezelfde die worden herkend door de externe computer die u wilt beheren. Als u echter andere referenties wilt gebruiken voor het beheren van de externe computer die u hebt opgegeven in stap 2, vouwt u de sectie **optionele Verbindings instellingen** uit en geeft u de alternatieve referenties op. Ga anders verder met stap 6.

1. Als de beheerder van Windows Power shell-webtoegang een aangepaste sessie configuratie heeft gemaakt voor gebruikers van Windows Power shell-webtoegang, typt u de naam van de sessie configuratie naam in het veld **configuratie naam** . Zie [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) (Engelstalig) voor meer informatie over sessieconfiguraties.

1. Zorg ervoor dat het **verificatie type** **standaard** is ingesteld, tenzij u een instructie hebt gekregen om anders te doen door de beheerder van de Windows Power shell-webtoegang.

1. Klik op **Aanmelden**.

## <a name="signing-out-and-timing-out"></a>Afmelden en time-out

Een van de volgende afmelden van een Windows Power shell-sessie op het web.

- Klik op **Afmelden** in de rechter benedenhoek van de console. (Alleen Windows Server 2012)
- Klik op **Opslaan** of **Afsluiten** in de rechter benedenhoek van de console (alleen Windows Server 2012 R2). Als u op **Opslaan** klikt, wordt uw Windows Power shell-Web Access-sessie opgeslagen en gesloten. u kunt later opnieuw verbinding maken met de sessie. Wanneer u zich opnieuw aanmeldt bij Windows Power shell-webtoegang, wordt in Windows Power shell Web Access een lijst met opgeslagen sessies weer gegeven. u kunt een opgeslagen sessie selecteren en opnieuw verbinding maken, of een nieuwe sessie starten. Het maximum aantal geopende sessies dat gebruikers zijn toegestaan, zowel opgeslagen als actief, wordt geconfigureerd door de Gateway beheerder.

  Als u op **Afsluiten** klikt, wordt u de Windows Power shell-sessie voor Internet toegang afgemeld zonder dat deze wordt opgeslagen.

- U probeert u aan te melden om een andere externe computer te beheren in dezelfde browser sessie of op een nieuw tabblad van dezelfde browser sessie. (Dit geldt niet als op de gateway server Windows Server 2012 R2 wordt uitgevoerd. Windows Power shell-Internet toegang die wordt uitgevoerd op Windows Server 2012 R2, staat meerdere gebruikers sessies toe op nieuwe tabbladen in dezelfde browser sessie.) Zie verbinding maken met meerdere doel computers tegelijk in het gedeelte [met beperkingen van het web-console](#limitations-of-the-web-based-console) van dit onderwerp voor meer informatie over het gebruik van meer dan één actieve sessie op dezelfde computer.

- 20 minuten van inactiviteit in de sessie. De beheerder van de gateway kan de time-outperiode voor inactiviteit aanpassen. Zie [sessie beheer](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management)voor meer informatie.

  - Als u geen verbinding hebt met een sessie in de webconsole vanwege een netwerk fout of andere niet-gepland afsluiten of mislukken, en niet omdat u de sessie zelf hebt gesloten, blijft de Windows Power shell-sessie voor webtoegang actief, verbonden met de doel computer totdat de time-outperiode aan de client zijde vervalt. Deze time-outperiode is standaard 20 minuten en wordt geconfigureerd door de Gateway beheerder. De sessie wordt verbroken na de standaard waarde van 20 minuten of na de time-outperiode die is opgegeven door de Gateway beheerder, afhankelijk van wat korter is.

    Als op de gateway server Windows Server 2012 R2 wordt uitgevoerd, kunnen gebruikers met Windows Power shell-webtoegang op een later tijdstip opnieuw verbinding maken met opgeslagen sessies, maar kunt u pas weer verbinding maken met opgeslagen sessies nadat de time-outperiode die is opgegeven door de Gateway beheerder is verstreken.

- Het browser venster of tabblad sluiten.

- Het client apparaat waarop de browser wordt uitgevoerd, uitschakelen of de verbinding met het netwerk verbreken.

- De opdracht **Exit** uitvoeren in de webconsole. Deze opdracht werkt niet als de sessie configuratie waarmee u verbinding hebt, zodanig is geconfigureerd dat deze de modus voor niet- [talen](/dotnet/api/system.management.automation.pslanguagemode) ondersteunt of zich in een beperkte runs Pace bevindt.

Als u zich opnieuw wilt aanmelden, opent u de webpagina van Windows Power shell Web Access opnieuw en meldt u zich aan met behulp van de stappen in [Aanmelden bij Windows Power shell-Internet toegang](#signing-in-to-windows-powershell-web-access) in dit onderwerp.

## <a name="differences-in-the-web-based-windows-powershell-console"></a>Verschillen in de op het web gebaseerde Windows Power shell-console

Nadat u zich hebt aangemeld bij Windows Power shell-webtoegang, wordt een op het web gebaseerde Windows Power shell-console geopend in uw browser venster of tabblad. Omdat de-console is verbonden met de externe computer die u hebt opgegeven tijdens het aanmeldings proces, kunnen alleen de Windows Power shell-cmdlets of-scripts die beschikbaar zijn op de externe computer, worden gebruikt in de-console. In deze sectie worden andere beperkingen beschreven van Windows Power shell Web Access-consoles en verschillen tussen Windows Power shell-Web Access-consoles en de geïnstalleerde **Power shell. exe** -console.

### <a name="functional-disparity-with-powershellexe"></a>Functionele depariteit met Power shell. exe

Het meren deel van de functionaliteit van de Windows Power shell-host is beschikbaar in de webconsole van Windows Power shell Web Access, maar er zijn enkele functies die niet beschikbaar zijn.

- Geneste voortgang wordt weer gegeven.

  Windows Power shell-webtoegang geeft een voortgangs interface weer voor cmdlets die de voortgang rapporteren, maar alleen voortgangs informatie op het hoogste niveau wordt weer gegeven.

- Wijziging in de invoer kleur.

  De invoer kleur (zowel voor de voor grond als de achtergrond) kan niet worden gewijzigd. De stijl van uitvoer, waarschuwingen, verbose en fout berichten kan allemaal worden gewijzigd door een script uit te voeren.

- PSHostRawUserInterface.

  Windows Power shell-Internet toegang wordt geïmplementeerd via extern beheer van Windows Power shell en maakt gebruik van een externe runs Pace. Windows Power shell-webtoegang implementeert geen enkele methode in deze interface; bijvoorbeeld elke opdracht die naar de Windows-console schrijft. Opdrachten zoals **PowerTab** werken niet in Windows Power shell-Internet toegang.

- Functie toetsen.

  Windows Power shell-Internet toegang biedt in veel gevallen geen ondersteuning voor sommige functie sleutels omdat de opdrachten zijn gereserveerd door de browser.

### <a name="unsupported-shortcut-keys"></a>Niet-ondersteunde sneltoetsen

 Functie toets   |                                                                                         Bewerking
--------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Ctrl+C          | In Windows Power shell Web Access wordt **CTRL + C** door de browser gebruikt om inhoud te kopiëren. De-console biedt een knop **Annuleren** en gebruikers kunnen ook **CTRL + Q** gebruiken om opdrachten te annuleren.
ALT-spatie, e, l | Schuif door de scherm buffer
ALT + spatie balk, e, f | Zoeken naar tekst in de scherm buffer
ALT + spatie balk, e, k | Tekst selecteren die uit de scherm buffer moet worden gekopieerd
ALT + spatie balk, e, p | Klembord inhoud in de Windows Power shell-console plakken
ALT + spatie balk, c    | De Windows Power shell-console sluiten
CTRL + onderbreken      | Het Windows Power shell-venster geforceerd sluiten
Ctrl+Home       | Verwijderd uit het begin van de huidige opdracht regel
Ctrl+End        | Verwijdert naar het einde van de opdracht regel
F1              | Cursor één teken naar rechts verplaatsen op de opdracht regel
F2              | Hiermee maakt u een nieuwe opdracht door de laatste opdracht te kopiëren naar het teken dat u typt
F3              | De opdracht regel met inhoud van de laatste opdracht regel volt ooien
F4              | Tekens uit de cursor positie verwijderen
F5              | Achterwaarts scannen met de opdracht geschiedenis. Als u opdrachten in de opdracht geschiedenis in Windows Power shell Web Access wilt openen, klikt u op de schuif knop **geschiedenis** in de webconsole.
F7              | Interactief een opdracht uit de opdracht geschiedenis selecteren
F8              | Scan geschiedenis met opdrachten die overeenkomen met de huidige tekst
F9              | Een specifieke genummerde opdracht uit de geschiedenis uitvoeren
Page Up         | De eerste opdracht in de geschiedenis uitvoeren
Page Down       | De laatste opdracht in de geschiedenis uitvoeren
Alt + F7          | De opdracht geschiedenis lijst wissen

### <a name="limitations-of-the-web-based-console"></a>Beperkingen van de webconsole

- Dubbele hop

  U kunt de dubbele hop (of verbinding maken met een tweede computer vanaf de eerste verbinding) ondervinden als u een nieuwe sessie probeert te maken of ermee wilt werken met behulp van Windows Power shell-webtoegang.
  Windows Power shell Web Access maakt gebruik van een externe runs Pace, en **Power shell. exe** biedt momenteel geen ondersteuning voor het tot stand brengen van een externe verbinding met een tweede computer vanaf een externe runs Pace. Als u probeert verbinding te maken met een tweede externe computer vanaf een bestaande verbinding met behulp van de **Enter-PSSession-** cmdlet, kunt u bijvoorbeeld verschillende fouten verkrijgen, &euro;zoals œCannot netwerk bronnen ophalen.

  Om dubbele-hop fouten te voor komen, moet de beheerder CredSSP-verificatie configureren in uw netwerk omgeving van uw organisatie. Zie voor meer informatie over het configureren van CredSSP [-verificatie CredSSP voor Second-hop Remoting](https://devblogs.microsoft.com/powershell/credssp-for-second-hop-remoting/) in het Power shell-blog. U kunt ook expliciete referenties opgeven wanneer u een tweede externe computer wilt beheren. impliciete referenties zijn waarschijnlijk niet toegestaan voor de tweede hop.

- Externe communicatie

  Windows Power shell Web Access gebruikt en heeft dezelfde beperkingen als een externe Windows Power shell-sessie. Opdrachten waarmee u Windows-console-Api's rechtstreeks aanroept, zoals die voor op de console gebaseerde editors of op tekst gebaseerde menu Programma's, werken niet omdat de opdrachten niet worden gelezen of geschreven naar standaard invoer-, uitvoer-en fout-pipes. Daarom werken opdrachten die een uitvoerbaar bestand starten, zoals **Notepad. exe**, of een grafische gebruikers interface weer `OpenGridView` geven `ogv`, zoals of. Dit gedrag is van invloed op uw ervaring. u ziet dat Windows Power shell-webtoegang niet reageert op de opdracht.

- Tabblad voltooiing

  Het tabblad volt ooien werkt niet in een sessie configuratie met een beperkte runs Pace of een in de modus voor niet- **taal** . Hoewel beheerders een sessie kunnen configureren ter ondersteuning van het volt ooien van het tabblad, wordt dit uit veiligheids overwegingen afgeraden, omdat de volgende informatie kan worden blootgesteld aan niet-gemachtigde gebruikers.

  - Interne bestandssysteem paden
  - Gedeelde mappen op interne computers
  - Variabelen in de runs Pace
  - Geladen typen or.NET Framework-naam ruimten
  - Omgevingsvariabelen

- Geen- **taal** sessie of beperkte runs Pace

  Gebruikers die zijn aangemeld bij een configuratie voor een niet- **Getaalde** sessie of een beperkte runs Pace in Windows Power shell-webtoegang, kunnen de opdracht **Afsluiten** niet uitvoeren om de sessie te beëindigen. Als gebruikers zich willen afmelden, klikt u op **Afmelden** op de pagina console.

- Tegelijkertijd verbinding maken met meerdere doel computers.

  Als op de gateway server Windows Server 2012 wordt uitgevoerd, is in Windows Power shell Web Access slechts één externe computer verbinding per browser sessie toegestaan. gebruikers kunnen zich niet eenmalig aanmelden en verbinding maken met meerdere externe computers via afzonderlijke browser tabbladen. Wanneer u een nieuw tabblad of nieuw browser venster opent, wordt u door Windows Power shell-webtoegang gevraagd uw huidige sessie te verbreken en een nieuwe sessie te starten, zodat u verbinding kunt maken met de nieuwe (of dezelfde) externe computer. Als twee of meer afzonderlijke sessies op verschillende externe computers gewenst zijn, kunt u met een functie in Internet Explorer echter een nieuwe sessie maken. Als u een nieuwe browser sessie in Internet Explorer wilt starten, drukt u op **Alt**, opent u het menu **bestand** en selecteert u vervolgens **nieuwe sessie**. Open vervolgens de website Windows Power shell Web Access in de nieuwe sessie en meld u aan om toegang te krijgen tot een andere externe computer.

  Wanneer de Windows Power shell Web Access-Gateway wordt uitgevoerd op Windows Server 2012 R2, kunnen gebruikers meerdere verbindingen met externe computers openen in verschillende browser tabbladen. Als u meer dan één verbinding met een externe computer wilt openen met behulp van de Windows Power shell-console op het web, raadpleegt u de Windows Power shell Web Access Gateway-beheerder om te zien of deze functie wordt ondersteund door de gateway server.

- Permanente Windows Power shell-sessies (opnieuw verbinding).

  Nadat u een time-out hebt opgelopen van de Windows Power shell Web Access-Gateway, wordt de externe verbinding tussen de gateway en de doel computer gesloten. Hiermee worden alle cmdlets of scripts gestopt die momenteel worden uitgevoerd. U wordt aangeraden de Windows Power shell **-taak** infrastructuur te gebruiken wanneer u langlopende taken uitvoert, zodat u taken kunt starten, de verbinding met de computer wilt verbreken, later opnieuw verbinding moet maken en de taken blijven behouden. Een ander voor deel van het gebruik van **-taak-** cmdlets is dat u deze kunt starten met Windows Power shell-webtoegang, zich afmeldt en later opnieuw verbinding maakt door Windows Power shell-webtoegang of een andere host (zoals Windows Power shell Integrated Scripting Environment (ISE)) uit te voeren.

- Grootte van console wijzigen.

  Het formaat van het console venster **Power shell. exe** kan op de volgende drie manieren worden gewijzigd.

  - Het formaat van het console venster met een muis slepen en aanpassen
  - De eigenschappen height en width wijzigen met behulp van een GUI voor console-eigenschappen
  - De hoogte en breedte van console vensters wijzigen met een cmdlet

    Het console venster voor Windows Power shell-webtoegang kan worden geconfigureerd met behulp van de-cmdlets als volgt. In het volgende voor beeld wijzigt een gebruiker de breedte van Windows Power shell Web Access-console in **20**.

    ```powershell
    $newSize = $Host.UI.RawUI.WindowSize
    $newSize.Width = $newSize.Width - 20
    $oldSize = $Host.UI.RawUI.WindowSize
    $Host.UI.RawUI.WindowSize = $newSize
    ```

    U kunt de hoogte van de console op een vergelijk bare manier wijzigen.

    Aanvullende voor beelden voor het aanpassen van de console weergave zijn beschikbaar in het [Windows Power shell-team blog](https://devblogs.microsoft.com/powershell).

## <a name="see-also"></a>Zie ook

- [Hallo scriptman!](https://devblogs.microsoft.com/scripting/)
