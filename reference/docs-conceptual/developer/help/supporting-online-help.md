---
ms.date: 09/13/2016
ms.topic: reference
title: Ondersteunende online help
description: Ondersteunende online help
ms.openlocfilehash: 0164b5e6c6c8d66a6ab2467a8adfb7efffe0fe17
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645420"
---
# <a name="supporting-online-help"></a><span data-ttu-id="7753d-103">Ondersteunende online help</span><span class="sxs-lookup"><span data-stu-id="7753d-103">Supporting Online Help</span></span>

<span data-ttu-id="7753d-104">Vanaf Power Shell 3,0 zijn er twee manieren om de `Get-Help` online functie voor Power shell-opdrachten te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="7753d-104">Beginning in PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for PowerShell commands.</span></span> <span data-ttu-id="7753d-105">In dit onderwerp wordt uitgelegd hoe u deze functie implementeert voor verschillende opdracht typen.</span><span class="sxs-lookup"><span data-stu-id="7753d-105">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="7753d-106">Online-Help</span><span class="sxs-lookup"><span data-stu-id="7753d-106">About Online Help</span></span>

<span data-ttu-id="7753d-107">Online-Help is altijd een essentieel onderdeel van Power shell.</span><span class="sxs-lookup"><span data-stu-id="7753d-107">Online help has always been a vital part of PowerShell.</span></span> <span data-ttu-id="7753d-108">Hoewel `Get-Help` met de cmdlet Help-onderwerpen worden weer gegeven bij de opdracht prompt, hebben veel gebruikers de voor keur aan het online lezen, met inbegrip van kleur codering, hyper links en het delen van ideeën in Community-inhoud en documenten op basis van wiki.</span><span class="sxs-lookup"><span data-stu-id="7753d-108">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="7753d-109">In de online Help werd de meest recente versie van de Help-bestanden het belangrijkst, vóór de komst van de Help-informatie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="7753d-109">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="7753d-110">Met de komst van bij te werken Help in Power Shell 3,0 speelt online Help nog steeds een belang rijke rol af.</span><span class="sxs-lookup"><span data-stu-id="7753d-110">With the advent of Updatable Help in PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="7753d-111">Naast de flexibele gebruikers ervaring biedt de online Help hulp bij gebruikers die geen Bewerk bare Help kunnen gebruiken om Help-onderwerpen te downloaden.</span><span class="sxs-lookup"><span data-stu-id="7753d-111">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="7753d-112">Hoe Get-Help online werkt</span><span class="sxs-lookup"><span data-stu-id="7753d-112">How Get-Help -Online Works</span></span>

<span data-ttu-id="7753d-113">Om gebruikers te helpen de online-Help-onderwerpen voor-opdrachten te vinden, `Get-Help` heeft de opdracht een online-para meter waarmee de online versie van het Help-onderwerp voor een opdracht in de standaard browser van de gebruiker wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="7753d-113">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default internet browser.</span></span>

<span data-ttu-id="7753d-114">Met de volgende opdracht wordt bijvoorbeeld het online-Help-onderwerp voor de `Invoke-Command` cmdlet geopend.</span><span class="sxs-lookup"><span data-stu-id="7753d-114">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="7753d-115">Om te implementeren `Get-Help -Online` , `Get-Help` zoekt de cmdlet naar een Uniform Resource Identifier (URI) voor het Help-onderwerp online versie op de volgende locaties.</span><span class="sxs-lookup"><span data-stu-id="7753d-115">To implement `Get-Help -Online`, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="7753d-116">De eerste koppeling in het gedeelte **Verwante koppelingen** van het Help-onderwerp voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7753d-116">The first link in the **Related Links** section of the help topic for the command.</span></span> <span data-ttu-id="7753d-117">Het Help-onderwerp moet worden geïnstalleerd op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7753d-117">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="7753d-118">Deze functie is geïntroduceerd in Power Shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="7753d-118">This feature was introduced in PowerShell 2.0.</span></span>

