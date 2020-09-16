---
title: Alias kenmerk declaratie | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782409"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="b3a1b-102">Declaratie van het kenmerk Alias</span><span class="sxs-lookup"><span data-stu-id="b3a1b-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="b3a1b-103">Met het alias kenmerk kan de gebruiker verschillende namen opgeven voor een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="b3a1b-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="b3a1b-104">Aliassen kunnen worden gebruikt om snelkoppelingen voor de naam van een para meter op te geven, of ze kunnen verschillende namen opgeven die geschikt zijn voor verschillende scenario's.</span><span class="sxs-lookup"><span data-stu-id="b3a1b-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="b3a1b-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b3a1b-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="b3a1b-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="b3a1b-106">Parameters</span></span>

<span data-ttu-id="b3a1b-107">`aliasName` (Teken reeks []) Vereist.</span><span class="sxs-lookup"><span data-stu-id="b3a1b-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="b3a1b-108">Hiermee geeft u een set met door komma's gescheiden alias namen op voor de cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="b3a1b-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3a1b-109">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b3a1b-109">Remarks</span></span>

- <span data-ttu-id="b3a1b-110">Het kenmerk alias wordt gebruikt met het parameter kenmerk wanneer u een cmdlet-para meter opgeeft.</span><span class="sxs-lookup"><span data-stu-id="b3a1b-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="b3a1b-111">Zie voor meer informatie over het declareren van deze kenmerken [cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b3a1b-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="b3a1b-112">Elke alias naam moet uniek zijn binnen een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3a1b-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="b3a1b-113">Windows Power shell controleert niet op dubbele alias namen.</span><span class="sxs-lookup"><span data-stu-id="b3a1b-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="b3a1b-114">Het alias kenmerk wordt één keer gebruikt voor elke para meter in een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3a1b-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="b3a1b-115">Het alias kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .</span><span class="sxs-lookup"><span data-stu-id="b3a1b-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3a1b-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b3a1b-116">See Also</span></span>

[<span data-ttu-id="b3a1b-117">Parameteraliassen</span><span class="sxs-lookup"><span data-stu-id="b3a1b-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="b3a1b-118">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="b3a1b-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
