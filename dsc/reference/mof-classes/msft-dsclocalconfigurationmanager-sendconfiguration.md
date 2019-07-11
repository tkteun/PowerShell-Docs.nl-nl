---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfiguration-methode
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734319"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="cfb14-103">De SendConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="cfb14-103">SendConfiguration method</span></span>

<span data-ttu-id="cfb14-104">Het configuratiebestand voor verzendt naar de beheerd knooppunt en wordt deze opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="cfb14-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="cfb14-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="cfb14-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="cfb14-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="cfb14-106">Parameters</span></span>

<span data-ttu-id="cfb14-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="cfb14-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="cfb14-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="cfb14-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="cfb14-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="cfb14-109">Return value</span></span>

<span data-ttu-id="cfb14-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="cfb14-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cfb14-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cfb14-111">Remarks</span></span>

<span data-ttu-id="cfb14-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="cfb14-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cfb14-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cfb14-113">Requirements</span></span>

<span data-ttu-id="cfb14-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cfb14-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cfb14-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cfb14-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cfb14-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cfb14-116">See also</span></span>

[<span data-ttu-id="cfb14-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cfb14-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
