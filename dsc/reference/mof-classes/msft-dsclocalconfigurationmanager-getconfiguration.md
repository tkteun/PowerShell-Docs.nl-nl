---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048335"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0d7f0-103">De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0d7f0-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0d7f0-104">Het configuratiebestand voor verzendt naar de beheerd knooppunt en maakt gebruik van de **ophalen** methode van de Agent configureren om toe te passen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="0d7f0-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d7f0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0d7f0-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="0d7f0-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="0d7f0-106">Parameters</span></span>

<span data-ttu-id="0d7f0-107">*configurationData* \[in\] Hiermee geeft u de configuratiegegevens te verzenden.</span><span class="sxs-lookup"><span data-stu-id="0d7f0-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="0d7f0-108">*configuraties* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="0d7f0-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d7f0-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="0d7f0-109">Return value</span></span>

<span data-ttu-id="0d7f0-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="0d7f0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d7f0-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0d7f0-111">Remarks</span></span>

<span data-ttu-id="0d7f0-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="0d7f0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d7f0-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0d7f0-113">Requirements</span></span>

<span data-ttu-id="0d7f0-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0d7f0-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0d7f0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d7f0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0d7f0-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0d7f0-116">See also</span></span>

[<span data-ttu-id="0d7f0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0d7f0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)