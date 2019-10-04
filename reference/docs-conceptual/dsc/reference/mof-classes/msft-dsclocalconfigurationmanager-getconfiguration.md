---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetConfiguration-methode
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942711"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="c4515-103">GetConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="c4515-103">GetConfiguration method</span></span>

<span data-ttu-id="c4515-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de **Get** -methode van de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="c4515-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4515-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c4515-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="c4515-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="c4515-106">Parameters</span></span>

<span data-ttu-id="c4515-107">*configurationData* \[in @ no__t-2 geeft aan welke configuratie gegevens moeten worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="c4515-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="c4515-108">*configuraties* \[out @ no__t-2 bij Return, bevat een Inge sloten instantie van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="c4515-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="c4515-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="c4515-109">Return value</span></span>

<span data-ttu-id="c4515-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c4515-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4515-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c4515-111">Remarks</span></span>

<span data-ttu-id="c4515-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="c4515-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4515-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c4515-113">Requirements</span></span>

<span data-ttu-id="c4515-114">**MANAGE** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="c4515-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c4515-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4515-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c4515-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c4515-116">See also</span></span>

[<span data-ttu-id="c4515-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c4515-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
