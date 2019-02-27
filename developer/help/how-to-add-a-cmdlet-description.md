---
title: Hoe u een beschrijving van de Cmdlet toevoegen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851427"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="48f9a-102">Een cmdlet-beschrijving toevoegen</span><span class="sxs-lookup"><span data-stu-id="48f9a-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="48f9a-103">In deze sectie wordt beschreven hoe u inhoud die wordt weergegeven in de sectie Beschrijving van de cmdlet Help toevoegen.</span><span class="sxs-lookup"><span data-stu-id="48f9a-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="48f9a-104">In het Help-bestand, wordt deze inhoud toegevoegd aan het knooppunt van de opdracht voor elke cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48f9a-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="48f9a-105">Voor een volledige weergave van een Help-bestand, open een van de dll-Help.xml-bestanden zich in de installatiemap van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48f9a-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="48f9a-106">Bijvoorbeeld, worden de inhoud van het bestand Microsoft.PowerShell.Commands.Management.dll Help.xml bevat voor verschillende van de Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="48f9a-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="48f9a-107">Een beschrijving toevoegen</span><span class="sxs-lookup"><span data-stu-id="48f9a-107">To Add a Description</span></span>

- <span data-ttu-id="48f9a-108">Door een uitleg van de belangrijkste functies van de cmdlet in meer detail te beginnen.</span><span class="sxs-lookup"><span data-stu-id="48f9a-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="48f9a-109">In veel gevallen kunt u de termen die worden gebruikt in de cmdletnaam van de wordt uitgelegd en illustratie van de onbekende concepten met een voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="48f9a-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="48f9a-110">Bijvoorbeeld, als de cmdlet worden de gegevens naar een bestand toegevoegd, wordt uitgelegd dat voegt gegevens toe aan het einde van een bestaand bestand.</span><span class="sxs-lookup"><span data-stu-id="48f9a-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="48f9a-111">Als u zoekt alle functies van de cmdlet, bekijk de lijst met parameters.</span><span class="sxs-lookup"><span data-stu-id="48f9a-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="48f9a-112">De primaire functie van de cmdlet wordt beschreven, en vervolgens andere functies en onderdelen.</span><span class="sxs-lookup"><span data-stu-id="48f9a-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="48f9a-113">Als de main-functie van de cmdlet is een eigenschap te wijzigen, maar de cmdlet alle eigenschappen kunt wijzigen, stel dit in de gedetailleerde beschrijving.</span><span class="sxs-lookup"><span data-stu-id="48f9a-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="48f9a-114">Als de cmdlet-parameters, de gebruikers informatie op verschillende manieren werven kunnen, uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="48f9a-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="48f9a-115">Bevatten informatie over de manieren waarop dat gebruikers kunnen worden gebruikt voor het gebruik van de cmdlet, naast de hand liggende gebruikt.</span><span class="sxs-lookup"><span data-stu-id="48f9a-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="48f9a-116">Bijvoorbeeld, kunt u het object dat de `Get-Host` cmdlet haalt de kleur van tekst in de Windows PowerShell-opdrachtvenster wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="48f9a-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="48f9a-117">Voorbeeld:  "De `Get-Acl` -cmdlet krijgt u objecten die staan voor de security descriptor van een bestand of de resource.</span><span class="sxs-lookup"><span data-stu-id="48f9a-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="48f9a-118">De security descriptor bevat de toegangsbeheerlijsten (ACL's) van de resource.</span><span class="sxs-lookup"><span data-stu-id="48f9a-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="48f9a-119">De ACL Hiermee geeft u de machtigingen die gebruikers en gebruikersgroepen hebben toegang tot de bron."</span><span class="sxs-lookup"><span data-stu-id="48f9a-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="48f9a-120">De gedetailleerde beschrijving moet worden beschreven de cmdlet, maar deze moet niet worden beschreven concepten die gebruikmaakt van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48f9a-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="48f9a-121">Definities van concept in aanvullende opmerkingen plaatsen.</span><span class="sxs-lookup"><span data-stu-id="48f9a-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="48f9a-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="48f9a-122">See Also</span></span>

[<span data-ttu-id="48f9a-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="48f9a-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
