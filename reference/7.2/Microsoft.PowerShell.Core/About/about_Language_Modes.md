---
description: Hierin worden de taal modi en hun effect op Power shell-sessies uitgelegd.
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 9e4b1ec2dd16d3442c553460ff217e7e0223f41f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705370"
---
# <a name="about-language-modes"></a><span data-ttu-id="b0207-103">Over taal modi</span><span class="sxs-lookup"><span data-stu-id="b0207-103">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="b0207-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b0207-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b0207-105">Hierin worden de taal modi en hun effect op Power shell-sessies uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="b0207-105">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="b0207-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b0207-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="b0207-107">De taal modus van een Power shell-sessie bepaalt, in deel, welke elementen van de Power shell-taal in de sessie kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b0207-107">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="b0207-108">Power shell ondersteunt de volgende taal modi:</span><span class="sxs-lookup"><span data-stu-id="b0207-108">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="b0207-109">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="b0207-109">FullLanguage</span></span>
- <span data-ttu-id="b0207-110">ConstrainedLanguage (geïntroduceerd in Power Shell 3,0)</span><span class="sxs-lookup"><span data-stu-id="b0207-110">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="b0207-111">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="b0207-111">RestrictedLanguage</span></span>
- <span data-ttu-id="b0207-112">Geen taal</span><span class="sxs-lookup"><span data-stu-id="b0207-112">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="b0207-113">WAT IS EEN TAAL MODUS?</span><span class="sxs-lookup"><span data-stu-id="b0207-113">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="b0207-114">De taal modus bepaalt de taal elementen die in de sessie zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0207-114">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="b0207-115">De taal modus is in feite een eigenschap van de sessie configuratie (of eind punt) die wordt gebruikt om de sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="b0207-115">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="b0207-116">Alle sessies die gebruikmaken van een bepaalde sessie configuratie hebben de taal modus van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="b0207-116">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="b0207-117">Alle Power shell-sessies hebben een taal modus, met inbegrip van PSSessions die u maakt met behulp van de `New-PSSession` cmdlet, tijdelijke sessies die gebruikmaken van de para meter ComputerName en de standaard sessies die worden weer gegeven wanneer u Power shell start.</span><span class="sxs-lookup"><span data-stu-id="b0207-117">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="b0207-118">Externe sessies worden gemaakt met behulp van de sessie configuraties op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="b0207-118">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="b0207-119">De taal modus die in de sessie configuratie is ingesteld, bepaalt de taal modus van de sessie.</span><span class="sxs-lookup"><span data-stu-id="b0207-119">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="b0207-120">Als u de sessie configuratie van een PSSession wilt opgeven, gebruikt u de para meter configuratiepad van cmdlets waarmee een sessie wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b0207-120">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="b0207-121">TAAL MODI</span><span class="sxs-lookup"><span data-stu-id="b0207-121">LANGUAGE MODES</span></span>

<span data-ttu-id="b0207-122">In deze sectie worden de taal modi in Power shell-sessies beschreven.</span><span class="sxs-lookup"><span data-stu-id="b0207-122">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="b0207-123">VOLLEDIGE taal (FullLanguage)</span><span class="sxs-lookup"><span data-stu-id="b0207-123">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="b0207-124">In de FullLanguage-modus zijn alle taal elementen in de sessie toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0207-124">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="b0207-125">FullLanguage is de standaard taal modus voor standaard sessies in alle versies van Windows, met uitzonde ring van Windows RT.</span><span class="sxs-lookup"><span data-stu-id="b0207-125">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="b0207-126">BEPERKTE taal (RestrictedLanguage)</span><span class="sxs-lookup"><span data-stu-id="b0207-126">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="b0207-127">In de RestrictedLanguage-modus kunnen gebruikers opdrachten uitvoeren (cmdlets, functies, CIM-opdrachten en werk stromen), maar ze mogen geen script blokken gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b0207-127">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="b0207-128">Standaard worden alleen de volgende variabelen toegestaan in de RestrictedLanguage-modus:</span><span class="sxs-lookup"><span data-stu-id="b0207-128">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="b0207-129">Module manifesten, die gebruikmaken van de modus RestrictedLanguage, staan ook de volgende aanvullende variabelen toe:</span><span class="sxs-lookup"><span data-stu-id="b0207-129">Module manifests, which use RestrictedLanguage mode, permit the following additional variables as well:</span></span>

