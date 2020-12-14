---
ms.date: 12/01/2020
title: Problemen met cmdlets oplossen
description: In dit artikel vindt u informatie en stappen voor het oplossen van problemen met behulp van de PowerShell Gallery
ms.openlocfilehash: 980da8ea7b8a09513f33a9939d512c437b755d8d
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913315"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="87b53-103">Problemen met cmdlets oplossen</span><span class="sxs-lookup"><span data-stu-id="87b53-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="87b53-104">Het oplossen van ' waarschuwing: pakket ' kan de pakket naam niet downloaden '</span><span class="sxs-lookup"><span data-stu-id="87b53-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="87b53-105">Er wordt gemeld dat `Install-Module` of `Update-Module` soms op sommige computers mislukt.</span><span class="sxs-lookup"><span data-stu-id="87b53-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="87b53-106">Op basis van ons onderzoek is het iets te doen met de netwerk verbinding.</span><span class="sxs-lookup"><span data-stu-id="87b53-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="87b53-107">Onlangs hebben we de NuGet-provider bijgewerkt zodat pakketten betrouwbaar kunnen worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="87b53-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="87b53-108">U kunt de onderstaande instructies volgen om de meest recente build van NuGet-provider te installeren en vervolgens uw module te installeren of bij te werken.</span><span class="sxs-lookup"><span data-stu-id="87b53-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="87b53-109">We gebruiken de module ' Azure ' als voor beeld hieronder.</span><span class="sxs-lookup"><span data-stu-id="87b53-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a><span data-ttu-id="87b53-110">Vereiste netwerk eindpunten</span><span class="sxs-lookup"><span data-stu-id="87b53-110">Required network endpoints</span></span>

<span data-ttu-id="87b53-111">Voor de cmdlets install en update is Internet toegang vereist om verbinding te maken met de netwerk eindpunten die door de PowerShell Gallery worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="87b53-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="87b53-112">Zorg ervoor dat u met uw netwerk toegangs beleid verbinding kunt maken met de volgende eind punten.</span><span class="sxs-lookup"><span data-stu-id="87b53-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="87b53-113">`psg-prod-eastus.azureedge.net` -CDN-hostnaam</span><span class="sxs-lookup"><span data-stu-id="87b53-113">`psg-prod-eastus.azureedge.net` - CDN hostname</span></span>
- <span data-ttu-id="87b53-114">`az818661.vo.msecnd.net` -CDN-hostnaam</span><span class="sxs-lookup"><span data-stu-id="87b53-114">`az818661.vo.msecnd.net` - CDN hostname</span></span>
- <span data-ttu-id="87b53-115">`devopsgallerystorage.blob.core.windows.net` -hostnaam van opslag account</span><span class="sxs-lookup"><span data-stu-id="87b53-115">`devopsgallerystorage.blob.core.windows.net` - storage account hostname</span></span>
- <span data-ttu-id="87b53-116">`*.powershellgallery.com` -website</span><span class="sxs-lookup"><span data-stu-id="87b53-116">`*.powershellgallery.com` - website</span></span>
- <span data-ttu-id="87b53-117">`go.microsoft.com` -omleidings service</span><span class="sxs-lookup"><span data-stu-id="87b53-117">`go.microsoft.com` - redirection service</span></span>

> [!NOTE]
> <span data-ttu-id="87b53-118">Cmdlets die communiceren met de PowerShell Gallery, kunnen mislukken met onverwachte fouten als er een storing optreedt in de PowerShell Gallery Services.</span><span class="sxs-lookup"><span data-stu-id="87b53-118">Cmdlets that interact with the PowerShell Gallery can fail with unexpected errors when there is an outage of the PowerShell Gallery services.</span></span> <span data-ttu-id="87b53-119">Als u de huidige status van de PowerShell Gallery wilt zien, gaat u naar de pagina [PowerShell Gallery status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) op github.</span><span class="sxs-lookup"><span data-stu-id="87b53-119">To see the current status of the PowerShell Gallery, see the [PowerShell Gallery Status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) page on GitHub.</span></span>
