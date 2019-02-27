---
title: Hoe u een Zie ook sectie toevoegen aan een Help-onderwerp Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848452"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="4e93c-102">Een gedeelte Zie ook toevoegen aan een Help-onderwerp over providers</span><span class="sxs-lookup"><span data-stu-id="4e93c-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="4e93c-103">In deze sectie wordt uitgelegd hoe u voor het vullen van de **Zie ook** gedeelte van een provider help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4e93c-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="4e93c-104">De **Zie ook** sectie bestaat uit een lijst met onderwerpen die betrekking hebben op de provider of de gebruiker beter te begrijpen en gebruiken van de provider kan helpen.</span><span class="sxs-lookup"><span data-stu-id="4e93c-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="4e93c-105">De lijst met onderwerpen help van de cmdlet, provider hulp kunt opnemen en conceptuele ('about'), help-onderwerpen in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e93c-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="4e93c-106">Het kan ook betekenen verwijzingen naar boeken, document en online onderwerpen, waaronder een onlineversie van de huidige provider help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4e93c-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="4e93c-107">Als u naar de online-onderwerpen verwijst, geeft u de URI of een zoekterm in tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="4e93c-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="4e93c-108">De `Get-Help` cmdlet niet koppelen of omleiden naar een van de onderwerpen in de lijst.</span><span class="sxs-lookup"><span data-stu-id="4e93c-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="4e93c-109">Ook de `Online` parameter van de `Get-Help` cmdlet werkt niet met behulp van de provider.</span><span class="sxs-lookup"><span data-stu-id="4e93c-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="4e93c-110">De sectie Zie ook is gemaakt op basis van de `RelatedLinks` -element en de labels die deze bevat.</span><span class="sxs-lookup"><span data-stu-id="4e93c-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="4e93c-111">De volgende XML-code laat zien hoe de labels toevoegen.</span><span class="sxs-lookup"><span data-stu-id="4e93c-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="4e93c-112">'Zie ook' onderwerpen toevoegen</span><span class="sxs-lookup"><span data-stu-id="4e93c-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="4e93c-113">In de *AssemblyName*.dll-help.xml-bestand, vanuit de `providerHelp` element toevoegen een `RelatedLinks` element.</span><span class="sxs-lookup"><span data-stu-id="4e93c-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="4e93c-114">De `RelatedLinks` element moet het laatste element in de `providerHelp` element.</span><span class="sxs-lookup"><span data-stu-id="4e93c-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="4e93c-115">Slechts één `RelatedLinks` element is toegestaan in elke provider help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4e93c-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="4e93c-116">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="4e93c-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="4e93c-117">Voor elk onderwerp in de **Zie ook** sectie, binnen de `RelatedLinks` element toevoegen een `navigationLink` element.</span><span class="sxs-lookup"><span data-stu-id="4e93c-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="4e93c-118">Klik, vanuit elk `navigationLink` -element, Voeg een `linkText` -element en een `uri` element.</span><span class="sxs-lookup"><span data-stu-id="4e93c-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="4e93c-119">Als u niet de `uri` -element, kunt u dit toevoegen als een leeg element (\<uri / >).</span><span class="sxs-lookup"><span data-stu-id="4e93c-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="4e93c-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="4e93c-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="4e93c-121">Typ de naam van het onderwerp tussen de `linkText` tags.</span><span class="sxs-lookup"><span data-stu-id="4e93c-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="4e93c-122">Als u een URI opgeeft, typt u het tussen de `uri` tags.</span><span class="sxs-lookup"><span data-stu-id="4e93c-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="4e93c-123">Om aan te geven van de online versie van de help-onderwerp, van de huidige provider tussen de `linkText` tags, type "onlineversie: ' in plaats van de naam van het onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4e93c-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="4e93c-124">Normaal gesproken de "onlineversie: ' koppeling is het eerste onderwerp in de lijst Zie ook onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4e93c-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="4e93c-125">Het volgende voorbeeld zijn drie Zie ook onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="4e93c-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="4e93c-126">De eerste verwijzen naar de online versie van het huidige onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4e93c-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="4e93c-127">De tweede verwijst naar een Windows PowerShell-cmdlet help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4e93c-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="4e93c-128">De derde verwijst naar een andere online-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4e93c-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```