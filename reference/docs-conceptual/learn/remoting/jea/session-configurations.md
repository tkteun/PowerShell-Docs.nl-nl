---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: JEA-sessie configuraties
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017879"
---
# <a name="jea-session-configurations"></a>JEA-sessie configuraties

Een JEA-eind punt wordt geregistreerd op een systeem door een Power shell-sessie configuratie bestand te maken en te registreren. Met sessie configuraties definieert u wie het JEA-eind punt kan gebruiken en met welke rollen ze toegang hebben. Ze definiëren ook algemene instellingen die van toepassing zijn op alle gebruikers van de JEA-sessie.

## <a name="create-a-session-configuration-file"></a>Een configuratie bestand voor de sessie maken

Als u een JEA-eind punt wilt registreren, moet u opgeven hoe dat eind punt is geconfigureerd. Er zijn veel opties om rekening mee te houden. De belangrijkste opties zijn:

- Wie heeft toegang tot het JEA-eind punt
- Aan welke rollen ze worden toegewezen
- Welke identiteits JEA worden gebruikt onder de kaften
- De naam van het JEA-eind punt

Deze opties worden gedefinieerd in een Power shell-gegevens bestand `.pssc` met een extensie die een Power shell-sessie configuratie bestand wordt genoemd. Het configuratie bestand van de sessie kan worden bewerkt met behulp van een tekst editor.

Voer de volgende opdracht uit om een leeg sjabloon configuratie bestand te maken.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Alleen de meest voorkomende configuratie opties zijn standaard opgenomen in het sjabloon bestand. Gebruik de `-Full` Schakel optie voor het toevoegen van alle toepasselijke instellingen in het gegenereerde PSSC.

In `-SessionType RestrictedRemoteServer` het veld wordt aangegeven dat de sessie configuratie wordt gebruikt door JEA voor beveiligd beheer. Sessies van dit type worden in de modus exclusief **taal** uitgevoerd en hebben alleen toegang tot de volgende standaard opdrachten (en aliassen):

- Clear-host (CLS, Clear)
- Afsluiten-PSSession (exsn, afsluiten)
- Get-opdracht (GCM)
- Get-FormatData
- Get-Help
- Measure-object (measure)
- Out-standaard
- Select-object (selecteren)

Er zijn geen Power shell-providers beschikbaar en ook geen externe Program ma's (uitvoer bare bestanden of scripts).

Zie [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes)voor meer informatie over taal modi.

### <a name="choose-the-jea-identity"></a>De JEA-identiteit kiezen

Achter de schermen heeft JEA een identiteit (account) nodig om te gebruiken bij het uitvoeren van de opdrachten van een verbonden gebruiker.
U definieert welke identiteit JEA in het sessie configuratie bestand gebruikt.

#### <a name="local-virtual-account"></a>Lokaal virtueel account

Lokale virtuele accounts zijn handig wanneer alle rollen die zijn gedefinieerd voor het JEA-eind punt worden gebruikt voor het beheren van de lokale computer en een lokaal Administrator-account voldoende is om de opdrachten te kunnen uitvoeren.
Virtuele accounts zijn tijdelijke accounts die uniek zijn voor een specifieke gebruiker en alleen voor de duur van de Power shell-sessie. Op een lidserver of werk station behoren virtuele accounts tot de groep Administrators van de lokale computer. Op een Active Directory-domein controller behoren virtuele accounts tot de groep **domein Administrators** van het domein.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Als voor de rollen die zijn gedefinieerd door de sessie configuratie geen volledige beheerders bevoegdheden zijn vereist, kunt u de beveiligings groepen opgeven waarvan het virtuele account deel uitmaakt. Op een lidserver of werk station moeten de opgegeven beveiligings groepen lokale groepen zijn, en niet groepen van een domein.

Wanneer een of meer beveiligings groepen worden opgegeven, wordt het virtuele account niet toegewezen aan de groep lokale of domein beheerders.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> Virtuele accounts hebben tijdelijk het recht aanmelden als een service in het beveiligings beleid van de lokale server. Als aan een van de opgegeven VirtualAccountGroups dit recht al is toegekend in het beleid, wordt het afzonderlijke virtuele account niet meer toegevoegd en verwijderd uit het beleid. Dit kan handig zijn in scenario's zoals domein controllers waar revisies van het beveiligings beleid van de domein controller nauw keurig worden gecontroleerd. Dit is alleen beschikbaar in Windows Server 2016 met de rollup van 2018 of hoger van november en Windows Server 2019 met de rollup van 2019 januari of hoger.

#### <a name="group-managed-service-account"></a>Door groep beheerd service account

