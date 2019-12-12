---
title: Parameter aliassen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359261"
---
# <a name="parameter-aliases"></a><span data-ttu-id="f33d5-102">Parameteraliassen</span><span class="sxs-lookup"><span data-stu-id="f33d5-102">Parameter Aliases</span></span>

<span data-ttu-id="f33d5-103">Cmdlet-para meters kunnen ook aliassen hebben.</span><span class="sxs-lookup"><span data-stu-id="f33d5-103">Cmdlet parameters can also have aliases.</span></span> <span data-ttu-id="f33d5-104">U kunt de aliassen gebruiken in plaats van de parameter namen wanneer u de para meter in een opdracht typt of opgeeft.</span><span class="sxs-lookup"><span data-stu-id="f33d5-104">You can use the aliases instead of the parameter names when you type or specify the parameter in a command.</span></span>

## <a name="benefits-of-using-aliases"></a><span data-ttu-id="f33d5-105">Voor delen van het gebruik van aliassen</span><span class="sxs-lookup"><span data-stu-id="f33d5-105">Benefits of Using Aliases</span></span>

<span data-ttu-id="f33d5-106">Het toevoegen van aliassen aan para meters biedt de volgende voor delen.</span><span class="sxs-lookup"><span data-stu-id="f33d5-106">Adding aliases to parameters provides the following benefits.</span></span>

- <span data-ttu-id="f33d5-107">U kunt een snelkoppeling opgeven zodat de gebruiker de volledige parameter naam niet hoeft te gebruiken wanneer de cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="f33d5-107">You can provide a shortcut so that the user does not have to use the complete parameter name when the cmdlet is called.</span></span> <span data-ttu-id="f33d5-108">U kunt bijvoorbeeld de alias ' CN ' gebruiken in plaats van de parameter naam ' ComputerName '.</span><span class="sxs-lookup"><span data-stu-id="f33d5-108">For example, you could use the "CN" alias instead of the parameter name "ComputerName".</span></span>

- <span data-ttu-id="f33d5-109">U kunt meerdere aliassen definiëren als u verschillende namen voor dezelfde para meter wilt opgeven.</span><span class="sxs-lookup"><span data-stu-id="f33d5-109">You can define multiple aliases if you want to provide different names for the same parameter.</span></span> <span data-ttu-id="f33d5-110">Mogelijk wilt u meerdere aliassen definiëren als u moet werken met meerdere gebruikers groepen die naar dezelfde gegevens op verschillende manieren verwijzen.</span><span class="sxs-lookup"><span data-stu-id="f33d5-110">You might want to define multiple aliases if you have to work with multiple user groups that refer to the same data in different ways.</span></span>

- <span data-ttu-id="f33d5-111">U kunt achterwaartse compatibiliteit voor bestaande scripts bieden als de naam van een para meter wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f33d5-111">You can provide backwards compatibility for existing scripts if the name of a parameter changes.</span></span>

- <span data-ttu-id="f33d5-112">Door gebruik te maken van het alias kenmerk samen met het kenmerk ValueFromPipelineByName, kunt u een para meter definiëren waarmee de cmdlet kan worden gebonden aan verschillende object typen.</span><span class="sxs-lookup"><span data-stu-id="f33d5-112">By using the Alias attribute along with the ValueFromPipelineByName attribute, you can define a parameter that allows your cmdlet to bind to different object types.</span></span> <span data-ttu-id="f33d5-113">Stel dat u twee objecten van verschillende typen hebt en het eerste object heeft een eigenschap Writer en het tweede object heeft een editor-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="f33d5-113">For example, say you had two objects of different types and the first object had a writer property and the second object had an editor property.</span></span> <span data-ttu-id="f33d5-114">Als uw cmdlet een para meter heeft met schrijver-en redacteur-aliassen en de door de cmdlet geaccepteerde invoer van de pijp lijn is gebaseerd op eigenschapnamen, kan de cmdlet met de twee parameter aliassen aan beide objecten worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="f33d5-114">If your cmdlet had a parameter that had writer and editor aliases and the cmdlet accepted pipeline input based in property names, your cmdlet could bind to both objects using the two parameter aliases.</span></span>

<span data-ttu-id="f33d5-115">Zie [common para meter names](./common-parameter-names.md)(Engelstalig) voor meer informatie over aliassen die kunnen worden gebruikt met specifieke para meters.</span><span class="sxs-lookup"><span data-stu-id="f33d5-115">For more information about aliases that can be used with specific parameters, see [Common Parameter Names](./common-parameter-names.md).</span></span>

## <a name="defining-parameter-aliases"></a><span data-ttu-id="f33d5-116">Parameter aliassen definiëren</span><span class="sxs-lookup"><span data-stu-id="f33d5-116">Defining Parameter Aliases</span></span>

<span data-ttu-id="f33d5-117">Als u een alias voor een para meter wilt definiëren, declareert u het alias kenmerk, zoals wordt weer gegeven in de volgende parameter declaratie.</span><span class="sxs-lookup"><span data-stu-id="f33d5-117">To define an alias for a parameter, declare the Alias attribute, as shown in the following parameter declaration.</span></span> <span data-ttu-id="f33d5-118">In dit voor beeld worden meerdere aliassen gedefinieerd voor dezelfde para meter.</span><span class="sxs-lookup"><span data-stu-id="f33d5-118">In this example, multiple aliases are defined for the same parameter.</span></span> <span data-ttu-id="f33d5-119">(Zie[cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md)voor meer informatie.)</span><span class="sxs-lookup"><span data-stu-id="f33d5-119">(For more information, see[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f33d5-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f33d5-120">See Also</span></span>

[<span data-ttu-id="f33d5-121">Algemene parameter namen</span><span class="sxs-lookup"><span data-stu-id="f33d5-121">Common Parameter Names</span></span>](./common-parameter-names.md)

[<span data-ttu-id="f33d5-122">Cmdlet-para meters declareren</span><span class="sxs-lookup"><span data-stu-id="f33d5-122">How to Declare Cmdlet Parameters</span></span>](./how-to-declare-cmdlet-parameters.md)

[<span data-ttu-id="f33d5-123">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="f33d5-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
