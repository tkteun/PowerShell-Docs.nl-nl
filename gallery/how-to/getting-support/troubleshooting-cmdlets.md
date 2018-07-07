---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Cmdlets voor het oplossen van problemen
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892471"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="7ffd3-103">Cmdlets voor het oplossen van problemen</span><span class="sxs-lookup"><span data-stu-id="7ffd3-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="7ffd3-104">Over het oplossen van ' Waarschuwing: kan het pakket 'uw pakket name' niet downloaden "probleem</span><span class="sxs-lookup"><span data-stu-id="7ffd3-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="7ffd3-105">Dit apparaat gerapporteerd die `Install-Module` of `Update-Module` soms op sommige computers mislukt.</span><span class="sxs-lookup"><span data-stu-id="7ffd3-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="7ffd3-106">Op basis van ons onderzoek, is het iets te maken met de netwerkverbinding.</span><span class="sxs-lookup"><span data-stu-id="7ffd3-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="7ffd3-107">Onlangs bijgewerkt we NuGet-provider zodat deze op betrouwbare wijze pakketten kan downloaden.</span><span class="sxs-lookup"><span data-stu-id="7ffd3-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="7ffd3-108">U kunt de meest recente versie van NuGet-provider installeren en vervolgens installeren of bijwerken van uw module in onderstaande instructies volgen.</span><span class="sxs-lookup"><span data-stu-id="7ffd3-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="7ffd3-109">We gaan 'Azure'-module gebruiken als het onderstaande voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="7ffd3-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```