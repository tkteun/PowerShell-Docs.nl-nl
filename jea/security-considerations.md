---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: Overwegingen bij de beveiliging van JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726580"
---
# <a name="jea-security-considerations"></a>Overwegingen bij de beveiliging van JEA

JEA helpt u bij uw beveiligingspostuur verbeteren door het aantal permanente beheerders op uw virtuele machines te verminderen. JEA maakt gebruik van de configuratie van een PowerShell-sessie te maken van een nieuw toegangspunt voor gebruikers voor het beheren van het systeem. Gebruikers met verhoogde bevoegdheden, maar niet onbeperkte toegang nodig tot de machine administratieve taken uitvoeren, kunnen de toegang tot de JEA-eindpunt worden verleend. Aangezien JEA kan deze gebruikers admin-opdrachten uitvoeren zonder de volledige functionaliteit voor beheerderstoegang hebben, kunt u vervolgens die gebruikers verwijderen uit maximaal beschermde-beveiligingsgroepen.

## <a name="run-as-account"></a>Run As-account

Elke JEA-eindpunt heeft een aangewezen **run as** account. Dit is het account waarmee de gebruiker verbinding maakt acties worden uitgevoerd. Dit account kan worden geconfigureerd in de [sessie configuratiebestand](session-configurations.md), en het account dat u kiest een grote invloed heeft op de beveiliging van uw eindpunt.

**Virtuele accounts** zijn de aanbevolen manier van het configureren van de **run as** account. Virtuele-accounts zijn eenmalige, tijdelijke lokale accounts die zijn gemaakt voor de gebruiker die de verbinding moet worden gebruikt tijdens de duur van hun JEA-sessie. Zodra de sessie wordt beëindigd, wordt de virtuele-account wordt vernietigd en kan niet meer worden gebruikt. De gebruiker die verbinding maakt weten niet de referenties voor de virtuele-account. De virtuele-account kan niet worden gebruikt voor toegang tot het systeem via andere middelen, zoals Extern bureaublad of een onbeperkte PowerShell-eindpunt.

Standaard virtuele accounts deel uitmaken van de lokale **beheerders** groep op de machine. Dit biedt ze volledige rechten voor het beheren van alles op het systeem, maar geen rechten voor het beheren van bronnen op het netwerk.
Bij het verifiëren met andere virtuele machines, is de context van de gebruiker die van het account lokale computer, niet op het virtuele account.

Domeincontrollers vormen een speciaal geval, omdat er geen lokale **beheerders** groep. In plaats daarvan virtuele accounts behoren tot **Domeinadministrators** en de directoryservices op de domeincontroller kan beheren. De domein-id is nog steeds beperkt voor gebruik op de domeincontroller waar de JEA-sessie is gemaakt. Toegang tot het netwerk wordt weergegeven in plaats daarvan afkomstig zijn van de domain controller computer-object.

In beide gevallen kan u uitdrukkelijk welke beveiligingsgroepen de virtueel account tot behoort definiëren. Dit is een goede gewoonte wanneer de taak kan worden uitgevoerd zonder een lokale of domeintoegang beheerdersbevoegdheden. Als u al een beveiligingsgroep die is gedefinieerd voor uw beheerders hebt, verleent u het accountlidmaatschap van de virtuele-aan die groep. Virtueel accountlidmaatschap is beperkt tot lokale beveiligingsgroepen op werkstations en lidservers. Op domeincontrollers moeten virtuele accounts lid van domein-beveiligingsgroepen.
Zodra de virtuele-account is toegevoegd aan een of meer beveiligingsgroepen, worden deze niet meer behoort tot de standaard-groepen (lokaal of domeinbeheerder beheerders).

De volgende tabel geeft een overzicht van de mogelijke configuratie-opties en de resulterende machtigingen voor virtuele accounts:

|        Het computertype         | Configuratie van virtueel account |                   Lokale gebruikerscontext                    | Netwerk-gebruikerscontext |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Domeincontroller            | Standaard                             | Domeingebruiker, lid van '*domein*\Domain beheerders         | Computeraccount     |
| Domeincontroller            | Domeingroepen A en B               | Domeingebruiker, lid van '*domein*\A ','*domein*\B'       | Computeraccount     |
| Lidserver of werkstation | Standaard                             | Lokale gebruiker, lid van '*BUILTIN*\Administrators'        | Computeraccount     |
| Lidserver of werkstation | Lokale groepen C en D                | Lokale gebruiker, lid van '*COMPUTER*\C' en '*COMPUTER*\D' | Computeraccount     |

