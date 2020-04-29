---
ms.date: 06/27/2017
keywords: Power shell, cmdlet
title: Autorisatie regels en beveiligings functies van Windows Power shell-Internet toegang
ms.openlocfilehash: ee25df052994e47e559daa87b89af813471d896b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624751"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Autorisatie regels en beveiligings functies van Windows Power shell-Internet toegang

Bijgewerkt: 24 juni 2013

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

Windows Power shell Web Access in Windows Server 2012 R2 en Windows Server 2012 heeft een beperkt beveiligings model. Gebruikers moeten uitdrukkelijk toegang worden verleend voordat ze zich kunnen aanmelden bij de gateway voor Windows Power shell-webtoegang en de Windows Power shell-console van het web gebruiken.

## <a name="configuring-authorization-rules-and-site-security"></a>Verificatie regels en site beveiliging configureren

Nadat Windows Power shell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, kunnen gebruikers de aanmeldings pagina in een browser openen, maar ze kunnen zich niet aanmelden totdat de beheerder van Windows Power shell-webtoegang expliciet toegang verleent voor gebruikers. Toegangs beheer voor Windows Power shell-webtoegang wordt beheerd met behulp van de set Windows Power shell-cmdlets die in de volgende tabel worden beschreven. Er is geen vergelijk bare GUI voor het toevoegen of beheren van autorisatie regels.
Zie [cmdlets voor Windows Power shell Web Access](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Beheerders kunnen verificatie `{0-n}` regels definiëren voor Windows Power shell-webtoegang. De standaard beveiliging is beperkend in plaats van strikte, nul verificatie regels betekent dat geen enkele gebruiker toegang heeft.

[Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) en [test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) in Windows Server 2012 R2 bevatten een referentie parameter waarmee u Windows Power shell-autorisatie regels voor webtoegang vanaf een externe computer kunt toevoegen en testen, of vanuit een actieve Windows Power shell-sessie voor Internet toegang. Net als bij andere Windows Power shell-cmdlets die een referentie parameter hebben, kunt u een PSCredential-object opgeven als de waarde van de para meter. Als u een PSCredential-object wilt maken dat referenties bevat die u wilt door geven aan een externe computer, voert u de cmdlet [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) uit.

Windows Power shell-verificatie regels voor webtoegang zijn white list-regels. Elke regel is een definitie van een toegestane verbinding tussen gebruikers, doel computers en specifieke Windows Power shell- [sessie configuraties](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) (ook wel eind punten of _runspaces_) op opgegeven doel computers.
Zie beginnen met het [gebruik van Power shell runspaces](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/) voor een uitleg over **runspaces** .

> [!IMPORTANT]
> Een gebruiker heeft slechts één regel nodig om toegang te krijgen. Als een gebruiker toegang heeft tot een computer met volledige taal toegang of alleen toegang tot Windows Power shell-cmdlets voor extern beheer, kan de gebruiker zich op de webgebaseerde console aanmelden (of hop) naar andere computers die zijn verbonden met de eerste doel computer. De veiligste manier om Windows Power shell Web Access te configureren is om gebruikers toegang te geven tot beperkte sessie configuraties waarmee ze specifieke taken kunnen uitvoeren die ze normaal gesp roken op afstand moeten uitvoeren.

Met de cmdlets waarnaar wordt verwezen in [Windows Power shell Web Access-cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) , kunt u een set toegangs regels maken die worden gebruikt om een gebruiker op de Windows Power shell Web Access-Gateway te autoriseren. De regels verschillen van de toegangs beheer lijsten (Acl's) op de doel computer en bieden een extra beveiligingslaag voor Internet toegang. Meer informatie over beveiliging wordt beschreven in de volgende sectie.

Als gebruikers geen van de voor gaande beveiligings lagen kunnen door geven, krijgen ze het bericht ' toegang geweigerd ' te zien in hun browser venster. Hoewel er beveiligings Details worden geregistreerd op de gateway server, worden eind gebruikers niet weer gegeven informatie over het aantal beveiligings lagen dat ze hebben door gegeven, of op welke laag het aanmelden of de verificatie fout is opgetreden.

Zie [autorisatie regels configureren](#configuring-authorization-rules-and-site-security) in dit onderwerp voor meer informatie over het configureren van autorisatie regels.

### <a name="security"></a>Beveiliging

Het beveiligings model van Windows Power shell-webtoegang heeft vier lagen tussen een eind gebruiker van de webconsole en een doel computer. Beheerders van Windows Power shell-webtoegang kunnen beveiligings lagen toevoegen via aanvullende configuratie in de IIS-beheer console. Zie [Configure Web Server Security (IIS7) (Engelstalig)](https://technet.microsoft.com/library/cc731278)voor meer informatie over het beveiligen van websites in de IIS-beheer console.

Zie [Aanbevolen procedures voor het voor komen van DOS/denial of service-aanvallen](https://technet.microsoft.com/library/cc750213)voor meer informatie over aanbevolen procedures voor IIS en denial-of-service-aanvallen te voor komen.
Een beheerder kan ook aanvullende Retail-verificatie software kopen en installeren.

In de volgende tabel worden de vier beveiligings lagen tussen eind gebruikers en doel computers beschreven.

|Niveau|Laag|
|-|-|
|1|[beveiligings functies van IIS-webserver](#iis-web-server-security-features)|
|2|[Windows Power shell Web Access-verificatie op basis van een gateway](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[Windows Power shell-autorisatie regels voor webtoegang](#windows-powershell-web-access-authorization-rules)|
|4|[verificatie-en autorisatie regels voor doel](#target-authentication-and-authorization-rules)|

Gedetailleerde informatie over elke laag vindt u in de volgende koppen:

#### <a name="iis-web-server-security-features"></a>Beveiligings functies van IIS-webserver

Gebruikers van Windows Power shell-webtoegang moeten altijd een gebruikers naam en wacht woord opgeven om hun accounts op de gateway te verifiëren. Windows Power shell-webtoegang kan echter ook optioneel verificatie van client certificaten in-of uitschakelen. Zie [Windows Power shell-webtoegang installeren en gebruiken](install-and-use-windows-powershell-web-access.md) om een test certificaat in te scha kelen en, later, hoe u een authentiek certificaat configureert).

De optionele client certificaat functie vereist dat eind gebruikers een geldig client certificaat hebben, naast hun gebruikers namen en wacht woorden, en maakt deel uit van de configuratie van de webserver (IIS). Wanneer de client certificaat laag is ingeschakeld, vraagt de aanmeldings pagina van Windows Power shell-webtoegang gebruikers geldige certificaten op te geven voordat hun aanmeldings referenties worden geëvalueerd. Verificatie van client certificaten controleert automatisch op het client certificaat. Als er geen geldig certificaat wordt gevonden, worden gebruikers door Windows Power shell-webtoegang op de hoogte gebracht zodat het certificaat kan worden verstrekt. Als er een geldig client certificaat wordt gevonden, wordt in Windows Power shell Web Access de aanmeldings pagina geopend zodat gebruikers hun gebruikers namen en wacht woorden kunnen opgeven.

Dit is een voor beeld van aanvullende beveiligings instellingen die worden aangeboden door de IIS-webserver. Zie [Configure Web Server Security (IIS 7) (Engelstalig)](https://technet.microsoft.com/library/cc731278)voor meer informatie over andere IIS-beveiligings functies.

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows Power shell Web Access-verificatie op basis van een gateway

Op de aanmeldings pagina voor Windows Power shell-webtoegang is een set referenties (gebruikers naam en wacht woord) vereist en biedt gebruikers de mogelijkheid om andere referenties voor de doel computer op te geven.
Als de gebruiker geen alternatieve referenties opgeeft, worden de primaire gebruikers naam en het wacht woord die worden gebruikt om verbinding te maken met de gateway ook gebruikt om verbinding te maken met de doel computer.

De vereiste referenties worden geverifieerd op de Windows Power shell Web Access-Gateway. Deze referenties moeten geldige gebruikers accounts zijn op de lokale Windows Power shell Web Access-Gateway server of in Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Windows Power shell-autorisatie regels voor webtoegang

Nadat een gebruiker is geverifieerd op de gateway, controleert Windows Power shell-webtoegang autorisatie regels om te controleren of de gebruiker toegang heeft tot de aangevraagde doel computer. Na een geslaagde autorisatie worden de referenties van de gebruiker door gegeven aan de doel computer.

Deze regels worden alleen geëvalueerd nadat een gebruiker is geverifieerd door de gateway en voordat een gebruiker kan worden geverifieerd op een doel computer.

#### <a name="target-authentication-and-authorization-rules"></a>Verificatie-en autorisatie regels voor doel

De laatste laag van beveiliging voor Windows Power shell-webtoegang is de eigen beveiligings configuratie van de doel computer. Gebruikers moeten beschikken over de juiste toegangs rechten die zijn geconfigureerd op de doel computer en ook in de autorisatie regels voor webtoegang van Windows Power shell om een Windows Power shell-webconsole uit te voeren die van invloed is op een doel computer via Windows Power shell-webtoegang.

Deze laag biedt dezelfde beveiligings mechanismen die Verbindings pogingen evalueren als gebruikers proberen een externe Windows Power shell-sessie te maken met een doel computer vanuit Windows Power shell door de [Enter-PSSession-](/powershell/module/microsoft.powershell.core/Enter-PSSession) of [New-PSSession-](/powershell/module/microsoft.powershell.core/new-pssession) cmdlets uit te voeren.

Windows Power shell Web Access maakt standaard gebruik van de primaire gebruikers naam en het wacht woord voor verificatie op de gateway en de doel computer. De webgebaseerde aanmeldings pagina, in een sectie met de naam **optionele Verbindings instellingen**, biedt gebruikers de mogelijkheid om andere referenties op te geven voor de doel computer, indien nodig. Als de gebruiker geen alternatieve referenties opgeeft, worden de primaire gebruikers naam en het wacht woord die worden gebruikt om verbinding te maken met de gateway ook gebruikt om verbinding te maken met de doel computer.

Autorisatie regels kunnen worden gebruikt om gebruikers toegang te geven tot een bepaalde sessie configuratie. U kunt _beperkte runspaces_ of sessie configuraties voor Windows Power shell-Internet toegang maken en specifieke gebruikers toestaan alleen verbinding te maken met specifieke sessie configuraties wanneer ze zich aanmelden bij Windows Power shell-webtoegang. U kunt toegangs beheer lijsten (Acl's) gebruiken om te bepalen welke gebruikers toegang hebben tot specifieke eind punten en de toegang tot het eind punt voor een bepaalde groep gebruikers verder beperken met behulp van autorisatie regels die in deze sectie worden beschreven. Zie [een beperkte runs Pace maken](/powershell/scripting/developer/hosting/creating-a-constrained-runspace)voor meer informatie over runspaces.

### <a name="configuring-authorization-rules"></a>Autorisatie regels configureren

Beheerders willen waarschijnlijk dezelfde autorisatie regel voor Windows Power shell Web Access-gebruikers die al zijn gedefinieerd in hun omgeving voor extern beheer van Windows Power shell. In de eerste procedure in deze sectie wordt beschreven hoe u een beveiligde autorisatie regel toevoegt waarmee toegang wordt verleend aan één gebruiker, zich kan aanmelden voor het beheren van één computer en binnen een configuratie met één sessie. In de tweede procedure wordt beschreven hoe u een autorisatie regel verwijdert die niet meer nodig is.

Als u van plan bent aangepaste sessie configuraties te gebruiken om specifieke gebruikers alleen binnen de beperkte runspaces in Windows Power shell-Internet toegang te laten werken, moet u uw aangepaste sessie configuraties maken voordat u autorisatie regels toevoegt die ernaar verwijzen. U kunt de cmdlets van Windows Power shell Web Access niet gebruiken om aangepaste sessie configuraties te maken. Zie [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files)voor meer informatie over het maken van aangepaste sessie configuraties.

Windows Power shell Web Access-cmdlets ondersteunen één Joker teken, een \* asterisk (). Joker tekens in teken reeksen worden niet ondersteund. Gebruik één asterisk per eigenschap (gebruikers, computers of sessie configuraties).

> [!NOTE]
> Voor meer manieren waarop u autorisatie regels kunt gebruiken om toegang te verlenen aan gebruikers en de Windows Power shell Web Access-omgeving te beveiligen, raadpleegt u de [voor beelden van een ander autorisatie regel scenario](#other-authorization-rule-scenario-examples) in dit onderwerp.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Een beperkende autorisatie regel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

   - Klik op het bureaublad van Windows met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **Als administrator uitvoeren**.

   - Klik op het Windows- **Start** scherm met de rechter muisknop op **Windows Power shell**en klik vervolgens op **als administrator uitvoeren**.

2. **Optionele stap** Voor het beperken van gebruikers toegang met behulp van sessie configuraties:

   Controleer of de sessie configuraties die u wilt gebruiken, al bestaan in uw-regels.

   Als ze nog niet zijn gemaakt, gebruikt u de instructies voor het maken van sessie configuraties in [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Met deze autorisatie regel kan een specifieke gebruiker toegang hebben tot één computer in het netwerk waartoe deze doorgaans toegang hebben, met toegang tot een specifieke sessie configuratie die wordt afgestemd op de typische scripting-en cmdlet-vereisten van de gebruiker. Typ het volgende en druk op **Enter**.

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
   Bijvoorbeeld `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Een autorisatie regel verwijderen

1. Als er nog geen Windows Power shell-sessie is geopend, raadpleegt u stap 1 van [om een beperkende autorisatie regel toe te voegen](#to-add-a-restrictive-authorization-rule) in deze sectie.

2. Typ het volgende en druk vervolgens op **Enter**, waarbij de *regel-id* staat voor het unieke id-nummer van de regel die u wilt verwijderen.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Als u het ID-nummer niet kent, maar wel de beschrijvende naam van de regel die u wilt verwijderen, kunt u de naam van de regel ophalen en deze naar de `Remove-PswaAuthorizationRule` cmdlet pipeen om de regel te verwijderen, zoals in het volgende voor beeld wordt weer gegeven:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> U wordt niet gevraagd om te bevestigen of u de opgegeven autorisatie regel wilt verwijderen. de regel wordt verwijderd wanneer u op **Enter**drukt. Zorg ervoor dat u de autorisatie regel wilt verwijderen voordat u de `Remove-PswaAuthorizationRule` cmdlet uitvoert.

#### <a name="other-authorization-rule-scenario-examples"></a>Andere scenario voorbeelden van autorisatie regels

Elke Windows Power shell-sessie maakt gebruik van een sessie configuratie. Als er geen is opgegeven voor een sessie, gebruikt Windows Power shell de standaard ingebouwde Windows Power shell-sessie configuratie met de naam micro soft. Power shell. De standaard sessie configuratie bevat alle cmdlets die beschikbaar zijn op een computer. Beheerders kunnen de toegang tot alle computers beperken door een sessie configuratie met een beperkte runs Pace te definiëren (een beperkt aantal cmdlets en taken die hun eind gebruikers kunnen uitvoeren). Een gebruiker die toegang tot één computer met volledige taal toegang of alleen de Windows Power shell-cmdlets voor extern beheer heeft gekregen, kan verbinding maken met andere computers die zijn verbonden met de eerste computer. Het definiëren van een beperkte runs Pace kan verhinderen dat gebruikers toegang hebben tot andere computers vanaf hun toegestane Windows Power shell-runs Pace en verbetert de beveiliging van uw Windows Power shell-webtoegang. De sessie configuratie kan worden gedistribueerd (met behulp van groepsbeleid) naar alle computers die beheerders toegankelijk willen maken via Windows Power shell-webtoegang. Zie [about_Session_Configurations](/powershell/module/Microsoft.PowerShell.Core/About/about_session_configurations) (Engelstalig) voor meer informatie over sessieconfiguraties.
Hier volgen enkele voor beelden van dit scenario.

- Een beheerder maakt een eind punt met de naam **pswaeindpunt**, met een beperkte runs Pace. Vervolgens maakt de beheerder een regel `*,*,PswaEndpoint`en distribueert het eind punt naar andere computers. Met de regel kunnen alle gebruikers toegang krijgen tot alle computers met het eind punt **pswaeindpunt**.
  Als dit de enige autorisatie regel is die in de regel is gedefinieerd, zijn computers zonder dat eind punt niet toegankelijk.

- De beheerder heeft een eind punt met een beperkte runs Pace met de naam **pswaeindpunt**gemaakt en wil de toegang tot specifieke gebruikers beperken. De beheerder maakt een groep gebruikers met de naam **niveau1ondersteuning**en definieert de volgende regel: **niveau1ondersteuning,\*, pswaeindpunt**. De regel verleent alle gebruikers in de groep **niveau1ondersteuning** toegang tot alle computers met de **pswaeindpunt** -configuratie. Op dezelfde manier kan toegang worden beperkt tot een specifieke set computers.

- Sommige beheerders bieden bepaalde gebruikers meer toegang dan andere. Een beheerder maakt bijvoorbeeld twee gebruikers groepen, **beheerders** en **basis ondersteuning**. De beheerder maakt ook een eind punt met een beperkte runs Pace met de naam **pswaeindpunt**en definieert de volgende twee regels: **beheerders,\*,\* ** en **basis ondersteuning,\*, pswaeindpunt**. De eerste regel biedt alle gebruikers in de **beheerders** groep toegang tot alle computers en de tweede regel biedt alle gebruikers in de groep **basis ondersteuning** alleen toegang tot deze computers met **pswaeindpunt**.

- Een beheerder heeft een persoonlijke test omgeving ingesteld en wil alle geautoriseerde netwerk gebruikers toegang geven tot alle computers in het netwerk waartoe ze doorgaans toegang hebben, met toegang tot alle sessie configuraties waartoe ze doorgaans toegang hebben. Omdat dit een persoonlijke test omgeving is, maakt de beheerder een autorisatie regel die niet beveiligd is. -De beheerder voert de cmdlet `Add-PswaAuthorizationRule * * *`uit die gebruikmaakt van het Joker **\*** teken om alle gebruikers, alle computers en alle configuraties weer te geven. -Deze regel is het equivalent van het volgende: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Deze regel wordt niet aanbevolen in een beveiligde omgeving en omzeilt de beveiligingslaag van de autorisatie regel van Windows Power shell-webtoegang.

- Een beheerder moet gebruikers in staat stellen om verbinding te maken met doel computers in een omgeving met zowel werk groepen als domeinen, waarbij werk groep computers af en toe worden gebruikt om verbinding te maken met doel computers in domeinen en computers in domeinen af en toe worden gebruikt om verbinding te maken met doel computers in werk groepen. De beheerder heeft een gateway server, *PswaServer*, in een werk groep. en de *SRV1.contoso.com* van de doel computer bevindt zich in een domein. Gebruiker *Chris* is een geautoriseerde lokale gebruiker op de gateway server van de werk groep en de doel computer. De gebruikers naam op de werkgroepserver is *chrisLocal*. en zijn gebruikers naam op de doel computer is *Contoso\\Chris*. De beheerder voegt de volgende regel toe om toegang tot srv1.contoso.com voor Chris te autoriseren.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Het voor beeld van de voor gaande regel verifieert Chris op de gateway server en autoriseert zijn toegang tot *SRV1*. Op de aanmeldings pagina moet Chris een tweede set referenties opgeven in het gedeelte **optionele Verbindings instellingen** (*\\contoso Chris*). De gateway server gebruikt de extra set referenties om hem te verifiëren op de doel computer, *SRV1.contoso.com*.

In het voor gaande scenario maakt Windows Power shell-webtoegang pas een geslaagde verbinding met de doel computer nadat het volgende is geslaagd en is toegestaan door ten minste één autorisatie regel.

1. Verificatie op de gateway server van de werk groep door een gebruikers naam in de indeling *server_name*\\*user_name* toe te voegen aan de autorisatie regel

2. Verificatie op de doel computer met behulp van alternatieve referenties op de aanmeldings pagina in het gedeelte **optionele Verbindings instellingen**

   > [!NOTE]
   > Als de gateway en de doel computer zich in verschillende werk groepen of domeinen bevinden, moet er een vertrouwens relatie tot stand worden gebracht tussen de twee werkgroepcomputers, de twee domeinen of tussen de werk groep en het domein. Deze relatie kan niet worden geconfigureerd met behulp van Windows Power shell Web Access Authorization Rule-cmdlets. Autorisatie regels definiëren geen vertrouwens relatie tussen computers. ze kunnen gebruikers alleen toestemming geven om verbinding te maken met specifieke doel computers en sessie configuraties. Zie [domeinen en forest-vertrouwens relaties maken](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794775(v=ws.10))voor meer informatie over het configureren van een vertrouwens relatie tussen verschillende domeinen.
   > Zie [extern beheer met Serverbeheer](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759202(v=ws.11))voor meer informatie over het toevoegen van werkgroepcomputers aan een lijst met vertrouwde hosts.

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Eén set autorisatie regels gebruiken voor meerdere sites

Autorisatie regels worden opgeslagen in een XML-bestand. De naam van het pad van het XML-bestand is `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`standaard.

Het pad naar het XML-bestand met autorisatie regels wordt opgeslagen in het bestand **powwa. config** , dat zich `$env:windir\Web\PowershellWebAccess\data`bevindt in. De beheerder heeft de flexibiliteit om de verwijzing naar het standaardpad in **powwa. config** aan te passen aan de voor keuren of vereisten. Door de beheerder in staat te stellen de locatie van het bestand te wijzigen, kunnen meerdere Windows Power shell-Web Access-gateways dezelfde autorisatie regels gebruiken als een dergelijke configuratie gewenst is.

## <a name="session-management"></a>Sessiebeheer

Windows Power shell Web Access beperkt standaard een gebruiker tot drie sessies tegelijk. U kunt het **Web. config** -bestand van de webtoepassing bewerken in IIS-beheer ter ondersteuning van een verschillend aantal sessies per gebruiker. Het pad naar het bestand **Web. config** is `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

IIS-webserver is standaard geconfigureerd om de groep van toepassingen opnieuw te starten als er instellingen worden bewerkt. De groep van toepassingen wordt bijvoorbeeld opnieuw gestart als er wijzigingen worden aangebracht in het bestand **Web. config** . >omdat **Windows Power shell-webtoegang** in de sessie status in het geheugen gebruikt, >gebruikers die zijn aangemeld bij **Windows Power shell** -sessies voor Internet toegang hun sessies verliezen wanneer de groep van toepassingen opnieuw wordt gestart.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Standaard parameters instellen op de aanmeldings pagina

Als uw Windows Power shell Web Access-Gateway wordt uitgevoerd op Windows Server 2012 R2, kunt u standaard waarden configureren voor de instellingen die worden weer gegeven op de aanmeldings pagina van de Windows Power shell-webtoegang. U kunt in het bestand **Web. config** waarden configureren dat wordt beschreven in de vorige alinea. Standaard waarden voor de instellingen van de aanmeldings pagina vindt u in de sectie **appSettings** van het bestand Web. config. Hier volgt een voor beeld van de sectie **appSettings** . Geldige waarden voor veel van deze instellingen zijn dezelfde als die voor de overeenkomstige para meters van de cmdlet [New-PSSession](/powershell/module/Microsoft.PowerShell.Core/New-PSSession) in Windows Power shell.

Bijvoorbeeld, de `defaultApplicationName` sleutel, zoals in het volgende code blok wordt weer gegeven, is de waarde van de variabele **$PSSessionApplicationName** voor keur op de doel computer.

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

### <a name="time-outs-and-unplanned-disconnections"></a>Time-outs en niet-geplande verbroken verbindingen

Time-out voor Windows Power shell-Web Access-sessies. In Windows Power shell Web Access, dat wordt uitgevoerd op Windows Server 2012, wordt een time-outbericht weer gegeven aan aangemelde gebruikers na 15 minuten van inactiviteit van de sessie. Als de gebruiker niet binnen vijf minuten reageert nadat het time-outbericht wordt weer gegeven, wordt de sessie beëindigd en wordt de gebruiker afgemeld. U kunt de time-outperioden voor sessies wijzigen in de website-instellingen in IIS-beheer.

In Windows Power shell Web Access, dat wordt uitgevoerd op Windows Server 2012 R2, time-out van sessies, standaard na 20 minuten inactiviteit. Als gebruikers geen verbinding meer hebben met sessies in de webconsole vanwege netwerk fouten of andere niet-geplande afsluitingen of storingen, en niet omdat ze de sessies zelf hebben gesloten, blijven de Windows Power shell-webtoegangs sessies actief, verbonden met doel computers, totdat de time-outperiode op de client is verstreken. De sessie wordt verbroken na de standaard waarde van 20 minuten of na de time-outperiode die is opgegeven door de Gateway beheerder, afhankelijk van wat korter is.

Als op de gateway server Windows Server 2012 R2 wordt uitgevoerd, kunnen gebruikers met Windows Power shell-webtoegang op een later tijdstip opnieuw verbinding maken met opgeslagen sessies, maar als er bij netwerk fouten, niet-gepland afsluiten of andere fouten sessies worden verbroken, kunnen gebruikers opgeslagen sessies pas weer geven of herstellen nadat de time-outperiode die is opgegeven door de Gateway beheerder is verstreken.

## <a name="see-also"></a>Zie ook

[Windows Power shell-webtoegang installeren en gebruiken](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831611(v=ws.11))

[about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_Session_Configurations)

[Windows Power shell Web Access-cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
