---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: JEA Sessieconfiguraties
ms.openlocfilehash: bdf3659357045203d90e8083613e51cce657da1a
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522951"
---
# <a name="jea-session-configurations"></a>JEA Sessieconfiguraties

> Is van toepassing op: Windows PowerShell 5.0

Een JEA-eindpunt is op een systeem door het maken en registreren van een configuratiebestand van de PowerShell-sessie op een specifieke manier geregistreerd.
Sessieconfiguraties bepalen *die* de JEA-eindpunt kunt gebruiken en welke rollen hebben ze toegang tot.
Ze bepalen ook algemene instellingen die van toepassing op gebruikers van een rol in de JEA-sessie.

In dit onderwerp wordt beschreven hoe u een PowerShell-sessie-configuratiebestand maken en registreren van een JEA-eindpunt.

## <a name="create-a-session-configuration-file"></a>Een sessie-configuratiebestand maken

Als u wilt een JEA-eindpunt registreren, moet u opgeven hoe dit eindpunt moet worden geconfigureerd.
Er zijn veel opties om te overwegen, de belangrijkste van welke wordt die toegang moeten hebben tot de JEA-eindpunt, welke functies worden ze worden toegewezen, welke identiteit JEA gebruikt op de achtergrond en wat is de naam van de JEA-eindpunt.
Deze worden alle gedefinieerd in een configuratiebestand voor PowerShell-sessie die is een PowerShell-gegevensbestand eindigt met de extensie .pssc.

Voer de volgende opdracht voor het maken van een minimale sessie-configuratiebestand voor de JEA-eindpunten.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Alleen de meest voorkomende configuratieopties zijn standaard opgenomen in de minimale bestand.
> Gebruik de `-Full` overschakelen naar alle toepasselijke instellingen worden opgenomen in de gegenereerde voor.

