---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: JEA-vereisten
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688355"
---
# <a name="prerequisites"></a>Vereisten

> Van toepassing op: Windows PowerShell 5.0

Just Enough Administration is een functie die wordt geleverd met Windows PowerShell 5.0 en hoger.
Dit onderwerp beschrijft de vereisten waaraan moeten worden voldaan om te starten met behulp van JEA.

## <a name="install-jea"></a>Installeren van JEA

JEA is beschikbaar met Windows PowerShell 5.0 en hoger, maar voor de volledige functionaliteit is het raadzaam dat u de meest recente versie van PowerShell beschikbaar voor uw systeem installeert.
De volgende tabel beschrijft de beschikbaarheid van JEA op Windows Server:

Server-besturingssysteem   | JEA-beschikbaarheid
--------------------------|--------------------------------
Windows Server 2016       | Vooraf is geïnstalleerd
Windows Server 2012 R2    | Volledige functionaliteit met WMF 5.1
Windows Server 2012       | Volledige functionaliteit met WMF 5.1
Windows Server 2008 R2    | Verminderde functionaliteit<sup>1</sup> met WMF 5.1

U kunt ook JEA gebruiken op uw computer thuis of werk:

Client-besturingssysteem   | JEA-beschikbaarheid
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Vooraf is geïnstalleerd
Windows 10 1603, 1511     | Vooraf is geïnstalleerd, met verminderde functionaliteit<sup>2</sup>
Windows 10 1507           | Niet beschikbaar
Windows 8, 8.1            | Volledige functionaliteit met WMF 5.1
Windows 7                 | Verminderde functionaliteit<sup>1</sup> met WMF 5.1

<sup>1</sup> JEA kan niet worden geconfigureerd voor het gebruik van door groepen beheerde serviceaccounts in Windows Server 2008 R2 of Windows 7.
Virtuele accounts en andere functies JEA *zijn* ondersteund.

<sup>2</sup> Windows 10 versie 1511 en 1603 bieden geen ondersteuning voor de volgende functies van JEA: uitgevoerd als een groep beheerd serviceaccount, de regels voor voorwaardelijke toegang in sessieconfiguraties, de schijf van de gebruiker en het verlenen van toegang voor lokale gebruikersaccounts.
Voor ondersteuning voor deze functies kunt bijwerken van Windows naar versie 1607 (Jubileumupdate) of hoger.

### <a name="check-which-version-of-powershell-is-installed"></a>Controleren welke versie van PowerShell is geïnstalleerd

Als u wilt controleren welke versie van PowerShell is geïnstalleerd op uw systeem, Controleer de `$PSVersionTable` variabele in een Windows PowerShell-prompt.

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

U bent klaar voor gebruik van JEA als de *belangrijke* versie is gelijk aan of groter zijn dan **5**.
Voor de beste ervaring en toegang hebben tot de nieuwste functies, is het raadzaam dat u een naar PowerShell-versie upgrade **5.1** indien mogelijk.

### <a name="install-windows-management-framework"></a>Installeer Windows Management Framework

Als u een oudere versie van PowerShell uitvoert, moet u uw systeem bijwerken met de meest recente update van Windows Management Framework (WMF).
-Updatepakketten en een koppeling naar de meest recente releaseopmerkingen van WMF zijn beschikbaar in de [Downloadcentrum](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).

Het is raadzaam dat u de compatibiliteit van uw workload met WMF testen vóór de upgrade van al uw servers.

Gebruikers van Windows 10 moeten de nieuwste functie-updates voor het ophalen van de huidige versie van Windows PowerShell installeren.

## <a name="enable-powershell-remoting"></a>Externe communicatie met PowerShell

Externe communicatie van PowerShell vormt de basis waarop JEA is gebouwd.
Het is daarom noodzakelijk voor externe communicatie van PowerShell is ingeschakeld en [goed beveiligde](/powershell/scripting/setup/winrmsecurity) op uw systeem voordat u de JEA kunt gebruiken.

Externe communicatie van PowerShell is standaard ingeschakeld op Windows Server 2012, 2012 R2 en 2016.
U kunt PowerShell voor externe toegang inschakelen door het uitvoeren van de volgende opdracht uit in een PowerShell-venster met verhoogde bevoegdheid.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>PowerShell-module en (optioneel) script blok-logboekregistratie inschakelen

De volgende stappen schakelt logboekregistratie voor alle PowerShell-bewerkingen op uw systeem.
Logboekregistratie van PowerShell-Module is niet vereist voor JEA, maar het is raadzaam dat u deze inschakelen om te controleren of de gebruikers opdrachten uitvoeren op een centrale locatie worden geregistreerd.

U kunt het beleid voor logboekregistratie van PowerShell-Module met behulp van Groepsbeleid configureren.

1. Open de Editor voor lokaal groepsbeleid op een werkstation of een Group Policy Object in de Console Groepsbeleidsbeheer op een Active Directory-domeincontroller
2. Navigeer naar **Computerconfiguratie\\Beheersjablonen\\Windows-onderdelen\\Windows PowerShell**
3. Dubbelklik op **Module logboekregistratie kunnen inschakelen**
4. Klik op **ingeschakeld**
5. Klik in de sectie opties op **weergeven** naast modulenamen
6. Type `\*` in het pop-upvenster. Dit Hiermee geeft u PowerShell om aan te melden opdrachten van alle modules.
7. Klik op **OK** om in te stellen van het beleid
8. Dubbelklik op **PowerShell-Script blok logboekregistratie kunnen inschakelen**
9. Klik op **ingeschakeld**
10. Klik op **OK** om in te stellen van het beleid
11. (Op domein machines alleen) Voer `gpupdate` of wacht totdat Groepsbeleid voor het verwerken van het bijgewerkte beleid en de instellingen toepassen

U kunt ook systeembrede PowerShell transcriptie via Groepsbeleid inschakelen.

## <a name="next-steps"></a>Volgende stappen

[Maak een bestand van de mogelijkheid rol](role-capabilities.md)

[Een sessie-configuratiebestand maken](session-configurations.md)

## <a name="see-also"></a>Zie ook

[Als u meer informatie over de beveiliging van PowerShell voor externe toegang en WinRM](/powershell/scripting/setup/winrmsecurity)

[*PowerShell ♥ het Blue Team* blogbericht over beveiliging](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)