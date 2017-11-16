---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9893f-103">GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="9893f-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9893f-104">Verzendt het configuratie-document naar het beheerde knooppunt en maakt gebruik van de **ophalen** methode van de configuratie-Agent de configuratie toepassen.</span><span class="sxs-lookup"><span data-stu-id="9893f-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="9893f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9893f-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="9893f-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="9893f-106">Parameters</span></span>
----------

<span data-ttu-id="9893f-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9893f-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="9893f-108">Hiermee geeft u de configuratiegegevens te verzenden.</span><span class="sxs-lookup"><span data-stu-id="9893f-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="9893f-109">*configuraties* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="9893f-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="9893f-110">Bevat een ingesloten exemplaar van de configuraties op return.</span><span class="sxs-lookup"><span data-stu-id="9893f-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="9893f-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="9893f-111">Return value</span></span>
------------

<span data-ttu-id="9893f-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="9893f-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9893f-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9893f-113">Remarks</span></span>

<span data-ttu-id="9893f-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="9893f-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9893f-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9893f-115">Requirements</span></span>
------------
><span data-ttu-id="9893f-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9893f-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9893f-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9893f-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9893f-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9893f-118">See also</span></span>


[<span data-ttu-id="9893f-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9893f-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



