---
title: Help testen die kan worden bijgewerkt
ms.date: 09/12/2016
ms.openlocfilehash: 0602349f853fddd0cadae545eaf0302c150e3a28
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892962"
---
# <a name="how-to-test-updatable-help"></a>Help testen die kan worden bijgewerkt

In dit onderwerp worden benaderingen beschreven voor het testen van de Help-informatie voor een module.

## <a name="using-verbose-to-detect-errors"></a>Uitgebreide detectie gebruiken om fouten te detecteren

Nadat u het HelpInfo XML-bestand en de CAB-bestanden voor uw module hebt geüpload, test u de bestanden door de opdracht [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) uit te voeren met de para meter **uitgebreid** . De para meter **uitgebreid** `Update-Help` om de kritieke stappen in de acties te melden, van het lezen van de sleutel **HelpInfoUri** in het manifest van de module voor het valideren van de bestands typen in het uitgepakte CAB-bestand en het plaatsen van de bestanden in de taalspecifieke module directory.

Wanneer alle uitgebreide berichten zijn opgelost, voert u een `Update-Help` opdracht uit met de para meter **debug** .
Met deze para meter moeten eventuele resterende problemen worden gedetecteerd met de Help-bestanden die kunnen worden bijgewerkt.
