---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 6356902193fc6ec651b2f7e53f8885cb59f17542
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="1758b-102">Updates voor FileInfo-object</span><span class="sxs-lookup"><span data-stu-id="1758b-102">Updates to FileInfo object</span></span>
<span data-ttu-id="1758b-103">Informatie over de bestandsversie misleidend kan zijn, met name in gevallen waarin het bestand is hersteld.</span><span class="sxs-lookup"><span data-stu-id="1758b-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="1758b-104">Deze versie van WMF 5.0 voegt nieuwe **FileVersionRaw** en **ProductVersionRaw** script eigenschappen FileInfo objecten.</span><span class="sxs-lookup"><span data-stu-id="1758b-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="1758b-105">Hier volgen de eigenschappen, zoals weergegeven voor powershell.exe (ervan uitgaande dat $pid is de ID van het PowerShell-proces):</span><span class="sxs-lookup"><span data-stu-id="1758b-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117