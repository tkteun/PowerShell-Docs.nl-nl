---
title: Aantal para meters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359256"
---
# <a name="quantity-parameters"></a><span data-ttu-id="97bf2-102">Hoeveelheidsparameters</span><span class="sxs-lookup"><span data-stu-id="97bf2-102">Quantity Parameters</span></span>

<span data-ttu-id="97bf2-103">De volgende tabel bevat de aanbevolen namen en functionaliteit voor hoeveelheids parameters.</span><span class="sxs-lookup"><span data-stu-id="97bf2-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="97bf2-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="97bf2-104">Parameter</span></span>|<span data-ttu-id="97bf2-105">Functionaliteit</span><span class="sxs-lookup"><span data-stu-id="97bf2-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="97bf2-106">**Hele**</span><span class="sxs-lookup"><span data-stu-id="97bf2-106">**All**</span></span><br><span data-ttu-id="97bf2-107">Gegevens type: Booleaans</span><span class="sxs-lookup"><span data-stu-id="97bf2-107">Data type: Boolean</span></span>|<span data-ttu-id="97bf2-108">Implementeer deze para meter zodanig dat `true` aangeeft dat alle resources moeten worden uitgevoerd in plaats van een standaard subset van resources.</span><span class="sxs-lookup"><span data-stu-id="97bf2-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="97bf2-109">Implementeer deze para meter zodanig dat `false` een subset van de resources aangeeft.</span><span class="sxs-lookup"><span data-stu-id="97bf2-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="97bf2-110">**Configuration**</span><span class="sxs-lookup"><span data-stu-id="97bf2-110">**Allocation**</span></span><br><span data-ttu-id="97bf2-111">Gegevens type: Int32</span><span class="sxs-lookup"><span data-stu-id="97bf2-111">Data type: Int32</span></span>|<span data-ttu-id="97bf2-112">Implementeer deze para meter zodat de gebruiker het aantal items kan opgeven dat moet worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="97bf2-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="97bf2-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="97bf2-113">**BlockCount**</span></span><br><span data-ttu-id="97bf2-114">Gegevens type: Int64</span><span class="sxs-lookup"><span data-stu-id="97bf2-114">Data type: Int64</span></span>|<span data-ttu-id="97bf2-115">Implementeer deze para meter zodat de gebruiker het aantal blokken kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="97bf2-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="97bf2-116">**Aantal**</span><span class="sxs-lookup"><span data-stu-id="97bf2-116">**Count**</span></span><br><span data-ttu-id="97bf2-117">Gegevens type: Int64</span><span class="sxs-lookup"><span data-stu-id="97bf2-117">Data type: Int64</span></span>|<span data-ttu-id="97bf2-118">Implementeer deze para meter zodat de gebruiker de telling kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="97bf2-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="97bf2-119">**Ligt**</span><span class="sxs-lookup"><span data-stu-id="97bf2-119">**Scope**</span></span><br><span data-ttu-id="97bf2-120">Gegevens type: tref woord</span><span class="sxs-lookup"><span data-stu-id="97bf2-120">Data type: Keyword</span></span>|<span data-ttu-id="97bf2-121">Implementeer deze para meter zodat de gebruiker het bereik kan opgeven dat moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="97bf2-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="97bf2-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="97bf2-122">See Also</span></span>

[<span data-ttu-id="97bf2-123">Cmdlet-para meters</span><span class="sxs-lookup"><span data-stu-id="97bf2-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="97bf2-124">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="97bf2-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="97bf2-125">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="97bf2-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
