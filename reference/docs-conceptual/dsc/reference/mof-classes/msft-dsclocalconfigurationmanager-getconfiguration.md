---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetConfiguration-methode
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942711"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="3adfe-103">GetConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="3adfe-103">GetConfiguration method</span></span>

<span data-ttu-id="3adfe-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de **Get** -methode van de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="3adfe-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="3adfe-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3adfe-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="3adfe-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="3adfe-106">Parameters</span></span>

<span data-ttu-id="3adfe-107">*configurationData* \[in\] geeft aan welke configuratie gegevens moeten worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="3adfe-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="3adfe-108">*configuraties* \[out\] als resultaat, bevat een Inge sloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="3adfe-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="3adfe-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="3adfe-109">Return value</span></span>

<span data-ttu-id="3adfe-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3adfe-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3adfe-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3adfe-111">Remarks</span></span>

<span data-ttu-id="3adfe-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="3adfe-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3adfe-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3adfe-113">Requirements</span></span>

<span data-ttu-id="3adfe-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="3adfe-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3adfe-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3adfe-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3adfe-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3adfe-116">See also</span></span>

[<span data-ttu-id="3adfe-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3adfe-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
