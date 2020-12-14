---
description: Hierin wordt de telemetrie die is verzameld in Power shell beschreven en wordt uitgelegd hoe u dit kunt afmelden.
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: 677d43b405fdc92e6b68d6e903847b11cb671a2c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705899"
---
# <a name="about-telemetry"></a><span data-ttu-id="a8f5c-103">Over telemetrie</span><span class="sxs-lookup"><span data-stu-id="a8f5c-103">About Telemetry</span></span>

## <a name="short-description"></a><span data-ttu-id="a8f5c-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a8f5c-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="a8f5c-105">Hierin wordt de telemetrie die is verzameld in Power shell beschreven en wordt uitgelegd hoe u dit kunt afmelden.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-105">Describes the telemetry collected in PowerShell and how to opt-out.</span></span>

## <a name="long-description"></a><span data-ttu-id="a8f5c-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a8f5c-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="a8f5c-107">Power shell verzendt elementaire telemetriegegevens naar micro soft.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-107">PowerShell sends basic telemetry data to Microsoft.</span></span>
<span data-ttu-id="a8f5c-108">Met deze gegevens kunnen we beter inzicht krijgen in de omgevingen waarin Power shell wordt gebruikt en kunnen we de prioriteit van nieuwe functies en oplossingen bepalen.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-108">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>
<span data-ttu-id="a8f5c-109">De volgende telemetriegegevens worden vastgelegd:</span><span class="sxs-lookup"><span data-stu-id="a8f5c-109">The following telemetry points are recorded:</span></span>

- <span data-ttu-id="a8f5c-110">Aantal Power shell wordt gestart op type (API versus console)</span><span class="sxs-lookup"><span data-stu-id="a8f5c-110">Count of PowerShell Starts by type (API vs console)</span></span>
- <span data-ttu-id="a8f5c-111">Aantal unieke Power shell-gebruik</span><span class="sxs-lookup"><span data-stu-id="a8f5c-111">Count of unique PowerShell usage</span></span>
- <span data-ttu-id="a8f5c-112">Aantal van de volgende uitvoerings typen:</span><span class="sxs-lookup"><span data-stu-id="a8f5c-112">Count of the following execution types:</span></span>
  - <span data-ttu-id="a8f5c-113">Toepassing (systeem eigen opdrachten)</span><span class="sxs-lookup"><span data-stu-id="a8f5c-113">Application (native commands)</span></span>
  - <span data-ttu-id="a8f5c-114">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="a8f5c-114">ExternalScript</span></span>
  - <span data-ttu-id="a8f5c-115">Script</span><span class="sxs-lookup"><span data-stu-id="a8f5c-115">Script</span></span>
  - <span data-ttu-id="a8f5c-116">Functie</span><span class="sxs-lookup"><span data-stu-id="a8f5c-116">Function</span></span>
  - <span data-ttu-id="a8f5c-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a8f5c-117">Cmdlet</span></span>
- <span data-ttu-id="a8f5c-118">Aantal ingeschakelde experimentele functies van micro soft of experimentele functies die worden geleverd met Power shell</span><span class="sxs-lookup"><span data-stu-id="a8f5c-118">Count of enabled Microsoft owned experimental features or experimental features shipped with PowerShell</span></span>
- <span data-ttu-id="a8f5c-119">Aantal gehoste sessies</span><span class="sxs-lookup"><span data-stu-id="a8f5c-119">Count of hosted sessions</span></span>
- <span data-ttu-id="a8f5c-120">Aantal geladen micro soft-modules</span><span class="sxs-lookup"><span data-stu-id="a8f5c-120">Count of Microsoft owned modules loaded</span></span>

<span data-ttu-id="a8f5c-121">Deze gegevens omvatten de naam van het besturings systeem, de versie van het besturings systeem, de Power shell-versie en het distributie kanaal.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-121">This data includes the OS name, OS version, the PowerShell version, and the distribution channel.</span></span>

<span data-ttu-id="a8f5c-122">Als u deze telemetrie wilt afmelden, stelt u de omgevings variabele POWERSHELL_TELEMETRY_OPTOUT in op waar, ja of 1.</span><span class="sxs-lookup"><span data-stu-id="a8f5c-122">To opt-out of this telemetry, set the environment variable POWERSHELL_TELEMETRY_OPTOUT to true, yes, or 1.</span></span>