- `$PSScriptRoot`
- <span data-ttu-id="b0207-130">`$PSEdition` (in Power shell core)</span><span class="sxs-lookup"><span data-stu-id="b0207-130">`$PSEdition` (in PowerShell Core)</span></span>
- <span data-ttu-id="b0207-131">`$EnabledExperimentalFeatures` (in Power shell core)</span><span class="sxs-lookup"><span data-stu-id="b0207-131">`$EnabledExperimentalFeatures` (in PowerShell Core)</span></span>

<span data-ttu-id="b0207-132">Alleen de volgende vergelijkings operatoren zijn toegestaan:</span><span class="sxs-lookup"><span data-stu-id="b0207-132">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="b0207-133">`-eq` waard</span><span class="sxs-lookup"><span data-stu-id="b0207-133">`-eq` (equal)</span></span>
- <span data-ttu-id="b0207-134">`-gt` (groter dan)</span><span class="sxs-lookup"><span data-stu-id="b0207-134">`-gt` (greater-than)</span></span>
- <span data-ttu-id="b0207-135">`-lt` (kleiner dan)</span><span class="sxs-lookup"><span data-stu-id="b0207-135">`-lt` (less-than)</span></span>

<span data-ttu-id="b0207-136">Toewijzings instructies, verwijzingen naar eigenschappen en methode aanroepen zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0207-136">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="b0207-137">Geen taal (geen taal)</span><span class="sxs-lookup"><span data-stu-id="b0207-137">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="b0207-138">De modus voor alleen talen kan worden gebruikt via de API.</span><span class="sxs-lookup"><span data-stu-id="b0207-138">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="b0207-139">De modus voor niet-talen betekent dat er geen script tekst van een formulier is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0207-139">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="b0207-140">Dit belet het gebruik van de methode **AddScript ()** waarmee fragmenten van het Power shell-script worden geparseerd en uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b0207-140">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="b0207-141">U kunt alleen **AddCommand ()** en **AddParameter ()** gebruiken die niet door de parser heen gaan.</span><span class="sxs-lookup"><span data-stu-id="b0207-141">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="b0207-142">BEPERKTE taal (beperkte taal)</span><span class="sxs-lookup"><span data-stu-id="b0207-142">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="b0207-143">De ConstrainedLanguage-modus staat alle cmdlets en alle Power shell-taal elementen toe, maar beperkt de toegestane typen.</span><span class="sxs-lookup"><span data-stu-id="b0207-143">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="b0207-144">De ConstrainedLanguage-modus is ontworpen ter ondersteuning van UMCI (user mode code Integrity) in Windows RT.</span><span class="sxs-lookup"><span data-stu-id="b0207-144">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="b0207-145">Dit is de enige ondersteunde taal modus in Windows RT, maar deze is beschikbaar op alle ondersteunde systemen.</span><span class="sxs-lookup"><span data-stu-id="b0207-145">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="b0207-146">UMCI beschermt ARM-apparaten door alleen door micro soft ondertekende en micro soft gecertificeerde apps te installeren op Windows RT-apparaten.</span><span class="sxs-lookup"><span data-stu-id="b0207-146">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="b0207-147">In de ConstrainedLanguage-modus wordt voor komen dat gebruikers Power shell gebruiken om UMCI te omzeilen of te schenden.</span><span class="sxs-lookup"><span data-stu-id="b0207-147">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="b0207-148">De functies van de ConstrainedLanguage-modus zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="b0207-148">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="b0207-149">Alle cmdlets in Windows-modules en andere UMCI-goedgekeurde cmdlets zijn volledig functioneel en hebben volledige toegang tot systeem bronnen, behalve zoals vermeld.</span><span class="sxs-lookup"><span data-stu-id="b0207-149">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="b0207-150">Alle elementen van de Power shell-script taal zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0207-150">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="b0207-151">Alle modules die in Windows zijn opgenomen, kunnen worden geïmporteerd en alle opdrachten die de modules exporteren worden uitgevoerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="b0207-151">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="b0207-152">In Power shell workflow kunt u script werk stromen schrijven en uitvoeren (workflows die zijn geschreven in de Power shell-taal).</span><span class="sxs-lookup"><span data-stu-id="b0207-152">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="b0207-153">Op XAML gebaseerde werk stromen worden niet ondersteund en u kunt XAML niet uitvoeren in een script werk stroom, bijvoorbeeld door te gebruiken `Invoke-Expression -Language XAML` .</span><span class="sxs-lookup"><span data-stu-id="b0207-153">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="b0207-154">Werk stromen kunnen ook geen andere werk stromen aanroepen, hoewel geneste werk stromen zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0207-154">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="b0207-155">Met de `Add-Type` cmdlet kunnen ondertekende assembly's worden geladen, maar kan er geen wille keurige C#-code of Win32 api's worden geladen.</span><span class="sxs-lookup"><span data-stu-id="b0207-155">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="b0207-156">De `New-Object` cmdlet kan alleen worden gebruikt voor toegestane typen (zie hieronder).</span><span class="sxs-lookup"><span data-stu-id="b0207-156">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="b0207-157">Alleen toegestane typen (zie hieronder) kunnen worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="b0207-157">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="b0207-158">Andere typen zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="b0207-158">Other types are not permitted.</span></span>

