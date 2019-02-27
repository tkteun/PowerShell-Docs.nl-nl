---
title: Modules en -modules | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849957"
---
# <a name="modules-and-snap-ins"></a>Modules en snap-ins

Cmdlets kunnen worden toegevoegd aan een sessie met modules (die door Windows PowerShell 2.0) of modules. Wanneer de cmdlet is toegevoegd aan de sessie die via een programma kan worden uitgevoerd op het door de hosttoepassing van een of interactief op de opdrachtregel.

U wordt aangeraden dat u modules als de leveringsmethode gebruiken voor cmdlets toe te voegen aan een sessie voor de volgende redenen:

- Modules kunnen u cmdlets toevoegen door het laden van de assembly waarin de cmdlet is gedefinieerd. Er is niet nodig voor het implementeren van een klasse-module.

- Modules kunnen u andere resources, zoals variabelen, functies, scripts, typen en opmaak bestanden en meer toevoegen.

- -Modules kunnen alleen worden gebruikt voor de cmdlets en providers toevoegen aan de sessie.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-Module schrijven](../module/writing-a-windows-powershell-module.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
