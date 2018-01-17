---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: MSFT_DSCLocalConfigurationManager klasse
ms.openlocfilehash: b2d2ce000988f2c10ab04c4ba5a4650bd3c75ec7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="37635-103">MSFT_DSCLocalConfigurationManager klasse</span><span class="sxs-lookup"><span data-stu-id="37635-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="37635-104">De lokale Configuration Manager (LCM) die bepaalt de status van de configuratiebestanden en Configuration Agent gebruikt om de configuraties te passen.</span><span class="sxs-lookup"><span data-stu-id="37635-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="37635-105">De volgende syntaxis van Managed Object Format (MOF) code is vereenvoudigd en bevat alle overgenomen eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="37635-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="37635-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="37635-106">Syntax</span></span>
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="37635-107">Leden</span><span class="sxs-lookup"><span data-stu-id="37635-107">Members</span></span>
-------

<span data-ttu-id="37635-108">De **MSFT_DSCLocalConfigurationManager** klasse heeft de volgende leden:</span><span class="sxs-lookup"><span data-stu-id="37635-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

-   <span data-ttu-id="37635-109">[Methoden] []</span><span class="sxs-lookup"><span data-stu-id="37635-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="37635-110">Methoden</span><span class="sxs-lookup"><span data-stu-id="37635-110">Methods</span></span>

<span data-ttu-id="37635-111">De **MSFT_DSCLocalConfigurationManager** klasse heeft deze methoden.</span><span class="sxs-lookup"><span data-stu-id="37635-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="37635-112">Methode</span><span class="sxs-lookup"><span data-stu-id="37635-112">Method</span></span> |<span data-ttu-id="37635-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="37635-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="37635-114">ApplyConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-114">ApplyConfiguration</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="37635-115">Gebruik de Configuration-Agent voor de configuratie die in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="37635-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>| 
| [<span data-ttu-id="37635-116">DisableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-116">DisableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="37635-117">Hiermee schakelt u foutopsporing van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="37635-117">Disables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="37635-118">EnableDebugConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-118">EnableDebugConfiguration</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="37635-119">Hiermee schakelt u foutopsporing van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="37635-119">Enables DSC resource debugging.</span></span>| 
| [<span data-ttu-id="37635-120">GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-120">GetConfiguration</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="37635-121">Verzendt het configuratie-document naar het beheerde knooppunt en maakt gebruik van de **ophalen** methode van de configuratie-Agent de configuratie toepassen.</span><span class="sxs-lookup"><span data-stu-id="37635-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="37635-122">GetConfigurationResultOutput</span><span class="sxs-lookup"><span data-stu-id="37635-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="37635-123">Hiermee wordt de uitvoer van de Configuration-Agent met betrekking tot een specifieke taak opgehaald.</span><span class="sxs-lookup"><span data-stu-id="37635-123">Gets the Configuration Agent output relating to a specific job.</span></span>| 
| [<span data-ttu-id="37635-124">GetConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="37635-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="37635-125">Haal de geschiedenis van de configuratie-status.</span><span class="sxs-lookup"><span data-stu-id="37635-125">Get the configuration status history.</span></span>| 
| [<span data-ttu-id="37635-126">GetMetaConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="37635-127">Hiermee haalt u de LCM-instellingen die worden gebruikt voor het beheren van configuratie-Agent.</span><span class="sxs-lookup"><span data-stu-id="37635-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>| 
| [<span data-ttu-id="37635-128">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="37635-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="37635-129">Start de consistentiecontrole.</span><span class="sxs-lookup"><span data-stu-id="37635-129">Starts the consistency check.</span></span>| 
| [<span data-ttu-id="37635-130">RemoveConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="37635-131">Hiermee verwijdert u de configuratiebestanden.</span><span class="sxs-lookup"><span data-stu-id="37635-131">Removes the configuration files.</span></span>| 
| [<span data-ttu-id="37635-132">ResourceGet</span><span class="sxs-lookup"><span data-stu-id="37635-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="37635-133">Rechtstreeks roept de **ophalen** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="37635-133">Directly calls the **Get** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="37635-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="37635-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="37635-135">Rechtstreeks roept de **ingesteld** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="37635-135">Directly calls the **Set** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="37635-136">ResourceTest</span><span class="sxs-lookup"><span data-stu-id="37635-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="37635-137">Rechtstreeks roept de **Test** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="37635-137">Directly calls the **Test** method of a DSC resource.</span></span>| 
| [<span data-ttu-id="37635-138">RollBack</span><span class="sxs-lookup"><span data-stu-id="37635-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="37635-139">Hiermee wordt de terug naar een eerdere configuratie.</span><span class="sxs-lookup"><span data-stu-id="37635-139">Rolls back to a previous configuration.</span></span>| 
| [<span data-ttu-id="37635-140">SendConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="37635-141">Het configuratiebestand voor verzendt naar het beheerde knooppunt en wordt deze opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="37635-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>| 
| [<span data-ttu-id="37635-142">SendConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="37635-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="37635-143">Het configuratiebestand voor het beheerde knooppunt verzendt en gebruik van de configuratie-Agent voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="37635-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>| 
| [<span data-ttu-id="37635-144">SendConfigurationApplyAsync</span><span class="sxs-lookup"><span data-stu-id="37635-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="37635-145">Het configuratie-document verzenden naar het beheerde knooppunt en start met behulp van de configuratie-Agent de configuratie toepassen.</span><span class="sxs-lookup"><span data-stu-id="37635-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="37635-146">Gebruik GetConfigurationResultOutput resultaat uitvoer ophalen.</span><span class="sxs-lookup"><span data-stu-id="37635-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>| 
| [<span data-ttu-id="37635-147">SendMetaConfigurationApply</span><span class="sxs-lookup"><span data-stu-id="37635-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="37635-148">Hiermee stelt u de LCM-instellingen die worden gebruikt voor het beheren van de configuratie-Agent.</span><span class="sxs-lookup"><span data-stu-id="37635-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>| 
| [<span data-ttu-id="37635-149">StopConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="37635-150">Hiermee stopt de configuratie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="37635-150">Stops the configuration that is in progress.</span></span>| 
| [<span data-ttu-id="37635-151">TestConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="37635-152">Het configuratiebestand voor het beheerde knooppunt verzendt en controleert of de huidige configuratie op basis van het document.</span><span class="sxs-lookup"><span data-stu-id="37635-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>| 



 

## <a name="requirements"></a><span data-ttu-id="37635-153">Vereisten</span><span class="sxs-lookup"><span data-stu-id="37635-153">Requirements</span></span>
------------
><span data-ttu-id="37635-154">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="37635-154">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="37635-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="37635-155">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>



 

 



