---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: JEA Sessieconfiguraties
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726545"
---
# <a name="jea-session-configurations"></a>JEA Sessieconfiguraties

Een JEA-eindpunt is geregistreerd op een systeem door het maken en registreren van een configuratiebestand van de PowerShell-sessie. Sessieconfiguraties definiëren die de JEA-eindpunt kunt gebruiken en welke functies ze toegang hebben. Ze bepalen ook algemene instellingen die betrekking hebben op alle gebruikers van de JEA-sessie.

## <a name="create-a-session-configuration-file"></a>Een sessie-configuratiebestand maken

Voor het registreren van een JEA-eindpunt, moet u opgeven hoe dit eindpunt is geconfigureerd. Er zijn veel opties om te overwegen. De belangrijkste opties zijn:

- Wie heeft toegang tot de JEA-eindpunt
- Welke functies ze worden toegewezen
- Welke identiteit JEA wordt gebruikt op de achtergrond
- De naam van de JEA-eindpunt

Deze opties zijn gedefinieerd in een bestand met PowerShell met een `.pssc` extensie bekend als een configuratiebestand van de PowerShell-sessie. Het configuratiebestand van de sessie kan worden bewerkt met behulp van een teksteditor.

Voer de volgende opdracht om te maken van een lege sjabloon-configuratiebestand.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Alleen de meest voorkomende configuratieopties zijn standaard opgenomen in het sjabloonbestand. Gebruik de `-Full` overschakelen naar alle toepasselijke instellingen worden opgenomen in de gegenereerde voor.

De `-SessionType RestrictedRemoteServer` veld geeft aan dat de sessieconfiguratie van de wordt gebruikt door JEA voor veilig beheer. Sessies van dit type werken in **NoLanguage** modus en hebben alleen toegang tot de volgende standaardopdrachten (en aliassen):

- Clear-Host (cls, wissen)
- Afsluiten PSSession (exsn, afsluiten)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Meting-Object (eenheid)
- Uitgaande standaard
- Select-Object (selecteren)

Er zijn geen PowerShell-providers zijn beschikbaar, noch zijn dat externe programma's (uitvoerbare bestanden of scripts).

Zie voor meer informatie over de modi van taal [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).

### <a name="choose-the-jea-identity"></a>Kies de JEA-identiteit

Achter de schermen moet JEA een identiteit (account) om te gebruiken bij het uitvoeren van de gebruiker van een verbonden-opdrachten.
Definieert u welke identiteit JEA wordt gebruikt in het configuratiebestand van de sessie.

#### <a name="local-virtual-account"></a>Lokale virtueel Account

Lokale virtuele accounts zijn handig als alle rollen die zijn gedefinieerd voor de JEA-eindpunt worden gebruikt voor het beheren van de lokale computer en een lokale administrator-account voldoende is voor een geslaagde uitvoering van de opdrachten.
Virtuele accounts zijn tijdelijke accounts die uniek is voor een specifieke gebruiker en alleen de laatste voor de duur van de PowerShell-sessie. Op een lidserver of werkstation virtuele accounts deel uitmaken van de lokale computer **beheerders** groep. Op een Active Directory-domeincontroller virtuele accounts deel uitmaken van het domein **Domeinadministrators** groep.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Als de rollen die zijn gedefinieerd door de sessieconfiguratie is volledige Administrator-bevoegdheden niet vereist, kunt u de beveiligingsgroepen die de virtuele-account behoort. Op een lidserver of werkstation zijn de opgegeven beveiligingsgroepen lokale groepen, niet voor groepen van een domein.

Wanneer een of meer beveiligingsgroepen zijn opgegeven, worden de virtuele-account is niet toegewezen aan de beheerdersgroep lokaal of domein.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Virtuele accounts krijgen tijdelijk de aanmelden als een service rechts in het beveiligingsbeleid van de lokale server. Als een van de opgegeven VirtualAccountGroups is al toegekend dit recht in het beleid, worden de afzonderlijke virtuele account niet meer toegevoegd en verwijderd uit het beleid. Dit kan zijn nuttig in scenario's zoals domeincontrollers waarbij wijzigingen aan het beveiligingsbeleid voor domeincontroller nauw worden gecontroleerd. Dit is alleen beschikbaar in Windows Server 2016 met de November 2018 of later updatepakket en Windows Server 2019 met de 2019 januari of later updatepakket.

#### <a name="group-managed-service-account"></a>Groep beheerd serviceaccount

