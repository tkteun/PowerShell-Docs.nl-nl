---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46eec896df643996bea5f2c371a9294034caae6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218413"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f06d4-103">De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f06d4-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f06d4-104">Verzendt het configuratie-document naar het beheerde knooppunt en maakt gebruik van de **ophalen** methode van de configuratie-Agent de configuratie toepassen.</span><span class="sxs-lookup"><span data-stu-id="f06d4-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="f06d4-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f06d4-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="f06d4-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="f06d4-106">Parameters</span></span>
----------

<span data-ttu-id="f06d4-107">*configurationData* \[in\] Hiermee geeft u de configuratiegegevens te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f06d4-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="f06d4-108">*configuraties* \[uit\] op return bevat een ingesloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="f06d4-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="f06d4-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="f06d4-109">Return value</span></span>
------------

<span data-ttu-id="f06d4-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="f06d4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f06d4-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f06d4-111">Remarks</span></span>

<span data-ttu-id="f06d4-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="f06d4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f06d4-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f06d4-113">Requirements</span></span>
------------
><span data-ttu-id="f06d4-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f06d4-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f06d4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f06d4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f06d4-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f06d4-116">See also</span></span>


[<span data-ttu-id="f06d4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f06d4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)