---
ms.date: 10/13/2017
keywords: DSC, powershell, configuratie, setup
title: Overzicht Desired State Configuration voor besluitvormers
ms.openlocfilehash: f8a851c5fbc5165ebe9642c5cd60964f1584efab
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189887"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Overzicht Desired State Configuration voor technici

Dit document is bedoeld voor teams van ontwikkelaars en bewerkingen om te begrijpen wat de voordelen van PowerShell Desired State Configuration (DSC).
Voor de weergave van een hoger niveau van de waarde DSC biedt, raadpleegt u [Desired Configuration overzicht voor besluitvormers](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Voordelen van Desired State Configuration

DSC bestaat met:

- Verklein de complexiteit van het uitvoeren van scripts in Windows
- De snelheid van herhaling verhogen

Het concept van 'continue implementatie' steeds belangrijker.
Doorlopende implementatie betekent dat de mogelijkheid om te implementeren, mogelijk meerdere keren per dag.
Het doel van deze implementaties zijn niet iets te repareren, maar naar iets snel gepubliceerd.
Met het ophalen van nieuwe functies via ontwikkeling in werking zo soepel en betrouwbaar mogelijk, moet u naar tijdwaarde maken van nieuwe bedrijfslogica verminderen.

De overgang naar cloud computing impliceert een implementatieoplossing die gebruikmaakt van een model 'declaratieve' sjabloon, waarbij een end-status-omgeving is gedeclareerd als tekst en gepubliceerd naar een implementatie-engine.
Deze techniek implementatie kunt u snel wijzigen, klikt u op grote schaal, met herstelmogelijkheden tegen bedreiging van de fout omdat op elk gewenst moment de implementatie kan worden consistent herhaald om bescherming te bieden een end-status.
Het maken van de hulpprogramma's en services die ondersteuning bieden voor deze stijl van bewerkingen door middel van automatisering is een reactie op deze wijzigingen.

DSC is een platform waarmee declaratieve en idempotent (herhaalbare)-implementatie, configuratie en overeenstemming.
De DSC-platform kunt u om ervoor te zorgen dat de onderdelen van uw datacenter de juiste configuratie, die voorkomt fouten en kostbaar implementatiestoringen voorkomt.
DSC ingeschakeld door het DSC-configuraties te behandelen als onderdeel van de toepassingscode, continue implementatie.
De DSC-configuratie moet worden bijgewerkt als onderdeel van de toepassing, ervoor zorgen dat de kennis die nodig zijn voor het implementeren van de toepassing altijd actueel en klaar om te worden gebruikt.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>'Ik heb PowerShell, waarom ik Desired State Configuration moet?'

DSC-configuraties afzonderlijk doel of 'wat ik wil', uitvoeren of "hoe ik wil dit doen."
Dit betekent dat de logica van de uitvoering van deel uitmaakt van de resources.
Gebruikers hoeven niet te weten hoe u kunt implementeren of implementeren van een functie wanneer een DSC-resource voor deze functie beschikbaar is.
Hierdoor kan de gebruiker zich richten op de structuur van hun implementatie.

Als u bijvoorbeeld er PowerShell-scripts als volgt uit:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Dit script is eenvoudig, begrijpen en snel.
Als u het script in productie te stellen probeert, kunt u wordt echter voor uitvoeren in verschillende problemen.
Wat gebeurt er als die script tweemaal in een rij wordt uitgevoerd?
Wat gebeurt er als Bob had eerder volledige toegang tot de share?

Om te compenseren voor deze problemen, een 'echte' versie van het script ziet er dichter bij ongeveer als volgt:
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

Dit script is complexere met veel van de logica en foutafhandeling.
Het script is complexer omdat u niet meer worden weergegeven naar wens gereed is, maar *te werk*.

DSC kunt u aannemen dat u de gewenste gereed en de onderliggende logica beschouwing verwijderd.

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
          ReadAccess  = "Alice"
          FullAccess  = "Bob"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Dit script is foutloos geformatteerd en eenvoudig te lezen.
De logische paden en foutafhandeling nog steeds aanwezig zijn in de [resource](resources.md) implementatie, maar onzichtbaar voor de auteur van het script.

## <a name="separating-environment-from-structure"></a>Het scheiden van de omgeving van structuur

Een algemene patroon in DevOps is om meerdere omgevingen voor implementatie.
Bijvoorbeeld, kunnen er een 'dev'-omgeving gebruikt voor het snel prototype nieuwe code.
De code uit de omgeving 'dev' gaat in een omgeving 'test' anderen controleren waar de nieuwe functionaliteit.
Ten slotte wordt de code 'prod' of de productieomgeving live site.

DSC-configuraties mogelijk deze dev-test-prod-pipeline met behulp van [configuratiegegevens](configData.md).
Hiermee isoleert verder het verschil tussen de structuur van de configuratie van de knooppunten die worden beheerd.
U kunt bijvoorbeeld een configuratie die een SQL-server, een IIS-server en een server voor de middelste laag vereist definiëren.
Ongeacht welke knooppunten de verschillende onderdelen van deze configuratie wordt weergegeven, wordt deze drie elementen altijd aanwezig zijn.
U kunt configuratiegegevens wijst alle drie elementen naar dezelfde machine in een omgeving dev afzonderlijke uit de drie elementen met drie verschillende machines voor een testomgeving en tot slot naar uw productieservers voor de prod-omgeving.
Als u wilt implementeren in verschillende omgevingen, u kunt aanroepen **Start DscConfiguration** met de juiste configuratie van de gegevens voor de omgeving die u wilt targeten.

## <a name="see-also"></a>Zie ook

[Configuraties](configurations.md)

[Configuratiegegevens](configData.md)

[Resources](resources.md)