---
title: Modules en modules | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: b3d8209ea7e3e8353e73ebce1531991ec9519c74
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811161"
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
