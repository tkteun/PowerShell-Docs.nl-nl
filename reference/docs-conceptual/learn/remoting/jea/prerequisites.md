---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: Vereisten voor JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017935"
---
# <a name="prerequisites"></a>Vereisten

Net genoeg beheer is een functie die is opgenomen in Power shell 5,0 en hoger. In dit artikel worden de vereisten beschreven waaraan moet worden voldaan om JEA te kunnen gebruiken.


## <a name="check-which-version-of-powershell-is-installed"></a>Controleren welke versie van Power shell is geïnstalleerd

Als u wilt controleren welke versie van Power shell op uw systeem is geïnstalleerd `$PSVersionTable` , controleert u de variabele in een Windows Power shell-prompt.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA is beschikbaar met Power shell 5,0 en hoger. Voor volledige functionaliteit is het raadzaam om de meest recente versie van Power shell te installeren die beschikbaar is voor uw systeem. In de volgende tabel wordt de beschik baarheid van JEA op Windows Server beschreven:

| Server-besturings systeem |                JEA-Beschik baarheid                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016 +    | Vooraf geïnstalleerd                                   |
| Windows Server 2012 R2  | Volledige functionaliteit met WMF 5,1                |
| Windows Server 2012     | Volledige functionaliteit met WMF 5,1                |
| Windows Server 2008 R2  | Verminderde functionaliteit<sup>1</sup> met WMF 5,1 |

U kunt JEA ook gebruiken op uw computer thuis of op het werk:

| Besturings systeem van client |                   JEA-Beschik baarheid                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Vooraf geïnstalleerd                                         |
| Windows 10 1603, 1511   | Vooraf geïnstalleerd, met beperkte functionaliteit<sup>2</sup> |
| Windows 10 1507         | Niet beschikbaar                                        |
| Windows 8, 8.1          | Volledige functionaliteit met WMF 5,1                      |
| Windows 7               | Verminderde functionaliteit<sup>1</sup> met WMF 5,1       |

- <sup>1</sup> JEA kan niet worden geconfigureerd voor het gebruik van door groepen beheerde service accounts in windows server 2008 R2 of Windows 7. Virtuele accounts en andere JEA-functies *worden* ondersteund.

- <sup>2</sup> de volgende JEA-functies worden niet ondersteund in Windows 10 versie 1511 en 1603:

  - Uitvoeren als een door een groep beheerd service account
  - Regels voor voorwaardelijke toegang in sessie configuraties
  - Het gebruikers station
  - Toegang verlenen tot lokale gebruikers accounts

  Als u ondersteuning voor deze functies wilt, werkt u Windows bij naar versie 1607 (jubileum update) of hoger.

### <a name="install-windows-management-framework"></a>Windows Management Framework installeren

Als u een oudere versie van Power shell gebruikt, moet u mogelijk uw systeem bijwerken met de meest recente Windows Management Framework (WMF)-update. Raadpleeg de [WMF-documentatie](/powershell/wmf/overview)voor meer informatie.

Het is raadzaam om de compatibiliteit van uw werk belasting met WMF te testen voordat u de upgrade van alle servers uitvoert.

Windows 10-gebruikers moeten de nieuwste functie-updates installeren om de huidige versie van Windows Power shell te verkrijgen.

## <a name="enable-powershell-remoting"></a>Externe communicatie met Power shell inschakelen

Externe communicatie met Power shell biedt de basis waarop JEA is gebouwd. Het is nood zakelijk om ervoor te zorgen dat externe communicatie van Power shell is ingeschakeld en goed wordt beveiligd voordat u JEA kunt gebruiken. Zie [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity)(Engelstalig) voor meer informatie.

Externe communicatie van Power shell is standaard ingeschakeld op Windows Server 2012, 2012 R2 en 2016. U kunt externe communicatie van Power shell inschakelen door de volgende opdracht uit te voeren in een Power shell-venster met verhoogde bevoegdheden.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Power shell-module en logboek registratie van script blokken inschakelen (optioneel)

Met de volgende stappen kunt u logboek registratie inschakelen voor alle Power shell-acties op uw systeem. Logboek registratie van de Power shell-module is niet vereist voor JEA, maar het is raadzaam om logboek registratie in te scha kelen om ervoor te zorgen dat de opdrachten die gebruikers uitvoeren, worden geregistreerd op een centrale locatie.

U kunt het beleid voor logboek registratie van Power shell-modules configureren met behulp van groepsbeleid.

1. Open de Lokale groepsbeleidsobjecteditor op een werk station of een groepsbeleid-object in de console Groepsbeleidbeheer op een Active Directory-domein controller
2. Navigeren naar **computer configuratie\\Beheersjablonen\\Windows-\\onderdelen Windows Power shell**
3. Dubbel klik op **inschakelen logboek registratie** van de module
4. Klik op **ingeschakeld**
5. Klik in de sectie opties op **weer geven** naast module namen
6. Typ `*` in het pop-upvenster om opdrachten van alle modules te registreren.
7. Klik op **OK** om het beleid in te stellen
8. Dubbel klik op **inschakelen logboek registratie van Power shell-script blokken**
9. Klik op **ingeschakeld**
10. Klik op **OK** om het beleid in te stellen
11. (Alleen op computers die lid zijn van een domein) Uitvoeren `gpupdate` of wachten tot Groepsbeleid het bijgewerkte beleid verwerkt en de instellingen toepast

U kunt ook de systeembrede Power shell-transcriptie inschakelen via groepsbeleid.

## <a name="next-steps"></a>Volgende stappen

[Een functie-mogelijkheidsprofiel maken](role-capabilities.md)

[Een configuratie bestand voor de sessie maken](session-configurations.md)

## <a name="see-also"></a>Zie ook

[WinRM-beveiliging](/powershell/scripting/learn/remoting/winrmsecurity)

[Power shell ♥ het blauwe team](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
