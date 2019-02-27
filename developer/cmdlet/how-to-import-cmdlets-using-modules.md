---
title: Het importeren van Modules met Cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849012"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Cmdlets importeren met modules

In dit onderwerp wordt beschreven hoe u cmdlets in een Windows PowerShell-sessie met behulp van een binaire module importeren.

> [!NOTE]
> De leden van de modules kunnen opnemen cmdlets, providers, functies, variabelen, aliassen en nog veel meer. Alleen-cmdlets en providers bevatten-modules.

## <a name="how-to-load-cmdlets-using-a-module"></a>Het laden van cmdlets met behulp van een module

1. Maak een modulemap met dezelfde naam als de assemblybestand waarin de cmdlets worden geïmplementeerd. In deze procedure wordt de modulemap gemaakt de `system32` map.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Zorg ervoor dat de `PSModulePath` omgevingsvariabele bevat het pad naar de nieuwe modulemap. De map is standaard al toegevoegd aan de `PSModulePath` omgevingsvariabele.

3. Kopieer de cmdlet-assembly in de modulemap.

4. Voer de volgende opdracht uit om toe te voegen van de cmdlets met de sessie:

   `import-module [Module_Name]`

   Deze procedure kan worden gebruikt voor het testen van uw cmdlets. Alle cmdlets wordt toegevoegd in de assembly met de sessie. Zie voor meer informatie over de verschillende soorten modules, de verschillende manieren om te laden modules en het beperken van de elementen van een module die zijn geëxporteerd, [schrijven van een Windows PowerShell-Module](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Modules installeren](../module/installing-a-powershell-module.md)