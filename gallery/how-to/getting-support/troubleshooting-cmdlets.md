---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Cmdlets voor het oplossen van problemen
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686549"
---
# <a name="troubleshooting-cmdlets"></a>Cmdlets voor het oplossen van problemen

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Over het oplossen van ' Waarschuwing: Pakket met de pakketnaam kan niet downloaden"probleem

Dit apparaat gerapporteerd die `Install-Module` of `Update-Module` soms op sommige computers mislukt.
Op basis van ons onderzoek, is het iets te maken met de netwerkverbinding.
Onlangs bijgewerkt we NuGet-provider zodat deze op betrouwbare wijze pakketten kan downloaden.
U kunt de meest recente versie van NuGet-provider installeren en vervolgens installeren of bijwerken van uw module in onderstaande instructies volgen.
We gaan 'Azure'-module gebruiken als het onderstaande voorbeeld.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
