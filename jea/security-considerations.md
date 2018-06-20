---
ms.date: 06/12/2017
keywords: jea powershell beveiliging
title: JEA beveiligingsoverwegingen
ms.openlocfilehash: 46ea5cc3e9bc7b6759524aa466e900950a6dee26
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190176"
---
# <a name="jea-security-considerations"></a>JEA beveiligingsoverwegingen

> Van toepassing op: Windows PowerShell 5.0

JEA helpt u bij uw beveiligingspostuur verbeteren door het aantal permanente beheerders op uw computers te verminderen.
Dit gebeurt door het maken van een nieuw toegangspunt voor gebruikers voor het beheren van het systeem (een PowerShell-sessie configuration) nauw standaard om te voorkomen dat misbruik wordt vergrendeld.
Gebruikers die sommige, maar niet nodig hebben onbeperkte toegang tot de computer voor het uitvoeren van beheertaken kan toegang tot het eindpunt JEA worden verleend.
JEA kunnen deze opdrachten uit te voeren admin zonder rechtstreeks beheerderstoegang, kunt u vervolgens die gebruikers verwijderen uit maximaal bevoorrechte beveiligingsgroepen (zodat ze kunnen gebruikers standaard).

Dit onderwerp beschrijft de JEA beveiligingsmodel en best practices in meer detail.

## <a name="run-as-account"></a>Run As-account

Elk eindpunt JEA heeft een aangewezen 'uitvoeren als'-account, dat het account waaronder de gebruiker verbinding maakt acties worden uitgevoerd.
Dit account is geconfigureerd in de [sessie configuratiebestand](session-configurations.md), en het account dat u kiest een grote invloed heeft op de beveiliging van uw eindpunt.

**Virtuele accounts** zijn de aanbevolen manier van het configureren van het run as-account.
Virtuele accounts zijn eenmalige, tijdelijke lokale accounts die zijn gemaakt voor de gebruiker verbinding probeert te maken voor gebruik tijdens de duur van hun JEA-sessie.
Zodra de sessie wordt beëindigd, wordt de virtuele-account wordt vernietigd en kan niet meer worden gebruikt.
De gebruiker verbinding maakt niet de referenties voor de virtuele account weet en virtueel account toegang tot het systeem via andere middelen, zoals Extern bureaublad of een onbeperkte PowerShell-eindpunt niet gebruiken.

Standaard worden virtuele accounts behoren tot de lokale groep administrators op de machine.
Dit geeft ze volledige rechten voor het beheren van op het systeem, maar geen rechten voor het beheren van bronnen op het netwerk.
Bij de verificatie met andere virtuele machines, worden de context van de gebruiker die het lokale computeraccount niet de virtueel account.

Domeincontrollers zijn een speciaal geval, omdat er geen concept van een lokale groep administrators.
In plaats daarvan virtuele accounts in plaats daarvan behoren tot Domeinadministrators en de directoryservices op de domeincontroller kunnen beheren.
De identiteit van het domein is nog steeds beperkt tot het op de domeincontroller waar de sessie JEA is geïnstantieerd en toegang tot het netwerk wordt weergegeven in plaats daarvan afkomstig zijn van de computer van het domeincontrollerobject gebruiken.

In beide gevallen kunt u ook expliciet welke beveiligingsgroepen virtueel account tot behoren moet definiëren.
Dit is een goede gewoonte wanneer de taak die u uitvoert zonder lokale/of domein beheerdersbevoegdheden kan worden gedaan.
Als u al een beveiligingsgroep die is gedefinieerd voor uw beheerders hebt, kunt u gewoon het lidmaatschap van de virtueel account verlenen aan die groep hieraan de machtigingen die nodig is.
Virtueel account lidmaatschap is beperkt tot lokale beveiligingsgroepen op werkstation en servers, maar op een domeincontroller alleen kan worden lid van domein, beveiligingsgroepen.
Wanneer u een of meer beveiligingsgroepen voor de virtuele-account om u te behoren tot opgeeft, wordt deze niet langer hoort bij de standaardgroepen (lokale Administrators of domeinbeheerder).

De onderstaande tabel bevat een overzicht van de mogelijke configuratie-opties en de resulterende machtigingen voor virtuele accounts

Het computertype                | Configuratie van virtueel account | Lokale gebruikerscontext                                      | Netwerk gebruikerscontext
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Domeincontroller            | Standaardinstelling                             | Domeingebruiker, lid is van '*domein*\Domain Admins'         | Computeraccount
Domeincontroller            | Domeingroepen A en B               | Domeingebruiker, lid is van '*domein*\A ','*domein*\ber '       | Computeraccount
Lidserver of werkstation | Standaardinstelling                             | Lokale gebruiker, lid is van '*BUILTIN*\Administrators'        | Computeraccount
Lidserver of werkstation | Lokale groepen C en D                | Lokale gebruiker, lid is van '*COMPUTER*\C' en '*COMPUTER*\D' | Computeraccount

