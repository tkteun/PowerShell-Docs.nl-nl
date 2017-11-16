---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: pswaauthorizationrule toevoegen
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 18422f71b2a5f9af07af94e4324d3c7774f1d5ea
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="acea8-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="acea8-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="acea8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="acea8-104">SYNOPSIS</span></span>

<span data-ttu-id="acea8-105">Voegt een nieuwe autorisatieregel toe aan de Windows PowerShell® Web Access autorisatieregelset.</span><span class="sxs-lookup"><span data-stu-id="acea8-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="acea8-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="acea8-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="acea8-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="acea8-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="acea8-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="acea8-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="acea8-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="acea8-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="acea8-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="acea8-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="acea8-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="acea8-111">DESCRIPTION</span></span>

<span data-ttu-id="acea8-112">De **Add-PswaAuthorizationRule** cmdlet voegt een nieuwe autorisatieregel toe aan de regelset van de Windows PowerShell® Web Access-autorisatie.</span><span class="sxs-lookup"><span data-stu-id="acea8-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="acea8-113">U moet de gebruikers, computers en Windows PowerShell-eindpunten voor deze regel opgeven.</span><span class="sxs-lookup"><span data-stu-id="acea8-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="acea8-114">U kunt gebruikers en computers door afzonderlijke gebruikersaccounts en -computernamen of door op te geven groepen opgeven.</span><span class="sxs-lookup"><span data-stu-id="acea8-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="acea8-115">Voor een computer die is gekoppeld aan een Active Directory-domein, gebruikt de cmdlet de beveiligings-id (SID) van de computer om de regel te maken.</span><span class="sxs-lookup"><span data-stu-id="acea8-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="acea8-116">Hiermee kunt u een korte naam, een volledig gekwalificeerde domeinnaam (FQDN) of een IP-adres voor de **computernaam** op de aanmeldingspagina.</span><span class="sxs-lookup"><span data-stu-id="acea8-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="acea8-117">De cmdlet maakt voor een computer die niet is gekoppeld aan een Active Directory-domein, de regel met behulp van de computernaam die is verstrekt door de beheerder.</span><span class="sxs-lookup"><span data-stu-id="acea8-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="acea8-118">Als u wilt verbinding maken met deze computer, moet de eindgebruiker de computernaam opgeven, precies zoals in de regel weergegeven.</span><span class="sxs-lookup"><span data-stu-id="acea8-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="acea8-119">Als er meerdere computers met dezelfde naam in het netwerk, kan korte naam omzetten in meer dan één computer.</span><span class="sxs-lookup"><span data-stu-id="acea8-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="acea8-120">Dit kan leiden tot verwarring bij het maken van een verbinding.</span><span class="sxs-lookup"><span data-stu-id="acea8-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="acea8-121">Bijvoorbeeld, als een regel bestaat voor de werkgroepcomputer met de naam '*Server1*' en een nieuwe computer met de naam *server1.contoso.com* is gekoppeld met het netwerk met behulp van de autorisatieregels voor validatie is geslaagd en Windows PowerShell Web Access probeert een verbinding maken met de computer met de naam '*Server1*'.</span><span class="sxs-lookup"><span data-stu-id="acea8-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="acea8-122">Deze kan niet worden gegarandeerd dat de verbinding is gemaakt met de computer van de opgegeven werkgroep. de poging kan worden gemaakt op de werkgroep of de computer van het domein met de naam '*Server1*'.</span><span class="sxs-lookup"><span data-stu-id="acea8-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="acea8-123">Als u dubbelzinnigheid, wordt het aanbevolen dat u de FQDN-naam voor de doelcomputer wanneer mogelijk te maken van een autorisatieregel.</span><span class="sxs-lookup"><span data-stu-id="acea8-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="acea8-124">De autorisatieregels evalueren van de primaire aanmelden referentie van de Windows PowerShell Web Access-gebruikers, niet de alternatieve referenties (de tweede set referenties die zijn gevonden in de **optionele verbindingsinstellingen** sectie van de aanmeldingspagina).</span><span class="sxs-lookup"><span data-stu-id="acea8-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="acea8-125">Zie voor een voorbeeld van dit voorbeeld 6.</span><span class="sxs-lookup"><span data-stu-id="acea8-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="acea8-126">Parameters</span><span class="sxs-lookup"><span data-stu-id="acea8-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="acea8-127">-ComputerGroupName&lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="acea8-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="acea8-128">Hiermee geeft de naam van een computergroep in Active Directory Domain Services (AD DS) of het lokale groepen waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="acea8-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="acea8-129">Aliassen</span><span class="sxs-lookup"><span data-stu-id="acea8-129">Aliases</span></span>                              | <span data-ttu-id="acea8-130">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-130">none</span></span>                                 |
| <span data-ttu-id="acea8-131">Nodig?</span><span class="sxs-lookup"><span data-stu-id="acea8-131">Required?</span></span>                            | <span data-ttu-id="acea8-132">De waarde True</span><span class="sxs-lookup"><span data-stu-id="acea8-132">true</span></span>                                 |
| <span data-ttu-id="acea8-133">Positie?</span><span class="sxs-lookup"><span data-stu-id="acea8-133">Position?</span></span>                            | <span data-ttu-id="acea8-134">Met de naam</span><span class="sxs-lookup"><span data-stu-id="acea8-134">named</span></span>                                |
| <span data-ttu-id="acea8-135">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="acea8-135">Default Value</span></span>                        | <span data-ttu-id="acea8-136">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-136">none</span></span>                                 |
| <span data-ttu-id="acea8-137">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="acea8-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="acea8-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="acea8-139">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="acea8-140">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="acea8-141">-ComputerName&lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="acea8-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="acea8-142">Hiermee geeft u de naam van de computer waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="acea8-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="acea8-143">Aliassen</span><span class="sxs-lookup"><span data-stu-id="acea8-143">Aliases</span></span>                              | <span data-ttu-id="acea8-144">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-144">none</span></span>                                 |
| <span data-ttu-id="acea8-145">Nodig?</span><span class="sxs-lookup"><span data-stu-id="acea8-145">Required?</span></span>                            | <span data-ttu-id="acea8-146">De waarde True</span><span class="sxs-lookup"><span data-stu-id="acea8-146">true</span></span>                                 |
| <span data-ttu-id="acea8-147">Positie?</span><span class="sxs-lookup"><span data-stu-id="acea8-147">Position?</span></span>                            | <span data-ttu-id="acea8-148">Met de naam</span><span class="sxs-lookup"><span data-stu-id="acea8-148">named</span></span>                                |
| <span data-ttu-id="acea8-149">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="acea8-149">Default Value</span></span>                        | <span data-ttu-id="acea8-150">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-150">none</span></span>                                 |
| <span data-ttu-id="acea8-151">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="acea8-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="acea8-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="acea8-153">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="acea8-154">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="acea8-155">-ConfigurationName&lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="acea8-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="acea8-156">Geeft de naam van de configuratie van Windows PowerShell-sessie, ook wel bekend als runspace waarvoor deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="acea8-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="acea8-157">Aliassen</span><span class="sxs-lookup"><span data-stu-id="acea8-157">Aliases</span></span>                              | <span data-ttu-id="acea8-158">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-158">none</span></span>                                 |
| <span data-ttu-id="acea8-159">Nodig?</span><span class="sxs-lookup"><span data-stu-id="acea8-159">Required?</span></span>                            | <span data-ttu-id="acea8-160">De waarde True</span><span class="sxs-lookup"><span data-stu-id="acea8-160">true</span></span>                                 |
| <span data-ttu-id="acea8-161">Positie?</span><span class="sxs-lookup"><span data-stu-id="acea8-161">Position?</span></span>                            | <span data-ttu-id="acea8-162">Met de naam</span><span class="sxs-lookup"><span data-stu-id="acea8-162">named</span></span>                                |
| <span data-ttu-id="acea8-163">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="acea8-163">Default Value</span></span>                        | <span data-ttu-id="acea8-164">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-164">none</span></span>                                 |
| <span data-ttu-id="acea8-165">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="acea8-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="acea8-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="acea8-167">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="acea8-168">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="acea8-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="acea8-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="acea8-170">Hiermee geeft u een **PSCredential** -object voor een gebruikersaccount dat u wilt gebruiken om Windows PowerShell-webtoegang autorisatieregels te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="acea8-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="acea8-171">Als u deze parameter niet toevoegt, gebruikt de cmdlet het account momenteel aangemelde gebruiker.</span><span class="sxs-lookup"><span data-stu-id="acea8-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="acea8-172">Ophalen van een **PSCredential** -object, dat vereist is voor het op afstand autorisatieregels toevoegen, voert u de [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="acea8-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="acea8-173">Aliassen</span><span class="sxs-lookup"><span data-stu-id="acea8-173">Aliases</span></span>                              | <span data-ttu-id="acea8-174">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-174">none</span></span>                                 |
| <span data-ttu-id="acea8-175">Nodig?</span><span class="sxs-lookup"><span data-stu-id="acea8-175">Required?</span></span>                            | <span data-ttu-id="acea8-176">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-176">false</span></span>                                |
| <span data-ttu-id="acea8-177">Positie?</span><span class="sxs-lookup"><span data-stu-id="acea8-177">Position?</span></span>                            | <span data-ttu-id="acea8-178">Met de naam</span><span class="sxs-lookup"><span data-stu-id="acea8-178">named</span></span>                                |
| <span data-ttu-id="acea8-179">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="acea8-179">Default Value</span></span>                        | <span data-ttu-id="acea8-180">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-180">none</span></span>                                 |
| <span data-ttu-id="acea8-181">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="acea8-182">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-182">false</span></span>                                |
| <span data-ttu-id="acea8-183">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="acea8-184">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="acea8-185">-Force</span><span class="sxs-lookup"><span data-stu-id="acea8-185">-Force</span></span>

<span data-ttu-id="acea8-186">Hiermee wordt de opdracht uitgevoerd zonder gebruikersbevestiging. \\</span><span class="sxs-lookup"><span data-stu-id="acea8-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="acea8-187">Bovendien ook wordt gevraagd om bevestiging wanneer u een eenvoudige of korte computernaam (zoals een naam die niet een domeinnaam of is geen volledig pad) opgeven.</span><span class="sxs-lookup"><span data-stu-id="acea8-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="acea8-188">Bevestiging is aangevraagd uit veiligheidsoverwegingen, zodat u kunt de eenvoudige naam toevoegen van een computer alleen als de computer zich in een werkgroep.</span><span class="sxs-lookup"><span data-stu-id="acea8-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="acea8-189">Aliassen</span><span class="sxs-lookup"><span data-stu-id="acea8-189">Aliases</span></span>                              | <span data-ttu-id="acea8-190">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-190">none</span></span>                                 |
| <span data-ttu-id="acea8-191">Nodig?</span><span class="sxs-lookup"><span data-stu-id="acea8-191">Required?</span></span>                            | <span data-ttu-id="acea8-192">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-192">false</span></span>                                |
| <span data-ttu-id="acea8-193">Positie?</span><span class="sxs-lookup"><span data-stu-id="acea8-193">Position?</span></span>                            | <span data-ttu-id="acea8-194">Met de naam</span><span class="sxs-lookup"><span data-stu-id="acea8-194">named</span></span>                                |
| <span data-ttu-id="acea8-195">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="acea8-195">Default Value</span></span>                        | <span data-ttu-id="acea8-196">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-196">none</span></span>                                 |
| <span data-ttu-id="acea8-197">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="acea8-198">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-198">false</span></span>                                |
| <span data-ttu-id="acea8-199">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="acea8-200">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="acea8-201">-RuleName&lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="acea8-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="acea8-202">Hiermee geeft u de beschrijvende naam voor deze regel.</span><span class="sxs-lookup"><span data-stu-id="acea8-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="acea8-203">Aliassen</span><span class="sxs-lookup"><span data-stu-id="acea8-203">Aliases</span></span>                              | <span data-ttu-id="acea8-204">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-204">none</span></span>                                 |
| <span data-ttu-id="acea8-205">Nodig?</span><span class="sxs-lookup"><span data-stu-id="acea8-205">Required?</span></span>                            | <span data-ttu-id="acea8-206">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-206">false</span></span>                                |
| <span data-ttu-id="acea8-207">Positie?</span><span class="sxs-lookup"><span data-stu-id="acea8-207">Position?</span></span>                            | <span data-ttu-id="acea8-208">Met de naam</span><span class="sxs-lookup"><span data-stu-id="acea8-208">named</span></span>                                |
| <span data-ttu-id="acea8-209">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="acea8-209">Default Value</span></span>                        | <span data-ttu-id="acea8-210">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-210">none</span></span>                                 |
| <span data-ttu-id="acea8-211">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="acea8-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="acea8-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="acea8-213">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="acea8-214">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="acea8-215">-UserGroupName&lt;tekenreeks\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="acea8-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="acea8-216">Hiermee geeft u de naam van een of meer gebruikersgroepen in AD DS of lokale groepen waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="acea8-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="acea8-217">Aliassen</span><span class="sxs-lookup"><span data-stu-id="acea8-217">Aliases</span></span>                              | <span data-ttu-id="acea8-218">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-218">none</span></span>                                 |
| <span data-ttu-id="acea8-219">Nodig?</span><span class="sxs-lookup"><span data-stu-id="acea8-219">Required?</span></span>                            | <span data-ttu-id="acea8-220">De waarde True</span><span class="sxs-lookup"><span data-stu-id="acea8-220">true</span></span>                                 |
| <span data-ttu-id="acea8-221">Positie?</span><span class="sxs-lookup"><span data-stu-id="acea8-221">Position?</span></span>                            | <span data-ttu-id="acea8-222">Met de naam</span><span class="sxs-lookup"><span data-stu-id="acea8-222">named</span></span>                                |
| <span data-ttu-id="acea8-223">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="acea8-223">Default Value</span></span>                        | <span data-ttu-id="acea8-224">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-224">none</span></span>                                 |
| <span data-ttu-id="acea8-225">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="acea8-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="acea8-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="acea8-227">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="acea8-228">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="acea8-229">-UserName&lt;tekenreeks\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="acea8-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="acea8-230">Hiermee geeft u een of meer gebruikers waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="acea8-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="acea8-231">De gebruikersnaam mag een lokale gebruikersaccount op de gatewaycomputer of een gebruiker in AD DS.</span><span class="sxs-lookup"><span data-stu-id="acea8-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="acea8-232">De indeling is `domain\user` of `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="acea8-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="acea8-233">Aliassen</span><span class="sxs-lookup"><span data-stu-id="acea8-233">Aliases</span></span>                              | <span data-ttu-id="acea8-234">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-234">none</span></span>                                 |
| <span data-ttu-id="acea8-235">Nodig?</span><span class="sxs-lookup"><span data-stu-id="acea8-235">Required?</span></span>                            | <span data-ttu-id="acea8-236">De waarde True</span><span class="sxs-lookup"><span data-stu-id="acea8-236">true</span></span>                                 |
| <span data-ttu-id="acea8-237">Positie?</span><span class="sxs-lookup"><span data-stu-id="acea8-237">Position?</span></span>                            | <span data-ttu-id="acea8-238">1</span><span class="sxs-lookup"><span data-stu-id="acea8-238">1</span></span>                                    |
| <span data-ttu-id="acea8-239">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="acea8-239">Default Value</span></span>                        | <span data-ttu-id="acea8-240">geen</span><span class="sxs-lookup"><span data-stu-id="acea8-240">none</span></span>                                 |
| <span data-ttu-id="acea8-241">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="acea8-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="acea8-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="acea8-243">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="acea8-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="acea8-244">onjuist</span><span class="sxs-lookup"><span data-stu-id="acea8-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="acea8-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="acea8-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="acea8-246">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="acea8-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="acea8-247">Zie voor meer informatie [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="acea8-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="acea8-248">INVOER</span><span class="sxs-lookup"><span data-stu-id="acea8-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="acea8-249">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="acea8-249">String</span></span>

<span data-ttu-id="acea8-250">Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.</span><span class="sxs-lookup"><span data-stu-id="acea8-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="acea8-251">Tekenreeks\[\]</span><span class="sxs-lookup"><span data-stu-id="acea8-251">String\[\]</span></span>

<span data-ttu-id="acea8-252">Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.</span><span class="sxs-lookup"><span data-stu-id="acea8-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="acea8-253">Resultaten</span><span class="sxs-lookup"><span data-stu-id="acea8-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="acea8-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="acea8-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="acea8-255">Deze cmdlet retourneert de autorisatie-regelobject.</span><span class="sxs-lookup"><span data-stu-id="acea8-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="acea8-256">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="acea8-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="acea8-257">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="acea8-257">EXAMPLE 1</span></span>

<span data-ttu-id="acea8-258">In dit voorbeeld verleent toegang tot de sessieconfiguratie *Pswaeindpunt*, wordt er een beperkte runspace op *srv2* voor gebruikers in de *SMAdmins* groep. \\</span><span class="sxs-lookup"><span data-stu-id="acea8-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="acea8-259">**Opmerking**: naam van de computer moet een volledig gekwalificeerde domeinnaam (FQDN).</span><span class="sxs-lookup"><span data-stu-id="acea8-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="acea8-260">Beheerders definiëren een beperkte sessieconfiguratie of een runspace, dit is een beperkt aantal cmdlets en taken die eindgebruikers kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="acea8-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="acea8-261">Het definiëren van een beperkte runspace kan voorkomen dat gebruikers toegang krijgen tot andere computers die niet in de toegestane Windows PowerShell® runspace, dus een beter beveiligde verbinding bieden.</span><span class="sxs-lookup"><span data-stu-id="acea8-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="acea8-262">Zie voor meer informatie over sessieconfiguraties [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) of de [installeren en gebruik Windows PowerShell-webtoegang](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="acea8-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="acea8-263">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="acea8-263">EXAMPLE 2</span></span>

<span data-ttu-id="acea8-264">In dit voorbeeld verleent toegang tot de Windows PowerShell-sessie standaardconfiguratie `Microsoft.PowerShell`op *srv2* voor gebruikers in de gebruikers met de naam contoso\\gebruiker1, contoso\\Gebruiker2 bevat, en contoso\\user3.</span><span class="sxs-lookup"><span data-stu-id="acea8-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="acea8-265">Deze cmdlet maakt drie regels (1 per persoon).</span><span class="sxs-lookup"><span data-stu-id="acea8-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="acea8-266">VOORBEELD 3</span><span class="sxs-lookup"><span data-stu-id="acea8-266">EXAMPLE 3</span></span>

<span data-ttu-id="acea8-267">In dit voorbeeld laat zien hoe voor het invoeren van waarden van de naam van gebruiker via de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="acea8-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="acea8-268">VOORBEELD 4</span><span class="sxs-lookup"><span data-stu-id="acea8-268">EXAMPLE 4</span></span>

<span data-ttu-id="acea8-269">In dit voorbeeld ziet u hoe u alle parameters waaruit waarden pijplijn naam van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="acea8-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject | 
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | 
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | 
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="acea8-270">VOORBEELD 5</span><span class="sxs-lookup"><span data-stu-id="acea8-270">EXAMPLE 5</span></span>

<span data-ttu-id="acea8-271">In dit voorbeeld wordt een regel met de naam van de lokale gebruiker toe om *PswaServer\\ChrisLocal* toegang tot de server met de naam *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="acea8-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="acea8-272">In dit voorbeeld ziet u een scenario waarbij de gateway in een werkgroep en de doelcomputer zich in een domein.</span><span class="sxs-lookup"><span data-stu-id="acea8-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="acea8-273">De autorisatieregel is van toepassing op de lokale gebruikers op de gateway.</span><span class="sxs-lookup"><span data-stu-id="acea8-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="acea8-274">Klik op de pagina Windows PowerShell-webtoegang aanmelden om te verifiëren, moet de gebruiker leveren een tweede set referenties in de **optionele verbindingsinstellingen** gebied.</span><span class="sxs-lookup"><span data-stu-id="acea8-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="acea8-275">De gatewayserver de aanvullende set referenties gebruikt voor het verifiëren van de gebruiker op de doelcomputer, een server met de naam *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="acea8-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="acea8-276">VOORBEELD 6</span><span class="sxs-lookup"><span data-stu-id="acea8-276">EXAMPLE 6</span></span>

<span data-ttu-id="acea8-277">In dit voorbeeld kan alle gebruikers toegang tot alle eindpunten op alle computers.</span><span class="sxs-lookup"><span data-stu-id="acea8-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="acea8-278">Hierdoor wordt het in feite uitgeschakeld autorisatieregels. \\</span><span class="sxs-lookup"><span data-stu-id="acea8-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="acea8-279">**Opmerking**: het gebruik van de `*` jokerteken wordt niet aanbevolen voor implementaties van de beveiliging van gevoelige en moet alleen worden beschouwd voor testomgevingen of gebruikt in implementaties waarbij de beveiliging kan worden versoepeld.</span><span class="sxs-lookup"><span data-stu-id="acea8-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="acea8-280">Zie ook</span><span class="sxs-lookup"><span data-stu-id="acea8-280">See Also</span></span>

- <span data-ttu-id="acea8-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="acea8-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="acea8-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="acea8-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="acea8-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="acea8-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="acea8-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="acea8-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="acea8-285">Voeg lid</span><span class="sxs-lookup"><span data-stu-id="acea8-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="acea8-286">Nieuw Object</span><span class="sxs-lookup"><span data-stu-id="acea8-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="acea8-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="acea8-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
