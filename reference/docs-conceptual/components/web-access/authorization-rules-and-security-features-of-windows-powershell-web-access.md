---
ms.date: 06/27/2017
keywords: Power shell, cmdlet
title: Autorisatieregels en beveiligingsfuncties van Windows PowerShell-internettoegang
ms.openlocfilehash: c426b8cfb10829241ba244a5d840c91e1de9f66e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058417"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Autorisatieregels en beveiligingsfuncties van Windows PowerShell-internettoegang

Bijgewerkt: 24 juni 2013

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

Windows Power shell Web Access in Windows Server 2012 R2 en Windows Server 2012 heeft een beperkt beveiligings model. Gebruikers moeten uitdrukkelijk toegang worden verleend voordat ze zich kunnen aanmelden bij de gateway voor Windows Power shell-webtoegang en de Windows Power shell-console van het web gebruiken.

## <a name="configuring-authorization-rules-and-site-security"></a>Autorisatieregels en sitebeveiliging configureren

Nadat Windows Power shell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, kunnen gebruikers de aanmeldings pagina in een browser openen, maar ze kunnen zich niet aanmelden totdat de beheerder van Windows Power shell-webtoegang expliciet toegang verleent voor gebruikers. Toegangs beheer voor Windows Power shell-webtoegang wordt beheerd met behulp van de set Windows Power shell-cmdlets die in de volgende tabel worden beschreven. Er is geen vergelijkbare grafische gebruikersinterface voor het toevoegen of beheren van autorisatieregels.
Zie [cmdlets voor Windows Power shell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Beheerders kunnen `{0-n}` verificatie regels definiëren voor Windows Power shell-webtoegang. De standaardbeveiliging is beperkend, niet toelatend. Als er geen verificatieregels zijn, heeft geen enkele gebruiker toegang tot iets.

[Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) en [test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) in Windows Server 2012 R2 bevatten een referentie parameter waarmee u Windows Power shell-autorisatie regels voor webtoegang vanaf een externe computer kunt toevoegen en testen, of vanuit een actieve Windows Power shell-sessie voor Internet toegang. Net als bij andere Windows Power shell-cmdlets die een referentie parameter hebben, kunt u een PSCredential-object opgeven als de waarde van de para meter. Als u een PSCredential-object wilt maken dat referenties bevat die u wilt door geven aan een externe computer, voert u de cmdlet [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) uit.

Windows Power shell-verificatie regels voor webtoegang zijn white list-regels. Elke regel is een definitie van een toegestane verbinding tussen gebruikers, doel computers en specifieke Windows Power shell- [sessie configuraties](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) (ook wel eind punten of _runspaces_) op opgegeven doel computers.
Zie beginnen met het [gebruik van Power shell runspaces](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/) voor een uitleg over **runspaces** .

> [!IMPORTANT]
> Voor een gebruiker hoeft slechts één regel waar te zijn om ervoor te zorgen dat hij of zij toegang krijgt. Als een gebruiker toegang heeft tot een computer met volledige taal toegang of alleen toegang tot Windows Power shell-cmdlets voor extern beheer, kan de gebruiker zich op de webgebaseerde console aanmelden (of hop) naar andere computers die zijn verbonden met de eerste doel computer. De veiligste manier om Windows Power shell Web Access te configureren is om gebruikers toegang te geven tot beperkte sessie configuraties waarmee ze specifieke taken kunnen uitvoeren die ze normaal gesp roken op afstand moeten uitvoeren.

Met de cmdlets waarnaar wordt verwezen in [Windows Power shell Web Access-cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) , kunt u een set toegangs regels maken die worden gebruikt om een gebruiker op de Windows Power shell Web Access-Gateway te autoriseren. De regels verschillen van de toegangsbeheerlijsten (ACL’s) op de doelcomputer en bieden een extra beveiligingslaag voor internettoegang. Meer informatie over beveiliging vindt u in het volgende gedeelte.

Als gebruikers geen van de voor gaande beveiligings lagen kunnen door geven, krijgen ze het bericht ' toegang geweigerd ' te zien in hun browser venster. Hoewel beveiligingsgegevens worden geregistreerd op de gatewayserver, zien eindgebruikers geen informatie over hoeveel beveiligingslagen ze zijn gepasseerd of op welke laag de aanmeldings- of verificatiefout is opgetreden.

Zie [autorisatie regels configureren](#configuring-authorization-rules-and-site-security) in dit onderwerp voor meer informatie over het configureren van autorisatie regels.

### <a name="security"></a>Beveiliging

Het beveiligings model van Windows Power shell-webtoegang heeft vier lagen tussen een eind gebruiker van de webconsole en een doel computer. Beheerders van Windows Power shell-webtoegang kunnen beveiligings lagen toevoegen via aanvullende configuratie in de IIS-beheer console. Zie [Configure Web Server Security (IIS7) (Engelstalig)](https://technet.microsoft.com/library/cc731278)voor meer informatie over het beveiligen van websites in de IIS-beheer console.

Zie [Aanbevolen procedures voor het voor komen van DOS/denial of service-aanvallen](https://technet.microsoft.com/library/cc750213)voor meer informatie over aanbevolen procedures voor IIS en denial-of-service-aanvallen te voor komen.
Een beheerder kan ook aanvullende Retail-verificatie software kopen en installeren.

In de volgende tabel worden de vier beveiligingslagen tussen eindgebruikers en doelcomputers beschreven.

|Niveau|Laag|
|-|-|
|1|[beveiligings functies van IIS-webserver](#iis-web-server-security-features)|
|2|[Windows Power shell Web Access-verificatie op basis van een gateway](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[Windows Power shell-autorisatie regels voor webtoegang](#windows-powershell-web-access-authorization-rules)|
|4|[verificatie-en autorisatie regels voor doel](#target-authentication-and-authorization-rules)|

Gedetailleerde informatie over elke laag vindt u in de volgende koppen:

#### <a name="iis-web-server-security-features"></a>Beveiligings functies van IIS-webserver

Gebruikers van Windows Power shell-webtoegang moeten altijd een gebruikers naam en wacht woord opgeven om hun accounts op de gateway te verifiëren. Windows Power shell-webtoegang kan echter ook optioneel verificatie van client certificaten in-of uitschakelen. Zie [Windows Power shell-webtoegang installeren en gebruiken](install-and-use-windows-powershell-web-access.md) om een test certificaat in te scha kelen en, later, hoe u een authentiek certificaat configureert).

De optionele functie voor clientcertificaten vereist dat eindgebruikers beschikken over een geldig clientcertificaat naast hun gebruikersnaam en wachtwoord en maakt deel uit van de webserverconfiguratie (IIS). Wanneer de client certificaat laag is ingeschakeld, vraagt de aanmeldings pagina van Windows Power shell-webtoegang gebruikers geldige certificaten op te geven voordat hun aanmeldings referenties worden geëvalueerd. Bij verificatie van clientcertificaten wordt het clientcertificaat automatisch gecontroleerd. Als er geen geldig certificaat wordt gevonden, worden gebruikers door Windows Power shell-webtoegang op de hoogte gebracht zodat het certificaat kan worden verstrekt. Als er een geldig client certificaat wordt gevonden, wordt in Windows Power shell Web Access de aanmeldings pagina geopend zodat gebruikers hun gebruikers namen en wacht woorden kunnen opgeven.

Dit is een voor beeld van aanvullende beveiligings instellingen die worden aangeboden door de IIS-webserver. Zie [Configure Web Server Security (IIS 7) (Engelstalig)](https://technet.microsoft.com/library/cc731278)voor meer informatie over andere IIS-beveiligings functies.

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows Power shell Web Access-verificatie op basis van een gateway

Op de aanmeldings pagina voor Windows Power shell-webtoegang is een set referenties (gebruikers naam en wacht woord) vereist en biedt gebruikers de mogelijkheid om andere referenties voor de doel computer op te geven.
Als de gebruiker geen alternatieve referenties opgeeft, worden de primaire gebruikersnaam en het primaire wachtwoord die worden gebruikt om verbinding te maken met de gateway, ook gebruikt om verbinding te maken met de doelcomputer.

De vereiste referenties worden geverifieerd op de Windows Power shell Web Access-Gateway. Deze referenties moeten geldige gebruikers accounts zijn op de lokale Windows Power shell Web Access-Gateway server of in Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Windows Power shell-autorisatie regels voor webtoegang

Nadat een gebruiker is geverifieerd op de gateway, controleert Windows Power shell-webtoegang autorisatie regels om te controleren of de gebruiker toegang heeft tot de aangevraagde doel computer. Na een geslaagde autorisatie worden de referenties van de gebruiker door gegeven aan de doel computer.

Deze regels worden pas geëvalueerd nadat een gebruiker is geverifieerd door de gateway en voordat een gebruiker kan worden geverifieerd op een doelcomputer.

#### <a name="target-authentication-and-authorization-rules"></a>Verificatie- en autorisatieregels van de doelcomputer

De laatste laag van beveiliging voor Windows Power shell-webtoegang is de eigen beveiligings configuratie van de doel computer. Gebruikers moeten beschikken over de juiste toegangs rechten die zijn geconfigureerd op de doel computer en ook in de autorisatie regels voor webtoegang van Windows Power shell om een Windows Power shell-webconsole uit te voeren die van invloed is op een doel computer via Windows Power shell-webtoegang.

Deze laag biedt dezelfde beveiligings mechanismen die Verbindings pogingen evalueren als gebruikers proberen een externe Windows Power shell-sessie te maken met een doel computer vanuit Windows Power shell door de [Enter-PSSession-](/powershell/module/microsoft.powershell.core/Enter-PSSession) of [New-PSSession-](/powershell/module/microsoft.powershell.core/new-pssession) cmdlets uit te voeren.

Windows Power shell Web Access maakt standaard gebruik van de primaire gebruikers naam en het wacht woord voor verificatie op de gateway en de doel computer. De webgebaseerde aanmeldings pagina, in een sectie met de naam **optionele Verbindings instellingen**, biedt gebruikers de mogelijkheid om andere referenties op te geven voor de doel computer, indien nodig. Als de gebruiker geen alternatieve referenties opgeeft, worden de primaire gebruikersnaam en het primaire wachtwoord die worden gebruikt om verbinding te maken met de gateway, ook gebruikt om verbinding te maken met de doelcomputer.

Autorisatieregels kunnen worden gebruikt om gebruikers toegang te verlenen tot een bepaalde sessieconfiguratie. U kunt _beperkte runspaces_ of sessie configuraties voor Windows Power shell-Internet toegang maken en specifieke gebruikers toestaan alleen verbinding te maken met specifieke sessie configuraties wanneer ze zich aanmelden bij Windows Power shell-webtoegang. U kunt toegangsbeheerlijsten (ACL's) gebruiken om te bepalen welke gebruikers toegang hebben tot specifieke eindpunten en de toegang tot het eindpunt voor specifieke gebruikers verder beperken met behulp van de autorisatieregels die in dit gedeelte worden beschreven. Zie [een beperkte runs Pace maken](https://msdn.microsoft.com/library/dn614668)voor meer informatie over runspaces.

### <a name="configuring-authorization-rules"></a>Autorisatieregels configureren

Beheerders willen waarschijnlijk dezelfde autorisatie regel voor Windows Power shell Web Access-gebruikers die al zijn gedefinieerd in hun omgeving voor extern beheer van Windows Power shell. In de eerste procedure in dit gedeelte wordt beschreven hoe u een veilige autorisatieregel toevoegt waarmee toegang wordt verleend aan één gebruiker die zich aanmeldt om één computer te beheren en binnen één sessieconfiguratie. In de tweede procedure wordt beschreven hoe u een autorisatieregel verwijdert die niet meer nodig is.

Als u van plan bent aangepaste sessie configuraties te gebruiken om specifieke gebruikers alleen binnen de beperkte runspaces in Windows Power shell-Internet toegang te laten werken, moet u uw aangepaste sessie configuraties maken voordat u autorisatie regels toevoegt die ernaar verwijzen. U kunt de cmdlets van Windows Power shell Web Access niet gebruiken om aangepaste sessie configuraties te maken. Zie [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files)voor meer informatie over het maken van aangepaste sessie configuraties.

Windows Power shell Web Access-cmdlets ondersteunen één Joker teken, een asterisk (\*). Jokertekens binnen tekenreeksen worden niet ondersteund. Gebruik één sterretje per eigenschap (gebruikers, computers of sessieconfiguraties).

> [!NOTE]
> Voor meer manieren waarop u autorisatie regels kunt gebruiken om toegang te verlenen aan gebruikers en de Windows Power shell Web Access-omgeving te beveiligen, raadpleegt u de [voor beelden van een ander autorisatie regel scenario](#other-authorization-rule-scenario-examples) in dit onderwerp.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Een beperkende autorisatieregel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

   - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.

   - Klik op het Windows- **Start** scherm met de rechter muisknop op **Windows Power shell**en klik vervolgens op **als administrator uitvoeren**.

2. **Optionele stap** Voor het beperken van gebruikers toegang met behulp van sessie configuraties:

   Controleer of de sessie configuraties die u wilt gebruiken, al bestaan in uw-regels.

   Als ze nog niet zijn gemaakt, gebruikt u de instructies voor het maken van sessie configuraties in [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Met deze autorisatie regel kan een specifieke gebruiker toegang hebben tot één computer in het netwerk waartoe deze doorgaans toegang hebben, met toegang tot een specifieke sessie configuratie die wordt toegewezen aan de gebruiker™ s typische scripting-en cmdlet-behoeften. Typ het volgende en druk vervolgens op **Enter**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - In het volgende voor beeld krijgt een gebruiker met de naam _JSmith_ in het domein _Contoso_ toegang tot het beheer van de computer _Contoso_214_en een sessie configuratie met de naam _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Controleer of de regel is gemaakt door de cmdlet **Get-PswaAuthorizationRule** of `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`uit te voeren.
   Voorbeeld: `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Een autorisatieregel verwijderen

1. Als er nog geen Windows Power shell-sessie is geopend, raadpleegt u stap 1 van [om een beperkende autorisatie regel toe te voegen](#to-add-a-restrictive-authorization-rule) in deze sectie.

2. Typ het volgende en druk vervolgens op **Enter**, waarbij de *regel-id* staat voor het unieke id-nummer van de regel die u wilt verwijderen.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Als u de id van de regel die u wilt verwijderen niet kent maar wel de beschrijvende naam, kunt u de naam van de regel doorgeven aan de cmdlet `Remove-PswaAuthorizationRule` om de regel te verwijderen, zoals in het volgende voorbeeld:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> U wordt niet gevraagd om te bevestigen of u de opgegeven autorisatie regel wilt verwijderen. de regel wordt verwijderd wanneer u op **Enter**drukt. Wees er zeker van dat u de autorisatieregel wilt verwijderen voordat u de cmdlet `Remove-PswaAuthorizationRule` uitvoert.

#### <a name="other-authorization-rule-scenario-examples"></a>Andere voorbeeldscenario’s met autorisatieregels

Elke Windows Power shell-sessie maakt gebruik van een sessie configuratie. Als er geen is opgegeven voor een sessie, gebruikt Windows Power shell de standaard ingebouwde Windows Power shell-sessie configuratie met de naam micro soft. Power shell. De standaardsessieconfiguratie bevat alle cmdlets die beschikbaar zijn op een computer. Beheerders kunnen de toegang tot alle computers beperken door een sessieconfiguratie met een beperkte runspace (een beperkt aantal cmdlets en taken die eindgebruikers kunnen uitvoeren) te definiëren. Een gebruiker die toegang tot één computer met volledige taal toegang of alleen de Windows Power shell-cmdlets voor extern beheer heeft gekregen, kan verbinding maken met andere computers die zijn verbonden met de eerste computer. Het definiëren van een beperkte runs Pace kan verhinderen dat gebruikers toegang hebben tot andere computers vanaf hun toegestane Windows Power shell-runs Pace en verbetert de beveiliging van uw Windows Power shell-webtoegang. De sessie configuratie kan worden gedistribueerd (met behulp van groepsbeleid) naar alle computers die beheerders toegankelijk willen maken via Windows Power shell-webtoegang. Zie [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)voor meer informatie over sessie configuraties. Hier volgen enkele voorbeelden van dit scenario.

- Een beheerder maakt een eind punt met de naam **pswaeindpunt**, met een beperkte runs Pace. Vervolgens maakt de beheerder een regel, `*,*,PswaEndpoint`en distribueert het eind punt naar andere computers. Met de regel kunnen alle gebruikers toegang krijgen tot alle computers met het eind punt **pswaeindpunt**.
  Als dit de enige autorisatieregel is die is gedefinieerd in de regelset, zijn computers zonder dat eindpunt niet toegankelijk.

- De beheerder heeft een eind punt met een beperkte runs Pace met de naam **pswaeindpunt**gemaakt en wil de toegang tot specifieke gebruikers beperken. De beheerder maakt een groep gebruikers met de naam **niveau1ondersteuning**en definieert de volgende regel: **niveau1ondersteuning,\*, pswaeindpunt**. De regel verleent alle gebruikers in de groep **niveau1ondersteuning** toegang tot alle computers met de **pswaeindpunt** -configuratie. Op vergelijkbare wijze kan de toegang worden beperkt tot een specifieke set computers.

- Sommige beheerders bieden bepaalde gebruikers uitgebreidere toegang dan andere. Een beheerder maakt bijvoorbeeld twee gebruikers groepen, **beheerders** en **basis ondersteuning**. De beheerder maakt ook een eind punt met een beperkte runs Pace met de naam **pswaeindpunt**en definieert de volgende twee regels: **beheerders,\*,\*** en **basis ondersteuning,\*, pswaeindpunt**. De eerste regel biedt alle gebruikers in de **beheerders** groep toegang tot alle computers en de tweede regel biedt alle gebruikers in de groep **basis ondersteuning** alleen toegang tot deze computers met **pswaeindpunt**.

- Een beheerder heeft een besloten testomgeving ingesteld en wil alle geautoriseerde netwerkgebruikers toegang geven tot alle computers in het netwerk waartoe ze gewoonlijk toegang hebben, met toegang tot alle sessieconfiguraties waartoe ze gewoonlijk toegang hebben. Omdat dit een besloten testomgeving is, maakt de beheerder een autorisatieregel die niet veilig is. -De beheerder voert de cmdlet uit `Add-PswaAuthorizationRule * * *`, die gebruikmaakt van het Joker teken **\*** om alle gebruikers, alle computers en alle configuraties weer te geven. -Deze regel is het equivalent van het volgende: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Deze regel wordt niet aanbevolen in een beveiligde omgeving en omzeilt de beveiligingslaag van de autorisatie regel van Windows Power shell-webtoegang.

- Een beheerder moet gebruikers toestaan verbinding te maken met doelcomputers in een omgeving met zowel werkgroepen als domeinen, waarbij werkgroepcomputers af en toe worden gebruikt om verbinding te maken met doelcomputers in domeinen en computers in domeinen af en toe worden gebruikt om verbinding te maken met doelcomputers in werkgroepen. De beheerder heeft een gateway server, *PswaServer*, in een werk groep. en de *SRV1.contoso.com* van de doel computer bevindt zich in een domein. Gebruiker *Chris* is een geautoriseerde lokale gebruiker op de gateway server van de werk groep en de doel computer. De gebruikers naam op de werkgroepserver is *chrisLocal*. en zijn gebruikers naam op de doel computer is *contoso\\Chris*. De beheerder verleent Chris toegang tot srv1.contoso.com door de volgende regel toe te voegen.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Het voor beeld van de voor gaande regel verifieert Chris op de gateway server en autoriseert zijn toegang tot *SRV1*. Op de aanmeldings pagina moet Chris een tweede set referenties opgeven in het gedeelte **optionele Verbindings instellingen** (*Contoso\\Chris*). De gateway server gebruikt de extra set referenties om hem te verifiëren op de doel computer, *SRV1.contoso.com*.

In het voor gaande scenario maakt Windows Power shell-webtoegang pas een geslaagde verbinding met de doel computer nadat het volgende is geslaagd en is toegestaan door ten minste één autorisatie regel.

1. Verificatie op de gateway server van de werk groep door een gebruikers naam in de indeling *server_name*\\*user_name* aan de autorisatie regel toe te voegen

2. Verificatie op de doel computer met behulp van alternatieve referenties op de aanmeldings pagina in het gedeelte **optionele Verbindings instellingen**

   > [!NOTE]
   > Als de gateway en de doelcomputer zich in verschillende werkgroepen of domeinen bevinden, moet een vertrouwensrelatie tussen de twee werkgroepcomputers, de twee domeinen of de werkgroep en het domein worden ingesteld. Deze relatie kan niet worden geconfigureerd met behulp van Windows Power shell Web Access Authorization Rule-cmdlets. Autorisatieregels definiëren geen vertrouwensrelatie tussen computers. Ze kunnen enkel gebruikers toestaan verbinding te maken met specifieke doelcomputers en sessieconfiguraties. Zie [domeinen en forest-vertrouwens relaties maken](https://technet.microsoft.com/library/cc794775.aspx)voor meer informatie over het configureren van een vertrouwens relatie tussen verschillende domeinen.
   > Zie [extern beheer met Serverbeheer](https://technet.microsoft.com/library/dd759202.aspx)voor meer informatie over het toevoegen van werkgroepcomputers aan een lijst met vertrouwde hosts.

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Eén set autorisatieregels gebruiken voor meerdere sites

Autorisatieregels worden opgeslagen in een XML-bestand. De naam van het pad van het XML-bestand is standaard `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

Het pad naar het XML-bestand met autorisatie regels wordt opgeslagen in het bestand **powwa. config** , dat zich in `$env:windir\Web\PowershellWebAccess\data`bevindt. De beheerder heeft de flexibiliteit om de verwijzing naar het standaardpad in **powwa. config** aan te passen aan de voor keuren of vereisten. Door de beheerder in staat te stellen de locatie van het bestand te wijzigen, kunnen meerdere Windows Power shell-Web Access-gateways dezelfde autorisatie regels gebruiken als een dergelijke configuratie gewenst is.

## <a name="session-management"></a>Sessiebeheer

Windows Power shell Web Access beperkt standaard een gebruiker tot drie sessies tegelijk. U kunt het **Web. config** -bestand van de webtoepassing bewerken in IIS-beheer ter ondersteuning van een verschillend aantal sessies per gebruiker. Het pad naar het bestand **Web. config** is `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

IIS-webserver is standaard geconfigureerd om de groep van toepassingen opnieuw te starten als er instellingen worden bewerkt. De groep van toepassingen wordt bijvoorbeeld opnieuw gestart als er wijzigingen worden aangebracht in het bestand **Web. config** . > omdat **Windows Power shell-webtoegang** in de sessie status in het geheugen gebruikt, > gebruikers die zijn aangemeld bij **Windows Power shell** -sessies voor Internet toegang hun sessies verliezen wanneer de groep van toepassingen opnieuw wordt gestart.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Standaardparameters instellen op de aanmeldingspagina

Als uw Windows Power shell Web Access-Gateway wordt uitgevoerd op Windows Server 2012 R2, kunt u standaard waarden configureren voor de instellingen die worden weer gegeven op de aanmeldings pagina van de Windows Power shell-webtoegang. U kunt in het bestand **Web. config** waarden configureren dat wordt beschreven in de vorige alinea. Standaard waarden voor de instellingen van de aanmeldings pagina vindt u in de sectie **appSettings** van het bestand Web. config. Hier volgt een voor beeld van de sectie **appSettings** . Geldige waarden voor veel van deze instellingen zijn dezelfde als die voor de overeenkomstige para meters van de cmdlet [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) in Windows Power shell.

Bijvoorbeeld, de `defaultApplicationName` sleutel, zoals in het volgende code blok wordt weer gegeven, is de waarde van de voorkeurs variabele **$PSSessionApplicationName** op de doel computer.

```xml
  <appSettings>
      <add key="maxSessionsAllowedPerUser" value="3"/>
      <add key="defaultPortNumber" value="5985"/>
      <add key="defaultSSLPortNumber" value="5986"/>
      <add key="defaultApplicationName" value="WSMAN"/>
      <add key="defaultUseSslSelection" value="0"/>
      <add key="defaultAuthenticationType" value="0"/>
      <add key="defaultAllowRedirection" value="0"/>
      <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
  </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>Time-outs en niet-geplande afgebroken sessies

Time-out voor Windows Power shell-Web Access-sessies. In Windows Power shell Web Access, dat wordt uitgevoerd op Windows Server 2012, wordt een time-outbericht weer gegeven aan aangemelde gebruikers na 15 minuten van inactiviteit van de sessie. Als de gebruiker niet binnen vijf minuten reageert nadat het time-outbericht wordt weer gegeven, wordt de sessie beëindigd en wordt de gebruiker afgemeld. U kunt de time-outperioden voor sessies wijzigen in de website-instellingen in IIS-beheer.

In Windows Power shell Web Access, dat wordt uitgevoerd op Windows Server 2012 R2, time-out van sessies, standaard na 20 minuten inactiviteit. Als gebruikers geen verbinding meer hebben met sessies in de webconsole vanwege netwerk fouten of andere niet-geplande afsluit gebeurtenissen of storingen, en niet omdat ze de sessies zelf hebben gesloten, blijven de Windows Power shell-sessies voor webtoegang actief, verbonden met doel computers, totdat de time-outperiode aan de client zijde vervalt. De sessie wordt beëindigd na de standaardperiode van 20 minuten of na de time-outperiode die is opgegeven door de beheerder van de gateway, afhankelijk van welke periode korter is.

Als op de gateway server Windows Server 2012 R2 wordt uitgevoerd, kunnen gebruikers met Windows Power shell-webtoegang op een later tijdstip opnieuw verbinding maken met opgeslagen sessies, maar wanneer er netwerk fouten, niet-gepland afsluiten of andere fouten worden verbroken, worden gebruikers niet weer geven of opnieuw verbonden met opslaan sessies tot na de time-outperiode die is opgegeven door de Gateway beheerder.

## <a name="see-also"></a>Zie ook

[Windows Power shell-webtoegang installeren en gebruiken](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Windows Power shell Web Access-cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
