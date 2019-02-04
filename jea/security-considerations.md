---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: Overwegingen bij de beveiliging van JEA
ms.openlocfilehash: ede727f0f30412d520712d6ba855ba2008375d9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687242"
---
# <a name="jea-security-considerations"></a>Overwegingen bij de beveiliging van JEA

> Van toepassing op: Windows PowerShell 5.0

JEA helpt u bij uw beveiligingspostuur verbeteren door het aantal permanente beheerders op uw virtuele machines te verminderen.
Dit gebeurt door het maken van een nieuw toegangspunt voor gebruikers voor het beheren van het systeem (een PowerShell-sessie-configuratie) die nauw standaard om te voorkomen dat misbruik wordt vergrendeld.
Gebruikers die sommige, maar niet nodig hebben onbeperkte toegang tot de machine administratieve taken uit te voeren toegang tot de JEA-eindpunt kan worden verleend.
JEA kunnen ze admin-opdrachten uitvoeren zonder rechtstreeks met beheerderstoegang, kunt u vervolgens deze gebruikers verwijderen uit maximaal beschermde-beveiligingsgroepen (zodat ze standaardgebruikers).

Dit onderwerp beschrijft de JEA-beveiligingsmodel en aanbevolen procedures in meer detail.

## <a name="run-as-account"></a>Uitvoeren als-account

Elke JEA-eindpunt heeft een aangewezen 'uitvoeren als'-account, dit is het account waarmee de gebruiker verbinding maakt acties worden uitgevoerd.
Dit account kan worden geconfigureerd in de [sessie configuratiebestand](session-configurations.md), en het account dat u kiest een grote invloed heeft op de beveiliging van uw eindpunt.

**Virtuele accounts** zijn de aanbevolen manier om de uitvoeren als-account configureren.
Virtuele-accounts zijn eenmalige, tijdelijke lokale accounts die zijn gemaakt voor de gebruiker die de verbinding moet worden gebruikt tijdens de duur van hun JEA-sessie.
Zodra de sessie wordt beëindigd, wordt de virtuele-account wordt vernietigd en kan niet meer worden gebruikt.
Gebruiker die de verbinding niet weet de referenties voor de virtuele-account en de virtuele-account niet gebruiken voor toegang tot het systeem via andere middelen, zoals Extern bureaublad of een onbeperkte PowerShell-eindpunt.

Standaard worden virtuele accounts behoren tot de lokale beheerdersgroep op de machine.
Dit biedt ze volledige rechten voor het beheren van alles op het systeem, maar geen rechten voor het beheren van bronnen op het netwerk.
Bij het verifiëren met andere virtuele machines, worden de context van de gebruiker van het account lokale computer, niet op het virtuele account.

Domeincontrollers vormen een speciaal geval, omdat er geen concept van een lokale groep administrators.
In plaats daarvan virtuele accounts behoren tot de groep Domeinadministrators in plaats daarvan en de directoryservices op de domeincontroller kunnen beheren.
De domein-identiteit is nog steeds beperkt tot het gebruik van de domeincontroller waar de JEA-sessie is gemaakt, en toegang tot het netwerk wordt weergegeven in plaats daarvan afkomstig zijn van de domain controller computer-object.

In beide gevallen kunt u ook expliciet welke beveiligingsgroepen de virtueel account tot behoren moet definiëren.
Dit is een goede gewoonte wanneer de taak die u uitvoert zonder beheerdersbevoegdheden lokale/domein kan worden gedaan.
Als u al een beveiligingsgroep die is gedefinieerd voor uw beheerders hebt, kunt u gewoon het lidmaatschap van de virtueel account verlenen aan die groep wijs hieraan de machtigingen die nodig zijn.
Virtueel accountlidmaatschap is beperkt tot lokale beveiligingsgroepen op werkstations en lidservers, maar op een domeincontroller ze kunnen alleen leden van de domein-beveiligingsgroepen.
Wanneer u een of meer beveiligingsgroepen voor de virtuele-account om u te behoren tot opgeeft, wordt deze niet meer behoren tot de standaard-groepen (lokale beheerder of domeinbeheerder).

De onderstaande tabel bevat een overzicht van de mogelijke configuratie-opties en de resulterende machtigingen voor virtuele accounts

Het computertype                | Configuratie van virtueel account | Lokale gebruikerscontext                                      | Netwerk-gebruikerscontext
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Domeincontroller            | Standaard                             | Domeingebruiker, lid van '*domein*\Domain beheerders         | Computeraccount
Domeincontroller            | Domeingroepen A en B               | Domeingebruiker, lid van '*domein*\A ','*domein*\B'       | Computeraccount
Lidserver of werkstation | Standaard                             | Lokale gebruiker, lid van '*BUILTIN*\Administrators'        | Computeraccount
Lidserver of werkstation | Lokale groepen C en D                | Lokale gebruiker, lid van '*COMPUTER*\C' en '*COMPUTER*\D' | Computeraccount

