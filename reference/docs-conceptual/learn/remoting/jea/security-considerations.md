---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: Beveiligings overwegingen voor JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017907"
---
# <a name="jea-security-considerations"></a>Beveiligings overwegingen voor JEA

JEA helpt u uw beveiligings postuur te verbeteren door het aantal permanente beheerders op uw computers te verminderen. JEA maakt gebruik van een Power shell-sessie configuratie voor het maken van een nieuw toegangs punt voor gebruikers om het systeem te beheren. Gebruikers die een verhoogde bevoegdheden nodig hebben, maar niet onbeperkt, toegang tot de computer om taken uit te voeren, kunnen toegang krijgen tot het JEA-eind punt. Omdat JEA deze gebruikers in staat stelt om beheer opdrachten uit te voeren zonder volledige beheerders toegang, kunt u deze gebruikers vervolgens verwijderen uit beveiligings groepen met hoge bevoegdheden.

## <a name="run-as-account"></a>Run as-account

Elk JEA-eind punt heeft een aangewezen **uitvoeren als-** account. Dit is het account waarmee de acties van de verbinding van de gebruiker worden uitgevoerd. Dit account kan worden geconfigureerd in het [configuratie bestand](session-configurations.md)voor de sessie en het account dat u kiest, heeft een grote invloed op de beveiliging van uw eind punt.

**Virtuele accounts** zijn de aanbevolen manier voor het configureren van het **Run as-** account. Virtuele accounts zijn eenmalige, tijdelijke lokale accounts die worden gemaakt voor de verbinding die wordt gebruikt tijdens de duur van hun JEA-sessie. Zodra de sessie is beëindigd, wordt het virtuele account vernietigd en kan het niet meer worden gebruikt. De gebruiker die de verbinding maakt, kent de referenties voor het virtuele account niet. Het virtuele account kan niet worden gebruikt voor toegang tot het systeem via een andere manier als Extern bureaublad of een niet-beperkt Power shell-eind punt.

Standaard maken virtuele accounts deel uit van de lokale groep **Administrators** op de computer. Dit geeft hen volledige rechten om alles op het systeem te beheren, maar geen rechten voor het beheren van bronnen in het netwerk.
Bij verificatie met andere computers is de gebruikers context die van het lokale computer account, niet het virtuele account.

Domein controllers zijn een speciaal geval omdat er geen lokale groep **Administrators** is. In plaats daarvan behoren virtuele accounts bij **domein Administrators** en kan de Directory Services op de domein controller beheren. De domein identiteit is nog steeds beperkt voor gebruik op de domein controller waarop de JEA-sessie is geïnstantieerd. Alle netwerk toegang lijkt in plaats daarvan te zijn vanaf het computer object van de domein controller.

In beide gevallen kunt u expliciet definiëren tot welke beveiligings groepen het virtuele account behoort. Dit is een goede gewoonte wanneer de taak kan worden uitgevoerd zonder lokale of domein Administrator bevoegdheden. Als u al een beveiligings groep voor uw beheerders hebt gedefinieerd, verleent u het lidmaatschap van de virtuele account aan die groep. Groepslid maatschap van virtuele accounts is beperkt tot lokale beveiligings groepen op werk stations en lidservers. Op domein controllers moeten virtuele accounts lid zijn van domein beveiligings groepen.
Zodra het virtuele account is toegevoegd aan een of meer beveiligings groepen, maakt het niet langer deel uit van de standaard groepen (lokale of domein Administrators).

De volgende tabel bevat een overzicht van de mogelijke configuratie opties en de resulterende machtigingen voor virtuele accounts:

|        Computertype         | Configuratie van de virtuele-account groep |                   Lokale gebruikers context                    | Context netwerk gebruikers |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Domeincontroller            | Standaardinstelling                             | Domein gebruiker, lid van*domein*\Domain Administrators         | Computer account     |
| Domeincontroller            | Domein groepen A en B               | Domein gebruiker, lid van*domein*\a,*domein*\b       | Computer account     |
| Lidserver of werk station | Standaardinstelling                             | Lokale gebruiker, lid van*ingebouwd*\Administrators        | Computer account     |
| Lidserver of werk station | Lokale groepen C en D                | Lokale gebruiker, lid van*computer*\c en*computer*\d | Computer account     |