Een groep beheerd serviceaccount (GMSA) is de juiste identiteit moet worden gebruikt wanneer de JEA-gebruikers nodig hebben voor toegang tot netwerkbronnen zoals bestandsshares en webservices. Gmsa's bieden u een domein-id die wordt gebruikt voor verificatie met resources op elke computer in het domein. De rechten die een GMSA biedt worden bepaald door de resources die u toegang wilt krijgen tot. U hebt geen beheerdersrechten op alle machines of services, tenzij deze rechten aan de voor GMSA expliciet door de machine of service-beheerder heeft verleend.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

Gmsa's moeten alleen worden gebruikt wanneer dat nodig is:

- Het is moeilijk te traceren terug acties aan een gebruiker bij het gebruik van een GMSA. Elke gebruiker deelt dezelfde run as-id. U moet PowerShell-sessie transcripties en logboeken correleren van afzonderlijke gebruikers met hun acties controleren.

- De GMSA hebben mogelijk toegang tot veel netwerkbronnen die gebruiker die de verbinding niet tot nodig. Probeer altijd aan de effectieve machtigingen beperken in een JEA-sessie te volgen het principe van minimale bevoegdheden.

> [!NOTE]
> Groep beheerde serviceaccounts zijn alleen beschikbaar op een domein machines met behulp van PowerShell 5.1 of hoger.

Zie voor meer informatie over het beveiligen van een JEA-sessie de [beveiligingsoverwegingen](security-considerations.md) artikel.

### <a name="session-transcripts"></a>Transcripten van sessie

Het verdient aanbeveling dat u een JEA-eindpunt automatisch vastleggen uitgeschreven van gebruikerssessies configureert. PowerShell-sessie Transcripten bevatten informatie over de gebruiker verbinding maakt, het uitvoeren als-identiteit is toegewezen, en de opdrachten worden uitgevoerd door de gebruiker. Ze kunnen nuttig zijn voor een beoordelingsteam die nodig heeft om te begrijpen die een specifieke wijziging hebt aangebracht in een systeem.

Voor het configureren van automatische transcriptie in het configuratiebestand van de sessie, Geef een pad naar een map waar de Transcripten moeten worden opgeslagen.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Transcripten worden geschreven naar de map met de **lokaal systeem** account waarvoor u lees- en schrijftoegang tot de map. Standaardgebruikers moeten geen toegang hebben tot de map. Beperk het aantal administrators voor rapportbeveiliging in die toegang hebben tot de Transcripten controleren.

### <a name="user-drive"></a>Schijf van de gebruiker

Als uw verbindende gebruikers nodig hebt om bestanden te kopiëren naar of van de JEA-eindpunt, kunt u de schijf van de gebruiker in het configuratiebestand van de sessie inschakelen. De schijf van de gebruiker is een **PSDrive** die is toegewezen aan een unieke map voor elke gebruiker die verbinding maakt. Deze map kan gebruikers bestanden te kopiëren naar of van het systeem zonder zodat ze toegang hebben tot het volledige systeem of de provider bestandssysteem om vrij te geven. De inhoud van de gebruiker stations zijn persistent in verschillende sessies voor situaties waar de verbinding met het netwerk kan worden onderbroken.

```powershell
MountUserDrive = $true
```

Standaard kunt de schijf van de gebruiker u voor het opslaan van een maximum van 50MB aan gegevens per gebruiker. U kunt de hoeveelheid gegevens die een gebruiker kan worden gebruikt met beperken de *UserDriveMaximumSize* veld.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Als u niet dat gegevens in de schijf van de gebruiker permanent zijn wilt, kunt u een geplande taak configureren op het systeem voor het automatisch opschonen van de map elke nacht.

> [!NOTE]
> De schijf van de gebruiker is alleen beschikbaar in PowerShell 5.1 of hoger.

Zie voor meer informatie over PSDrives [beheren-PowerShell-stations](/powershell/scripting/samples/managing-windows-powershell-drives).

### <a name="role-definitions"></a>Roldefinities

Roldefinities in een sessie-configuratiebestand definieert de toewijzing van **gebruikers** naar **rollen**. Elke gebruiker of groep die zijn opgenomen in dit veld is gemachtigd voor de JEA-eindpunt wanneer deze geregistreerd.
Elke gebruiker of groep kan worden opgenomen als een sleutel in de hash-tabel slechts één keer, maar meerdere rollen kan worden toegewezen. De naam van de mogelijkheid van de rol moet de naam van het bestand van de mogelijkheid rol zonder de `.psrc` extensie.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Als een gebruiker tot meer dan één groep in het roldefinitie van de behoort, krijgen toegang tot de functies van elk. Wanneer twee rollen toegang tot de dezelfde cmdlets verleent, worden de meest strikte parameterset wordt verleend aan de gebruiker.

