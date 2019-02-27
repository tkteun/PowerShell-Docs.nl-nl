---
title: Filter invoerparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845736"
---
# <a name="input-filter-parameters"></a>Filterparameters voor invoer

Een cmdlet kunt definiëren `Filter`, `Include`, en `Exclude` parameters die de set invoer objecten die gevolgen heeft voor de cmdlet filteren.

Normaal gesproken de set invoer objecten wordt opgegeven door een `InputObject`, `Path`, of `Name` parameter. Bijvoorbeeld, een cmdlet kunt hebben een `Path` parameter meerdere paden accepteert met jokertekens en elk pad verwijst naar een invoer-object. Samen, gebruikt de `Filter`, `Include`, en `Exclude` verdere parameters in aanmerking komen de paden die de cmdlet werkt op telkens wanneer de toepassing wordt aangeroepen.

## <a name="include-and-exclude-parameters"></a>Opnemen en uitsluiten van Parameters

De `Include` en `Exclude` parameters identificeren de objecten die zijn opgenomen of uitgesloten van de set invoer objecten die zijn doorgegeven aan de cmdlet. Deze parameters gebruiken wanneer u het filter kan worden uitgedrukt in de standard wildcard-taal. (Zie voor meer informatie over jokertekens [ondersteunt jokertekens in de Cmdlet-Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) De `Include` parameter bevat alle objecten waarvan de namen overeenkomen met het filter opgenomen. De `Exclude` parameter niet van toepassing op alle objecten waarvan de namen overeenkomen met het filter.

## <a name="filter-parameter"></a>Filter Parameter

De `Filter` parameter geeft u een filter op dat niet wordt uitgedrukt in de standard wildcard-taal. Bijvoorbeeld, Active Directory Service Interfaces (ADSI) of SQL-filters kunnen worden doorgegeven aan de cmdlet via de `Filter` parameter. Deze filters worden in de beschikbare Windows PowerShell cmdlets, opgegeven door de Windows PowerShell-providers die gebruikmaken van de cmdlet voor toegang tot een gegevensarchief. Elke provider definieert doorgaans een eigen filter.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Als u geen Set invoer objecten opgeeft filteren

Als u geen set invoer objecten opgeeft, betekent dit doorgaans om te filteren op basis van alle objecten. Zie voor meer informatie,[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)