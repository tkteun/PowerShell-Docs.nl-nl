---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, Power shell, cmdlet, psget
title: Problemen met cmdlets oplossen
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329048"
---
# <a name="troubleshooting-cmdlets"></a>Problemen met cmdlets oplossen

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Oplossen van waarschuwingen: Het probleem van de pakket naam kan niet worden gedownload

Er wordt gemeld dat `Install-Module` of `Update-Module` soms op sommige computers mislukt.
Op basis van ons onderzoek is het iets te doen met de netwerk verbinding.
Onlangs hebben we de NuGet-provider bijgewerkt zodat pakketten betrouwbaar kunnen worden gedownload.
U kunt de onderstaande instructies volgen om de meest recente build van NuGet-provider te installeren en vervolgens uw module te installeren of bij te werken.
We gebruiken de module ' Azure ' als voor beeld hieronder.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
