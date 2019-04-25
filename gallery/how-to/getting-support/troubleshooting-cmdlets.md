---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Cmdlets voor het oplossen van problemen
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084178"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="17171-103">Cmdlets voor het oplossen van problemen</span><span class="sxs-lookup"><span data-stu-id="17171-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="17171-104">Over het oplossen van ' Waarschuwing: Pakket met de pakketnaam kan niet downloaden"probleem</span><span class="sxs-lookup"><span data-stu-id="17171-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="17171-105">Dit apparaat gerapporteerd die `Install-Module` of `Update-Module` soms op sommige computers mislukt.</span><span class="sxs-lookup"><span data-stu-id="17171-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="17171-106">Op basis van ons onderzoek, is het iets te maken met de netwerkverbinding.</span><span class="sxs-lookup"><span data-stu-id="17171-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="17171-107">Onlangs bijgewerkt we NuGet-provider zodat deze op betrouwbare wijze pakketten kan downloaden.</span><span class="sxs-lookup"><span data-stu-id="17171-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="17171-108">U kunt de meest recente versie van NuGet-provider installeren en vervolgens installeren of bijwerken van uw module in onderstaande instructies volgen.</span><span class="sxs-lookup"><span data-stu-id="17171-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="17171-109">We gaan 'Azure'-module gebruiken als het onderstaande voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="17171-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