Als u gebeurtenissen voor beveiligingscontrole en de gebeurtenislogboeken van toepassingen bekijkt, ziet u dat elke gebruiker JEA sessie een uniek virtueel account heeft.
Zo kunt u gebruikersacties in een eindpunt JEA terug naar de oorspronkelijke gebruiker die de opdracht uitvoert.
Virtueel account namen volgt u de indeling ' WinRM virtuele gebruikers\\WinRM\_VA\_*ACCOUNTNUMBER*\_*domein* \_ *sAMAccountName*' als gebruiker "Els' in 'Contoso' domein opnieuw wordt opgestart een service in een eindpunt JEA, de gebruikersnaam die is gekoppeld aan de service control manager gebeurtenissen zou bijvoorbeeld ' WinRM virtuele gebruikers\\WinRM\_ VA\_1\_contoso\_Els '.


**Groep beheerde serviceaccounts (gmsa's)** zijn nuttig wanneer er een lidserver moet toegang hebben tot netwerkbronnen in de sessie JEA.
Een voorbeeld gebruiksvoorbeeld voor dit is een JEA-eindpunt dat wordt gebruikt voor toegang tot een REST-API die worden gehost op een andere computer beheren.
Het is gemakkelijk om te schrijven functies om de gewenste aanroepen in de REST-API, maar om te verifiëren met de API die u moeten een netwerk-id.
Met behulp van een groep beheerd serviceaccount, maakt de 'tweede hop' mogelijk en toch hebben besturingselement gedurende welke computers de account kunnen gebruiken.
De effectieve machtigingen van de gMSA worden gedefinieerd door de beveiligingsgroepen (lokaal of domeinbeheerder) waarbij het gMSA-account hoort.

Wanneer een JEA-eindpunt is geconfigureerd voor gebruik van een beheerd serviceaccount, verschijnt de acties van gebruikers met alle JEA afkomstig zijn van dezelfde groep beheerd serviceaccount.
De enige manier kunt u acties terug naar een specifieke gebruiker traceren is het identificeren van de reeks opdrachten uitvoert in de tekst van een PowerShell-sessie.

**-Passthrough referenties** worden gebruikt wanneer u niet opgeven van een run as-account en wilt dat PowerShell te gebruiken referenties van de gebruiker van de verbindende opdrachten uit te voeren op de externe server.
Deze configuratie is *niet* voor JEA wordt aanbevolen als u de verbindende gebruiker direct toegang verlenen tot bevoegde beheergroepen zou moeten.
Als de gebruiker verbinding maakt al beheerdersbevoegdheden, kunnen JEA helemaal te voorkomen en beheren van het systeem via andere, onbeperkte middelen.
Zie de sectie hieronder voor het [JEA biedt geen bescherming tegen admins](#jea-does-not-protect-against-admins) voor meer informatie.

**Standaard run as-accounts** kunt u opgeven van een gebruikersaccount op waaronder de gehele PowerShell-sessie wordt uitgevoerd.
Dit is een belangrijk verschil, omdat een sessieconfiguratie is ingesteld op een vaste run as-account gebruiken (met de `-RunAsCredential` parameter) is niet JEA-bewust.
Dat betekent dat roldefinities niet meer werkt zoals verwacht, en elke gebruiker die toegang hebben tot het eindpunt wordt dezelfde rol worden toegewezen.

U moet een RunAsCredential niet gebruiken op een eindpunt JEA vanwege de problemen bij het traceren van acties weer voor specifieke gebruikers en het ontbreken van ondersteuning voor het toewijzen van gebruikers aan rollen.

## <a name="winrm-endpoint-acl"></a>WinRM ACL voor eindpunten

Als met de reguliere PowerShell remoting eindpunten, elk eindpunt JEA een afzonderlijke toegangsbeheerlijst (ACL heeft) instellen in de WinRM-configuratie die bepaalt kunnen die worden geverifieerd met het eindpunt JEA.
Als u niet goed geconfigureerd, vertrouwde gebruikers wellicht geen toegang krijgen tot het eindpunt JEA en/of niet-vertrouwde gebruikers toegang kunnen krijgen.
De WinRM-ACL bepaalt echter niet het geval is, de toewijzing van gebruikers aan rollen JEA.
Die wordt beheerd door de *RoleDefinitions* veld in het configuratiebestand van de sessie die is geregistreerd op het systeem.

Standaard, wanneer u registreert een JEA-eindpunt met een configuratiebestand sessie als een of meer mogelijkheden voor rol, wordt de WinRM-ACL worden geconfigureerd, zodat alle gebruikers toewijzen aan een of meer rollen-toegang tot het eindpunt.
Bijvoorbeeld, een JEA-sessie die is geconfigureerd met behulp van de volgende opdrachten wordt volledige toegang verlenen tot *CONTOSO\JEA\_Lev1* en *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

U kunt controleren de machtigingen van gebruiker met de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Als u wilt wijzigen welke gebruikers toegang hebben, voer een `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` voor een interactieve prompt of `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` de machtigingen bijwerken.
Gebruikers moeten ten minste *Invoke* rechten voor toegang tot het eindpunt JEA.

Als extra gebruikers toegang tot het eindpunt JEA krijgen maar niet in een van de rollen gedefinieerd in het configuratiebestand van de sessie vallen, worden ze kunnen een JEA-sessie starten, maar hebben alleen toegang tot de standaard-cmdlets.
U kunt de gebruikersmachtigingen in een eindpunt JEA controleren door te voeren `Get-PSSessionCapability`.
Bekijk de [controle en rapportage over JEA](audit-and-report.md) artikel voor meer informatie over controle en die opdrachten van een gebruiker toegang heeft tot in een JEA-eindpunt.

## <a name="least-privilege-roles"></a>Minimale bevoegdheid rollen

Bij het ontwerpen van JEA rollen, is het belangrijk te weten dat de virtuele of groep beheerde service-account met achter de schermen vaak onbeperkte toegang tot het beheer van de lokale computer heeft.
JEA rol mogelijkheden te beperken waarvoor dat account kan worden gebruikt door het beperken van de opdrachten en toepassingen die kunnen worden uitgevoerd met behulp van die bevoegde context.
Onjuist ontworpen rollen kunt gevaarlijke opdrachten die een gebruiker kan opsplitsen buiten de grenzen JEA of toegang krijgen tot gevoelige informatie.

Neem bijvoorbeeld de volgende vermelding van de rol-functionaliteit:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Deze mogelijkheid rol kan gebruikers een PowerShell-cmdlet uitvoeren met het zelfstandig naamwoord 'Proces' van de module Microsoft.PowerShell.Management.
Gebruikers hebben mogelijk nodig voor toegang tot cmdlets, zoals `Get-Process` om te begrijpen welke toepassingen worden uitgevoerd op het systeem en `Stop-Process` afsluiten een vastgelopen toepassingen.
Deze vermelding ook kan echter `Start-Process`, die kan worden gebruikt om op te starten met volledige administrator-machtigingen van een willekeurige programma.
Het programma niet moet lokaal op het systeem worden geïnstalleerd zodat een adversary kan een programma te starten op een bestandsshare waarmee de verbindende gebruikersbevoegdheden voor lokale beheerder en schadelijke software wordt uitgevoerd.'

Een beter beveiligde versie van deze mogelijkheid met dezelfde functie eruit als:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Vermijd het gebruik van jokertekens in de mogelijkheden van de rol en zorg ervoor dat [effectieve machtigingen van de audit](audit-and-report.md#check-effective-rights-for-a-specific-user) regelmatig om te begrijpen die opdrachten van een gebruiker toegang heeft tot.

## <a name="jea-does-not-protect-against-admins"></a>JEA biedt geen bescherming tegen beheerders

Een van de belangrijkste principes van JEA is dat kunnen niet-beheerders om uit te voeren *sommige* beheertaken.
JEA biedt geen bescherming tegen mensen die al administrator-bevoegdheden hebben.
Gebruikers die deel uitmaken van 'Domeinadministrators', 'lokale beheerders,' of andere maximaal bevoorrechte groepen in uw omgeving nog steeds mogelijk om op te halen om de bescherming van JEA wanneer u zich aanmeldt bij de computer via een andere manier.
Ze kunnen bijvoorbeeld aanmelden met RDP, externe MMC-consoles gebruiken of verbinding maken met onbeperkte PowerShell-eindpunten.
Lokale beheerder zijn op het systeem kunt JEA configuraties als u extra gebruikers beheren van het systeem of wijzigen van een rol mogelijkheid om uit te breiden het bereik van wat een gebruiker in hun sessie JEA doen kan mogen ook wijzigen.
Daarom is het belangrijk om te bepalen van uw gebruikers JEA uitgebreide machtigingen om te zien of er andere manieren ze kunnen bevoorrechte toegang krijgen tot het systeem.

Een gebruikelijk is JEA voor regelmatig onderhoud van de dagelijkse en hebben een 'just-in tijd' uitgebreide oplossing voor het beheer van toegang kunnen gebruikers zich tijdelijk worden lokale beheerders in noodsituaties.
Dit zorgt ervoor gebruikers geen permanente beheerders op het systeem, maar deze rechten kunnen krijgen als en alleen wanneer ze een werkstroom die het gebruik van deze machtigingen documenten voltooien.