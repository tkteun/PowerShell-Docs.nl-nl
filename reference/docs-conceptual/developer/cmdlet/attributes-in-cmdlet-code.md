---
title: Kenmerken in cmdlet-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1f92e329d304754d5596cef0c95dc597aca3a538
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774912"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="07ab7-102">Kenmerken in de cmdlet-code</span><span class="sxs-lookup"><span data-stu-id="07ab7-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="07ab7-103">Als u de algemene functionaliteit van Windows Power shell wilt gebruiken, worden de klassen en open bare eigenschappen die in de cmdlet-code zijn gedefinieerd, voorzien van kenmerken.</span><span class="sxs-lookup"><span data-stu-id="07ab7-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="07ab7-104">De volgende klassen definitie maakt bijvoorbeeld gebruik van het cmdlet-kenmerk om de Microsoft .NET Framework-klasse te identificeren waarin de **Get-proc-** cmdlet wordt geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="07ab7-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="07ab7-105">(Deze cmdlet wordt gebruikt als voor beeld in dit document en is vergelijkbaar met de `Get-Process` cmdlet van Windows Power shell.)</span><span class="sxs-lookup"><span data-stu-id="07ab7-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="07ab7-106">Deze kenmerken worden beschouwd als meta gegevens omdat hun implementatie gescheiden is van de implementatie van de cmdlet-code.</span><span class="sxs-lookup"><span data-stu-id="07ab7-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="07ab7-107">Wanneer de Windows Power shell-runtime de cmdlet uitvoert, herkent deze de kenmerken en voert vervolgens de juiste actie uit voor elk kenmerk.</span><span class="sxs-lookup"><span data-stu-id="07ab7-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="07ab7-108">Hoewel het mogelijk is om uw eigen versie van de functionaliteit van deze kenmerken te implementeren, maakt een goed ontwerp van de cmdlet gebruik van deze algemene functies.</span><span class="sxs-lookup"><span data-stu-id="07ab7-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="07ab7-109">Zie [kenmerk typen](./attribute-types.md)voor meer informatie over de verschillende kenmerken die kunnen worden gedeclareerd in de-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="07ab7-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07ab7-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="07ab7-110">See Also</span></span>

[<span data-ttu-id="07ab7-111">Typen kenmerken</span><span class="sxs-lookup"><span data-stu-id="07ab7-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="07ab7-112">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="07ab7-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
