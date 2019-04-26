---
title: Alias kenmerkdeclaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068708"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="9c35f-102">Declaratie van het kenmerk Alias</span><span class="sxs-lookup"><span data-stu-id="9c35f-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="9c35f-103">Het kenmerk Alias kan de gebruiker om op te geven van verschillende namen voor een cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="9c35f-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="9c35f-104">Aliassen kunnen worden gebruikt voor snelkoppelingen voor een parameternaam of ze verschillende namen die geschikt voor verschillende scenario's zijn kunnen opgeven.</span><span class="sxs-lookup"><span data-stu-id="9c35f-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c35f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9c35f-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="9c35f-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="9c35f-106">Parameters</span></span>

<span data-ttu-id="9c35f-107">`aliasName` (String[]) Vereist.</span><span class="sxs-lookup"><span data-stu-id="9c35f-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="9c35f-108">Hiermee geeft u een set met de door komma's gescheiden aliasnamen van de cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="9c35f-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c35f-109">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9c35f-109">Remarks</span></span>

- <span data-ttu-id="9c35f-110">Het kenmerk Alias wordt gebruikt met de Parameter-kenmerk wanneer u een cmdlet-parameter opgeven.</span><span class="sxs-lookup"><span data-stu-id="9c35f-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="9c35f-111">Zie voor meer informatie over het declareren van deze kenmerken [hoe u de Cmdlet-Parameters declareren](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9c35f-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="9c35f-112">De naam van elke alias moet uniek zijn binnen een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c35f-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="9c35f-113">Dubbele aliasnamen controleert niet op Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c35f-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="9c35f-114">Het kenmerk Alias wordt één keer gebruikt voor elke parameter in een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c35f-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="9c35f-115">De Alias-kenmerk wordt gedefinieerd door de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) klasse.</span><span class="sxs-lookup"><span data-stu-id="9c35f-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c35f-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9c35f-116">See Also</span></span>

[<span data-ttu-id="9c35f-117">Parameter Aliases</span><span class="sxs-lookup"><span data-stu-id="9c35f-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="9c35f-118">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9c35f-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
