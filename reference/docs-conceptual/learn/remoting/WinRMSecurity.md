---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: WinRMSecurity
ms.openlocfilehash: 59717e4806857e6760de523335bbee6028da8e84
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086357"
---
# <a name="powershell-remoting-security-considerations"></a>Beveiligings overwegingen voor externe communicatie met Power shell

Externe communicatie van Power shell is de aanbevolen manier om Windows-systemen te beheren. Externe communicatie van Power shell is standaard ingeschakeld in Windows Server 2012 R2. Dit document bevat beveiligings problemen, aanbevelingen en aanbevolen procedures voor het gebruik van externe communicatie met Power shell.

## <a name="what-is-powershell-remoting"></a>Wat is externe communicatie van Power shell?

Externe communicatie van Power Shell maakt gebruik van [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), de micro soft-implementatie van het protocol [Web Services for Management (WS-Management)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) , waarmee gebruikers Power shell-opdrachten kunnen uitvoeren op externe computers. U kunt meer informatie vinden over het gebruik van externe toegang via Power shell bij het [uitvoeren van opdrachten op afstand](https://technet.microsoft.com/library/dd819505.aspx).

Externe communicatie met Power shell is niet hetzelfde als het gebruik van de para meter **ComputerName** van een cmdlet om deze uit te voeren op een externe computer, die gebruikmaakt van Remote Procedure Call (RPC) als onderliggend protocol.

## <a name="powershell-remoting-default-settings"></a>Externe standaard instellingen voor Power shell

Externe communicatie van Power shell (en WinRM) luistert op de volgende poorten:

- HTTP: 5985
- HTTPS: 5986

Externe communicatie van Power Shell staat standaard alleen verbindingen toe van leden van de groep Administrators. Sessies worden gestart op basis van de context van de gebruiker, zodat alle toegangs beheer van besturings systemen die worden toegepast op afzonderlijke gebruikers en groepen, blijven gelden tijdens de verbinding via externe communicatie met Power shell.

In particuliere netwerken accepteert de standaard Windows Firewall regel voor externe communicatie van Power shell alle verbindingen. In open bare netwerken staat de standaard Windows Firewall regel externe verbindingen van Power shell alleen vanuit hetzelfde subnet toe. U moet deze regel expliciet wijzigen om externe communicatie van Power shell te openen voor alle verbindingen op een openbaar netwerk.

>**Waarschuwing:** De firewall regel voor open bare netwerken is bedoeld om de computer te beschermen tegen mogelijk kwaad aardige externe Verbindings pogingen. Wees voorzichtig bij het verwijderen van deze regel.

## <a name="process-isolation"></a>Proces isolatie

Externe toegang voor Power Shell maakt gebruik van [Windows Remote Management (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) voor communicatie tussen computers.
WinRM wordt uitgevoerd als een service onder het netwerk service account en geïsoleerde processen worden uitgevoerd als gebruikers accounts voor het hosten van Power shell-exemplaren. Een instantie van Power shell die wordt uitgevoerd als één gebruiker heeft geen toegang tot een proces dat een exemplaar van Power shell uitvoert als een andere gebruiker.

## <a name="event-logs-generated-by-powershell-remoting"></a>Gebeurtenis logboeken die zijn gegenereerd door externe communicatie met Power shell

FireEye heeft een goed overzicht gegeven van de gebeurtenis logboeken en andere beveiligings bewijzen die worden gegenereerd door externe communicatie sessies van Power shell, die beschikbaar zijn bij het [onderzoeken van Power shell-aanvallen](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Versleutelings-en transport protocollen

Het is handig om de beveiliging van een externe Power shell-verbinding van twee perspectieven te overwegen: initiële verificatie en doorlopende communicatie.

Ongeacht het transport protocol dat wordt gebruikt (HTTP of HTTPS), versleutelt Power shell Remoting altijd alle communicatie na de initiële verificatie met een symmetrische sleutel van het niveau van AES-256.

### <a name="initial-authentication"></a>Initiële verificatie

Met verificatie wordt de identiteit van de client aan de server en de ideale server voor de-client bevestigd.

Wanneer een client verbinding maakt met een domein server met behulp van de bijbehorende computer naam (bijvoorbeeld: Server01 of server01.contoso.com), is het standaard verificatie protocol [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos garandeert zowel de identiteit van de gebruikers-id als de server zonder de herbruikbare referentie te verzenden.

Kerberos-verificatie is niet mogelijk wanneer een client verbinding maakt met een domein server met behulp van het IP-adres of verbinding maakt met een werkgroepserver. In dat geval is externe communicatie van Power shell afhankelijk van het [NTLM-verificatie protocol](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). Het NTLM-verificatie protocol garandeert de gebruikers identiteit zonder dat er een sortering van Delegeer bare-referenties wordt verzonden. Als u de identiteit van de gebruiker wilt bewijzen, moet de client en server een sessie sleutel van het wacht woord van de gebruiker berekenen zonder dat het wacht woord zelf hoeft te worden uitgewisseld. De server weet doorgaans niet het wacht woord van de gebruiker, zodat deze communiceert met de domein controller, die het wacht woord van de gebruiker kent en de sessie sleutel voor de server berekent.

Het NTLM-protocol garandeert echter niet de identiteit van de server. Net als bij alle protocollen die gebruikmaken van NTLM voor verificatie, kan een aanvaller met toegang tot het computer account van een computer die lid is van een domein, de domein controller aanroepen om een NTLM-sessie sleutel te berekenen en de server te imiteren.

Verificatie op basis van NTLM is standaard uitgeschakeld, maar kan worden toegestaan door SSL op de doel server te configureren of door de WinRM TrustedHosts-instelling op de client te configureren.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>SSL-certificaten gebruiken voor het valideren van de server identiteit tijdens op NTLM gebaseerde verbindingen

Omdat het NTLM-verificatie protocol de identiteit van de doel server niet kan garanderen (alleen dat uw wacht woord al bekend is), kunt u doel servers configureren voor het gebruik van SSL voor externe communicatie met Power shell. Als u een SSL-certificaat aan de doel server toewijst (indien dit wordt uitgegeven door een certificerings instantie die de client ook vertrouwt), schakelt u verificatie op basis van NTLM in die zowel de gebruikers-id als de identiteit van de server garandeert.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Server identiteits fouten op basis van NTLM negeren

Als het implementeren van een SSL-certificaat op een server voor NTLM-verbindingen niet haalbaar is, kunt u de resulterende identiteits fouten onderdrukken door de server toe te voegen aan de lijst met WinRM **TrustedHosts** . Het toevoegen van een server naam aan de TrustedHosts-lijst mag niet worden beschouwd als een instructie van de betrouw baarheid van de hosts zelf, omdat het NTLM-verificatie protocol niet kan garanderen dat u verbinding maakt met de host die u bent wil verbinding maken met.
In plaats daarvan moet u de TrustedHosts-instelling beschouwen als de lijst met hosts waarvoor u de fout die is gegenereerd door de server identiteit niet kunt controleren.


### <a name="ongoing-communication"></a>Doorlopende communicatie

Zodra de initiële verificatie is voltooid, versleutelt het [Power shell Remoting-protocol](https://msdn.microsoft.com/library/dd357801.aspx) alle lopende communicatie met een symmetrische sleutel van AES-256.


## <a name="making-the-second-hop"></a>De tweede hop maken

Power shell Remoting maakt standaard gebruik van Kerberos (indien beschikbaar) of NTLM voor authenticatie. Beide protocollen verifiëren aan de externe computer zonder referenties te verzenden.
Dit is de veiligste manier om te verifiëren, maar omdat de externe computer niet beschikt over de referenties van de gebruiker, heeft deze geen toegang tot andere computers en services namens de gebruiker.
Dit staat bekend als het ' probleem met de tweede hop '.

Er zijn verschillende manieren om dit probleem te voor komen. Zie [de tweede hop in Power shell Remoting maken](PS-remoting-second-hop.md)voor beschrijvingen van deze methoden en de voor-en nadelen van elke methode.