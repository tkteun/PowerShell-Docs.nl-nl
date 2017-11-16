---
ms.date: 2017-10-13
author: eslesar;mgreenegit
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Desired State Configuration overzicht voor besluitvormers
ms.openlocfilehash: 66822d9a60f98aab3d4f27d14b27ebc6ec90b2c9
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2017
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="c30ed-103">Desired State Configuration overzicht voor Engineers</span><span class="sxs-lookup"><span data-stu-id="c30ed-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="c30ed-104">Dit document is bedoeld voor teams van ontwikkelaars en bewerkingen om te begrijpen wat de voordelen van PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="c30ed-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span>
<span data-ttu-id="c30ed-105">Voor de weergave van een hoger niveau van de waarde DSC biedt, raadpleegt u [Desired Configuration overzicht voor besluitvormers](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="c30ed-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="c30ed-106">Voordelen van Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="c30ed-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="c30ed-107">DSC bestaat met:</span><span class="sxs-lookup"><span data-stu-id="c30ed-107">DSC exists to:</span></span>

- <span data-ttu-id="c30ed-108">Verklein de complexiteit van het uitvoeren van scripts in Windows</span><span class="sxs-lookup"><span data-stu-id="c30ed-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="c30ed-109">De snelheid van herhaling verhogen</span><span class="sxs-lookup"><span data-stu-id="c30ed-109">Increase the speed of iteration</span></span>

<span data-ttu-id="c30ed-110">Het concept van 'continue implementatie' steeds belangrijker.</span><span class="sxs-lookup"><span data-stu-id="c30ed-110">The concept of "continuous deployment" is becoming more important.</span></span>
<span data-ttu-id="c30ed-111">Doorlopende implementatie betekent dat de mogelijkheid om te implementeren, mogelijk meerdere keren per dag.</span><span class="sxs-lookup"><span data-stu-id="c30ed-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span>
<span data-ttu-id="c30ed-112">Het doel van deze implementaties zijn niet iets te repareren, maar naar iets snel gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="c30ed-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span>
<span data-ttu-id="c30ed-113">Met het ophalen van nieuwe functies via ontwikkeling in werking zo soepel en betrouwbaar mogelijk, moet u naar tijdwaarde maken van nieuwe bedrijfslogica verminderen.</span><span class="sxs-lookup"><span data-stu-id="c30ed-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="c30ed-114">De overgang naar cloud computing impliceert een implementatieoplossing die gebruikmaakt van een model 'declaratieve' sjabloon, waarbij een end-status-omgeving is gedeclareerd als tekst en gepubliceerd naar een implementatie-engine.</span><span class="sxs-lookup"><span data-stu-id="c30ed-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span>
<span data-ttu-id="c30ed-115">Deze techniek implementatie kunt u snel wijzigen, klikt u op grote schaal, met herstelmogelijkheden tegen bedreiging van de fout omdat op elk gewenst moment de implementatie kan worden consistent herhaald om bescherming te bieden een end-status.</span><span class="sxs-lookup"><span data-stu-id="c30ed-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span>
<span data-ttu-id="c30ed-116">Het maken van de hulpprogramma's en services die ondersteuning bieden voor deze stijl van bewerkingen door middel van automatisering is een reactie op deze wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="c30ed-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="c30ed-117">DSC is een platform waarmee declaratieve en idempotent (herhaalbare)-implementatie, configuratie en overeenstemming.</span><span class="sxs-lookup"><span data-stu-id="c30ed-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span>
<span data-ttu-id="c30ed-118">De DSC-platform kunt u om ervoor te zorgen dat de onderdelen van uw datacenter de juiste configuratie, die voorkomt fouten en kostbaar implementatiestoringen voorkomt.</span><span class="sxs-lookup"><span data-stu-id="c30ed-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span>
<span data-ttu-id="c30ed-119">DSC ingeschakeld door het DSC-configuraties te behandelen als onderdeel van de toepassingscode, continue implementatie.</span><span class="sxs-lookup"><span data-stu-id="c30ed-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span>
<span data-ttu-id="c30ed-120">De DSC-configuratie moet worden bijgewerkt als onderdeel van de toepassing, ervoor zorgen dat de kennis die nodig zijn voor het implementeren van de toepassing altijd actueel en klaar om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c30ed-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="c30ed-121">'Ik heb PowerShell, waarom ik Desired State Configuration moet?'</span><span class="sxs-lookup"><span data-stu-id="c30ed-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="c30ed-122">DSC-configuraties afzonderlijk doel of 'wat ik wil', uitvoeren of "hoe ik wil dit doen."</span><span class="sxs-lookup"><span data-stu-id="c30ed-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span>
<span data-ttu-id="c30ed-123">Dit betekent dat de logica van de uitvoering van deel uitmaakt van de resources.</span><span class="sxs-lookup"><span data-stu-id="c30ed-123">This means the logic of execution is contained within the resources.</span></span>
<span data-ttu-id="c30ed-124">Gebruikers hoeven niet te weten hoe u kunt implementeren of implementeren van een functie wanneer een DSC-resource voor deze functie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="c30ed-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span>
<span data-ttu-id="c30ed-125">Hierdoor kan de gebruiker zich richten op de structuur van hun implementatie.</span><span class="sxs-lookup"><span data-stu-id="c30ed-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="c30ed-126">Als u bijvoorbeeld er PowerShell-scripts als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="c30ed-126">As an example, PowerShell scripts should look like this:</span></span>
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
<span data-ttu-id="c30ed-127">Dit script is eenvoudig, begrijpen en snel.</span><span class="sxs-lookup"><span data-stu-id="c30ed-127">This script is simple, comprehensible, and straightforward.</span></span>
<span data-ttu-id="c30ed-128">Als u het script in productie te stellen probeert, kunt u wordt echter voor uitvoeren in verschillende problemen.</span><span class="sxs-lookup"><span data-stu-id="c30ed-128">However, if you try putting that script into production, you will run into several issues.</span></span>
<span data-ttu-id="c30ed-129">Wat gebeurt er als die script tweemaal in een rij wordt uitgevoerd?</span><span class="sxs-lookup"><span data-stu-id="c30ed-129">What happens if that script is run twice in a row?</span></span>
<span data-ttu-id="c30ed-130">Wat gebeurt er als Bob had eerder volledige toegang tot de share?</span><span class="sxs-lookup"><span data-stu-id="c30ed-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="c30ed-131">Om te compenseren voor deze problemen, een 'echte' versie van het script ziet er dichter bij ongeveer als volgt:</span><span class="sxs-lookup"><span data-stu-id="c30ed-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>
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

<span data-ttu-id="c30ed-132">Dit script is complexere met veel van de logica en foutafhandeling.</span><span class="sxs-lookup"><span data-stu-id="c30ed-132">This script is more complex, with plenty of logic and error handling.</span></span>
<span data-ttu-id="c30ed-133">Het script is complexer omdat u niet meer worden weergegeven naar wens gereed is, maar *te werk*.</span><span class="sxs-lookup"><span data-stu-id="c30ed-133">The script is more complex because you are no longer stating what you want done, but *how to do it*.</span></span>

<span data-ttu-id="c30ed-134">DSC kunt u aannemen dat u de gewenste gereed en de onderliggende logica beschouwing verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c30ed-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

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

<span data-ttu-id="c30ed-135">Dit script is foutloos geformatteerd en eenvoudig te lezen.</span><span class="sxs-lookup"><span data-stu-id="c30ed-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="c30ed-136">De logische paden en foutafhandeling nog steeds aanwezig zijn in de [resource](resources.md) implementatie, maar onzichtbaar voor de auteur van het script.</span><span class="sxs-lookup"><span data-stu-id="c30ed-136">The logic paths and error handling are still present in the [resource](resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="c30ed-137">Het scheiden van de omgeving van structuur</span><span class="sxs-lookup"><span data-stu-id="c30ed-137">Separating Environment from Structure</span></span>

<span data-ttu-id="c30ed-138">Een algemene patroon in DevOps is om meerdere omgevingen voor implementatie.</span><span class="sxs-lookup"><span data-stu-id="c30ed-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span>
<span data-ttu-id="c30ed-139">Bijvoorbeeld, kunnen er een 'dev'-omgeving gebruikt voor het snel prototype nieuwe code.</span><span class="sxs-lookup"><span data-stu-id="c30ed-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span>
<span data-ttu-id="c30ed-140">De code uit de omgeving 'dev' gaat in een omgeving 'test' anderen controleren waar de nieuwe functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="c30ed-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span>
<span data-ttu-id="c30ed-141">Ten slotte wordt de code 'prod' of de productieomgeving live site.</span><span class="sxs-lookup"><span data-stu-id="c30ed-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="c30ed-142">DSC-configuraties mogelijk deze dev-test-prod-pipeline met behulp van [configuratiegegevens](configData.md).</span><span class="sxs-lookup"><span data-stu-id="c30ed-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](configData.md).</span></span>
<span data-ttu-id="c30ed-143">Hiermee isoleert verder het verschil tussen de structuur van de configuratie van de knooppunten die worden beheerd.</span><span class="sxs-lookup"><span data-stu-id="c30ed-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span>
<span data-ttu-id="c30ed-144">U kunt bijvoorbeeld een configuratie die een SQL-server, een IIS-server en een server voor de middelste laag vereist definiëren.</span><span class="sxs-lookup"><span data-stu-id="c30ed-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span>
<span data-ttu-id="c30ed-145">Ongeacht welke knooppunten de verschillende onderdelen van deze configuratie wordt weergegeven, wordt deze drie elementen altijd aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="c30ed-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span>
<span data-ttu-id="c30ed-146">U kunt configuratiegegevens wijst alle drie elementen naar dezelfde machine in een omgeving dev afzonderlijke uit de drie elementen met drie verschillende machines voor een testomgeving en tot slot naar uw productieservers voor de prod-omgeving.</span><span class="sxs-lookup"><span data-stu-id="c30ed-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span>
<span data-ttu-id="c30ed-147">Als u wilt implementeren in verschillende omgevingen, u kunt aanroepen **Start DscConfiguration** met de juiste configuratie van de gegevens voor de omgeving die u wilt targeten.</span><span class="sxs-lookup"><span data-stu-id="c30ed-147">To deploy to the different environments, you can invoke **Start-DscConfiguration** with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="c30ed-148">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c30ed-148">See Also</span></span>

[<span data-ttu-id="c30ed-149">Configuraties</span><span class="sxs-lookup"><span data-stu-id="c30ed-149">Configurations</span></span>](configurations.md)

[<span data-ttu-id="c30ed-150">Configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="c30ed-150">Configuration Data</span></span>](configData.md)

[<span data-ttu-id="c30ed-151">Resources</span><span class="sxs-lookup"><span data-stu-id="c30ed-151">Resources</span></span>](resources.md)
