---
title: Kenmerken in de Cmdlet-Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068676"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="d0cf3-102">Kenmerken in de cmdlet-code</span><span class="sxs-lookup"><span data-stu-id="d0cf3-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="d0cf3-103">De algemene functionaliteit die is geleverd door Windows PowerShell wilt gebruiken, worden de klassen en de openbare eigenschappen die zijn gedefinieerd in de cmdlet-code voorzien van kenmerken.</span><span class="sxs-lookup"><span data-stu-id="d0cf3-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="d0cf3-104">De volgende klassendefinitie gebruikt bijvoorbeeld de Cmdlet-kenmerk voor het identificeren van de Microsoft .NET Framework-klasse waarin de **Get-Proc** cmdlet is geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="d0cf3-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="d0cf3-105">(Deze cmdlet wordt gebruikt als een voorbeeld in dit document en is vergelijkbaar met de `Get-Process` geleverd door Windows PowerShell cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="d0cf3-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="d0cf3-106">Deze kenmerken worden beschouwd als van metagegevens omdat de toepassing gescheiden van de implementatie van de cmdlet-code is.</span><span class="sxs-lookup"><span data-stu-id="d0cf3-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="d0cf3-107">Wanneer de Windows PowerShell-runtime wordt uitgevoerd van de cmdlet, herkent de kenmerken en vervolgens de juiste actie uitvoeren voor elk kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d0cf3-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="d0cf3-108">Hoewel u wilt mogelijk voor het implementeren van uw eigen versie van de functionaliteit van deze kenmerken, een goede cmdlet-ontwerp maakt gebruik van deze algemene functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="d0cf3-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="d0cf3-109">Zie voor meer informatie over de verschillende kenmerken die kunnen worden gedefinieerd in uw cmdlets, [kenmerktypen](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="d0cf3-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0cf3-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d0cf3-110">See Also</span></span>

[<span data-ttu-id="d0cf3-111">Kenmerktypen</span><span class="sxs-lookup"><span data-stu-id="d0cf3-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="d0cf3-112">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d0cf3-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
