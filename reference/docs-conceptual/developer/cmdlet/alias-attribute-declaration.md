---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk Alias
description: Declaratie van het kenmerk Alias
ms.openlocfilehash: f2fe49578da2c795643b1f80fa44deefe1dbff09
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668300"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="31310-103">Declaratie van het kenmerk Alias</span><span class="sxs-lookup"><span data-stu-id="31310-103">Alias Attribute Declaration</span></span>

<span data-ttu-id="31310-104">Met het alias kenmerk kan de gebruiker verschillende namen opgeven voor een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="31310-104">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="31310-105">Aliassen kunnen worden gebruikt om snelkoppelingen voor de naam van een para meter op te geven, of ze kunnen verschillende namen opgeven die geschikt zijn voor verschillende scenario's.</span><span class="sxs-lookup"><span data-stu-id="31310-105">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="31310-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="31310-106">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="31310-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="31310-107">Parameters</span></span>

<span data-ttu-id="31310-108">`aliasName` (Teken reeks []) Vereist.</span><span class="sxs-lookup"><span data-stu-id="31310-108">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="31310-109">Hiermee geeft u een set met door komma's gescheiden alias namen op voor de cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="31310-109">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="31310-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="31310-110">Remarks</span></span>

- <span data-ttu-id="31310-111">Het kenmerk alias wordt gebruikt met het parameter kenmerk wanneer u een cmdlet-para meter opgeeft.</span><span class="sxs-lookup"><span data-stu-id="31310-111">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="31310-112">Zie voor meer informatie over het declareren van deze kenmerken [cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="31310-112">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="31310-113">Elke alias naam moet uniek zijn binnen een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31310-113">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="31310-114">Windows Power shell controleert niet op dubbele alias namen.</span><span class="sxs-lookup"><span data-stu-id="31310-114">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="31310-115">Het alias kenmerk wordt één keer gebruikt voor elke para meter in een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31310-115">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="31310-116">Het alias kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .</span><span class="sxs-lookup"><span data-stu-id="31310-116">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="31310-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="31310-117">See Also</span></span>

[<span data-ttu-id="31310-118">Parameteraliassen</span><span class="sxs-lookup"><span data-stu-id="31310-118">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="31310-119">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="31310-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
