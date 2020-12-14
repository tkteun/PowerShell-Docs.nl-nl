---
description: Hiermee worden gebruikers op de hoogte gesteld van het starten van Power shell dat er een nieuwe versie van Power shell is uitgebracht.
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 1a9f8cfec15f83566fdb77175dcc1aed6d9e8c34
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705515"
---
# <a name="about-update-notifications"></a><span data-ttu-id="086ec-103">Over update meldingen</span><span class="sxs-lookup"><span data-stu-id="086ec-103">About Update Notifications</span></span>

## <a name="short-description"></a><span data-ttu-id="086ec-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="086ec-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="086ec-105">Hiermee worden gebruikers op de hoogte gesteld van het starten van Power shell dat er een nieuwe versie van Power shell is uitgebracht.</span><span class="sxs-lookup"><span data-stu-id="086ec-105">Notifies users on startup of PowerShell that a new version of PowerShell has been released.</span></span>

## <a name="long-description"></a><span data-ttu-id="086ec-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="086ec-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="086ec-107">Vanaf Power shell 7,0 worden er update meldingen gebruikt om gebruikers te waarschuwen dat er updates zijn voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="086ec-107">Beginning with PowerShell 7.0, PowerShell uses update notifications to alert users to the existence of updates to PowerShell.</span></span> <span data-ttu-id="086ec-108">Eenmaal per dag vraagt Power shell een online service aan om te bepalen of er een nieuwere versie beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="086ec-108">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="086ec-109">Hoewel tijdens de eerste sessie van een bepaalde periode van 24 uur de update controle plaatsvindt, wordt de melding alleen weer gegeven aan het begin van volgende sessies.</span><span class="sxs-lookup"><span data-stu-id="086ec-109">While the update check happens during the first session in a given 24-hour period, for performance reasons, the notification will only be shown on the start of subsequent sessions.</span></span> <span data-ttu-id="086ec-110">De controle kan ook om prestatie redenen niet worden gestart tot ten minste 3 seconden nadat de sessie is gestart.</span><span class="sxs-lookup"><span data-stu-id="086ec-110">Also for performance reasons, the check will not start until at least 3 seconds after the session begins.</span></span>

<span data-ttu-id="086ec-111">Power shell abonneert standaard op een van twee verschillende meldings kanalen, afhankelijk van de versie/vertakking.</span><span class="sxs-lookup"><span data-stu-id="086ec-111">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="086ec-112">Ondersteunde, algemeen beschik bare (GA) versies van Power shell retour neren alleen meldingen voor bijgewerkte GA-releases.</span><span class="sxs-lookup"><span data-stu-id="086ec-112">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="086ec-113">Preview en release Candi date (RC) geven een melding van updates voor preview-, RC-en GA-releases.</span><span class="sxs-lookup"><span data-stu-id="086ec-113">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="086ec-114">Het gedrag van de update melding kan worden gewijzigd met behulp van de `POWERSHELL_UPDATECHECK` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="086ec-114">The update notification behavior can be changed using the `POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="086ec-115">De volgende waarden worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="086ec-115">The following values are supported:</span></span>

- <span data-ttu-id="086ec-116">`Off` Hiermee schakelt u de update meldings functie uit</span><span class="sxs-lookup"><span data-stu-id="086ec-116">`Off` turns off the update notification feature</span></span>
- <span data-ttu-id="086ec-117">`Default` is hetzelfde als niet definiëren `POWERSHELL_UPDATECHECK` :</span><span class="sxs-lookup"><span data-stu-id="086ec-117">`Default` is the same as not defining `POWERSHELL_UPDATECHECK`:</span></span>
  - <span data-ttu-id="086ec-118">GA releases op de hoogte van updates voor GA releases</span><span class="sxs-lookup"><span data-stu-id="086ec-118">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="086ec-119">Preview/RC geeft melding van updates voor GA-en Preview-versies</span><span class="sxs-lookup"><span data-stu-id="086ec-119">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="086ec-120">`LTS` alleen berichten met updates voor LTS-GA releases (Long-term-Servicing)</span><span class="sxs-lookup"><span data-stu-id="086ec-120">`LTS` only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

<span data-ttu-id="086ec-121">De volgende eind punten worden momenteel gebruikt voor het bepalen van de meest recente versie van elk kanaal:</span><span class="sxs-lookup"><span data-stu-id="086ec-121">The following endpoints are currently used for determining the latest version of each channel:</span></span>

- <span data-ttu-id="086ec-122">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span><span class="sxs-lookup"><span data-stu-id="086ec-122">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span></span>
- <span data-ttu-id="086ec-123">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span><span class="sxs-lookup"><span data-stu-id="086ec-123">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span></span>
- <span data-ttu-id="086ec-124">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span><span class="sxs-lookup"><span data-stu-id="086ec-124">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span></span>

<span data-ttu-id="086ec-125">De update melding biedt geen manier om Power shell automatisch bij te werken.</span><span class="sxs-lookup"><span data-stu-id="086ec-125">The update notification doesn't provide any way to automatically update PowerShell.</span></span> <span data-ttu-id="086ec-126">In de toekomst kunnen er meer instructies of mogelijkheden zijn om bij te werken vanuit Power shell, maar vandaag moet u hetzelfde installatie mechanisme gebruiken dat u hebt gebruikt om Power shell te installeren om het bij te werken.</span><span class="sxs-lookup"><span data-stu-id="086ec-126">In the future, there may be more instructions or capabilities to update from within PowerShell, but today, you should use the same install mechanism you used to install PowerShell to update it.</span></span>

