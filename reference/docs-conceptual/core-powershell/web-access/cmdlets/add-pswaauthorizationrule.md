---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: pswaauthorizationrule toevoegen
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 07ddd4df6a776f3ef6763242f8682747b9b97061
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="a44a1-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a44a1-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="a44a1-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a44a1-104">SYNOPSIS</span></span>

<span data-ttu-id="a44a1-105">Voegt een nieuwe autorisatieregel toe aan de Windows PowerShell® Web Access autorisatieregelset.</span><span class="sxs-lookup"><span data-stu-id="a44a1-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="a44a1-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a44a1-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="a44a1-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="a44a1-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="a44a1-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="a44a1-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="a44a1-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="a44a1-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="a44a1-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="a44a1-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="a44a1-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a44a1-111">DESCRIPTION</span></span>

<span data-ttu-id="a44a1-112">De **Add-PswaAuthorizationRule** cmdlet voegt een nieuwe autorisatieregel toe aan de regelset van de Windows PowerShell® Web Access-autorisatie.</span><span class="sxs-lookup"><span data-stu-id="a44a1-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="a44a1-113">U moet de gebruikers, computers en Windows PowerShell-eindpunten voor deze regel opgeven.</span><span class="sxs-lookup"><span data-stu-id="a44a1-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="a44a1-114">U kunt gebruikers en computers door afzonderlijke gebruikersaccounts en -computernamen of door op te geven groepen opgeven.</span><span class="sxs-lookup"><span data-stu-id="a44a1-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="a44a1-115">Voor een computer die is gekoppeld aan een Active Directory-domein, gebruikt de cmdlet de beveiligings-id (SID) van de computer om de regel te maken.</span><span class="sxs-lookup"><span data-stu-id="a44a1-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="a44a1-116">Hiermee kunt u een korte naam, een volledig gekwalificeerde domeinnaam (FQDN) of een IP-adres voor de **computernaam** op de aanmeldingspagina.</span><span class="sxs-lookup"><span data-stu-id="a44a1-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="a44a1-117">De cmdlet maakt voor een computer die niet is gekoppeld aan een Active Directory-domein, de regel met behulp van de computernaam die is verstrekt door de beheerder.</span><span class="sxs-lookup"><span data-stu-id="a44a1-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="a44a1-118">Als u wilt verbinding maken met deze computer, moet de eindgebruiker de computernaam opgeven, precies zoals in de regel weergegeven.</span><span class="sxs-lookup"><span data-stu-id="a44a1-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="a44a1-119">Als er meerdere computers met dezelfde naam in het netwerk, kan korte naam omzetten in meer dan één computer.</span><span class="sxs-lookup"><span data-stu-id="a44a1-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="a44a1-120">Dit kan leiden tot verwarring bij het maken van een verbinding.</span><span class="sxs-lookup"><span data-stu-id="a44a1-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="a44a1-121">Bijvoorbeeld, als een regel bestaat voor de werkgroepcomputer met de naam '*Server1*' en een nieuwe computer met de naam *server1.contoso.com* is gekoppeld met het netwerk met behulp van de autorisatieregels voor validatie is geslaagd en Windows PowerShell Web Access probeert een verbinding maken met de computer met de naam '*Server1*'.</span><span class="sxs-lookup"><span data-stu-id="a44a1-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="a44a1-122">Deze kan niet worden gegarandeerd dat de verbinding is gemaakt met de computer van de opgegeven werkgroep. de poging kan worden gemaakt op de werkgroep of de computer van het domein met de naam '*Server1*'.</span><span class="sxs-lookup"><span data-stu-id="a44a1-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="a44a1-123">Als u dubbelzinnigheid, wordt het aanbevolen dat u de FQDN-naam voor de doelcomputer wanneer mogelijk te maken van een autorisatieregel.</span><span class="sxs-lookup"><span data-stu-id="a44a1-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="a44a1-124">De autorisatieregels evalueren van de primaire aanmelden referentie van de Windows PowerShell Web Access-gebruikers, niet de alternatieve referenties (de tweede set referenties die zijn gevonden in de **optionele verbindingsinstellingen** sectie van de aanmeldingspagina).</span><span class="sxs-lookup"><span data-stu-id="a44a1-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="a44a1-125">Zie voor een voorbeeld van dit voorbeeld 6.</span><span class="sxs-lookup"><span data-stu-id="a44a1-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="a44a1-126">Parameters</span><span class="sxs-lookup"><span data-stu-id="a44a1-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="a44a1-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="a44a1-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="a44a1-128">Hiermee geeft de naam van een computergroep in Active Directory Domain Services (AD DS) of het lokale groepen waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="a44a1-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="a44a1-129">Aliassen</span><span class="sxs-lookup"><span data-stu-id="a44a1-129">Aliases</span></span>                              | <span data-ttu-id="a44a1-130">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-130">none</span></span>                                 |
| <span data-ttu-id="a44a1-131">Nodig?</span><span class="sxs-lookup"><span data-stu-id="a44a1-131">Required?</span></span>                            | <span data-ttu-id="a44a1-132">De waarde True</span><span class="sxs-lookup"><span data-stu-id="a44a1-132">true</span></span>                                 |
| <span data-ttu-id="a44a1-133">Positie?</span><span class="sxs-lookup"><span data-stu-id="a44a1-133">Position?</span></span>                            | <span data-ttu-id="a44a1-134">Met de naam</span><span class="sxs-lookup"><span data-stu-id="a44a1-134">named</span></span>                                |
| <span data-ttu-id="a44a1-135">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="a44a1-135">Default Value</span></span>                        | <span data-ttu-id="a44a1-136">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-136">none</span></span>                                 |
| <span data-ttu-id="a44a1-137">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a44a1-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="a44a1-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="a44a1-139">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a44a1-140">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="a44a1-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="a44a1-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="a44a1-142">Hiermee geeft u de naam van de computer waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="a44a1-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="a44a1-143">Aliassen</span><span class="sxs-lookup"><span data-stu-id="a44a1-143">Aliases</span></span>                              | <span data-ttu-id="a44a1-144">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-144">none</span></span>                                 |
| <span data-ttu-id="a44a1-145">Nodig?</span><span class="sxs-lookup"><span data-stu-id="a44a1-145">Required?</span></span>                            | <span data-ttu-id="a44a1-146">De waarde True</span><span class="sxs-lookup"><span data-stu-id="a44a1-146">true</span></span>                                 |
| <span data-ttu-id="a44a1-147">Positie?</span><span class="sxs-lookup"><span data-stu-id="a44a1-147">Position?</span></span>                            | <span data-ttu-id="a44a1-148">Met de naam</span><span class="sxs-lookup"><span data-stu-id="a44a1-148">named</span></span>                                |
| <span data-ttu-id="a44a1-149">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="a44a1-149">Default Value</span></span>                        | <span data-ttu-id="a44a1-150">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-150">none</span></span>                                 |
| <span data-ttu-id="a44a1-151">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a44a1-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="a44a1-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="a44a1-153">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a44a1-154">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="a44a1-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="a44a1-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="a44a1-156">Geeft de naam van de configuratie van Windows PowerShell-sessie, ook wel bekend als runspace waarvoor deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="a44a1-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="a44a1-157">Aliassen</span><span class="sxs-lookup"><span data-stu-id="a44a1-157">Aliases</span></span>                              | <span data-ttu-id="a44a1-158">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-158">none</span></span>                                 |
| <span data-ttu-id="a44a1-159">Nodig?</span><span class="sxs-lookup"><span data-stu-id="a44a1-159">Required?</span></span>                            | <span data-ttu-id="a44a1-160">De waarde True</span><span class="sxs-lookup"><span data-stu-id="a44a1-160">true</span></span>                                 |
| <span data-ttu-id="a44a1-161">Positie?</span><span class="sxs-lookup"><span data-stu-id="a44a1-161">Position?</span></span>                            | <span data-ttu-id="a44a1-162">Met de naam</span><span class="sxs-lookup"><span data-stu-id="a44a1-162">named</span></span>                                |
| <span data-ttu-id="a44a1-163">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="a44a1-163">Default Value</span></span>                        | <span data-ttu-id="a44a1-164">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-164">none</span></span>                                 |
| <span data-ttu-id="a44a1-165">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a44a1-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="a44a1-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="a44a1-167">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a44a1-168">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="a44a1-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="a44a1-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="a44a1-170">Hiermee geeft u een **PSCredential** -object voor een gebruikersaccount dat u wilt gebruiken om Windows PowerShell-webtoegang autorisatieregels te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a44a1-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="a44a1-171">Als u deze parameter niet toevoegt, gebruikt de cmdlet het account momenteel aangemelde gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a44a1-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="a44a1-172">Ophalen van een **PSCredential** -object, dat vereist is voor het op afstand autorisatieregels toevoegen, voert u de [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a44a1-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="a44a1-173">Aliassen</span><span class="sxs-lookup"><span data-stu-id="a44a1-173">Aliases</span></span>                              | <span data-ttu-id="a44a1-174">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-174">none</span></span>                                 |
| <span data-ttu-id="a44a1-175">Nodig?</span><span class="sxs-lookup"><span data-stu-id="a44a1-175">Required?</span></span>                            | <span data-ttu-id="a44a1-176">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-176">false</span></span>                                |
| <span data-ttu-id="a44a1-177">Positie?</span><span class="sxs-lookup"><span data-stu-id="a44a1-177">Position?</span></span>                            | <span data-ttu-id="a44a1-178">Met de naam</span><span class="sxs-lookup"><span data-stu-id="a44a1-178">named</span></span>                                |
| <span data-ttu-id="a44a1-179">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="a44a1-179">Default Value</span></span>                        | <span data-ttu-id="a44a1-180">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-180">none</span></span>                                 |
| <span data-ttu-id="a44a1-181">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a44a1-182">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-182">false</span></span>                                |
| <span data-ttu-id="a44a1-183">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a44a1-184">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="a44a1-185">-Force</span><span class="sxs-lookup"><span data-stu-id="a44a1-185">-Force</span></span>

<span data-ttu-id="a44a1-186">Hiermee wordt de opdracht uitgevoerd zonder gebruikersbevestiging. \\</span><span class="sxs-lookup"><span data-stu-id="a44a1-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="a44a1-187">Bovendien ook wordt gevraagd om bevestiging wanneer u een eenvoudige of korte computernaam (zoals een naam die niet een domeinnaam of is geen volledig pad) opgeven.</span><span class="sxs-lookup"><span data-stu-id="a44a1-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="a44a1-188">Bevestiging is aangevraagd uit veiligheidsoverwegingen, zodat u kunt de eenvoudige naam toevoegen van een computer alleen als de computer zich in een werkgroep.</span><span class="sxs-lookup"><span data-stu-id="a44a1-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="a44a1-189">Aliassen</span><span class="sxs-lookup"><span data-stu-id="a44a1-189">Aliases</span></span>                              | <span data-ttu-id="a44a1-190">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-190">none</span></span>                                 |
| <span data-ttu-id="a44a1-191">Nodig?</span><span class="sxs-lookup"><span data-stu-id="a44a1-191">Required?</span></span>                            | <span data-ttu-id="a44a1-192">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-192">false</span></span>                                |
| <span data-ttu-id="a44a1-193">Positie?</span><span class="sxs-lookup"><span data-stu-id="a44a1-193">Position?</span></span>                            | <span data-ttu-id="a44a1-194">Met de naam</span><span class="sxs-lookup"><span data-stu-id="a44a1-194">named</span></span>                                |
| <span data-ttu-id="a44a1-195">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="a44a1-195">Default Value</span></span>                        | <span data-ttu-id="a44a1-196">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-196">none</span></span>                                 |
| <span data-ttu-id="a44a1-197">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a44a1-198">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-198">false</span></span>                                |
| <span data-ttu-id="a44a1-199">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a44a1-200">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="a44a1-201">-RuleName&lt;tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="a44a1-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="a44a1-202">Hiermee geeft u de beschrijvende naam voor deze regel.</span><span class="sxs-lookup"><span data-stu-id="a44a1-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="a44a1-203">Aliassen</span><span class="sxs-lookup"><span data-stu-id="a44a1-203">Aliases</span></span>                              | <span data-ttu-id="a44a1-204">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-204">none</span></span>                                 |
| <span data-ttu-id="a44a1-205">Nodig?</span><span class="sxs-lookup"><span data-stu-id="a44a1-205">Required?</span></span>                            | <span data-ttu-id="a44a1-206">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-206">false</span></span>                                |
| <span data-ttu-id="a44a1-207">Positie?</span><span class="sxs-lookup"><span data-stu-id="a44a1-207">Position?</span></span>                            | <span data-ttu-id="a44a1-208">Met de naam</span><span class="sxs-lookup"><span data-stu-id="a44a1-208">named</span></span>                                |
| <span data-ttu-id="a44a1-209">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="a44a1-209">Default Value</span></span>                        | <span data-ttu-id="a44a1-210">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-210">none</span></span>                                 |
| <span data-ttu-id="a44a1-211">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a44a1-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="a44a1-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="a44a1-213">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a44a1-214">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="a44a1-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="a44a1-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="a44a1-216">Hiermee geeft u de naam van een of meer gebruikersgroepen in AD DS of lokale groepen waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="a44a1-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="a44a1-217">Aliassen</span><span class="sxs-lookup"><span data-stu-id="a44a1-217">Aliases</span></span>                              | <span data-ttu-id="a44a1-218">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-218">none</span></span>                                 |
| <span data-ttu-id="a44a1-219">Nodig?</span><span class="sxs-lookup"><span data-stu-id="a44a1-219">Required?</span></span>                            | <span data-ttu-id="a44a1-220">De waarde True</span><span class="sxs-lookup"><span data-stu-id="a44a1-220">true</span></span>                                 |
| <span data-ttu-id="a44a1-221">Positie?</span><span class="sxs-lookup"><span data-stu-id="a44a1-221">Position?</span></span>                            | <span data-ttu-id="a44a1-222">Met de naam</span><span class="sxs-lookup"><span data-stu-id="a44a1-222">named</span></span>                                |
| <span data-ttu-id="a44a1-223">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="a44a1-223">Default Value</span></span>                        | <span data-ttu-id="a44a1-224">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-224">none</span></span>                                 |
| <span data-ttu-id="a44a1-225">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a44a1-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="a44a1-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="a44a1-227">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a44a1-228">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="a44a1-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="a44a1-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="a44a1-230">Hiermee geeft u een of meer gebruikers waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="a44a1-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="a44a1-231">De gebruikersnaam mag een lokale gebruikersaccount op de gatewaycomputer of een gebruiker in AD DS.</span><span class="sxs-lookup"><span data-stu-id="a44a1-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="a44a1-232">De indeling is `domain\user` of `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="a44a1-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="a44a1-233">Aliassen</span><span class="sxs-lookup"><span data-stu-id="a44a1-233">Aliases</span></span>                              | <span data-ttu-id="a44a1-234">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-234">none</span></span>                                 |
| <span data-ttu-id="a44a1-235">Nodig?</span><span class="sxs-lookup"><span data-stu-id="a44a1-235">Required?</span></span>                            | <span data-ttu-id="a44a1-236">De waarde True</span><span class="sxs-lookup"><span data-stu-id="a44a1-236">true</span></span>                                 |
| <span data-ttu-id="a44a1-237">Positie?</span><span class="sxs-lookup"><span data-stu-id="a44a1-237">Position?</span></span>                            | <span data-ttu-id="a44a1-238">1</span><span class="sxs-lookup"><span data-stu-id="a44a1-238">1</span></span>                                    |
| <span data-ttu-id="a44a1-239">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="a44a1-239">Default Value</span></span>                        | <span data-ttu-id="a44a1-240">geen</span><span class="sxs-lookup"><span data-stu-id="a44a1-240">none</span></span>                                 |
| <span data-ttu-id="a44a1-241">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="a44a1-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="a44a1-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="a44a1-243">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="a44a1-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="a44a1-244">onjuist</span><span class="sxs-lookup"><span data-stu-id="a44a1-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="a44a1-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="a44a1-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="a44a1-246">Deze cmdlet ondersteunt de algemene parameters:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="a44a1-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="a44a1-247">Zie voor meer informatie [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="a44a1-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="a44a1-248">INVOER</span><span class="sxs-lookup"><span data-stu-id="a44a1-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="a44a1-249">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a44a1-249">String</span></span>

<span data-ttu-id="a44a1-250">Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.</span><span class="sxs-lookup"><span data-stu-id="a44a1-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="a44a1-251">Tekenreeks\[\]</span><span class="sxs-lookup"><span data-stu-id="a44a1-251">String\[\]</span></span>

<span data-ttu-id="a44a1-252">Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.</span><span class="sxs-lookup"><span data-stu-id="a44a1-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="a44a1-253">Resultaten</span><span class="sxs-lookup"><span data-stu-id="a44a1-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="a44a1-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="a44a1-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="a44a1-255">Deze cmdlet retourneert de autorisatie-regelobject.</span><span class="sxs-lookup"><span data-stu-id="a44a1-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="a44a1-256">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a44a1-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="a44a1-257">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="a44a1-257">EXAMPLE 1</span></span>

<span data-ttu-id="a44a1-258">In dit voorbeeld verleent toegang tot de sessieconfiguratie *Pswaeindpunt*, wordt er een beperkte runspace op *srv2* voor gebruikers in de *SMAdmins* groep. \\</span><span class="sxs-lookup"><span data-stu-id="a44a1-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="a44a1-259">**Opmerking**: naam van de computer moet een volledig gekwalificeerde domeinnaam (FQDN).</span><span class="sxs-lookup"><span data-stu-id="a44a1-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="a44a1-260">Beheerders definiëren een beperkte sessieconfiguratie of een runspace, dit is een beperkt aantal cmdlets en taken die eindgebruikers kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a44a1-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="a44a1-261">Het definiëren van een beperkte runspace kan voorkomen dat gebruikers toegang krijgen tot andere computers die niet in de toegestane Windows PowerShell® runspace, dus een beter beveiligde verbinding bieden.</span><span class="sxs-lookup"><span data-stu-id="a44a1-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="a44a1-262">Zie voor meer informatie over sessieconfiguraties [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) of de [installeren en gebruik Windows PowerShell-webtoegang](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="a44a1-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="a44a1-263">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="a44a1-263">EXAMPLE 2</span></span>

<span data-ttu-id="a44a1-264">In dit voorbeeld verleent toegang tot de Windows PowerShell-sessie standaardconfiguratie `Microsoft.PowerShell`op *srv2* voor gebruikers in de gebruikers met de naam contoso\\gebruiker1, contoso\\Gebruiker2 bevat, en contoso\\user3.</span><span class="sxs-lookup"><span data-stu-id="a44a1-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="a44a1-265">Deze cmdlet maakt drie regels (1 per persoon).</span><span class="sxs-lookup"><span data-stu-id="a44a1-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="a44a1-266">VOORBEELD 3</span><span class="sxs-lookup"><span data-stu-id="a44a1-266">EXAMPLE 3</span></span>

<span data-ttu-id="a44a1-267">In dit voorbeeld laat zien hoe voor het invoeren van waarden van de naam van gebruiker via de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="a44a1-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="a44a1-268">VOORBEELD 4</span><span class="sxs-lookup"><span data-stu-id="a44a1-268">EXAMPLE 4</span></span>

<span data-ttu-id="a44a1-269">In dit voorbeeld ziet u hoe u alle parameters waaruit waarden pijplijn naam van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="a44a1-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="a44a1-270">VOORBEELD 5</span><span class="sxs-lookup"><span data-stu-id="a44a1-270">EXAMPLE 5</span></span>

<span data-ttu-id="a44a1-271">In dit voorbeeld wordt een regel met de naam van de lokale gebruiker toe om *PswaServer\\ChrisLocal* toegang tot de server met de naam *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="a44a1-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="a44a1-272">In dit voorbeeld ziet u een scenario waarbij de gateway in een werkgroep en de doelcomputer zich in een domein.</span><span class="sxs-lookup"><span data-stu-id="a44a1-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="a44a1-273">De autorisatieregel is van toepassing op de lokale gebruikers op de gateway.</span><span class="sxs-lookup"><span data-stu-id="a44a1-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="a44a1-274">Klik op de pagina Windows PowerShell-webtoegang aanmelden om te verifiëren, moet de gebruiker leveren een tweede set referenties in de **optionele verbindingsinstellingen** gebied.</span><span class="sxs-lookup"><span data-stu-id="a44a1-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="a44a1-275">De gatewayserver de aanvullende set referenties gebruikt voor het verifiëren van de gebruiker op de doelcomputer, een server met de naam *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="a44a1-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="a44a1-276">VOORBEELD 6</span><span class="sxs-lookup"><span data-stu-id="a44a1-276">EXAMPLE 6</span></span>

<span data-ttu-id="a44a1-277">In dit voorbeeld kan alle gebruikers toegang tot alle eindpunten op alle computers.</span><span class="sxs-lookup"><span data-stu-id="a44a1-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="a44a1-278">Hierdoor wordt het in feite uitgeschakeld autorisatieregels. \\</span><span class="sxs-lookup"><span data-stu-id="a44a1-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="a44a1-279">**Opmerking**: het gebruik van de `*` jokerteken wordt niet aanbevolen voor implementaties van de beveiliging van gevoelige en moet alleen worden beschouwd voor testomgevingen of gebruikt in implementaties waarbij de beveiliging kan worden versoepeld.</span><span class="sxs-lookup"><span data-stu-id="a44a1-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="a44a1-280">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a44a1-280">See Also</span></span>

- <span data-ttu-id="a44a1-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="a44a1-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="a44a1-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="a44a1-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="a44a1-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="a44a1-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="a44a1-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="a44a1-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="a44a1-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="a44a1-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="a44a1-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="a44a1-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="a44a1-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="a44a1-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)