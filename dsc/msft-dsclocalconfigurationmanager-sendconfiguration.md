---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="10068-103">SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="10068-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="10068-104">Het configuratiebestand voor verzendt naar het beheerde knooppunt en wordt deze opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="10068-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="10068-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="10068-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="10068-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="10068-106">Parameters</span></span>
----------

<span data-ttu-id="10068-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="10068-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="10068-108">De omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="10068-108">The environment data for the configuration.</span></span>

<span data-ttu-id="10068-109">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="10068-109">*force* \[in\]</span></span>  
<span data-ttu-id="10068-110">**de waarde True** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="10068-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="10068-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="10068-111">Return value</span></span>
------------

<span data-ttu-id="10068-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="10068-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="10068-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="10068-113">Remarks</span></span>

<span data-ttu-id="10068-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="10068-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="10068-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="10068-115">Requirements</span></span>
------------
><span data-ttu-id="10068-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="10068-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="10068-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="10068-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="10068-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="10068-118">See also</span></span>


[<span data-ttu-id="10068-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="10068-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



