---
ms.date: 2017-06-27
keywords: PowerShell-cmdlet
title: Autorisatieregels en beveiligingsfuncties van Windows PowerShell-internettoegang
ms.openlocfilehash: 19e4aa1bb55178ec2634af0771afe2db5db3423c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Autorisatieregels en beveiligingsfuncties van Windows PowerShell-internettoegang

Bijgewerkte: 24 juni 2013

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

Windows PowerShell Web Access in Windows Server 2012 R2 en Windows Server 2012 heeft een beperkend beveiligingsmodel.
Gebruikers moeten expliciet toegang worden verleend voordat ze kunnen zich bij de Windows PowerShell Web Access-gateway aanmelden en de Windows PowerShell webgebaseerde console gebruiken.

## <a name="configuring-authorization-rules-and-site-security"></a>Autorisatieregels en sitebeveiliging configureren

Nadat Windows PowerShell-webtoegang is geïnstalleerd en de gateway is geconfigureerd, kunnen gebruikers de aanmeldingspagina openen in een browser, maar ze zich niet aanmelden totdat de Windows PowerShell Web Access-beheerder gebruikers toegang expliciet verleent.
'Windows PowerShell Web Access' toegangsbeheer wordt beheerd met behulp van de set Windows PowerShell-cmdlets in de volgende tabel beschreven.
Er is geen vergelijkbare grafische gebruikersinterface voor het toevoegen of beheren van autorisatieregels.
Zie [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md).

Beheerders kunnen definiëren 0 -*n* verificatieregels voor Windows PowerShell Web Access.
De standaardbeveiliging is beperkend, niet toelatend. Als er geen verificatieregels zijn, heeft geen enkele gebruiker toegang tot iets.

