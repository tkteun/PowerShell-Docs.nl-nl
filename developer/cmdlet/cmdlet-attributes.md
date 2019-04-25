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
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068603"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="01e36-102">Cmdlet-kenmerken</span><span class="sxs-lookup"><span data-stu-id="01e36-102">Cmdlet Attributes</span></span>

<span data-ttu-id="01e36-103">Windows PowerShell definieert verschillende kenmerken die u algemene functionaliteit toevoegen aan uw cmdlets kunt zonder dat de functionaliteit in uw eigen code te implementeren.</span><span class="sxs-lookup"><span data-stu-id="01e36-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="01e36-104">Dit omvat het Cmdlet-kenmerk dat een Microsoft .NET Framework-klasse als een cmdlet-klasse, het OutputType-kenmerk dat Hiermee geeft u de .NET Framework-typen die wordt geretourneerd door de cmdlet, de Parameter-kenmerk dat verwijst naar openbare eigenschappen als cmdlet identificeert parameters, en meer.</span><span class="sxs-lookup"><span data-stu-id="01e36-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="01e36-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="01e36-105">In This Section</span></span>

<span data-ttu-id="01e36-106">[Kenmerken in de Code van de Cmdlet](./attributes-in-cmdlet-code.md) beschrijving van het voordeel van het gebruik van kenmerken in de code van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01e36-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="01e36-107">[Kenmerken van het type](./attribute-types.md) beschrijft de verschillende kenmerken die de klasse van een cmdlet kunnen opmaken.</span><span class="sxs-lookup"><span data-stu-id="01e36-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="01e36-108">[Alias kenmerkdeclaratie](./alias-attribute-declaration.md) wordt beschreven hoe u voor het definiëren van aliassen voor de naam van een cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="01e36-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="01e36-109">[Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md) wordt beschreven hoe u een .NET Framework-klasse definiëren als een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01e36-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="01e36-110">[Referentie-kenmerkdeclaratie](./credential-attribute-declaration.md) wordt beschreven hoe u het toevoegen van ondersteuning voor het converteren van de tekenreeksinvoer van de in een [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span><span class="sxs-lookup"><span data-stu-id="01e36-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="01e36-111">[OutputType kenmerk declaratie](./outputtype-attribute-declaration.md) wordt beschreven hoe u om op te geven van de .NET Framework-typen die wordt geretourneerd door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01e36-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="01e36-112">[Kenmerk parameterdeclaratie](./parameter-attribute-declaration.md) wordt beschreven hoe u de parameters van een cmdlet definieert.</span><span class="sxs-lookup"><span data-stu-id="01e36-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="01e36-113">[ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md) wordt beschreven hoe u voor het definiëren van het aantal argumenten voor een parameter zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="01e36-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="01e36-114">[ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md) wordt beschreven hoe u de lengte (in tekens) van het parameterargument van een definiëren.</span><span class="sxs-lookup"><span data-stu-id="01e36-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="01e36-115">[ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md) wordt beschreven hoe u de geldige patronen voor het parameterargument van een definiëren.</span><span class="sxs-lookup"><span data-stu-id="01e36-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="01e36-116">[ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md) wordt beschreven hoe u het geldige bereik voor het parameterargument van een definiëren.</span><span class="sxs-lookup"><span data-stu-id="01e36-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="01e36-117">[ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md) wordt beschreven hoe u de mogelijke waarden voor het parameterargument van een definiëren.</span><span class="sxs-lookup"><span data-stu-id="01e36-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="01e36-118">Verwijzing</span><span class="sxs-lookup"><span data-stu-id="01e36-118">Reference</span></span>

[<span data-ttu-id="01e36-119">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="01e36-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
