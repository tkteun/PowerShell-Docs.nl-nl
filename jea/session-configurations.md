---
ms.date: 06/12/2017
keywords: jea powershell beveiliging
title: JEA Sessieconfiguraties
ms.openlocfilehash: 3e5a663be8e7aba09a2592c278224cd892c89a20
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190091"
---
# <a name="jea-session-configurations"></a>JEA Sessieconfiguraties

> Van toepassing op: Windows PowerShell 5.0

Een eindpunt JEA is geregistreerd op een systeem door het maken en registreren van een configuratiebestand van de PowerShell-sessie in een bepaalde manier.
Bepalen van sessieconfiguraties *die* het eindpunt JEA kunt gebruiken, en welke rollen hebben toegang tot.
Ze bepalen ook algemene instellingen die van toepassing op gebruikers van een rol in de sessie JEA.

In dit onderwerp wordt beschreven hoe een configuratiebestand van de PowerShell-sessie maken en een eindpunt JEA registreren.

## <a name="create-a-session-configuration-file"></a>Een configuratiebestand sessie maken

Om een eindpunt JEA registreren, moet u opgeven hoe dat eindpunt moet worden geconfigureerd.
Er zijn veel opties om te overwegen hier, de belangrijkste welke is die toegang moeten hebben tot het eindpunt JEA, welke functies worden ze worden toegewezen, welke identiteit JEA gebruiken onder de dekt en wat de naam van het eindpunt JEA zal zijn.
Deze worden alle gedefinieerd in een configuratiebestand voor PowerShell-sessie die is een PowerShell-gegevensbestand eindigt met de extensie .pssc.

Voer de volgende opdracht voor het maken van een geraamte sessie-configuratiebestand voor JEA eindpunten.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Alleen de meest voorkomende configuratieopties zijn standaard opgenomen in het geraamte bestand.
> Gebruik de `-Full` switch in de gegenereerde voor alle toepasselijke instellingen wilt opnemen.

