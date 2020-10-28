---
ms.date: 07/17/2020
ms.topic: reference
title: GetMetaConfiguration-methode
description: GetMetaConfiguration-methode
ms.openlocfilehash: deca6b8ec342a34543bbe0e1fabbc2a740a88feb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644725"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="e05b3-103">GetMetaConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="e05b3-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="e05b3-104">Hiermee haalt u de lokale Configuration Manager-instellingen op die worden gebruikt voor het beheren van de configuratie agent.</span><span class="sxs-lookup"><span data-stu-id="e05b3-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="e05b3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e05b3-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="e05b3-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e05b3-106">Parameters</span></span>

<span data-ttu-id="e05b3-107">- **Configuratie** \[ out \] on return bevat een Inge sloten exemplaar van de klasse **MSFT_DSCMetaConfiguration** die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="e05b3-107">**MetaConfiguration** \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="e05b3-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="e05b3-108">Return value</span></span>

<span data-ttu-id="e05b3-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e05b3-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e05b3-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e05b3-110">Remarks</span></span>

<span data-ttu-id="e05b3-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="e05b3-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e05b3-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e05b3-112">Requirements</span></span>

<span data-ttu-id="e05b3-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="e05b3-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e05b3-114">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e05b3-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e05b3-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e05b3-115">See also</span></span>

[<span data-ttu-id="e05b3-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e05b3-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
