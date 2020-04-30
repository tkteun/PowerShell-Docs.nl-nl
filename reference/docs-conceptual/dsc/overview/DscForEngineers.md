---
ms.date: 10/13/2017
keywords: DSC, Power shell, configuratie, installatie
title: Overzicht Desired State Configuration voor technici
ms.openlocfilehash: dbed274d5333c216970247b88d2a0956025e969d
ms.sourcegitcommit: a5e945e0889d0635b7af767d80d6a13bc5526269
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82584519"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="0f399-103">Overzicht Desired State Configuration voor technici</span><span class="sxs-lookup"><span data-stu-id="0f399-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="0f399-104">Dit document is bedoeld voor ontwikkel aars-en IT-teams om inzicht te krijgen in de voor delen van Power shell desired state Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="0f399-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="0f399-105">Voor een weer gave op een hoger niveau van de waarde DSC vindt [u een overzicht van de desired state Configuration voor besluit vormers](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="0f399-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="0f399-106">Voor delen van desired state Configuration</span><span class="sxs-lookup"><span data-stu-id="0f399-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="0f399-107">DSC bestaat uit:</span><span class="sxs-lookup"><span data-stu-id="0f399-107">DSC exists to:</span></span>

- <span data-ttu-id="0f399-108">De complexiteit van het uitvoeren van scripts in Windows verminderen</span><span class="sxs-lookup"><span data-stu-id="0f399-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="0f399-109">De snelheid van herhaling verhogen</span><span class="sxs-lookup"><span data-stu-id="0f399-109">Increase the speed of iteration</span></span>

<span data-ttu-id="0f399-110">Het concept van ' continue implementatie ' wordt belang rijker.</span><span class="sxs-lookup"><span data-stu-id="0f399-110">The concept of "continuous deployment" is becoming more important.</span></span> <span data-ttu-id="0f399-111">Continue implementatie houdt in dat u regel matig, mogelijk vaak per dag, kunt implementeren.</span><span class="sxs-lookup"><span data-stu-id="0f399-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span> <span data-ttu-id="0f399-112">Het doel van deze implementaties is om iets niet op te lossen, maar om snel iets te doen.</span><span class="sxs-lookup"><span data-stu-id="0f399-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span> <span data-ttu-id="0f399-113">Door nieuwe functies zo soepel en betrouwbaar mogelijk te maken, verkleint u de tijd tot waard van nieuwe bedrijfs logica.</span><span class="sxs-lookup"><span data-stu-id="0f399-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="0f399-114">De overstap naar Cloud Computing impliceert een implementatie oplossing die gebruikmaakt van een ' declaratief ' sjabloon model, waarbij een eind status omgeving wordt gedeclareerd als tekst en wordt gepubliceerd naar een implementatie-engine.</span><span class="sxs-lookup"><span data-stu-id="0f399-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span> <span data-ttu-id="0f399-115">Met deze implementatie techniek kunt u op schaal snel wijzigingen door lopen, waarbij u op elk gewenst moment de implementatie consistent kunt herhalen om een eind status te garanderen.</span><span class="sxs-lookup"><span data-stu-id="0f399-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span> <span data-ttu-id="0f399-116">Het maken van hulpprogram ma's en services die ondersteuning bieden voor deze stijl van bewerkingen via Automation is een antwoord op deze wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="0f399-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="0f399-117">DSC is een platform dat declaratieve en idempotent (Herhaal bare) implementatie, configuratie en conformiteit biedt.</span><span class="sxs-lookup"><span data-stu-id="0f399-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span> <span data-ttu-id="0f399-118">Met het DSC-platform kunt u ervoor zorgen dat de onderdelen van uw Data Center de juiste configuratie hebben, waardoor fouten worden voor komen en dat er geen kosten in rekening worden getreden.</span><span class="sxs-lookup"><span data-stu-id="0f399-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span> <span data-ttu-id="0f399-119">Door DSC-configuraties te behandelen als onderdeel van de toepassings code, maakt DSC gebruik van continue implementatie.</span><span class="sxs-lookup"><span data-stu-id="0f399-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span> <span data-ttu-id="0f399-120">De DSC-configuratie moet worden bijgewerkt als onderdeel van de toepassing, zodat de kennis die nodig is om de toepassing te implementeren altijd up-to-date is en klaar is om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0f399-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="0f399-121">"Ik heb Power shell, waarom heb ik de gewenste status configuratie nodig?"</span><span class="sxs-lookup"><span data-stu-id="0f399-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="0f399-122">DSC-configuraties van afzonderlijke intentie, of ' wat ik wil doen ', van uitvoering of ' Hoe wil ik dit doen? '</span><span class="sxs-lookup"><span data-stu-id="0f399-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span> <span data-ttu-id="0f399-123">Dit betekent dat de logica van de uitvoering in de resources is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="0f399-123">This means the logic of execution is contained within the resources.</span></span> <span data-ttu-id="0f399-124">Gebruikers hoeven niet te weten hoe ze een functie moeten implementeren of implementeren wanneer een DSC-resource voor die functie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="0f399-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span> <span data-ttu-id="0f399-125">Op deze manier kan de gebruiker zich richten op de structuur van de implementatie.</span><span class="sxs-lookup"><span data-stu-id="0f399-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="0f399-126">Power shell-scripts zouden er als voor beeld als volgt moeten uitzien:</span><span class="sxs-lookup"><span data-stu-id="0f399-126">As an example, PowerShell scripts should look like this:</span></span>

