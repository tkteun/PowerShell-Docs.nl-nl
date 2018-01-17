---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Terugdraaien van de methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="632d0-103">Terugdraaien van de methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="632d0-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="632d0-104">De configuratie teruggedraaid naar een eerdere versie.</span><span class="sxs-lookup"><span data-stu-id="632d0-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="632d0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="632d0-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="632d0-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="632d0-106">Parameters</span></span>
----------

<span data-ttu-id="632d0-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="632d0-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="632d0-108">Hiermee geeft u de aangevraagde configuratie.</span><span class="sxs-lookup"><span data-stu-id="632d0-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="632d0-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="632d0-109">Return value</span></span>
------------

<span data-ttu-id="632d0-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="632d0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="632d0-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="632d0-111">Remarks</span></span>

<span data-ttu-id="632d0-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="632d0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="632d0-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="632d0-113">Requirements</span></span>
------------
><span data-ttu-id="632d0-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="632d0-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="632d0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="632d0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="632d0-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="632d0-116">See also</span></span>


[<span data-ttu-id="632d0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="632d0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