- <span data-ttu-id="b0207-159">Type conversie is toegestaan, maar alleen als het resultaat een toegestaan type is.</span><span class="sxs-lookup"><span data-stu-id="b0207-159">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="b0207-160">Cmdlet-para meters die de invoer van teken reeksen converteren naar typen werken alleen wanneer het resulterende type een toegestaan type is.</span><span class="sxs-lookup"><span data-stu-id="b0207-160">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="b0207-161">De methode **toString ()** en de .net-methoden van toegestane typen (zie hieronder) kunnen worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b0207-161">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="b0207-162">Andere methoden kunnen niet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b0207-162">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="b0207-163">Gebruikers kunnen alle eigenschappen van toegestane typen ophalen.</span><span class="sxs-lookup"><span data-stu-id="b0207-163">Users can get all properties of allowed types.</span></span> <span data-ttu-id="b0207-164">Gebruikers kunnen de waarden van eigenschappen alleen instellen voor kern typen.</span><span class="sxs-lookup"><span data-stu-id="b0207-164">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="b0207-165">Alleen de volgende COM-objecten zijn toegestaan:</span><span class="sxs-lookup"><span data-stu-id="b0207-165">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="b0207-166">**Scripting. Dictionary**</span><span class="sxs-lookup"><span data-stu-id="b0207-166">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="b0207-167">**Scripting. File System object**</span><span class="sxs-lookup"><span data-stu-id="b0207-167">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="b0207-168">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="b0207-168">**VBScript.RegExp**</span></span>

<span data-ttu-id="b0207-169">De volgende typen zijn toegestaan in de ConstrainedLanguage-modus.</span><span class="sxs-lookup"><span data-stu-id="b0207-169">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="b0207-170">Gebruikers kunnen eigenschappen ophalen, methoden aanroepen en objecten converteren naar deze typen.</span><span class="sxs-lookup"><span data-stu-id="b0207-170">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="b0207-171">Toegestane typen:</span><span class="sxs-lookup"><span data-stu-id="b0207-171">Allowed Types:</span></span>

