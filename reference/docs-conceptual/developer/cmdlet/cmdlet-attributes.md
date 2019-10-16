---
title: Cmdlet-kenmerken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359446"
---
# <a name="cmdlet-attributes"></a>Cmdlet-kenmerken

Windows Power shell definieert diverse kenmerken die u kunt gebruiken om algemene functionaliteit toe te voegen aan uw cmdlets zonder dat u deze functionaliteit in uw eigen code hoeft te implementeren. Dit omvat het cmdlet-kenmerk dat een Microsoft .NET Framework-klasse identificeert als een cmdlet-klasse, het kenmerk output type waarmee de .NET Framework typen worden opgegeven die worden geretourneerd door de cmdlet, het parameter kenmerk dat open bare eigenschappen identificeert als cmdlet para meters en nog veel meer.

## <a name="in-this-section"></a>In deze sectie

[Kenmerken in cmdlet-code](./attributes-in-cmdlet-code.md) Beschrijft het voor deel van het gebruik van kenmerken in de cmdlet-code.

[Kenmerk typen](./attribute-types.md) Hierin worden de verschillende kenmerken beschreven waarmee een cmdlet-klasse kan worden gedecoreerd.

[Alias kenmerk declaratie](./alias-attribute-declaration.md) Hierin wordt beschreven hoe u aliassen definieert voor de naam van een cmdlet-para meter.

[Kenmerk declaratie van cmdlet](./cmdlet-attribute-declaration.md) Hierin wordt beschreven hoe u een .NET Framework klasse als een cmdlet definieert.

[Referentie kenmerk declaratie](./credential-attribute-declaration.md) Hierin wordt beschreven hoe u ondersteuning toevoegt voor het converteren van teken reeks invoer naar een [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object.

[Output type kenmerk declaratie](./outputtype-attribute-declaration.md) Hierin wordt beschreven hoe u de .NET Framework typen opgeeft die door de cmdlet worden geretourneerd.

[Parameter kenmerk declaratie](./parameter-attribute-declaration.md) Hierin wordt beschreven hoe u de para meters van een cmdlet definieert.

[ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md) Hierin wordt beschreven hoe u definieert hoeveel argumenten zijn toegestaan voor een para meter.

[ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md) Hierin wordt beschreven hoe u de lengte (in tekens) van een parameter argument definieert.

[ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md) Hierin wordt beschreven hoe u de geldige patronen voor een parameter argument definieert.

[ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md) Hierin wordt beschreven hoe u het geldige bereik voor een parameter argument definieert.

[Verklaring van de kenmerkset validate](./validateset-attribute-declaration.md) Hierin wordt beschreven hoe u de mogelijke waarden voor een parameter argument definieert.

## <a name="reference"></a>Verwijzing

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
