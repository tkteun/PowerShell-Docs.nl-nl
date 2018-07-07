---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a5e55611ac59ff5bfecee59ba2b7d7669d08f840
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893736"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="83d3d-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="83d3d-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="83d3d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="83d3d-104">SYNOPSIS</span></span>

<span data-ttu-id="83d3d-105">Voegt een nieuwe autorisatieregel toe aan de set met autorisatieregels Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="83d3d-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="83d3d-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="83d3d-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="83d3d-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="83d3d-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="83d3d-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="83d3d-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="83d3d-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="83d3d-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="83d3d-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="83d3d-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="83d3d-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="83d3d-111">DESCRIPTION</span></span>

<span data-ttu-id="83d3d-112">De **Add-PswaAuthorizationRule** cmdlet voegt een nieuwe autorisatieregel toe aan de set met autorisatieregels Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="83d3d-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="83d3d-113">U moet de gebruikers, computers en Windows PowerShell-eindpunten voor deze regel opgeven.</span><span class="sxs-lookup"><span data-stu-id="83d3d-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="83d3d-114">U kunt gebruikers en computers door afzonderlijke gebruikersaccounts en computernamen of door op te geven groepen opgeven.</span><span class="sxs-lookup"><span data-stu-id="83d3d-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="83d3d-115">Voor een computer die lid van een Active Directory-domein is, wordt de cmdlet de beveiligings-id (SID) van de computer gebruikt om de regel te maken.</span><span class="sxs-lookup"><span data-stu-id="83d3d-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="83d3d-116">Hiermee kunt u gebruikmaken van een korte naam, een volledig gekwalificeerde domeinnaam (FQDN) of een IP-adres voor de **computernaam** op de aanmeldingspagina.</span><span class="sxs-lookup"><span data-stu-id="83d3d-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="83d3d-117">De cmdlet maakt voor een computer die niet is gekoppeld aan een Active Directory-domein, de regel met behulp van de computernaam die is opgegeven door de beheerder.</span><span class="sxs-lookup"><span data-stu-id="83d3d-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="83d3d-118">Als u wilt verbinding maken met deze machine, moet de eindgebruiker de computernaam opgeven precies zoals deze wordt weergegeven in de regel.</span><span class="sxs-lookup"><span data-stu-id="83d3d-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="83d3d-119">Als er meerdere computers met dezelfde naam in het netwerk, kan korte naam omzetten in meer dan één computer.</span><span class="sxs-lookup"><span data-stu-id="83d3d-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="83d3d-120">Dit kan leiden tot verwarring bij het maken van een verbinding.</span><span class="sxs-lookup"><span data-stu-id="83d3d-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="83d3d-121">Bijvoorbeeld, als een regel bestaat voor de werkgroepcomputer met de naam '*Server1*' en een nieuwe computer met de naam *server1.contoso.com* is gekoppeld met het netwerk met behulp van regels voor de validatie is geslaagd en Windows PowerShell-webtoegang wil een verbinding met de computer met de naam '*Server1*'.</span><span class="sxs-lookup"><span data-stu-id="83d3d-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="83d3d-122">Is er geen garantie dat de verbinding tot stand is gebracht met de opgegeven werkgroepcomputer. de poging kan worden gemaakt op de werkgroep of het domeincomputer met de naam '*Server1*'.</span><span class="sxs-lookup"><span data-stu-id="83d3d-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="83d3d-123">Als u wilt verkleinen dubbelzinnigheid, wordt het aanbevolen dat u de FQDN-naam voor de doelcomputer wanneer dit mogelijk gebruiken te maken van een autorisatieregel.</span><span class="sxs-lookup"><span data-stu-id="83d3d-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="83d3d-124">Regels voor het evalueren van de primaire aanmelden referentie van de Windows PowerShell Web Access-gebruikers, niet de alternatieve referenties (de tweede set referenties die zijn gevonden in de **optionele verbindingsinstellingen** sectie van de aanmeldingspagina).</span><span class="sxs-lookup"><span data-stu-id="83d3d-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="83d3d-125">Zie voor een voorbeeld van dit voorbeeld 6.</span><span class="sxs-lookup"><span data-stu-id="83d3d-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="83d3d-126">Parameters</span><span class="sxs-lookup"><span data-stu-id="83d3d-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="83d3d-127">-ComputerGroupName \<tekenreeks\></span><span class="sxs-lookup"><span data-stu-id="83d3d-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="83d3d-128">Hiermee geeft u de naam van een computergroep in Active Directory Domain Services (AD DS) of het lokale groepen waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="83d3d-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="83d3d-129">Aliassen</span><span class="sxs-lookup"><span data-stu-id="83d3d-129">Aliases</span></span>                              | <span data-ttu-id="83d3d-130">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-130">none</span></span>                                 |
| <span data-ttu-id="83d3d-131">Nodig?</span><span class="sxs-lookup"><span data-stu-id="83d3d-131">Required?</span></span>                            | <span data-ttu-id="83d3d-132">True</span><span class="sxs-lookup"><span data-stu-id="83d3d-132">true</span></span>                                 |
| <span data-ttu-id="83d3d-133">Positie?</span><span class="sxs-lookup"><span data-stu-id="83d3d-133">Position?</span></span>                            | <span data-ttu-id="83d3d-134">met de naam</span><span class="sxs-lookup"><span data-stu-id="83d3d-134">named</span></span>                                |
| <span data-ttu-id="83d3d-135">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="83d3d-135">Default Value</span></span>                        | <span data-ttu-id="83d3d-136">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-136">none</span></span>                                 |
| <span data-ttu-id="83d3d-137">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="83d3d-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="83d3d-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="83d3d-139">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="83d3d-140">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-140">false</span></span>                                |

