---
description: Hiermee worden gebruikers op de hoogte gesteld van het starten van Power shell dat er een nieuwe versie van Power shell is uitgebracht.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 258eb9316ba063069d032bc115bdeb4614666f37
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252974"
---
# <a name="about-update-notifications"></a><span data-ttu-id="6c97e-104">Over update meldingen</span><span class="sxs-lookup"><span data-stu-id="6c97e-104">About Update Notifications</span></span>

## <a name="short-description"></a><span data-ttu-id="6c97e-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6c97e-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="6c97e-106">Hiermee worden gebruikers op de hoogte gesteld van het starten van Power shell dat er een nieuwe versie van Power shell is uitgebracht.</span><span class="sxs-lookup"><span data-stu-id="6c97e-106">Notifies users on startup of PowerShell that a new version of PowerShell has been released.</span></span>

## <a name="long-description"></a><span data-ttu-id="6c97e-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6c97e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="6c97e-108">Vanaf Power shell 7,0 worden er update meldingen gebruikt om gebruikers te waarschuwen dat er updates zijn voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="6c97e-108">Beginning with PowerShell 7.0, PowerShell uses update notifications to alert users to the existence of updates to PowerShell.</span></span> <span data-ttu-id="6c97e-109">Eenmaal per dag vraagt Power shell een online service aan om te bepalen of er een nieuwere versie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="6c97e-109">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="6c97e-110">Hoewel tijdens de eerste sessie van een bepaalde periode van 24 uur de update controle plaatsvindt, wordt de melding alleen weer gegeven aan het begin van volgende sessies.</span><span class="sxs-lookup"><span data-stu-id="6c97e-110">While the update check happens during the first session in a given 24-hour period, for performance reasons, the notification will only be shown on the start of subsequent sessions.</span></span> <span data-ttu-id="6c97e-111">De controle kan ook om prestatie redenen niet worden gestart tot ten minste 3 seconden nadat de sessie is gestart.</span><span class="sxs-lookup"><span data-stu-id="6c97e-111">Also for performance reasons, the check will not start until at least 3 seconds after the session begins.</span></span>

<span data-ttu-id="6c97e-112">Power shell abonneert standaard op een van twee verschillende meldings kanalen, afhankelijk van de versie/vertakking.</span><span class="sxs-lookup"><span data-stu-id="6c97e-112">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="6c97e-113">Ondersteunde, algemeen beschik bare (GA) versies van Power shell retour neren alleen meldingen voor bijgewerkte GA-releases.</span><span class="sxs-lookup"><span data-stu-id="6c97e-113">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="6c97e-114">Preview en release Candi date (RC) geven een melding van updates voor preview-, RC-en GA-releases.</span><span class="sxs-lookup"><span data-stu-id="6c97e-114">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="6c97e-115">Het gedrag van de update melding kan worden gewijzigd met behulp van de `POWERSHELL_UPDATECHECK` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="6c97e-115">The update notification behavior can be changed using the `POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="6c97e-116">De volgende waarden worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="6c97e-116">The following values are supported:</span></span>

- <span data-ttu-id="6c97e-117">`Off` Hiermee schakelt u de update meldings functie uit</span><span class="sxs-lookup"><span data-stu-id="6c97e-117">`Off` turns off the update notification feature</span></span>
- <span data-ttu-id="6c97e-118">`Default` is hetzelfde als niet definiëren `POWERSHELL_UPDATECHECK` :</span><span class="sxs-lookup"><span data-stu-id="6c97e-118">`Default` is the same as not defining `POWERSHELL_UPDATECHECK`:</span></span>
  - <span data-ttu-id="6c97e-119">GA releases op de hoogte van updates voor GA releases</span><span class="sxs-lookup"><span data-stu-id="6c97e-119">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="6c97e-120">Preview/RC geeft melding van updates voor GA-en Preview-versies</span><span class="sxs-lookup"><span data-stu-id="6c97e-120">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="6c97e-121">`LTS` alleen berichten met updates voor LTS-GA releases (Long-term-Servicing)</span><span class="sxs-lookup"><span data-stu-id="6c97e-121">`LTS` only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

<span data-ttu-id="6c97e-122">De volgende eind punten worden momenteel gebruikt voor het bepalen van de meest recente versie van elk kanaal:</span><span class="sxs-lookup"><span data-stu-id="6c97e-122">The following endpoints are currently used for determining the latest version of each channel:</span></span>

- <span data-ttu-id="6c97e-123">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span><span class="sxs-lookup"><span data-stu-id="6c97e-123">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span></span>
- <span data-ttu-id="6c97e-124">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span><span class="sxs-lookup"><span data-stu-id="6c97e-124">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span></span>
- <span data-ttu-id="6c97e-125">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span><span class="sxs-lookup"><span data-stu-id="6c97e-125">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span></span>

<span data-ttu-id="6c97e-126">De update melding biedt geen manier om Power shell automatisch bij te werken.</span><span class="sxs-lookup"><span data-stu-id="6c97e-126">The update notification doesn't provide any way to automatically update PowerShell.</span></span> <span data-ttu-id="6c97e-127">In de toekomst kunnen er meer instructies of mogelijkheden zijn om bij te werken vanuit Power shell, maar vandaag moet u hetzelfde installatie mechanisme gebruiken dat u hebt gebruikt om Power shell te installeren om het bij te werken.</span><span class="sxs-lookup"><span data-stu-id="6c97e-127">In the future, there may be more instructions or capabilities to update from within PowerShell, but today, you should use the same install mechanism you used to install PowerShell to update it.</span></span>

