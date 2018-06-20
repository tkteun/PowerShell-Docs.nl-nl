---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225637"
---
# <a name="updates-to-fileinfo-object"></a>Updates voor FileInfo-object
Informatie over de bestandsversie misleidend kan zijn, met name in gevallen waarin het bestand is hersteld. Deze versie van WMF 5.0 voegt nieuwe **FileVersionRaw** en **ProductVersionRaw** script eigenschappen FileInfo objecten. Hier volgen de eigenschappen, zoals weergegeven voor powershell.exe (ervan uitgaande dat $pid is de ID van het PowerShell-proces):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