Een door een groep beheerd service account (GMSA) is de geschikte identiteit die moet worden gebruikt wanneer JEA-gebruikers toegang nodig hebben tot netwerk bronnen zoals bestands shares en webservices. Gmsa's geven u een domein identiteit die wordt gebruikt voor verificatie met resources op elke computer in het domein. De rechten die een GMSA biedt, worden bepaald door de resources die u wilt openen. U hebt geen beheerders rechten op computers of services, tenzij de machine of service beheerder deze rechten expliciet heeft verleend aan de GMSA.

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

Gmsa's mag alleen worden gebruikt wanneer dit nodig is:

- Het is lastig om de acties terug te traceren naar een gebruiker wanneer een GMSA wordt gebruikt. Elke gebruiker deelt dezelfde run-as-identiteit. U moet de transcripten en logboeken van Power shell-sessies controleren om afzonderlijke gebruikers met hun acties te correleren.

- De GMSA heeft mogelijk toegang tot veel netwerk bronnen waartoe de verbinding van de gebruiker geen toegang nodig heeft. Probeer altijd de juiste machtigingen in een JEA-sessie te beperken om het principe van minimale bevoegdheden te volgen.

> [!NOTE]
> Door groepen beheerde service accounts zijn alleen beschikbaar op computers die lid zijn van een domein met behulp van Power shell 5,1 of nieuwer.

Zie het artikel [beveiligings overwegingen](security-considerations.md) voor meer informatie over het beveiligen van een JEA-sessie.

### <a name="session-transcripts"></a>Transcripten van sessies

Het is raadzaam om een JEA-eind punt te configureren voor het automatisch vastleggen van transcripten van gebruikers sessies. De transcripten van Power shell-sessies bevatten informatie over de gebruiker die verbinding maakt, de run as-identiteit die aan hen is toegewezen en de opdrachten die worden uitgevoerd door de gebruiker. Ze kunnen nuttig zijn voor een audit team dat moet weten wie een specifieke wijziging in een systeem heeft aangebracht.

Als u automatische transcriptie in het configuratie bestand voor de sessie wilt configureren, geeft u een pad naar een map op waarin de transcripten moeten worden opgeslagen.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

Transcripten worden naar de map geschreven door het **lokale systeem** account, waarvoor lees-en schrijf toegang tot de map is vereist. Standaard gebruikers mogen geen toegang hebben tot de map. Beperk het aantal beveiligings beheerders dat toegang heeft om de transcripten te controleren.

### <a name="user-drive"></a>Gebruikers station

Als uw gebruikers die verbinding maken, bestanden moeten kopiëren naar of van het JEA-eind punt, kunt u het gebruikers station inschakelen in het configuratie bestand van de sessie. Het gebruikers station is een **PSDrive** die is toegewezen aan een unieke map voor elke gebruiker die verbinding maakt. Met deze map kunnen gebruikers bestanden kopiëren naar of van het systeem zonder dat ze toegang hebben tot het volledige bestands systeem of de bestandssysteem provider weer geven. De inhoud van het gebruikers station is permanente sessies voor situaties waarin de netwerk verbinding mogelijk wordt verbroken.

```powershell
MountUserDrive = $true
```

Standaard kunt u met het gebruikers station Maxi maal 50 MB gegevens per gebruiker opslaan. U kunt de hoeveelheid gegevens beperken die een gebruiker kan verbruiken met het veld *UserDriveMaximumSize* .

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Als u niet wilt dat gegevens in het gebruikers station permanent zijn, kunt u een geplande taak op het systeem configureren om elke avond automatisch de map op te schonen.

> [!NOTE]
> Het gebruikers station is alleen beschikbaar in Power shell 5,1 of nieuwer.

Zie [Power Shell-stations beheren](/powershell/scripting/samples/managing-windows-powershell-drives)voor meer informatie over PSDrives.

### <a name="role-definitions"></a>Roldefinities

Roldefinities in een sessie configuratie bestand definiëren de toewijzing van **gebruikers** aan **rollen**. Elke gebruiker of groep die in dit veld is opgenomen, krijgt toegang tot het JEA-eind punt wanneer het is geregistreerd.
Elke gebruiker of groep kan slechts eenmaal als sleutel in de hashtabel worden opgenomen, maar kan meerdere rollen krijgen. De naam van de functie mogelijkheid moet de naam zijn van het functie-Capability-bestand `.psrc` , zonder de extensie.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Als een gebruiker deel uitmaakt van meer dan één groep in de roldefinitie, krijgen ze toegang tot de rollen van elk. Wanneer twee rollen toegang verlenen tot dezelfde cmdlets, wordt de meest strikte parameterset verleend aan de gebruiker.

Wanneer u lokale gebruikers of groepen in het veld roldefinities opgeeft, moet u ervoor zorgen dat u de computer naam, niet **localhost** of joker tekens, gebruikt. U kunt de naam van de computer controleren door de `$env:COMPUTERNAME` variabele te controleren.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Zoek volgorde van functie mogelijkheden

