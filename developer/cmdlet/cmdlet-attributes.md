---
title: Kenmerken van de cmdlet | Microsoft Docs
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
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845351"
---
# <a name="cmdlet-attributes"></a>Cmdlet-kenmerken

Windows PowerShell definieert verschillende kenmerken die u algemene functionaliteit toevoegen aan uw cmdlets kunt zonder dat de functionaliteit in uw eigen code te implementeren. Dit omvat het Cmdlet-kenmerk dat een Microsoft .NET Framework-klasse als een cmdlet-klasse, het OutputType-kenmerk dat Hiermee geeft u de .NET Framework-typen die wordt geretourneerd door de cmdlet, de Parameter-kenmerk dat verwijst naar openbare eigenschappen als cmdlet identificeert parameters, en meer.

## <a name="in-this-section"></a>In deze sectie

[Kenmerken in de Code van de Cmdlet](./attributes-in-cmdlet-code.md) beschrijving van het voordeel van het gebruik van kenmerken in de code van de cmdlet.

[Kenmerken van het type](./attribute-types.md) beschrijft de verschillende kenmerken die de klasse van een cmdlet kunnen opmaken.

[Alias kenmerkdeclaratie](./alias-attribute-declaration.md) wordt beschreven hoe u voor het definiëren van aliassen voor de naam van een cmdlet-parameter.

[Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md) wordt beschreven hoe u een .NET Framework-klasse definiëren als een cmdlet.

[Referentie-kenmerkdeclaratie](./credential-attribute-declaration.md) wordt beschreven hoe u het toevoegen van ondersteuning voor het converteren van de tekenreeksinvoer van de in een [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.

[OutputType kenmerk declaratie](./outputtype-attribute-declaration.md) wordt beschreven hoe u om op te geven van de .NET Framework-typen die wordt geretourneerd door de cmdlet.

[Kenmerk parameterdeclaratie](./parameter-attribute-declaration.md) wordt beschreven hoe u de parameters van een cmdlet definieert.

[ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md) wordt beschreven hoe u voor het definiëren van het aantal argumenten voor een parameter zijn toegestaan.

[ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md) wordt beschreven hoe u de lengte (in tekens) van het parameterargument van een definiëren.

[ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md) wordt beschreven hoe u de geldige patronen voor het parameterargument van een definiëren.

[ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md) wordt beschreven hoe u het geldige bereik voor het parameterargument van een definiëren.

[ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md) wordt beschreven hoe u de mogelijke waarden voor het parameterargument van een definiëren.

## <a name="reference"></a>Verwijzing

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