U kunt het configuratiebestand van de sessie openen in een teksteditor.
De `-SessionType RestrictedRemoteServer` veld geeft aan dat de sessieconfiguratie van de wordt gebruikt door JEA voor veilig beheer.
Sessies die is geconfigureerd op deze manier wordt uitgevoerd [NoLanguage modus](https://technet.microsoft.com/library/dn433292.aspx) en hebt u alleen de volgende 8 standaardopdrachten (en aliassen) beschikbaar:

- Clear-Host (cls, wissen)
- Afsluiten PSSession (exsn, afsluiten)
- Get-Command (gcm)
- Get-FormatData
- Help ontvangen
- Meting-Object (eenheid)
- Uitgaande standaard
- Select-Object (selecteren)

Er zijn geen PowerShell-providers zijn beschikbaar, noch zijn dat externe programma's (uitvoerbare bestanden, scripts, enzovoort).

Er zijn diverse andere velden die u wilt configureren voor de JEA-sessie.
Ze worden behandeld in de volgende secties.

### <a name="choose-the-jea-identity"></a>Kies de JEA-identiteit

Achter de schermen moet JEA een identiteit (account) om te gebruiken bij het uitvoeren van de gebruiker van een verbonden-opdrachten.
U bepalen welke identiteit JEA wordt gebruikt in het configuratiebestand van de sessie.

#### <a name="local-virtual-account"></a>Lokale virtueel Account

Als de rollen die worden ondersteund door dit JEA-eindpunt worden gebruikt voor het beheren van de lokale computer en een lokale administrator-account voldoende is om de opdrachten succes is uitgevoerd, moet u de JEA voor het gebruik van een lokale virtuele-account configureren.
Virtuele accounts zijn tijdelijke accounts die uniek is voor een specifieke gebruiker en alleen de laatste voor de duur van de PowerShell-sessie.
Op een lidserver of werkstation virtuele accounts deel uitmaken van de lokale computer **beheerders** groep en toegang hebben tot de meeste systeembronnen.
Op een Active Directory-domeincontroller virtuele accounts deel uitmaken van het domein **Domeinadministrators** groep.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Als de rollen die worden ondersteund door de sessieconfiguratie geen dergelijke uitgebreide bevoegdheden vereist, kunt u eventueel de beveiligingsgroepen die de virtuele-account behoort.
Op een lidserver of werkstation zijn de opgegeven beveiligingsgroepen lokale groepen, niet voor groepen van een domein.

Wanneer een of meer beveiligingsgroepen is opgegeven, wordt niet langer de virtuele account aan de beheerdersgroep lokaal of domein behoren.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>Door groep beheerd serviceaccount


Voor scenario's vereisen dat de JEA-gebruiker voor toegang tot netwerkbronnen, zoals andere computers of webservices, is een groep beheerd serviceaccount (gMSA) een geschiktere identiteit te gebruiken.
gMSA-accounts bieden u een domein-id die kan worden gebruikt voor verificatie op basis van resources op elke computer in het domein.
De rechten van het gMSA-account biedt u wordt bepaald door de resources die u wilt openen.
U wordt automatisch geen beheerdersrechten op alle machines of services, tenzij de machine/service-beheerder heeft expliciet verleend voor het gMSA-account beheerdersbevoegdheden.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

gMSA-accounts moeten alleen worden gebruikt wanneer toegang tot netwerkbronnen zijn vereist voor een aantal oorzaken hebben:

- Is het moeilijker om te traceren terug acties aan een gebruiker bij het gebruik van een gMSA-account, omdat elke gebruiker dezelfde run as-id deelt. U moet moet u de PowerShell-sessie transcripties en logboeken correleren van gebruikers met hun acties.

- Het gMSA-account hebben mogelijk toegang tot veel netwerkbronnen die de gebruiker die de verbinding heeft geen toegang nodig tot. Probeer altijd aan de effectieve machtigingen beperken in een JEA-sessie te volgen het principe van minimale bevoegdheden.

> [!NOTE]
> Groep beheerde serviceaccounts zijn alleen beschikbaar in Windows PowerShell 5.1 of hoger en op domein systemen.


#### <a name="more-information-about-run-as-users"></a>Meer informatie over run as-gebruikers

Als u meer informatie over uitvoeren als-id's en hoe ze factor in de beveiliging van een JEA-sessie te vinden in de [beveiligingsoverwegingen](security-considerations.md) artikel.

### <a name="session-transcripts"></a>Transcripten van sessie

Het is raadzaam dat u een JEA-sessie-configuratiebestand op automatisch vastleggen Transcripten van gebruikerssessies configureert.
PowerShell-sessie Transcripten bevatten informatie over de gebruiker verbinding maakt, het uitvoeren als-identiteit is toegewezen, en de opdrachten worden uitgevoerd door de gebruiker.
Ze kunnen nuttig zijn voor een beoordelingsteam die nodig heeft om te begrijpen wie een specifieke wijziging in een systeem hebt uitgevoerd.

Voor het configureren van automatische transcriptie in het configuratiebestand van de sessie, Geef een pad naar een map waar de Transcripten moeten worden opgeslagen.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

De opgegeven map moet worden geconfigureerd om te voorkomen dat gebruikers van wijzigt of verwijdert alle gegevens in het.
Transcripten worden geschreven naar de map met het lokale systeemaccount, waarvoor lezen en schrijven toegang tot de map is vereist.
Standaardgebruikers kunnen geen toegang moeten hebben tot de map en een beperkte set van administrators voor rapportbeveiliging moet toegang hebben tot de Transcripten controleren.

### <a name="user-drive"></a>Schijf van de gebruiker

Als uw verbindende gebruikers moeten het kopiëren van bestanden naar/van de JEA-eindpunt om uit te voeren van een opdracht, kunt u de schijf van de gebruiker in het configuratiebestand van de sessie inschakelen.
De schijf van de gebruiker is een [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) die is toegewezen aan een unieke map voor elke gebruiker die verbinding maakt.
Deze map fungeert als een ruimte voor deze bestanden te kopiëren naar/van het systeem zonder zodat ze toegang hebben tot het volledige systeem of de provider bestandssysteem om vrij te geven.
De inhoud van de gebruiker stations zijn persistent in verschillende sessies voor situaties waar de verbinding met het netwerk kan worden onderbroken.

```powershell
MountUserDrive = $true
```

Standaard kunt de schijf van de gebruiker u voor het opslaan van een maximum van 50MB aan gegevens per gebruiker.
U kunt de hoeveelheid gegevens die een gebruiker kan worden gebruikt met beperken de *UserDriveMaximumSize* veld.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Als u niet dat gegevens in de schijf van de gebruiker permanent zijn wilt, kunt u een geplande taak configureren op het systeem voor het automatisch opschonen van de map elke nacht.

> [!NOTE]
> De schijf van de gebruiker is alleen beschikbaar in Windows PowerShell 5.1 of hoger.

### <a name="role-definitions"></a>Roldefinities

Roldefinities in een sessie-configuratiebestand definieert de toewijzing van *gebruikers* naar *rollen*.
Elke gebruiker of groep die zijn opgenomen in dit veld wordt automatisch een machtiging verleend de JEA-eindpunt wanneer deze is geregistreerd.
Elke gebruiker of groep kan worden opgenomen als een sleutel in de hash-tabel slechts één keer, maar meerdere rollen kan worden toegewezen.
De naam van de mogelijkheid van de rol moet de naam van het bestand van een rol mogelijkheid, zonder de extensie .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Als een gebruiker tot meer dan één groep in het roldefinitie van de behoort, krijgt zij toegang tot de functies van elk.
Als twee rollen toegang tot de dezelfde cmdlets verleent, worden de meest strikte parameterset wordt toegekend aan de gebruiker.

Bij het opgeven van lokale gebruikers en groepen in het veld van de definities rol, zorg ervoor dat u de naam van de computer (niet *localhost* of *.*) voor de backslash opgeeft.
U kunt de naam van de computer controleren door het inspecteren van de `$env:computername` variabele.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Zoekvolgorde van rol mogelijkheid
Zoals u in het bovenstaande voorbeeld, rolmogelijkheden zijn waarnaar wordt verwezen door de platte domeinnaam (bestandsnaam zonder extensie) van het bestand van de mogelijkheid rol.
Als meerdere functie-mogelijkheden beschikbaar op het systeem met dezelfde naam platte zijn, kunnen PowerShell de impliciete zoekvolgorde wordt gebruikt om de effectieve rol mogelijkheid-bestand te selecteren.
Het wordt **niet** toegang geven tot alle rol mogelijkheid bestanden met dezelfde naam.

JEA maakt gebruik van de `$env:PSModulePath` omgevingsvariabele om te bepalen welke paden om te scannen op rol mogelijkheid bestanden.
Binnen elk van deze paden zoekt JEA naar geldige PowerShell-modules die een submap 'RoleCapabilities' bevatten.
Net als bij importeren van modules, verkiest JEA rolmogelijkheden die worden geleverd met Windows op de mogelijkheden van de aangepaste rol met dezelfde naam.
Voor alle andere naamconflicten wordt prioriteit bepaald door de volgorde waarin Windows de bestanden in de map inventariseert (niet noodzakelijkerwijs worden alfabetisch).
Het eerste bestand van de rol-mogelijkheid gevonden die overeenkomt met de gewenste naam wordt gebruikt voor de gebruiker die verbinding maakt.

Aangezien de zoekvolgorde van rol mogelijkheid is niet deterministisch wanneer twee of meer rolmogelijkheden dezelfde naam delen, is het **sterk aanbevolen** Zorg ervoor dat rolmogelijkheden unieke namen hebben op uw computer.

### <a name="conditional-access-rules"></a>Regels voor voorwaardelijke toegang

Alle gebruikers en groepen die zijn opgenomen in het veld RoleDefinitions worden automatisch verleend voor toegang tot de JEA-eindpunten.
Regels voor voorwaardelijke toegang kunnen u deze toegang verfijnen en vereisen dat gebruikers deel uitmaken van aanvullende beveiligingsgroepen die niet van invloed op de rollen die zijn toegewezen.
Dit is handig als u integreren een 'just in time wilt' in beschermde modus toegang krijgen tot de oplossing voor het beheer, smartcardverificatie of andere oplossing voor meervoudige verificatie met JEA.

Regels voor voorwaardelijke toegang worden gedefinieerd in het veld RequiredGroups in een sessie-configuratiebestand.
Daar kunt u een hash-tabel (eventueel geneste) die gebruikmaakt van bieden 'En' en 'Of' sleutels te maken van uw regels.
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
Sessie-configuratiebestanden kunnen ook doen alles wat die een bestand van de mogelijkheid rol doen kunt, maar wel zonder de mogelijkheid om te verbinden gebruikerstoegang geven tot andere opdrachten.
Als u wilt dat alle gebruikers toegang tot bepaalde cmdlets, functies of -providers, kunt u doen rechts in het configuratiebestand van de sessie.
Voor een volledige lijst van ondersteunde eigenschappen in het configuratiebestand van de sessie, voert u `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Testen van een sessie-configuratiebestand

U kunt testen met een sessie configureren met behulp van de [Test PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.
Het is raadzaam dat u het configuratiebestand van de sessie testen als u hebt de voor-bestand handmatig met behulp van een teksteditor om te controleren of dat de syntaxis juist is bewerkt.
Als een sessie-configuratiebestand deze test niet slaagt, is het niet mogelijk om te worden geregistreerd op het systeem.

## <a name="sample-session-configuration-file"></a>Voorbeeldconfiguratiebestand sessie

Hieronder volgt een compleet voorbeeld waarin wordt getoond hoe maakt en valideert de sessieconfiguratie van een voor JEA.
Houd er rekening mee dat de definities van gebruikersrollen worden gemaakt en opgeslagen in de `$roles` variabele voor uw gemak en leesbaarheid.
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

## <a name="updating-session-configuration-files"></a>Bijwerken van de sessie-configuratiebestanden

Als u wijzigen eigenschappen van een JEA-sessieconfiguratie wilt, met inbegrip van de toewijzing van gebruikers aan rollen, moet u [registratie](register-jea.md#unregistering-jea-configurations) en [opnieuw registreren](register-jea.md) de JEA-sessieconfiguratie.
Als u de JEA-sessieconfiguratie opnieuw registreert, een bijgewerkte PowerShell-sessie configuratiebestand gebruiken met de gewenste wijzigingen.

## <a name="next-steps"></a>Volgende stappen

- [Een JEA-configuratiegegevens registreren](register-jea.md)
- [De auteur van JEA-rollen](role-capabilities.md)