Wanneer u gebeurtenissen voor beveiligingscontrole en gebeurtenislogboeken van toepassing bekijkt, ziet u dat elke gebruikerssessie JEA een unieke virtueel account is. Deze unieke account helpt u bij het bijhouden van acties in een JEA-eindpunt van de gebruiker terug naar de oorspronkelijke gebruiker die de opdracht uitvoert. Virtueel account namen worden als volgt de indeling `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` bijvoorbeeld, als gebruiker **Els** in domein **Contoso** een service wordt opnieuw opgestart in een JEA-eindpunt, de gebruikersnaam die is gekoppeld aan een servicebesturingsbeheer gebeurtenissen zijn `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

**Groep beheerde serviceaccounts (gmsa's)** zijn nuttig wanneer een lidserver moet toegang hebben tot netwerkbronnen in de JEA-sessie. Bijvoorbeeld, wanneer een JEA-eindpunt wordt gebruikt voor het beheren van toegang tot een REST-API-service die wordt gehost op een andere computer. Het is eenvoudig om functies voor het aanroepen van de REST API's te schrijven, maar u moet een netwerk-id om te verifiëren met de API. Met behulp van een groep beheerde serviceaccount, maakt de tweede hop mogelijk behoud van controle over welke computers de account kunnen gebruiken. De effectieve machtigingen van de gMSA worden gedefinieerd door de beveiligingsgroepen (lokaal of domein) waarbij het gMSA-account hoort.

Wanneer een JEA-eindpunt is geconfigureerd voor gebruik van een gMSA, worden de acties van alle gebruikers van JEA afkomstig zijn van de dezelfde gMSA weergegeven. De enige manier om tracering acties terug naar een specifieke gebruiker is het identificeren van de reeks opdrachten uitvoeren in de tekst van een PowerShell-sessie.

**-Passthrough referenties** worden gebruikt wanneer u geen opgeeft een **run as** account. PowerShell maakt gebruik van referenties van de gebruiker van het maken van verbinding opdrachten uitvoeren op de externe server. Hiervoor moet u de verbindende gebruikers direct toegang geven tot privileged-beheergroepen. Deze configuratie is **niet** aanbevolen voor JEA. Als gebruiker die de verbinding is al beheerdersbevoegdheden, kunnen ze JEA voorkomen en het systeem via andere, onbeperkte manier beheren. Zie de sectie hieronder voor meer informatie over hoe u [JEA niet beschermd tegen beheerders](#jea-doesnt-protect-against-admins).

**Standaard run as-accounts** kunt u opgeven van een gebruikersaccount waarmee de volledige PowerShell-sessie wordt uitgevoerd. Met behulp van sessieconfiguraties vaste **run as** accounts (met de `-RunAsCredential` parameter) worden niet op de JEA-hoogte. Roldefinities niet langer werken zoals verwacht. Elke gebruiker die is gemachtigd voor toegang tot het eindpunt is dezelfde rol toegewezen.

U mag niet een **RunAsCredential** op een JEA-eindpunt omdat het is moeilijk te traceren acties aan specifieke gebruikers en aanmeldingsbasis wordt de ondersteuning voor het toewijzen van gebruikers aan rollen.

## <a name="winrm-endpoint-acl"></a>WinRM ACL voor eindpunten

Omdat elke JEA-eindpunt met de reguliere PowerShell remoting eindpunten, een afzonderlijke toegangsbeheerlijst (ACL) die bepaalt kunnen die worden geverifieerd met de JEA-eindpunt. Als u niet goed geconfigureerd, vertrouwde gebruikers wellicht geen toegang hebben tot de JEA-eindpunt en niet-vertrouwde gebruikers mogelijk toegang heeft. De WinRM-ACL niet van invloed op de toewijzing van gebruikers aan rollen JEA. Toewijzing wordt bepaald door de **RoleDefinitions** veld in het configuratiebestand van de sessie die is gebruikt voor het registreren van het eindpunt.

Wanneer een JEA-eindpunt meerdere rolmogelijkheden heeft, wordt de ACL WinRM standaard geconfigureerd voor toegang tot alle toegewezen gebruikers. Bijvoorbeeld, een JEA-sessie die is geconfigureerd met behulp van de volgende opdrachten, hebben volledige toegang tot `CONTOSO\JEA_Lev1` en `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

