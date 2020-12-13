---
ms.date: 09/13/2016
ms.topic: reference
title: Parameteraliassen
description: Parameteraliassen
ms.openlocfilehash: 0895e2c4df3a149ae75a9741fb65134a8e1122c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648514"
---
# <a name="parameter-aliases"></a><span data-ttu-id="dd34c-103">Parameteraliassen</span><span class="sxs-lookup"><span data-stu-id="dd34c-103">Parameter Aliases</span></span>

<span data-ttu-id="dd34c-104">Cmdlet-para meters kunnen ook aliassen hebben.</span><span class="sxs-lookup"><span data-stu-id="dd34c-104">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="dd34c-105">U kunt de aliassen gebruiken in plaats van de parameter namen wanneer u de para meter in een opdracht typt of opgeeft.</span><span class="sxs-lookup"><span data-stu-id="dd34c-105">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="dd34c-106">Voor delen van het gebruik van aliassen</span><span class="sxs-lookup"><span data-stu-id="dd34c-106">Benefits of Using Aliases</span></span>

<span data-ttu-id="dd34c-107">Het toevoegen van aliassen aan para meters biedt de volgende voor delen.</span><span class="sxs-lookup"><span data-stu-id="dd34c-107">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="dd34c-108">U kunt een snelkoppeling opgeven zodat de gebruiker de volledige parameter naam niet hoeft te gebruiken wanneer de cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="dd34c-108">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="dd34c-109">U kunt bijvoorbeeld de alias ' CN ' gebruiken in plaats van de parameter naam ' ComputerName '.</span><span class="sxs-lookup"><span data-stu-id="dd34c-109">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="dd34c-110">U kunt meerdere aliassen definiëren als u verschillende namen voor dezelfde para meter wilt opgeven.</span><span class="sxs-lookup"><span data-stu-id="dd34c-110">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="dd34c-111">Mogelijk wilt u meerdere aliassen definiëren als u moet werken met meerdere gebruikers groepen die naar dezelfde gegevens op verschillende manieren verwijzen.</span><span class="sxs-lookup"><span data-stu-id="dd34c-111">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="dd34c-112">U kunt achterwaartse compatibiliteit voor bestaande scripts bieden als de naam van een para meter wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="dd34c-112">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="dd34c-113">Door gebruik te maken van het alias kenmerk samen met het kenmerk ValueFromPipelineByName, kunt u een para meter definiëren waarmee de cmdlet kan worden gebonden aan verschillende object typen.</span><span class="sxs-lookup"><span data-stu-id="dd34c-113">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="dd34c-114">Stel dat u twee objecten van verschillende typen hebt en het eerste object heeft een eigenschap Writer en het tweede object heeft een editor-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="dd34c-114">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="dd34c-115">Als uw cmdlet een para meter heeft met schrijver-en redacteur-aliassen en de door de cmdlet geaccepteerde invoer van de pijp lijn is gebaseerd op eigenschapnamen, kan de cmdlet met de twee parameter aliassen aan beide objecten worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="dd34c-115">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="dd34c-116">Zie [common para meter names](./common-parameter-names.md)(Engelstalig) voor meer informatie over aliassen die kunnen worden gebruikt met specifieke para meters.</span><span class="sxs-lookup"><span data-stu-id="dd34c-116">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="dd34c-117">Parameter aliassen definiëren</span><span class="sxs-lookup"><span data-stu-id="dd34c-117">Defining Parameter Aliases</span></span>

<span data-ttu-id="dd34c-118">Als u een alias voor een para meter wilt definiëren, declareert u het alias kenmerk, zoals wordt weer gegeven in de volgende parameter declaratie.</span><span class="sxs-lookup"><span data-stu-id="dd34c-118">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="dd34c-119">In dit voor beeld worden meerdere aliassen gedefinieerd voor dezelfde para meter.</span><span class="sxs-lookup"><span data-stu-id="dd34c-119">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="dd34c-120">(Zie[cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md)voor meer informatie.)</span><span class="sxs-lookup"><span data-stu-id="dd34c-120">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dd34c-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dd34c-121">See Also</span></span>

[<span data-ttu-id="dd34c-122">Namen van veelvoorkomende parameters</span><span class="sxs-lookup"><span data-stu-id="dd34c-122">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="dd34c-123">Cmdlet-parameters declareren</span><span class="sxs-lookup"><span data-stu-id="dd34c-123">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="dd34c-124">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="dd34c-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
