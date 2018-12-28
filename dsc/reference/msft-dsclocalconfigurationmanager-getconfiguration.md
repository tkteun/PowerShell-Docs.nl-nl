---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403958"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4d94a-103">De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4d94a-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4d94a-104">Het configuratiebestand voor verzendt naar de beheerd knooppunt en maakt gebruik van de **ophalen** methode van de Agent configureren om toe te passen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="4d94a-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d94a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4d94a-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="4d94a-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="4d94a-106">Parameters</span></span>

<span data-ttu-id="4d94a-107">*configurationData* \[in\] Hiermee geeft u de configuratiegegevens te verzenden.</span><span class="sxs-lookup"><span data-stu-id="4d94a-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="4d94a-108">*configuraties* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="4d94a-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="4d94a-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="4d94a-109">Return value</span></span>

<span data-ttu-id="4d94a-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="4d94a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d94a-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4d94a-111">Remarks</span></span>

<span data-ttu-id="4d94a-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="4d94a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4d94a-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4d94a-113">Requirements</span></span>

<span data-ttu-id="4d94a-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4d94a-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4d94a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d94a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4d94a-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4d94a-116">See also</span></span>

[<span data-ttu-id="4d94a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4d94a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)