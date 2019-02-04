---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: toegangsproblemen in windows powershell-webtoegang oplossen
ms.openlocfilehash: 314e4a8098988111739705d55b68ff5ed2f5eff3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688117"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Toegangsproblemen in Windows PowerShell Web Access oplossen

Bijgewerkt: Juni 24 2013 (herziene versie van 23 augustus 2017)

Van toepassing op: Windows Server 2012 R2, Windows Server 2012

De volgende secties enkele veelvoorkomende problemen identificeren tijdens het verbinding maken met een externe computer met Windows PowerShell-webtoegang en de tabel bevat suggesties voor het oplossen van problemen.

## <a name="sign-in-failure"></a>Aanmelding mislukt

Deze fout kan de volgende oorzaken hebben.

- Een autorisatieregel die de gebruiker toegang verleent tot de computer of een bepaalde sessieconfiguratie op de externe computer bestaat niet.

  Beveiliging van Windows PowerShell-webtoegang is beperkend; gebruikers moet expliciet toegang tot externe computers worden verleend via autorisatieregels.

  Zie voor meer informatie over het maken van autorisatieregels [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- De gebruiker heeft geen geautoriseerde toegang tot de doelcomputer. Dit wordt bepaald door toegangsbeheerlijsten (ACL's).

  Zie voor meer informatie, [aanmelden bij Windows PowerShell-webtoegang](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), of de Windows PowerShell Team Blog.

- Extern beheer van Windows PowerShell kan niet worden ingeschakeld op de doelcomputer.

  Controleer of extern beheer is ingeschakeld op de computer waarop de gebruiker probeert om verbinding te maken.

  Zie voor meer informatie, [hoe u uw Computer configureren voor externe toegang](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>Interne serverfout

Wanneer gebruikers proberen zich aanmeldt bij Windows PowerShell-webtoegang in een venster van Internet Explorer, worden ze weergegeven een **interne serverfout** pagina of *Internet Explorer* reageert niet meer.

Dit probleem is specifiek voor Internet Explorer.

### <a name="possible-cause"></a>Mogelijke oorzaak

Dit probleem kan optreden bij gebruikers die zijn aangemeld met een domeinnaam die Chinese tekens bevat of als de naam van de gatewayserver een of meer Chinese tekens bevat.

#### <a name="workaround"></a>Tijdelijke oplossing

1. [Installeren en uitvoeren van Internet Explorer 10](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Wijzigen van Internet Explorer **documentmodus** instelt op *IE10* standaarden.
   1. Druk op **F12** openen van de console ontwikkelhulpprogramma's
   1. Klik in Internet Explorer 10 op **Browsermodus**, en selecteer vervolgens *Internet Explorer 10*.
   1. Klik op **documentmodus**, en klik vervolgens op *IE10* standaarden.
   1. Druk op **F12** opnieuw uit te sluiten van de console ontwikkelhulpprogramma's.
1. Schakel automatische proxyconfiguratie in Internet Explorer 10.
   1. Klik op **extra**, en klik vervolgens op **Internetopties**.
   1. In de **Internetopties** dialoogvenster op de **verbindingen** tabblad **LAN-instellingen**.
   1. Schakel de **-instellingen automatisch detecteren** selectievakje. Klik op **OK**, en klik vervolgens op **OK** opnieuw uit te sluiten de *Internetopties* in het dialoogvenster.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Kan geen verbinding maken met een externe werkgroepcomputer

Als de doelcomputer lid is van een werkgroep, gebruikt u de volgende syntaxis om te bieden uw gebruikersnaam en meld u aan bij de computer: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Kan de beheerhulpprogramma's voor Webserver (IIS) niet vinden ook al is de functie geïnstalleerd

Als u Windows PowerShell-webtoegang geïnstalleerd met behulp van de `Install-WindowsFeature` cmdlet, management-hulpprogramma's zijn niet geïnstalleerd, tenzij de `-IncludeManagementTools` parameter is toegevoegd aan de cmdlet.

Zie voor een voorbeeld [Windows PowerShell-webtoegang installeren met behulp van Windows PowerShell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

U kunt de IIS Manager-console toevoegen en andere IIS-beheerprogramma's die u nodig hebt, selecteert u de hulpprogramma's in een **functies Wizard Functies toevoegen en** sessie die is gericht op de gateway-server.
De toevoegen Wizard functies en onderdelen wordt geopend vanuit binnen Server Manager.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Windows PowerShell Web Access-website is niet toegankelijk

Als Verbeterde beveiliging is ingeschakeld in Internet Explorer (IE ESC), kunt u de Windows PowerShell Web Access-website toevoegen aan de lijst met vertrouwde sites.

Een minder aanbevolen benadering, vanwege een beveiligingsrisico's, is het IE ESC uitschakelen.
U kunt IE ESC uitschakelen in de tegel eigenschappen op de lokale Server-pagina in Serverbeheer.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Er is een Autorisatiefout opgetreden. Controleer of u gemachtigd bent om verbinding te maken met de doelcomputer.

De bovenstaande foutbericht wordt weergegeven tijdens het verbinding maken wanneer de gatewayserver de doelcomputer is en ook in een werkgroep is.

Wanneer de gatewayserver ook de doelserver is en deel uitmaakt van een werkgroep, geeft u de gebruikersnaam, computernaam en naam van de gebruikersgroep.
Gebruik een punt (.) niet op zichzelf voor de computernaam van de.

### <a name="scenarios-and-proper-values"></a>Scenario's en de juiste waarden

#### <a name="all-cases"></a>Alle aanvragen

Parameter | Waarde
-- | --
UserName | Server\_naam\\gebruiker\_naam<br/>Localhost\\gebruiker\_naam<br/>. \\gebruiker\_naam
Gebruikersgroep | Server\_naam\\gebruiker\_groep<br/>Localhost\\gebruiker\_groep<br/>.\\user\_group
ComputerGroup | Server\_naam\\computer\_groep<br/>Localhost\\computer\_group<br/>.\\computer\_group

#### <a name="gateway-server-is-in-a-domain"></a>Gatewayserver bevindt zich in een domein.

Parameter | Waarde
-- | --
ComputerName | Volledig gekwalificeerde naam van gatewayserver of Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Bestandsserver maakt deel uit van een werkgroep

Parameter | Waarde
-- | --
ComputerName | Servernaam

### <a name="gateway-credentials"></a>Gatewayreferenties

Meld u aan bij een gatewayserver als doelcomputer met referenties die de volgende indeling hebben.

- Server\_naam\\gebruiker\_naam
- Localhost\\gebruiker\_naam
- . \\gebruiker\_naam

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Een beveiligings-id (SID) wordt weergegeven in een autorisatieregel

Een beveiligings-id (SID) wordt weergegeven in een autorisatieregel in plaats van de syntaxis van de gebruiker\_naam en de computer\_naam.

De regel is niet meer geldig of de Active Directory Domain Services-query is mislukt.
Een autorisatieregel is doorgaans niet geldig in scenario's waarin de gatewayserver is in één keer in een werkgroep, maar later is toegevoegd aan een domein

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Zich niet aanmelden met regel als een IPv6-adres met een domein

Kan niet aanmelden bij een doelcomputer die is opgegeven in autorisatieregels als een IPv6-adres met een domein.

Autorisatieregels ondersteunen geen IPv6-adressen in de vorm van een domeinnaam.

Als u een doelcomputer wilt opgeven met behulp van een IPv6-adres, gebruikt u het oorspronkelijke IPv6-adres (dat dubbele punten bevat) in de autorisatieregel.
Zowel het domein als numerieke (met dubbele punten) IPv6-adressen worden ondersteund als naam van de doelcomputer op de aanmeldingspagina van Windows PowerShell-webtoegang, maar niet in autorisatieregels.

Zie voor meer informatie over IPv6-adressen, [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Zie ook

- [Autorisatieregels en beveiligingsfuncties van Windows PowerShell-internettoegang](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [De webgebaseerde Windows PowerShell-Console gebruiken](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)