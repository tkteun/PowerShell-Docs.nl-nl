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
# <a name="updates-to-fileinfo-object"></a>Updates voor FileInfo-object
Informatie over de bestandsversie kan misleidend zijn, met name in gevallen waar het bestand is hersteld. Deze versie van WMF 5.0 voegt nieuwe **FileVersionRaw** en **ProductVersionRaw** script eigenschappen voor FileInfo-objecten. Hier zijn de eigenschappen als worden weergegeven voor de powershell.exe (ervan uitgaande dat $pid is de ID van de PowerShell-proces):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
