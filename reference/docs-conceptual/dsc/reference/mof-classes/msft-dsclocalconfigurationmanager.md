---
ms.date: 07/14/2020
ms.topic: reference
title: MSFT_DSCLocalConfigurationManager-klasse
description: MSFT_DSCLocalConfigurationManager-klasse
ms.openlocfilehash: 31112c7d15884699171ec732ac20b6960b0858a9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644815"
---
# <a name="msft_dsclocalconfigurationmanager-class"></a><span data-ttu-id="a43e8-103">MSFT_DSCLocalConfigurationManager-klasse</span><span class="sxs-lookup"><span data-stu-id="a43e8-103">MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a43e8-104">De lokale Configuration Manager (LCM) die de statussen van configuratie bestanden beheert en configuratie-agent gebruikt om de configuraties toe te passen.</span><span class="sxs-lookup"><span data-stu-id="a43e8-104">The Local Configuration Manager (LCM) that controls the states of configuration files and uses Configuration Agent to apply the configurations.</span></span>

<span data-ttu-id="a43e8-105">De volgende syntaxis is vereenvoudigd via de code van Managed Object Format (MOF) en bevat alle overgenomen eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="a43e8-105">The following syntax is simplified from Managed Object Format (MOF) code and includes all of the inherited properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="a43e8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a43e8-106">Syntax</span></span>

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a><span data-ttu-id="a43e8-107">Leden</span><span class="sxs-lookup"><span data-stu-id="a43e8-107">Members</span></span>

<span data-ttu-id="a43e8-108">De klasse **MSFT_DSCLocalConfigurationManager** heeft de volgende leden:</span><span class="sxs-lookup"><span data-stu-id="a43e8-108">The **MSFT_DSCLocalConfigurationManager** class has the following members:</span></span>

- <span data-ttu-id="a43e8-109">Technieken []</span><span class="sxs-lookup"><span data-stu-id="a43e8-109">[Methods][]</span></span>

### <a name="methods"></a><span data-ttu-id="a43e8-110">Methoden</span><span class="sxs-lookup"><span data-stu-id="a43e8-110">Methods</span></span>

<span data-ttu-id="a43e8-111">De klasse **MSFT_DSCLocalConfigurationManager** heeft deze methoden.</span><span class="sxs-lookup"><span data-stu-id="a43e8-111">The **MSFT_DSCLocalConfigurationManager** class has these methods.</span></span>

