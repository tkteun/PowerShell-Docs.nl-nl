---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: SendConfiguration-methode
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941549"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="b0bf3-103">SendConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="b0bf3-103">SendConfiguration method</span></span>

<span data-ttu-id="b0bf3-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="b0bf3-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0bf3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b0bf3-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="b0bf3-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="b0bf3-106">Parameters</span></span>

<span data-ttu-id="b0bf3-107">*ConfigurationData* \[in\] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="b0bf3-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="b0bf3-108">*dwing* \[in\] **waar** om te voor komen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="b0bf3-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0bf3-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="b0bf3-109">Return value</span></span>

<span data-ttu-id="b0bf3-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b0bf3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0bf3-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b0bf3-111">Remarks</span></span>

<span data-ttu-id="b0bf3-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="b0bf3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0bf3-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b0bf3-113">Requirements</span></span>

<span data-ttu-id="b0bf3-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="b0bf3-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b0bf3-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0bf3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b0bf3-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b0bf3-116">See also</span></span>

[<span data-ttu-id="b0bf3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b0bf3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