### <a name="-computername-string"></a><span data-ttu-id="83d3d-141">-ComputerName \<tekenreeks\></span><span class="sxs-lookup"><span data-stu-id="83d3d-141">-ComputerName \<String\></span></span>

<span data-ttu-id="83d3d-142">Hiermee geeft u de naam van de computer waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="83d3d-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="83d3d-143">Aliassen</span><span class="sxs-lookup"><span data-stu-id="83d3d-143">Aliases</span></span>                              | <span data-ttu-id="83d3d-144">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-144">none</span></span>                                 |
| <span data-ttu-id="83d3d-145">Nodig?</span><span class="sxs-lookup"><span data-stu-id="83d3d-145">Required?</span></span>                            | <span data-ttu-id="83d3d-146">True</span><span class="sxs-lookup"><span data-stu-id="83d3d-146">true</span></span>                                 |
| <span data-ttu-id="83d3d-147">Positie?</span><span class="sxs-lookup"><span data-stu-id="83d3d-147">Position?</span></span>                            | <span data-ttu-id="83d3d-148">met de naam</span><span class="sxs-lookup"><span data-stu-id="83d3d-148">named</span></span>                                |
| <span data-ttu-id="83d3d-149">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="83d3d-149">Default Value</span></span>                        | <span data-ttu-id="83d3d-150">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-150">none</span></span>                                 |
| <span data-ttu-id="83d3d-151">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="83d3d-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="83d3d-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="83d3d-153">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="83d3d-154">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-154">false</span></span>                                |

### <a name="-configurationname-string"></a><span data-ttu-id="83d3d-155">-ConfigurationName \<tekenreeks\></span><span class="sxs-lookup"><span data-stu-id="83d3d-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="83d3d-156">Hiermee geeft u de naam van de configuratie van Windows PowerShell-sessie, ook wel bekend als runspace, waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="83d3d-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="83d3d-157">Aliassen</span><span class="sxs-lookup"><span data-stu-id="83d3d-157">Aliases</span></span>                              | <span data-ttu-id="83d3d-158">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-158">none</span></span>                                 |
| <span data-ttu-id="83d3d-159">Nodig?</span><span class="sxs-lookup"><span data-stu-id="83d3d-159">Required?</span></span>                            | <span data-ttu-id="83d3d-160">True</span><span class="sxs-lookup"><span data-stu-id="83d3d-160">true</span></span>                                 |
| <span data-ttu-id="83d3d-161">Positie?</span><span class="sxs-lookup"><span data-stu-id="83d3d-161">Position?</span></span>                            | <span data-ttu-id="83d3d-162">met de naam</span><span class="sxs-lookup"><span data-stu-id="83d3d-162">named</span></span>                                |
| <span data-ttu-id="83d3d-163">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="83d3d-163">Default Value</span></span>                        | <span data-ttu-id="83d3d-164">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-164">none</span></span>                                 |
| <span data-ttu-id="83d3d-165">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="83d3d-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="83d3d-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="83d3d-167">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="83d3d-168">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-168">false</span></span>                                |

