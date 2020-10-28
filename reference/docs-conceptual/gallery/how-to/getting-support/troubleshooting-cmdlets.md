---
ms.date: 06/12/2017
title: Problemen met cmdlets oplossen
description: In dit artikel vindt u informatie en stappen voor het oplossen van problemen met behulp van de PowerShell Gallery
ms.openlocfilehash: db9e58c185c6f3bca26ff3639af85fa2dba48909
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661066"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="5d5b4-103">Problemen met cmdlets oplossen</span><span class="sxs-lookup"><span data-stu-id="5d5b4-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="5d5b4-104">Het oplossen van ' waarschuwing: pakket ' kan de pakket naam niet downloaden '</span><span class="sxs-lookup"><span data-stu-id="5d5b4-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="5d5b4-105">Er wordt gemeld dat `Install-Module` of `Update-Module` soms op sommige computers mislukt.</span><span class="sxs-lookup"><span data-stu-id="5d5b4-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="5d5b4-106">Op basis van ons onderzoek is het iets te doen met de netwerk verbinding.</span><span class="sxs-lookup"><span data-stu-id="5d5b4-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="5d5b4-107">Onlangs hebben we de NuGet-provider bijgewerkt zodat pakketten betrouwbaar kunnen worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="5d5b4-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="5d5b4-108">U kunt de onderstaande instructies volgen om de meest recente build van NuGet-provider te installeren en vervolgens uw module te installeren of bij te werken.</span><span class="sxs-lookup"><span data-stu-id="5d5b4-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="5d5b4-109">We gebruiken de module ' Azure ' als voor beeld hieronder.</span><span class="sxs-lookup"><span data-stu-id="5d5b4-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="5d5b4-110">Vereiste netwerk eindpunten</span><span class="sxs-lookup"><span data-stu-id="5d5b4-110">Required network endpoints</span></span>

<span data-ttu-id="5d5b4-111">Voor de cmdlets install en update is Internet toegang vereist om verbinding te maken met de netwerk eindpunten die door de PowerShell Gallery worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5d5b4-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="5d5b4-112">Zorg ervoor dat u met uw netwerk toegangs beleid verbinding kunt maken met de volgende eind punten.</span><span class="sxs-lookup"><span data-stu-id="5d5b4-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="5d5b4-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="5d5b4-113">oneget.org</span></span>
- <span data-ttu-id="5d5b4-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="5d5b4-114">go.microsoft.com</span></span>
- <span data-ttu-id="5d5b4-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="5d5b4-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="5d5b4-116">www.powershellgallery.com</span><span class="sxs-lookup"><span data-stu-id="5d5b4-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="5d5b4-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="5d5b4-117">devopsgallerystorage.blob.core.windows.net</span></span>
