---
ms.date: 10/16/2017
keywords: DSC, powershell, configuratie en installatie
title: Configuraties doorvoeren
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079936"
---
# <a name="enacting-configurations"></a><span data-ttu-id="df985-103">Configuraties doorvoeren</span><span class="sxs-lookup"><span data-stu-id="df985-103">Enacting configurations</span></span>

><span data-ttu-id="df985-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="df985-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="df985-105">Er zijn twee manieren op te nemen van PowerShell Desired State Configuration (DSC) configuraties: push- en pull-modus.</span><span class="sxs-lookup"><span data-stu-id="df985-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="df985-106">Push-modus</span><span class="sxs-lookup"><span data-stu-id="df985-106">Push mode</span></span>

<span data-ttu-id="df985-107">![Push-modus](../images/pushModel.png "hoe push-modus werkt")</span><span class="sxs-lookup"><span data-stu-id="df985-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="df985-108">Push-modus verwijst naar het toepassen van een configuratie actief op een doelknooppunt door het aanroepen van een gebruiker de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df985-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="df985-109">Na het maken en compileren van een configuratie, u kunt nemen deze in de pushmodus gebruikt door het aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, instellen van de parameter - Path van de cmdlet naar het pad waar de configuratie van de MOF zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="df985-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="df985-110">Bijvoorbeeld, als de configuratie van de MOF bevindt zich in `C:\DSC\Configurations\localhost.mof`, zou u deze toepassen op de lokale computer met de volgende opdracht: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="df985-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="df985-111">__Houd er rekening mee__: DSC wordt standaard uitgevoerd van een configuratie als achtergrondtaak.</span><span class="sxs-lookup"><span data-stu-id="df985-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="df985-112">Als u wilt de configuratie van de interactief uitvoeren, aanroepen de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) met de __-wacht__ parameter.</span><span class="sxs-lookup"><span data-stu-id="df985-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="df985-113">Pull-modus</span><span class="sxs-lookup"><span data-stu-id="df985-113">Pull mode</span></span>

<span data-ttu-id="df985-114">![Pull-modus](../images/pullModel.png "hoe pull-modus werkt")</span><span class="sxs-lookup"><span data-stu-id="df985-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="df985-115">In de pull-modus, pull-clients geconfigureerd voor de configuraties van de gewenste status van een externe pull-service.</span><span class="sxs-lookup"><span data-stu-id="df985-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="df985-116">Evenzo, de pull-service is ingesteld op de host de DSC-service en is ingericht met de configuraties en resources die door de pull-clients vereist zijn.</span><span class="sxs-lookup"><span data-stu-id="df985-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="df985-117">Elk van de pull-clients heeft een geplande gebeurtenis waarmee een controle op periodieke naleving van de configuratie van het knooppunt worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="df985-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="df985-118">Wanneer de gebeurtenis wordt de eerste keer geactiveerd, maakt de lokale Configuration Manager (LCM) op de pull-client een aanvraag naar de pull-service om op te halen van de configuratie die is opgegeven in de LCM.</span><span class="sxs-lookup"><span data-stu-id="df985-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="df985-119">Als deze configuratie op de pull-service bestaat, en controleert op de eerste validatie wordt doorgegeven, wordt de configuratie gedownload naar de pull-client waarop deze wordt vervolgens uitgevoerd door de LCM.</span><span class="sxs-lookup"><span data-stu-id="df985-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="df985-120">De LCM wordt gecontroleerd of de client in overeenstemming met de configuratie met regelmatige intervallen die zijn opgegeven door de **ConfigurationModeFrequencyMins** eigenschap van de LCM.</span><span class="sxs-lookup"><span data-stu-id="df985-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="df985-121">De LCM gecontroleerd op bijgewerkte configuraties op de pull-service met regelmatige intervallen die zijn opgegeven door de **RefreshModeFrequency** eigenschap van de LCM.</span><span class="sxs-lookup"><span data-stu-id="df985-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="df985-122">Zie voor meer informatie over het configureren van de LCM [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="df985-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="df985-123">De aanbevolen oplossing voor het hosten van een Pull-Service, is de DSC-cloudservice, [Azure Automation](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="df985-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="df985-124">Dit wordt gehost oplossing biedt een grafische beheerprogramma, rapporten en gecentraliseerd beheer.</span><span class="sxs-lookup"><span data-stu-id="df985-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="df985-125">Zie voor meer informatie over het instellen van een Pull-Service op Windows Server [instellen van een DSC-pull-endwebserver](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="df985-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="df985-126">Begrijp echter dat deze implementatie heeft beperkte functionaliteit en sommige 'zelf'-integratie is vereist.</span><span class="sxs-lookup"><span data-stu-id="df985-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="df985-127">De volgende onderwerpen wordt uitgelegd voor pull-service en -clients:</span><span class="sxs-lookup"><span data-stu-id="df985-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="df985-128">Overzicht van Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="df985-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="df985-129">Instellen van een SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="df985-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="df985-130">Een pull-client configureren</span><span class="sxs-lookup"><span data-stu-id="df985-130">Configuring a pull client</span></span>](pullClientConfigID.md)
