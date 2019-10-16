---
title: Invoer filter parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355494"
---
# <a name="input-filter-parameters"></a>Filterparameters voor invoer

Een cmdlet kan `Filter`, `Include`-en `Exclude` para meters definiëren waarmee de set invoer objecten wordt gefilterd waarop de cmdlet van invloed is.

Normaal gesp roken wordt de set invoer objecten opgegeven met een `InputObject`, `Path` of de para meter `Name`. Een cmdlet kan bijvoorbeeld een para meter `Path` hebben die meerdere paden accepteert met behulp van joker tekens, en elk pad wijst naar een invoer object. In combi natie met de para meters `Filter`, `Include` en `Exclude` worden de paden die de cmdlet op elke keer dat deze wordt aangeroepen, verder gekwalificeerd.

## <a name="include-and-exclude-parameters"></a>Para meters opnemen en uitsluiten

De para meters `Include` en `Exclude` identificeren de objecten die worden opgenomen in of uitgesloten van de set invoer objecten die worden door gegeven aan de cmdlet. Gebruik deze para meters wanneer het filter kan worden weer gegeven in de standaard taal joker tekens. (Zie het [ondersteunings joker tekens in cmdlet-para meters](./supporting-wildcard-characters-in-cmdlet-parameters.md)voor meer informatie over joker tekens.) De para meter `Include` bevat alle objecten waarvan de namen overeenkomen met het insluitings filter. Met de para meter `Exclude` worden alle objecten uitgesloten waarvan de namen overeenkomen met het filter.

## <a name="filter-parameter"></a>Filter parameter

De para meter `Filter` geeft een filter op dat niet wordt weer gegeven in de standaard taal voor joker tekens. Active Directory Service interfaces (ADSI) of SQL-filters kunnen bijvoorbeeld worden door gegeven aan de cmdlet via de para meter `Filter`. In de cmdlets van Windows Power shell worden deze filters opgegeven door de Windows Power shell-providers die de cmdlet gebruiken om toegang te krijgen tot een gegevens archief. Elke provider definieert meestal een eigen filter.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filteren als er geen set invoer objecten is opgegeven

Als er geen set invoer objecten is opgegeven, betekent dit meestal dat u wilt filteren op alle objecten. Zie[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)voor meer informatie.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)