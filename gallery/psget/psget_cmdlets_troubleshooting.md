---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="91f10-103">Het oplossen van ' Waarschuwing: pakket de pakketnaam kan niet worden gedownload ' probleem?</span><span class="sxs-lookup"><span data-stu-id="91f10-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="91f10-104">Het is bekend dat Install-Module of Update soms op sommige computers mislukt.</span><span class="sxs-lookup"><span data-stu-id="91f10-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="91f10-105">Op basis van ons onderzoek, is het iets te maken met de netwerkverbinding.</span><span class="sxs-lookup"><span data-stu-id="91f10-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="91f10-106">Onlangs is bijgewerkt NuGet provider zodat het op betrouwbare wijze pakketten kan downloaden.</span><span class="sxs-lookup"><span data-stu-id="91f10-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="91f10-107">U kunt de laatste build van NuGet-provider installeren en vervolgens installeren of bijwerken van de module in onderstaande instructies volgen.</span><span class="sxs-lookup"><span data-stu-id="91f10-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="91f10-108">We gaan 'Azure'-module gebruiken als het onderstaande voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="91f10-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

