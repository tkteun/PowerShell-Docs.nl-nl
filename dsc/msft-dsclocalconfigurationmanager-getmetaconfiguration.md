---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892838"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="24696-103">De GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="24696-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="24696-104">De lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie van Agent worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="24696-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="24696-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="24696-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="24696-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="24696-106">Parameters</span></span>

<span data-ttu-id="24696-107">*MetaConfiguration* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de **MSFT_DSCMetaConfiguration** klasse waarin de instellingen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="24696-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="24696-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="24696-108">Return value</span></span>

<span data-ttu-id="24696-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="24696-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24696-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="24696-110">Remarks</span></span>

<span data-ttu-id="24696-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="24696-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24696-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="24696-112">Requirements</span></span>

<span data-ttu-id="24696-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24696-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="24696-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24696-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="24696-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="24696-115">See also</span></span>

[<span data-ttu-id="24696-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="24696-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)