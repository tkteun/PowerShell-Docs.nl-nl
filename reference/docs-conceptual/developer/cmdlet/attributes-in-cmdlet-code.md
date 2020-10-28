---
ms.date: 09/13/2016
ms.topic: reference
title: Kenmerken in de cmdlet-code
description: Kenmerken in de cmdlet-code
ms.openlocfilehash: 296bb8bcb06ef660e97dc792d1ecf596cc7c2930
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653642"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="fe8db-103">Kenmerken in de cmdlet-code</span><span class="sxs-lookup"><span data-stu-id="fe8db-103">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="fe8db-104">Als u de algemene functionaliteit van Windows Power shell wilt gebruiken, worden de klassen en open bare eigenschappen die in de cmdlet-code zijn gedefinieerd, voorzien van kenmerken.</span><span class="sxs-lookup"><span data-stu-id="fe8db-104">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="fe8db-105">De volgende klassen definitie maakt bijvoorbeeld gebruik van het cmdlet-kenmerk om de Microsoft .NET Framework-klasse te identificeren waarin de **Get-proc-** cmdlet wordt geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="fe8db-105">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="fe8db-106">(Deze cmdlet wordt gebruikt als voor beeld in dit document en is vergelijkbaar met de `Get-Process` cmdlet van Windows Power shell.)</span><span class="sxs-lookup"><span data-stu-id="fe8db-106">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="fe8db-107">Deze kenmerken worden beschouwd als meta gegevens omdat hun implementatie gescheiden is van de implementatie van de cmdlet-code.</span><span class="sxs-lookup"><span data-stu-id="fe8db-107">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="fe8db-108">Wanneer de Windows Power shell-runtime de cmdlet uitvoert, herkent deze de kenmerken en voert vervolgens de juiste actie uit voor elk kenmerk.</span><span class="sxs-lookup"><span data-stu-id="fe8db-108">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="fe8db-109">Hoewel het mogelijk is om uw eigen versie van de functionaliteit van deze kenmerken te implementeren, maakt een goed ontwerp van de cmdlet gebruik van deze algemene functies.</span><span class="sxs-lookup"><span data-stu-id="fe8db-109">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="fe8db-110">Zie [kenmerk typen](./attribute-types.md)voor meer informatie over de verschillende kenmerken die kunnen worden gedeclareerd in de-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fe8db-110">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe8db-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fe8db-111">See Also</span></span>

[<span data-ttu-id="fe8db-112">Typen kenmerken</span><span class="sxs-lookup"><span data-stu-id="fe8db-112">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="fe8db-113">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="fe8db-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
