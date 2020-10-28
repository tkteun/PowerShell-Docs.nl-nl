---
ms.date: 06/12/2017
title: Problemen met cmdlets oplossen
description: In dit artikel vindt u informatie en stappen voor het oplossen van problemen met behulp van de PowerShell Gallery
ms.openlocfilehash: db9e58c185c6f3bca26ff3639af85fa2dba48909
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661066"
---
# <a name="troubleshooting-cmdlets"></a>Problemen met cmdlets oplossen

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Het oplossen van ' waarschuwing: pakket ' kan de pakket naam niet downloaden '

Er wordt gemeld dat `Install-Module` of `Update-Module` soms op sommige computers mislukt. Op basis van ons onderzoek is het iets te doen met de netwerk verbinding. Onlangs hebben we de NuGet-provider bijgewerkt zodat pakketten betrouwbaar kunnen worden gedownload. U kunt de onderstaande instructies volgen om de meest recente build van NuGet-provider te installeren en vervolgens uw module te installeren of bij te werken. We gebruiken de module ' Azure ' als voor beeld hieronder.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a>Vereiste netwerk eindpunten

Voor de cmdlets install en update is Internet toegang vereist om verbinding te maken met de netwerk eindpunten die door de PowerShell Gallery worden gebruikt. Zorg ervoor dat u met uw netwerk toegangs beleid verbinding kunt maken met de volgende eind punten.

- oneget.org
- go.microsoft.com
- az818661.vo.msecnd.net
- www.powershellgallery.com
- devopsgallerystorage.blob.core.windows.net
