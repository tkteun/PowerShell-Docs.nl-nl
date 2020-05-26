---
title: De Help-informatie die kan worden bijgewerkt, testen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: 8dd3770a60ca56634ad1eb1ac8cf89d96c975c90
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810825"
---
# <a name="how-to-test-updatable-help"></a>Help testen die kan worden bijgewerkt

In dit onderwerp worden benaderingen beschreven voor het testen van de Help-informatie voor een module.

## <a name="using-verbose-to-detect-errors"></a>Uitgebreide detectie gebruiken om fouten te detecteren

Nadat u het HelpInfo XML-bestand en de CAB-bestanden voor uw module hebt geüpload, test u de bestanden door de opdracht [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) uit te voeren met de para meter **uitgebreid** . De para meter **uitgebreid** `Update-Help` om de kritieke stappen in de acties te melden, van het lezen van de sleutel **HelpInfoUri** in het manifest van de module voor het valideren van de bestands typen in het uitgepakte CAB-bestand en het plaatsen van de bestanden in de taalspecifieke module directory.

Wanneer alle uitgebreide berichten zijn opgelost, voert u een `Update-Help` opdracht uit met de para meter **debug** . Met deze para meter moeten eventuele resterende problemen worden gedetecteerd met de Help-bestanden die kunnen worden bijgewerkt.
