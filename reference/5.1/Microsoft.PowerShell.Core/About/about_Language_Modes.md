---
description: Hierin worden de taal modi en hun effect op Power shell-sessies uitgelegd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: a75afd5149f3d290a8ec377417d4920b0ad6b526
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252602"
---
# <a name="about-language-modes"></a><span data-ttu-id="e97a3-104">Over taal modi</span><span class="sxs-lookup"><span data-stu-id="e97a3-104">About Language Modes</span></span>

## <a name="short-description"></a><span data-ttu-id="e97a3-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e97a3-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e97a3-106">Hierin worden de taal modi en hun effect op Power shell-sessies uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="e97a3-106">Explains language modes and their effect on PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="e97a3-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e97a3-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e97a3-108">De taal modus van een Power shell-sessie bepaalt, in deel, welke elementen van de Power shell-taal in de sessie kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e97a3-108">The language mode of a PowerShell session determines, in part, which elements of the PowerShell language can be used in the session.</span></span>

<span data-ttu-id="e97a3-109">Power shell ondersteunt de volgende taal modi:</span><span class="sxs-lookup"><span data-stu-id="e97a3-109">PowerShell supports the following language modes:</span></span>

- <span data-ttu-id="e97a3-110">FullLanguage</span><span class="sxs-lookup"><span data-stu-id="e97a3-110">FullLanguage</span></span>
- <span data-ttu-id="e97a3-111">ConstrainedLanguage (geïntroduceerd in Power Shell 3,0)</span><span class="sxs-lookup"><span data-stu-id="e97a3-111">ConstrainedLanguage (introduced in PowerShell 3.0)</span></span>
- <span data-ttu-id="e97a3-112">RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="e97a3-112">RestrictedLanguage</span></span>
- <span data-ttu-id="e97a3-113">Geen taal</span><span class="sxs-lookup"><span data-stu-id="e97a3-113">NoLanguage</span></span>

### <a name="what-is-a-language-mode"></a><span data-ttu-id="e97a3-114">WAT IS EEN TAAL MODUS?</span><span class="sxs-lookup"><span data-stu-id="e97a3-114">WHAT IS A LANGUAGE MODE?</span></span>

<span data-ttu-id="e97a3-115">De taal modus bepaalt de taal elementen die in de sessie zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e97a3-115">The language mode determines the language elements that are permitted in the session.</span></span>

<span data-ttu-id="e97a3-116">De taal modus is in feite een eigenschap van de sessie configuratie (of eind punt) die wordt gebruikt om de sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="e97a3-116">The language mode is actually a property of the session configuration (or "endpoint") that is used to create the session.</span></span> <span data-ttu-id="e97a3-117">Alle sessies die gebruikmaken van een bepaalde sessie configuratie hebben de taal modus van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="e97a3-117">All sessions that use a particular session configuration have the language mode of the session configuration.</span></span>

<span data-ttu-id="e97a3-118">Alle Power shell-sessies hebben een taal modus, met inbegrip van PSSessions die u maakt met behulp van de `New-PSSession` cmdlet, tijdelijke sessies die gebruikmaken van de para meter ComputerName en de standaard sessies die worden weer gegeven wanneer u Power shell start.</span><span class="sxs-lookup"><span data-stu-id="e97a3-118">All PowerShell sessions have a language mode, including PSSessions that you create by using the `New-PSSession` cmdlet, temporary sessions that use the ComputerName parameter, and the default sessions that appear when you start PowerShell.</span></span>

<span data-ttu-id="e97a3-119">Externe sessies worden gemaakt met behulp van de sessie configuraties op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="e97a3-119">Remote sessions are created by using the session configurations on the remote computer.</span></span> <span data-ttu-id="e97a3-120">De taal modus die in de sessie configuratie is ingesteld, bepaalt de taal modus van de sessie.</span><span class="sxs-lookup"><span data-stu-id="e97a3-120">The language mode set in the session configuration determines the language mode of the session.</span></span> <span data-ttu-id="e97a3-121">Als u de sessie configuratie van een PSSession wilt opgeven, gebruikt u de para meter configuratiepad van cmdlets waarmee een sessie wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e97a3-121">To specify the session configuration of a PSSession, use the ConfigurationName parameter of cmdlets that create a session.</span></span>

