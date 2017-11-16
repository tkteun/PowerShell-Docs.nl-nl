---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Terugdraaien van de methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="38fbb-103">Terugdraaien van de methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="38fbb-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="38fbb-104">De configuratie teruggedraaid naar een eerdere versie.</span><span class="sxs-lookup"><span data-stu-id="38fbb-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="38fbb-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="38fbb-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="38fbb-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="38fbb-106">Parameters</span></span>
----------

<span data-ttu-id="38fbb-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="38fbb-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="38fbb-108">Hiermee geeft u de aangevraagde configuratie.</span><span class="sxs-lookup"><span data-stu-id="38fbb-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="38fbb-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="38fbb-109">Return value</span></span>
------------

<span data-ttu-id="38fbb-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="38fbb-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="38fbb-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="38fbb-111">Remarks</span></span>

<span data-ttu-id="38fbb-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="38fbb-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="38fbb-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="38fbb-113">Requirements</span></span>
------------
><span data-ttu-id="38fbb-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="38fbb-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="38fbb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="38fbb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="38fbb-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="38fbb-116">See also</span></span>


[<span data-ttu-id="38fbb-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="38fbb-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



