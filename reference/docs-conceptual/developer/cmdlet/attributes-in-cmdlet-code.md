---
title: Kenmerken in cmdlet-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359463"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="3a749-102">Kenmerken in de cmdlet-code</span><span class="sxs-lookup"><span data-stu-id="3a749-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="3a749-103">Als u de algemene functionaliteit van Windows Power shell wilt gebruiken, worden de klassen en open bare eigenschappen die in de cmdlet-code zijn gedefinieerd, voorzien van kenmerken.</span><span class="sxs-lookup"><span data-stu-id="3a749-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="3a749-104">De volgende klassen definitie maakt bijvoorbeeld gebruik van het cmdlet-kenmerk om de Microsoft .NET Framework-klasse te identificeren waarin de **Get-proc-** cmdlet wordt geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="3a749-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="3a749-105">(Deze cmdlet wordt gebruikt als voor beeld in dit document en is vergelijkbaar met de `Get-Process`-cmdlet van Windows Power shell.)</span><span class="sxs-lookup"><span data-stu-id="3a749-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="3a749-106">Deze kenmerken worden beschouwd als meta gegevens omdat hun implementatie gescheiden is van de implementatie van de cmdlet-code.</span><span class="sxs-lookup"><span data-stu-id="3a749-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="3a749-107">Wanneer de Windows Power shell-runtime de cmdlet uitvoert, herkent deze de kenmerken en voert vervolgens de juiste actie uit voor elk kenmerk.</span><span class="sxs-lookup"><span data-stu-id="3a749-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="3a749-108">Hoewel het mogelijk is om uw eigen versie van de functionaliteit van deze kenmerken te implementeren, maakt een goed ontwerp van de cmdlet gebruik van deze algemene functies.</span><span class="sxs-lookup"><span data-stu-id="3a749-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="3a749-109">Zie [kenmerk typen](./attribute-types.md)voor meer informatie over de verschillende kenmerken die kunnen worden gedeclareerd in de-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3a749-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3a749-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3a749-110">See Also</span></span>

[<span data-ttu-id="3a749-111">Kenmerk typen</span><span class="sxs-lookup"><span data-stu-id="3a749-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="3a749-112">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="3a749-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
