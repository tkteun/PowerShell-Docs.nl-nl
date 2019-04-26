---
title: Aliassen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067583"
---
# <a name="parameter-aliases"></a><span data-ttu-id="17784-102">Parameteraliassen</span><span class="sxs-lookup"><span data-stu-id="17784-102">Parameter Aliases</span></span>

<span data-ttu-id="17784-103">Cmdlet-parameters kunnen ook aliassen hebben.</span><span class="sxs-lookup"><span data-stu-id="17784-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="17784-104">Wanneer u typt of de parameter in een opdracht opgeven, kunt u de aliassen in plaats van de namen van parameters.</span><span class="sxs-lookup"><span data-stu-id="17784-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="17784-105">Voordelen van het gebruik van aliassen</span><span class="sxs-lookup"><span data-stu-id="17784-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="17784-106">Aliassen aan parameters toe te voegen, biedt de volgende voordelen.</span><span class="sxs-lookup"><span data-stu-id="17784-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="17784-107">U kunt een snelkoppeling kunt opgeven, zodat de gebruiker beschikt niet over de volledige parameternaam gebruiken wanneer de cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="17784-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="17784-108">U kunt bijvoorbeeld de alias 'CN' gebruiken in plaats van de naam van de parameter "Computernaam".</span><span class="sxs-lookup"><span data-stu-id="17784-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="17784-109">U kunt meerdere aliassen definiëren als u wilt dat verschillende namen voor de dezelfde parameter op te geven.</span><span class="sxs-lookup"><span data-stu-id="17784-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="17784-110">Het is raadzaam om te definiëren meerdere aliassen instellen als u wilt werken met meerdere gebruikersgroepen die naar dezelfde gegevens op verschillende manieren verwijzen.</span><span class="sxs-lookup"><span data-stu-id="17784-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="17784-111">U kunt zorgen voor compatibiliteit voor bestaande scripts als de naam van een parameter wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="17784-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="17784-112">Met behulp van het kenmerk Alias, samen met het kenmerk ValueFromPipelineByName, kunt u een parameter waarmee de cmdlet verbinding maken met verschillende objecttypen definiëren.</span><span class="sxs-lookup"><span data-stu-id="17784-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="17784-113">Stel bijvoorbeeld dat er twee objecten van verschillende typen en het eerste object al een eigenschap schrijver en de tweede object heeft een eigenschap van een editor.</span><span class="sxs-lookup"><span data-stu-id="17784-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="17784-114">Als uw cmdlet heeft een parameter die was met de schrijver en editor aliassen en de cmdlet geaccepteerd pijpleidinginvoer gebaseerd in de namen van eigenschappen, uw cmdlet kan binden aan beide objecten met behulp van de twee parameter-aliassen.</span><span class="sxs-lookup"><span data-stu-id="17784-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="17784-115">Zie voor meer informatie over aliassen die kunnen worden gebruikt met bepaalde parameters [algemene parameternamen](./common-parameter-names.md).</span><span class="sxs-lookup"><span data-stu-id="17784-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="17784-116">Parameter-aliassen definiëren</span><span class="sxs-lookup"><span data-stu-id="17784-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="17784-117">Declareren voor het definiëren van een alias voor een parameter, de Alias-kenmerk, zoals wordt weergegeven in de volgende parameterdeclaratie.</span><span class="sxs-lookup"><span data-stu-id="17784-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="17784-118">In dit voorbeeld worden meerdere aliassen instellen voor de dezelfde parameter gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="17784-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="17784-119">(Zie voor meer informatie,[hoe u de Cmdlet-Parameters declareren](./how-to-declare-cmdlet-parameters.md).)</span><span class="sxs-lookup"><span data-stu-id="17784-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a><span data-ttu-id="17784-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="17784-120">See Also</span></span>

[<span data-ttu-id="17784-121">Namen van algemene parameters</span><span class="sxs-lookup"><span data-stu-id="17784-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="17784-122">Hoe om te declareren Cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="17784-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="17784-123">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="17784-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
