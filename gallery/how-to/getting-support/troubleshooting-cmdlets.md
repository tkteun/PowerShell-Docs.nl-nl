---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Cmdlets voor het oplossen van problemen
ms.openlocfilehash: e8890cb6bbe661b8524d83cabf91483acbde8095
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219824"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="6a1b7-103">Cmdlets voor het oplossen van problemen</span><span class="sxs-lookup"><span data-stu-id="6a1b7-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="6a1b7-104">Het oplossen van ' Waarschuwing: pakket de pakketnaam kan niet worden gedownload ' probleem?</span><span class="sxs-lookup"><span data-stu-id="6a1b7-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="6a1b7-105">Het is bekend dat Install-Module of Update soms op sommige computers mislukt.</span><span class="sxs-lookup"><span data-stu-id="6a1b7-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="6a1b7-106">Op basis van ons onderzoek, is het iets te maken met de netwerkverbinding.</span><span class="sxs-lookup"><span data-stu-id="6a1b7-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="6a1b7-107">Onlangs is bijgewerkt NuGet provider zodat het op betrouwbare wijze pakketten kan downloaden.</span><span class="sxs-lookup"><span data-stu-id="6a1b7-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="6a1b7-108">U kunt de laatste build van NuGet-provider installeren en vervolgens installeren of bijwerken van de module in onderstaande instructies volgen.</span><span class="sxs-lookup"><span data-stu-id="6a1b7-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="6a1b7-109">We gaan 'Azure'-module gebruiken als het onderstaande voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="6a1b7-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```