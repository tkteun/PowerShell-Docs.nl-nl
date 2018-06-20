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
# <a name="troubleshooting-cmdlets"></a>Cmdlets voor het oplossen van problemen

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Het oplossen van ' Waarschuwing: pakket de pakketnaam kan niet worden gedownload ' probleem?

Het is bekend dat Install-Module of Update soms op sommige computers mislukt.
Op basis van ons onderzoek, is het iets te maken met de netwerkverbinding.
Onlangs is bijgewerkt NuGet provider zodat het op betrouwbare wijze pakketten kan downloaden.
U kunt de laatste build van NuGet-provider installeren en vervolgens installeren of bijwerken van de module in onderstaande instructies volgen.
We gaan 'Azure'-module gebruiken als het onderstaande voorbeeld.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```