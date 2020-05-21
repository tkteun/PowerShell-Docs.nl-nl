---
title: Een sectie ' Zie ook ' toevoegen aan het Help-onderwerp van een provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: b6561120d1bbe848ab4ebcdec7de92c6cad96314
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564820"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="5600c-102">Een gedeelte Zie ook toevoegen aan een Help-onderwerp over providers</span><span class="sxs-lookup"><span data-stu-id="5600c-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="5600c-103">In deze sectie wordt uitgelegd hoe u de sectie **Zie ook** in het Help-onderwerp van een provider vult.</span><span class="sxs-lookup"><span data-stu-id="5600c-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="5600c-104">De sectie **Zie ook** bestaat uit een lijst met onderwerpen die betrekking hebben op de provider of waarmee de gebruiker de provider beter kan begrijpen en gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5600c-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="5600c-105">De lijst met onderwerpen kan Help-onderwerpen over de cmdlet Help, de Help van de provider en conceptuele informatie ("about") bevatten in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="5600c-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="5600c-106">Het kan ook verwijzingen bevatten naar boeken, papier en online onderwerpen, met inbegrip van een online versie van het Help-onderwerp van de huidige provider.</span><span class="sxs-lookup"><span data-stu-id="5600c-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="5600c-107">Wanneer u verwijst naar online-onderwerpen, geeft u de URI of een zoek term op in tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="5600c-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="5600c-108">De `Get-Help` cmdlet wordt niet gekoppeld of omgeleid naar een van de onderwerpen in de lijst.</span><span class="sxs-lookup"><span data-stu-id="5600c-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="5600c-109">De `Online` para meter van de `Get-Help` cmdlet werkt ook niet met de Help van de provider.</span><span class="sxs-lookup"><span data-stu-id="5600c-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="5600c-110">De sectie Zie ook wordt gemaakt van het `RelatedLinks` element en de labels die het bevat.</span><span class="sxs-lookup"><span data-stu-id="5600c-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="5600c-111">In het volgende XML-bestand ziet u hoe u de tags kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="5600c-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="5600c-112">Voor het toevoegen van ' Zie ook onderwerpen '</span><span class="sxs-lookup"><span data-stu-id="5600c-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="5600c-113">Voeg in het bestand *assemblyname*. dll-Help. XML binnen het- `providerHelp` element een- `RelatedLinks` element toe.</span><span class="sxs-lookup"><span data-stu-id="5600c-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="5600c-114">Het `RelatedLinks` element moet het laatste element in het- `providerHelp` element zijn.</span><span class="sxs-lookup"><span data-stu-id="5600c-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="5600c-115">Er is slechts één `RelatedLinks` element toegestaan in elk Help-onderwerp van de provider.</span><span class="sxs-lookup"><span data-stu-id="5600c-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="5600c-116">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5600c-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="5600c-117">Voor elk onderwerp in de sectie **Zie ook** , binnen het `RelatedLinks` element, voegt u een- `navigationLink` element toe.</span><span class="sxs-lookup"><span data-stu-id="5600c-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="5600c-118">Voeg vervolgens binnen elk `navigationLink` element één `linkText` element en één element toe `uri` .</span><span class="sxs-lookup"><span data-stu-id="5600c-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="5600c-119">Als u het element niet gebruikt `uri` , kunt u dit toevoegen als een leeg element ( \< uri/>).</span><span class="sxs-lookup"><span data-stu-id="5600c-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="5600c-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5600c-120">For example:</span></span>

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

3. <span data-ttu-id="5600c-121">Typ de naam van het onderwerp tussen de `linkText` Tags.</span><span class="sxs-lookup"><span data-stu-id="5600c-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="5600c-122">Als u een URI opgeeft, typt u deze tussen de `uri` Tags.</span><span class="sxs-lookup"><span data-stu-id="5600c-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="5600c-123">Als u de online versie van het Help-onderwerp van de huidige provider wilt aangeven tussen de `linkText` Tags, typt u ' online versie: ' in plaats van de naam van het onderwerp.</span><span class="sxs-lookup"><span data-stu-id="5600c-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="5600c-124">Normaal gesp roken is de koppeling ' online versie: ' het eerste onderwerp in de lijst Zie ook topics.</span><span class="sxs-lookup"><span data-stu-id="5600c-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="5600c-125">In het volgende voor beeld zijn drie Zie ook onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="5600c-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="5600c-126">De eerste keer naar de online versie van het huidige onderwerp.</span><span class="sxs-lookup"><span data-stu-id="5600c-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="5600c-127">De tweede verwijst naar het Help-onderwerp van een Windows Power shell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5600c-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="5600c-128">De derde verwijst naar een ander online onderwerp.</span><span class="sxs-lookup"><span data-stu-id="5600c-128">The third refers to another online topic.</span></span>

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
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
