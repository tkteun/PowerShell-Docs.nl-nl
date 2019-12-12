---
title: Een cmdlet-beschrijving toevoegen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353317"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="82b8e-102">Een cmdlet-beschrijving toevoegen</span><span class="sxs-lookup"><span data-stu-id="82b8e-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="82b8e-103">In deze sectie wordt beschreven hoe u inhoud kunt toevoegen die wordt weer gegeven in de sectie Beschrijving van de Help van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="82b8e-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="82b8e-104">In het Help-bestand wordt deze inhoud toegevoegd aan het opdracht knooppunt voor elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="82b8e-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="82b8e-105">Voor een volledig overzicht van een Help-bestand opent u een van de dll-Help. XML-bestanden die zich in de installatiemap van Windows Power shell bevinden.</span><span class="sxs-lookup"><span data-stu-id="82b8e-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="82b8e-106">Het bestand micro soft. Power shell. commands. Management. dll-Help. XML bevat bijvoorbeeld inhoud voor verschillende Windows Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="82b8e-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="82b8e-107">Een beschrijving toevoegen</span><span class="sxs-lookup"><span data-stu-id="82b8e-107">To Add a Description</span></span>

- <span data-ttu-id="82b8e-108">Begin met het uitleggen van de basis functies van de cmdlet in meer detail.</span><span class="sxs-lookup"><span data-stu-id="82b8e-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="82b8e-109">In veel gevallen kunt u de termen die worden gebruikt in de naam van de cmdlet uitleggen en niet-bekende concepten illustreren met een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="82b8e-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="82b8e-110">Als met de cmdlet bijvoorbeeld gegevens worden toegevoegd aan een bestand, wordt uitgelegd dat er gegevens aan het einde van een bestaand bestand worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="82b8e-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="82b8e-111">Als u alle functies van de cmdlet wilt vinden, controleert u de lijst met para meters.</span><span class="sxs-lookup"><span data-stu-id="82b8e-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="82b8e-112">Beschrijf de primaire functie van de cmdlet en voeg vervolgens andere functies en onderdelen toe.</span><span class="sxs-lookup"><span data-stu-id="82b8e-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="82b8e-113">Als de hoofd functie van de cmdlet bijvoorbeeld één eigenschap wijzigt, maar de cmdlet alle eigenschappen kan wijzigen, doet u dat in de gedetailleerde beschrijving.</span><span class="sxs-lookup"><span data-stu-id="82b8e-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="82b8e-114">Als met de cmdlet-para meters de gebruikers informatie op verschillende manieren kunnen vragen, moet u deze uitleggen.</span><span class="sxs-lookup"><span data-stu-id="82b8e-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="82b8e-115">Neem naast het duidelijke gebruik ook informatie op over manieren waarop gebruikers de cmdlet kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="82b8e-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="82b8e-116">U kunt bijvoorbeeld het object gebruiken dat door de `Get-Host`-cmdlet wordt opgehaald om de kleur van tekst in het Windows Power shell-opdracht venster te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="82b8e-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="82b8e-117">Voor beeld: met de cmdlet `Get-Acl` worden objecten opgehaald die de security descriptor van een bestand of resource vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="82b8e-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="82b8e-118">De security descriptor bevat de toegangs beheer lijsten (Acl's) van de resource.</span><span class="sxs-lookup"><span data-stu-id="82b8e-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="82b8e-119">In de ACL worden de machtigingen opgegeven die gebruikers en gebruikers groepen hebben om toegang te krijgen tot de resource.</span><span class="sxs-lookup"><span data-stu-id="82b8e-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="82b8e-120">In de gedetailleerde beschrijving wordt de cmdlet beschreven, maar het mag niet de concepten beschrijven die de cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="82b8e-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="82b8e-121">Concept definities plaatsen in aanvullende notities.</span><span class="sxs-lookup"><span data-stu-id="82b8e-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="82b8e-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="82b8e-122">See Also</span></span>

[<span data-ttu-id="82b8e-123">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="82b8e-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
