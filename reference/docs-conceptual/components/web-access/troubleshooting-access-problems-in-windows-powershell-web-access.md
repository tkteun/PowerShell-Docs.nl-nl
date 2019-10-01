---
ms.date: 08/23/2017
keywords: Power shell, cmdlet
title: toegangs problemen in Windows Power shell-Internet toegang oplossen
ms.openlocfilehash: 74cebbe418fecd21567ba9ecc7c561b51ac008fd
ms.sourcegitcommit: a35450f420dc10a02379f6e6f08a28ad11fe5a6d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71692241"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Toegangsproblemen in Windows PowerShell Web Access oplossen

Vernieuwd 24 juni 2013 (herziene versie van 23 augustus 2017)

Van toepassing op: Windows Server 2012 R2, Windows Server 2012

In de volgende secties worden enkele veelvoorkomende problemen beschreven bij het maken van verbinding met een externe computer met Windows Power shell-webtoegang, en vindt u suggesties voor het oplossen van de problemen.

## <a name="sign-in-failure"></a>Aanmelding mislukt

Deze fout kan de volgende oorzaken hebben.

- Een autorisatieregel die de gebruiker toegang verleent tot de computer of een bepaalde sessieconfiguratie op de externe computer bestaat niet.

  Beveiliging van Windows Power shell-Internet toegang is beperkend; gebruikers moeten expliciet toegang tot externe computers worden verleend via autorisatie regels.

  Zie [autorisatie regels en beveiligings functies van Windows Power shell-Internet toegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md)voor meer informatie over het maken van autorisatie regels.

