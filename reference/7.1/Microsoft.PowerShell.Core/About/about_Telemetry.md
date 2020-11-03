---
description: Hierin wordt de telemetrie die is verzameld in Power shell beschreven en wordt uitgelegd hoe u dit kunt afmelden.
keywords: powershell
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: ef921d0feefe277c2832c0a459ae150c9a6b4acb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252514"
---
# <a name="about-telemetry"></a>Over telemetrie

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin wordt de telemetrie die is verzameld in Power shell beschreven en wordt uitgelegd hoe u dit kunt afmelden.

## <a name="long-description"></a>LANGE BESCHRIJVING

Power shell verzendt elementaire telemetriegegevens naar micro soft.
Met deze gegevens kunnen we beter inzicht krijgen in de omgevingen waarin Power shell wordt gebruikt en kunnen we de prioriteit van nieuwe functies en oplossingen bepalen.
De volgende telemetriegegevens worden vastgelegd:

- Aantal Power shell wordt gestart op type (API versus console)
- Aantal unieke Power shell-gebruik
- Aantal van de volgende uitvoerings typen:
  - Toepassing (systeem eigen opdrachten)
  - ExternalScript
  - Script
  - Functie
  - Cmdlet
- Aantal ingeschakelde experimentele functies van micro soft of experimentele functies die worden geleverd met Power shell
- Aantal gehoste sessies
- Aantal geladen micro soft-modules

Deze gegevens omvatten de naam van het besturings systeem, de versie van het besturings systeem, de Power shell-versie en het distributie kanaal.

Als u deze telemetrie wilt afmelden, stelt u de omgevings variabele POWERSHELL_TELEMETRY_OPTOUT in op waar, ja of 1.

