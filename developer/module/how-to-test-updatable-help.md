---
title: Bij te werken Help testen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082323"
---
# <a name="how-to-test-updatable-help"></a>Help testen die kan worden bijgewerkt

Dit onderwerp beschrijft de methoden voor het testen van de bij te werken Help voor een module.

## <a name="using-verbose-to-detect-errors"></a>Met behulp van uitgebreide voor het detecteren van fouten

Na het uploaden van de HelpInfo XML-bestand en het CAB-bestanden voor de module, kunt u de bestanden testen door het uitvoeren van een [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) opdracht met de **uitgebreid** parameter. De **uitgebreid** parameter stuurt `Update-Help` voor het rapporteren van de belangrijke stappen in de acties van lezen de **HelpInfoUri** sleutel in de module-manifest voor het valideren van de bestandstypen in de uitgepakte CAB-bestand en de bestanden in de modulemap taalspecifieke plaatsen.

Wanneer alle uitgebreide berichten opgelost worden, voert een `Update-Help` opdracht met de **Debug** parameter. Deze parameter moet eventuele resterende problemen met de bestanden bij te werken Help detecteren.