### <a name="-credential--pscredential"></a><span data-ttu-id="83d3d-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="83d3d-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="83d3d-170">Hiermee geeft u een **PSCredential** -object voor een gebruikersaccount dat u wilt gebruiken voor het wijzigen van de Windows PowerShell-webtoegang autorisatieregels.</span><span class="sxs-lookup"><span data-stu-id="83d3d-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="83d3d-171">Als u deze parameter niet toevoegt, gebruikt de cmdlet het gebruikersaccount momenteel is aangemeld.</span><span class="sxs-lookup"><span data-stu-id="83d3d-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="83d3d-172">Om op te halen een **PSCredential** object, dat vereist voor het op afstand autorisatieregels toevoegen is, voert u de [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83d3d-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="83d3d-173">Aliassen</span><span class="sxs-lookup"><span data-stu-id="83d3d-173">Aliases</span></span>                              | <span data-ttu-id="83d3d-174">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-174">none</span></span>                                 |
| <span data-ttu-id="83d3d-175">Nodig?</span><span class="sxs-lookup"><span data-stu-id="83d3d-175">Required?</span></span>                            | <span data-ttu-id="83d3d-176">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-176">false</span></span>                                |
| <span data-ttu-id="83d3d-177">Positie?</span><span class="sxs-lookup"><span data-stu-id="83d3d-177">Position?</span></span>                            | <span data-ttu-id="83d3d-178">met de naam</span><span class="sxs-lookup"><span data-stu-id="83d3d-178">named</span></span>                                |
| <span data-ttu-id="83d3d-179">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="83d3d-179">Default Value</span></span>                        | <span data-ttu-id="83d3d-180">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-180">none</span></span>                                 |
| <span data-ttu-id="83d3d-181">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="83d3d-182">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-182">false</span></span>                                |
| <span data-ttu-id="83d3d-183">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="83d3d-184">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="83d3d-185">-Force</span><span class="sxs-lookup"><span data-stu-id="83d3d-185">-Force</span></span>

<span data-ttu-id="83d3d-186">Hiermee wordt de opdracht uitgevoerd zonder gebruikersbevestiging. \\</span><span class="sxs-lookup"><span data-stu-id="83d3d-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="83d3d-187">Daarnaast wordt ook gevraagd om bevestiging bij het invoeren van een eenvoudige of korte computernaam (zoals een naam die niet de naam van een domein of is niet volledig gekwalificeerd).</span><span class="sxs-lookup"><span data-stu-id="83d3d-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="83d3d-188">Bevestiging is aangevraagd voor opmaaktalen wordt om beveiligingsredenen, zodat u de naam van de eenvoudige gebruiken kunt om toe te voegen een computer als de computer in een werkgroep.</span><span class="sxs-lookup"><span data-stu-id="83d3d-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="83d3d-189">Aliassen</span><span class="sxs-lookup"><span data-stu-id="83d3d-189">Aliases</span></span>                              | <span data-ttu-id="83d3d-190">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-190">none</span></span>                                 |
| <span data-ttu-id="83d3d-191">Nodig?</span><span class="sxs-lookup"><span data-stu-id="83d3d-191">Required?</span></span>                            | <span data-ttu-id="83d3d-192">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-192">false</span></span>                                |
| <span data-ttu-id="83d3d-193">Positie?</span><span class="sxs-lookup"><span data-stu-id="83d3d-193">Position?</span></span>                            | <span data-ttu-id="83d3d-194">met de naam</span><span class="sxs-lookup"><span data-stu-id="83d3d-194">named</span></span>                                |
| <span data-ttu-id="83d3d-195">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="83d3d-195">Default Value</span></span>                        | <span data-ttu-id="83d3d-196">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-196">none</span></span>                                 |
| <span data-ttu-id="83d3d-197">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="83d3d-198">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-198">false</span></span>                                |
| <span data-ttu-id="83d3d-199">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="83d3d-200">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="83d3d-201">-RuleName \<tekenreeks\></span><span class="sxs-lookup"><span data-stu-id="83d3d-201">-RuleName \<String\></span></span>