### <a name="language-modes"></a><span data-ttu-id="e97a3-122">TAAL MODI</span><span class="sxs-lookup"><span data-stu-id="e97a3-122">LANGUAGE MODES</span></span>

<span data-ttu-id="e97a3-123">In deze sectie worden de taal modi in Power shell-sessies beschreven.</span><span class="sxs-lookup"><span data-stu-id="e97a3-123">This section describes the language modes in PowerShell sessions.</span></span>

#### <a name="full-language-fulllanguage"></a><span data-ttu-id="e97a3-124">VOLLEDIGE taal (FullLanguage)</span><span class="sxs-lookup"><span data-stu-id="e97a3-124">FULL LANGUAGE (FullLanguage)</span></span>

<span data-ttu-id="e97a3-125">In de FullLanguage-modus zijn alle taal elementen in de sessie toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e97a3-125">The FullLanguage mode permits all language elements in the session.</span></span>
<span data-ttu-id="e97a3-126">FullLanguage is de standaard taal modus voor standaard sessies in alle versies van Windows, met uitzonde ring van Windows RT.</span><span class="sxs-lookup"><span data-stu-id="e97a3-126">FullLanguage is the default language mode for default sessions on all versions of Windows except for Windows RT.</span></span>

#### <a name="restricted-language-restrictedlanguage"></a><span data-ttu-id="e97a3-127">BEPERKTE taal (RestrictedLanguage)</span><span class="sxs-lookup"><span data-stu-id="e97a3-127">RESTRICTED LANGUAGE (RestrictedLanguage)</span></span>

<span data-ttu-id="e97a3-128">In de RestrictedLanguage-modus kunnen gebruikers opdrachten uitvoeren (cmdlets, functies, CIM-opdrachten en werk stromen), maar ze mogen geen script blokken gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e97a3-128">In RestrictedLanguage mode, users may run commands (cmdlets, functions, CIM commands, and workflows) but are not permitted to use script blocks.</span></span>

<span data-ttu-id="e97a3-129">Standaard worden alleen de volgende variabelen toegestaan in de RestrictedLanguage-modus:</span><span class="sxs-lookup"><span data-stu-id="e97a3-129">By default, only the following variables are permitted in RestrictedLanguage mode:</span></span>

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

<span data-ttu-id="e97a3-130">Alleen de volgende vergelijkings operatoren zijn toegestaan:</span><span class="sxs-lookup"><span data-stu-id="e97a3-130">Only the following comparison operators are permitted:</span></span>

- <span data-ttu-id="e97a3-131">`-eq` waard</span><span class="sxs-lookup"><span data-stu-id="e97a3-131">`-eq` (equal)</span></span>
- <span data-ttu-id="e97a3-132">`-gt` (groter dan)</span><span class="sxs-lookup"><span data-stu-id="e97a3-132">`-gt` (greater-than)</span></span>
- <span data-ttu-id="e97a3-133">`-lt` (kleiner dan)</span><span class="sxs-lookup"><span data-stu-id="e97a3-133">`-lt` (less-than)</span></span>

<span data-ttu-id="e97a3-134">Toewijzings instructies, verwijzingen naar eigenschappen en methode aanroepen zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e97a3-134">Assignment statements, property references, and method calls are not permitted.</span></span>

#### <a name="no-language-nolanguage"></a><span data-ttu-id="e97a3-135">Geen taal (geen taal)</span><span class="sxs-lookup"><span data-stu-id="e97a3-135">NO LANGUAGE (NoLanguage)</span></span>

<span data-ttu-id="e97a3-136">De modus voor alleen talen kan worden gebruikt via de API.</span><span class="sxs-lookup"><span data-stu-id="e97a3-136">NoLanguage mode can only be used through the API.</span></span> <span data-ttu-id="e97a3-137">De modus voor niet-talen betekent dat er geen script tekst van een formulier is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e97a3-137">NoLanguage mode means no script text of any form is permitted.</span></span> <span data-ttu-id="e97a3-138">Dit belet het gebruik van de methode **AddScript ()** waarmee fragmenten van het Power shell-script worden geparseerd en uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e97a3-138">This precludes the use of the **AddScript()** method which sends fragments of PowerShell script to be parsed and executed.</span></span> <span data-ttu-id="e97a3-139">U kunt alleen **AddCommand ()** en **AddParameter ()** gebruiken die niet door de parser heen gaan.</span><span class="sxs-lookup"><span data-stu-id="e97a3-139">You can only use **AddCommand()** and **AddParameter()** which don't go through the parser.</span></span>

