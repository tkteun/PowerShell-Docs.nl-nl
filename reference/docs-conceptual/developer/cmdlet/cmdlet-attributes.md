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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359446"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="62b4c-102">Cmdlet-kenmerken</span><span class="sxs-lookup"><span data-stu-id="62b4c-102">Cmdlet Attributes</span></span>

<span data-ttu-id="62b4c-103">Windows Power shell definieert diverse kenmerken die u kunt gebruiken om algemene functionaliteit toe te voegen aan uw cmdlets zonder dat u deze functionaliteit in uw eigen code hoeft te implementeren.</span><span class="sxs-lookup"><span data-stu-id="62b4c-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="62b4c-104">Dit omvat het cmdlet-kenmerk dat een Microsoft .NET Framework-klasse identificeert als een cmdlet-klasse, het kenmerk output type waarmee de .NET Framework typen worden opgegeven die worden geretourneerd door de cmdlet, het parameter kenmerk dat open bare eigenschappen identificeert als cmdlet para meters en nog veel meer.</span><span class="sxs-lookup"><span data-stu-id="62b4c-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="62b4c-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="62b4c-105">In This Section</span></span>

<span data-ttu-id="62b4c-106">[Kenmerken in cmdlet-code](./attributes-in-cmdlet-code.md) Beschrijft het voor deel van het gebruik van kenmerken in de cmdlet-code.</span><span class="sxs-lookup"><span data-stu-id="62b4c-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="62b4c-107">[Kenmerk typen](./attribute-types.md) Hierin worden de verschillende kenmerken beschreven waarmee een cmdlet-klasse kan worden gedecoreerd.</span><span class="sxs-lookup"><span data-stu-id="62b4c-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="62b4c-108">[Alias kenmerk declaratie](./alias-attribute-declaration.md) Hierin wordt beschreven hoe u aliassen definieert voor de naam van een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="62b4c-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="62b4c-109">[Kenmerk declaratie van cmdlet](./cmdlet-attribute-declaration.md) Hierin wordt beschreven hoe u een .NET Framework klasse als een cmdlet definieert.</span><span class="sxs-lookup"><span data-stu-id="62b4c-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="62b4c-110">[Referentie kenmerk declaratie](./credential-attribute-declaration.md) Hierin wordt beschreven hoe u ondersteuning toevoegt voor het converteren van teken reeks invoer naar een [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object.</span><span class="sxs-lookup"><span data-stu-id="62b4c-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="62b4c-111">[Output type kenmerk declaratie](./outputtype-attribute-declaration.md) Hierin wordt beschreven hoe u de .NET Framework typen opgeeft die door de cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="62b4c-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="62b4c-112">[Parameter kenmerk declaratie](./parameter-attribute-declaration.md) Hierin wordt beschreven hoe u de para meters van een cmdlet definieert.</span><span class="sxs-lookup"><span data-stu-id="62b4c-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="62b4c-113">[ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md) Hierin wordt beschreven hoe u definieert hoeveel argumenten zijn toegestaan voor een para meter.</span><span class="sxs-lookup"><span data-stu-id="62b4c-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="62b4c-114">[ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md) Hierin wordt beschreven hoe u de lengte (in tekens) van een parameter argument definieert.</span><span class="sxs-lookup"><span data-stu-id="62b4c-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="62b4c-115">[ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md) Hierin wordt beschreven hoe u de geldige patronen voor een parameter argument definieert.</span><span class="sxs-lookup"><span data-stu-id="62b4c-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="62b4c-116">[ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md) Hierin wordt beschreven hoe u het geldige bereik voor een parameter argument definieert.</span><span class="sxs-lookup"><span data-stu-id="62b4c-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="62b4c-117">[Verklaring van de kenmerkset validate](./validateset-attribute-declaration.md) Hierin wordt beschreven hoe u de mogelijke waarden voor een parameter argument definieert.</span><span class="sxs-lookup"><span data-stu-id="62b4c-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="62b4c-118">Verwijzing</span><span class="sxs-lookup"><span data-stu-id="62b4c-118">Reference</span></span>

[<span data-ttu-id="62b4c-119">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="62b4c-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
