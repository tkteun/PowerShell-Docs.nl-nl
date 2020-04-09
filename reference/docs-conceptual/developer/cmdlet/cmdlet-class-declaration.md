---
title: Cmdlet-klassen declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 0de49d979c31b0e8d111323a2e1899d97868ec3f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978709"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="4856a-102">Declaratie van cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="4856a-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="4856a-103">Een Microsoft .NET Framework-klasse wordt gedeclareerd als een cmdlet door het **cmdlet** -kenmerk op te geven als meta gegevens voor de klasse.</span><span class="sxs-lookup"><span data-stu-id="4856a-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="4856a-104">(Het **cmdlet** -kenmerk is het enige vereiste kenmerk voor alle cmdlets).</span><span class="sxs-lookup"><span data-stu-id="4856a-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span>
<span data-ttu-id="4856a-105">Wanneer u het **cmdlet** -kenmerk opgeeft, moet u de combi natie van verb en samen stelling opgeven waarmee de cmdlet aan de gebruiker wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="4856a-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="4856a-106">En u moet de Windows Power shell-functionaliteit beschrijven die door de cmdlet wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="4856a-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="4856a-107">Zie voor meer informatie over de declaratie syntaxis die wordt gebruikt om het **cmdlet** -kenmerk op te geven de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4856a-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4856a-108">Het **cmdlet** -kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="4856a-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="4856a-109">De eigenschappen van deze klasse komen overeen met de declaratie parameters die worden gebruikt bij het declareren van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="4856a-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="4856a-110">Woorden</span><span class="sxs-lookup"><span data-stu-id="4856a-110">Nouns</span></span>

<span data-ttu-id="4856a-111">Het zelfstandige naam woord van de cmdlet specificeert de resources waarop de cmdlet optreedt.</span><span class="sxs-lookup"><span data-stu-id="4856a-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="4856a-112">Het zelfstandig naam woord onderscheidt uw cmdlets van andere cmdlets.</span><span class="sxs-lookup"><span data-stu-id="4856a-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="4856a-113">Zelfstandige naam woorden in de namen van de cmdlets moeten specifiek zijn en in het geval van algemene zelfstandig naam woorden, zoals *Server*, is het raadzaam om een kort voor voegsel toe te voegen waarmee uw resource van andere vergelijk bare bronnen wordt onderscheiden.</span><span class="sxs-lookup"><span data-stu-id="4856a-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="4856a-114">Bijvoorbeeld een naam van een cmdlet die een zelfstandig nummer met een voor voegsel bevat `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="4856a-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="4856a-115">Met de combi natie van een specifiek zelfstandig naam woord met een meer algemene term kan de gebruiker snel de cmdlet vinden op basis van de actie en vervolgens de cmdlet identificeren aan de hand van de bijbehorende resource, terwijl het voor komen van onnodige naam duplicatie van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4856a-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="4856a-116">Zie [vereiste ontwikkel richtlijnen](./required-development-guidelines.md)voor een lijst met speciale tekens die niet kunnen worden gebruikt in cmdlet-namen.</span><span class="sxs-lookup"><span data-stu-id="4856a-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="4856a-117">Termen</span><span class="sxs-lookup"><span data-stu-id="4856a-117">Verbs</span></span>

<span data-ttu-id="4856a-118">Wanneer u een term opgeeft, moet u voor de ontwikkelings richtlijnen een van de vooraf gedefinieerde woorden gebruiken die worden meegeleverd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4856a-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="4856a-119">Als u een van deze vooraf gedefinieerde termen gebruikt, zorgt u ervoor dat de cmdlets die u schrijft en de cmdlets die door micro soft en door anderen zijn geschreven, consistent zijn.</span><span class="sxs-lookup"><span data-stu-id="4856a-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="4856a-120">De opdracht ' Get ' wordt bijvoorbeeld gebruikt voor cmdlets waarmee gegevens worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="4856a-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="4856a-121">Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over richt lijnen voor termen.</span><span class="sxs-lookup"><span data-stu-id="4856a-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="4856a-122">Zie [vereiste ontwikkel richtlijnen](./required-development-guidelines.md)voor een lijst met speciale tekens die niet kunnen worden gebruikt in cmdlet-namen.</span><span class="sxs-lookup"><span data-stu-id="4856a-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="4856a-123">Ondersteuning van Windows Power shell-functionaliteit</span><span class="sxs-lookup"><span data-stu-id="4856a-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="4856a-124">Met het kenmerk **cmdlet** kunt u ook opgeven dat uw cmdlet een van de algemene functionaliteit ondersteunt die wordt geboden door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="4856a-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="4856a-125">Dit omvat ondersteuning voor algemene functionaliteit, zoals het bevestigen van de gebruikers feedback (ondersteuning voor de functie ShouldProcess) en ondersteuning voor trans acties.</span><span class="sxs-lookup"><span data-stu-id="4856a-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="4856a-126">(Ondersteuning voor trans acties is geïntroduceerd in Windows Power Shell 2,0).</span><span class="sxs-lookup"><span data-stu-id="4856a-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="4856a-127">Zie voor meer informatie over de declaratie syntaxis die wordt gebruikt om het **cmdlet** -kenmerk op te geven de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4856a-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="4856a-128">Definitie van cmdlet-klasse</span><span class="sxs-lookup"><span data-stu-id="4856a-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="4856a-129">De volgende code is de definitie voor een GetProc-cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="4856a-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="4856a-130">U ziet dat Pascal-behuizing wordt gebruikt en dat de naam van de klasse het werk woord en het zelfstandige woord van de cmdlet bevat.</span><span class="sxs-lookup"><span data-stu-id="4856a-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a><span data-ttu-id="4856a-131">Pascal-behuizing</span><span class="sxs-lookup"><span data-stu-id="4856a-131">Pascal Casing</span></span>

<span data-ttu-id="4856a-132">Wanneer u een naam wilt voor cmdlets, gebruikt u het hoofdletter gebruik.</span><span class="sxs-lookup"><span data-stu-id="4856a-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="4856a-133">De cmdlets `Get-Item` en `Get-ItemProperty` tonen bijvoorbeeld de juiste manier om hoofdletter gebruik te gebruiken wanneer u de naamgeving van cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4856a-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="4856a-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4856a-134">See Also</span></span>

[<span data-ttu-id="4856a-135">System. Management. Automation. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="4856a-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="4856a-136">CmdletAttribute-declaratie</span><span class="sxs-lookup"><span data-stu-id="4856a-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="4856a-137">Namen van cmdlet-termen</span><span class="sxs-lookup"><span data-stu-id="4856a-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="4856a-138">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="4856a-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="4856a-139">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="4856a-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
