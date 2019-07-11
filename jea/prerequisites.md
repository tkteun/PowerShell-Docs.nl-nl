---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: JEA-vereisten
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734294"
---
# <a name="prerequisites"></a>Vereisten

Just Enough Administration is een functie die is opgenomen in PowerShell 5.0 en hoger. Dit artikel beschrijft de vereisten waaraan moeten worden voldaan aan de slag met JEA.


## <a name="check-which-version-of-powershell-is-installed"></a>Controleren welke versie van PowerShell is geïnstalleerd

Als u wilt controleren welke versie van PowerShell is geïnstalleerd op uw systeem, Controleer de `$PSVersionTable` variabele in een Windows PowerShell-prompt.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA is beschikbaar met PowerShell 5.0 en hoger. Voor de volledige functionaliteit, wordt het aanbevolen dat u de meest recente versie van PowerShell beschikbaar voor uw systeem installeert. De volgende tabel beschrijft de beschikbaarheid van JEA op Windows Server:

| Server-besturingssysteem |                JEA-beschikbaarheid                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016+    | Vooraf is geïnstalleerd                                   |
| Windows Server 2012 R2  | Volledige functionaliteit met WMF 5.1                |
| Windows Server 2012     | Volledige functionaliteit met WMF 5.1                |
| Windows Server 2008 R2  | Verminderde functionaliteit<sup>1</sup> met WMF 5.1 |

U kunt ook JEA gebruiken op uw computer thuis of werk:

| Client-besturingssysteem |                   JEA-beschikbaarheid                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Vooraf is geïnstalleerd                                         |
| Windows 10 1603, 1511   | Vooraf is geïnstalleerd, met verminderde functionaliteit<sup>2</sup> |
| Windows 10 1507         | Niet beschikbaar                                        |
| Windows 8, 8.1          | Volledige functionaliteit met WMF 5.1                      |
| Windows 7               | Verminderde functionaliteit<sup>1</sup> met WMF 5.1       |

- <sup>1</sup> JEA kan niet worden geconfigureerd voor het gebruik van de groep beheerde serviceaccounts op Windows Server 2008 R2 of Windows 7. Virtuele accounts en andere functies JEA *zijn* ondersteund.

- <sup>2</sup> de volgende JEA-functies worden niet ondersteund op Windows 10 versie 1511 en 1603:

  - Service wordt uitgevoerd als een groep beheerd serviceaccount
  - Regels voor voorwaardelijke toegang in sessieconfiguraties
  - De schijf van de gebruiker
  - Verlenen van toegang tot lokale gebruikersaccounts

  Voor ondersteuning voor deze functies kunt bijwerken van Windows naar versie 1607 (Jubileumupdate) of hoger.

### <a name="install-windows-management-framework"></a>Installeer Windows Management Framework

Als u een oudere versie van PowerShell uitvoert, moet u mogelijk uw systeem bijwerken met de meest recente update van Windows Management Framework (WMF). Zie voor meer informatie de [WMF documentatie](/powershell/wmf/overview).

Het raadzaam dat u de compatibiliteit van uw workload met WMF testen vóór de upgrade van al uw servers.

Gebruikers van Windows 10 moeten de nieuwste functie-updates voor het ophalen van de huidige versie van Windows PowerShell installeren.

## <a name="enable-powershell-remoting"></a>Externe communicatie met PowerShell

Externe communicatie van PowerShell vormt de basis waarop JEA is gebouwd. Het is noodzakelijk om ervoor te zorgen voor externe communicatie van PowerShell is ingeschakeld en naar behoren zijn beveiligd voordat u de JEA kunt gebruiken. Zie voor meer informatie, [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).

Externe communicatie van PowerShell is standaard ingeschakeld op Windows Server 2012, 2012 R2 en 2016. U kunt PowerShell voor externe toegang inschakelen door het uitvoeren van de volgende opdracht uit in een PowerShell-venster met verhoogde bevoegdheid.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>PowerShell-module en (optioneel) script blok-logboekregistratie inschakelen

De volgende stappen schakelt logboekregistratie voor alle PowerShell-bewerkingen op uw systeem. Logboekregistratie van PowerShell-Module is niet vereist voor JEA, maar het wordt aangeraden u logboekregistratie om te controleren of de gebruikers opdrachten uitvoeren inschakelen bent aangemeld op een centrale locatie.

U kunt het beleid voor logboekregistratie van PowerShell-Module met behulp van Groepsbeleid configureren.

1. Open de Editor voor lokaal groepsbeleid op een werkstation of een Group Policy Object in de Console Groepsbeleidsbeheer op een Active Directory-domeincontroller
2. Navigeer naar **Computerconfiguratie\\Beheersjablonen\\Windows-onderdelen\\Windows PowerShell**
3. Dubbelklik op **Module logboekregistratie inschakelen**
4. Klik op **ingeschakeld**
5. Klik in de sectie opties op **weergeven** naast modulenamen
6. Type `*` in het pop-upvenster om aan te melden opdrachten van alle modules.
7. Klik op **OK** om in te stellen van het beleid
8. Dubbelklik op **PowerShell-Script-blok logboekregistratie inschakelen**
9. Klik op **ingeschakeld**
10. Klik op **OK** om in te stellen van het beleid
11. (Op domein machines alleen) Voer `gpupdate` of wacht totdat Groepsbeleid voor het verwerken van het bijgewerkte beleid en de instellingen toepassen

U kunt ook systeembrede PowerShell transcriptie via Groepsbeleid inschakelen.

## <a name="next-steps"></a>Volgende stappen

[Maak een bestand van de mogelijkheid rol](role-capabilities.md)

[Een sessie-configuratiebestand maken](session-configurations.md)

## <a name="see-also"></a>Zie ook

[WinRM-beveiliging](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ het Blue Team](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