<span data-ttu-id="83d3d-202">Hiermee geeft u de beschrijvende naam voor deze regel.</span><span class="sxs-lookup"><span data-stu-id="83d3d-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="83d3d-203">Aliassen</span><span class="sxs-lookup"><span data-stu-id="83d3d-203">Aliases</span></span>                              | <span data-ttu-id="83d3d-204">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-204">none</span></span>                                 |
| <span data-ttu-id="83d3d-205">Nodig?</span><span class="sxs-lookup"><span data-stu-id="83d3d-205">Required?</span></span>                            | <span data-ttu-id="83d3d-206">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-206">false</span></span>                                |
| <span data-ttu-id="83d3d-207">Positie?</span><span class="sxs-lookup"><span data-stu-id="83d3d-207">Position?</span></span>                            | <span data-ttu-id="83d3d-208">met de naam</span><span class="sxs-lookup"><span data-stu-id="83d3d-208">named</span></span>                                |
| <span data-ttu-id="83d3d-209">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="83d3d-209">Default Value</span></span>                        | <span data-ttu-id="83d3d-210">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-210">none</span></span>                                 |
| <span data-ttu-id="83d3d-211">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="83d3d-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="83d3d-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="83d3d-213">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="83d3d-214">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="83d3d-215">-UserGroupName \<tekenreeks\[\]\></span><span class="sxs-lookup"><span data-stu-id="83d3d-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="83d3d-216">Hiermee geeft u de naam van een of meer gebruikersgroepen in AD DS of lokale groepen waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="83d3d-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="83d3d-217">Aliassen</span><span class="sxs-lookup"><span data-stu-id="83d3d-217">Aliases</span></span>                              | <span data-ttu-id="83d3d-218">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-218">none</span></span>                                 |
| <span data-ttu-id="83d3d-219">Nodig?</span><span class="sxs-lookup"><span data-stu-id="83d3d-219">Required?</span></span>                            | <span data-ttu-id="83d3d-220">True</span><span class="sxs-lookup"><span data-stu-id="83d3d-220">true</span></span>                                 |
| <span data-ttu-id="83d3d-221">Positie?</span><span class="sxs-lookup"><span data-stu-id="83d3d-221">Position?</span></span>                            | <span data-ttu-id="83d3d-222">met de naam</span><span class="sxs-lookup"><span data-stu-id="83d3d-222">named</span></span>                                |
| <span data-ttu-id="83d3d-223">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="83d3d-223">Default Value</span></span>                        | <span data-ttu-id="83d3d-224">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-224">none</span></span>                                 |
| <span data-ttu-id="83d3d-225">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="83d3d-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="83d3d-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="83d3d-227">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="83d3d-228">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="83d3d-229">-UserName \<tekenreeks\[\]\></span><span class="sxs-lookup"><span data-stu-id="83d3d-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="83d3d-230">Hiermee geeft u een of meer gebruikers waarop deze regel toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="83d3d-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="83d3d-231">Naam van de gebruiker kan een lokale gebruikersaccount op de computer met de gateway of een gebruiker in AD DS zijn.</span><span class="sxs-lookup"><span data-stu-id="83d3d-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="83d3d-232">De indeling is `domain\user` of `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="83d3d-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="83d3d-233">Aliassen</span><span class="sxs-lookup"><span data-stu-id="83d3d-233">Aliases</span></span>                              | <span data-ttu-id="83d3d-234">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-234">none</span></span>                                 |
| <span data-ttu-id="83d3d-235">Nodig?</span><span class="sxs-lookup"><span data-stu-id="83d3d-235">Required?</span></span>                            | <span data-ttu-id="83d3d-236">True</span><span class="sxs-lookup"><span data-stu-id="83d3d-236">true</span></span>                                 |
| <span data-ttu-id="83d3d-237">Positie?</span><span class="sxs-lookup"><span data-stu-id="83d3d-237">Position?</span></span>                            | <span data-ttu-id="83d3d-238">1</span><span class="sxs-lookup"><span data-stu-id="83d3d-238">1</span></span>                                    |
| <span data-ttu-id="83d3d-239">Standaardwaarde</span><span class="sxs-lookup"><span data-stu-id="83d3d-239">Default Value</span></span>                        | <span data-ttu-id="83d3d-240">geen</span><span class="sxs-lookup"><span data-stu-id="83d3d-240">none</span></span>                                 |
| <span data-ttu-id="83d3d-241">Pijplijn-invoer accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="83d3d-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="83d3d-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="83d3d-243">Jokertekens accepteren?</span><span class="sxs-lookup"><span data-stu-id="83d3d-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="83d3d-244">onjuist</span><span class="sxs-lookup"><span data-stu-id="83d3d-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="83d3d-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="83d3d-245">\<CommonParameters\></span></span>

