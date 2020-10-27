---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfiguration-methode
description: SendConfiguration-methode
ms.openlocfilehash: 3939a76ab6672b49559847b0ef1408f1c7be6d0c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650548"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="645b1-103">SendConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="645b1-103">SendConfiguration method</span></span>

<span data-ttu-id="645b1-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="645b1-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="645b1-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="645b1-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="645b1-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="645b1-106">Parameters</span></span>

<span data-ttu-id="645b1-107">**ConfigurationData** \[ in \] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="645b1-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="645b1-108">**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="645b1-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="645b1-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="645b1-109">Return value</span></span>

<span data-ttu-id="645b1-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="645b1-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="645b1-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="645b1-111">Remarks</span></span>

<span data-ttu-id="645b1-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="645b1-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="645b1-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="645b1-113">Requirements</span></span>

<span data-ttu-id="645b1-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="645b1-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="645b1-115">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="645b1-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="645b1-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="645b1-116">See also</span></span>

[<span data-ttu-id="645b1-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="645b1-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