U kunt het configuratiebestand van de sessie openen in een teksteditor.
De `-SessionType RestrictedRemoteServer` veld geeft aan dat de sessieconfiguratie van de wordt gebruikt door JEA voor beveiligde management.
Sessies is geconfigureerd op deze manier wordt uitgevoerd [NoLanguage modus](https://technet.microsoft.com/library/dn433292.aspx) en hebt u alleen de volgende standaardopdrachten uit 8-(en aliassen) beschikbaar:

- Clear-Host (cls, wissen)
- Exit-PSSession (exsn, afsluiten)
- Get-Command (gcm)
- Get-FormatData
- Help ontvangen
- Meetobject (maatregel)
- Uitgaande standaard
- Select-Object (geselecteerd)

Geen PowerShell-providers beschikbaar zijn en worden dat alle externe programma's (uitvoerbare bestanden, scripts, enzovoort).

Er zijn diverse andere velden die u wilt configureren voor de sessie JEA.
Ze worden in de volgende secties besproken.

### <a name="choose-the-jea-identity"></a>Kies de identiteit JEA

JEA moet achter de schermen wordt een identiteit (account) moet worden gebruikt wanneer een gebruiker verbonden opdrachten uit te voeren.
U besluiten welke identiteit JEA wordt gebruikt in het configuratiebestand van de sessie.

#### <a name="local-virtual-account"></a>Lokale virtuele-Account

Als de rollen die worden ondersteund door dit eindpunt JEA worden gebruikt voor het beheren van de lokale computer en een lokaal beheerdersaccount volstaat om de opdrachten succes is uitgevoerd, moet u JEA voor het gebruik van een lokale virtuele-account configureren.
Virtuele accounts zijn tijdelijke accounts die uniek is voor een specifieke gebruiker en alleen de laatste voor de duur van de PowerShell-sessie.
Op een lidserver of werkstation virtuele accounts deel uitmaken van de lokale computer **beheerders** groeperen en hebben toegang tot de meeste systeembronnen.
Op een Active Directory-domeincontroller virtuele accounts deel uitmaken van het domein **Domeinadministrators** groep.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Als de rollen die worden ondersteund door de sessieconfiguratie geen dergelijke brede bevoegdheden vereist, kunt u eventueel de beveiligingsgroepen waartoe het virtuele-account behoort.
De opgegeven beveiligingsgroepen moet op een lidserver of werkstation lokale groepen, niet voor groepen van een domein.

Wanneer een of meer beveiligingsgroepen wordt opgegeven, wordt niet langer virtueel account aan de beheerdersgroep lokaal of domeinbeheerder behoren.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Door groep beheerd serviceaccount


Een beheerd serviceaccount (gMSA) is voor scenario's vereisen dat de gebruiker JEA voor toegang tot netwerkbronnen zoals andere machines of webservices, een geschiktere identiteit moet worden gebruikt.
gMSA accounts bieden u de identiteit van een domein dat kan worden gebruikt voor verificatie op basis van bronnen op elke computer in het domein.
De rechten van het gMSA-account biedt u wordt bepaald door de bronnen die u wilt openen.
U wordt automatisch geen beheerdersrechten op alle machines of services tenzij de beheerder van de machine-service heeft expliciet verleend voor het gMSA-account beheerdersbevoegdheden.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

accounts van gMSA mag alleen worden gebruikt wanneer toegang tot netwerkbronnen zijn vereist voor een aantal oorzaken hebben:

- Is het moeilijker te traceren terug acties voor een gebruiker wanneer u een beheerd serviceaccount omdat elke gebruiker dezelfde run as-id deelt. U moet Raadpleeg Logboeken correleren van gebruikers met hun acties en transcripties van PowerShell-sessie.

- Het gMSA-account hebben mogelijk toegang tot veel netwerkbronnen die de gebruiker die de verbinding heeft geen toegang tot nodig. Probeert altijd effectieve machtigingen beperken in een sessie JEA volgen het principe van minimale bevoegdheden.

> [!NOTE]
> Groep beheerde serviceaccounts zijn alleen beschikbaar in Windows PowerShell 5.1 of nieuwere en op computers die lid zijn van een domein.


#### <a name="more-information-about-run-as-users"></a>Meer informatie over run as-gebruikers

Meer informatie over uitvoeren als identiteiten en hoe ze rekening te houden in de beveiliging van een sessie JEA vindt u in de [beveiligingsoverwegingen](security-considerations.md) artikel.

### <a name="session-transcripts"></a>Sessie transcripties

Het verdient aanbeveling dat u een configuratiebestand voor JEA sessie automatisch vastleggen uitgeschreven gebruikerssessies configureert.
PowerShell-sessie transcripties bevatten informatie over de gebruiker verbinding maakt, het run as-identiteit is toegewezen, en de opdrachten uitgevoerd door de gebruiker.
Ze kunnen nuttig zijn voor een controle team wil weten wie een bepaalde wijziging in een systeem uitgevoerd.

Voor het configureren van automatische schrijffouten in het configuratiebestand van de sessie, Geef een pad naar een map waar de transcripties moeten worden opgeslagen.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

De opgegeven map moet worden geconfigureerd om te voorkomen dat gebruikers wijzigen of verwijderen van alle gegevens in dit.
Transcripties worden geschreven naar de map door het lokale systeemaccount, waarvoor lees- en schrijftoegang tot de map is vereist.
Standaardgebruikers moeten hebben geen toegang tot de map en een beperkt aantal Beveiligingsbeheerders moet toegang hebben tot de transcripties controleren.

### <a name="user-drive"></a>Schijf van de gebruiker

Als uw gebruikers verbinding moeten voor het kopiëren van bestanden naar het eindpunt JEA om een opdracht wordt uitgevoerd, kunt u de schijf van de gebruiker in het configuratiebestand van de sessie inschakelen.
De schijf van de gebruiker is een [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) die is toegewezen aan een unieke map voor elke gebruiker die verbinding maakt.
Deze map fungeert als een ruimte voor deze bestanden te kopiëren van het systeem zonder zodat ze toegang hebben tot het volledige bestandssysteem of de provider bestandssysteem blootstellen.
De inhoud van de gebruiker stations zijn permanent over de sessies voor situaties waarin de verbinding met het netwerk mag worden onderbroken.

```powershell
MountUserDrive = $true
```

Standaard kunt de schijf van de gebruiker u voor het opslaan van een maximum van 50MB aan gegevens per gebruiker.
U kunt de hoeveelheid gegevens die een gebruiker met gebruiken kunt beperken de *UserDriveMaximumSize* veld.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Als u niet dat de gegevens in het station gebruiker permanent zijn wilt, kunt u een geplande taak op het systeem automatisch opschonen van de map elke nacht configureren.

> [!NOTE]
> De schijf van de gebruiker is alleen beschikbaar in Windows PowerShell 5.1 of hoger.

### <a name="role-definitions"></a>Roldefinities

Roldefinities in een configuratiebestand sessie definiëren de toewijzing van *gebruikers* naar *rollen*.
Elke gebruiker of groep die zijn opgenomen in dit veld wordt automatisch worden gemachtigd voor het eindpunt JEA wanneer deze is geregistreerd.
Elke gebruiker of groep kan worden opgenomen als de sleutel in de hash-tabel slechts één keer, maar kan meerdere functies worden toegewezen.
De naam van de mogelijkheid van de rol moet de naam van het bestand van de rol mogelijkheid zonder de extensie .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Als een gebruiker tot meer dan één groep in de roldefinitie van de behoort, krijgen ze toegang tot de functies van elk.
Als twee rollen toegang tot de dezelfde cmdlets verlenen, wordt de meest strikte parameterset worden toegekend aan de gebruiker.

Bij het opgeven van lokale gebruikers en groepen in het veld rol-definities, moet u de naam van de computer gebruikt (geen *localhost* of *.*) voordat u de backslash.
U kunt de naam van de computer controleren door te inspecteren de `$env:computername` variabele.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Zoekvolgorde van rol mogelijkheid
Zoals u in het bovenstaande voorbeeld, rol mogelijkheden zijn waarnaar wordt verwezen door de platte domeinnaam (bestandsnaam zonder de extensie) van het bestand van de mogelijkheid rol.
Als meerdere rol mogelijkheden beschikbaar op het systeem met dezelfde naam platte zijn, kunnen PowerShell de impliciete zoekvolgorde wordt gebruikt om de effectieve rol mogelijkheid-bestand te selecteren.
Het **niet** toegang geven tot alle rol capability-bestanden met dezelfde naam.

JEA gebruikt de `$env:PSModulePath` omgevingsvariabele om te bepalen welke paden om te scannen op rol capability-bestanden.
In elk van die paden zoekt JEA naar geldige PowerShell-modules die een submap 'RoleCapabilities' bevatten.
Net als bij het importeren van modules, verkiest JEA rol mogelijkheden die worden geleverd met Windows tot mogelijkheden van de aangepaste rol met dezelfde naam.
Voor alle andere naamconflicten wordt prioriteit bepaald door de volgorde waarin Windows de bestanden in de map somt (niet noodzakelijkerwijs alfabetisch).
Het eerste rol mogelijkheid bestand gevonden die overeenkomt met de gewenste naam voor de gebruiker die de verbinding wordt gebruikt.

Aangezien de zoekvolgorde van rol mogelijkheid is niet deterministisch wanneer twee of meer mogelijkheden van de functie dezelfde naam delen, is het **sterk aanbevolen** Zorg ervoor dat functie-mogelijkheden unieke namen hebben op uw computer.

### <a name="conditional-access-rules"></a>Regels voor voorwaardelijke toegang

Alle gebruikers en groepen die zijn opgenomen in het veld RoleDefinitions krijgen automatisch toegang tot JEA eindpunten.
Regels voor voorwaardelijke toegang kunnen u deze toegang verfijnen en gebruikers moeten behoren tot meer beveiligingsgroepen die hebben geen invloed op de rollen die ze zijn toegewezen.
Dit is handig als u integreren van een 'just-in tijd wilt' bevoegde toegang tot oplossing voor het beheer, smartcardverificatie of een andere oplossing multifactor-verificatie met JEA.

Regels voor voorwaardelijke toegang worden gedefinieerd in het veld RequiredGroups in een sessie-configuratiebestand.
Daar kunt u een hash-tabel (eventueel geneste) die gebruikmaakt van bieden 'En' en 'Of' sleutels u uw regels samenstelt.
Hier volgen enkele voorbeelden van hoe u dit veld:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> Regels voor voorwaardelijke toegang zijn alleen beschikbaar in Windows PowerShell 5.1 of hoger.

### <a name="other-properties"></a>Andere eigenschappen
Sessie-configuratiebestanden kunnen alles die een rol mogelijkheid bestand uitvoeren kunt, maar wel zonder de mogelijkheid om te verbinden gebruikerstoegang geven tot andere opdrachten ook doen.
Als u dat alle gebruikers toegang tot bepaalde cmdlets, functies of providers wilt, kunt u doen rechts in het configuratiebestand van de sessie.
Voer voor een volledige lijst met ondersteunde eigenschappen in het configuratiebestand van de sessie `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Een configuratiebestand sessie testen

U kunt testen met een sessie configuratie met de [Test PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.
Het is raadzaam dat u uw configuratiebestand sessie testen als u de voor-bestand handmatig met een teksteditor om te controleren of dat de syntaxis is juist hebt bewerkt.
Als een sessie-configuratiebestand deze test niet slaagt, is het niet mogelijk is op het systeem worden geregistreerd.

## <a name="sample-session-configuration-file"></a>Voorbeeldconfiguratiebestand sessie

Hieronder volgt een voorbeeld van een volledige waarin wordt getoond hoe maakt en valideert de sessieconfiguratie van een voor JEA.
Houd er rekening mee dat de definities van gebruikersrollen worden gemaakt en opgeslagen in de `$roles` variabele voor uw gemak en de leesbaarheid.
Het is niet vereist om dit te doen.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Sessie-configuratiebestanden bijwerken

Als u wijzigen van de eigenschappen van een sessieconfiguratie JEA wilt, met inbegrip van de toewijzing van gebruikers aan rollen, moet u [registratie](register-jea.md#unregistering-jea-configurations) en [opnieuw registreren](register-jea.md) de sessieconfiguratie JEA.
Wanneer u de configuratie van de sessie JEA opnieuw registreren, gebruikt u een bijgewerkte PowerShell-sessie configuratiebestand met de gewenste wijzigingen.

## <a name="next-steps"></a>Volgende stappen

- [De configuratie van een JEA registreren](register-jea.md)
- [Auteur JEA rollen](role-capabilities.md)