---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: Problemen met cmdlets oplossen
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329048"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="ec8d9-103">Problemen met cmdlets oplossen</span><span class="sxs-lookup"><span data-stu-id="ec8d9-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="ec8d9-104">Oplossen van waarschuwingen: Het probleem van de pakket naam kan niet worden gedownload</span><span class="sxs-lookup"><span data-stu-id="ec8d9-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="ec8d9-105">Er wordt gemeld dat `Install-Module` of `Update-Module` soms op sommige computers mislukt.</span><span class="sxs-lookup"><span data-stu-id="ec8d9-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="ec8d9-106">Op basis van ons onderzoek is het iets te doen met de netwerk verbinding.</span><span class="sxs-lookup"><span data-stu-id="ec8d9-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="ec8d9-107">Onlangs hebben we de NuGet-provider bijgewerkt zodat pakketten betrouwbaar kunnen worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="ec8d9-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="ec8d9-108">U kunt de onderstaande instructies volgen om de meest recente build van NuGet-provider te installeren en vervolgens uw module te installeren of bij te werken.</span><span class="sxs-lookup"><span data-stu-id="ec8d9-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="ec8d9-109">We gebruiken de module ' Azure ' als voor beeld hieronder.</span><span class="sxs-lookup"><span data-stu-id="ec8d9-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
