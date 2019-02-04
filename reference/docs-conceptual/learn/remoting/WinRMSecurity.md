---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: WinRMSecurity
ms.openlocfilehash: 59717e4806857e6760de523335bbee6028da8e84
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688306"
---
# <a name="powershell-remoting-security-considerations"></a>Beveiligingsoverwegingen bij externe communicatie van PowerShell

Externe communicatie van PowerShell is de aanbevolen manier om Windows-systemen worden beheerd. Externe communicatie van PowerShell is standaard ingeschakeld in Windows Server 2012 R2. Dit document bevat informatie over beveiligingsproblemen, aanbevelingen en aanbevolen procedures bij het gebruik van PowerShell voor externe toegang.

## <a name="what-is-powershell-remoting"></a>Wat is de externe communicatie van PowerShell?

Maakt gebruik van PowerShell voor externe toegang [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), dit is de Microsoft-implementatie van de [Web Services for Management (WS-Management)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) -protocol, waarmee gebruikers PowerShell ook uitvoeren de opdrachten op externe computers. U vindt meer informatie over het gebruik van PowerShell voor externe toegang op [externe opdrachten uitgevoerd](https://technet.microsoft.com/library/dd819505.aspx).

PowerShell voor externe toegang is niet hetzelfde als wanneer u de **ComputerName** parameter van een cmdlet uit te voeren op een externe computer, waardoor Remote Procedure Call (RPC) gebruikt als het onderliggende protocol.

## <a name="powershell-remoting-default-settings"></a>Standaardinstellingen voor externe communicatie van PowerShell

PowerShell voor externe toegang (en WinRM) luisteren op de volgende poorten:

- HTTP: 5985
- HTTPS: 5986

Standaard staat PowerShell voor externe toegang alleen verbindingen van leden van de groep Administrators. Sessies worden gestart in de context van de gebruiker, zodat alle besturingssysteem-toegangsbeheer wordt toegepast op afzonderlijke gebruikers en groepen toepassen op deze blijven terwijl u bent verbonden via externe communicatie van PowerShell.

Op particuliere netwerken accepteert de standaardregel voor de Windows Firewall voor externe communicatie van PowerShell alle verbindingen. Op openbare netwerken, de standaard Windows Firewall-regel PowerShell voor externe toegang alleen verbindingen via toegestaan binnen hetzelfde subnet. U moet expliciet wijzigen die regel voor het openen van PowerShell voor externe toegang op alle verbindingen van een openbaar netwerk.

>**Waarschuwing:** De firewall-regel voor openbare netwerken is bedoeld om de computer beschermen tegen kwaadwillende externe verbindingspogingen. Wees voorzichtig bij het verwijderen van deze regel.

## <a name="process-isolation"></a>Isolatie van het toepassingsproces

Maakt gebruik van PowerShell voor externe toegang [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) voor communicatie tussen computers.
WinRM wordt uitgevoerd als een service met de Netwerkservice-account en gestart geïsoleerde processen die worden uitgevoerd als gebruikersaccounts PowerShell-exemplaren hosten. Een exemplaar van PowerShell die worden uitgevoerd als een gebruiker heeft geen toegang tot een proces een instantie van PowerShell wordt uitgevoerd als een andere gebruiker.

## <a name="event-logs-generated-by-powershell-remoting"></a>Logboeken die worden gegenereerd door externe communicatie van PowerShell

FireEye is een goed overzicht van de logboeken en andere security aanwijzingen die worden gegenereerd door externe communicatie van PowerShell-sessies, beschikbaar op opgegeven [PowerShell-aanvallen onderzoeken](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Versleuteling en transport protocollen

Is het handig om de beveiliging van een externe communicatie van PowerShell-verbinding vanuit twee perspectieven: initiële verificatie en voortdurend communiceren.

Ongeacht het transportprotocol gebruikt (HTTP of HTTPS) codeert PowerShell voor externe toegang altijd alle communicatie na de initiële verificatie met een sessie-AES-256 symmetrische sleutel.

### <a name="initial-authentication"></a>Initiële verificatie

Verificatie wordt bevestigd dat de identiteit van de client naar de server- of in het ideale geval - de server naar de client.

Wanneer een client verbinding maakt met een domeinserver met behulp van de naam van de computer (dat wil zeggen: server01, of server01.contoso.com), het standaard-verificatieprotocol [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos garandeert de gebruikers-id en de serveridentiteit zonder een of andere vorm van herbruikbare referenties te verzenden.

Wanneer een client verbinding maakt met een domeinserver met behulp van het IP-adres of verbinding met een werkgroepserver maakt, is Kerberos-verificatie niet mogelijk. In dat geval PowerShell voor externe toegang is afhankelijk van de [NTLM-verificatieprotocol](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). Het NTLM-verificatieprotocol garandeert de identiteit van de gebruiker zonder een of andere vorm van delegeerbare referentie te verzenden. Om te bewijzen dat gebruikers-id, het NTLM-protocol is vereist dat de client en de server een sessiesleutel van het wachtwoord van gebruikers compute zonder ooit uitwisselen van het wachtwoord zelf. De server normaal gesproken weet niet het wachtwoord van gebruikers, zodat deze communiceert met de domeincontroller, dit van de gebruiker het wachtwoord en berekent de sessiesleutel voor de server.

Het NTLM-protocol is echter niet zo is, garantie voor de identiteit van server. Net als bij alle protocollen die gebruikmaken van NTLM voor verificatie, kan een aanvaller met toegang tot een domein computer-computeraccount aanroepen van de domeincontroller voor het berekenen van een NTLM-sessiesleutel en waardoor voordoen als de server.

NTLM-verificatie is standaard uitgeschakeld, maar kan worden toegestaan door een van beide SSL configureren op de doelserver, of door het configureren van de WinRM-TrustedHosts-instelling op de client.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Met behulp van SSL-certificaten voor het valideren van de identiteit van server tijdens verbindingen op basis van NTLM

Omdat het NTLM-protocol voor verificatie kan niet zorgen dat de identiteit van de doelserver (alleen die deze uw wachtwoord al kent), kunt u de doelservers voor het gebruik van SSL voor PowerShell voor externe toegang kunt configureren. Een SSL-certificaat toewijzen aan de doelserver (als dat is uitgegeven door een certificeringsinstantie die de client ook vertrouwensrelaties), kunt NTLM-verificatie die de gebruikers-id en de serveridentiteit wordt gegarandeerd.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Server NTLM op basis van identiteit fouten worden genegeerd

Als een SSL-certificaat implementeren op een server voor NTLM-verbindingen onbruikbare is, mag u de resulterende identiteit fouten onderdrukken door de server toe te voegen aan de WinRM **TrustedHosts** lijst. Houd er rekening mee dat de naam van een server toe te voegen aan de TrustedHosts-lijst moet niet worden beschouwd als een vorm van instructie van de betrouwbaarheid van de hosts zichzelf: als het NTLM-protocol voor verificatie kan niet garanderen dat u in feite verbinding met de host maakt zijn verbinding maken met wilde maken.
In plaats daarvan moet u overwegen de TrustedHosts-instelling moet de lijst met hosts die u onderdrukken van de fout die worden gegenereerd wilt door het niet kan controleren of de identiteit van de server.


### <a name="ongoing-communication"></a>Verdere communicatie

Zodra de initiële verificatie is voltooid, de [PowerShell Remoting Protocol](https://msdn.microsoft.com/library/dd357801.aspx) versleutelt alle verdere communicatie met een sessie-AES-256 symmetrische sleutel.


## <a name="making-the-second-hop"></a>De tweede hop maken

Standaard gebruikt PowerShell Remoting Kerberos (indien beschikbaar) of NTLM voor authenticatie. Beide van deze protocollen worden geverifieerd bij de externe computer zonder referenties te verzenden naar deze.
Dit is de veiligste manier om te verifiëren, maar omdat de externe computer geen referenties van de gebruiker heeft geen toegang tot andere computers en services namens de gebruiker.
Dit staat bekend als het 'tweede hop '-probleem.

Er zijn verschillende manieren om dit probleem te voorkomen. Zie voor beschrijvingen van deze methoden, en de voor- en nadelen van elk [de tweede hop maken in PowerShell Remoting](PS-remoting-second-hop.md).