---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="a8eb4-102">Updates voor FileInfo-object</span><span class="sxs-lookup"><span data-stu-id="a8eb4-102">Updates to FileInfo object</span></span>
<span data-ttu-id="a8eb4-103">Informatie over de bestandsversie misleidend kan zijn, met name in gevallen waarin het bestand is hersteld.</span><span class="sxs-lookup"><span data-stu-id="a8eb4-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="a8eb4-104">Deze versie van WMF 5.0 voegt nieuwe **FileVersionRaw** en **ProductVersionRaw** script eigenschappen FileInfo objecten.</span><span class="sxs-lookup"><span data-stu-id="a8eb4-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="a8eb4-105">Hier volgen de eigenschappen, zoals weergegeven voor powershell.exe (ervan uitgaande dat $pid is de ID van het PowerShell-proces):</span><span class="sxs-lookup"><span data-stu-id="a8eb4-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