<span data-ttu-id="83d3d-246">Deze cmdlet worden de gangbare parameters ondersteund:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer en - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="83d3d-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="83d3d-247">Zie voor meer informatie, [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="83d3d-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="83d3d-248">INVOER</span><span class="sxs-lookup"><span data-stu-id="83d3d-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="83d3d-249">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="83d3d-249">String</span></span>

<span data-ttu-id="83d3d-250">Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.</span><span class="sxs-lookup"><span data-stu-id="83d3d-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="83d3d-251">Tekenreeks\[\]</span><span class="sxs-lookup"><span data-stu-id="83d3d-251">String\[\]</span></span>

<span data-ttu-id="83d3d-252">Deze cmdlet accepteert een tekenreeks of een matrix met tekenreeksen als invoer.</span><span class="sxs-lookup"><span data-stu-id="83d3d-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="83d3d-253">Resultaten</span><span class="sxs-lookup"><span data-stu-id="83d3d-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="83d3d-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="83d3d-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="83d3d-255">Deze cmdlet retourneert de autorisatie-regelobject.</span><span class="sxs-lookup"><span data-stu-id="83d3d-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="83d3d-256">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="83d3d-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="83d3d-257">VOORBEELD 1</span><span class="sxs-lookup"><span data-stu-id="83d3d-257">EXAMPLE 1</span></span>

