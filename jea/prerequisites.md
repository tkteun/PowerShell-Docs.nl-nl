---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea powershell beveiliging
title: JEA vereisten
ms.openlocfilehash: e6ee16e34eb9f1f0b2f3601c1aa9e90ab4f785f1
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="prerequisites"></a>Vereisten

> Van toepassing op: Windows PowerShell 5.0

Net genoeg Administration is een functie met Windows PowerShell 5.0 en hoger.
Dit onderwerp beschrijft de vereisten waaraan moeten worden voldaan om te beginnen met behulp van JEA.

## <a name="install-jea"></a>JEA installeren

JEA is beschikbaar met Windows PowerShell 5.0 en hoger, maar voor de volledige functionaliteit wordt aanbevolen dat u de nieuwste versie van PowerShell beschikbaar voor uw systeem installeert.
De volgende tabel beschrijft de beschikbaarheid van JEA op Windows Server:

Server-besturingssysteem   | JEA beschikbaarheid
--------------------------|--------------------------------
Windows Server 2016       | Vooraf geïnstalleerd
Windows Server 2012 R2    | De volledige functionaliteit met WMF 5.1
Windows Server 2012       | De volledige functionaliteit met WMF 5.1
Windows Server 2008 R2    | Verminderde functionaliteit<sup>1</sup> met WMF 5.1

U kunt ook JEA gebruiken op uw computer thuisnetwerk of:

Client-besturingssysteem   | JEA beschikbaarheid
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Vooraf geïnstalleerd
Windows 10 1603, 1511     | Vooraf is geïnstalleerd, met verminderde functionaliteit<sup>2</sup>
Windows 10 1507           | Niet beschikbaar
Windows 8, 8.1            | De volledige functionaliteit met WMF 5.1
Windows 7                 | Verminderde functionaliteit<sup>1</sup> met WMF 5.1

<sup>1</sup> JEA kan niet worden geconfigureerd voor het gebruik van beheerde serviceaccounts voor groepen op Windows Server 2008 R2 of Windows 7.
Virtuele accounts en andere functies JEA *zijn* ondersteund.

<sup>2</sup> Windows 10 versie 1511 en 1603 bieden geen ondersteuning voor de volgende functies van JEA: uitgevoerd als een groep beheerd serviceaccount, regels voor voorwaardelijke toegang in sessieconfiguraties, de schijf van de gebruiker en het verlenen van toegang aan lokale gebruikersaccounts.
Als u ondersteuning voor deze functies, Windows bijwerken naar versie 1607 (Verjaardag bijwerken) of hoger.

### <a name="check-which-version-of-powershell-is-installed"></a>Controleren welke versie van PowerShell is geïnstalleerd

Als u wilt controleren welke versie van PowerShell is geïnstalleerd op uw systeem, Controleer de `$PSVersionTable` variabele in een Windows PowerShell-prompt.

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Bent u klaar voor gebruik van JEA als de *belangrijke* versie is groter dan of gelijk aan **5**.
Voor de beste ervaring, en toegang hebben tot de nieuwste functies, is het raadzaam dat u een naar de PowerShell-versie upgrade **5.1** indien mogelijk.

### <a name="install-windows-management-framework"></a>Installeer Windows Management Framework

Als u een oudere versie van PowerShell uitvoert, moet u uw systeem bijwerken met de nieuwste update van Windows Management Framework (WMF).
Updatepakketten en een koppeling naar de meest recente release-opmerkingen van WMF zijn beschikbaar in de [Downloadcentrum](https://aka.ms/WMF5).

Het is raadzaam dat u de compatibiliteit van uw workload met WMF test vóór de upgrade van al uw servers.

Windows 10-gebruikers moeten de meest recente updates van de functie voor het ophalen van de huidige versie van Windows PowerShell installeren.

## <a name="enable-powershell-remoting"></a>PowerShell op afstand inschakelen

Externe communicatie van PowerShell vormt de basis waarop JEA is gebouwd.
Het is daarom nodig om te controleren of externe communicatie van PowerShell is ingeschakeld en [goed beveiligde](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) op uw systeem voordat u JEA kunt gebruiken.

Externe communicatie van PowerShell is standaard ingeschakeld op Windows Server 2012 en 2012 R2 2016.
U kunt PowerShell voor externe toegang inschakelen door de volgende opdracht in een PowerShell-venster met verhoogde bevoegdheid.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>PowerShell-module en script blok logboekregistratie (optioneel) inschakelen

De volgende stappen schakelt logboekregistratie in voor alle PowerShell-acties op uw systeem.
Logboekregistratie van PowerShell-Module is niet vereist voor JEA, maar het wordt ten zeerste aangeraden dat u deze inschakelen om te controleren of de gebruikers opdrachten uitvoeren op een centrale locatie worden geregistreerd.

U kunt de PowerShell-Module logboekregistratie beleid via Groepsbeleid configureren.

1. Open de Editor voor lokaal groepsbeleid op een werkstation of a Group Policy Object in de Console Groepsbeleidsbeheer op een Active Directory-domeincontroller
2. Navigeer naar **Computerconfiguratie\\Beheersjablonen\\Windows-onderdelen\\Windows PowerShell**
3. Dubbelklik op **Module logboekregistratie inschakelen**
4. Klik op **ingeschakeld**
5. Klik in de sectie opties op **weergeven** naast de namen van Statusberichtmodule
6. Type '**\***' in het pop-upvenster. Dit geïnstrueerd PowerShell aan te melden opdrachten van alle modules.
7. Klik op **OK** aan het beleid instellen
8. Dubbelklik op **PowerShell Script blok logboekregistratie inschakelen**
9. Klik op **ingeschakeld**
10. Klik op **OK** aan het beleid instellen
11. (Op domein machines alleen) Voer **gpupdate** of wacht totdat Groepsbeleid voor het verwerken van het bijgewerkte beleid en de instellingen toepassen

U kunt ook hele systeem PowerShell schrijffouten via Groepsbeleid inschakelen.

## <a name="next-steps"></a>Volgende stappen

- [Maak een bestand van de mogelijkheid rol](role-capabilities.md)
- [Een configuratiebestand sessie maken](session-configurations.md)

## <a name="see-also"></a>Zie ook

- [Als u meer informatie over de beveiliging PowerShell voor externe toegang en WinRM](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [*PowerShell ♥ het Team van blauw* blogbericht op beveiliging](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

