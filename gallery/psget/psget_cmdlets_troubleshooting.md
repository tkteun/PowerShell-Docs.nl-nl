---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: bc49dc78b8205d1194ddfe4bdca98b3e681860bd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="5f16b-103">Het oplossen van ' Waarschuwing: pakket de pakketnaam kan niet worden gedownload ' probleem?</span><span class="sxs-lookup"><span data-stu-id="5f16b-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="5f16b-104">Het is bekend dat Install-Module of Update soms op sommige computers mislukt.</span><span class="sxs-lookup"><span data-stu-id="5f16b-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="5f16b-105">Op basis van ons onderzoek, is het iets te maken met de netwerkverbinding.</span><span class="sxs-lookup"><span data-stu-id="5f16b-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="5f16b-106">Onlangs is bijgewerkt NuGet provider zodat het op betrouwbare wijze pakketten kan downloaden.</span><span class="sxs-lookup"><span data-stu-id="5f16b-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="5f16b-107">U kunt de laatste build van NuGet-provider installeren en vervolgens installeren of bijwerken van de module in onderstaande instructies volgen.</span><span class="sxs-lookup"><span data-stu-id="5f16b-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="5f16b-108">We gaan 'Azure'-module gebruiken als het onderstaande voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="5f16b-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```