- <span data-ttu-id="7753d-119">De eigenschap **HelpUri** van een wille keurige opdracht.</span><span class="sxs-lookup"><span data-stu-id="7753d-119">The **HelpUri** property of any command.</span></span> <span data-ttu-id="7753d-120">De eigenschap **HelpUri** is toegankelijk, zelfs wanneer het Help-onderwerp voor de opdracht niet is geïnstalleerd op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7753d-120">The **HelpUri** property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="7753d-121">Deze functie is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7753d-121">This feature was introduced in PowerShell 3.0.</span></span>

  <span data-ttu-id="7753d-122">`Get-Help` zoekt naar een URI in de eerste vermelding in de sectie **Verwante koppelingen** voordat u de waarde van de eigenschap **HelpUri** ophaalt.</span><span class="sxs-lookup"><span data-stu-id="7753d-122">`Get-Help` looks for a URI in the first entry in the **Related Links** section before getting the **HelpUri** property value.</span></span> <span data-ttu-id="7753d-123">Als de waarde van de eigenschap onjuist is of is gewijzigd, kunt u deze overschrijven door een andere waarde in te voeren in de eerste gerelateerde koppeling.</span><span class="sxs-lookup"><span data-stu-id="7753d-123">If the property value is incorrect or has changed, you can override it by entering a different value in the first related link.</span></span> <span data-ttu-id="7753d-124">De eerste gerelateerde koppeling werkt echter alleen als de Help-onderwerpen zijn geïnstalleerd op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7753d-124">However, the first related link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="7753d-125">Een URI toevoegen aan de eerste gerelateerde koppeling van een Help-onderwerp van een opdracht</span><span class="sxs-lookup"><span data-stu-id="7753d-125">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="7753d-126">U kunt `Get-Help -Online` elke opdracht ondersteunen door een geldige URI toe te voegen aan de eerste vermelding in de sectie **Verwante koppelingen** van het Help-onderwerp op basis van XML voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7753d-126">You can support `Get-Help -Online` for any command by adding a valid URI to the first entry in the **Related Links** section of the XML-based help topic for the command.</span></span> <span data-ttu-id="7753d-127">Deze optie is alleen geldig in Help-onderwerpen op basis van XML en werkt alleen wanneer het Help-onderwerp op de computer van de gebruiker is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7753d-127">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="7753d-128">Wanneer het Help-onderwerp is geïnstalleerd en de URI is gevuld, heeft deze waarde voor rang op de eigenschap **HelpUri** van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7753d-128">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="7753d-129">Ter ondersteuning van deze functie moet de URI worden weer gegeven in het- `maml:uri` element onder het eerste `maml:relatedLinks/maml:navigationLink` element in het- `maml:relatedLinks` element.</span><span class="sxs-lookup"><span data-stu-id="7753d-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="7753d-130">In het volgende XML-bestand wordt de juiste plaatsing van de URI weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7753d-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="7753d-131">De `Online version:` tekst in het `maml:linkText` element is een Best Practice, maar dit is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="7753d-131">The `Online version:` text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

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

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="7753d-132">De eigenschap HelpUri toevoegen aan een opdracht</span><span class="sxs-lookup"><span data-stu-id="7753d-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="7753d-133">In deze sectie wordt uitgelegd hoe u de eigenschap HelpUri kunt toevoegen aan opdrachten van verschillende typen.</span><span class="sxs-lookup"><span data-stu-id="7753d-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="7753d-134">Een HelpUri-eigenschap toevoegen aan een cmdlet</span><span class="sxs-lookup"><span data-stu-id="7753d-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="7753d-135">Voor cmdlets die zijn geschreven in C#, voegt u een **HelpUri** -kenmerk toe aan de klasse **cmdlet** .</span><span class="sxs-lookup"><span data-stu-id="7753d-135">For cmdlets written in C#, add a **HelpUri** attribute to the **Cmdlet** class.</span></span> <span data-ttu-id="7753d-136">De waarde van het kenmerk moet een URI zijn die begint met `http` of `https` .</span><span class="sxs-lookup"><span data-stu-id="7753d-136">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="7753d-137">Met de volgende code wordt het kenmerk **HelpUri** van de `Get-History` klasse cmdlet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7753d-137">The following code shows the **HelpUri** attribute of the `Get-History` cmdlet class.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="7753d-138">Een eigenschap HelpUri toevoegen aan een geavanceerde functie</span><span class="sxs-lookup"><span data-stu-id="7753d-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="7753d-139">Voor geavanceerde functies voegt u een eigenschap **HelpUri** toe aan het kenmerk **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="7753d-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="7753d-140">De waarde van de eigenschap moet een URI zijn die begint met http of https.</span><span class="sxs-lookup"><span data-stu-id="7753d-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="7753d-141">De volgende code toont het kenmerk **HelpUri** van de `New-Calendar` functie</span><span class="sxs-lookup"><span data-stu-id="7753d-141">The following code shows the **HelpUri** attribute of the `New-Calendar` function</span></span>

```powershell
function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="7753d-142">Een HelpUri-kenmerk toevoegen aan een CIM-opdracht</span><span class="sxs-lookup"><span data-stu-id="7753d-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="7753d-143">Voor CIM-opdrachten voegt u een **HelpUri** -kenmerk toe aan het **CmdletMetadata** -element in het CDXML-bestand.</span><span class="sxs-lookup"><span data-stu-id="7753d-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span>
<span data-ttu-id="7753d-144">De waarde van het kenmerk moet een URI zijn die begint met `http` of `https` .</span><span class="sxs-lookup"><span data-stu-id="7753d-144">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="7753d-145">De volgende code toont het kenmerk HelpUri van de `Start-Debug` CIM-opdracht</span><span class="sxs-lookup"><span data-stu-id="7753d-145">The following code shows the HelpUri attribute of the `Start-Debug` CIM command</span></span>

```xml
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="7753d-146">Een HelpUri-kenmerk toevoegen aan een werk stroom</span><span class="sxs-lookup"><span data-stu-id="7753d-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="7753d-147">Voor werk stromen die in de Power shell-taal zijn geschreven, voegt u een toe **. ExternalHelp** van de opmerkings richtlijn naar de werk stroom code.</span><span class="sxs-lookup"><span data-stu-id="7753d-147">For workflows that are written in the PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="7753d-148">De waarde van de instructie moet een URI zijn die begint met `http` of `https` .</span><span class="sxs-lookup"><span data-stu-id="7753d-148">The value of the directive must be a URI that begins with `http` or `https`.</span></span>

> [!NOTE]
> <span data-ttu-id="7753d-149">De eigenschap HelpUri wordt niet ondersteund voor op XAML gebaseerde werk stromen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="7753d-149">The HelpUri property is not supported for XAML-based workflows in PowerShell.</span></span>

<span data-ttu-id="7753d-150">De volgende code toont de. ExternalHelp-instructie in een werk stroom bestand.</span><span class="sxs-lookup"><span data-stu-id="7753d-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