- <span data-ttu-id="b0207-172">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-172">AliasAttribute</span></span>
- <span data-ttu-id="b0207-173">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-173">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="b0207-174">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-174">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="b0207-175">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-175">AllowNullAttribute</span></span>
- <span data-ttu-id="b0207-176">Matrix</span><span class="sxs-lookup"><span data-stu-id="b0207-176">Array</span></span>
- <span data-ttu-id="b0207-177">Booleaanse waarde</span><span class="sxs-lookup"><span data-stu-id="b0207-177">Bool</span></span>
- <span data-ttu-id="b0207-178">DBCS</span><span class="sxs-lookup"><span data-stu-id="b0207-178">byte</span></span>
- <span data-ttu-id="b0207-179">char</span><span class="sxs-lookup"><span data-stu-id="b0207-179">char</span></span>
- <span data-ttu-id="b0207-180">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-180">CmdletBindingAttribute</span></span>
- <span data-ttu-id="b0207-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="b0207-181">DateTime</span></span>
- <span data-ttu-id="b0207-182">decimal</span><span class="sxs-lookup"><span data-stu-id="b0207-182">decimal</span></span>
- <span data-ttu-id="b0207-183">Directory entry</span><span class="sxs-lookup"><span data-stu-id="b0207-183">DirectoryEntry</span></span>
- <span data-ttu-id="b0207-184">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="b0207-184">DirectorySearcher</span></span>
- <span data-ttu-id="b0207-185">double</span><span class="sxs-lookup"><span data-stu-id="b0207-185">double</span></span>
- <span data-ttu-id="b0207-186">float</span><span class="sxs-lookup"><span data-stu-id="b0207-186">float</span></span>
- <span data-ttu-id="b0207-187">Guid</span><span class="sxs-lookup"><span data-stu-id="b0207-187">Guid</span></span>
- <span data-ttu-id="b0207-188">Hashtabel</span><span class="sxs-lookup"><span data-stu-id="b0207-188">Hashtable</span></span>
- <span data-ttu-id="b0207-189">int</span><span class="sxs-lookup"><span data-stu-id="b0207-189">int</span></span>
- <span data-ttu-id="b0207-190">Int16</span><span class="sxs-lookup"><span data-stu-id="b0207-190">Int16</span></span>
- <span data-ttu-id="b0207-191">long</span><span class="sxs-lookup"><span data-stu-id="b0207-191">long</span></span>
- <span data-ttu-id="b0207-192">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="b0207-192">ManagementClass</span></span>
- <span data-ttu-id="b0207-193">ManagementObject</span><span class="sxs-lookup"><span data-stu-id="b0207-193">ManagementObject</span></span>
- <span data-ttu-id="b0207-194">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="b0207-194">ManagementObjectSearcher</span></span>
- <span data-ttu-id="b0207-195">NullString</span><span class="sxs-lookup"><span data-stu-id="b0207-195">NullString</span></span>
- <span data-ttu-id="b0207-196">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-196">OutputTypeAttribute</span></span>
- <span data-ttu-id="b0207-197">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-197">ParameterAttribute</span></span>
- <span data-ttu-id="b0207-198">PSCredential</span><span class="sxs-lookup"><span data-stu-id="b0207-198">PSCredential</span></span>
- <span data-ttu-id="b0207-199">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-199">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="b0207-200">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="b0207-200">PSListModifier</span></span>
- <span data-ttu-id="b0207-201">PSObject</span><span class="sxs-lookup"><span data-stu-id="b0207-201">PSObject</span></span>
- <span data-ttu-id="b0207-202">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="b0207-202">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="b0207-203">PSReference</span><span class="sxs-lookup"><span data-stu-id="b0207-203">PSReference</span></span>
- <span data-ttu-id="b0207-204">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-204">PSTypeNameAttribute</span></span>
- <span data-ttu-id="b0207-205">Reguliere</span><span class="sxs-lookup"><span data-stu-id="b0207-205">Regex</span></span>
- <span data-ttu-id="b0207-206">SByte</span><span class="sxs-lookup"><span data-stu-id="b0207-206">SByte</span></span>
- <span data-ttu-id="b0207-207">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b0207-207">string</span></span>
- <span data-ttu-id="b0207-208">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="b0207-208">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="b0207-209">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b0207-209">SwitchParameter</span></span>
- <span data-ttu-id="b0207-210">System. Globalization. Culture info</span><span class="sxs-lookup"><span data-stu-id="b0207-210">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="b0207-211">Systeem .net. IPAddress</span><span class="sxs-lookup"><span data-stu-id="b0207-211">System.Net.IPAddress</span></span>
- <span data-ttu-id="b0207-212">Het e-mail adres van System .net. E-mail</span><span class="sxs-lookup"><span data-stu-id="b0207-212">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="b0207-213">Systeem. numerics. BigInteger</span><span class="sxs-lookup"><span data-stu-id="b0207-213">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="b0207-214">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="b0207-214">System.Security.SecureString</span></span>
- <span data-ttu-id="b0207-215">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="b0207-215">TimeSpan</span></span>
- <span data-ttu-id="b0207-216">UInt16</span><span class="sxs-lookup"><span data-stu-id="b0207-216">UInt16</span></span>
- <span data-ttu-id="b0207-217">UInt32</span><span class="sxs-lookup"><span data-stu-id="b0207-217">UInt32</span></span>
- <span data-ttu-id="b0207-218">UInt64</span><span class="sxs-lookup"><span data-stu-id="b0207-218">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="b0207-219">DE TAAL MODUS VAN EEN SESSIE CONFIGURATIE ZOEKEN</span><span class="sxs-lookup"><span data-stu-id="b0207-219">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="b0207-220">Wanneer een sessie configuratie is gemaakt met behulp van een sessie configuratie bestand, heeft de sessie configuratie een eigenschap LanguageMode.</span><span class="sxs-lookup"><span data-stu-id="b0207-220">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="b0207-221">U kunt de taal modus vinden door de waarde van de eigenschap LanguageMode op te halen.</span><span class="sxs-lookup"><span data-stu-id="b0207-221">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="b0207-222">Bij andere sessie configuraties kunt u de taal modus indirect vinden door de taal modus te zoeken van een sessie die is gemaakt met behulp van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="b0207-222">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="b0207-223">DE TAAL MODUS VAN EEN SESSIE ZOEKEN</span><span class="sxs-lookup"><span data-stu-id="b0207-223">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="b0207-224">U kunt de taal modus van een FullLanguage-of ConstrainedLanguage-sessie vinden door de waarde van de eigenschap LanguageMode van de sessie status op te halen.</span><span class="sxs-lookup"><span data-stu-id="b0207-224">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="b0207-225">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b0207-225">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="b0207-226">In sessies met RestrictedLanguage en de modus voor alleen talen kunt u de punt methode echter niet gebruiken voor het ophalen van eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="b0207-226">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="b0207-227">In plaats daarvan wordt de taal modus in het fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0207-227">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="b0207-228">Wanneer u de `$ExecutionContext.SessionState.LanguageMode` opdracht uitvoert in een RestrictedLanguage-sessie, retourneert Power shell de PropertyReferenceNotSupportedInDataSection-en VariableReferenceNotSupportedInDataSection-fout berichten.</span><span class="sxs-lookup"><span data-stu-id="b0207-228">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="b0207-229">PropertyReferenceNotSupportedInDataSection: verwijzingen naar eigenschappen zijn niet toegestaan in de modus voor een beperkte taal of een gegevens sectie.</span><span class="sxs-lookup"><span data-stu-id="b0207-229">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="b0207-230">VariableReferenceNotSupportedInDataSection een variabele waarnaar niet kan worden verwezen in de modus voor een beperkte taal of waarnaar wordt verwezen in een gegevens sectie.</span><span class="sxs-lookup"><span data-stu-id="b0207-230">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="b0207-231">Wanneer u de `$ExecutionContext.SessionState.LanguageMode` opdracht in een niet-taal sessie uitvoert, retourneert Power shell het ScriptsNotAllowed-fout bericht.</span><span class="sxs-lookup"><span data-stu-id="b0207-231">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="b0207-232">ScriptsNotAllowed: de syntaxis wordt niet ondersteund door deze runs Pace.</span><span class="sxs-lookup"><span data-stu-id="b0207-232">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="b0207-233">Dit kan zijn omdat deze zich in een niet-taal modus bevindt.</span><span class="sxs-lookup"><span data-stu-id="b0207-233">This might be because it is in no-language mode.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0207-234">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="b0207-234">SEE ALSO</span></span>

- [<span data-ttu-id="b0207-235">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="b0207-235">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="b0207-236">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="b0207-236">about_Session_Configurations</span></span>](about_Session_Configurations.md)
