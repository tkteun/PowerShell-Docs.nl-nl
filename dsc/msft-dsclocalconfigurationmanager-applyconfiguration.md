---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892604"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6ae04-103">De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6ae04-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6ae04-104">Gebruik de configuratie van Agent voor de configuratie die in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="6ae04-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="6ae04-105">Als er geen configuratie in behandeling is, wordt deze methode de huidige configuratie opnieuw toegepast.</span><span class="sxs-lookup"><span data-stu-id="6ae04-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ae04-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6ae04-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="6ae04-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="6ae04-107">Parameters</span></span>

<span data-ttu-id="6ae04-108">*afdwingen dat* \[in\] als dit **waar**, de huidige configuratie is toegepast, zelfs als er een configuratie in behandeling.</span><span class="sxs-lookup"><span data-stu-id="6ae04-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="6ae04-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="6ae04-109">Return value</span></span>

<span data-ttu-id="6ae04-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="6ae04-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ae04-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6ae04-111">Remarks</span></span>

<span data-ttu-id="6ae04-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="6ae04-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6ae04-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6ae04-113">Requirements</span></span>

<span data-ttu-id="6ae04-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6ae04-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6ae04-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ae04-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6ae04-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6ae04-116">See also</span></span>

[<span data-ttu-id="6ae04-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6ae04-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)