---
description: Hierin wordt de telemetrie die is verzameld in Power shell beschreven en wordt uitgelegd hoe u dit kunt afmelden.
keywords: powershell
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: ef921d0feefe277c2832c0a459ae150c9a6b4acb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252514"
---
# <a name="about-telemetry"></a><span data-ttu-id="5add9-104">Over telemetrie</span><span class="sxs-lookup"><span data-stu-id="5add9-104">About Telemetry</span></span>

## <a name="short-description"></a><span data-ttu-id="5add9-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5add9-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="5add9-106">Hierin wordt de telemetrie die is verzameld in Power shell beschreven en wordt uitgelegd hoe u dit kunt afmelden.</span><span class="sxs-lookup"><span data-stu-id="5add9-106">Describes the telemetry collected in PowerShell and how to opt-out.</span></span>

## <a name="long-description"></a><span data-ttu-id="5add9-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5add9-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="5add9-108">Power shell verzendt elementaire telemetriegegevens naar micro soft.</span><span class="sxs-lookup"><span data-stu-id="5add9-108">PowerShell sends basic telemetry data to Microsoft.</span></span>
<span data-ttu-id="5add9-109">Met deze gegevens kunnen we beter inzicht krijgen in de omgevingen waarin Power shell wordt gebruikt en kunnen we de prioriteit van nieuwe functies en oplossingen bepalen.</span><span class="sxs-lookup"><span data-stu-id="5add9-109">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>
<span data-ttu-id="5add9-110">De volgende telemetriegegevens worden vastgelegd:</span><span class="sxs-lookup"><span data-stu-id="5add9-110">The following telemetry points are recorded:</span></span>

- <span data-ttu-id="5add9-111">Aantal Power shell wordt gestart op type (API versus console)</span><span class="sxs-lookup"><span data-stu-id="5add9-111">Count of PowerShell Starts by type (API vs console)</span></span>
- <span data-ttu-id="5add9-112">Aantal unieke Power shell-gebruik</span><span class="sxs-lookup"><span data-stu-id="5add9-112">Count of unique PowerShell usage</span></span>
- <span data-ttu-id="5add9-113">Aantal van de volgende uitvoerings typen:</span><span class="sxs-lookup"><span data-stu-id="5add9-113">Count of the following execution types:</span></span>
  - <span data-ttu-id="5add9-114">Toepassing (systeem eigen opdrachten)</span><span class="sxs-lookup"><span data-stu-id="5add9-114">Application (native commands)</span></span>
  - <span data-ttu-id="5add9-115">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="5add9-115">ExternalScript</span></span>
  - <span data-ttu-id="5add9-116">Script</span><span class="sxs-lookup"><span data-stu-id="5add9-116">Script</span></span>
  - <span data-ttu-id="5add9-117">Functie</span><span class="sxs-lookup"><span data-stu-id="5add9-117">Function</span></span>
  - <span data-ttu-id="5add9-118">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5add9-118">Cmdlet</span></span>
- <span data-ttu-id="5add9-119">Aantal ingeschakelde experimentele functies van micro soft of experimentele functies die worden geleverd met Power shell</span><span class="sxs-lookup"><span data-stu-id="5add9-119">Count of enabled Microsoft owned experimental features or experimental features shipped with PowerShell</span></span>
- <span data-ttu-id="5add9-120">Aantal gehoste sessies</span><span class="sxs-lookup"><span data-stu-id="5add9-120">Count of hosted sessions</span></span>
- <span data-ttu-id="5add9-121">Aantal geladen micro soft-modules</span><span class="sxs-lookup"><span data-stu-id="5add9-121">Count of Microsoft owned modules loaded</span></span>

<span data-ttu-id="5add9-122">Deze gegevens omvatten de naam van het besturings systeem, de versie van het besturings systeem, de Power shell-versie en het distributie kanaal.</span><span class="sxs-lookup"><span data-stu-id="5add9-122">This data includes the OS name, OS version, the PowerShell version, and the distribution channel.</span></span>

<span data-ttu-id="5add9-123">Als u deze telemetrie wilt afmelden, stelt u de omgevings variabele POWERSHELL_TELEMETRY_OPTOUT in op waar, ja of 1.</span><span class="sxs-lookup"><span data-stu-id="5add9-123">To opt-out of this telemetry, set the environment variable POWERSHELL_TELEMETRY_OPTOUT to true, yes, or 1.</span></span>