Wanneer u gebeurtenissen voor beveiligings controle en logboeken van toepassingen bekijkt, ziet u dat elke JEA-gebruikers sessie een uniek virtueel account heeft. Dit unieke account helpt u bij het volgen van gebruikers acties in een JEA-eind punt naar de oorspronkelijke gebruiker die de opdracht uitvoert. Namen van virtuele accounts voldoen aan de notatie `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` bijvoorbeeld als gebruiker **Lisa** in domein **Contoso** een service opnieuw start in een JEA-eind punt, wordt de gebruikers naam die aan de service besturings beheer-gebeurtenissen is gekoppeld, `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

Door een **groep beheerde service accounts (gmsa's)** zijn handig wanneer een lidserver toegang moet hebben tot netwerk bronnen in de JEA-sessie. Bijvoorbeeld wanneer een JEA-eind punt wordt gebruikt voor het beheren van de toegang tot een REST API-service die op een andere computer wordt gehost. Het is eenvoudig om functies te schrijven voor het aanroepen van de REST-Api's, maar u hebt een netwerk identiteit nodig om te verifiëren met de API. Door een door een groep beheerd service account te gebruiken, wordt de tweede hop mogelijk bij het behoud van de controle over de computers die het account kunnen gebruiken. De efficiënte machtigingen van de gMSA worden gedefinieerd door de beveiligings groepen (lokaal of domein) waartoe het gMSA-account behoort.

Wanneer een JEA-eind punt is geconfigureerd voor het gebruik van een gMSA, moeten de acties van alle JEA-gebruikers afkomstig zijn uit dezelfde gMSA. De enige manier om acties terug te sporen naar een specifieke gebruiker is het identificeren van de reeks opdrachten die worden uitgevoerd in een Power shell-sessie transcript.

**Pass-Through-referenties** worden gebruikt wanneer u geen **uitvoeren als-** account opgeeft. Power shell gebruikt de referenties van de verbinding van de gebruiker om opdrachten uit te voeren op de externe server. Hiervoor moet u de gebruiker rechtstreeks toegang verlenen tot geprivilegieerde beheer groepen. Deze configuratie wordt **niet** aanbevolen voor jea. Als de gebruiker die de verbinding maakt, al beheerders bevoegdheden heeft, kan deze het JEA voor komen en het systeem beheren via een andere, onbeperkte manier. Zie de sectie hieronder over de manier waarop [JEA geen bescherming biedt tegen beheerders](#jea-doesnt-protect-against-admins)voor meer informatie.

Met de **standaard run as-accounts** kunt u elk gebruikers account opgeven waaronder de volledige Power shell-sessie wordt uitgevoerd. Sessie configuraties die gebruikmaken van vaste **Run-as-** accounts (met de para meter `-RunAsCredential`) zijn niet jea. Roldefinities werken niet meer zoals verwacht. Elke gebruiker die gemachtigd is om toegang te krijgen tot het eind punt krijgt dezelfde rol toegewezen.

U mag geen **RunAsCredential** gebruiken op een JEA-eind punt omdat het lastig is om acties terug te sporen naar specifieke gebruikers en geen ondersteuning voor het toewijzen van gebruikers aan rollen.

## <a name="winrm-endpoint-acl"></a>WinRM-eindpunt-ACL

Net als bij gewone externe Power shell-eind punten heeft elk JEA-eind punt een afzonderlijke toegangs beheer lijst (ACL) die bepaalt wie zich kan verifiëren met het JEA-eind punt. Bij een onjuiste configuratie kunnen vertrouwde gebruikers geen toegang krijgen tot het JEA-eind punt en kunnen niet-vertrouwde gebruikers toegang hebben. De WinRM-ACL heeft geen invloed op de toewijzing van gebruikers aan JEA-rollen. Toewijzing wordt bepaald door het veld **RoleDefinitions** in het sessie configuratie bestand dat wordt gebruikt om het eind punt te registreren.

Wanneer een JEA-eind punt meerdere functie mogelijkheden heeft, wordt de WinRM-ACL standaard zo geconfigureerd dat toegang tot alle toegewezen gebruikers is toegestaan. Een JEA-sessie die is geconfigureerd met de volgende opdrachten, geeft bijvoorbeeld volledige toegang tot `CONTOSO\JEA_Lev1` en `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

