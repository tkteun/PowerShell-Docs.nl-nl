---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="58a2c-103">SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="58a2c-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="58a2c-104">Het configuratiebestand voor verzendt naar het beheerde knooppunt en wordt deze opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="58a2c-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="58a2c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="58a2c-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="58a2c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="58a2c-106">Parameters</span></span>
----------

<span data-ttu-id="58a2c-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="58a2c-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="58a2c-108">De omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="58a2c-108">The environment data for the configuration.</span></span>

<span data-ttu-id="58a2c-109">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="58a2c-109">*force* \[in\]</span></span>  
<span data-ttu-id="58a2c-110">**de waarde True** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="58a2c-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="58a2c-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="58a2c-111">Return value</span></span>
------------

<span data-ttu-id="58a2c-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="58a2c-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="58a2c-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="58a2c-113">Remarks</span></span>

<span data-ttu-id="58a2c-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="58a2c-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="58a2c-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="58a2c-115">Requirements</span></span>
------------
><span data-ttu-id="58a2c-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="58a2c-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="58a2c-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="58a2c-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="58a2c-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="58a2c-118">See also</span></span>


[<span data-ttu-id="58a2c-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="58a2c-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