[Add-PswaAuthorizationRule](cmdlets/add-pswaauthorizationrule.md) en [Test-PswaAuthorizationRule](cmdlets/test-pswaauthorizationrule.md) in Windows Server 2012 R2 bevatten de parameter Credential waarmee u toevoegen en testen van Windows PowerShell-webtoegang autorisatieregels van een externe computer, of uit binnen een actieve sessie voor Windows PowerShell Web Access.
Als kunt andere Windows PowerShell-cmdlets die u een referentieparameter hebt u een PSCredential-object opgeven als de waarde van de parameter.
U maakt een PSCredential-object met de referenties die u wilt doorgeven aan een externe computer, voeren de [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.

Windows PowerShell-webtoegang verificatieregels zijn regels van de goedgekeurde IP-adressen.
Elke regel is een definitie van een toegestane verbinding tussen gebruikers, doelcomputers en bepaalde Windows-PowerShellÂ [sessieconfiguraties](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) (ook wel eindpunten of _runspaces_) op opgegeven doelcomputers.
Voor een uitleg op **runspaces** Zie [begin gebruik van PowerShell Runspaces](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> **Opmerking over beveiliging**
>
> Voor een gebruiker hoeft slechts één regel waar te zijn om ervoor te zorgen dat hij of zij toegang krijgt.
Als een gebruiker toegang tot een computer met volledige taaltoegang of alleen toegang tot Windows PowerShell cmdlets voor extern beheer van de webconsole krijgt, kunt de gebruiker aanmelden (of springen) naar andere computers die zijn verbonden met de eerste doelcomputer.
De veiligste manier voor het configureren van Windows PowerShell-webtoegang is dat gebruikers alleen toegang tot beperkte sessieconfiguraties waarmee ze specifieke taken die ze normaal op afstand moeten uitvoeren.

De cmdlets waarnaar wordt verwezen in [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) toestaan voor het maken van een reeks toegangsregels die worden gebruikt voor het autoriseren van een gebruiker op de Windows PowerShell Web Access-gateway.
De regels verschillen van de toegangsbeheerlijsten (ACL’s) op de doelcomputer en bieden een extra beveiligingslaag voor internettoegang.
Meer informatie over beveiliging vindt u in het volgende gedeelte.

Als gebruikers niet een van de voorgaande beveiligingslagen doorgeven, ontvangen ze een algemeen 'toegang geweigerd'-bericht in hun browservensters.
Hoewel beveiligingsgegevens worden geregistreerd op de gatewayserver, zien eindgebruikers geen informatie over hoeveel beveiligingslagen ze zijn gepasseerd of op welke laag de aanmeldings- of verificatiefout is opgetreden.

Zie voor meer informatie over het configureren van autorisatieregels [autorisatieregels configureren](#configuring-authorization-rules-and-site-security) in dit onderwerp.

### <a name="security"></a>Beveiliging

Het beveiligingsmodel van Windows PowerShell-internettoegang heeft vier lagen tussen een eindgebruiker van de webconsole en een doelcomputer.
Windows PowerShell Web Access-beheerders kunnen beveiligingslagen toevoegen via aanvullende configuratie in de console IIS-beheer.
Zie voor meer informatie over het beveiligen van websites in IIS-beheerconsole, [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278).
Voor meer informatie over IIS best practices en het voorkomen van denial of service-aanvallen, Zie [Best Practices voor voorkomen van DoS/tot Denial Service-aanvallen](https://technet.microsoft.com/library/cc750213).
Een beheerder kan ook kopen en installeren van extra retail verificatiesoftware.

In de volgende tabel worden de vier beveiligingslagen tussen eindgebruikers en doelcomputers beschreven.

|Niveau|Laag|
|-|-|
|1|[beveiligingsfuncties voor IIS-webservers](#iis-web-server-security-features)|
|2|[Windows powershell web access op formulieren gebaseerde gatewayverificatie](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[Windows powershell web access-autorisatieregels](#windows-powershell-web-access-authorization-rules)|
|4|[doel-verificatie en autorisatie-regels](#target-authentication-and-authorization-rules)|

Onder de volgende rubrieken vindt u gedetailleerde informatie over elke laag:

#### <a name="iis-web-server-security-features"></a>Beveiligingsfuncties van IIS-webserver

Gebruikers van Windows PowerShell-webtoegang moeten altijd een gebruikersnaam en wachtwoord voor hun account op de gateway verificatie opgeven.
Echter dat Windows PowerShell-webtoegang beheerders ook verificatie van clientcertificaten desgewenst kunnen inschakelen of uitschakelen, Zie [installeren en gebruiken van windows powershell-webtoegang](install-and-use-windows-powershell-web-access.md) een testcertificaat inschakelen en hoger, het configureren van een legitiem certificaat).

De optionele functie voor clientcertificaten vereist dat eindgebruikers beschikken over een geldig clientcertificaat naast hun gebruikersnaam en wachtwoord en maakt deel uit van de webserverconfiguratie (IIS).
Als de clientcertificaatlaag is ingeschakeld, vraagt de aanmeldingspagina van Windows PowerShell-webtoegang gebruikers een geldig certificaat voordat hun aanmeldingsreferenties worden geëvalueerd.
Bij verificatie van clientcertificaten wordt het clientcertificaat automatisch gecontroleerd.
Als een geldig certificaat niet wordt gevonden, informeert Windows PowerShell-webtoegang gebruikers, zodat ze voor het certificaat leveren kunnen.
Als een geldig clientcertificaat wordt gevonden, wordt de aanmeldingspagina voor gebruikers om toegang te bieden hun gebruikersnamen en wachtwoorden in Windows PowerShell Web Access geopend.

Dit is een voorbeeld van aanvullende beveiligingsinstellingen die worden aangeboden via IIS-webserver.
Zie voor meer informatie over andere IIS-beveiligingsfuncties [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278)

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Verificatie van Windows PowerShell Web Access-gateway op basis van formulieren

De aanmeldingspagina van Windows PowerShell-webtoegang vereist een set referenties (gebruikersnaam en wachtwoord) en biedt gebruikers de mogelijkheid om andere referenties te bieden voor de doelcomputer.
Als de gebruiker geen alternatieve referenties opgeeft, worden de primaire gebruikersnaam en het primaire wachtwoord die worden gebruikt om verbinding te maken met de gateway, ook gebruikt om verbinding te maken met de doelcomputer.

De vereiste referenties worden geverifieerd op de Windows PowerShell Web Access-gateway.
Deze referenties moeten geldige gebruikersaccounts op de lokale Windows PowerShell Web Access-gatewayserver of in Active Directory zijn.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Autorisatieregels voor Windows PowerShell-webtoegang

Nadat een gebruiker is geverifieerd op de gateway, controleert Windows PowerShell-webtoegang autorisatieregels om te controleren of de gebruiker toegang tot de gevraagde doelcomputer heeft.
Na een geslaagde autorisatie worden referenties van de gebruiker doorgegeven aan de doelcomputer.

Deze regels worden pas geëvalueerd nadat een gebruiker is geverifieerd door de gateway en voordat een gebruiker kan worden geverifieerd op een doelcomputer.

#### <a name="target-authentication-and-authorization-rules"></a>Verificatie- en autorisatieregels van de doelcomputer

De laatste beveiligingslaag voor Windows PowerShell-internettoegang is de beveiligingsconfiguratie voor doel van het computer.
Gebruikers moeten de juiste toegangsrechten op de doelcomputer en ook in de Windows PowerShell Web Access-autorisatieregels geconfigureerd om uit te voeren van een Windows PowerShell-webconsole die van invloed op een doelcomputer via Windows PowerShell-webtoegang hebben.

Deze laag biedt dezelfde beveiligingsmechanismen die evalueren verbindingspogingen als gebruikers proberen een externe Windows PowerShell-sessie met een doelcomputer van Windows PowerShell maken door het uitvoeren van de [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Enter-PSSession) of [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/new-pssession) cmdlets.

Standaard gebruikt Windows PowerShell Web Access de primaire gebruikersnaam en het wachtwoord voor verificatie op de gateway en de doelcomputer.
Het web gebaseerde aanmeldingspagina, in de sectie **optionele verbindingsinstellingen**, biedt gebruikers de mogelijkheid om andere referenties te bieden voor de doelcomputer maken als ze vereist zijn.
Als de gebruiker geen alternatieve referenties opgeeft, worden ook de primaire gebruikersnaam en het wachtwoord die worden gebruikt voor het verbinding maken met de gateway gebruikt voor het verbinding maken met de doelcomputer.

Autorisatieregels kunnen worden gebruikt om gebruikers toegang te verlenen tot een bepaalde sessieconfiguratie.
U kunt maken _beperkte runspaces_ of sessieconfiguraties voor Windows PowerShell-webtoegang en bepaalde gebruikers verbinding maken met alleen specifieke sessieconfiguraties wanneer ze zich bij Windows PowerShell-internettoegang aanmelden toestaan.
U kunt toegangsbeheerlijsten (ACL's) gebruiken om te bepalen welke gebruikers toegang hebben tot specifieke eindpunten en toegang tot het eindpunt voor een specifieke groep gebruikers verder beperken via autorisatieregels die in deze sectie beschreven.
Zie voor meer informatie over beperkte runspaces [maken van een beperkte runspace](https://msdn.microsoft.com/en-us/library/dn614668).

### <a name="configuring-authorization-rules"></a>Autorisatieregels configureren

Beheerders willen waarschijnlijk dezelfde autorisatieregel voor Windows PowerShell Web Access-gebruikers die al is gedefinieerd in hun omgeving voor extern beheer van Windows PowerShell.
De eerste procedure in deze sectie wordt beschreven hoe een veilige autorisatieregel waarmee toegang wordt verleend aan één gebruiker, aanmelding bij één computer beheren en binnen één sessieconfiguratie toevoegen.
In de tweede procedure wordt beschreven hoe u een autorisatieregel verwijdert die niet meer nodig is.

Als u van plan bent aangepaste sessieconfiguraties gebruiken om specifieke gebruikers werken binnen beperkte runspaces in Windows PowerShell Web Access in staat, maakt u uw aangepaste sessieconfiguraties voordat u autorisatieregels die naar deze verwijzen toevoegt.
U kunt de Windows PowerShell Web Access cmdlets niet gebruiken aangepaste sessieconfiguraties maken.
Zie voor meer informatie over het maken van aangepaste sessieconfiguraties [about_Session_Configuration_Files](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files).

Windows PowerShell Web Access cmdlets ondersteunen één jokerteken, een sterretje ( \* ).
Jokertekens binnen tekenreeksen worden niet ondersteund. Gebruik één sterretje per eigenschap (gebruikers, computers of sessieconfiguraties).

> **Opmerking**
>
> Voor Zie voor meer manieren kunt u autorisatieregels toegang te verlenen aan gebruikers en de Windows PowerShell Web Access-omgeving te beveiligen [andere voorbeeldscenario's met autorisatieregels](#other-authorization-rule-scenario-examples) in dit onderwerp.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Een beperkende autorisatieregel toevoegen

1. Doe het volgende om een Windows PowerShell-sessie met verhoogde gebruikersrechten te openen.

    - Het Windows-bureaublad met de rechtermuisknop op **Windows PowerShell** op de taakbalk en klik vervolgens op **als Administrator uitvoeren**.

    - Windows **Start** scherm, met de rechtermuisknop op **Windows PowerShell** , en klik vervolgens op **als Administrator uitvoeren**.

2. **Optionele stap** voor het beperken van gebruikerstoegang met behulp van sessieconfiguraties:

    Controleren of de sessieconfiguraties die u wilt gebruiken, al in uw regels bestaan.
Als ze nog geen hebt is gemaakt, gebruikt u instructies voor het maken van sessieconfiguraties in [about_Session_Configuration_Files](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files).

3. Deze autorisatieregel verleent een bepaalde gebruikerstoegang tot een computer op het netwerk waartoe ze gewoonlijk toegang hebben, met toegang tot een bepaalde sessieconfiguratie die is afgestemd op de gebruiker '™ s typische scripting- en cmdlet-behoeften. Typ het volgende en druk vervolgens op **Enter**.

```powershell
Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
```

  - In het volgende voorbeeld wordt een gebruiker met de naam _JSmith_ in de _Contoso_ domein krijgt toegangsrechten voor het beheren van de computer _Contoso_214_, en een sessieconfiguratie genaamd gebruiken _NewAdminsOnly_.

```powershell
Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
```

4. Controleer of dat de regel is gemaakt door de **Get-PswaAuthorizationRule** -cmdlet of **Test-PswaAuthorizationRule - UserName &lt;domein\\gebruiker | computer\\ gebruiker&gt; - ComputerName** &lt;computer_name&gt;. Bijvoorbeeld: **Test-PswaAuthorizationRule - UserName Contoso\\JSmith - ComputerName Contoso_214**.

#### <a name="to-remove-an-authorization-rule"></a>Een autorisatieregel verwijderen

1. Als een Windows PowerShell-sessie nog niet is geopend, raadpleegt u stap 1 van [een beperkende autorisatieregel toevoegen](#to-add-a-restrictive-authorization-rule) in deze sectie.

2. Typ het volgende en druk vervolgens op **Enter**, waarbij *regel-ID* vertegenwoordigt de unieke id van de regel die u wilt verwijderen.

```powershell
Remove-PswaAuthorizationRule -ID <rule ID>
```

U kunt ook als u de ID-nummer niet kent maar wel de beschrijvende naam van de regel die u wilt verwijderen, u kunt de naam van de regel en doorgeven aan de `Remove-PswaAuthorizationRule` cmdlet om te verwijderen van de regel, zoals wordt weergegeven in het volgende voorbeeld: `Get-PswaAuthorizationRule -RuleName <rule-name> | Remove-PswaAuthorizationRule`.

>**Opmerking**:
>
>U wordt niet gevraagd te bevestigen of u wilt verwijderen van de opgegeven autorisatieregel; de regel wordt verwijderd wanneer u op **Enter**. Wees er zeker van dat u de autorisatieregel wilt verwijderen voordat u de cmdlet `Remove-PswaAuthorizationRule` uitvoert.

#### <a name="other-authorization-rule-scenario-examples"></a>Andere voorbeeldscenario’s met autorisatieregels

Elke Windows PowerShell-sessie gebruikt een sessieconfiguratie; Als er een is niet opgegeven voor een sessie, Windows PowerShell gebruikt het standaard ingebouwde Windows PowerShell, sessieconfiguratie genaamd Microsoft.PowerShell. De standaardsessieconfiguratie bevat alle cmdlets die beschikbaar zijn op een computer. Beheerders kunnen de toegang tot alle computers beperken door een sessieconfiguratie met een beperkte runspace (een beperkt aantal cmdlets en taken die eindgebruikers kunnen uitvoeren) te definiëren. Een gebruiker die toegang tot een computer met volledige taaltoegang of alleen de Windows PowerShell extern beheer-cmdlets kunt verbinden met andere computers die zijn verbonden met de eerste computer. Een beperkte runspace definiëren kunnen voorkomen dat gebruikers toegang krijgen tot andere computers vanuit hun toegestane Windows PowerShell-runspace en verbetert de beveiliging van uw Windows PowerShell Web Access-omgeving. De sessieconfiguratie kan (via Groepsbeleid) worden gedistribueerd naar alle computers die beheerders toegankelijk willen maken via Windows PowerShell-webtoegang. Zie voor meer informatie over sessieconfiguraties [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx).
Hier volgen enkele voorbeelden van dit scenario.

- Een beheerder maakt een eindpunt met de naam **Pswaeindpunt**, met een beperkte runspace. En vervolgens de beheerder een regel maakt  **\*,\*, Pswaeindpunt**, en distribueert het eindpunt naar andere computers. De regel verleent alle gebruikers toegang tot alle computers met het eindpunt **Pswaeindpunt**. Als dit de enige autorisatieregel is die is gedefinieerd in de regelset, zijn computers zonder dat eindpunt niet toegankelijk.

- De beheerder een eindpunt worden gemaakt met een beperkte runspace genaamd **Pswaeindpunt**, en wil de toegang beperken tot specifieke gebruikers. De beheerder maakt een groep gebruikers genaamd **Level1Support**, en definieert de volgende regel: **Level1Support,\*, Pswaeindpunt**. De regel verleent alle gebruikers in de groep **Level1Support** toegang tot alle computers met de **Pswaeindpunt** configuratie. Op vergelijkbare wijze kan de toegang worden beperkt tot een specifieke set computers.

- Sommige beheerders bieden bepaalde gebruikers uitgebreidere toegang dan andere. Een beheerder maakt bijvoorbeeld twee gebruikersgroepen, **Admins** en **basisondersteuning**. De beheerder maakt ook een eindpunt met een beperkte runspace genaamd **Pswaeindpunt**, en definieert de volgende twee regels: **beheerders,\*,\***  en  **Basisondersteuning,\*, Pswaeindpunt**. De eerste regel biedt alle gebruikers in de **Admin** groepstoegang tot alle computers en de tweede regel biedt alle gebruikers in de **basisondersteuning** groep alleen toegang tot computers met  **Pswaeindpunt**.

- Een beheerder heeft een besloten testomgeving ingesteld en wil alle geautoriseerde netwerkgebruikers toegang geven tot alle computers in het netwerk waartoe ze gewoonlijk toegang hebben, met toegang tot alle sessieconfiguraties waartoe ze gewoonlijk toegang hebben. Omdat dit een besloten testomgeving is, maakt de beheerder een autorisatieregel die niet veilig is.
  - De beheerder voert de cmdlet `Add-PswaAuthorizationRule * * *`, waarin het jokerteken  **\***  voor alle gebruikers alle computers en alle configuraties.
  - Deze regel komt overeen met het volgende: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  >**Opmerking**:
  >
  >Deze regel wordt niet aanbevolen in een beveiligde omgeving en omzeilt de beveiligingslaag autorisatie beveiliging van Windows PowerShell Web Access.

- Een beheerder moet gebruikers toestaan verbinding te maken met doelcomputers in een omgeving met zowel werkgroepen als domeinen, waarbij werkgroepcomputers af en toe worden gebruikt om verbinding te maken met doelcomputers in domeinen en computers in domeinen af en toe worden gebruikt om verbinding te maken met doelcomputers in werkgroepen. De beheerder heeft een gatewayserver *PswaServer*, in een werkgroep en de doelcomputer *srv1.contoso.com* zich in een domein. Gebruiker *Chris* is een geautoriseerde lokale gebruiker op zowel de gatewayserver werkgroep als de doelcomputer. Zijn gebruikersnaam op de werkgroepserver is *chrisLocal*; en zijn gebruikersnaam op de doelcomputer is *contoso\\chris*. De beheerder verleent Chris toegang tot srv1.contoso.com door de volgende regel toe te voegen.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Het vorige Regelvoorbeeld wordt voor Chris verificatie op de gatewayserver en dan toelaat zijn toegang tot *srv1*. Op de aanmeldingspagina moet Chris een tweede set referenties in opgeven. de **optionele verbindingsinstellingen** gebied (*contoso\\chris*). De gatewayserver gebruikt de aanvullende set referenties om hem te verifiëren op de doelcomputer *srv1.contoso.com*.

Windows PowerShell-webtoegang stelt u een verbinding met de doelcomputer nadat het volgende geslaagd en is toegestaan door ten minste één autorisatieregel is in het voorgaande scenario.

1. Verificatie op de gatewayserver werkgroep door de naam van een gebruiker toe te voegen in de notatie *servernaam*\\*gebruikersnaam* aan de autorisatieregel

2. Verificatie op de doelcomputer met behulp van alternatieve referenties op de aanmeldingspagina in de **optionele verbindingsinstellingen** gebied

  >**Opmerking**:
  >
  >Als de gateway en de doelcomputer zich in verschillende werkgroepen of domeinen bevinden, moet een vertrouwensrelatie tussen de twee werkgroepcomputers, de twee domeinen of de werkgroep en het domein worden ingesteld. Deze relatie kan niet worden geconfigureerd met behulp van Windows PowerShell Web Access cmdlets voor autorisatieregels. Autorisatieregels definiëren geen vertrouwensrelatie tussen computers. Ze kunnen enkel gebruikers toestaan verbinding te maken met specifieke doelcomputers en sessieconfiguraties. Zie voor meer informatie over het configureren van een vertrouwensrelatie tussen verschillende domeinen [Creating Domain and Forest Trusts](https://technet.microsoft.com/library/cc794775.aspx"). Zie voor meer informatie over hoe u werkgroepcomputers toevoegt aan een lijst met vertrouwde hosts, [extern beheer met Serverbeheer](https://technet.microsoft.com/library/dd759202.aspx)

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Eén set autorisatieregels gebruiken voor meerdere sites

Autorisatieregels worden opgeslagen in een XML-bestand. De naam van het pad van het XML-bestand is standaard _% windir %\\Web\\PowershellWebAccess\\gegevens\\AuthorizationRules.xml_.

Het pad naar het XML-bestand met autorisatieregels wordt opgeslagen in de **powwa.config** bestand, dat is gevonden in _% windir %\\Web\\PowershellWebAccess\\gegevens_. De beheerder heeft de flexibiliteit de verwijzing naar het standaardpad in wijzigen **powwa.config** op basis van voorkeuren of vereisten. De beheerder om de locatie van het bestand te wijzigen zodat kiest, kunnen meerdere Windows PowerShell-webtoegang gateways dezelfde autorisatieregels gebruiken indien zo'n configuratie gewenst is.

## <a name="session-management"></a>Sessiebeheer

Standaard beperkt de Windows PowerShell-webtoegang een gebruiker tot drie sessies tegelijk. U kunt de webtoepassing bewerken **web.config** bestand in IIS-beheer voor de ondersteuning van een verschillend aantal sessies per gebruiker.
Het pad naar de **web.config** bestand is _$Env: Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config_.

IIS-webserver is standaard geconfigureerd om opnieuw te starten van de groep van toepassingen als u alle instellingen worden bewerkt. Bijvoorbeeld, de groep van toepassingen opnieuw wordt gestart als er wijzigingen zijn aangebracht aan de **web.config** bestand.
>Omdat **Windows PowerShell-webtoegang** de sessiestatus uit het geheugen gebruikt, raken gebruikers aangemeld bij **Windows PowerShell-webtoegang** sessies hun sessie wanneer de groep van toepassingen opnieuw wordt opgestart kwijt.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Standaardparameters instellen op de aanmeldingspagina

Als uw Windows PowerShell Web Access-gateway op Windows Server 2012 R2 wordt uitgevoerd, kunt u de standaardwaarden voor de instellingen die worden weergegeven op de aanmeldingspagina van Windows PowerShell-webtoegang configureren. U kunt waarden configureren in de **web.config** -bestand dat wordt beschreven in de vorige alinea. Standaardwaarden voor de instellingen van de aanmeldingspagina zijn gevonden in de **appSettings** sectie van het bestand web.config; Hieronder volgt een voorbeeld van de **appSettings** sectie. Geldige waarden voor veel van deze instellingen zijn hetzelfde als die voor de overeenkomstige parameters van de [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet in Windows PowerShell.
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

Er is een time-out opgetreden voor de Windows PowerShell Web Access-sessies. In Windows PowerShell-webtoegang op Windows Server 2012 wordt uitgevoerd, een time-outbericht weergegeven aan gebruikers aangemeld na 15 minuten van inactiviteit in de sessie. Als de gebruiker niet reageert binnen vijf minuten nadat het time-outbericht wordt weergegeven, wordt de sessie beëindigd en wordt de gebruiker afgemeld. U kunt de time-outperiode voor sessies wijzigen in de website-instellingen in IIS-beheer.

In Windows PowerShell Web Access uitgevoerd op Windows Server 2012 R2, time-outwaarde voor sessies, standaard na 20 minuten van inactiviteit. Als gebruikers verbinding met sessies in de webconsole wordt verbroken vanwege netwerkfouten of andere niet-gepland afsluiten of fouten, en niet omdat ze de sessie zelf hebt gesloten, blijven de Windows PowerShell Web Access-sessies actief, verbonden met doelcomputers, totdat de time-outperiode op de client is verstreken. De sessie wordt beëindigd na de standaardperiode van 20 minuten of na de time-outperiode die is opgegeven door de beheerder van de gateway, afhankelijk van welke periode korter is.

Als de gateway-server wordt uitgevoerd van Windows Server 2012 R2, Windows PowerShell Web Access kunnen gebruikers opnieuw verbinding met maken opgeslagen sessies op een later tijdstip, maar wanneer netwerkfouten, niet-gepland afsluiten of andere fouten sessies loskoppelt, gebruikers niet zien of opnieuw verbinding maken met opgeslagen sessies pas na de time-outperiode die is opgegeven door de beheerder.

## <a name="see-also"></a>Zie ook

- [Installeren en gebruiken van Windows PowerShell-internettoegang](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
- [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
- [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md)