|<span data-ttu-id="a43e8-112">Methoden</span><span class="sxs-lookup"><span data-stu-id="a43e8-112">Methods</span></span> |<span data-ttu-id="a43e8-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a43e8-113">Description</span></span> |
|:--- |:---|
| [<span data-ttu-id="a43e8-114">ApplyConfiguration (Booleaans)</span><span class="sxs-lookup"><span data-stu-id="a43e8-114">ApplyConfiguration(boolean)</span></span>](msft-dsclocalconfigurationmanager-applyconfiguration.md)| <span data-ttu-id="a43e8-115">Maakt gebruik van de configuratie agent om de in behandeling zijnde configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="a43e8-115">Uses the Configuration Agent to apply the configuration that is pending.</span></span>|
| [<span data-ttu-id="a43e8-116">De disabledebugconfiguration ()</span><span class="sxs-lookup"><span data-stu-id="a43e8-116">DisableDebugConfiguration()</span></span>](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| <span data-ttu-id="a43e8-117">Hiermee schakelt u fout opsporing voor DSC-resources uit.</span><span class="sxs-lookup"><span data-stu-id="a43e8-117">Disables DSC resource debugging.</span></span>|
| [<span data-ttu-id="a43e8-118">De enabledebugconfiguration (Booleaans)</span><span class="sxs-lookup"><span data-stu-id="a43e8-118">EnableDebugConfiguration(boolean)</span></span>](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| <span data-ttu-id="a43e8-119">Hiermee schakelt u fout opsporing voor DSC-resources in.</span><span class="sxs-lookup"><span data-stu-id="a43e8-119">Enables DSC resource debugging.</span></span>|
| [<span data-ttu-id="a43e8-120">De getconfiguration ()</span><span class="sxs-lookup"><span data-stu-id="a43e8-120">GetConfiguration()</span></span>](msft-dsclocalconfigurationmanager-getconfiguration.md)| <span data-ttu-id="a43e8-121">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de **Get** -methode van de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="a43e8-121">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="a43e8-122">De getconfigurationresultoutput</span><span class="sxs-lookup"><span data-stu-id="a43e8-122">GetConfigurationResultOutput</span></span>](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| <span data-ttu-id="a43e8-123">Hiermee wordt de uitvoer van de configuratie agent opgehaald die betrekking heeft op een specifieke taak.</span><span class="sxs-lookup"><span data-stu-id="a43e8-123">Gets the Configuration Agent output relating to a specific job.</span></span>|
| [<span data-ttu-id="a43e8-124">De getconfigurationstatus</span><span class="sxs-lookup"><span data-stu-id="a43e8-124">GetConfigurationStatus</span></span>](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| <span data-ttu-id="a43e8-125">De geschiedenis van de configuratie status ophalen.</span><span class="sxs-lookup"><span data-stu-id="a43e8-125">Get the configuration status history.</span></span>|
| [<span data-ttu-id="a43e8-126">De getmetaconfiguration</span><span class="sxs-lookup"><span data-stu-id="a43e8-126">GetMetaConfiguration</span></span>](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| <span data-ttu-id="a43e8-127">Hiermee worden de instellingen van de LCM opgehaald die worden gebruikt voor het beheren van de configuratie agent.</span><span class="sxs-lookup"><span data-stu-id="a43e8-127">Gets the LCM settings that are used to control Configuration Agent.</span></span>|
| [<span data-ttu-id="a43e8-128">De performrequiredconfigurationchecks</span><span class="sxs-lookup"><span data-stu-id="a43e8-128">PerformRequiredConfigurationChecks</span></span>](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| <span data-ttu-id="a43e8-129">Hiermee wordt de consistentie controle gestart.</span><span class="sxs-lookup"><span data-stu-id="a43e8-129">Starts the consistency check.</span></span>|
| [<span data-ttu-id="a43e8-130">De removeconfiguration</span><span class="sxs-lookup"><span data-stu-id="a43e8-130">RemoveConfiguration</span></span>](msft-dsclocalconfigurationmanager-removeconfiguration.md)| <span data-ttu-id="a43e8-131">Hiermee verwijdert u de configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="a43e8-131">Removes the configuration files.</span></span>|
| [<span data-ttu-id="a43e8-132">De resourceget</span><span class="sxs-lookup"><span data-stu-id="a43e8-132">ResourceGet</span></span>](msft-dsclocalconfigurationmanager-resourceget.md)| <span data-ttu-id="a43e8-133">Roept rechtstreeks de **Get** -methode van een DSC-resource aan.</span><span class="sxs-lookup"><span data-stu-id="a43e8-133">Directly calls the **Get** method of a DSC resource.</span></span>|
| [<span data-ttu-id="a43e8-134">ResourceSet</span><span class="sxs-lookup"><span data-stu-id="a43e8-134">ResourceSet</span></span>](msft-dsclocalconfigurationmanager-resourceset.md)| <span data-ttu-id="a43e8-135">Roept rechtstreeks de **ingestelde** methode van een DSC-resource aan.</span><span class="sxs-lookup"><span data-stu-id="a43e8-135">Directly calls the **Set** method of a DSC resource.</span></span>|
| [<span data-ttu-id="a43e8-136">Resource Test</span><span class="sxs-lookup"><span data-stu-id="a43e8-136">ResourceTest</span></span>](msft-dsclocalconfigurationmanager-resourcetest.md)| <span data-ttu-id="a43e8-137">Roept rechtstreeks de **test** methode van een DSC-resource aan.</span><span class="sxs-lookup"><span data-stu-id="a43e8-137">Directly calls the **Test** method of a DSC resource.</span></span>|
| [<span data-ttu-id="a43e8-138">Actie</span><span class="sxs-lookup"><span data-stu-id="a43e8-138">RollBack</span></span>](msft-dsclocalconfigurationmanager-rollback.md)| <span data-ttu-id="a43e8-139">Hiermee wordt teruggedraaid naar een eerdere configuratie.</span><span class="sxs-lookup"><span data-stu-id="a43e8-139">Rolls back to a previous configuration.</span></span>|
| [<span data-ttu-id="a43e8-140">De sendconfiguration</span><span class="sxs-lookup"><span data-stu-id="a43e8-140">SendConfiguration</span></span>](msft-dsclocalconfigurationmanager-sendconfiguration.md)| <span data-ttu-id="a43e8-141">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="a43e8-141">Sends the configuration document to the managed node and saves it as a pending change.</span></span>|
| [<span data-ttu-id="a43e8-142">De sendconfigurationapply</span><span class="sxs-lookup"><span data-stu-id="a43e8-142">SendConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| <span data-ttu-id="a43e8-143">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="a43e8-143">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>|
| [<span data-ttu-id="a43e8-144">De sendconfigurationapplyasync</span><span class="sxs-lookup"><span data-stu-id="a43e8-144">SendConfigurationApplyAsync</span></span>](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| <span data-ttu-id="a43e8-145">Stuur het configuratie document naar het beheerde knoop punt en start met behulp van de configuratie agent om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="a43e8-145">Send the configuration document to the managed node and start using the Configuration Agent to apply the configuration.</span></span> <span data-ttu-id="a43e8-146">Gebruik de getconfigurationresultoutput om resultaat uitvoer op te halen.</span><span class="sxs-lookup"><span data-stu-id="a43e8-146">Use GetConfigurationResultOutput to retrieve result output.</span></span>|
| [<span data-ttu-id="a43e8-147">De sendmetaconfigurationapply</span><span class="sxs-lookup"><span data-stu-id="a43e8-147">SendMetaConfigurationApply</span></span>](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| <span data-ttu-id="a43e8-148">Hiermee stelt u de instellingen voor de LCM die worden gebruikt voor het beheren van de configuratie agent.</span><span class="sxs-lookup"><span data-stu-id="a43e8-148">Sets the LCM settings that are used to control the Configuration Agent.</span></span>|
| [<span data-ttu-id="a43e8-149">De stopconfiguration</span><span class="sxs-lookup"><span data-stu-id="a43e8-149">StopConfiguration</span></span>](msft-dsclocalconfigurationmanager-stopconfiguration.md)| <span data-ttu-id="a43e8-150">Hiermee wordt de configuratie gestopt die momenteel wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a43e8-150">Stops the configuration that is in progress.</span></span>|
| [<span data-ttu-id="a43e8-151">De testconfiguration</span><span class="sxs-lookup"><span data-stu-id="a43e8-151">TestConfiguration</span></span>](msft-dsclocalconfigurationmanager-testconfiguration.md)| <span data-ttu-id="a43e8-152">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de huidige configuratie gecontroleerd op basis van het document.</span><span class="sxs-lookup"><span data-stu-id="a43e8-152">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>|

## <a name="requirements"></a><span data-ttu-id="a43e8-153">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a43e8-153">Requirements</span></span>

<span data-ttu-id="a43e8-154">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="a43e8-154">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a43e8-155">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a43e8-155">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>
