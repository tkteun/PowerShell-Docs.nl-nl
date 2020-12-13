---
ms.date: 07/09/2020
ms.topic: reference
title: Uitgebreide type systeem klasse leden
description: Uitgebreide type systeem klasse leden
ms.openlocfilehash: 06488ce423f363a285ab53b21ab45989654346dc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666838"
---
# <a name="extended-type-system-class-members"></a><span data-ttu-id="0bf15-103">Uitgebreide type systeem klasse leden</span><span class="sxs-lookup"><span data-stu-id="0bf15-103">Extended Type System class members</span></span>

<span data-ttu-id="0bf15-104">ETS verwijst naar een aantal verschillende soorten leden waarvan de typen worden gedefinieerd door de **PSMemberTypes** -inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="0bf15-104">ETS refers to a number of different kinds of members whose types are defined by the **PSMemberTypes** enumeration.</span></span> <span data-ttu-id="0bf15-105">Deze leden typen zijn onder andere eigenschappen, methoden, leden en leden sets die zijn gedefinieerd door hun eigen CLR-type.</span><span class="sxs-lookup"><span data-stu-id="0bf15-105">These member types include properties, methods, members, and member sets that are each defined by their own CLR type.</span></span> <span data-ttu-id="0bf15-106">Een **NoteProperty** wordt bijvoorbeeld gedefinieerd door het eigen **PSNoteProperty** -type.</span><span class="sxs-lookup"><span data-stu-id="0bf15-106">For example, a **NoteProperty** is defined by its own **PSNoteProperty** type.</span></span> <span data-ttu-id="0bf15-107">Deze afzonderlijke CLR-typen hebben zowel hun eigen unieke eigenschappen als algemene eigenschappen die worden overgenomen van de [klasse PSMemberInfo](/dotnet/api/system.management.automation.psmemberinfo).</span><span class="sxs-lookup"><span data-stu-id="0bf15-107">These individual CLR types have both their own unique properties and common properties that are inherited from the [PSMemberInfo class](/dotnet/api/system.management.automation.psmemberinfo).</span></span>

## <a name="the-psmemberinfo-class"></a><span data-ttu-id="0bf15-108">De PSMemberInfo-klasse</span><span class="sxs-lookup"><span data-stu-id="0bf15-108">The PSMemberInfo class</span></span>

<span data-ttu-id="0bf15-109">De klasse **PSMemberInfo** fungeert als basis klasse voor alle ETS-leden typen.</span><span class="sxs-lookup"><span data-stu-id="0bf15-109">The **PSMemberInfo** class serves as a base class for all ETS member types.</span></span> <span data-ttu-id="0bf15-110">Deze klasse biedt de volgende basis eigenschappen aan alle member CLR-typen.</span><span class="sxs-lookup"><span data-stu-id="0bf15-110">This class provides the following base properties to all member CLR types.</span></span>

- <span data-ttu-id="0bf15-111">**Naam** eigenschap: de naam van het lid.</span><span class="sxs-lookup"><span data-stu-id="0bf15-111">**Name** property: The name of the member.</span></span> <span data-ttu-id="0bf15-112">Deze naam kan worden gedefinieerd door het basis object of door Power shell gedefinieerd wanneer aangepaste leden of uitgebreide leden worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0bf15-112">This name can be defined by the base-object or defined by PowerShell when adapted members or extended members are exposed.</span></span>
- <span data-ttu-id="0bf15-113">Eigenschap **waarde** : de waarde die is geretourneerd door het specifieke lid.</span><span class="sxs-lookup"><span data-stu-id="0bf15-113">**Value** property: The value returned from the particular member.</span></span> <span data-ttu-id="0bf15-114">Elk lidtype bepaalt hoe de waarde van het lid wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="0bf15-114">Each member type defines how it handles its member value.</span></span>
- <span data-ttu-id="0bf15-115">Eigenschap **TypeNameOfValue** : dit is de naam van het CLR-type van de waarde die wordt geretourneerd door de eigenschap Value.</span><span class="sxs-lookup"><span data-stu-id="0bf15-115">**TypeNameOfValue** property: This is the name of the CLR type of the value that is returned by the Value property.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="0bf15-116">Toegang tot leden</span><span class="sxs-lookup"><span data-stu-id="0bf15-116">Accessing members</span></span>

<span data-ttu-id="0bf15-117">U kunt toegang krijgen tot verzamelingen van leden via de eigenschappen van de **leden**, **methoden** en **Eigenschappen** van het object **PSObject** .</span><span class="sxs-lookup"><span data-stu-id="0bf15-117">Collections of members can be accessed through the **Members**, **Methods**, and **Properties** properties of the **PSObject** object.</span></span>

## <a name="ets-properties"></a><span data-ttu-id="0bf15-118">ETS-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="0bf15-118">ETS properties</span></span>

<span data-ttu-id="0bf15-119">ETS-eigenschappen zijn leden die als eigenschap kunnen worden behandeld.</span><span class="sxs-lookup"><span data-stu-id="0bf15-119">ETS properties are members that can be treated as a property.</span></span> <span data-ttu-id="0bf15-120">In feite kunnen ze worden weer gegeven aan de linkerkant van een expressie.</span><span class="sxs-lookup"><span data-stu-id="0bf15-120">Essentially, they can appear on the left-hand side of an expression.</span></span> <span data-ttu-id="0bf15-121">Deze bevatten alias eigenschappen, code-eigenschappen, eigenschappen van de Power shell, notitie-eigenschappen en script eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="0bf15-121">They include alias properties, code properties, PowerShell properties, note properties, and script properties.</span></span> <span data-ttu-id="0bf15-122">Zie [ETS-eigenschappen](properties.md)voor meer informatie over deze typen eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="0bf15-122">For more information about these types of properties, see [ETS properties](properties.md).</span></span>

## <a name="ets-methods"></a><span data-ttu-id="0bf15-123">ETS-methoden</span><span class="sxs-lookup"><span data-stu-id="0bf15-123">ETS methods</span></span>

<span data-ttu-id="0bf15-124">ETS-methoden zijn leden waarmee argumenten kunnen worden geretourneerd, kunnen resultaten retour neren en kunnen niet aan de linkerkant van een expressie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0bf15-124">ETS methods are members that can take arguments, may return results, and cannot appear on the left-hand side of an expression.</span></span> <span data-ttu-id="0bf15-125">Ze omvatten code methoden, Power shell-methoden en script methoden.</span><span class="sxs-lookup"><span data-stu-id="0bf15-125">They include code methods, PowerShell methods, and script methods.</span></span>
<span data-ttu-id="0bf15-126">Zie voor meer informatie over deze typen methoden ETS- [methoden](methods.md).</span><span class="sxs-lookup"><span data-stu-id="0bf15-126">For more information about these types of methods, see [ETS methods](methods.md).</span></span>
