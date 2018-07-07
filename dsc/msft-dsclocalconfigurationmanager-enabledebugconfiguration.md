---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892396"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2989b-103">De EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2989b-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2989b-104">U kunt foutopsporing van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="2989b-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="2989b-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2989b-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="2989b-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="2989b-106">Parameters</span></span>

<span data-ttu-id="2989b-107">*BreakAll* \[in\] een onderbrekingspunt instellen op elke regel in het resource-script.</span><span class="sxs-lookup"><span data-stu-id="2989b-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="2989b-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="2989b-108">Return value</span></span>

<span data-ttu-id="2989b-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="2989b-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2989b-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2989b-110">Remarks</span></span>

<span data-ttu-id="2989b-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="2989b-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2989b-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2989b-112">Requirements</span></span>

<span data-ttu-id="2989b-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2989b-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2989b-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2989b-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2989b-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2989b-115">See also</span></span>

[<span data-ttu-id="2989b-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2989b-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)