---
title: Ondersteuning voor online-Help | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: de25b099e61f82891daff87c4c73bb8cad9111a4
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83559978"
---
# <a name="supporting-online-help"></a><span data-ttu-id="440a2-102">Ondersteunende online help</span><span class="sxs-lookup"><span data-stu-id="440a2-102">Supporting Online Help</span></span>

<span data-ttu-id="440a2-103">Vanaf Windows Power Shell 3,0 zijn er twee manieren om de `Get-Help` online functie voor Windows Power shell-opdrachten te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="440a2-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="440a2-104">In dit onderwerp wordt uitgelegd hoe u deze functie implementeert voor verschillende opdracht typen.</span><span class="sxs-lookup"><span data-stu-id="440a2-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="440a2-105">Online-Help</span><span class="sxs-lookup"><span data-stu-id="440a2-105">About Online Help</span></span>

<span data-ttu-id="440a2-106">Online-Help is altijd een essentieel onderdeel van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="440a2-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="440a2-107">Hoewel `Get-Help` met de cmdlet Help-onderwerpen worden weer gegeven bij de opdracht prompt, hebben veel gebruikers de voor keur aan het online lezen, met inbegrip van kleur codering, hyper links en het delen van ideeën in Community-inhoud en documenten op basis van wiki.</span><span class="sxs-lookup"><span data-stu-id="440a2-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="440a2-108">In de online Help werd de meest recente versie van de Help-bestanden het belangrijkst, vóór de komst van de Help-informatie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="440a2-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="440a2-109">Met de komst van de bijwerk bare Help in Windows Power Shell 3,0 speelt de online Help nog steeds een belang rijke rol af.</span><span class="sxs-lookup"><span data-stu-id="440a2-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="440a2-110">Naast de flexibele gebruikers ervaring biedt de online Help hulp bij gebruikers die geen Bewerk bare Help kunnen gebruiken om Help-onderwerpen te downloaden.</span><span class="sxs-lookup"><span data-stu-id="440a2-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="440a2-111">Help-online werken</span><span class="sxs-lookup"><span data-stu-id="440a2-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="440a2-112">Om gebruikers te helpen de online-Help-onderwerpen voor-opdrachten te vinden, `Get-Help` heeft de opdracht een online-para meter waarmee de online versie van het Help-onderwerp voor een opdracht in de standaard browser van de gebruiker wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="440a2-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="440a2-113">Met de volgende opdracht wordt bijvoorbeeld het online-Help-onderwerp voor de `Invoke-Command` cmdlet geopend.</span><span class="sxs-lookup"><span data-stu-id="440a2-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="440a2-114">Om `Get-Help` -online te implementeren, `Get-Help` zoekt de cmdlet naar een Uniform Resource Identifier (URI) voor het Help-onderwerp online versie op de volgende locaties.</span><span class="sxs-lookup"><span data-stu-id="440a2-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="440a2-115">De eerste koppeling in het gedeelte Verwante koppelingen van het Help-onderwerp voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="440a2-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="440a2-116">Het Help-onderwerp moet worden geïnstalleerd op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="440a2-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="440a2-117">Deze functie is geïntroduceerd in Windows Power Shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="440a2-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="440a2-118">De eigenschap HelpUri van een wille keurige opdracht.</span><span class="sxs-lookup"><span data-stu-id="440a2-118">The HelpUri property of any command.</span></span> <span data-ttu-id="440a2-119">De eigenschap HelpUri is toegankelijk, zelfs wanneer het Help-onderwerp voor de opdracht niet is geïnstalleerd op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="440a2-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="440a2-120">Deze functie is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="440a2-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="440a2-121">`Get-Help`zoekt naar een URI in de eerste vermelding in de sectie verwante koppelingen voordat u de waarde van de eigenschap HelpUri ophaalt.</span><span class="sxs-lookup"><span data-stu-id="440a2-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="440a2-122">Als de waarde van de eigenschap onjuist is of is gewijzigd, kunt u deze overschrijven door een andere waarde in te voeren in de eerste gerelateerde koppeling.</span><span class="sxs-lookup"><span data-stu-id="440a2-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="440a2-123">De eerste gerelateerde koppeling werkt echter alleen als de Help-onderwerpen zijn geïnstalleerd op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="440a2-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="440a2-124">Een URI toevoegen aan de eerste gerelateerde koppeling van een Help-onderwerp van een opdracht</span><span class="sxs-lookup"><span data-stu-id="440a2-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="440a2-125">U kunt `Get-Help` online een wille keurige opdracht ondersteunen door een geldige URI toe te voegen aan de eerste vermelding in de sectie verwante koppelingen van het Help-onderwerp op basis van XML voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="440a2-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="440a2-126">Deze optie is alleen geldig in Help-onderwerpen op basis van XML en werkt alleen wanneer het Help-onderwerp op de computer van de gebruiker is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="440a2-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="440a2-127">Wanneer het Help-onderwerp is geïnstalleerd en de URI is gevuld, heeft deze waarde voor rang op de eigenschap **HelpUri** van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="440a2-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="440a2-128">Ter ondersteuning van deze functie moet de URI worden weer gegeven in het- `maml:uri` element onder het eerste `maml:relatedLinks/maml:navigationLink` element in het- `maml:relatedLinks` element.</span><span class="sxs-lookup"><span data-stu-id="440a2-128">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="440a2-129">In het volgende XML-bestand wordt de juiste plaatsing van de URI weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="440a2-129">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="440a2-130">De tekst ' Online version: ' in het `maml:linkText` element is een Best Practice, maar dit is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="440a2-130">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="440a2-131">De eigenschap HelpUri toevoegen aan een opdracht</span><span class="sxs-lookup"><span data-stu-id="440a2-131">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="440a2-132">In deze sectie wordt uitgelegd hoe u de eigenschap HelpUri kunt toevoegen aan opdrachten van verschillende typen.</span><span class="sxs-lookup"><span data-stu-id="440a2-132">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="440a2-133">Een HelpUri-eigenschap toevoegen aan een cmdlet</span><span class="sxs-lookup"><span data-stu-id="440a2-133">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="440a2-134">Voor cmdlets die zijn geschreven in C#, voegt u een **HelpUri** -kenmerk toe aan de klasse cmdlet.</span><span class="sxs-lookup"><span data-stu-id="440a2-134">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="440a2-135">De waarde van het kenmerk moet een URI zijn die begint met http of https.</span><span class="sxs-lookup"><span data-stu-id="440a2-135">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="440a2-136">Met de volgende code wordt het kenmerk HelpUri van de `Get-History` klasse cmdlet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="440a2-136">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="440a2-137">Een eigenschap HelpUri toevoegen aan een geavanceerde functie</span><span class="sxs-lookup"><span data-stu-id="440a2-137">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="440a2-138">Voor geavanceerde functies voegt u een eigenschap **HelpUri** toe aan het kenmerk **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="440a2-138">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="440a2-139">De waarde van de eigenschap moet een URI zijn die begint met http of https.</span><span class="sxs-lookup"><span data-stu-id="440a2-139">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="440a2-140">De volgende code toont het kenmerk HelpUri van de functie New-Calendar</span><span class="sxs-lookup"><span data-stu-id="440a2-140">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="440a2-141">Een HelpUri-kenmerk toevoegen aan een CIM-opdracht</span><span class="sxs-lookup"><span data-stu-id="440a2-141">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="440a2-142">Voor CIM-opdrachten voegt u een **HelpUri** -kenmerk toe aan het **CmdletMetadata** -element in het CDXML-bestand.</span><span class="sxs-lookup"><span data-stu-id="440a2-142">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="440a2-143">De waarde van het kenmerk moet een URI zijn die begint met http of https.</span><span class="sxs-lookup"><span data-stu-id="440a2-143">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="440a2-144">De volgende code toont het kenmerk HelpUri van de CIM-opdracht start-debug</span><span class="sxs-lookup"><span data-stu-id="440a2-144">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="440a2-145">Een HelpUri-kenmerk toevoegen aan een werk stroom</span><span class="sxs-lookup"><span data-stu-id="440a2-145">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="440a2-146">Voor werk stromen die in de Windows Power shell-taal zijn geschreven, voegt u een toe **. ExternalHelp** van de opmerkings richtlijn naar de werk stroom code.</span><span class="sxs-lookup"><span data-stu-id="440a2-146">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="440a2-147">De waarde van de instructie moet een URI zijn die begint met http of https.</span><span class="sxs-lookup"><span data-stu-id="440a2-147">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="440a2-148">De eigenschap HelpUri wordt niet ondersteund voor op XAML gebaseerde werk stromen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="440a2-148">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="440a2-149">De volgende code toont de. ExternalHelp-instructie in een werk stroom bestand.</span><span class="sxs-lookup"><span data-stu-id="440a2-149">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