U kunt de gebruikers machtigingen controleren met de cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) .

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Als u wilt wijzigen welke gebruikers toegang hebben, voert u `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` uit voor een interactieve prompt of `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` om de machtigingen bij te werken. Gebruikers *hebben ten minste recht op* toegang tot het JEA-eind punt.

Het is mogelijk om een JEA-eind punt te maken dat geen gedefinieerde rol toewijst aan elke gebruiker die toegang heeft. Deze gebruikers kunnen een JEA-sessie starten, maar hebben alleen toegang tot de standaard-cmdlets. U kunt de gebruikers machtigingen in een JEA-eind punt controleren door `Get-PSSessionCapability`uit te voeren. Zie [controle en rapportage op JEA](audit-and-report.md)voor meer informatie.

## <a name="least-privilege-roles"></a>Minimale bevoegdheden rollen

Bij het ontwerpen van JEA-rollen is het belang rijk te weten dat de virtuele en groep beheerde service accounts die achter de schermen worden uitgevoerd, onbeperkte toegang hebben tot de lokale computer. Met JEA kunt u de opdrachten en toepassingen beperken die in die geprivilegieerde context kunnen worden uitgevoerd.
Onjuist ontworpen rollen kunnen gevaarlijke opdrachten toestaan waardoor een gebruiker de grenzen van de JEA kan verstoren of toegang kan krijgen tot gevoelige informatie.

Denk bijvoorbeeld aan de volgende functie-invoer:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Deze functie biedt gebruikers de mogelijkheid om een Power shell-cmdlet uit te voeren met het zelfstandig **proces** uit de module **micro soft. Power shell. Management** . Gebruikers moeten mogelijk toegang hebben tot cmdlets zoals `Get-Process` om te zien welke toepassingen op het systeem worden uitgevoerd en `Stop-Process` om toepassingen te beëindigen die niet reageren. Met deze vermelding kunnen `Start-Process`echter ook worden gebruikt voor het starten van een wille keurig programma met volledige beheerders machtigingen. Het programma hoeft niet lokaal op het systeem te worden geïnstalleerd. Een verbonden gebruiker kan een programma starten van een bestands share die de lokale Administrator bevoegdheden van de gebruiker geeft, malware uitvoert en meer.

Een veiligere versie van dezelfde functie capaciteit zou er als volgt uitzien:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Vermijd het gebruik van joker tekens in functie mogelijkheden. Zorg ervoor dat u regel matig [effectief gebruikers machtigingen controleert](audit-and-report.md#check-effective-rights-for-a-specific-user) om te begrijpen welke opdrachten toegankelijk zijn voor de gebruiker.

## <a name="jea-doesnt-protect-against-admins"></a>JEA beschermt niet tegen beheerders

Een van de kern principes van JEA is dat niet-beheerders een aantal beheer taken kunnen uitvoeren. JEA biedt geen bescherming tegen gebruikers die al beheerders bevoegdheden hebben. Gebruikers die lid zijn van **domein Administrators**, lokale **beheerders**of andere groepen met hoge bevoegdheden, kunnen de beveiliging van JEA via een andere manier omzeilen. Ze kunnen zich bijvoorbeeld aanmelden met RDP, externe MMC-consoles gebruiken of verbinding maken met een niet-beperkt Power shell-eind punt. Lokale beheerders op een systeem kunnen ook JEA-configuraties wijzigen om extra gebruikers toe te staan of een functie mogelijkheid te wijzigen om het bereik van wat een gebruiker in hun JEA-sessie kan doen, uit te breiden. Het is belang rijk om de uitgebreide machtigingen van uw JEA-gebruikers te evalueren om te controleren of er andere manieren zijn om bevoegde toegang tot het systeem te verkrijgen.

Een veelvoorkomende procedure is het gebruik van JEA voor regel matige dagelijkse onderhoud en een just-in-time, Privileged Access Management-oplossing waarmee gebruikers tijdelijk lokale beheerders kunnen worden in nood situaties. Dit helpt ervoor te zorgen dat gebruikers geen permanente beheerders zijn op het systeem, maar deze rechten wel kunnen verkrijgen als en alleen wanneer ze een werk stroom volt ooien waarmee hun gebruik van deze machtigingen wordt gedocumenteerd.
