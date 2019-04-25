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
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="93468-103">Overzicht Desired State Configuration voor technici</span><span class="sxs-lookup"><span data-stu-id="93468-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="93468-104">Dit document is bedoeld voor ontwikkelaars en uitvoerende teams om te begrijpen van de voordelen van PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="93468-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="93468-105">Voor de weergave van een hoger niveau van de DSC-waarde biedt, Raadpleeg [overzicht van Desired State Configuration voor besluitvormers](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="93468-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="93468-106">Voordelen van Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="93468-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="93468-107">Er bestaat een DSC naar:</span><span class="sxs-lookup"><span data-stu-id="93468-107">DSC exists to:</span></span>

- <span data-ttu-id="93468-108">Verkleinen van de complexiteit van het uitvoeren van scripts in Windows</span><span class="sxs-lookup"><span data-stu-id="93468-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="93468-109">De snelheid van iteratie verhogen</span><span class="sxs-lookup"><span data-stu-id="93468-109">Increase the speed of iteration</span></span>

<span data-ttu-id="93468-110">Het concept van 'continue implementatie' steeds belangrijker.</span><span class="sxs-lookup"><span data-stu-id="93468-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="93468-111">Continue implementatie betekent dat de mogelijkheid tot het implementeren van vaker en mogelijk meerdere keren per dag.</span><span class="sxs-lookup"><span data-stu-id="93468-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="93468-112">Het doel van deze implementaties zijn niet op te lossen, maar om op te halen iets snel gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="93468-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="93468-113">Met het ophalen van nieuwe functies bij de ontwikkeling in werking zo soepel en betrouwbaar mogelijk, kunt u tijd-waarde van nieuwe zakelijke logica verminderen.</span><span class="sxs-lookup"><span data-stu-id="93468-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="93468-114">De overstap naar cloudcomputing betekent een implementatieoplossing die gebruikmaakt van een "declaratieve" sjabloon-model, waarbij een end-status-omgeving is gedeclareerd als tekst en gepubliceerd naar een implementatie-engine.</span><span class="sxs-lookup"><span data-stu-id="93468-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="93468-115">Deze techniek implementatie kunt u snelle veranderingen, op schaal, met de tolerantie tegen bedreiging van de fout omdat op elk gewenst moment de implementatie kan worden steeds herhaald om te waarborgen van een end-status.</span><span class="sxs-lookup"><span data-stu-id="93468-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="93468-116">Het maken van hulpprogramma's en services die ondersteuning bieden voor de stijl van bewerkingen via automation is een antwoord op deze wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="93468-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="93468-117">DSC is een platform dat biedt een declaratieve en idempotent zijn (herhaalbare)-implementatie, configuratie en conformiteit.</span><span class="sxs-lookup"><span data-stu-id="93468-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="93468-118">De DSC-platform kunt u om ervoor te zorgen dat de onderdelen van uw datacenter de juiste configuratie, die voorkomt fouten en voorkomt u dat kostbare implementatiefouten.</span><span class="sxs-lookup"><span data-stu-id="93468-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="93468-119">DSC wordt door het DSC-configuraties te behandelen als onderdeel van de toepassingscode, continue implementatie ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="93468-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="93468-120">De DSC-configuratie moet worden bijgewerkt als onderdeel van de toepassing, ervoor te zorgen dat de kennis die nodig zijn om de toepassing te implementeren is altijd up-to-date en klaar om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="93468-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="93468-121">"Ik heb PowerShell, waarom ik moet Desired State Configuration?"</span><span class="sxs-lookup"><span data-stu-id="93468-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="93468-122">DSC-configuraties afzonderlijk doel of 'wat ik wil doen', worden uitgevoerd of "hoe ik wil doen."</span><span class="sxs-lookup"><span data-stu-id="93468-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="93468-123">Dit betekent dat de logica van de uitvoering is opgenomen in de resources.</span><span class="sxs-lookup"><span data-stu-id="93468-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="93468-124">Gebruikers hoeven niet te weten hoe u voor het implementeren of implementeren van een functie wanneer een DSC-resource voor deze functie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="93468-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="93468-125">Hierdoor kan de gebruiker zich kunt richten op de structuur van de implementatie.</span><span class="sxs-lookup"><span data-stu-id="93468-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="93468-126">Een voorbeeld: PowerShell-scripts als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="93468-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="93468-127">Dit script is eenvoudig, begrijpen en eenvoudig.</span><span class="sxs-lookup"><span data-stu-id="93468-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="93468-128">Als u het script in productie brengen probeert, kunt u wordt echter voor uitgevoerd in verschillende problemen.</span><span class="sxs-lookup"><span data-stu-id="93468-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="93468-129">Wat gebeurt er als dat het script wordt uitgevoerd twee keer op rij?</span><span class="sxs-lookup"><span data-stu-id="93468-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="93468-130">Wat gebeurt er als Bob eerder volledige toegang tot de share?</span><span class="sxs-lookup"><span data-stu-id="93468-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="93468-131">Om te compenseren voor deze problemen, er een 'echte' versie van het script dichter bij ongeveer als volgt:</span><span class="sxs-lookup"><span data-stu-id="93468-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
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

<span data-ttu-id="93468-132">Dit script is complexer worden, met veel van de logica en foutafhandeling.</span><span class="sxs-lookup"><span data-stu-id="93468-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="93468-133">Het script is wat ingewikkelder, omdat u niet meer worden weergegeven wat u wilt dat gereed is, maar *hoe voer ik*.</span><span class="sxs-lookup"><span data-stu-id="93468-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="93468-134">DSC kunt u kunt aangeven wat u wilt gereed en de onderliggende logica is ze kunnen worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="93468-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

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

<span data-ttu-id="93468-135">Dit script is correct opgemaakte en eenvoudig te lezen.</span><span class="sxs-lookup"><span data-stu-id="93468-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="93468-136">De logische paden en foutafhandeling zijn wel aanwezig in de [resource](../resources/resources.md) -implementatie, maar onzichtbaar voor de auteur van het script.</span><span class="sxs-lookup"><span data-stu-id="93468-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="93468-137">Het scheiden van de omgeving van de structuur</span><span class="sxs-lookup"><span data-stu-id="93468-137">Separating Environment from Structure</span></span>

<span data-ttu-id="93468-138">Een algemeen patroon in DevOps is dat meerdere omgevingen voor implementatie.</span><span class="sxs-lookup"><span data-stu-id="93468-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="93468-139">Bijvoorbeeld, er mogelijk een ' '-ontwikkelomgeving gebruikt voor het snel prototype nieuwe code.</span><span class="sxs-lookup"><span data-stu-id="93468-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="93468-140">De code van de ontwikkelingsomgeving '', krijgt een omgeving 'test', waar anderen controleren of de nieuwe functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="93468-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="93468-141">Ten slotte wordt de code in op 'prod' of de live site productie-omgeving.</span><span class="sxs-lookup"><span data-stu-id="93468-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="93468-142">DSC-configuraties kunnen deze dev-test-prod-pijplijn met behulp van [configuratiegegevens](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="93468-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="93468-143">Hiermee isoleert verder het verschil tussen de structuur van de configuratie van de knooppunten die worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="93468-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="93468-144">U kunt bijvoorbeeld een configuratie waarvoor een SQL-server, een IIS-server en een server voor de middelste laag definiëren.</span><span class="sxs-lookup"><span data-stu-id="93468-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="93468-145">Ongeacht welke knooppunten de verschillende onderdelen van deze configuratie ontvangen, wordt deze drie elementen altijd aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="93468-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="93468-146">U kunt configuratiegegevens zodat alle drie elementen op dezelfde computer voor een ontwikkelingsomgeving, afzonderlijk van de drie elementen naar drie verschillende computers voor een testomgeving, en tot slot naar al uw productieservers voor de productie-omgeving.</span><span class="sxs-lookup"><span data-stu-id="93468-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="93468-147">Als u wilt implementeren op de verschillende omgevingen, kunt u aanroepen **Start-DscConfiguration** met de juiste configuratiegegevens voor de omgeving die u wilt targeten.</span><span class="sxs-lookup"><span data-stu-id="93468-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="93468-148">Zie ook</span><span class="sxs-lookup"><span data-stu-id="93468-148">See Also</span></span>

[<span data-ttu-id="93468-149">Configuraties</span><span class="sxs-lookup"><span data-stu-id="93468-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="93468-150">Configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="93468-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="93468-151">Resources</span><span class="sxs-lookup"><span data-stu-id="93468-151">Resources</span></span>](../resources/resources.md)
