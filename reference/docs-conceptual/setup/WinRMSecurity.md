---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: WinRMSecurity
ms.openlocfilehash: 43e77067e301cdf1b792cb0d24b72ee0abb3349a
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482944"
---
# <a name="powershell-remoting-security-considerations"></a>Beveiligingsoverwegingen voor externe communicatie van PowerShell

Externe communicatie van PowerShell is de aanbevolen manier voor het beheren van Windows-systemen. Externe communicatie van PowerShell is standaard ingeschakeld in Windows Server 2012 R2. Dit document bevat informatie over beveiligingsproblemen, aanbevelingen en best practices wanneer u externe communicatie van PowerShell.

## <a name="what-is-powershell-remoting"></a>Wat is PowerShell voor externe toegang?

Externe communicatie van PowerShell gebruikt [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), dit is de Microsoft-implementatie van de [Web Services for Management (WS-Management)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) protocol, zodat gebruikers kunnen uitvoeren van PowerShell de opdrachten op externe computers. U vindt meer informatie over het gebruik van PowerShell voor externe toegang op [externe opdrachten uitgevoerd](https://technet.microsoft.com/library/dd819505.aspx).

Externe communicatie van PowerShell is niet hetzelfde als het gebruik van de **ComputerName** parameter van een cmdlet uit te voeren op een externe computer waarop Remote Procedure Call (RPC) gebruikt als het onderliggende protocol.

## <a name="powershell-remoting-default-settings"></a>Standaardinstellingen voor externe communicatie van PowerShell

Externe communicatie van PowerShell (en WinRM) luisteren op de volgende poorten:

- HTTP: 5985
- HTTPS: 5986

Standaard toelaat externe communicatie van PowerShell alleen verbindingen van leden van de groep Administrators. Sessies worden gestart in de context van de gebruiker, zodat alle besturingssysteem toegangsbeheer op afzonderlijke gebruikers toegepast en groepen blijven toepassen op terwijl via externe communicatie van PowerShell is verbonden.

De standaardregel voor Windows Firewall voor externe communicatie van PowerShell accepteert op particuliere netwerken, alle verbindingen. De standaardregel voor Windows Firewall kunt op openbare netwerken externe communicatie van PowerShell verbindingen alleen via binnen hetzelfde subnet. U moet expliciet wijzigen die regel voor het openen van PowerShell voor externe toegang op alle verbindingen van een openbaar netwerk.

>**Waarschuwing:** de firewallregel voor openbare netwerken is bedoeld om de computer beschermen tegen mogelijk schadelijke externe verbindingspogingen. Wees voorzichtig bij het verwijderen van deze regel.

## <a name="process-isolation"></a>Geïsoleerde processen

Externe communicatie van PowerShell gebruikt [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) voor communicatie tussen computers.
WinRM wordt uitgevoerd als een service onder het account Network Service en geïsoleerde processen die worden uitgevoerd als gebruikersaccounts aan host PowerShell exemplaren gestart. Een exemplaar van PowerShell uitgevoerd als een gebruiker heeft geen toegang tot een proces dat een exemplaar van PowerShell uitgevoerd als een andere gebruiker.

## <a name="event-logs-generated-by-powershell-remoting"></a>Gebeurtenislogboeken gegenereerd door externe communicatie van PowerShell

FireEye is een goed overzicht van de gebeurtenislogboeken en andere beveiligingsbewijs gegenereerd door externe communicatie van PowerShell-sessies, beschikbaar op opgegeven [onderzoeken PowerShell aanvallen](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Versleuteling en transportprotocollen

Is het handig om de beveiliging van een externe communicatie van PowerShell-verbinding vanuit twee perspectieven: initiële verificatie en voortdurend communiceren.

Ongeacht het transportprotocol gebruikt (HTTP of HTTPS) versleutelt externe communicatie van PowerShell altijd alle communicatie na de eerste verificatie met een per-AES-256 symmetrische sessiesleutel.

### <a name="initial-authentication"></a>Eerste verificatie

Verificatie bevestigt de identiteit van de client bij de server- en in het ideale geval - de server naar de client.

Wanneer een client verbinding maakt met een domeinserver met de naam van de computer (dat wil zeggen: server01, of server01.contoso.com), is het standaardverificatieprotocol [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos wordt gegarandeerd dat de gebruikers-id en de identiteit van server zonder een soort herbruikbare referenties te verzenden.

Wanneer een client verbinding maakt met de domeinserver van een met behulp van het IP-adres of verbinding met een werkgroepserver is maakt, is Kerberos-verificatie niet mogelijk. In dat geval PowerShell voor externe toegang is afhankelijk van de [NTLM-verificatieprotocol](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). Het NTLM-verificatieprotocol wordt gegarandeerd dat de identiteit van de gebruiker zonder een soort delegable referentie te verzenden. Om te bewijzen dat gebruikers-id, het NTLM-protocol is vereist dat de client en de server een sessiesleutel van het wachtwoord van de gebruiker berekenen zonder ooit uitwisselen van het wachtwoord zelf. De server normaal gesproken weet niet het wachtwoord van de gebruiker, zodat deze communiceert met de domeincontroller de gebruiker het wachtwoord en berekent de sessiesleutel voor de server.

Het NTLM-protocol wordt echter niet, gegarandeerd dat de identiteit van server. Net als bij alle protocollen die gebruikmaken van NTLM voor verificatie, kan de domeincontroller voor het berekenen van een sessiesleutel NTLM en waardoor imiteren van de server worden aangeroepen door een kwaadwillende persoon met toegang tot een domein van het computeraccount.

Op basis van NTLM-verificatie is standaard uitgeschakeld, maar kan worden toegestaan door beide SSL configureren op de doelserver, of door het configureren van de WinRM-TrustedHosts-instelling op de client.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Met behulp van SSL-certificaten voor het valideren van de identiteit van server tijdens verbindingen op basis van NTLM

Aangezien het NTLM-verificatieprotocol kan niet Zorg ervoor dat de identiteit van de doelserver (maar wel dat dit uw wachtwoord al kent), kunt u de doelservers om SSL te gebruiken voor externe communicatie van PowerShell kunt configureren. Een SSL-certificaat toewijzen aan de doelserver (indien uitgegeven door een certificeringsinstantie die door de client ook vertrouwd), kunt NTLM-verificatie die wordt gegarandeerd dat de gebruikers-id en de identiteit van server.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>NTLM-gebaseerde server identity-fouten worden genegeerd

Als het implementeren van een SSL-certificaat op een server voor NTLM-verbindingen onbruikbare is, mag u de resulterende identiteit fouten onderdrukken door de server toe te voegen aan de WinRM **TrustedHosts** lijst. Houd er rekening mee dat de naam van een server toe te voegen aan de lijst TrustedHosts moet niet worden beschouwd als een vorm van instructie van de betrouwbaarheid van de hosts zelf - als het NTLM-verificatieprotocol kan niet worden gegarandeerd dat u in feite een verbinding met de host verbinding maken met wilde.
In plaats daarvan moet u de instelling TrustedHosts aan de lijst met hosts die u onderdrukken van de fout is gegenereerd wilt door het controleren van de identiteit van de server niet kan worden.


### <a name="ongoing-communication"></a>Voortdurend communiceren

Zodra de eerste verificatie is voltooid, de [PowerShell Remoting Protocol](https://msdn.microsoft.com/library/dd357801.aspx) versleutelt alle verdere communicatie met een per-AES-256 symmetrische sessiesleutel.


## <a name="making-the-second-hop"></a>De tweede hop maken

Standaard PowerShell voor externe toegang maakt gebruik van Kerberos (indien beschikbaar) of NTLM voor verificatie. Beide van deze protocollen worden geverifieerd bij de externe computer zonder referenties te verzenden aan.
Dit is de veiligste manier om te verifiëren, maar omdat de externe computer geen referenties van de gebruiker deze geen toegang tot andere computers en services namens de gebruiker.
Dit staat bekend als de "tweede hop '-probleem.

Er zijn verschillende manieren om dit probleem te voorkomen. Zie voor beschrijvingen van deze methoden en de voor- en nadelen van elke [maken van de tweede hop in externe communicatie van PowerShell](PS-remoting-second-hop.md).