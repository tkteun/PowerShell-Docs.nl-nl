---
title: Ondersteunende Online Help | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082138"
---
# <a name="supporting-online-help"></a><span data-ttu-id="22aa4-102">Ondersteunende Online Help</span><span class="sxs-lookup"><span data-stu-id="22aa4-102">Supporting Online Help</span></span>

<span data-ttu-id="22aa4-103">Vanaf Windows PowerShell 3.0, er zijn twee manieren voor de ondersteuning van de `Get-Help` Online-functie voor Windows PowerShell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="22aa4-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="22aa4-104">In dit onderwerp wordt uitgelegd hoe u deze functie voor verschillende opdrachttypen implementeren.</span><span class="sxs-lookup"><span data-stu-id="22aa4-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="22aa4-105">Informatie over Online Help</span><span class="sxs-lookup"><span data-stu-id="22aa4-105">About Online Help</span></span>

<span data-ttu-id="22aa4-106">Online-help is altijd een essentieel onderdeel van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22aa4-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="22aa4-107">Hoewel de `Get-Help` cmdlet geeft help-onderwerpen bij de opdrachtprompt, die veel gebruikers de voorkeur geeft aan de ervaring voor het lezen van online, met inbegrip van kleurcodering, hyperlinks en delen ideeën in Community-inhoud en documenten op basis van een wiki.</span><span class="sxs-lookup"><span data-stu-id="22aa4-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="22aa4-108">Voordat u de opkomst van bij te werken Help opgegeven online-help belangrijker nog, de meest recente versie van de help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="22aa4-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="22aa4-109">Met de komst van bij te werken Help in Windows PowerShell 3.0, in online-help nog steeds een belangrijke rol speelt.</span><span class="sxs-lookup"><span data-stu-id="22aa4-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="22aa4-110">Naast de flexibele gebruikerservaring biedt online-help help voor gebruikers die niet of niet bij te werken Help voor het downloaden van help-onderwerpen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="22aa4-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="22aa4-111">Hoe Get-Help-Online werkt</span><span class="sxs-lookup"><span data-stu-id="22aa4-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="22aa4-112">Om u te helpen bij het zoeken van de online help-onderwerpen voor opdrachten de `Get-Help` opdracht heeft een Online-parameter die de online versie van help-onderwerp voor een opdracht in de standaardinternetbrowser van de gebruiker wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="22aa4-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="22aa4-113">Bijvoorbeeld, de volgende opdracht wordt geopend met de online help-onderwerp voor de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22aa4-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="22aa4-114">Voor het implementeren van `Get-Help` -Online, de `Get-Help` cmdlet ziet er uit voor een Uniform Resource Identifier (URI) voor de versie van de online help-onderwerp in de volgende locaties.</span><span class="sxs-lookup"><span data-stu-id="22aa4-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="22aa4-115">De eerste koppeling in de sectie Verwante koppelingen van het help-onderwerp voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="22aa4-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="22aa4-116">Het help-onderwerp moet worden geïnstalleerd op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="22aa4-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="22aa4-117">Deze functie is geïntroduceerd in Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="22aa4-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="22aa4-118">De eigenschap HelpUri van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="22aa4-118">The HelpUri property of any command.</span></span> <span data-ttu-id="22aa4-119">De eigenschap HelpUri is toegankelijk is, zelfs wanneer het help-onderwerp voor de opdracht is niet geïnstalleerd op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="22aa4-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="22aa4-120">Deze functie is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="22aa4-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="22aa4-121">`Get-Help` zoekt naar een URI zijn die in de eerste vermelding in het gedeelte Verwante koppelingen alvorens de waarde van de eigenschap HelpUri.</span><span class="sxs-lookup"><span data-stu-id="22aa4-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="22aa4-122">Als de eigenschapswaarde onjuist is of is gewijzigd, kunt u deze overschrijven door te voeren van een andere waarde in de eerste gerelateerde koppeling.</span><span class="sxs-lookup"><span data-stu-id="22aa4-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="22aa4-123">De eerste gerelateerde koppeling werkt echter alleen wanneer de help-onderwerpen op de computer van de gebruiker zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="22aa4-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="22aa4-124">Een URI toe te voegen aan de eerste gerelateerde koppeling van een opdracht help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="22aa4-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="22aa4-125">U kunt ondersteunen `Get-Help` -Online voor elke opdracht door een geldige URI toe te voegen aan het eerste item in de sectie Verwante koppelingen van het help-onderwerp op basis van XML voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="22aa4-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="22aa4-126">Deze optie is alleen geldig in de help-onderwerpen op basis van XML en werkt alleen als het help-onderwerp is geïnstalleerd op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="22aa4-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="22aa4-127">Wanneer het help-onderwerp is geïnstalleerd en de URI is gevuld, deze waarde heeft voorrang op de **HelpUri** eigenschap van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="22aa4-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="22aa4-128">Zie voor meer informatie over het help-onderwerpen op basis van XML voor opdrachten [Writing XML-Based Help-onderwerpen voor opdrachten](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="22aa4-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="22aa4-129">Ter ondersteuning van deze functie, moet de URI worden weergegeven de `maml:uri` element onder de eerste `maml:relatedLinks/maml:navigationLink` -element in de `maml:relatedLinks` element.</span><span class="sxs-lookup"><span data-stu-id="22aa4-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="22aa4-130">Het volgende XML-bestand ziet u de juiste plaatsing van de URI.</span><span class="sxs-lookup"><span data-stu-id="22aa4-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="22aa4-131">De ' onlineversie: "tekst in de `maml:linkText` element is een aanbevolen procedure, maar dit is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="22aa4-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="22aa4-132">De eigenschap HelpUri aan een opdracht toe te voegen</span><span class="sxs-lookup"><span data-stu-id="22aa4-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="22aa4-133">Deze sectie wordt beschreven hoe u de eigenschap HelpUri toevoegen aan de opdrachten van verschillende typen.</span><span class="sxs-lookup"><span data-stu-id="22aa4-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="22aa4-134">Een eigenschap HelpUri toe te voegen aan een Cmdlet</span><span class="sxs-lookup"><span data-stu-id="22aa4-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="22aa4-135">Voor cmdlets die zijn geschreven in C#, Voeg een **HelpUri** kenmerk aan de Cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="22aa4-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="22aa4-136">De waarde van het kenmerk moet een URI die met 'http' of 'https begint'.</span><span class="sxs-lookup"><span data-stu-id="22aa4-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="22aa4-137">De volgende code toont het kenmerk HelpUri van de `Get-History` cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="22aa4-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="22aa4-138">Een eigenschap HelpUri toe te voegen aan een geavanceerde functie</span><span class="sxs-lookup"><span data-stu-id="22aa4-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="22aa4-139">Voor geavanceerde functies, voegt u toe een **HelpUri** eigenschap in op de **CmdletBinding** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="22aa4-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="22aa4-140">De waarde van de eigenschap moet een URI die met 'http' of 'https begint'.</span><span class="sxs-lookup"><span data-stu-id="22aa4-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="22aa4-141">De volgende code toont het kenmerk HelpUri van de functie New-agenda</span><span class="sxs-lookup"><span data-stu-id="22aa4-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="22aa4-142">Een kenmerk HelpUri toe te voegen aan een CIM-opdracht</span><span class="sxs-lookup"><span data-stu-id="22aa4-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="22aa4-143">Voor de CIM-opdrachten, voegt u toe een **HelpUri** kenmerk aan de **CmdletMetadata** element in het bestand CDXML.</span><span class="sxs-lookup"><span data-stu-id="22aa4-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="22aa4-144">De waarde van het kenmerk moet een URI die met 'http' of 'https begint'.</span><span class="sxs-lookup"><span data-stu-id="22aa4-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="22aa4-145">De volgende code toont het kenmerk HelpUri van de begin-Debug CIM-opdracht</span><span class="sxs-lookup"><span data-stu-id="22aa4-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="22aa4-146">Een kenmerk HelpUri toe te voegen aan een werkstroom</span><span class="sxs-lookup"><span data-stu-id="22aa4-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="22aa4-147">Voor werkstromen die zijn geschreven in de Windows PowerShell-taal, voegt u toe een **. ExternalHelp** Opmerking-richtlijn voor de werkstroomcode.</span><span class="sxs-lookup"><span data-stu-id="22aa4-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="22aa4-148">De waarde van de richtlijn moet een URI die met 'http' of 'https begint'.</span><span class="sxs-lookup"><span data-stu-id="22aa4-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="22aa4-149">De eigenschap HelpUri wordt niet ondersteund voor werkstromen op basis van XAML in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="22aa4-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="22aa4-150">De volgende code toont de. ExternalHelp richtlijn in een werkstroombestand.</span><span class="sxs-lookup"><span data-stu-id="22aa4-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```