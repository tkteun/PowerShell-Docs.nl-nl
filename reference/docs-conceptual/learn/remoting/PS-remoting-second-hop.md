---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De tweede hop maken voor externe communicatie met PowerShell
ms.openlocfilehash: 1b6e5ad53346324adc7be2d013e154c8600afa4f
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265583"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="d5d69-103">De tweede hop maken voor externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5d69-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="d5d69-104">De 'tweede hop '-probleem verwijst naar een situatie als volgt:</span><span class="sxs-lookup"><span data-stu-id="d5d69-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="d5d69-105">U bent aangemeld bij _ServerA_.</span><span class="sxs-lookup"><span data-stu-id="d5d69-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="d5d69-106">Van _ServerA_, u verbinding maken met een externe PowerShell-sessie starten _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="d5d69-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="d5d69-107">Een opdracht die u uitvoert op _ServerB_ via uw externe communicatie van PowerShell sessie probeert te krijgen tot een bron op _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="d5d69-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="d5d69-108">Toegang tot de resource op _ServerC_ is geweigerd omdat de referenties die u gebruikt voor het maken van de externe communicatie van PowerShell-sessie niet worden doorgegeven van _ServerB_ naar _ServerC_.</span><span class="sxs-lookup"><span data-stu-id="d5d69-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="d5d69-109">Er zijn verschillende manieren om dit probleem te verhelpen.</span><span class="sxs-lookup"><span data-stu-id="d5d69-109">There are several ways to address this problem.</span></span> <span data-ttu-id="d5d69-110">In dit onderwerp, zullen we verschillende van de meest populaire oplossingen voor het tweede hop probleem.</span><span class="sxs-lookup"><span data-stu-id="d5d69-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="d5d69-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="d5d69-111">CredSSP</span></span>

