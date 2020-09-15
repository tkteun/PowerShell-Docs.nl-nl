---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: GetMetaConfiguration-methode
ms.openlocfilehash: 5111cb3b15e0fba0bf71b412580efdd3cd95b2dc
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463972"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="7823c-103">GetMetaConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="7823c-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="7823c-104">Hiermee haalt u de lokale Configuration Manager-instellingen op die worden gebruikt voor het beheren van de configuratie agent.</span><span class="sxs-lookup"><span data-stu-id="7823c-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="7823c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7823c-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="7823c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="7823c-106">Parameters</span></span>

<span data-ttu-id="7823c-107">- **Configuratie** \[ out \] on return bevat een Inge sloten exemplaar van de klasse **MSFT_DSCMetaConfiguration** die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="7823c-107">**MetaConfiguration** \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="7823c-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="7823c-108">Return value</span></span>

<span data-ttu-id="7823c-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7823c-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7823c-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7823c-110">Remarks</span></span>

<span data-ttu-id="7823c-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="7823c-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7823c-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7823c-112">Requirements</span></span>

<span data-ttu-id="7823c-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="7823c-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7823c-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7823c-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7823c-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7823c-115">See also</span></span>

[<span data-ttu-id="7823c-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7823c-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