#### <a name="constrained-language-constrained-language"></a><span data-ttu-id="e97a3-140">BEPERKTE taal (beperkte taal)</span><span class="sxs-lookup"><span data-stu-id="e97a3-140">CONSTRAINED LANGUAGE (Constrained Language)</span></span>

<span data-ttu-id="e97a3-141">De ConstrainedLanguage-modus staat alle cmdlets en alle Power shell-taal elementen toe, maar beperkt de toegestane typen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-141">The ConstrainedLanguage mode permits all cmdlets and all PowerShell language elements, but it limits permitted types.</span></span>

<span data-ttu-id="e97a3-142">De ConstrainedLanguage-modus is ontworpen ter ondersteuning van UMCI (user mode code Integrity) in Windows RT.</span><span class="sxs-lookup"><span data-stu-id="e97a3-142">ConstrainedLanguage mode is designed to support User Mode Code Integrity (UMCI) on Windows RT.</span></span> <span data-ttu-id="e97a3-143">Dit is de enige ondersteunde taal modus in Windows RT, maar deze is beschikbaar op alle ondersteunde systemen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-143">It is the only supported language mode on Windows RT, but it is available on all supported systems.</span></span>

<span data-ttu-id="e97a3-144">UMCI beschermt ARM-apparaten door alleen door micro soft ondertekende en micro soft gecertificeerde apps te installeren op Windows RT-apparaten.</span><span class="sxs-lookup"><span data-stu-id="e97a3-144">UMCI protects ARM devices by allowing only Microsoft-signed and Microsoft-certified apps to be installed on Windows RT-based devices.</span></span>
<span data-ttu-id="e97a3-145">In de ConstrainedLanguage-modus wordt voor komen dat gebruikers Power shell gebruiken om UMCI te omzeilen of te schenden.</span><span class="sxs-lookup"><span data-stu-id="e97a3-145">ConstrainedLanguage mode prevents users from using PowerShell to circumvent or violate UMCI.</span></span>

<span data-ttu-id="e97a3-146">De functies van de ConstrainedLanguage-modus zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="e97a3-146">The features of ConstrainedLanguage mode are as follows:</span></span>

- <span data-ttu-id="e97a3-147">Alle cmdlets in Windows-modules en andere UMCI-goedgekeurde cmdlets zijn volledig functioneel en hebben volledige toegang tot systeem bronnen, behalve zoals vermeld.</span><span class="sxs-lookup"><span data-stu-id="e97a3-147">All cmdlets in Windows modules, and other UMCI-approved cmdlets, are fully functional and have complete access to system resources, except as noted.</span></span>

- <span data-ttu-id="e97a3-148">Alle elementen van de Power shell-script taal zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e97a3-148">All elements of the PowerShell scripting language are permitted.</span></span>

- <span data-ttu-id="e97a3-149">Alle modules die in Windows zijn opgenomen, kunnen worden geïmporteerd en alle opdrachten die de modules exporteren worden uitgevoerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="e97a3-149">All modules included in Windows can be imported and all commands that the modules export run in the session.</span></span>

- <span data-ttu-id="e97a3-150">In Power shell workflow kunt u script werk stromen schrijven en uitvoeren (workflows die zijn geschreven in de Power shell-taal).</span><span class="sxs-lookup"><span data-stu-id="e97a3-150">In PowerShell Workflow, you can write and run script workflows (workflows written in the PowerShell language).</span></span> <span data-ttu-id="e97a3-151">Op XAML gebaseerde werk stromen worden niet ondersteund en u kunt XAML niet uitvoeren in een script werk stroom, bijvoorbeeld door te gebruiken `Invoke-Expression -Language XAML` .</span><span class="sxs-lookup"><span data-stu-id="e97a3-151">XAML-based workflows are not supported and you cannot run XAML in a script workflow, such as by using `Invoke-Expression -Language XAML`.</span></span> <span data-ttu-id="e97a3-152">Werk stromen kunnen ook geen andere werk stromen aanroepen, hoewel geneste werk stromen zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e97a3-152">Also, workflows cannot call other workflows, although nested workflows are permitted.</span></span>