Wanneer u gebeurtenissen voor beveiligingscontrole en gebeurtenislogboeken van toepassing bekijkt, ziet u dat elke gebruikerssessie JEA een unieke virtueel account is.
Zo kunt u het bijhouden van acties in een JEA-eindpunt van de gebruiker terug naar de oorspronkelijke gebruiker die de opdracht uitvoert.
Virtueel account namen worden als volgt de indeling ' WinRM virtuele gebruikers\\WinRM\_VA\_*ACCOUNTNUMBER*\_*domein* \_ *sAMAccountName*' als gebruiker 'Els' in domein "Contoso" opnieuw wordt opgestart een service in een JEA-eindpunt, de gebruikersnaam die is gekoppeld aan de service control manager gebeurtenissen zou bijvoorbeeld ' WinRM virtuele gebruikers\\WinRM\_ Evaluatie van beveiligingsproblemen\_1\_contoso\_Els '.


**Groep beheerde serviceaccounts (gmsa's)** zijn nuttig wanneer een lidserver moet toegang hebben tot netwerkbronnen in de JEA-sessie.
Een voorbeeld van de use-case voor dit is een JEA-eindpunt dat wordt gebruikt voor het beheren van toegang tot een REST-API die wordt gehost op een andere computer.
Het is gemakkelijk om te schrijven functies om de gewenste aanroepen in de REST-API, maar om te kunnen verifiëren met de API die u moeten een netwerk-id.
Met behulp van een groep beheerd serviceaccount, maakt het 'tweede hop' mogelijk terwijl nog steeds controle over welke computers de account kunnen gebruiken.
De effectieve machtigingen van de gMSA worden gedefinieerd door de beveiligingsgroepen (lokaal of domein) waarbij het gMSA-account hoort.

Wanneer een JEA-eindpunt is geconfigureerd om een gMSA-account te gebruiken, verschijnt de acties van gebruikers met alle JEA afkomstig zijn van dezelfde groep beheerd serviceaccount.
De enige manier kunt u acties terug naar een specifieke gebruiker traceren is het identificeren van de reeks opdrachten uitvoeren in de tekst van een PowerShell-sessie.

**-Passthrough referenties** worden gebruikt wanneer u niet opgeven van een uitvoeren als-account en wilt dat PowerShell-opdrachten uitvoeren op de externe server met referenties van de gebruiker van het maken van verbinding.
Deze configuratie is *niet* voor JEA aanbevolen als u de verbindende gebruikers direct toegang geven tot privileged beheergroepen zou moeten.
Als gebruiker die de verbinding is al beheerdersbevoegdheden, kunnen ze helemaal te voorkomen dat JEA en beheren van het systeem via andere, onbeperkte betekent.
Zie het gedeelte hieronder voor het [JEA biedt geen bescherming tegen beheerders](#jea-does-not-protect-against-admins) voor meer informatie.

**Standaard uitvoeren als-accounts** kunt u opgeven van een gebruikersaccount op waaronder de volledige PowerShell-sessie wordt uitgevoerd.
Dit is een belangrijke onderscheidende factor zijn, omdat een sessieconfiguratie ingesteld voor het gebruik van een vaste uitvoeren als-account (met de `-RunAsCredential` parameter) is niet JEA-bewust.
Dit betekent dat dat roldefinities niet langer werken zoals verwacht, en elke gebruiker die is gemachtigd voor toegang tot het eindpunt wordt dezelfde rol worden toegewezen.

U moet een RunAsCredential niet gebruiken op een JEA-eindpunt vanwege de problemen bij het traceren van acties terug naar specifieke gebruikers en het ontbreken van ondersteuning voor het toewijzen van gebruikers aan rollen.

## <a name="winrm-endpoint-acl"></a>WinRM ACL voor eindpunten

Omdat elke JEA-eindpunt met de reguliere PowerShell remoting eindpunten, een afzonderlijke toegangsbeheerlijst (ACL) instellen in de WinRM-configuratie die bepaalt kunnen die worden geverifieerd met de JEA-eindpunt.
Als u niet goed geconfigureerd, vertrouwde gebruikers wellicht geen toegang hebben tot de JEA-eindpunt en/of niet-vertrouwde gebruikers toegang kunnen krijgen.
De WinRM-ACL beïnvloedt echter niet zo is, de toewijzing van gebruikers aan rollen JEA.
Die wordt beheerd door de *RoleDefinitions* veld in het configuratiebestand van de sessie die is geregistreerd op het systeem.

Standaard, wanneer u een JEA-eindpunt met behulp van een sessie-configuratiebestand als een of meer rolmogelijkheden, registreert wordt de WinRM-ACL worden geconfigureerd dat alle gebruikers toe te wijzen aan een of meer rollen toegang tot het eindpunt.
Bijvoorbeeld, een JEA-sessie die is geconfigureerd met behulp van de volgende opdrachten wordt volledige toegang verlenen tot *CONTOSO\JEA\_Lev1* en *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

U kunt controleren de machtigingen van de gebruiker met de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Als u wilt wijzigen welke gebruikers toegang hebben, voer een `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` voor een interactieve prompt of `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` om bij te werken van de machtigingen.
Gebruikers moeten ten minste *Invoke* rechten voor toegang tot de JEA-eindpunt.

Als extra gebruikers toegang tot de JEA-eindpunt krijgen, maar niet in een van de rollen die zijn gedefinieerd in het configuratiebestand van de sessie vallen, worden ze wel een JEA-sessie starten, maar hebben alleen toegang tot de standaard-cmdlets.
U kunt de machtigingen van de gebruiker in een JEA-eindpunt controleren door te voeren `Get-PSSessionCapability`.
Bekijk de [controle en rapportage over JEA](audit-and-report.md) artikel voor meer informatie over het controleren van opdrachten van een gebruiker die toegang heeft tot in een JEA-eindpunt.

## <a name="least-privilege-roles"></a>Minimale bevoegdheid rollen

Bij het ontwerpen van JEA-functies, is het belangrijk om te weten dat de virtuele of een groep beheerde service-account die wordt uitgevoerd op de achtergrond vaak onbeperkte toegang tot het beheer van de lokale computer is.
Rolmogelijkheden JEA te beperken wat dat account kan worden gebruikt door het beperken van de opdrachten en toepassingen die kunnen worden uitgevoerd met behulp van die beschermde context.
Niet goed ontworpen rollen kunt gevaarlijke opdrachten die een gebruiker kan verbreken buiten de grenzen van de JEA of toegang krijgen tot gevoelige informatie.

Bijvoorbeeld, houd rekening met de volgende vermelding van de rol-mogelijkheid:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

De mogelijkheid van deze rol kan gebruikers een PowerShell-cmdlet uitvoeren met het zelfstandig naamwoord 'Proces' van de module Microsoft.PowerShell.Management.
Gebruikers mogelijk toegang tot cmdlets, zoals `Get-Process` om te begrijpen welke toepassingen worden uitgevoerd op het systeem en `Stop-Process` afsluiten een vastgelopen toepassingen.
Deze post ook kan echter `Start-Process`, die kan worden gebruikt om een willekeurige programma met volledige beheerdersrechten worden opgestart.
Het programma niet moet lokaal op het systeem worden geïnstalleerd, zodat een kwaadwillende persoon kan een programma te starten op een bestandsshare waarmee de verbindende gebruiker lokale beheerdersbevoegdheden en schadelijke software wordt uitgevoerd.'

Een beter beveiligde versie van deze dezelfde rol mogelijkheid zou er als volgt uitzien:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Vermijd het gebruik van jokertekens in rolmogelijkheden en zorg ervoor dat u [controleren de machtigingen van de effectieve gebruikersnaam](audit-and-report.md#check-effective-rights-for-a-specific-user) regelmatig om te begrijpen welke opdrachten van een gebruiker toegang heeft tot.

## <a name="jea-does-not-protect-against-admins"></a>JEA biedt geen bescherming tegen beheerders

Een van de belangrijkste principes van JEA is dat het niet-beheerders om uit te voeren kunt *sommige* beheertaken.
JEA biedt geen bescherming tegen mensen die al administrator-bevoegdheden hebt.
Gebruikers die deel uitmaken van 'Domeinadministrators', 'lokale admins', of andere maximaal beschermde groepen in uw omgeving worden nog steeds de JEA-beveiligingen als u zich aanmeldt bij de computer via een andere manier wordt omzeild.
Ze kunnen, bijvoorbeeld: Meld u aan met RDP, externe MMC-consoles gebruiken of verbinding maken met onbeperkte PowerShell-eindpunten.
Lokale beheerders op het systeem kunt JEA configuraties zodat andere gebruikers te beheren van het systeem of te wijzigen van de mogelijkheid van een rol om uit te breiden het bereik van wat een gebruiker in hun sessie JEA doen kan ook wijzigen.
Daarom is het belangrijk om te bepalen van uw gebruikers JEA uitgebreide machtigingen om te zien of er andere manieren kan ook bevoegde toegang tot het systeem.

Een normaal worden bij gebruik van JEA voor reguliere dagelijks onderhoud en hebben een 'just in time' in beschermde modus beheeroplossing toegang toestaan dat gebruikers tijdelijk worden lokale beheerders in noodsituaties.
Dit zorgt ervoor gebruikers zijn geen permanente beheerders op het systeem, maar deze rechten kunnen krijgen als en alleen wanneer ze een werkstroom die documenten van hun gebruik van deze machtigingen hebt voltooid.