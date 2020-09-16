---
title: Invoer filter parameters | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ccaf6c4859d2a4f14866ec1252b999e90e1a830f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784041"
---
# <a name="input-filter-parameters"></a>Filterparameters voor invoer

Met een cmdlet kunt `Filter` u `Include` `Exclude` de para meters, en opgeven voor het filteren van de set invoer objecten die door de cmdlet worden beïnvloed.

Normaal gesp roken wordt de set invoer objecten opgegeven met een `InputObject` , `Path` of `Name` para meter. Een cmdlet kan bijvoorbeeld een `Path` para meter hebben die meerdere paden accepteert door gebruik te maken van joker tekens, en elk pad wijst naar een invoer object. Samen worden gebruikt, worden de `Filter` -, `Include` -en- `Exclude` para meters de paden die de cmdlet op elke keer dat deze wordt aangeroepen, verder gekwalificeerd.

## <a name="include-and-exclude-parameters"></a>Para meters opnemen en uitsluiten

De `Include` `Exclude` para meters en identificeren de objecten die zijn opgenomen of uitgesloten van de set invoer objecten die worden door gegeven aan de cmdlet. Gebruik deze para meters wanneer het filter kan worden weer gegeven in de standaard taal joker tekens. (Zie het [ondersteunings joker tekens in cmdlet-para meters](./supporting-wildcard-characters-in-cmdlet-parameters.md)voor meer informatie over joker tekens.) De `Include` para meter bevat alle objecten waarvan de namen overeenkomen met het insluitings filter. `Exclude`Met de para meter worden alle objecten uitgesloten waarvan de namen overeenkomen met het filter.

## <a name="filter-parameter"></a>Filter parameter

`Filter`Met de para meter wordt een filter opgegeven dat niet wordt weer gegeven in de standaard taal voor joker tekens. Active Directory Service interfaces (ADSI) of SQL-filters kunnen bijvoorbeeld worden door gegeven aan de cmdlet via de `Filter` para meter. In de cmdlets van Windows Power shell worden deze filters opgegeven door de Windows Power shell-providers die de cmdlet gebruiken om toegang te krijgen tot een gegevens archief. Elke provider definieert meestal een eigen filter.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filteren als er geen set invoer objecten is opgegeven

Als er geen set invoer objecten is opgegeven, betekent dit meestal dat u wilt filteren op alle objecten. Zie[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)voor meer informatie.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
