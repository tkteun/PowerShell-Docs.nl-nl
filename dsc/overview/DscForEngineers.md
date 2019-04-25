---
ms.date: 10/13/2017
keywords: DSC, powershell, configuratie en installatie
title: Overzicht Desired State Configuration voor technici
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079968"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Overzicht Desired State Configuration voor technici

Dit document is bedoeld voor ontwikkelaars en uitvoerende teams om te begrijpen van de voordelen van PowerShell Desired State Configuration (DSC).
Voor de weergave van een hoger niveau van de DSC-waarde biedt, Raadpleeg [overzicht van Desired State Configuration voor besluitvormers](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Voordelen van Desired State Configuration

Er bestaat een DSC naar:

- Verkleinen van de complexiteit van het uitvoeren van scripts in Windows
- De snelheid van iteratie verhogen

Het concept van 'continue implementatie' steeds belangrijker.
Continue implementatie betekent dat de mogelijkheid tot het implementeren van vaker en mogelijk meerdere keren per dag.
Het doel van deze implementaties zijn niet op te lossen, maar om op te halen iets snel gepubliceerd.
Met het ophalen van nieuwe functies bij de ontwikkeling in werking zo soepel en betrouwbaar mogelijk, kunt u tijd-waarde van nieuwe zakelijke logica verminderen.

De overstap naar cloudcomputing betekent een implementatieoplossing die gebruikmaakt van een "declaratieve" sjabloon-model, waarbij een end-status-omgeving is gedeclareerd als tekst en gepubliceerd naar een implementatie-engine.
Deze techniek implementatie kunt u snelle veranderingen, op schaal, met de tolerantie tegen bedreiging van de fout omdat op elk gewenst moment de implementatie kan worden steeds herhaald om te waarborgen van een end-status.
Het maken van hulpprogramma's en services die ondersteuning bieden voor de stijl van bewerkingen via automation is een antwoord op deze wijzigingen.

DSC is een platform dat biedt een declaratieve en idempotent zijn (herhaalbare)-implementatie, configuratie en conformiteit.
De DSC-platform kunt u om ervoor te zorgen dat de onderdelen van uw datacenter de juiste configuratie, die voorkomt fouten en voorkomt u dat kostbare implementatiefouten.
DSC wordt door het DSC-configuraties te behandelen als onderdeel van de toepassingscode, continue implementatie ingeschakeld.
De DSC-configuratie moet worden bijgewerkt als onderdeel van de toepassing, ervoor te zorgen dat de kennis die nodig zijn om de toepassing te implementeren is altijd up-to-date en klaar om te worden gebruikt.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Ik heb PowerShell, waarom ik moet Desired State Configuration?"

DSC-configuraties afzonderlijk doel of 'wat ik wil doen', worden uitgevoerd of "hoe ik wil doen."
Dit betekent dat de logica van de uitvoering is opgenomen in de resources.
Gebruikers hoeven niet te weten hoe u voor het implementeren of implementeren van een functie wanneer een DSC-resource voor deze functie beschikbaar is.
Hierdoor kan de gebruiker zich kunt richten op de structuur van de implementatie.

Een voorbeeld: PowerShell-scripts als volgt uitzien:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Dit script is eenvoudig, begrijpen en eenvoudig.
Als u het script in productie brengen probeert, kunt u wordt echter voor uitgevoerd in verschillende problemen.
Wat gebeurt er als dat het script wordt uitgevoerd twee keer op rij?
Wat gebeurt er als Bob eerder volledige toegang tot de share?

Om te compenseren voor deze problemen, er een 'echte' versie van het script dichter bij ongeveer als volgt:
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Dit script is complexer worden, met veel van de logica en foutafhandeling.
Het script is wat ingewikkelder, omdat u niet meer worden weergegeven wat u wilt dat gereed is, maar *hoe voer ik*.

DSC kunt u kunt aangeven wat u wilt gereed en de onderliggende logica is ze kunnen worden opgeslagen.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Dit script is correct opgemaakte en eenvoudig te lezen.
De logische paden en foutafhandeling zijn wel aanwezig in de [resource](../resources/resources.md) -implementatie, maar onzichtbaar voor de auteur van het script.

## <a name="separating-environment-from-structure"></a>Het scheiden van de omgeving van de structuur

Een algemeen patroon in DevOps is dat meerdere omgevingen voor implementatie.
Bijvoorbeeld, er mogelijk een ' '-ontwikkelomgeving gebruikt voor het snel prototype nieuwe code.
De code van de ontwikkelingsomgeving '', krijgt een omgeving 'test', waar anderen controleren of de nieuwe functionaliteit.
Ten slotte wordt de code in op 'prod' of de live site productie-omgeving.

DSC-configuraties kunnen deze dev-test-prod-pijplijn met behulp van [configuratiegegevens](../configurations/configData.md).
Hiermee isoleert verder het verschil tussen de structuur van de configuratie van de knooppunten die worden beheerd.
U kunt bijvoorbeeld een configuratie waarvoor een SQL-server, een IIS-server en een server voor de middelste laag definiëren.
Ongeacht welke knooppunten de verschillende onderdelen van deze configuratie ontvangen, wordt deze drie elementen altijd aanwezig zijn.
U kunt configuratiegegevens zodat alle drie elementen op dezelfde computer voor een ontwikkelingsomgeving, afzonderlijk van de drie elementen naar drie verschillende computers voor een testomgeving, en tot slot naar al uw productieservers voor de productie-omgeving.
Als u wilt implementeren op de verschillende omgevingen, kunt u aanroepen **Start-DscConfiguration** met de juiste configuratiegegevens voor de omgeving die u wilt targeten.

## <a name="see-also"></a>Zie ook

[Configuraties](../configurations/configurations.md)

[Configuratiegegevens](../configurations/configData.md)

[Resources](../resources/resources.md)