- De gebruiker heeft geen geautoriseerde toegang tot de doelcomputer. Dit wordt bepaald door toegangsbeheerlijsten (ACL's).

  Zie [Aanmelden bij Windows Power shell-webtoegang](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)of het Windows Power shell-team blog voor meer informatie.

- Extern beheer van Windows Power shell wordt mogelijk niet ingeschakeld op de doel computer.

  Controleer of extern beheer is ingeschakeld op de computer waarmee de gebruiker verbinding probeert te maken.

  Zie [How to configure your computer voor externe toegang](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting)voor meer informatie.

## <a name="internal-server-error"></a>Interne server fout

Wanneer gebruikers zich proberen aan te melden bij Windows Power shell-webtoegang in een Internet Explorer-venster, wordt een **interne server fout** pagina weer gegeven of reageert *Internet Explorer* niet meer.

Dit probleem is specifiek voor Internet Explorer.

### <a name="possible-cause"></a>Mogelijke oorzaak

Dit probleem kan optreden bij gebruikers die zijn aangemeld met een domeinnaam die Chinese tekens bevat of als de naam van de gatewayserver een of meer Chinese tekens bevat.

#### <a name="workaround"></a>Tijdelijke oplossing

1. Internet Explorer 10 installeren en uitvoeren
1. Wijzig de instelling voor de **document modus** van Internet Explorer in *IE10* -standaarden.
   1. Druk op **F12** om de Ontwikkelhulpprogramma's-console te openen
   1. Klik in Internet Explorer 10 op **browser modus**en selecteer vervolgens *Internet Explorer 10*.
   1. Klik op **document modus**en klik vervolgens op *IE10* -standaarden.
   1. Druk nogmaals op **F12** om de Ontwikkelhulpprogramma's-console te sluiten.
1. Schakel automatische proxy configuratie uit in Internet Explorer 10.
   1. Klik op **extra**en klik vervolgens op **Internet opties**.
   1. Klik in het dialoog venster **Internet opties** op het tabblad **verbindingen** op **LAN-instellingen**.
   1. Schakel het selectie vakje **instellingen automatisch detecteren** uit. Klik op **OK**en klik nogmaals op **OK** om het dialoog venster *Internet opties* te sluiten.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Kan geen verbinding maken met een externe werkgroepcomputer

Als de doel computer lid is van een werk groep, gebruikt u de volgende syntaxis om uw gebruikers naam op te geven en zich aan te melden bij de computer: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Kan de beheerhulpprogramma's voor Webserver (IIS) niet vinden ook al is de functie geïnstalleerd

Als u Windows Power shell-webtoegang hebt geïnstalleerd met behulp van de cmdlet `Install-WindowsFeature`, worden beheer hulpprogramma's niet geïnstalleerd, tenzij de para meter `-IncludeManagementTools` wordt toegevoegd aan de cmdlet.

Zie [Windows Power shell-webtoegang installeren met behulp van Windows Power shell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)voor een voor beeld.

U kunt de IIS-beheer console en andere IIS-beheer hulpprogramma's die u nodig hebt, toevoegen door de hulpprogram ma's te selecteren in de **wizard functies en onderdelen toevoegen** die is gericht op de gateway server.
De wizard functies en onderdelen toevoegen wordt geopend vanuit Serverbeheer.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Windows Power shell Web Access-website is niet toegankelijk

Als verbeterde beveiliging is ingeschakeld in Internet Explorer (IE ESC), kunt u de website Windows Power shell Web Access toevoegen aan de lijst met vertrouwde sites.

Een minder aanbevolen aanpak door beveiligings Risico's is het uitschakelen van Internet Explorer ESC.
U kunt IE ESC uitschakelen op de tegel eigenschappen op de pagina lokale server in Serverbeheer.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Er is een autorisatie fout opgetreden. Controleer of u gemachtigd bent om verbinding te maken met de doelcomputer.

Het bovenstaande fout bericht wordt weer gegeven wanneer u verbinding probeert te maken wanneer de gateway server de doel computer is en zich ook in een werk groep bevindt.

Wanneer de gateway server ook de doel server is en deze zich in een werk groep bevindt, geeft u de gebruikers naam, de computer naam en de naam van de gebruikers groep op.
Gebruik niet een punt (.) om de computer naam weer te geven.

### <a name="scenarios-and-proper-values"></a>Scenario's en de juiste waarden

#### <a name="all-cases"></a>Alle cases

Parameter | Value
-- | --
UserName | Server @ no__t-0name @ no__t-1user @ no__t-2name<br/>Localhost @ no__t-0user @ no__t-1name<br/>. \\user @ no__t-1name
UserGroup | Server @ no__t-0name @ no__t-1user @ no__t-2group<br/>Localhost @ no__t-0user @ no__t-1group<br/>. \\user @ no__t-1group
ComputerGroup | Server @ no__t-0name @ no__t-1computer @ no__t-2group<br/>Localhost @ no__t-0computer @ no__t-1group<br/>. \\computer @ no__t-1group

#### <a name="gateway-server-is-in-a-domain"></a>Gatewayserver bevindt zich in een domein.

Parameter | Value
-- | --
Computernaam | Volledig gekwalificeerde naam van gatewayserver of Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Bestandsserver maakt deel uit van een werkgroep

Parameter | Value
-- | --
Computernaam | Servernaam

### <a name="gateway-credentials"></a>Gateway referenties

Meld u aan bij een gatewayserver als doelcomputer met referenties die de volgende indeling hebben.

- Server @ no__t-0name @ no__t-1user @ no__t-2name
- Localhost @ no__t-0user @ no__t-1name
- . \\user @ no__t-1name

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Er wordt een beveiligings-id (SID) weer gegeven in een autorisatie regel

Er wordt een beveiligings-id (SID) weer gegeven in een autorisatie regel in plaats van de syntaxis gebruiker @ no__t-0name/computer @ no__t-1name.

De regel is niet meer geldig of de Active Directory Domain Services-query is mislukt.
Een autorisatie regel is doorgaans niet geldig in scenario's waarin de gateway server zich in één keer in een werk groep bevond, maar later is toegevoegd aan een domein

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Kan niet aanmelden met een regel als een IPv6-adres met een domein

Kan niet aanmelden bij een doelcomputer die is opgegeven in autorisatieregels als een IPv6-adres met een domein.

Autorisatieregels ondersteunen geen IPv6-adressen in de vorm van een domeinnaam.

Als u een doelcomputer wilt opgeven met behulp van een IPv6-adres, gebruikt u het oorspronkelijke IPv6-adres (dat dubbele punten bevat) in de autorisatieregel.
Zowel domein-als numerieke IPv6-adressen (met dubbele punten) worden ondersteund als de naam van de doel computer op de aanmeldings pagina van de Windows Power shell-webtoegang, maar niet in autorisatie regels.

Zie [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx)(Engelstalig) voor meer informatie over IPv6-adressen.

## <a name="see-also"></a>Zie ook

- [Autorisatie regels en beveiligings functies van Windows Power shell-Internet toegang](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [De Windows Power shell-console van het web gebruiken](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