<span data-ttu-id="d5d69-112">U kunt de [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="d5d69-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="d5d69-113">CredSSP in de cache opgeslagen referenties op de externe server (_ServerB_), zodat deze wordt geopend u maximaal credential theft aanvallen.</span><span class="sxs-lookup"><span data-stu-id="d5d69-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="d5d69-114">Als de externe computer is geknoeid, heeft de aanvaller toegang tot de referenties van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d5d69-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="d5d69-115">CredSSP is standaard uitgeschakeld in zowel client- en servercomputers.</span><span class="sxs-lookup"><span data-stu-id="d5d69-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="d5d69-116">Alleen in de meest vertrouwde omgevingen, moet u CredSSP inschakelen.</span><span class="sxs-lookup"><span data-stu-id="d5d69-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="d5d69-117">Bijvoorbeeld, een domeinbeheerder verbinding te maken met een domeincontroller, omdat de domeincontroller uiterst vertrouwde is.</span><span class="sxs-lookup"><span data-stu-id="d5d69-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="d5d69-118">Zie voor meer informatie over de beveiligingsoverwegingen wanneer u CredSSP voor externe communicatie van PowerShell [onbedoeld Sabotage: Houd er rekening mee van CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span><span class="sxs-lookup"><span data-stu-id="d5d69-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="d5d69-119">Zie voor meer informatie over credential theft aanvallen [Mitigating Pass-the-Hash (PtH) aanvallen en andere Referentiediefstal](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span><span class="sxs-lookup"><span data-stu-id="d5d69-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="d5d69-120">Zie voor een voorbeeld van hoe u inschakelen en gebruiken van CredSSP voor externe communicatie van PowerShell [CredSSP met behulp van de tweede hop probleem op te lossen](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span><span class="sxs-lookup"><span data-stu-id="d5d69-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="d5d69-121">Voordelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-121">Pros</span></span>

- <span data-ttu-id="d5d69-122">De Tool werkt voor alle servers met Windows Server 2008 of hoger.</span><span class="sxs-lookup"><span data-stu-id="d5d69-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="d5d69-123">Nadelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-123">Cons</span></span>

- <span data-ttu-id="d5d69-124">Beveiligingsproblemen heeft.</span><span class="sxs-lookup"><span data-stu-id="d5d69-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="d5d69-125">Configuratie van functies voor zowel client als server vereist.</span><span class="sxs-lookup"><span data-stu-id="d5d69-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="d5d69-126">Kerberos-overdracht (een)</span><span class="sxs-lookup"><span data-stu-id="d5d69-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="d5d69-127">U kunt ook een Kerberos-overdracht gebruikt voor het maken van de tweede hop.</span><span class="sxs-lookup"><span data-stu-id="d5d69-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="d5d69-128">Deze methode biedt echter geen controle van waar de gedelegeerde referenties worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d5d69-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="d5d69-129">**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden overgedragen.</span><span class="sxs-lookup"><span data-stu-id="d5d69-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="d5d69-130">Zie voor meer informatie [Focus beveiliging: Analyse van 'Account is vertrouwelijk en kan niet worden overgedragen' voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="d5d69-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="d5d69-131">Voordelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-131">Pros</span></span>

- <span data-ttu-id="d5d69-132">Vereist geen speciale coderen.</span><span class="sxs-lookup"><span data-stu-id="d5d69-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="d5d69-133">Nadelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-133">Cons</span></span>

- <span data-ttu-id="d5d69-134">Biedt de tweede hop geen ondersteuning voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="d5d69-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="d5d69-135">Biedt geen controle over waar de referenties worden gebruikt, het maken van een beveiligingsprobleem.</span><span class="sxs-lookup"><span data-stu-id="d5d69-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="d5d69-136">Kerberos-beperkte overdracht</span><span class="sxs-lookup"><span data-stu-id="d5d69-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="d5d69-137">Verouderde beperkte delegering (geen resource gebaseerde) kunt u de tweede hop maken.</span><span class="sxs-lookup"><span data-stu-id="d5d69-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="d5d69-138">Kerberos-beperkte overdracht configureren met de optie "Elk protocol voor verificatie gebruiken" om toe te staan van overgang.</span><span class="sxs-lookup"><span data-stu-id="d5d69-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="d5d69-139">Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden overgedragen.</span><span class="sxs-lookup"><span data-stu-id="d5d69-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="d5d69-140">Zie voor meer informatie [Focus beveiliging: Analyse van 'Account is vertrouwelijk en kan niet worden overgedragen' voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="d5d69-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="d5d69-141">Voordelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-141">Pros</span></span>

- <span data-ttu-id="d5d69-142">Vereist geen speciale coderen</span><span class="sxs-lookup"><span data-stu-id="d5d69-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="d5d69-143">Nadelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-143">Cons</span></span>

- <span data-ttu-id="d5d69-144">Biedt de tweede hop geen ondersteuning voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="d5d69-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="d5d69-145">Moet worden geconfigureerd op de Active Directory-object van de externe server (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="d5d69-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="d5d69-146">Beperkt tot één domein.</span><span class="sxs-lookup"><span data-stu-id="d5d69-146">Limited to one domain.</span></span> <span data-ttu-id="d5d69-147">Kan niet meerdere domeinen of forests.</span><span class="sxs-lookup"><span data-stu-id="d5d69-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="d5d69-148">Rechten voor het bijwerken van objecten en Service Principal Names (SPN's) vereist.</span><span class="sxs-lookup"><span data-stu-id="d5d69-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="d5d69-149">Bronnen gebaseerde beperkte Kerberos-overdracht</span><span class="sxs-lookup"><span data-stu-id="d5d69-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="d5d69-150">Met behulp van Kerberos bronnen gebaseerde beperkte delegering (geïntroduceerd in Windows Server 2012), configureert u de overdracht van referenties op het object van de server waar de bronnen zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="d5d69-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="d5d69-151">In het tweede hop-scenario die hierboven worden beschreven, configureert u _ServerC_ om op te geven van waar worden geaccepteerd overgedragen referenties.</span><span class="sxs-lookup"><span data-stu-id="d5d69-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="d5d69-152">**Opmerking:** Active Directory-accounts waarvoor de **Account is vertrouwelijk en kan niet worden overgedragen** eigenschap is ingesteld, kan niet worden overgedragen.</span><span class="sxs-lookup"><span data-stu-id="d5d69-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="d5d69-153">Zie voor meer informatie [Focus beveiliging: Analyse van 'Account is vertrouwelijk en kan niet worden overgedragen' voor bevoegde Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) en [Kerberos-verificatie-hulpprogramma's en instellingen](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="d5d69-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="d5d69-154">Voordelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-154">Pros</span></span>

- <span data-ttu-id="d5d69-155">Referenties worden niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="d5d69-155">Credentials are not stored.</span></span>
- <span data-ttu-id="d5d69-156">Betrekkelijk eenvoudig te configureren met behulp van PowerShell-cmdlets--er is geen speciale codering vereist.</span><span class="sxs-lookup"><span data-stu-id="d5d69-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="d5d69-157">Er is geen speciale domeintoegang is vereist.</span><span class="sxs-lookup"><span data-stu-id="d5d69-157">No special domain access is required.</span></span>
- <span data-ttu-id="d5d69-158">Deze optie werkt in domeinen en forests.</span><span class="sxs-lookup"><span data-stu-id="d5d69-158">Works across domains and forests.</span></span>
- <span data-ttu-id="d5d69-159">PowerShell-code.</span><span class="sxs-lookup"><span data-stu-id="d5d69-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="d5d69-160">Nadelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-160">Cons</span></span>

- <span data-ttu-id="d5d69-161">WindowsServer 2012 of later vereist.</span><span class="sxs-lookup"><span data-stu-id="d5d69-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="d5d69-162">Biedt de tweede hop geen ondersteuning voor WinRM.</span><span class="sxs-lookup"><span data-stu-id="d5d69-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="d5d69-163">Rechten voor het bijwerken van objecten en Service Principal Names (SPN's) vereist.</span><span class="sxs-lookup"><span data-stu-id="d5d69-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="d5d69-164">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d5d69-164">Example</span></span>

<span data-ttu-id="d5d69-165">Bekijk een voorbeeld van de resource configureert u beperkte delegering op basis van PowerShell _ServerC_ waarmee gedelegeerde referenties van een _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="d5d69-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="d5d69-166">In dit voorbeeld wordt ervan uitgegaan dat alle servers worden uitgevoerd met WindowsServer 2012 of later, en of er ten minste één Windows Server 2012-domeincontroller waarop elke van de servers elk domein behoren.</span><span class="sxs-lookup"><span data-stu-id="d5d69-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="d5d69-167">Voordat u beperkte delegering configureren kunt, moet u toevoegen de `RSAT-AD-PowerShell` om te installeren van de Active Directory PowerShell-module en vervolgens importeren die module in uw sessie:</span><span class="sxs-lookup"><span data-stu-id="d5d69-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="d5d69-168">Verschillende beschikbare cmdlets hebt nu een **PrincipalsAllowedToDelegateToAccount** parameter:</span><span class="sxs-lookup"><span data-stu-id="d5d69-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="d5d69-169">De **PrincipalsAllowedToDelegateToAccount** parameter stelt het Active Directory-objectkenmerk **msDS-AllowedToActOnBehalfOfOtherIdentity**, die een toegangsbeheerlijst (ACL) bevat die Hiermee geeft u op welke accounts gemachtigd voor het overdragen van referenties voor de gekoppelde account (in ons voorbeeld dient de computeraccount voor _Server_).</span><span class="sxs-lookup"><span data-stu-id="d5d69-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="d5d69-170">Nu gaan we instellen van de variabelen die we gebruiken om weer te geven van de servers:</span><span class="sxs-lookup"><span data-stu-id="d5d69-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="d5d69-171">WinRM (en dus PowerShell voor externe toegang) wordt uitgevoerd als het computeraccount standaard.</span><span class="sxs-lookup"><span data-stu-id="d5d69-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="d5d69-172">U kunt dit zien door te kijken naar de **StartName** eigenschap van de `winrm` service:</span><span class="sxs-lookup"><span data-stu-id="d5d69-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="d5d69-173">Voor _ServerC_ waarmee de overdracht van een PowerShell-sessie voor externe toegang op _ServerB_, zullen we toegang verlenen door in te stellen de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ voor het computerobject van _ServerB_:</span><span class="sxs-lookup"><span data-stu-id="d5d69-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="d5d69-174">Het Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches geweigerd toegangspogingen (negatieve cache) gedurende 15 minuten.</span><span class="sxs-lookup"><span data-stu-id="d5d69-174">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="d5d69-175">Als _ServerB_ eerder heeft geprobeerd toegang te _ServerC_, moet u de cache wissen op _ServerB_ door het aanroepen van de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="d5d69-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="d5d69-176">U kunt ook de computer opnieuw opstarten of wacht ten minste 15 minuten om de cache te wissen.</span><span class="sxs-lookup"><span data-stu-id="d5d69-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="d5d69-177">Na het uitschakelen van de cache kunt u de code van uitgevoerd _ServerA_ via _ServerB_ naar _ServerC_:</span><span class="sxs-lookup"><span data-stu-id="d5d69-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="d5d69-178">In dit voorbeeld wordt de `$using` variabele wordt gebruikt om de `$ServerC` variabele zichtbaar is voor _ServerB_.</span><span class="sxs-lookup"><span data-stu-id="d5d69-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="d5d69-179">Voor meer informatie over de `$using` variabele, Zie [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="d5d69-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="d5d69-180">Op meerdere servers te delegeren referenties _ServerC_, stel de waarde van de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ om in een matrix:</span><span class="sxs-lookup"><span data-stu-id="d5d69-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="d5d69-181">Als u maken van de tweede hop tussen domeinen wilt, volledig gekwalificeerde domeinnaam (FQDN) van de domeincontroller van het domein aan toevoegen die _ServerB_ behoort:</span><span class="sxs-lookup"><span data-stu-id="d5d69-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="d5d69-182">Als u wilt verwijderen van de mogelijkheid overdragen van referenties voor ServerC, stel de waarde van de **PrincipalsAllowedToDelegateToAccount** parameter op _ServerC_ naar `$null`:</span><span class="sxs-lookup"><span data-stu-id="d5d69-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="d5d69-183">Informatie over bronnen gebaseerde beperkte Kerberos-overdracht</span><span class="sxs-lookup"><span data-stu-id="d5d69-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="d5d69-184">Wat is er nieuw in Kerberos-verificatie</span><span class="sxs-lookup"><span data-stu-id="d5d69-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- [<span data-ttu-id="d5d69-185">Hoe Windows Server 2012 versnellingen de last van het Kerberos-beperkte overdracht, deel 1</span><span class="sxs-lookup"><span data-stu-id="d5d69-185">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)
- [<span data-ttu-id="d5d69-186">Hoe Windows Server 2012 versnellingen de last van het Kerberos-beperkte overdracht, deel 2</span><span class="sxs-lookup"><span data-stu-id="d5d69-186">How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2</span></span>](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)
- [<span data-ttu-id="d5d69-187">Informatie over Kerberos-beperkte overdracht voor Azure Active Directory Application Proxy implementaties met geïntegreerde Windows-verificatie</span><span class="sxs-lookup"><span data-stu-id="d5d69-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="d5d69-188">[[MS-ADA2]: Active Directory-Schema kenmerken M2.210 kenmerk msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span><span class="sxs-lookup"><span data-stu-id="d5d69-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="d5d69-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and beperkte delegering Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span><span class="sxs-lookup"><span data-stu-id="d5d69-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="d5d69-190">Resource op basis van Kerberos-beperkte overdracht</span><span class="sxs-lookup"><span data-stu-id="d5d69-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [<span data-ttu-id="d5d69-191">Extern beheer zonder beperkte delegering PrincipalsAllowedToDelegateToAccount gebruiken</span><span class="sxs-lookup"><span data-stu-id="d5d69-191">Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount</span></span>](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="d5d69-192">Met RunAs-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="d5d69-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="d5d69-193">U kunt een sessieconfiguratie maken op _ServerB_ en stel de **RunAsCredential** parameter.</span><span class="sxs-lookup"><span data-stu-id="d5d69-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="d5d69-194">Zie voor meer informatie over het gebruik van PSSessionConfiguration en RunAs voor het oplossen van de tweede hop probleem [andere oplossing voor externe communicatie van PowerShell Multihop](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span><span class="sxs-lookup"><span data-stu-id="d5d69-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="d5d69-195">Voordelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-195">Pros</span></span>

- <span data-ttu-id="d5d69-196">Als u werkt met een server met WMF 3.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="d5d69-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="d5d69-197">Nadelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-197">Cons</span></span>

- <span data-ttu-id="d5d69-198">Configuratie van vereist **PSSessionConfiguration** en **RunAs** op elke server tussenliggende (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="d5d69-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="d5d69-199">Wachtwoord onderhoud is vereist bij het gebruik van een domein **RunAs** account</span><span class="sxs-lookup"><span data-stu-id="d5d69-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="d5d69-200">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="d5d69-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="d5d69-201">JEA kunt u beperken welke opdrachten die een beheerder kan worden uitgevoerd tijdens een PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="d5d69-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="d5d69-202">Het kan worden gebruikt voor het oplossen van de tweede hop probleem.</span><span class="sxs-lookup"><span data-stu-id="d5d69-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="d5d69-203">Zie voor meer informatie over JEA [net genoeg beheer](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="d5d69-203">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="d5d69-204">Voordelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-204">Pros</span></span>

- <span data-ttu-id="d5d69-205">Er is geen wachtwoord onderhoud bij gebruik van een virtueel account.</span><span class="sxs-lookup"><span data-stu-id="d5d69-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="d5d69-206">Nadelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-206">Cons</span></span>

- <span data-ttu-id="d5d69-207">WMF 5.0 of hoger vereist.</span><span class="sxs-lookup"><span data-stu-id="d5d69-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="d5d69-208">Moet worden geconfigureerd op elke server tussenliggende (_ServerB_).</span><span class="sxs-lookup"><span data-stu-id="d5d69-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="d5d69-209">Referenties in een scriptblok Invoke-Command doorgeven</span><span class="sxs-lookup"><span data-stu-id="d5d69-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="d5d69-210">U kunt doorgeven referenties binnen de **ScriptBlock** parameter van een aanroep naar de [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d5d69-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="d5d69-211">Voordelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-211">Pros</span></span>

- <span data-ttu-id="d5d69-212">Is geen speciale configuratie vereist.</span><span class="sxs-lookup"><span data-stu-id="d5d69-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="d5d69-213">Werkt op elke server waarop WMF 2.0 of hoger wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d5d69-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="d5d69-214">Nadelen</span><span class="sxs-lookup"><span data-stu-id="d5d69-214">Cons</span></span>

- <span data-ttu-id="d5d69-215">Vereist een techniek onhandige code.</span><span class="sxs-lookup"><span data-stu-id="d5d69-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="d5d69-216">Als WMF 2.0 wordt uitgevoerd, moet andere syntaxis voor het doorgeven van de argumenten voor een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="d5d69-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="d5d69-217">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d5d69-217">Example</span></span>

<span data-ttu-id="d5d69-218">Het volgende voorbeeld ziet u hoe u kunt doorgeven van referenties in een **Invoke-Command** scriptblok:</span><span class="sxs-lookup"><span data-stu-id="d5d69-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="d5d69-219">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d5d69-219">See also</span></span>

[<span data-ttu-id="d5d69-220">Beveiligingsoverwegingen bij externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5d69-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
