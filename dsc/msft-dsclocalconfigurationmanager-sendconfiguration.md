---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892440"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="379ba-103">De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="379ba-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="379ba-104">Het configuratiebestand voor verzendt naar de beheerd knooppunt en wordt deze opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="379ba-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="379ba-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="379ba-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="379ba-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="379ba-106">Parameters</span></span>

<span data-ttu-id="379ba-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="379ba-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="379ba-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="379ba-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="379ba-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="379ba-109">Return value</span></span>

<span data-ttu-id="379ba-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="379ba-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="379ba-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="379ba-111">Remarks</span></span>

<span data-ttu-id="379ba-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="379ba-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="379ba-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="379ba-113">Requirements</span></span>

<span data-ttu-id="379ba-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="379ba-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="379ba-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="379ba-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="379ba-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="379ba-116">See also</span></span>

[<span data-ttu-id="379ba-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="379ba-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)