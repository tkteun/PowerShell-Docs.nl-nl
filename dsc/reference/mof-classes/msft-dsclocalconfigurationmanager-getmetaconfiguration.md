---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetMetaConfiguration-methode
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734443"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="db5f5-103">De GetMetaConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="db5f5-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="db5f5-104">De lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie van Agent worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="db5f5-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="db5f5-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="db5f5-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="db5f5-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="db5f5-106">Parameters</span></span>

<span data-ttu-id="db5f5-107">*MetaConfiguration* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de **MSFT_DSCMetaConfiguration** klasse waarin de instellingen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="db5f5-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="db5f5-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="db5f5-108">Return value</span></span>

<span data-ttu-id="db5f5-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="db5f5-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="db5f5-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="db5f5-110">Remarks</span></span>

<span data-ttu-id="db5f5-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="db5f5-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="db5f5-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="db5f5-112">Requirements</span></span>

<span data-ttu-id="db5f5-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="db5f5-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="db5f5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="db5f5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="db5f5-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="db5f5-115">See also</span></span>

[<span data-ttu-id="db5f5-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="db5f5-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
