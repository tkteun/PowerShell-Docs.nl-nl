---
ms.date: 12/01/2020
title: Problemen met cmdlets oplossen
description: In dit artikel vindt u informatie en stappen voor het oplossen van problemen met behulp van de PowerShell Gallery
ms.openlocfilehash: 980da8ea7b8a09513f33a9939d512c437b755d8d
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913315"
---
# <a name="troubleshooting-cmdlets"></a>Problemen met cmdlets oplossen

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Het oplossen van ' waarschuwing: pakket ' kan de pakket naam niet downloaden '

Er wordt gemeld dat `Install-Module` of `Update-Module` soms op sommige computers mislukt. Op basis van ons onderzoek is het iets te doen met de netwerk verbinding. Onlangs hebben we de NuGet-provider bijgewerkt zodat pakketten betrouwbaar kunnen worden gedownload. U kunt de onderstaande instructies volgen om de meest recente build van NuGet-provider te installeren en vervolgens uw module te installeren of bij te werken. We gebruiken de module ' Azure ' als voor beeld hieronder.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a>Vereiste netwerk eindpunten

Voor de cmdlets install en update is Internet toegang vereist om verbinding te maken met de netwerk eindpunten die door de PowerShell Gallery worden gebruikt. Zorg ervoor dat u met uw netwerk toegangs beleid verbinding kunt maken met de volgende eind punten.

- `psg-prod-eastus.azureedge.net` -CDN-hostnaam
- `az818661.vo.msecnd.net` -CDN-hostnaam
- `devopsgallerystorage.blob.core.windows.net` -hostnaam van opslag account
- `*.powershellgallery.com` -website
- `go.microsoft.com` -omleidings service

> [!NOTE]
> Cmdlets die communiceren met de PowerShell Gallery, kunnen mislukken met onverwachte fouten als er een storing optreedt in de PowerShell Gallery Services. Als u de huidige status van de PowerShell Gallery wilt zien, gaat u naar de pagina [PowerShell Gallery status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) op github.
