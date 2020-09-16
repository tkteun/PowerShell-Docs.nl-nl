---
title: Cmdlet-kenmerken | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.openlocfilehash: f22c2882fbe5b2f51ca5ea218b921192b0a7d41f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784517"
---
# <a name="cmdlet-attributes"></a>Cmdlet-kenmerken

Windows Power shell definieert diverse kenmerken die u kunt gebruiken om algemene functionaliteit toe te voegen aan uw cmdlets zonder dat u deze functionaliteit in uw eigen code hoeft te implementeren. Dit omvat het cmdlet-kenmerk dat een Microsoft .NET Framework-klasse identificeert als een cmdlet-klasse, het kenmerk output type waarmee de .NET Framework typen worden opgegeven die door de cmdlet worden geretourneerd, het parameter kenmerk dat open bare eigenschappen identificeert als cmdlet-para meters en meer.

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

## <a name="reference"></a>Naslaginformatie

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