- <span data-ttu-id="e97a3-153">Met de `Add-Type` cmdlet kunnen ondertekende assembly's worden geladen, maar kan er geen wille keurige C#-code of Win32 api's worden geladen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-153">The `Add-Type` cmdlet can load signed assemblies, but it cannot load arbitrary C# code or Win32 APIs.</span></span>

- <span data-ttu-id="e97a3-154">De `New-Object` cmdlet kan alleen worden gebruikt voor toegestane typen (zie hieronder).</span><span class="sxs-lookup"><span data-stu-id="e97a3-154">The `New-Object` cmdlet can be used only on allowed types (listed below).</span></span>

- <span data-ttu-id="e97a3-155">Alleen toegestane typen (zie hieronder) kunnen worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="e97a3-155">Only allowed types (listed below) can be used in PowerShell.</span></span> <span data-ttu-id="e97a3-156">Andere typen zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="e97a3-156">Other types are not permitted.</span></span>

- <span data-ttu-id="e97a3-157">Type conversie is toegestaan, maar alleen als het resultaat een toegestaan type is.</span><span class="sxs-lookup"><span data-stu-id="e97a3-157">Type conversion is permitted, but only when the result is an allowed type.</span></span>

- <span data-ttu-id="e97a3-158">Cmdlet-para meters die de invoer van teken reeksen converteren naar typen werken alleen wanneer het resulterende type een toegestaan type is.</span><span class="sxs-lookup"><span data-stu-id="e97a3-158">Cmdlet parameters that convert string input to types work only when the resulting type is an allowed type.</span></span>

- <span data-ttu-id="e97a3-159">De methode **toString ()** en de .net-methoden van toegestane typen (zie hieronder) kunnen worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-159">The **ToString()** method and the .NET methods of allowed types (listed below) can be invoked.</span></span> <span data-ttu-id="e97a3-160">Andere methoden kunnen niet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-160">Other methods cannot be invoked.</span></span>

- <span data-ttu-id="e97a3-161">Gebruikers kunnen alle eigenschappen van toegestane typen ophalen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-161">Users can get all properties of allowed types.</span></span> <span data-ttu-id="e97a3-162">Gebruikers kunnen de waarden van eigenschappen alleen instellen voor kern typen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-162">Users can set the values of properties only on Core types.</span></span> <span data-ttu-id="e97a3-163">Alleen de volgende COM-objecten zijn toegestaan:</span><span class="sxs-lookup"><span data-stu-id="e97a3-163">Only the following COM objects are permitted:</span></span>

  - <span data-ttu-id="e97a3-164">**Scripting. Dictionary**</span><span class="sxs-lookup"><span data-stu-id="e97a3-164">**Scripting.Dictionary**</span></span>
  - <span data-ttu-id="e97a3-165">**Scripting. File System object**</span><span class="sxs-lookup"><span data-stu-id="e97a3-165">**Scripting.FileSystemObject**</span></span>
  - <span data-ttu-id="e97a3-166">**VBScript. RegExp**</span><span class="sxs-lookup"><span data-stu-id="e97a3-166">**VBScript.RegExp**</span></span>

<span data-ttu-id="e97a3-167">De volgende typen zijn toegestaan in de ConstrainedLanguage-modus.</span><span class="sxs-lookup"><span data-stu-id="e97a3-167">The following types are permitted in ConstrainedLanguage mode.</span></span> <span data-ttu-id="e97a3-168">Gebruikers kunnen eigenschappen ophalen, methoden aanroepen en objecten converteren naar deze typen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-168">Users can get properties, invoke methods, and convert objects to these types.</span></span>

<span data-ttu-id="e97a3-169">Toegestane typen:</span><span class="sxs-lookup"><span data-stu-id="e97a3-169">Allowed Types:</span></span>

