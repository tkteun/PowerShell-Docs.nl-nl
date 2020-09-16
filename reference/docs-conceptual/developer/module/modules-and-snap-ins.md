---
title: Modules en modules | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07cdc55fd6d1462130f1a81deb30056623a525e6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787305"
---
# <a name="modules-and-snap-ins"></a>Modules en snap-ins

Cmdlets kunnen worden toegevoegd aan een sessie met behulp van modules (geïntroduceerd door Windows Power Shell 2,0) of modules. Zodra de cmdlet is toegevoegd aan de sessie, kan de toepassing programmatisch worden uitgevoerd door een hosttoepassing of interactief op de opdracht regel.

U wordt aangeraden modules te gebruiken als de leverings methode voor het toevoegen van cmdlets aan een sessie om de volgende redenen:

- Met modules kunt u cmdlets toevoegen door de assembly te laden waarin de cmdlet is gedefinieerd. U hoeft geen module te implementeren.

- Met modules kunt u andere resources toevoegen, zoals variabelen, functies, scripts, typen en indelings bestanden, en meer.

- Modules kunnen alleen worden gebruikt om cmdlets en providers toe te voegen aan de sessie.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-module schrijven](writing-a-windows-powershell-module.md)

[Een Windows PowerShell-cmdlet schrijven](../cmdlet/cmdlet-overview.md)
