---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b4d4c901268344ba67d77e4dc982042bfc2abd78
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7ffd9-103">De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7ffd9-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7ffd9-104">Het configuratiebestand voor verzendt naar het beheerde knooppunt en wordt deze opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="7ffd9-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="7ffd9-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7ffd9-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="7ffd9-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="7ffd9-106">Parameters</span></span>
----------

<span data-ttu-id="7ffd9-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="7ffd9-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="7ffd9-108">*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="7ffd9-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7ffd9-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="7ffd9-109">Return value</span></span>
------------

<span data-ttu-id="7ffd9-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="7ffd9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ffd9-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7ffd9-111">Remarks</span></span>

<span data-ttu-id="7ffd9-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="7ffd9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7ffd9-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7ffd9-113">Requirements</span></span>
------------
><span data-ttu-id="7ffd9-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7ffd9-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7ffd9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ffd9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7ffd9-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7ffd9-116">See also</span></span>


[<span data-ttu-id="7ffd9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7ffd9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)