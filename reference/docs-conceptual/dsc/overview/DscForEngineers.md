---
ms.date: 10/13/2017
keywords: DSC, Power shell, configuratie, installatie
title: Overzicht Desired State Configuration voor technici
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941836"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Overzicht Desired State Configuration voor technici

Dit document is bedoeld voor ontwikkel aars-en IT-teams om inzicht te krijgen in de voor delen van Power shell desired state Configuration (DSC).
Voor een weer gave op een hoger niveau van de waarde DSC vindt [u een overzicht van de desired state Configuration voor besluit vormers](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Voor delen van desired state Configuration

DSC bestaat uit:

- De complexiteit van het uitvoeren van scripts in Windows verminderen
- De snelheid van herhaling verhogen

Het concept van ' continue implementatie ' wordt belang rijker.
Continue implementatie houdt in dat u regel matig, mogelijk vaak per dag, kunt implementeren.
Het doel van deze implementaties is om iets niet op te lossen, maar om snel iets te doen.
Door nieuwe functies zo soepel en betrouwbaar mogelijk te maken, verkleint u de tijd tot waard van nieuwe bedrijfs logica.

De overstap naar Cloud Computing impliceert een implementatie oplossing die gebruikmaakt van een ' declaratief ' sjabloon model, waarbij een eind status omgeving wordt gedeclareerd als tekst en wordt gepubliceerd naar een implementatie-engine.
Met deze implementatie techniek kunt u op schaal snel wijzigingen door lopen, waarbij u op elk gewenst moment de implementatie consistent kunt herhalen om een eind status te garanderen.
Het maken van hulpprogram ma's en services die ondersteuning bieden voor deze stijl van bewerkingen via Automation is een antwoord op deze wijzigingen.

DSC is een platform dat declaratieve en idempotent (Herhaal bare) implementatie, configuratie en conformiteit biedt.
Met het DSC-platform kunt u ervoor zorgen dat de onderdelen van uw Data Center de juiste configuratie hebben, waardoor fouten worden voor komen en dat er geen kosten in rekening worden getreden.
Door DSC-configuraties te behandelen als onderdeel van de toepassings code, maakt DSC gebruik van continue implementatie.
De DSC-configuratie moet worden bijgewerkt als onderdeel van de toepassing, zodat de kennis die nodig is om de toepassing te implementeren altijd up-to-date is en klaar is om te worden gebruikt.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Ik heb Power shell, waarom heb ik de gewenste status configuratie nodig?"

DSC-configuraties van afzonderlijke intentie, of ' wat ik wil doen ', van uitvoering of ' Hoe wil ik dit doen? '
Dit betekent dat de logica van de uitvoering in de resources is opgenomen.
Gebruikers hoeven niet te weten hoe ze een functie moeten implementeren of implementeren wanneer een DSC-resource voor die functie beschikbaar is.
Op deze manier kan de gebruiker zich richten op de structuur van de implementatie.

Power shell-scripts zouden er als voor beeld als volgt moeten uitzien:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Dit script is eenvoudig, begrijpelijk en eenvoudig.
Als u het script echter probeert te plaatsen in productie, worden er meerdere problemen uitgevoerd.
Wat gebeurt er als dat script twee keer in een rij wordt uitgevoerd?
Wat gebeurt er als Bob eerder volledige toegang had tot de share?

Om deze problemen te compenseren, ziet een ' Real '-versie van het script er dichter als:
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

Dit script is complexere, met veel logica en fout afhandeling.
Het script is ingewik kelder omdat u niet meer weet wat u wilt doen, maar hoe u *Dit doet*.

Met DSC kunt u zeggen wat u wilt doen en de onderliggende logica wordt abstract gemaakt.

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

Dit script is duidelijk opgemaakt en eenvoudig te lezen.
De logische paden en fout afhandeling zijn nog steeds aanwezig in de [resource](../resources/resources.md) -implementatie, maar zijn niet zichtbaar voor de auteur van het script.

## <a name="separating-environment-from-structure"></a>Omgeving scheiden van structuur

Een gemeen schappelijk patroon in DevOps is om meerdere omgevingen te hebben voor de implementatie.
Er kan bijvoorbeeld een ' dev ' omgeving worden gebruikt om snel nieuwe code te prototypen.
De code van de omgeving ' dev ' gaat in een test omgeving, waar andere personen de nieuwe functionaliteit verifiëren.
Ten slotte gaat de code naar ' Prod ' of de productie omgeving van de live site.

DSC-configuraties voldoen aan deze dev-test-Prod-pijp lijn door het gebruik van [configuratie gegevens](../configurations/configData.md).
Hiermee wordt het verschil tussen de structuur van de configuratie van de knoop punten die worden beheerd, verder abstract.
U kunt bijvoorbeeld een configuratie definiëren waarvoor een SQL-Server, een IIS-server en een server voor de middelste laag zijn vereist.
Ongeacht welke knoop punten de verschillende onderdelen van deze configuratie ontvangen, zullen deze drie elementen altijd aanwezig zijn.
U kunt configuratie gegevens gebruiken om alle drie de elementen op dezelfde machine te laten wijzen voor een ontwikkel omgeving, de drie elementen van elkaar te scheiden op drie verschillende machines voor een test omgeving, en ten slotte naar alle productie servers voor de Prod-omgeving.
Als u wilt implementeren in de verschillende omgevingen, kunt u **Start-DscConfiguration** aanroepen met de juiste configuratie gegevens voor de omgeving die u wilt instellen.

## <a name="see-also"></a>Zie ook

[Configuraties](../configurations/configurations.md)

[Configuratie gegevens](../configurations/configData.md)

[Resources](../resources/resources.md)
