---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="55182-103">GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="55182-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="55182-104">Hiermee haalt u de lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie-Agent.</span><span class="sxs-lookup"><span data-stu-id="55182-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="55182-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="55182-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="55182-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="55182-106">Parameters</span></span>
----------

<span data-ttu-id="55182-107">*Metaconfiguratie* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="55182-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="55182-108">Op return bevat een ingesloten exemplaar van de **MSFT_DSCMetaConfiguration** klasse die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="55182-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="55182-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="55182-109">Return value</span></span>
------------

<span data-ttu-id="55182-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="55182-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="55182-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="55182-111">Remarks</span></span>

<span data-ttu-id="55182-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="55182-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="55182-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="55182-113">Requirements</span></span>
------------
><span data-ttu-id="55182-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="55182-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="55182-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="55182-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="55182-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="55182-116">See also</span></span>


[<span data-ttu-id="55182-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="55182-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



