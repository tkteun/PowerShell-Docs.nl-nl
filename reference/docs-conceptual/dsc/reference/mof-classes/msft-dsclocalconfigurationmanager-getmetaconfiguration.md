---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetMetaConfiguration-methode
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941563"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="07e12-103">GetMetaConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="07e12-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="07e12-104">Hiermee haalt u de lokale Configuration Manager-instellingen op die worden gebruikt voor het beheren van de configuratie agent.</span><span class="sxs-lookup"><span data-stu-id="07e12-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="07e12-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="07e12-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="07e12-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="07e12-106">Parameters</span></span>

<span data-ttu-id="07e12-107">*MetaConfiguration* \[De meta-\] configuratie out voor Return bevat een Inge sloten instantie van de klasse **MSFT_DSCMetaConfiguration** die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="07e12-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="07e12-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="07e12-108">Return value</span></span>

<span data-ttu-id="07e12-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="07e12-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="07e12-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="07e12-110">Remarks</span></span>

<span data-ttu-id="07e12-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="07e12-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="07e12-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="07e12-112">Requirements</span></span>

<span data-ttu-id="07e12-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="07e12-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="07e12-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="07e12-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="07e12-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="07e12-115">See also</span></span>

[<span data-ttu-id="07e12-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="07e12-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
