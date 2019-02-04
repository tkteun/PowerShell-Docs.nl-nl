---
ms.date: 06/27/2017
keywords: PowerShell-cmdlet
title: Autorisatieregels en beveiligingsfuncties van Windows PowerShell-internettoegang
ms.openlocfilehash: c426b8cfb10829241ba244a5d840c91e1de9f66e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686416"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Autorisatieregels en beveiligingsfuncties van Windows PowerShell-internettoegang

Bijgewerkt: 24: juni 2013

Van toepassing op: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell-webtoegang in Windows Server 2012 R2 en Windows Server 2012 heeft een beperkend beveiligingsmodel. Gebruikers moeten expliciet toegang worden verleend voordat ze kunnen zich aanmelden bij de Windows PowerShell Web Access-gateway en het web gebaseerde Windows PowerShell-console gebruiken.

## <a name="configuring-authorization-rules-and-site-security"></a>Autorisatieregels en sitebeveiliging configureren

Nadat Windows PowerShell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, wordt gebruikers de aanmeldingspagina in een browser kunnen openen, maar ze pas aanmelden nadat de Windows PowerShell Web Access-beheerder gebruikers toegang expliciet verleent. 'Windows PowerShell Web Access'-toegangsbeheer wordt beheerd met behulp van de set Windows PowerShell-cmdlets die in de volgende tabel beschreven. Er is geen vergelijkbare grafische gebruikersinterface voor het toevoegen of beheren van autorisatieregels.
Zie [Windows PowerShell Web Access Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Beheerders kunnen definiëren `{0-n}` -verificatieregels voor Windows PowerShell-webtoegang. De standaardbeveiliging is beperkend, niet toelatend. Als er geen verificatieregels zijn, heeft geen enkele gebruiker toegang tot iets.

[Add-PswaAuthorizationRule](/powershell/module/powershellwebaccess/add-pswaauthorizationrule?view=winserver2012r2-ps) en [Test-PswaAuthorizationRule](/powershell/module/powershellwebaccess/test-pswaauthorizationrule?view=winserver2012r2-ps) in Windows Server 2012 R2 bevatten de parameter Credential waarmee u kunt toevoegen en autorisatieregels van Windows PowerShell-internettoegang vanaf een externe testen computer, of uit binnen een actieve sessie van de Windows PowerShell-webtoegang. Als kunt andere Windows PowerShell-cmdlets waarvoor de parameter Credential, u een PSCredential-object opgeven als de waarde van de parameter. Voer voor het maken van een PSCredential-object met de referenties die u wilt doorgeven aan een externe computer de [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) cmdlet.

Windows PowerShell Web Access-verificatieregels zijn regels die bepaalde verbindingen. Elke regel is een definitie van een toegestane verbinding tussen gebruikers, doelcomputers en bepaalde Windows PowerShell [sessieconfiguraties](/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1) (ook wel eindpunten of _runspaces_) op opgegeven doelcomputers.
Voor een uitleg op **runspaces** Zie [begin gebruik van PowerShell Runspaces](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> Voor een gebruiker hoeft slechts één regel waar te zijn om ervoor te zorgen dat hij of zij toegang krijgt. Als een gebruiker toegang tot een computer met volledige taaltoegang of alleen toegang tot Windows PowerShell-cmdlets voor extern beheer, van de webconsole krijgt, kunt de gebruiker aanmelden (of hop) op andere computers die zijn verbonden met de eerste doelcomputer. Er is de veiligste manier om Windows PowerShell-webtoegang configureren zodat gebruikers alleen toegang tot beperkte sessieconfiguraties waarmee ze specifieke taken die ze normaal gesproken nodig hebben om uit te voeren op afstand.

De cmdlets waarnaar wordt verwezen in [Windows PowerShell Web Access Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps) toestaan om te maken van een reeks toegangsregels die worden gebruikt voor het autoriseren van een gebruiker op de Windows PowerShell Web Access-gateway. De regels verschillen van de toegangsbeheerlijsten (ACL’s) op de doelcomputer en bieden een extra beveiligingslaag voor internettoegang. Meer informatie over beveiliging vindt u in het volgende gedeelte.

Als gebruikers niet een van de voorgaande beveiligingslagen worden doorgegeven, ontvangen ze een algemeen 'toegang geweigerd'-bericht in hun browservensters. Hoewel beveiligingsgegevens worden geregistreerd op de gatewayserver, zien eindgebruikers geen informatie over hoeveel beveiligingslagen ze zijn gepasseerd of op welke laag de aanmeldings- of verificatiefout is opgetreden.

Zie voor meer informatie over het configureren van autorisatieregels [autorisatieregels configureren](#configuring-authorization-rules-and-site-security) in dit onderwerp.

### <a name="security"></a>Beveiliging

Het beveiligingsmodel van Windows PowerShell-webtoegang bevinden zich vier lagen tussen een eindgebruiker van de webconsole en een doelcomputer. Windows PowerShell Web Access-beheerders kunnen beveiligingslagen toevoegen via aanvullende configuratie in de IIS-beheerconsole. Zie voor meer informatie over het beveiligen van websites in de IIS-beheerconsole, [Configure Web Server Security (IIS7)](https://technet.microsoft.com/library/cc731278).

Voor meer informatie over IIS best practices en voorkomen van denial-of-service-aanvallen, Zie [Best Practices voor om te voorkomen dat DoS/tot denial of Service-aanvallen](https://technet.microsoft.com/library/cc750213).
Een beheerder kan ook kopen en aanvullende retail verificatiesoftware installeren.

In de volgende tabel worden de vier beveiligingslagen tussen eindgebruikers en doelcomputers beschreven.

|Niveau|Laag|
|-|-|
|1|[IIS web server security-functies](#iis-web-server-security-features)|
|2|[Windows powershell web access op formulieren gebaseerde gatewayverificatie](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[Windows powershell web access-autorisatieregels](#windows-powershell-web-access-authorization-rules)|
|4|[verificatie en autorisatie regels als doel](#target-authentication-and-authorization-rules)|

Gedetailleerde informatie over elke laag kan worden gevonden in de volgende rubrieken:

#### <a name="iis-web-server-security-features"></a>Beveiligingsfuncties voor IIS-webserver

Gebruikers van Windows PowerShell-webtoegang moeten altijd een gebruikersnaam en wachtwoord voor het verifiëren van hun accounts op de gateway opgeven. Echter dat Windows PowerShell-webtoegang beheerders ook verificatie van clientcertificaten desgewenst kunnen inschakelen of uitschakelen, Zie [installeren en gebruiken van windows powershell-webtoegang](install-and-use-windows-powershell-web-access.md) om in te schakelen van een testcertificaat en hoger, het configureren van een legitiem certificaat).

De optionele functie voor clientcertificaten vereist dat eindgebruikers beschikken over een geldig clientcertificaat naast hun gebruikersnaam en wachtwoord en maakt deel uit van de webserverconfiguratie (IIS). Als de clientcertificaatlaag is ingeschakeld, vraagt de aanmeldingspagina van Windows PowerShell-webtoegang gebruikers een geldig certificaat voordat hun aanmeldingsreferenties worden geëvalueerd. Bij verificatie van clientcertificaten wordt het clientcertificaat automatisch gecontroleerd. Als een geldig certificaat niet wordt gevonden, geeft de Windows PowerShell-webtoegang gebruikers, zodat ze het certificaat kunnen verstrekken. Als een geldig clientcertificaat wordt gevonden, wordt de aanmeldingspagina voor gebruikers voor hun gebruikersnamen en wachtwoorden in Windows PowerShell-webtoegang geopend.

Dit is een voorbeeld van aanvullende beveiligingsinstellingen die worden aangeboden via IIS-webserver. Zie voor meer informatie over andere IIS-beveiligingsfuncties [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Windows PowerShell-webtoegang op formulieren gebaseerde gatewayverificatie

De aanmeldingspagina van Windows PowerShell-webtoegang vereist een set referenties (gebruikersnaam en wachtwoord) en biedt gebruikers de mogelijkheid andere referenties voor de doelcomputer op te geven.
Als de gebruiker geen alternatieve referenties opgeeft, worden de primaire gebruikersnaam en het primaire wachtwoord die worden gebruikt om verbinding te maken met de gateway, ook gebruikt om verbinding te maken met de doelcomputer.

De vereiste referenties zijn geverifieerd op de Windows PowerShell Web Access-gateway. Deze referenties moeten geldige gebruikersaccounts op een van beide de lokale Windows PowerShell-webtoegang gatewayserver of in Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Autorisatieregels voor Windows PowerShell-webtoegang

Nadat een gebruiker is geverifieerd op de gateway, controleert Windows PowerShell-webtoegang autorisatieregels om te controleren of de gebruiker toegang tot de gevraagde doelcomputer heeft. Na een geslaagde autorisatie worden van de gebruiker referenties doorgegeven aan de doelcomputer.

Deze regels worden pas geëvalueerd nadat een gebruiker is geverifieerd door de gateway en voordat een gebruiker kan worden geverifieerd op een doelcomputer.

#### <a name="target-authentication-and-authorization-rules"></a>Verificatie- en autorisatieregels van de doelcomputer

De laatste beveiligingslaag voor Windows PowerShell-webtoegang is het doel van computer-beveiligingsconfiguratie. Gebruikers moeten de juiste toegangsrechten op de doelcomputer en ook in de Windows PowerShell Web Access-autorisatieregels geconfigureerd om uit te voeren van een Windows PowerShell web-console op basis van die van invloed op een doelcomputer via Windows PowerShell-webtoegang hebben.

Deze laag biedt dezelfde beveiligingsmechanismen die verbindingspogingen evalueren als gebruikers proberen te maken van een externe Windows PowerShell-sessie met een doelcomputer uit in Windows PowerShell door uit te voeren de [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) of [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession) cmdlets.

Standaard Windows PowerShell-webtoegang maakt gebruik van de primaire gebruikersnaam en het wachtwoord voor verificatie op zowel de gateway en de doelcomputer. Het web gebaseerde aanmeldingspagina, in een sectie met de titel **optionele verbindingsinstellingen**, biedt het gebruikers de mogelijkheid om andere referenties voor de doelcomputer op te geven als ze vereist zijn. Als de gebruiker geen alternatieve referenties opgeeft, worden de primaire gebruikersnaam en het primaire wachtwoord die worden gebruikt om verbinding te maken met de gateway, ook gebruikt om verbinding te maken met de doelcomputer.

Autorisatieregels kunnen worden gebruikt om gebruikers toegang te verlenen tot een bepaalde sessieconfiguratie. U kunt maken _beperkte runspaces_ of sessieconfiguraties voor Windows PowerShell-webtoegang, en bepaalde gebruikers verbinding maken met alleen specifieke sessieconfiguraties wanneer ze zich aanmelden bij Windows PowerShell-webtoegang. U kunt toegangsbeheerlijsten (ACL's) gebruiken om te bepalen welke gebruikers toegang hebben tot specifieke eindpunten en de toegang tot het eindpunt voor specifieke gebruikers verder beperken met behulp van de autorisatieregels die in dit gedeelte worden beschreven. Zie voor meer informatie over beperkte runspaces [het maken van een beperkte runspace](https://msdn.microsoft.com/library/dn614668).

### <a name="configuring-authorization-rules"></a>Autorisatieregels configureren

Beheerders willen waarschijnlijk dezelfde autorisatieregel voor Windows PowerShell Web Access-gebruikers die al is gedefinieerd in hun omgeving voor extern beheer van Windows PowerShell. In de eerste procedure in dit gedeelte wordt beschreven hoe u een veilige autorisatieregel toevoegt waarmee toegang wordt verleend aan één gebruiker die zich aanmeldt om één computer te beheren en binnen één sessieconfiguratie. In de tweede procedure wordt beschreven hoe u een autorisatieregel verwijdert die niet meer nodig is.

Als u van plan bent aangepaste sessieconfiguraties gebruiken waarmee specifieke gebruikers kunnen werken binnen beperkte runspaces in Windows PowerShell-webtoegang, maakt u uw aangepaste sessieconfiguraties voordat u autorisatieregels die ernaar verwijzen. U kunt de Windows PowerShell Web Access cmdlets niet gebruiken voor aangepaste sessieconfiguraties maken. Zie voor meer informatie over het maken van aangepaste sessieconfiguraties [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Windows PowerShell Web Access cmdlets ondersteunen één jokerteken, een sterretje ( \* ). Jokertekens binnen tekenreeksen worden niet ondersteund. Gebruik één sterretje per eigenschap (gebruikers, computers of sessieconfiguraties).

> [!NOTE]
> Voor meer manieren waarop u autorisatieregels kunt gebruiken voor toegang verlenen aan gebruikers en voor het beveiligen van de Windows PowerShell Web Access-omgeving, [andere voorbeelden van scenario autorisatie](#other-authorization-rule-scenario-examples) in dit onderwerp.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Een beperkende autorisatieregel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

   - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.

   - Op de Windows **Start** met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als Administrator uitvoeren**.

2. **Optionele stap** voor het beperken van toegang voor gebruikers met behulp van sessieconfiguraties:

   Controleer of de sessieconfiguraties die u wilt gebruiken, al bestaan in uw regels.

   Als ze zijn nog geen is gemaakt, gebruikt u instructies voor het maken van sessieconfiguraties in [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Deze autorisatieregel verleent een bepaalde gebruikerstoegang tot een computer op het netwerk waartoe ze gewoonlijk toegang hebben, met toegang tot een bepaalde sessieconfiguratie die is afgestemd op de gebruiker '™ s typische scripting en cmdlet-behoeften. Typ het volgende en druk vervolgens op **Enter**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - In het volgende voorbeeld wordt een gebruiker met de naam _JSmith_ in de _Contoso_ domein krijgt toegangsrechten voor het beheren van de computer _Contoso_214_, en de sessieconfiguratie van een met de naam gebruiken _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Controleer of dat de regel is gemaakt door de **Get-PswaAuthorizationRule** -cmdlet of `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`.
   Voorbeeld: `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Een autorisatieregel verwijderen

1. Als een Windows PowerShell-sessie nog niet is geopend, raadpleegt u stap 1 van [om toe te voegen een beperkende autorisatieregel](#to-add-a-restrictive-authorization-rule) in deze sectie.

2. Typ het volgende en druk vervolgens op **Enter**, waarbij *regel-ID* vertegenwoordigt de unieke id van de regel die u wilt verwijderen.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Als u de id van de regel die u wilt verwijderen niet kent maar wel de beschrijvende naam, kunt u de naam van de regel doorgeven aan de cmdlet `Remove-PswaAuthorizationRule` om de regel te verwijderen, zoals in het volgende voorbeeld:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
   ```

> [!NOTE]
> U wordt niet gevraagd om te bevestigen of u wilt verwijderen van de opgegeven autorisatieregel; de regel wordt verwijderd wanneer u op de toets **Enter**. Wees er zeker van dat u de autorisatieregel wilt verwijderen voordat u de cmdlet `Remove-PswaAuthorizationRule` uitvoert.

#### <a name="other-authorization-rule-scenario-examples"></a>Andere voorbeeldscenario’s met autorisatieregels

Elke Windows PowerShell-sessie gebruikt een sessieconfiguratie; Als deze niet voor een sessie opgegeven is, Windows PowerShell maakt gebruik van de standaard ingebouwde Windows PowerShell, sessieconfiguratie genaamd Microsoft.PowerShell. De standaardsessieconfiguratie bevat alle cmdlets die beschikbaar zijn op een computer. Beheerders kunnen de toegang tot alle computers beperken door een sessieconfiguratie met een beperkte runspace (een beperkt aantal cmdlets en taken die eindgebruikers kunnen uitvoeren) te definiëren. Een gebruiker die toegang tot een computer met volledige taaltoegang of alleen de Windows PowerShell extern beheer-cmdlets hebben kunt verbinden met andere computers die zijn verbonden met de eerste computer. Een beperkte runspace te definiëren kan voorkomen dat gebruikers toegang krijgen tot andere computers vanuit hun toegestane Windows PowerShell-runspace en verbetert de beveiliging van uw Windows PowerShell Web Access-omgeving. De sessieconfiguratie kan (via Groepsbeleid) worden gedistribueerd naar alle computers die beheerders toegankelijk willen maken via Windows PowerShell-webtoegang. Zie voor meer informatie over sessieconfiguraties [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx). Hier volgen enkele voorbeelden van dit scenario.

- Een beheerder maakt een eindpunt met de naam **Pswaeindpunt**, met een beperkte runspace. Vervolgens, de beheerder maakt een regel, `*,*,PswaEndpoint`, en distribueert het eindpunt naar andere computers. De regel verleent alle gebruikers toegang krijgen tot alle computers met het eindpunt **Pswaeindpunt**.
  Als dit de enige autorisatieregel is die is gedefinieerd in de regelset, zijn computers zonder dat eindpunt niet toegankelijk.

- De beheerder wordt gemaakt van een eindpunt met een beperkte runspace met de naam **Pswaeindpunt**, en wil de toegang beperken tot specifieke gebruikers. De beheerder maakt een groep gebruikers genaamd **Level1Support**, en definieert de volgende regel: **Level1Support,\*, Pswaeindpunt**. De regel verleent alle gebruikers in de groep **Level1Support** toegang tot alle computers met de **Pswaeindpunt** configuratie. Op vergelijkbare wijze kan de toegang worden beperkt tot een specifieke set computers.

- Sommige beheerders bieden bepaalde gebruikers uitgebreidere toegang dan andere. Een beheerder maakt bijvoorbeeld twee gebruikersgroepen, **beheerders** en **basisondersteuning**. De beheerder maakt ook een eindpunt met een beperkte runspace met de naam **Pswaeindpunt**, en definieert de volgende twee regels: **Beheerders,\*,\***  en **basisondersteuning,\*, Pswaeindpunt**. De eerste regel biedt alle gebruikers in de **Admin** groepstoegang tot alle computers en de tweede regel biedt alle gebruikers in de **basisondersteuning** groep alleen toegang tot computers met  **Pswaeindpunt**.

- Een beheerder heeft een besloten testomgeving ingesteld en wil alle geautoriseerde netwerkgebruikers toegang geven tot alle computers in het netwerk waartoe ze gewoonlijk toegang hebben, met toegang tot alle sessieconfiguraties waartoe ze gewoonlijk toegang hebben. Omdat dit een besloten testomgeving is, maakt de beheerder een autorisatieregel die niet veilig is. -De beheerder voert de cmdlet `Add-PswaAuthorizationRule * * *`, waarin het jokerteken **\*** om weer te geven van alle gebruikers, alle computers en alle configuraties. -Met deze regel is het equivalent van de volgende opties: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Deze regel wordt niet aangeraden in een beveiligde omgeving en omzeilt de beveiligingslaag autorisatie van de beveiliging van Windows PowerShell-webtoegang.

- Een beheerder moet gebruikers toestaan verbinding te maken met doelcomputers in een omgeving met zowel werkgroepen als domeinen, waarbij werkgroepcomputers af en toe worden gebruikt om verbinding te maken met doelcomputers in domeinen en computers in domeinen af en toe worden gebruikt om verbinding te maken met doelcomputers in werkgroepen. De beheerder heeft een gatewayserver *PswaServer*, in een werkgroep en de doelcomputer *srv1.contoso.com* zich in een domein. Gebruiker *Chris* is een geautoriseerde lokale gebruiker op zowel de gatewayserver van de werkgroep als de doelcomputer. Zijn gebruikersnaam op de werkgroepserver is *chrisLocal*; en zijn gebruikersnaam op de doelcomputer is *contoso\\chris*. De beheerder verleent Chris toegang tot srv1.contoso.com door de volgende regel toe te voegen.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Het vorige Regelvoorbeeld wordt voor Chris verificatie op de gatewayserver en vervolgens autoriseert zijn toegang tot *srv1*. Op de aanmeldingspagina moet Chris een tweede set referenties in opgeven. de **optionele verbindingsinstellingen** gebied (*contoso\\chris*). De gateway-server gebruikt de aanvullende set referenties om hem te verifiëren op de doelcomputer *srv1.contoso.com*.

Windows PowerShell-webtoegang stelt in het voorgaande scenario kan een geslaagde verbinding met de doelcomputer nadat het volgende geslaagd en is toegestaan door ten minste één autorisatieregel is.

1. Verificatie op de gatewayserver werkgroep door de naam van een gebruiker toe te voegen in de indeling *servernaam*\\*gebruikersnaam* aan de autorisatieregel

2. Verificatie op de doelcomputer met behulp van alternatieve referenties die zijn opgegeven op de pagina aanmelden de **optionele verbindingsinstellingen** gebied

   > [!NOTE]
   > Als de gateway en de doelcomputer zich in verschillende werkgroepen of domeinen bevinden, moet een vertrouwensrelatie tussen de twee werkgroepcomputers, de twee domeinen of de werkgroep en het domein worden ingesteld. Deze relatie kan niet worden geconfigureerd met behulp van Windows PowerShell Web Access cmdlets voor autorisatieregels. Autorisatieregels definiëren geen vertrouwensrelatie tussen computers. Ze kunnen enkel gebruikers toestaan verbinding te maken met specifieke doelcomputers en sessieconfiguraties. Zie voor meer informatie over het configureren van een vertrouwensrelatie tussen verschillende domeinen [Creating Domain and Forest Trusts](https://technet.microsoft.com/library/cc794775.aspx).
   > Zie voor meer informatie over hoe u werkgroepcomputers toevoegt aan een lijst met vertrouwde hosts, [extern beheer met Serverbeheer](https://technet.microsoft.com/library/dd759202.aspx).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Eén set autorisatieregels gebruiken voor meerdere sites

Autorisatieregels worden opgeslagen in een XML-bestand. De naam van het pad van het XML-bestand is standaard `$env:windir\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

Het pad naar het XML-bestand met autorisatieregels wordt opgeslagen in de **powwa.config** -bestand, dat is gevonden in `$env:windir\Web\PowershellWebAccess\data`. De beheerder heeft de flexibiliteit om te wijzigen van de verwijzing naar het standaardpad in **powwa.config** op basis van voorkeuren of vereisten. De beheerder om de locatie van het bestand te wijzigen zodat kunt meerdere Windows PowerShell-webtoegang gateways dezelfde autorisatieregels gebruiken, als een dergelijke configuratie vereist is.

## <a name="session-management"></a>Sessiebeheer

Standaard beperkt Windows PowerShell-webtoegang een gebruiker tot drie sessies tegelijk. U kunt de webtoepassing bewerken **web.config** bestand in IIS-beheer voor de ondersteuning van een ander aantal sessies per gebruiker. Het pad naar de **web.config** bestand `$env:windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

IIS-webserver is standaard geconfigureerd voor het opnieuw opstarten van de groep van toepassingen als alle instellingen worden bewerkt. Bijvoorbeeld, de groep van toepassingen opnieuw wordt gestart als wijzigingen worden aangebracht in de **web.config** bestand. > omdat **Windows PowerShell-webtoegang** maakt gebruik van de sessiestatus in het geheugen, > gebruikers die zijn aangemeld bij **Windows PowerShell-webtoegang** sessies hun sessie wanneer de groep van toepassingen opnieuw wordt opgestart kwijt.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Standaardparameters instellen op de aanmeldingspagina

Als uw Windows PowerShell Web Access-gateway op Windows Server 2012 R2 wordt uitgevoerd, kunt u de standaardwaarden voor de instellingen die worden weergegeven op de aanmeldingspagina van Windows PowerShell-webtoegang configureren. U kunt waarden configureren in de **web.config** -bestand dat wordt beschreven in de vorige paragraaf. Standaardwaarden voor de instellingen van de aanmeldingspagina vindt u in de **appSettings** sectie van het bestand web.config; Hier volgt een voorbeeld van de **appSettings** sectie. Geldige waarden voor veel van deze instellingen zijn hetzelfde als die voor de bijbehorende parameters van de [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet in Windows PowerShell.

Bijvoorbeeld, de `defaultApplicationName` sleutel, zoals wordt weergegeven in het volgende codeblok, is de waarde van de **$PSSessionApplicationName** voorkeursvariabele op de doelcomputer.

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

Er is een time-out opgetreden voor de Windows PowerShell-webtoegang sessies. Een time-outbericht wordt voor aangemelde gebruikers in Windows PowerShell-webtoegang die worden uitgevoerd op Windows Server 2012, weergegeven na 15 minuten van inactiviteit in de sessie. Als de gebruiker niet reageert binnen vijf minuten nadat het time-outbericht wordt weergegeven, wordt de sessie beëindigd en wordt de gebruiker afgemeld. U kunt de time-outperiode voor sessies wijzigen in de website-instellingen in IIS-beheer.

In Windows PowerShell-webtoegang uitgevoerd op Windows Server 2012 R2, sessies time-out, standaard na 20 minuten van inactiviteit. Als gebruikers van sessies in de webconsole zijn verbroken vanwege netwerkfouten of andere niet-gepland afsluiten of fouten, en niet omdat ze de sessie zelf hebt gesloten, de Windows PowerShell Web Access-sessies worden uitgevoerd, die zijn verbonden met doelcomputers, totdat de time-outperiode op de client-side-systeem. De sessie wordt beëindigd na de standaardperiode van 20 minuten of na de time-outperiode die is opgegeven door de beheerder van de gateway, afhankelijk van welke periode korter is.

Als de gateway-server wordt uitgevoerd Windows Server 2012 R2, Windows PowerShell Web Access kunnen gebruikers opnieuw verbinding met maken opgeslagen sessies op een later tijdstip, maar als netwerkfouten, niet-gepland afsluiten of andere fouten sessies verbreken, gebruikers niet zien of opnieuw verbinding maken met opgeslagen sessies pas na de time-outperiode die is opgegeven door de beheerder is opgegeven.

## <a name="see-also"></a>Zie ook

[Installeren en gebruiken van Windows PowerShell-internettoegang](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Windows PowerShell Web Access Cmdlets](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps)
