---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: pswaauthorizationrule ophalen
ms.technology: powershell
ms.openlocfilehash: 74c044c329d8b6a305b86c9056a7041fb5fd046b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="55e99-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="55e99-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="55e99-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="55e99-104">SYNOPSIS</span></span>

<span data-ttu-id="55e99-105">Retourneert een set met autorisatieregels van de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="55e99-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="55e99-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="55e99-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="55e99-107">ID</span><span class="sxs-lookup"><span data-stu-id="55e99-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="55e99-108">Naam</span><span class="sxs-lookup"><span data-stu-id="55e99-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="55e99-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="55e99-109">DESCRIPTION</span></span>

<span data-ttu-id="55e99-110">De **Get-PswaAuthorizationRule** cmdlet retourneert een set met autorisatieregels van de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="55e99-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="55e99-111">Als noch de **Id** parameter noch de **RuleName** parameter wordt opgegeven, wordt deze cmdlet geeft een lijst van alle regels.</span><span class="sxs-lookup"><span data-stu-id="55e99-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="55e99-112">De **Id** parameter kan worden gebruikt om de resultaten te filteren.</span><span class="sxs-lookup"><span data-stu-id="55e99-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="55e99-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="55e99-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="55e99-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="55e99-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="55e99-115">Hiermee geeft u de id's van de regels die deze cmdlet moet ontvangen.</span><span class="sxs-lookup"><span data-stu-id="55e99-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="55e99-116">Als er geen id's zijn opgegeven, retourneert deze cmdlet alle autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="55e99-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="55e99-117">Aliassen</span><span class="sxs-lookup"><span data-stu-id="55e99-117">Aliases</span></span>                              | <span data-ttu-id="55e99-118">geen</span><span class="sxs-lookup"><span data-stu-id="55e99-118">none</span></span>                                 |
| <span data-ttu-id="55e99-119">Nodig?</span><span class="sxs-lookup"><span data-stu-id="55e99-119">Required?</span></span>                            | <span data-ttu-id="55e99-120">onjuist</span><span class="sxs-lookup"><span data-stu-id="55e99-120">false</span></span>                                |
| <span data-ttu-id="55e99-121">Positie?</span><span class="sxs-lookup"><span data-stu-id="55e99-121">Position?</span></span>                            | <span data-ttu-id="55e99-122">2</span><span class="sxs-lookup"><span data-stu-id="55e99-122">2</span></span>                                    |
| <span data-ttu-id="55e99-123">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="55e99-123">Default Value</span></span>                        | <span data-ttu-id="55e99-124">geen</span><span class="sxs-lookup"><span data-stu-id="55e99-124">none</span></span>                                 |
| <span data-ttu-id="55e99-125">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="55e99-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="55e99-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="55e99-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="55e99-127">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="55e99-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="55e99-128">onjuist</span><span class="sxs-lookup"><span data-stu-id="55e99-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="55e99-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="55e99-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="55e99-130">Hiermee worden de namen van autorisatieregels om op te halen.</span><span class="sxs-lookup"><span data-stu-id="55e99-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="55e99-131">Deze parameter retourneert alle regels waarmee exact overeenkomen met de namen van de regel van de tekenreeksen in deze matrix.</span><span class="sxs-lookup"><span data-stu-id="55e99-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="55e99-132">Aliassen</span><span class="sxs-lookup"><span data-stu-id="55e99-132">Aliases</span></span>                              | <span data-ttu-id="55e99-133">geen</span><span class="sxs-lookup"><span data-stu-id="55e99-133">none</span></span>                                 |
| <span data-ttu-id="55e99-134">Nodig?</span><span class="sxs-lookup"><span data-stu-id="55e99-134">Required?</span></span>                            | <span data-ttu-id="55e99-135">De waarde True</span><span class="sxs-lookup"><span data-stu-id="55e99-135">true</span></span>                                 |
| <span data-ttu-id="55e99-136">Positie?</span><span class="sxs-lookup"><span data-stu-id="55e99-136">Position?</span></span>                            | <span data-ttu-id="55e99-137">2</span><span class="sxs-lookup"><span data-stu-id="55e99-137">2</span></span>                                    |
| <span data-ttu-id="55e99-138">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="55e99-138">Default Value</span></span>                        | <span data-ttu-id="55e99-139">geen</span><span class="sxs-lookup"><span data-stu-id="55e99-139">none</span></span>                                 |
| <span data-ttu-id="55e99-140">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="55e99-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="55e99-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="55e99-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="55e99-142">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="55e99-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="55e99-143">onjuist</span><span class="sxs-lookup"><span data-stu-id="55e99-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="55e99-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="55e99-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="55e99-145">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="55e99-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="55e99-146">Zie voor meer informatie [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="55e99-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="55e99-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="55e99-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="55e99-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="55e99-148">int\[\]</span></span>

<span data-ttu-id="55e99-149">Deze cmdlet accepteert een matrix van gehele getallen of een matrix van tekenreekswaarden als invoer.</span><span class="sxs-lookup"><span data-stu-id="55e99-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="55e99-150">Tekenreeks\[\]</span><span class="sxs-lookup"><span data-stu-id="55e99-150">String\[\]</span></span>

<span data-ttu-id="55e99-151">Deze cmdlet accepteert een matrix van gehele getallen of een matrix van tekenreekswaarden als invoer.</span><span class="sxs-lookup"><span data-stu-id="55e99-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="55e99-152">OUTPUTS</span><span class="sxs-lookup"><span data-stu-id="55e99-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="55e99-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="55e99-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="55e99-154">Deze cmdlet produceert een PswaAuthorizationRule-object als uitvoer.</span><span class="sxs-lookup"><span data-stu-id="55e99-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="55e99-155">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="55e99-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="55e99-156">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="55e99-156">EXAMPLE 1</span></span>

<span data-ttu-id="55e99-157">In dit voorbeeld haalt alle regels.</span><span class="sxs-lookup"><span data-stu-id="55e99-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="55e99-158">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="55e99-158">EXAMPLE 2</span></span>

<span data-ttu-id="55e99-159">In dit voorbeeld wordt een regel met een ID van *2*.</span><span class="sxs-lookup"><span data-stu-id="55e99-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="55e99-160">Voorbeeld 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="55e99-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="55e99-161">In dit voorbeeld ziet u hoe de cmdlet accepteert een waarde van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="55e99-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="55e99-162">Een regel-id en de naam van een regel worden doorgegeven in deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="55e99-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="55e99-163">Verwante onderwerpen</span><span class="sxs-lookup"><span data-stu-id="55e99-163">Related topics</span></span>

- [<span data-ttu-id="55e99-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="55e99-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="55e99-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="55e99-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="55e99-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="55e99-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="55e99-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="55e99-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)