- <span data-ttu-id="e97a3-170">AliasAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-170">AliasAttribute</span></span>
- <span data-ttu-id="e97a3-171">AllowEmptyCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-171">AllowEmptyCollectionAttribute</span></span>
- <span data-ttu-id="e97a3-172">AllowEmptyStringAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-172">AllowEmptyStringAttribute</span></span>
- <span data-ttu-id="e97a3-173">AllowNullAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-173">AllowNullAttribute</span></span>
- <span data-ttu-id="e97a3-174">Matrix</span><span class="sxs-lookup"><span data-stu-id="e97a3-174">Array</span></span>
- <span data-ttu-id="e97a3-175">Booleaanse waarde</span><span class="sxs-lookup"><span data-stu-id="e97a3-175">Bool</span></span>
- <span data-ttu-id="e97a3-176">DBCS</span><span class="sxs-lookup"><span data-stu-id="e97a3-176">byte</span></span>
- <span data-ttu-id="e97a3-177">char</span><span class="sxs-lookup"><span data-stu-id="e97a3-177">char</span></span>
- <span data-ttu-id="e97a3-178">CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-178">CmdletBindingAttribute</span></span>
- <span data-ttu-id="e97a3-179">DateTime</span><span class="sxs-lookup"><span data-stu-id="e97a3-179">DateTime</span></span>
- <span data-ttu-id="e97a3-180">decimal</span><span class="sxs-lookup"><span data-stu-id="e97a3-180">decimal</span></span>
- <span data-ttu-id="e97a3-181">Directory entry</span><span class="sxs-lookup"><span data-stu-id="e97a3-181">DirectoryEntry</span></span>
- <span data-ttu-id="e97a3-182">DirectorySearcher</span><span class="sxs-lookup"><span data-stu-id="e97a3-182">DirectorySearcher</span></span>
- <span data-ttu-id="e97a3-183">double</span><span class="sxs-lookup"><span data-stu-id="e97a3-183">double</span></span>
- <span data-ttu-id="e97a3-184">float</span><span class="sxs-lookup"><span data-stu-id="e97a3-184">float</span></span>
- <span data-ttu-id="e97a3-185">Guid</span><span class="sxs-lookup"><span data-stu-id="e97a3-185">Guid</span></span>
- <span data-ttu-id="e97a3-186">Hashtabel</span><span class="sxs-lookup"><span data-stu-id="e97a3-186">Hashtable</span></span>
- <span data-ttu-id="e97a3-187">int</span><span class="sxs-lookup"><span data-stu-id="e97a3-187">int</span></span>
- <span data-ttu-id="e97a3-188">Int16</span><span class="sxs-lookup"><span data-stu-id="e97a3-188">Int16</span></span>
- <span data-ttu-id="e97a3-189">long</span><span class="sxs-lookup"><span data-stu-id="e97a3-189">long</span></span>
- <span data-ttu-id="e97a3-190">ManagementClass</span><span class="sxs-lookup"><span data-stu-id="e97a3-190">ManagementClass</span></span>
- <span data-ttu-id="e97a3-191">ManagementObject</span><span class="sxs-lookup"><span data-stu-id="e97a3-191">ManagementObject</span></span>
- <span data-ttu-id="e97a3-192">ManagementObjectSearcher</span><span class="sxs-lookup"><span data-stu-id="e97a3-192">ManagementObjectSearcher</span></span>
- <span data-ttu-id="e97a3-193">NullString</span><span class="sxs-lookup"><span data-stu-id="e97a3-193">NullString</span></span>
- <span data-ttu-id="e97a3-194">OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-194">OutputTypeAttribute</span></span>
- <span data-ttu-id="e97a3-195">ParameterAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-195">ParameterAttribute</span></span>
- <span data-ttu-id="e97a3-196">PSCredential</span><span class="sxs-lookup"><span data-stu-id="e97a3-196">PSCredential</span></span>
- <span data-ttu-id="e97a3-197">PSDefaultValueAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-197">PSDefaultValueAttribute</span></span>
- <span data-ttu-id="e97a3-198">PSListModifier</span><span class="sxs-lookup"><span data-stu-id="e97a3-198">PSListModifier</span></span>
- <span data-ttu-id="e97a3-199">PSObject</span><span class="sxs-lookup"><span data-stu-id="e97a3-199">PSObject</span></span>
- <span data-ttu-id="e97a3-200">PSPrimitiveDictionary</span><span class="sxs-lookup"><span data-stu-id="e97a3-200">PSPrimitiveDictionary</span></span>
- <span data-ttu-id="e97a3-201">PSReference</span><span class="sxs-lookup"><span data-stu-id="e97a3-201">PSReference</span></span>
- <span data-ttu-id="e97a3-202">PSTypeNameAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-202">PSTypeNameAttribute</span></span>
- <span data-ttu-id="e97a3-203">Reguliere</span><span class="sxs-lookup"><span data-stu-id="e97a3-203">Regex</span></span>
- <span data-ttu-id="e97a3-204">SByte</span><span class="sxs-lookup"><span data-stu-id="e97a3-204">SByte</span></span>
- <span data-ttu-id="e97a3-205">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e97a3-205">string</span></span>
- <span data-ttu-id="e97a3-206">SupportsWildcardsAttribute</span><span class="sxs-lookup"><span data-stu-id="e97a3-206">SupportsWildcardsAttribute</span></span>
- <span data-ttu-id="e97a3-207">SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e97a3-207">SwitchParameter</span></span>
- <span data-ttu-id="e97a3-208">System. Globalization. Culture info</span><span class="sxs-lookup"><span data-stu-id="e97a3-208">System.Globalization.CultureInfo</span></span>
- <span data-ttu-id="e97a3-209">Systeem .net. IPAddress</span><span class="sxs-lookup"><span data-stu-id="e97a3-209">System.Net.IPAddress</span></span>
- <span data-ttu-id="e97a3-210">Het e-mail adres van System .net. E-mail</span><span class="sxs-lookup"><span data-stu-id="e97a3-210">System.Net.Mail.MailAddress</span></span>
- <span data-ttu-id="e97a3-211">Systeem. numerics. BigInteger</span><span class="sxs-lookup"><span data-stu-id="e97a3-211">System.Numerics.BigInteger</span></span>
- <span data-ttu-id="e97a3-212">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="e97a3-212">System.Security.SecureString</span></span>
- <span data-ttu-id="e97a3-213">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="e97a3-213">TimeSpan</span></span>
- <span data-ttu-id="e97a3-214">UInt16</span><span class="sxs-lookup"><span data-stu-id="e97a3-214">UInt16</span></span>
- <span data-ttu-id="e97a3-215">UInt32</span><span class="sxs-lookup"><span data-stu-id="e97a3-215">UInt32</span></span>
- <span data-ttu-id="e97a3-216">UInt64</span><span class="sxs-lookup"><span data-stu-id="e97a3-216">UInt64</span></span>

