---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-kenmerken
description: Cmdlet-kenmerken
ms.openlocfilehash: 6a106f33cb34c6c33b88a981815543bc9af4e4ba
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653513"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="9923e-103">Cmdlet-kenmerken</span><span class="sxs-lookup"><span data-stu-id="9923e-103">Cmdlet Attributes</span></span>

<span data-ttu-id="9923e-104">Windows Power shell definieert diverse kenmerken die u kunt gebruiken om algemene functionaliteit toe te voegen aan uw cmdlets zonder dat u deze functionaliteit in uw eigen code hoeft te implementeren.</span><span class="sxs-lookup"><span data-stu-id="9923e-104">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="9923e-105">Dit omvat het cmdlet-kenmerk dat een Microsoft .NET Framework-klasse identificeert als een cmdlet-klasse, het kenmerk output type waarmee de .NET Framework typen worden opgegeven die door de cmdlet worden geretourneerd, het parameter kenmerk dat open bare eigenschappen identificeert als cmdlet-para meters en meer.</span><span class="sxs-lookup"><span data-stu-id="9923e-105">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9923e-106">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="9923e-106">In This Section</span></span>

<span data-ttu-id="9923e-107">[Kenmerken in cmdlet-code](./attributes-in-cmdlet-code.md) Beschrijft het voor deel van het gebruik van kenmerken in de cmdlet-code.</span><span class="sxs-lookup"><span data-stu-id="9923e-107">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="9923e-108">[Kenmerk typen](./attribute-types.md) Hierin worden de verschillende kenmerken beschreven waarmee een cmdlet-klasse kan worden gedecoreerd.</span><span class="sxs-lookup"><span data-stu-id="9923e-108">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="9923e-109">[Alias kenmerk declaratie](./alias-attribute-declaration.md) Hierin wordt beschreven hoe u aliassen definieert voor de naam van een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="9923e-109">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="9923e-110">[Kenmerk declaratie van cmdlet](./cmdlet-attribute-declaration.md) Hierin wordt beschreven hoe u een .NET Framework klasse als een cmdlet definieert.</span><span class="sxs-lookup"><span data-stu-id="9923e-110">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="9923e-111">[Referentie kenmerk declaratie](./credential-attribute-declaration.md) Hierin wordt beschreven hoe u ondersteuning toevoegt voor het converteren van teken reeks invoer naar een [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -object.</span><span class="sxs-lookup"><span data-stu-id="9923e-111">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="9923e-112">[Output type kenmerk declaratie](./outputtype-attribute-declaration.md) Hierin wordt beschreven hoe u de .NET Framework typen opgeeft die door de cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9923e-112">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="9923e-113">[Parameter kenmerk declaratie](./parameter-attribute-declaration.md) Hierin wordt beschreven hoe u de para meters van een cmdlet definieert.</span><span class="sxs-lookup"><span data-stu-id="9923e-113">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="9923e-114">[ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md) Hierin wordt beschreven hoe u definieert hoeveel argumenten zijn toegestaan voor een para meter.</span><span class="sxs-lookup"><span data-stu-id="9923e-114">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="9923e-115">[ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md) Hierin wordt beschreven hoe u de lengte (in tekens) van een parameter argument definieert.</span><span class="sxs-lookup"><span data-stu-id="9923e-115">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="9923e-116">[ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md) Hierin wordt beschreven hoe u de geldige patronen voor een parameter argument definieert.</span><span class="sxs-lookup"><span data-stu-id="9923e-116">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="9923e-117">[ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md) Hierin wordt beschreven hoe u het geldige bereik voor een parameter argument definieert.</span><span class="sxs-lookup"><span data-stu-id="9923e-117">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="9923e-118">[Verklaring van de kenmerkset validate](./validateset-attribute-declaration.md) Hierin wordt beschreven hoe u de mogelijke waarden voor een parameter argument definieert.</span><span class="sxs-lookup"><span data-stu-id="9923e-118">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="9923e-119">Naslaginformatie</span><span class="sxs-lookup"><span data-stu-id="9923e-119">Reference</span></span>

[<span data-ttu-id="9923e-120">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="9923e-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
