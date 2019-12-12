---
ms.date: 10/16/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuraties doorvoeren
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941731"
---
# <a name="enacting-configurations"></a><span data-ttu-id="2139d-103">Configuraties doorvoeren</span><span class="sxs-lookup"><span data-stu-id="2139d-103">Enacting configurations</span></span>

><span data-ttu-id="2139d-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="2139d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2139d-105">Er zijn twee manieren om de configuraties van desired state Configuration (DSC) van Power shell te nemen: push-modus en pull-modus.</span><span class="sxs-lookup"><span data-stu-id="2139d-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="2139d-106">Push-modus</span><span class="sxs-lookup"><span data-stu-id="2139d-106">Push mode</span></span>

<span data-ttu-id="2139d-107">![Push modus](../images/pushModel.png "De werking van de push modus")</span><span class="sxs-lookup"><span data-stu-id="2139d-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="2139d-108">De push modus verwijst naar een gebruiker die actief een configuratie toepast op een doel knooppunt door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="2139d-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="2139d-109">Nadat u een configuratie hebt gemaakt en gecompileerd, kunt u deze in de push-modus Toep assen door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen en de para meter-Path van de cmdlet in te stellen op het pad waar de configuratie-MOF zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="2139d-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="2139d-110">Als de configuratie-MOF zich bijvoorbeeld bevindt op `C:\DSC\Configurations\localhost.mof`, past u deze toe op de lokale computer met de volgende opdracht: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="2139d-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="2139d-111">__Opmerking__: standaard voert DSC een configuratie uit als achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="2139d-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="2139d-112">Als u de configuratie interactief wilt uitvoeren, roept u [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan met de __-wait__ -para meter.</span><span class="sxs-lookup"><span data-stu-id="2139d-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="2139d-113">Pull-modus</span><span class="sxs-lookup"><span data-stu-id="2139d-113">Pull mode</span></span>

<span data-ttu-id="2139d-114">![Pull-modus](../images/pullModel.png "Hoe werkt de pull-modus?")</span><span class="sxs-lookup"><span data-stu-id="2139d-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="2139d-115">Pull-clients worden in de pull-modus geconfigureerd om de gewenste status configuraties te verkrijgen van een externe pull-service.</span><span class="sxs-lookup"><span data-stu-id="2139d-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="2139d-116">Op dezelfde manier is de pull-service ingesteld voor het hosten van de DSC-service en is deze ingericht met de configuraties en resources die vereist zijn voor de pull-clients.</span><span class="sxs-lookup"><span data-stu-id="2139d-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="2139d-117">Elk van de pull-clients heeft een geplande gebeurtenis die een periodieke controle op de naleving van de configuratie van het knoop punt uitvoert.</span><span class="sxs-lookup"><span data-stu-id="2139d-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="2139d-118">Wanneer de gebeurtenis de eerste keer wordt geactiveerd, maakt de lokale Configuration Manager (LCM) op de pull-client een aanvraag voor de pull-service om de configuratie op te halen die is opgegeven in de LCM.</span><span class="sxs-lookup"><span data-stu-id="2139d-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="2139d-119">Als deze configuratie bestaat in de pull-service en de initiële validatie controles worden door gegeven, wordt de configuratie gedownload naar de pull-client, waar deze wordt uitgevoerd door de LCM.</span><span class="sxs-lookup"><span data-stu-id="2139d-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="2139d-120">De LCM controleert of de client in overeenstemming is met de configuratie met regel matige tussen pozen die is opgegeven door de eigenschap **ConfigurationModeFrequencyMins** van de LCM.</span><span class="sxs-lookup"><span data-stu-id="2139d-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="2139d-121">De LCM controleert met regel matige tussen pozen die zijn opgegeven door de eigenschap **RefreshModeFrequency** van de LCM op bijgewerkte configuraties van de pull-service.</span><span class="sxs-lookup"><span data-stu-id="2139d-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="2139d-122">Zie [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)(Engelstalig) voor meer informatie over het configureren van de LCM.</span><span class="sxs-lookup"><span data-stu-id="2139d-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="2139d-123">De aanbevolen oplossing voor het hosten van een pull-service is de DSC-Cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="2139d-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="2139d-124">Dit is een gehoste oplossing die grafische beheer, rapportage en gecentraliseerd beheer biedt.</span><span class="sxs-lookup"><span data-stu-id="2139d-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="2139d-125">Zie [een DSC Web-pull-server instellen](pullServer.md)voor meer informatie over het instellen van een pull-service op Windows Server.</span><span class="sxs-lookup"><span data-stu-id="2139d-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="2139d-126">Meer informatie over deze implementatie heeft beperkte functies. hiervoor is wel een ' zelf-' zelf-integratie vereist.</span><span class="sxs-lookup"><span data-stu-id="2139d-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="2139d-127">In de volgende onderwerpen worden pull-Services en-clients beschreven:</span><span class="sxs-lookup"><span data-stu-id="2139d-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="2139d-128">Overzicht van Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="2139d-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="2139d-129">Een SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="2139d-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="2139d-130">Een pull-client configureren</span><span class="sxs-lookup"><span data-stu-id="2139d-130">Configuring a pull client</span></span>](pullClientConfigID.md)
