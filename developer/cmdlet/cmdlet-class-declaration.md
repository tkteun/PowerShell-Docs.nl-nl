---
title: Cmdlet klassendeclaratie | Microsoft Docs
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
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068637"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="0fe43-102">Declaratie van cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="0fe43-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="0fe43-103">Een Microsoft .NET Framework-klasse is gedeclareerd als een cmdlet door op te geven de **Cmdlet** kenmerk, zoals metagegevens voor de klasse.</span><span class="sxs-lookup"><span data-stu-id="0fe43-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="0fe43-104">(De **Cmdlet** kenmerk is de enige vereiste kenmerk voor alle cmdlets).</span><span class="sxs-lookup"><span data-stu-id="0fe43-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="0fe43-105">Wanneer u opgeeft de **Cmdlet** kenmerk, moet u het werkwoord-en-zelfstandig naamwoord paar die de cmdlet voor de gebruiker identificeert.</span><span class="sxs-lookup"><span data-stu-id="0fe43-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="0fe43-106">Daarnaast moet u de Windows PowerShell-functionaliteit die ondersteuning biedt voor de cmdlet beschrijft.</span><span class="sxs-lookup"><span data-stu-id="0fe43-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="0fe43-107">Voor meer informatie over de syntaxis van de declaratie die wordt gebruikt om op te geven de **Cmdlet** kenmerk, Zie [Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0fe43-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0fe43-108">De **Cmdlet** kenmerk wordt gedefinieerd door de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klasse.</span><span class="sxs-lookup"><span data-stu-id="0fe43-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="0fe43-109">De eigenschappen van deze klasse komen overeen met de declaratie-parameters die worden gebruikt wanneer u het kenmerk declareren.</span><span class="sxs-lookup"><span data-stu-id="0fe43-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="0fe43-110">Zelfstandige naamwoorden</span><span class="sxs-lookup"><span data-stu-id="0fe43-110">Nouns</span></span>

<span data-ttu-id="0fe43-111">Het zelfstandig naamwoord van de cmdlet Hiermee geeft u de resources waarop de cmdlet fungeert.</span><span class="sxs-lookup"><span data-stu-id="0fe43-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="0fe43-112">Het zelfstandig naamwoord wordt onderscheid gemaakt tussen de cmdlets van andere cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0fe43-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="0fe43-113">Zelfstandige naamwoorden in namen van de cmdlets moet specifiek, en in het geval van algemene zelfstandige naamwoorden, zoals *server*, het is raadzaam om toe te voegen een korte voorvoegsel dat wordt onderscheid gemaakt uw resource vanuit andere vergelijkbare resources tussen.</span><span class="sxs-lookup"><span data-stu-id="0fe43-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="0fe43-114">Bijvoorbeeld, een cmdletnaam met een zelfstandig naamwoord met het voorvoegsel is `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="0fe43-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="0fe43-115">De combinatie van een specifieke zelfstandig naamwoord met een algemene term kan de gebruiker de cmdlet snel vinden door de bijbehorende actie en klikt u vervolgens de cmdlet identificeren door de resource zonder duplicatie van onnodige cmdlet-naam.</span><span class="sxs-lookup"><span data-stu-id="0fe43-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="0fe43-116">Zie voor een lijst van speciale tekens die niet in de namen van de cmdlets worden gebruikt, [vereist ontwikkeling richtlijnen](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="0fe43-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="0fe43-117">Termen</span><span class="sxs-lookup"><span data-stu-id="0fe43-117">Verbs</span></span>

<span data-ttu-id="0fe43-118">Wanneer u een term opgeeft, wordt de richtlijnen voor ontwikkeling moeten u een van de vooraf gedefinieerde bewerkingen die worden geleverd door Windows PowerShell te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0fe43-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="0fe43-119">Met behulp van een van deze vooraf gedefinieerde bewerkingen, wordt u zorgen voor consistentie tussen de cmdlets die u schrijft en de cmdlets die zijn ontwikkeld door Microsoft en door anderen.</span><span class="sxs-lookup"><span data-stu-id="0fe43-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="0fe43-120">Bijvoorbeeld, wordt de term 'Ophalen' gebruikt voor cmdlets waarmee gegevens worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0fe43-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="0fe43-121">Zie voor meer informatie over richtlijnen voor termen [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="0fe43-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="0fe43-122">Zie voor een lijst van speciale tekens die niet in de namen van de cmdlets worden gebruikt, [vereist ontwikkeling richtlijnen](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="0fe43-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="0fe43-123">Ondersteuning van Windows PowerShell-functionaliteit</span><span class="sxs-lookup"><span data-stu-id="0fe43-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="0fe43-124">De **Cmdlet** kenmerk ook kunt u opgeven dat de cmdlet biedt ondersteuning voor enkele van de algemene functionaliteit die wordt geleverd door Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0fe43-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="0fe43-125">Dit omvat ondersteuning voor algemene functionaliteit zoals (aangeduid als ondersteuning voor de functie shouldprocess wordt overgeslagen) de bevestiging van de gebruiker feedback en ondersteuning voor transacties.</span><span class="sxs-lookup"><span data-stu-id="0fe43-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="0fe43-126">(Ondersteuning voor transacties is geïntroduceerd in Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="0fe43-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="0fe43-127">Voor meer informatie over de syntaxis van de declaratie die wordt gebruikt om op te geven de **Cmdlet** kenmerk, Zie [Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="0fe43-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="0fe43-128">De definitie van de cmdlet-klasse</span><span class="sxs-lookup"><span data-stu-id="0fe43-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="0fe43-129">De volgende code wordt de definitie voor een cmdlet GetProc klasse.</span><span class="sxs-lookup"><span data-stu-id="0fe43-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="0fe43-130">U ziet dat Pascal hoofdlettergebruik wordt gebruikt en dat de naam van de klasse het werkwoord en een zelfstandig naamwoord van de cmdlet bevat.</span><span class="sxs-lookup"><span data-stu-id="0fe43-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="0fe43-131">Pascal hoofdlettergebruik</span><span class="sxs-lookup"><span data-stu-id="0fe43-131">Pascal Casing</span></span>

<span data-ttu-id="0fe43-132">Wanneer u cmdlets naam, gebruikt u Pascal hoofdlettergebruik.</span><span class="sxs-lookup"><span data-stu-id="0fe43-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="0fe43-133">Bijvoorbeeld, de `Get-Item` en `Get-ItemProperty` cmdlets weer de juiste manier hoofdletters gebruikt bij het benoemen van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0fe43-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fe43-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0fe43-134">See Also</span></span>

[<span data-ttu-id="0fe43-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="0fe43-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="0fe43-136">CmdletAttribute declaratie</span><span class="sxs-lookup"><span data-stu-id="0fe43-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="0fe43-137">Namen van de cmdlet-bewerking</span><span class="sxs-lookup"><span data-stu-id="0fe43-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="0fe43-138">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0fe43-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="0fe43-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0fe43-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
