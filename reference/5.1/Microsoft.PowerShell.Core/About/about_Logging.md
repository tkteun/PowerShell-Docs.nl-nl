---
description: Power shell registreert interne bewerkingen van de engine, providers en cmdlets.
keywords: powershell
Locale: en-US
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging
ms.openlocfilehash: 5d061b38b5b0fa45cf0a86c2f5b7e0efcb8d1f7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252605"
---
# <a name="about-logging"></a>Over logboek registratie

## <a name="short-description"></a>Korte beschrijving

Power shell registreert interne bewerkingen van de engine, providers en cmdlets.

## <a name="long-description"></a>Lange beschrijving

Power shell registreert gegevens over Power shell-bewerkingen, zoals het starten en stoppen van de engine en providers, en het uitvoeren van Power shell-opdrachten.

> [!NOTE]
> Windows Power shell-versies 3,0, 4,0, 5,0 en 5,1 bevatten **Eventlog** -cmdlets voor de Windows-gebeurtenis Logboeken. In deze versies geeft u de lijst van het type **Eventlog** -cmdlets weer: `Get-Command -Noun EventLog` . Raadpleeg de cmdlet-documentatie en-about_EventLogs voor uw versie van Windows Power shell voor meer informatie.

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a>De logboek vermeldingen van het Power shell-logboek in Windows weer geven

Power shell-logboeken kunnen worden weer gegeven met behulp van de Windows-Logboeken. Het gebeurtenis logboek bevindt zich in de groep toepassings-en service logboeken en heeft de naam `Microsoft-Windows-PowerShell` . De gekoppelde ETW-provider `GUID` is `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}` .

Wanneer de logboek registratie van script blokken is ingeschakeld, registreert Power shell de volgende gebeurtenissen in het `Microsoft-Windows-PowerShell/Operational` logboek:

|Veld| Waarde|
|-|-|
|Gebeurtenis|`4104` / `0x1008`|
|Kanaal|`Operational`|
|Niveau|`Verbose`|
|Code|`Create`|
|Taak|`CommandStart`|
|Zoek|`Runspace`|

## <a name="enabling-script-block-logging"></a>Logboek registratie van script blok inschakelen

Wanneer u logboek registratie van script blokken inschakelt, registreert Power shell de inhoud van alle script blokken die worden verwerkt. Wanneer deze functie is ingeschakeld, wordt deze informatie door een nieuwe Power shell-sessie geregistreerd.

> [!NOTE]
> Het is raadzaam om beveiligde logboek registratie in te scha kelen, zoals hieronder wordt beschreven, wanneer script blok logboek registratie alleen voor diagnostische doel einden wordt gebruikt.

Logboek registratie van script blokken kan worden ingeschakeld via groepsbeleid of een register instelling.

### <a name="using-group-policy"></a>Met behulp van Groepsbeleid

Als u automatische transcriptie wilt inschakelen, schakelt u de `Turn on PowerShell Script Block
Logging` functie in Groepsbeleid in `Administrative Templates -> Windows
Components -> Windows PowerShell` .

### <a name="using-the-registry"></a>Het REGI ster gebruiken

Voer de volgende functie uit:

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a>Beveiligde logboek registratie

Het verhogen van het niveau van logboek registratie op een systeem verhoogt de kans dat geregistreerde inhoud gevoelige gegevens kan bevatten. Als bijvoorbeeld script logboek registratie is ingeschakeld, kunnen referenties of andere gevoelige gegevens die door een script worden gebruikt, naar het gebeurtenis logboek worden geschreven. Wanneer een computer met gevoelige gegevens is aangetast, kunnen de logboeken een aanvaller de benodigde informatie geven om hun bereik te verg Roten.

Voor het beveiligen van deze informatie introduceert Windows 10 beveiligde logboek registratie.
Met logboek registratie van beveiligde gebeurtenissen kunnen deelnemende toepassingen gevoelige gegevens die naar het gebeurtenis logboek zijn geschreven, versleutelen. Later kunt u deze logboeken ontsleutelen en verwerken op een veiligere en gecentraliseerde logboek verzamelaar.

De inhoud van het gebeurtenis logboek wordt beveiligd met de CMS-standaard (Cryptographic Message Syntax). CMS maakt gebruik van open bare-sleutel cryptografie. De sleutels die worden gebruikt voor het versleutelen van inhoud en het ontsleutelen van inhoud worden gescheiden bewaard.

De open bare sleutel kan breed worden gedeeld en kan geen gevoelige gegevens zijn. Alle inhoud die is versleuteld met deze open bare sleutel kan alleen worden ontsleuteld door de persoonlijke sleutel. Zie voor meer informatie over crypto grafie met open bare sleutels [Wikipedia-open bare-sleutel cryptografie](https://en.wikipedia.org/wiki/Public-key_cryptography).

Als u een beleid voor beveiligde logboek registratie wilt inschakelen, implementeert u een open bare sleutel voor alle computers met gebeurtenis logboek gegevens die moeten worden beveiligd. De bijbehorende persoonlijke sleutel wordt gebruikt voor het verwerken van de gebeurtenis logboeken op een veiligere locatie, zoals een centrale gebeurtenis logboek verzamelaar of [Siem][] aggregator. U kunt SIEM instellen in Azure. Zie [algemene Siem-integratie](/cloud-app-security/siem)voor meer informatie.

### <a name="enabling-protected-event-logging-via-group-policy"></a>Beveiligde logboek registratie via groepsbeleid inschakelen

Als u beveiligde logboek registratie wilt inschakelen, schakelt u de `Enable Protected Event Logging` functie in Groepsbeleid in `Administrative Templates -> Windows Components
-> Event Logging` . Voor deze instelling is een versleutelings certificaat vereist, dat u kunt opgeven in een van de volgende formulieren:

- De inhoud van een base-64 Encoded X. 509-certificaat (bijvoorbeeld, zoals aangeboden door de `Export` optie in Certificate Manager).
- De vinger afdruk van een certificaat dat kan worden gevonden in het certificaat archief van de lokale computer (kan worden geïmplementeerd door de PKI-infra structuur).
- Het volledige pad naar een certificaat (kan lokaal of op een externe share zijn).
- Het pad naar een map met een certificaat of certificaten (lokaal of op een externe share).
- De onderwerpnaam van een certificaat dat kan worden gevonden in het certificaat archief van de lokale computer (kan worden geïmplementeerd door de PKI-infra structuur).

Het resulterende certificaat moet `Document Encryption` als Enhanced Key Usage ( `1.3.6.1.4.1.311.80.1` ) en `Data Encipherment` of `Key
Encipherment` sleutel gebruik zijn ingeschakeld.

> [!WARNING]
> De persoonlijke sleutel mag niet worden geïmplementeerd op de computer registratie gebeurtenissen. Het moet worden bewaard op een veilige locatie waar u de berichten ontsleutelt.

### <a name="decrypting-protected-event-logging-messages"></a>Beveiligde gebeurtenis logboek registratie berichten decoderen

Het volgende script wordt opgehaald en ontsleuteld, ervan uitgaande dat u beschikt over de persoonlijke sleutel:

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a>Zie ook

[Het blauwe team van Power shell](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[Algemene SIEM-integratie](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