### <a name="finding-the-language-mode-of-a-session-configuration"></a><span data-ttu-id="e97a3-217">DE TAAL MODUS VAN EEN SESSIE CONFIGURATIE ZOEKEN</span><span class="sxs-lookup"><span data-stu-id="e97a3-217">FINDING THE LANGUAGE MODE OF A SESSION CONFIGURATION</span></span>

<span data-ttu-id="e97a3-218">Wanneer een sessie configuratie is gemaakt met behulp van een sessie configuratie bestand, heeft de sessie configuratie een eigenschap LanguageMode.</span><span class="sxs-lookup"><span data-stu-id="e97a3-218">When a session configuration is created by using a session configuration file, the session configuration has a LanguageMode property.</span></span> <span data-ttu-id="e97a3-219">U kunt de taal modus vinden door de waarde van de eigenschap LanguageMode op te halen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-219">You can find the language mode by getting the value of the LanguageMode property.</span></span>

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

<span data-ttu-id="e97a3-220">Bij andere sessie configuraties kunt u de taal modus indirect vinden door de taal modus te zoeken van een sessie die is gemaakt met behulp van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="e97a3-220">On other session configurations, you can find the language mode indirectly by finding the language mode of a session that is created by using the session configuration.</span></span>

### <a name="finding-the-language-mode-of-a-session"></a><span data-ttu-id="e97a3-221">DE TAAL MODUS VAN EEN SESSIE ZOEKEN</span><span class="sxs-lookup"><span data-stu-id="e97a3-221">FINDING THE LANGUAGE MODE OF A SESSION</span></span>

<span data-ttu-id="e97a3-222">U kunt de taal modus van een FullLanguage-of ConstrainedLanguage-sessie vinden door de waarde van de eigenschap LanguageMode van de sessie status op te halen.</span><span class="sxs-lookup"><span data-stu-id="e97a3-222">You can find the language mode of a FullLanguage or ConstrainedLanguage session by getting the value of the LanguageMode property of the session state.</span></span>

