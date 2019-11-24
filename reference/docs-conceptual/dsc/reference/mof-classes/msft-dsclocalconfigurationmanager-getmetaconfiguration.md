---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetMetaConfiguration-methode
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941563"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="e6f15-103">GetMetaConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="e6f15-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="e6f15-104">Hiermee haalt u de lokale Configuration Manager-instellingen op die worden gebruikt voor het beheren van de configuratie agent.</span><span class="sxs-lookup"><span data-stu-id="e6f15-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6f15-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e6f15-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="e6f15-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e6f15-106">Parameters</span></span>

<span data-ttu-id="e6f15-107">Meta *configuratie* \[out\] als resultaat, bevat een Inge sloten instantie van de **MSFT_DSCMetaConfiguration** -klasse die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="e6f15-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="e6f15-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="e6f15-108">Return value</span></span>

<span data-ttu-id="e6f15-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e6f15-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6f15-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e6f15-110">Remarks</span></span>

<span data-ttu-id="e6f15-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="e6f15-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6f15-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e6f15-112">Requirements</span></span>

<span data-ttu-id="e6f15-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="e6f15-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e6f15-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e6f15-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e6f15-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e6f15-115">See also</span></span>

[<span data-ttu-id="e6f15-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e6f15-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
