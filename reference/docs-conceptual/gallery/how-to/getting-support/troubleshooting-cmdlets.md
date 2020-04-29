---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: Problemen met cmdlets oplossen
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "72352115"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="0ea14-103">Problemen met cmdlets oplossen</span><span class="sxs-lookup"><span data-stu-id="0ea14-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="0ea14-104">Het oplossen van ' waarschuwing: pakket ' kan de pakket naam niet downloaden '</span><span class="sxs-lookup"><span data-stu-id="0ea14-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="0ea14-105">Er wordt gemeld dat `Install-Module` of `Update-Module` soms op sommige computers mislukt.</span><span class="sxs-lookup"><span data-stu-id="0ea14-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="0ea14-106">Op basis van ons onderzoek is het iets te doen met de netwerk verbinding.</span><span class="sxs-lookup"><span data-stu-id="0ea14-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="0ea14-107">Onlangs hebben we de NuGet-provider bijgewerkt zodat pakketten betrouwbaar kunnen worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="0ea14-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="0ea14-108">U kunt de onderstaande instructies volgen om de meest recente build van NuGet-provider te installeren en vervolgens uw module te installeren of bij te werken.</span><span class="sxs-lookup"><span data-stu-id="0ea14-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="0ea14-109">We gebruiken de module ' Azure ' als voor beeld hieronder.</span><span class="sxs-lookup"><span data-stu-id="0ea14-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="0ea14-110">Vereiste netwerk eindpunten</span><span class="sxs-lookup"><span data-stu-id="0ea14-110">Required network endpoints</span></span>

<span data-ttu-id="0ea14-111">Voor de cmdlets install en update is Internet toegang vereist om verbinding te maken met de netwerk eindpunten die door de PowerShell Gallery worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0ea14-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="0ea14-112">Zorg ervoor dat u met uw netwerk toegangs beleid verbinding kunt maken met de volgende eind punten.</span><span class="sxs-lookup"><span data-stu-id="0ea14-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="0ea14-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="0ea14-113">oneget.org</span></span>
- <span data-ttu-id="0ea14-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="0ea14-114">go.microsoft.com</span></span>
- <span data-ttu-id="0ea14-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="0ea14-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="0ea14-116">www.powershellgallery.com</span><span class="sxs-lookup"><span data-stu-id="0ea14-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="0ea14-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="0ea14-117">devopsgallerystorage.blob.core.windows.net</span></span>