Bij het opgeven van lokale gebruikers en groepen in het veld van de definities rol, zorg ervoor dat u de naam van de computer niet **localhost** of jokertekens. U kunt de naam van de computer controleren door het inspecteren van de `$env:COMPUTERNAME` variabele.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Zoekvolgorde van rol mogelijkheid

Zoals u in het bovenstaande voorbeeld, rolmogelijkheden zijn waarnaar wordt verwezen door de naam van het bestand van de mogelijkheid rol. De naam van een bestand is de bestandsnaam zonder extensie. Als meerdere rolmogelijkheden beschikbaar op het systeem met dezelfde naam zijn, wordt de impliciete zoekvolgorde in PowerShell gebruikt om de effectieve rol mogelijkheid-bestand te selecteren. JEA heeft **niet** toegang geven tot alle rol mogelijkheid bestanden met dezelfde naam.

JEA maakt gebruik van de `$env:PSModulePath` omgevingsvariabele om te bepalen welke paden om te scannen op rol mogelijkheid bestanden. Binnen elk van deze paden JEA gezocht naar geldige PowerShell-modules die een submap 'RoleCapabilities' bevatten. Net als bij importeren van modules, verkiest JEA rolmogelijkheden die worden geleverd met Windows op de mogelijkheden van de aangepaste rol met dezelfde naam.

Voor alle andere naamconflicten wordt prioriteit bepaald door de volgorde waarin Windows de bestanden in de map inventariseren. De order wordt niet gegarandeerd alfabetische. Het eerste bestand van de rol-mogelijkheid gevonden die overeenkomt met de opgegeven naam wordt gebruikt voor de gebruiker die verbinding maakt. Omdat de rol mogelijkheid order niet deterministisch is, is het **sterk aanbevolen** dat rolmogelijkheden unieke namen van bestanden hebben.

### <a name="conditional-access-rules"></a>Regels voor voorwaardelijke toegang

Alle gebruikers en groepen die zijn opgenomen in de **RoleDefinitions** veld automatisch toegang verleend tot JEA-eindpunten. Regels voor voorwaardelijke toegang kunnen u deze toegang verfijnen en vereisen dat gebruikers deel uitmaken van aanvullende beveiligingsgroepen die niet van invloed zijn op de rollen waaraan ze zijn toegewezen. Dit is handig als u wilt een just-in-time privileged access management-oplossing, smartcardverificatie of andere oplossing voor multifactor-verificatie integreren met JEA.

Regels voor voorwaardelijke toegang worden gedefinieerd in het veld RequiredGroups in een sessie-configuratiebestand.
Daar kunt u een hash-tabel (eventueel geneste) die gebruikmaakt van bieden 'En' en 'Of' sleutels te maken van uw regels. Hier volgen enkele voorbeelden van hoe u dit veld:

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
> Regels voor voorwaardelijke toegang zijn alleen beschikbaar in PowerShell 5.1 of hoger.

### <a name="other-properties"></a>Andere eigenschappen

Sessie-configuratiebestanden kunnen ook doen alles wat die een bestand van de mogelijkheid rol doen kunt, maar wel zonder de mogelijkheid om te verbinden gebruikerstoegang geven tot andere opdrachten. Als u wilt dat alle gebruikers toegang tot bepaalde cmdlets, functies of -providers, kunt u doen rechts in het configuratiebestand van de sessie.
Voor een volledige lijst van ondersteunde eigenschappen in het configuratiebestand van de sessie, voert u `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Testen van een sessie-configuratiebestand

U kunt testen met een sessie configureren met behulp van de [Test PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet. Het verdient aanbeveling uw sessie-configuratiebestand te testen, als u handmatig hebt bewerkt de `.pssc` bestand. Testen, zorgt ervoor dat de syntaxis juist is. Als een sessie-configuratiebestand deze test mislukt, kan deze kan niet worden geregistreerd op het systeem.

## <a name="sample-session-configuration-file"></a>Voorbeeldconfiguratiebestand sessie

Het volgende voorbeeld ziet hoe u maakt en een sessieconfiguratie voor JEA valideren. De definities van gebruikersrollen worden gemaakt en opgeslagen in de `$roles` variabele voor uw gemak en leesbaarheid. Het is niet vereist om dit te doen.

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

Als u wilt wijzigen van de eigenschappen van een JEA-sessieconfiguratie, met inbegrip van de toewijzing van gebruikers aan rollen, moet u [registratie](register-jea.md#unregistering-jea-configurations). Vervolgens [opnieuw registreren](register-jea.md) de JEA-sessieconfiguratie met behulp van een configuratiebestand bijgewerkte sessie.

## <a name="next-steps"></a>Volgende stappen

- [Een JEA-configuratiegegevens registreren](register-jea.md)
- [De auteur van JEA-rollen](role-capabilities.md)