<span data-ttu-id="e97a3-223">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e97a3-223">For example:</span></span>

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

<span data-ttu-id="e97a3-224">In sessies met RestrictedLanguage en de modus voor alleen talen kunt u de punt methode echter niet gebruiken voor het ophalen van eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="e97a3-224">However, in sessions with RestrictedLanguage and NoLanguage modes, you cannot use the dot method to get property values.</span></span> <span data-ttu-id="e97a3-225">In plaats daarvan wordt de taal modus in het fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e97a3-225">Instead, the error message reveals the language mode.</span></span>

<span data-ttu-id="e97a3-226">Wanneer u de `$ExecutionContext.SessionState.LanguageMode` opdracht uitvoert in een RestrictedLanguage-sessie, retourneert Power shell de PropertyReferenceNotSupportedInDataSection-en VariableReferenceNotSupportedInDataSection-fout berichten.</span><span class="sxs-lookup"><span data-stu-id="e97a3-226">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a RestrictedLanguage session, PowerShell returns the PropertyReferenceNotSupportedInDataSection and VariableReferenceNotSupportedInDataSection error messages.</span></span>

- <span data-ttu-id="e97a3-227">PropertyReferenceNotSupportedInDataSection: verwijzingen naar eigenschappen zijn niet toegestaan in de modus voor een beperkte taal of een gegevens sectie.</span><span class="sxs-lookup"><span data-stu-id="e97a3-227">PropertyReferenceNotSupportedInDataSection: Property references are not allowed in restricted language mode or a Data section.</span></span>
- <span data-ttu-id="e97a3-228">VariableReferenceNotSupportedInDataSection een variabele waarnaar niet kan worden verwezen in de modus voor een beperkte taal of waarnaar wordt verwezen in een gegevens sectie.</span><span class="sxs-lookup"><span data-stu-id="e97a3-228">VariableReferenceNotSupportedInDataSection A variable that cannot be referenced in restricted language mode or a Data section is being referenced.</span></span>

<span data-ttu-id="e97a3-229">Wanneer u de `$ExecutionContext.SessionState.LanguageMode` opdracht in een niet-taal sessie uitvoert, retourneert Power shell het ScriptsNotAllowed-fout bericht.</span><span class="sxs-lookup"><span data-stu-id="e97a3-229">When you run the `$ExecutionContext.SessionState.LanguageMode` command in a NoLanguage session, PowerShell returns the ScriptsNotAllowed error message.</span></span>

- <span data-ttu-id="e97a3-230">ScriptsNotAllowed: de syntaxis wordt niet ondersteund door deze runs Pace.</span><span class="sxs-lookup"><span data-stu-id="e97a3-230">ScriptsNotAllowed: The syntax is not supported by this runspace.</span></span> <span data-ttu-id="e97a3-231">Dit kan zijn omdat deze zich in een niet-taal modus bevindt.</span><span class="sxs-lookup"><span data-stu-id="e97a3-231">This might be because it is in no-language mode.</span></span>

## <a name="keywords"></a><span data-ttu-id="e97a3-232">WOORD</span><span class="sxs-lookup"><span data-stu-id="e97a3-232">KEYWORDS</span></span>

- <span data-ttu-id="e97a3-233">about_ConstrainedLanguage</span><span class="sxs-lookup"><span data-stu-id="e97a3-233">about_ConstrainedLanguage</span></span>
- <span data-ttu-id="e97a3-234">about_FullLanguage</span><span class="sxs-lookup"><span data-stu-id="e97a3-234">about_FullLanguage</span></span>
- <span data-ttu-id="e97a3-235">about_NoLanguage</span><span class="sxs-lookup"><span data-stu-id="e97a3-235">about_NoLanguage</span></span>
- <span data-ttu-id="e97a3-236">about_RestrictedLanguage</span><span class="sxs-lookup"><span data-stu-id="e97a3-236">about_RestrictedLanguage</span></span>

## <a name="see-also"></a><span data-ttu-id="e97a3-237">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="e97a3-237">SEE ALSO</span></span>

- [<span data-ttu-id="e97a3-238">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="e97a3-238">about_Session_Configuration_Files</span></span>](about_Session_Configuration_Files.md)
- [<span data-ttu-id="e97a3-239">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="e97a3-239">about_Session_Configurations</span></span>](about_Session_Configurations.md)