Zoals u in het bovenstaande voor beeld kunt zien, wordt naar de functie functionaliteit verwezen met de basis naam van het functie-Capability-bestand. De basis naam van een bestand is de bestands naam zonder extensie. Als er meerdere functie mogelijkheden beschikbaar zijn op het systeem met dezelfde naam, gebruikt Power shell de impliciete Zoek volgorde van de functie om het juiste bestandsbeheer bestand te selecteren. JEA geeft **geen** toegang tot alle functie-Capability-bestanden met dezelfde naam.

JEA maakt gebruik `$env:PSModulePath` van de omgevings variabele om te bepalen welke paden moeten worden gescand op functie-Capability-bestanden. In elk van deze paden zoekt JEA naar geldige Power shell-modules die een submap ' RoleCapabilities ' bevatten. Net als bij het importeren van modules, geven JEA de voor keur aan functie mogelijkheden die worden geleverd met Windows naar aangepaste functie mogelijkheden met dezelfde naam.

Voor alle andere naam conflicten wordt de prioriteit bepaald aan de hand van de volg orde waarin Windows de bestanden in de map inventariseert. De bestelling is niet gegarandeerd in alfabetische volg orde. Het eerste functie-mogelijkheidsprofiel gevonden dat overeenkomt met de opgegeven naam wordt gebruikt voor de gebruiker die verbinding maakt. Omdat de zoek volgorde van de functie mogelijkheden niet deterministisch is, wordt het **ten zeerste aanbevolen** om functie mogelijkheden unieke bestands namen te bieden.

### <a name="conditional-access-rules"></a>Regels voor voorwaardelijke toegang

Alle gebruikers en groepen die zijn opgenomen in het veld **RoleDefinitions** , krijgen automatisch toegang tot JEA-eind punten. Met regels voor voorwaardelijke toegang kunt u deze toegang verfijnen en moeten gebruikers deel nemen aan extra beveiligings groepen die niet van invloed zijn op de rollen waaraan ze zijn toegewezen. Dit is handig als u een just-in-time privileged Access Management-oplossing, smartcard verificatie of andere multi-factor Authentication-oplossing wilt integreren met JEA.

Regels voor voorwaardelijke toegang worden gedefinieerd in het veld RequiredGroups in een configuratie bestand voor de sessie.
Daar kunt u een hashtabel (optioneel genest) opgeven die gebruikmaakt van ' and ' en ' or '-sleutels om uw regels te maken. Hier volgen enkele voor beelden van het gebruik van dit veld:

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
> Regels voor voorwaardelijke toegang zijn alleen beschikbaar in Power shell 5,1 of nieuwer.

### <a name="other-properties"></a>Andere eigenschappen

Sessie configuratie bestanden kunnen ook alles doen wat een functie-mogelijkheidsprofiel kan doen, alleen zonder de mogelijkheid om verbinding te maken tussen gebruikers en andere opdrachten. Als u alle gebruikers toegang wilt geven tot specifieke cmdlets, functies of providers, kunt u dit rechtstreeks doen in het configuratie bestand voor de sessie.
Voer uit `Get-Help New-PSSessionConfigurationFile -Full`voor een volledige lijst met ondersteunde eigenschappen in het configuratie bestand voor de sessie.

## <a name="testing-a-session-configuration-file"></a>Een configuratie bestand voor een sessie testen

U kunt een sessie configuratie testen met de cmdlet [test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) . Het is raadzaam om uw sessie configuratie bestand te testen als u het `.pssc` bestand hand matig hebt bewerkt. Testen zorgt ervoor dat de syntaxis juist is. Als een sessie configuratie bestand deze test niet kan registreren, kan het niet worden geregistreerd op het systeem.

## <a name="sample-session-configuration-file"></a>Configuratie bestand voor voorbeeld sessie

In het volgende voor beeld ziet u hoe u een sessie configuratie voor JEA maakt en valideert. De roldefinities worden gemaakt en opgeslagen in de `$roles` variabele voor gemak en lees baarheid. Dit is geen vereiste.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Sessie configuratie bestanden bijwerken

Als u de eigenschappen van een JEA-sessie configuratie wilt wijzigen, met inbegrip van de toewijzing van gebruikers aan rollen, moet u de [registratie ongedaan maken](register-jea.md#unregistering-jea-configurations). Registreer de JEA-sessie configuratie vervolgens [opnieuw](register-jea.md) met een bijgewerkt sessie configuratie bestand.

## <a name="next-steps"></a>Volgende stappen

- [Een JEA-configuratie registreren](register-jea.md)
- [JEA-rollen ontwerpen](role-capabilities.md)