```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```

<span data-ttu-id="0f399-127">Dit script is eenvoudig, begrijpelijk en eenvoudig.</span><span class="sxs-lookup"><span data-stu-id="0f399-127">This script is simple, comprehensible, and straightforward.</span></span> <span data-ttu-id="0f399-128">Als u het script echter probeert te plaatsen in productie, worden er meerdere problemen uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0f399-128">However, if you try putting that script into production, you will run into several issues.</span></span> <span data-ttu-id="0f399-129">Wat gebeurt er als dat script twee keer in een rij wordt uitgevoerd?</span><span class="sxs-lookup"><span data-stu-id="0f399-129">What happens if that script is run twice in a row?</span></span> <span data-ttu-id="0f399-130">Wat gebeurt er als Bob eerder volledige toegang had tot de share?</span><span class="sxs-lookup"><span data-stu-id="0f399-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="0f399-131">Om deze problemen te compenseren, ziet een ' Real '-versie van het script er dichter als:</span><span class="sxs-lookup"><span data-stu-id="0f399-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>

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
    New-SmbShare @PSBoundParameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($PSBoundParameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="0f399-132">Dit script is complexere, met veel logica en fout afhandeling.</span><span class="sxs-lookup"><span data-stu-id="0f399-132">This script is more complex, with plenty of logic and error handling.</span></span> <span data-ttu-id="0f399-133">Het script is ingewik kelder omdat u niet meer weet wat u wilt doen, maar hoe u _Dit doet_.</span><span class="sxs-lookup"><span data-stu-id="0f399-133">The script is more complex because you are no longer stating what you want done, but _how to do it_.</span></span>

<span data-ttu-id="0f399-134">Met DSC kunt u zeggen wat u wilt doen en de onderliggende logica wordt abstract gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0f399-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

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

<span data-ttu-id="0f399-135">Dit script is duidelijk opgemaakt en eenvoudig te lezen.</span><span class="sxs-lookup"><span data-stu-id="0f399-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="0f399-136">De logische paden en fout afhandeling zijn nog steeds aanwezig in de [resource](../resources/resources.md) -implementatie, maar zijn niet zichtbaar voor de auteur van het script.</span><span class="sxs-lookup"><span data-stu-id="0f399-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="0f399-137">Omgeving scheiden van structuur</span><span class="sxs-lookup"><span data-stu-id="0f399-137">Separating Environment from Structure</span></span>

<span data-ttu-id="0f399-138">Een gemeen schappelijk patroon in DevOps is om meerdere omgevingen te hebben voor de implementatie.</span><span class="sxs-lookup"><span data-stu-id="0f399-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span> <span data-ttu-id="0f399-139">Er kan bijvoorbeeld een ' dev ' omgeving worden gebruikt om snel nieuwe code te prototypen.</span><span class="sxs-lookup"><span data-stu-id="0f399-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span> <span data-ttu-id="0f399-140">De code van de omgeving ' dev ' gaat in een test omgeving, waar andere personen de nieuwe functionaliteit verifiëren.</span><span class="sxs-lookup"><span data-stu-id="0f399-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span> <span data-ttu-id="0f399-141">Ten slotte gaat de code naar ' Prod ' of de productie omgeving van de live site.</span><span class="sxs-lookup"><span data-stu-id="0f399-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="0f399-142">DSC-configuraties voldoen aan deze dev-test-Prod-pijp lijn door het gebruik van [configuratie gegevens](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="0f399-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="0f399-143">Hiermee wordt het verschil tussen de structuur van de configuratie van de knoop punten die worden beheerd, verder abstract.</span><span class="sxs-lookup"><span data-stu-id="0f399-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span> <span data-ttu-id="0f399-144">U kunt bijvoorbeeld een configuratie definiëren waarvoor een SQL-Server, een IIS-server en een server voor de middelste laag zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="0f399-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span> <span data-ttu-id="0f399-145">Ongeacht welke knoop punten de verschillende onderdelen van deze configuratie ontvangen, zullen deze drie elementen altijd aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="0f399-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span> <span data-ttu-id="0f399-146">U kunt configuratie gegevens gebruiken om alle drie de elementen op dezelfde machine te laten wijzen voor een ontwikkel omgeving, de drie elementen van elkaar te scheiden op drie verschillende machines voor een test omgeving, en ten slotte naar alle productie servers voor de Prod-omgeving.</span><span class="sxs-lookup"><span data-stu-id="0f399-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span> <span data-ttu-id="0f399-147">Als u wilt implementeren in de verschillende omgevingen, kunt `Start-DscConfiguration` u aanroepen met de juiste configuratie gegevens voor de omgeving die u wilt instellen.</span><span class="sxs-lookup"><span data-stu-id="0f399-147">To deploy to the different environments, you can invoke `Start-DscConfiguration` with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f399-148">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0f399-148">See Also</span></span>

[<span data-ttu-id="0f399-149">Configuraties</span><span class="sxs-lookup"><span data-stu-id="0f399-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="0f399-150">Configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="0f399-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="0f399-151">Resources</span><span class="sxs-lookup"><span data-stu-id="0f399-151">Resources</span></span>](../resources/resources.md)
