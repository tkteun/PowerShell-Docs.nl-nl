---
ms.date: 08/23/2017
keywords: PowerShell-cmdlet
title: het oplossen van toegangsproblemen in windows powershell-webtoegang
ms.openlocfilehash: ef476d8e386e5380cb2c9dda69180dfce8748bf4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953443"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Toegangsproblemen in Windows PowerShell Web Access oplossen

Bijgewerkt: Juni 24 2013 (herziene versie 23 augustus 2017)

Van toepassing op: Windows Server 2012 R2, WindowsServer 2012

De volgende secties enkele veelvoorkomende problemen te identificeren bij een poging verbinding maken met een externe computer met behulp van Windows PowerShell-webtoegang en bevat suggesties voor het oplossen van problemen.

## <a name="sign-in-failure"></a>Aanmelding mislukt

Deze fout kan de volgende oorzaken hebben.

- Een autorisatieregel die de gebruiker toegang verleent tot de computer of een bepaalde sessieconfiguratie op de externe computer bestaat niet.

  Beveiliging van Windows PowerShell-webtoegang is beperkend; gebruikers moet expliciet toegang tot externe computers worden verleend via autorisatieregels.

  Zie voor meer informatie over het maken van autorisatieregels [autorisatieregels en beveiliging functies van Windows PowerShell-webtoegang](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- De gebruiker heeft geen geautoriseerde toegang tot de doelcomputer. Dit wordt bepaald door toegangsbeheerlijsten (ACL's).

  Zie voor meer informatie [aanmelden bij Windows PowerShell-webtoegang](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), of de Windows PowerShell Team Blog.

- Windows PowerShell extern beheer is mogelijk niet ingeschakeld op de doelcomputer.

  Controleer of extern beheer is ingeschakeld op de computer waarop de gebruiker probeert verbinding maken.

  Zie voor meer informatie [hoe configureren op uw Computer voor extern beheer](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>Interne serverfout

Wanneer gebruikers proberen aan te melden bij Windows PowerShell Web Access in een venster van Internet Explorer, worden ze weergegeven een **interne serverfout** pagina of *Internet Explorer* reageert niet meer.

Dit probleem is specifiek voor Internet Explorer.

### <a name="possible-cause"></a>Mogelijke oorzaak

Dit probleem kan optreden bij gebruikers die zijn aangemeld met een domeinnaam die Chinese tekens bevat of als de naam van de gatewayserver een of meer Chinese tekens bevat.

#### <a name="workaround"></a>Tijdelijke oplossing

1. [Installeren en uitvoeren van Internet Explorer 10](http://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Wijzigen van Internet Explorer **documentmodus** instelt op *IE10* standaarden.
   1. Druk op **F12** openen van de console ontwikkelhulpprogramma's
   1. Klik in Internet Explorer 10 op **Browsermodus**, en selecteer vervolgens *Internet Explorer 10*.
   1. Klik op **documentmodus**, en klik vervolgens op *IE10* standaarden.
   1. Druk op **F12** opnieuw naar de console ontwikkelhulpprogramma's te sluiten.
1. Schakel automatische proxyconfiguratie in Internet Explorer 10 uit.
   1. Klik op **extra**, en klik vervolgens op **Internetopties**.
   1. In de **Internetopties** in het dialoogvenster op de **verbindingen** tabblad **LAN-instellingen**.
   1. Schakel de **-instellingen automatisch detecteren** selectievakje. Klik op **OK**, en klik vervolgens op **OK** opnieuw moet worden afgesloten de *Internetopties* in het dialoogvenster.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Kan geen verbinding maken met een externe werkgroepcomputer

Als de doelcomputer lid is van een werkgroep, gebruikt u de volgende syntaxis om te bieden uw gebruikersnaam en meld u bij de computer: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Kan de beheerhulpprogramma's voor Webserver (IIS) niet vinden ook al is de functie geïnstalleerd

Als u Windows PowerShell-webtoegang geïnstalleerd met behulp van de `Install-WindowsFeature` cmdlet beheerhulpprogramma's niet geïnstalleerd, tenzij de `-IncludeManagementTools` parameter wordt toegevoegd aan de cmdlet.

Zie voor een voorbeeld [Windows PowerShell-webtoegang installeren met behulp van Windows PowerShell-cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

U kunt de IIS Manager-console toevoegen en andere IIS-beheerhulpprogramma's dat u nodig hebt, selecteert u de hulpprogramma's in een **Wizard Functies toevoegen en onderdelen** sessie die is gericht op de gatewayserver.
De functies en onderdelen wordt geopend vanuit binnen Server Manager.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Windows PowerShell Web Access-website is niet toegankelijk

Als Verbeterde beveiliging is ingeschakeld in Internet Explorer (IE ESC), kunt u de Windows PowerShell Web Access-website toevoegen aan de lijst met vertrouwde sites.

Een benadering minder aanbevolen vanwege beveiligingsrisico's, is het IE ESC uitschakelen.
U kunt IE ESC uitschakelen in de tegel eigenschappen op de pagina lokale Server in Serverbeheer.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Er is een Autorisatiefout opgetreden. Controleer of u gemachtigd bent om verbinding te maken met de doelcomputer.

De bovenstaande foutbericht wordt weergegeven tijdens het verbinding maken wanneer de gatewayserver de doelcomputer is en ook in een werkgroep is.

Wanneer de gatewayserver ook de doelserver is en deze zich in een werkgroep, geeft u de gebruikersnaam, computernaam en gebruikersgroepnaam.
Gebruik een punt (.) niet zelfstandig vertegenwoordigt de naam van de computer.

### <a name="scenarios-and-proper-values"></a>Scenario's en de juiste waarden

#### <a name="all-cases"></a>Alle gevallen

Parameter | Value
-- | --
UserName | Server\_naam\\gebruiker\_naam<br/>Localhost\\user\_name<br/>. \\gebruiker\_naam
UserGroup | Server\_naam\\gebruiker\_groep<br/>Localhost\\gebruiker\_groep<br/>. \\gebruiker\_groep
ComputerGroup | Server\_naam\\computer\_groep<br/>Localhost\\computer\_groep<br/>. \\computer\_groep

#### <a name="gateway-server-is-in-a-domain"></a>Gatewayserver bevindt zich in een domein.

Parameter | Value
-- | --
ComputerName | Volledig gekwalificeerde naam van gatewayserver of Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Bestandsserver maakt deel uit van een werkgroep

Parameter | Value
-- | --
ComputerName | Servernaam

### <a name="gateway-credentials"></a>Gatewayreferenties

Meld u aan bij een gatewayserver als doelcomputer met referenties die de volgende indeling hebben.

- Server\_naam\\gebruiker\_naam
- Localhost\\user\_name
- . \\gebruiker\_naam

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Een beveiligings-id (SID) wordt weergegeven in een autorisatieregel

Een beveiligings-id (SID) wordt weergegeven in een autorisatieregel in plaats van de syntaxis van de gebruiker\_naam en de computer\_naam.

De regel is niet meer geldig of de Active Directory Domain Services-query is mislukt.
Een autorisatieregel is doorgaans niet geldig in scenario's waarin de gatewayserver is tegelijk in een werkgroep, maar later is toegevoegd aan een domein

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Als een IPv6-adres met een domein zich niet aanmelden met de regel

Kan niet aanmelden bij een doelcomputer die is opgegeven in autorisatieregels als een IPv6-adres met een domein.

Autorisatieregels ondersteunen geen IPv6-adressen in de vorm van een domeinnaam.

Als u een doelcomputer wilt opgeven met behulp van een IPv6-adres, gebruikt u het oorspronkelijke IPv6-adres (dat dubbele punten bevat) in de autorisatieregel.
Zowel het domein als numerieke (met dubbele punten) IPv6-adressen worden ondersteund als naam van de doelcomputer op de aanmeldingspagina van Windows PowerShell-webtoegang, maar niet in autorisatieregels.

Zie voor meer informatie over IPv6-adressen [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Zie ook

- [Autorisatieregels en beveiligingsfuncties van Windows PowerShell-internettoegang](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [De webconsole voor Windows PowerShell-Console gebruiken](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)