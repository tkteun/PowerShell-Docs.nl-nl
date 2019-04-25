---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 5280ef5ff95679dc8721be8f5f81031a4ffe796f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085235"
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="9974d-102">Updates voor FileInfo-object</span><span class="sxs-lookup"><span data-stu-id="9974d-102">Updates to FileInfo object</span></span>
<span data-ttu-id="9974d-103">Informatie over de bestandsversie kan misleidend zijn, met name in gevallen waar het bestand is hersteld.</span><span class="sxs-lookup"><span data-stu-id="9974d-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="9974d-104">Deze versie van WMF 5.0 voegt nieuwe **FileVersionRaw** en **ProductVersionRaw** script eigenschappen voor FileInfo-objecten.</span><span class="sxs-lookup"><span data-stu-id="9974d-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="9974d-105">Hier zijn de eigenschappen als worden weergegeven voor de powershell.exe (ervan uitgaande dat $pid is de ID van de PowerShell-proces):</span><span class="sxs-lookup"><span data-stu-id="9974d-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
