---
title: Eigenschappen als Parameters declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068263"
---
# <a name="declaring-properties-as-parameters"></a><span data-ttu-id="3aa5d-102">Eigenschappen declareren als parameters</span><span class="sxs-lookup"><span data-stu-id="3aa5d-102">Declaring Properties as Parameters</span></span>

<span data-ttu-id="3aa5d-103">Dit onderwerp bevat algemene informatie die u begrijpen moet voordat u de parameters van een cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-103">This topic provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="3aa5d-104">U declareert de parameters van een cmdlet uit binnen de klasse van de cmdlet, definiëren van de openbare eigenschappen die staan voor elke parameter en vervolgens een of meer kenmerken van de Parameter toevoegen aan elke eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-104">To declare the parameters of a cmdlet within your cmdlet class, define the public properties that represent each parameter, and then add one or more Parameter attributes to each property.</span></span> <span data-ttu-id="3aa5d-105">De Windows PowerShell-runtime maakt gebruik van de Parameter-kenmerken voor het identificeren van de eigenschap als cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-105">The Windows PowerShell runtime uses the Parameter attributes to identify the property as a cmdlet parameter.</span></span> <span data-ttu-id="3aa5d-106">De syntaxis van de basis voor de Parameter-kenmerk declareren is `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-106">The basic syntax for declaring the Parameter attribute is `[Parameter()]`.</span></span>

<span data-ttu-id="3aa5d-107">Hier volgt een voorbeeld van een eigenschap die is gedefinieerd als een vereiste parameter.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-107">Here is an example of a property defined as a required parameter.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="3aa5d-108">Hier volgen enkele dingen om te weten over parameters.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-108">Here are some things to remember about parameters.</span></span>

- <span data-ttu-id="3aa5d-109">Een parameter moet expliciet gemarkeerd als openbaar.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-109">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="3aa5d-110">Parameters die niet zijn gemarkeerd als openbare standaard naar interne en wordt niet worden gevonden door de Windows PowerShell-runtime.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-110">Parameters that are not marked as public default to internal and will not be found by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="3aa5d-111">Parameters moeten worden gedefinieerd als Microsoft .NET Framework-typen voor betere validatie van de parameter.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-111">Parameters should be defined as Microsoft .NET Framework types to provide better parameter validation.</span></span> <span data-ttu-id="3aa5d-112">Parameters die beperkt tot één waarde uit een set waarden zijn moeten bijvoorbeeld worden gedefinieerd als een opsommingstype.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-112">For example, parameters that are restricted to one value out of a set of values should be defined as an enumeration type.</span></span> <span data-ttu-id="3aa5d-113">Parameters die een Uniform Resource Identifier (URI)-waarde moet van het type [System.Uri](/dotnet/api/System.Uri).</span><span class="sxs-lookup"><span data-stu-id="3aa5d-113">Parameters that take a Uniform Resource Identifier (URI) value should be of type [System.Uri](/dotnet/api/System.Uri).</span></span>

- <span data-ttu-id="3aa5d-114">Vermijd basic queryreeksparameters voor eigenschappen van alle vrije tekst.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-114">Avoid basic string parameters for all but free-form text properties.</span></span>

- <span data-ttu-id="3aa5d-115">U kunt een parameter toevoegen aan een willekeurig aantal parametersets.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-115">You can add a parameter to any number of parameter sets.</span></span> <span data-ttu-id="3aa5d-116">Zie voor meer informatie over parametersets [Cmdlet-Parameter stelt](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="3aa5d-116">For more information about parameter sets, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

<span data-ttu-id="3aa5d-117">Windows PowerShell biedt ook een aantal gemeenschappelijke parameters die automatisch beschikbaar voor elke cmdlet zijn.</span><span class="sxs-lookup"><span data-stu-id="3aa5d-117">Windows PowerShell also provides a set of common parameters that are automatically available to every cmdlet.</span></span> <span data-ttu-id="3aa5d-118">Zie voor meer informatie over deze parameters en hun aliassen, [algemene Parameters van de Cmdlet](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="3aa5d-118">For more information about these parameters and their aliases, see [Cmdlet Common Parameters](./common-parameter-names.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3aa5d-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3aa5d-119">See Also</span></span>

[<span data-ttu-id="3aa5d-120">Algemene cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="3aa5d-120">Cmdlet Common Parameters</span></span>](./common-parameter-names.md)

[<span data-ttu-id="3aa5d-121">Typen van de Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="3aa5d-121">Types of Cmdlet Parameter</span></span>](./types-of-cmdlet-parameters.md)

[<span data-ttu-id="3aa5d-122">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3aa5d-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