<span data-ttu-id="83d3d-258">In dit voorbeeld verleent toegang tot de sessieconfiguratie *Pswaeindpunt*, een beperkte runspace op *srv2* voor gebruikers in de *SMAdmins* groep. \\</span><span class="sxs-lookup"><span data-stu-id="83d3d-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="83d3d-259">**Houd er rekening mee**: naam van de computer moet een volledig gekwalificeerde domeinnaam (FQDN).</span><span class="sxs-lookup"><span data-stu-id="83d3d-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="83d3d-260">Beheerders definiëren voor een beperkte sessieconfiguratie of een runspace, dit is een beperkt aantal cmdlets en taken die eindgebruikers kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="83d3d-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="83d3d-261">Een beperkte runspace te definiëren kan voorkomen dat gebruikers toegang tot andere computers die niet in de toegestane Windows PowerShell® runspace, dus firewallopties voor een beter beveiligde verbinding.</span><span class="sxs-lookup"><span data-stu-id="83d3d-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="83d3d-262">Zie voor meer informatie over sessieconfiguraties [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) of de [installeren en gebruik Windows PowerShell-webtoegang](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="83d3d-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="83d3d-263">VOORBEELD 2</span><span class="sxs-lookup"><span data-stu-id="83d3d-263">EXAMPLE 2</span></span>

<span data-ttu-id="83d3d-264">In dit voorbeeld verleent toegang tot de Windows PowerShell-sessie standaardconfiguratie `Microsoft.PowerShell`op *srv2* voor gebruikers in de gebruikers met de naam `contoso\user1`, `contoso\user2`, en `contoso\user3`.</span><span class="sxs-lookup"><span data-stu-id="83d3d-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="83d3d-265">Met deze cmdlet maakt drie regels (1 per persoon).</span><span class="sxs-lookup"><span data-stu-id="83d3d-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="83d3d-266">VOORBEELD 3</span><span class="sxs-lookup"><span data-stu-id="83d3d-266">EXAMPLE 3</span></span>

<span data-ttu-id="83d3d-267">In dit voorbeeld ziet u hoe u voor het invoeren van waarden van de naam van gebruiker via de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="83d3d-267">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="83d3d-268">VOORBEELD 4</span><span class="sxs-lookup"><span data-stu-id="83d3d-268">EXAMPLE 4</span></span>

<span data-ttu-id="83d3d-269">In dit voorbeeld laat zien hoe alle parameters, nemen de waarden van de pijplijn door de naam van eigenschap.</span><span class="sxs-lookup"><span data-stu-id="83d3d-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="83d3d-270">VOORBEELD 5</span><span class="sxs-lookup"><span data-stu-id="83d3d-270">EXAMPLE 5</span></span>

<span data-ttu-id="83d3d-271">In dit voorbeeld wordt een regel voor het toestaan van de lokale gebruiker met de naam `PswaServer\ChrisLocal` toegang tot de server met de naam **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="83d3d-271">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="83d3d-272">In dit voorbeeld wordt een scenario waarin de gateway zich in een werkgroep en de doelcomputer zich in een domein.</span><span class="sxs-lookup"><span data-stu-id="83d3d-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="83d3d-273">De autorisatieregel is van toepassing op de lokale gebruikers op de gateway.</span><span class="sxs-lookup"><span data-stu-id="83d3d-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="83d3d-274">Op de Windows PowerShell-webtoegang aanmelden pagina als u wilt verifiëren, moet de gebruiker leveren een tweede set referenties in de **optionele verbindingsinstellingen** gebied.</span><span class="sxs-lookup"><span data-stu-id="83d3d-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="83d3d-275">De gateway-server gebruikt de aanvullende set referenties voor het verifiëren van de gebruiker op de doelcomputer, een server met de naam *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="83d3d-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="83d3d-276">VOORBEELD 6</span><span class="sxs-lookup"><span data-stu-id="83d3d-276">EXAMPLE 6</span></span>

<span data-ttu-id="83d3d-277">In dit voorbeeld kan alle gebruikers toegang tot alle eindpunten op alle computers.</span><span class="sxs-lookup"><span data-stu-id="83d3d-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="83d3d-278">Hiermee schakelt u in feite uit autorisatieregels. \\</span><span class="sxs-lookup"><span data-stu-id="83d3d-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="83d3d-279">**Houd er rekening mee**: het gebruik van de `*` jokerteken wordt niet aanbevolen voor implementaties van de beveiliging van gevoelige en moet alleen worden beschouwd voor testomgevingen of wordt gebruikt in implementaties waarbij de beveiliging kan worden verminderd.</span><span class="sxs-lookup"><span data-stu-id="83d3d-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="83d3d-280">Zie ook</span><span class="sxs-lookup"><span data-stu-id="83d3d-280">See Also</span></span>

<span data-ttu-id="83d3d-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="83d3d-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="83d3d-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="83d3d-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="83d3d-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="83d3d-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="83d3d-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="83d3d-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="83d3d-285">Add Member</span><span class="sxs-lookup"><span data-stu-id="83d3d-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="83d3d-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="83d3d-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="83d3d-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="83d3d-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)