U kunt controleren de machtigingen van de gebruiker met de [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Als u wilt wijzigen welke gebruikers toegang hebben, voer een `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` voor een interactieve prompt of `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` om bij te werken van de machtigingen. Gebruikers moeten ten minste *Invoke* rechten voor toegang tot de JEA-eindpunt.

Het is mogelijk te maken van een JEA-eindpunt dat een bepaalde rol niet is toegewezen aan elke gebruiker die toegang heeft. Deze gebruikers kunnen een JEA-sessie starten, maar hebben alleen toegang tot de standaard-cmdlets. U kunt de machtigingen van de gebruiker in een JEA-eindpunt controleren door te voeren `Get-PSSessionCapability`. Zie voor meer informatie, [controle en rapportage over JEA](audit-and-report.md).

## <a name="least-privilege-roles"></a>Minimale bevoegdheid rollen

Bij het ontwerpen van JEA-functies, is het belangrijk om te weten dat de virtuele en groep beheerde serviceaccounts die achter de schermen kunnen hebben onbeperkte toegang tot de lokale computer. Rolmogelijkheden JEA te beperken van de opdrachten en toepassingen die kunnen worden uitgevoerd in die beschermde context.
Niet goed ontworpen rollen kunt gevaarlijke opdrachten die kunnen toestaan dat een gebruiker buiten de grenzen van de JEA opsplitsen of toegang krijgen tot gevoelige informatie.

Bijvoorbeeld, houd rekening met de volgende vermelding van de rol-mogelijkheid:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

De mogelijkheid van deze rol kan gebruikers een PowerShell-cmdlet uitvoeren met het zelfstandig naamwoord **proces** uit de **Microsoft.PowerShell.Management** module. Gebruikers mogelijk toegang tot cmdlets, zoals `Get-Process` om te zien welke toepassingen worden uitgevoerd op het systeem en `Stop-Process` afsluiten van toepassingen die worden niet meer reageert. Deze post ook kan echter `Start-Process`, die kan worden gebruikt om een willekeurige programma met volledige beheerdersrechten worden opgestart. Het programma moet niet lokaal worden geïnstalleerd op het systeem. Een gebruiker verbinding kan een programma start vanuit een bestandsshare die u geeft de gebruiker lokale beheerdersbevoegdheden, malware en meer worden uitgevoerd.

Een beter beveiligde versie van deze dezelfde rol mogelijkheid zou er als volgt uitzien:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Vermijd het gebruik van jokertekens in rolmogelijkheden. Zorg ervoor dat regelmatig [controleren de machtigingen van de effectieve gebruikersnaam](audit-and-report.md#check-effective-rights-for-a-specific-user) om te begrijpen welke opdrachten zijn toegankelijk voor de gebruiker.

## <a name="jea-doesnt-protect-against-admins"></a>JEA biedt geen bescherming tegen beheerders

Een van de belangrijkste principes van JEA is dat niet-beheerders bepaalde beheertaken doen. JEA biedt geen bescherming tegen gebruikers die al administrator-bevoegdheden hebben. Gebruikers die deel uitmaken van **Domeinadministrators**, lokale **beheerders**, of andere maximaal beschermde groepen van JEA-beveiligingen via een andere manier kunnen omzeilen. Ze kunnen bijvoorbeeld, meld u aan met RDP, externe MMC-consoles gebruiken of verbinding maken met onbeperkte PowerShell-eindpunten. Lokale beheerders op een systeem Wijzig ook JEA-configuraties om te kunnen extra gebruikers of wijzig de mogelijkheid van een rol om uit te breiden het bereik van wat een gebruiker in de JEA-sessie doen kan. Het is belangrijk om te evalueren van uw gebruikers JEA uitgebreide machtigingen om te zien of er andere manieren om bevoegde toegang te krijgen tot het systeem.

Normaal worden JEA voor reguliere dagelijks onderhoud en een just-in-time, de beheeroplossing voor bevoegde toegang waarmee gebruikers tijdelijk worden lokale beheerders in noodsituaties. Dit zorgt ervoor gebruikers zijn niet permanente beheerders op het systeem, maar deze rechten kunnen krijgen als en alleen wanneer ze een werkstroom die documenten van hun gebruik van deze machtigingen hebt voltooid.
