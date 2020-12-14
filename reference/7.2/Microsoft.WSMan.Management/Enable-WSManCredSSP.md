---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: bacafee683fa47d7be331b4e44d2ab75be5bdb23
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706004"
---
# <span data-ttu-id="871d6-102">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="871d6-102">Enable-WSManCredSSP</span></span>

## <span data-ttu-id="871d6-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="871d6-103">SYNOPSIS</span></span>
<span data-ttu-id="871d6-104">Hiermee schakelt u CredSSP-verificatie (Credential Security Support Provider) in op een computer.</span><span class="sxs-lookup"><span data-stu-id="871d6-104">Enables Credential Security Support Provider (CredSSP) authentication on a computer.</span></span>

## <span data-ttu-id="871d6-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="871d6-105">SYNTAX</span></span>

### <span data-ttu-id="871d6-106">Alles</span><span class="sxs-lookup"><span data-stu-id="871d6-106">All</span></span>

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="871d6-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="871d6-107">DESCRIPTION</span></span>

<span data-ttu-id="871d6-108">`Enable-WSManCredSSP`Met de cmdlet wordt CredSSP-verificatie op een client of op een Server computer ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="871d6-108">The `Enable-WSManCredSSP` cmdlet enables CredSSP authentication on a client or on a server computer.</span></span>
<span data-ttu-id="871d6-109">Wanneer CredSSP-verificatie wordt gebruikt, worden de gebruikers referenties door gegeven aan een externe computer die moet worden geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="871d6-109">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span> <span data-ttu-id="871d6-110">Dit type verificatie is ontworpen voor opdrachten die een externe sessie vanuit een andere externe sessie maken.</span><span class="sxs-lookup"><span data-stu-id="871d6-110">This type of authentication is designed for commands that create a remote session from another remote session.</span></span> <span data-ttu-id="871d6-111">Als u bijvoorbeeld een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u dit type verificatie.</span><span class="sxs-lookup"><span data-stu-id="871d6-111">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="871d6-112">`Enable-WSManCredSSP` kan CredSSP inschakelen op een **client** of een **Server**.</span><span class="sxs-lookup"><span data-stu-id="871d6-112">`Enable-WSManCredSSP` can enable CredSSP on a **Client** or a **Server**.</span></span> <span data-ttu-id="871d6-113">Als u CredSSP wilt inschakelen op een client, geeft u de **client** op in de para meter **Role** .</span><span class="sxs-lookup"><span data-stu-id="871d6-113">To enable CredSSP on a client, specify **Client** in the **Role** parameter.</span></span> <span data-ttu-id="871d6-114">Clients dragen expliciete referenties over aan een server wanneer Server verificatie wordt behaald.</span><span class="sxs-lookup"><span data-stu-id="871d6-114">Clients delegate explicit credentials to a server when server authentication is achieved.</span></span> <span data-ttu-id="871d6-115">Als u CredSSP wilt inschakelen op een server, geeft u de **Server** op in de para meter **Role** .</span><span class="sxs-lookup"><span data-stu-id="871d6-115">To enable CredSSP on a server, specify **Server** in the **Role** parameter.</span></span> <span data-ttu-id="871d6-116">Een server fungeert als gemachtigde voor clients.</span><span class="sxs-lookup"><span data-stu-id="871d6-116">A server acts as a delegate for clients.</span></span> <span data-ttu-id="871d6-117">Zie voor meer informatie **rol** in het gedeelte para meters.</span><span class="sxs-lookup"><span data-stu-id="871d6-117">For more details, see **Role** in the Parameters section.</span></span>

> [!CAUTION]
> <span data-ttu-id="871d6-118">CredSSP-verificatie delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="871d6-118">CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="871d6-119">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="871d6-119">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="871d6-120">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="871d6-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="871d6-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="871d6-121">EXAMPLES</span></span>

### <span data-ttu-id="871d6-122">Voor beeld 1: Client Referenties delegeren</span><span class="sxs-lookup"><span data-stu-id="871d6-122">Example 1: Delegate client credentials</span></span>

<span data-ttu-id="871d6-123">In dit voor beeld kunnen de client referenties worden gedelegeerd naar een computer met behulp van de Fully Qualified Domain Name.</span><span class="sxs-lookup"><span data-stu-id="871d6-123">This example allows the client credentials to be delegated to a computer by using the fully qualified domain name.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="871d6-124">Voor beeld 2: Client Referenties delegeren naar alle computers in een domein</span><span class="sxs-lookup"><span data-stu-id="871d6-124">Example 2: Delegate client credentials to all computers in a domain</span></span>

<span data-ttu-id="871d6-125">In dit voor beeld kunnen de client referenties worden gedelegeerd naar alle computers in het domein **fabrikam.com** .</span><span class="sxs-lookup"><span data-stu-id="871d6-125">This example allows the client credentials to be delegated to all the computers in the **fabrikam.com** domain.</span></span> <span data-ttu-id="871d6-126">Met het `*` Joker teken sterretje () geeft u alle computers op.</span><span class="sxs-lookup"><span data-stu-id="871d6-126">The asterisk (`*`) wildcard specifies all computers.</span></span>

> [!NOTE]
> <span data-ttu-id="871d6-127">Door gebruik te maken van joker tekens met de para meter **DelegateComputer** kan CredSSP op meer computers dan nodig worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="871d6-127">Using wildcards with the **DelegateComputer** parameter can enable CredSSP on more computers than necessary.</span></span>

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### <span data-ttu-id="871d6-128">Voor beeld 3: Client Referenties delegeren naar meerdere computers</span><span class="sxs-lookup"><span data-stu-id="871d6-128">Example 3: Delegate client credentials to multiple computers</span></span>

<span data-ttu-id="871d6-129">In dit voor beeld kunnen de client referenties worden gedelegeerd naar meerdere computers.</span><span class="sxs-lookup"><span data-stu-id="871d6-129">This example allows the client credentials to be delegated to multiple computers.</span></span>

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

<span data-ttu-id="871d6-130">De `$servers` variabele bevat een lijst met server namen.</span><span class="sxs-lookup"><span data-stu-id="871d6-130">The `$servers` variable contains a list of server names.</span></span> <span data-ttu-id="871d6-131">`Enable-WSManCredSSP` maakt gebruik van de para meter **Role** om de **client** functie op te geven.</span><span class="sxs-lookup"><span data-stu-id="871d6-131">`Enable-WSManCredSSP` uses the **Role** parameter to specify the **Client** role.</span></span> <span data-ttu-id="871d6-132">De **DelegateComputer** haalt de computer namen op uit de `$servers` variabele.</span><span class="sxs-lookup"><span data-stu-id="871d6-132">The **DelegateComputer** gets the computer names from the `$servers` variable.</span></span>

### <span data-ttu-id="871d6-133">Voor beeld 4: een computer toestaan als gemachtigde fungeren</span><span class="sxs-lookup"><span data-stu-id="871d6-133">Example 4: Allow a computer to act as a delegate</span></span>

<span data-ttu-id="871d6-134">In dit voor beeld kan een computer fungeren als een gemachtigde voor een andere.</span><span class="sxs-lookup"><span data-stu-id="871d6-134">This example allows a computer to act as a delegate for another.</span></span> <span data-ttu-id="871d6-135">De `Enable-WSManCredSSP` cmdlet, zoals weer gegeven in de eerdere voor beelden, schakelt alleen CredSSP-verificatie in op de client en geeft de externe computers op die namens u kunnen handelen.</span><span class="sxs-lookup"><span data-stu-id="871d6-135">The `Enable-WSManCredSSP` cmdlet, shown in the earlier examples, only enables CredSSP authentication on the client, and specifies the remote computers that can act on its behalf.</span></span> <span data-ttu-id="871d6-136">Om ervoor te zorgen dat de externe computer als gemachtigde voor de client fungeert, moet het CredSSP-item in het **service** knooppunt van WSMan worden ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="871d6-136">In order for the remote computer to act as a delegate for the client, the CredSSP item in the **Service** node of WSMan must be set to true.</span></span> <span data-ttu-id="871d6-137">In dit voor beeld wordt het CredSSP-item in het **service** knooppunt van WSMan ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="871d6-137">This example sets the CredSSP item in the **Service** node of WSMan to true.</span></span>

```powershell
Enable-WSManCredSSP -Role "Server"
```

### <span data-ttu-id="871d6-138">Voor beeld 5: een computer toestaan om te fungeren als een gemachtigde met behulp van Set-Item</span><span class="sxs-lookup"><span data-stu-id="871d6-138">Example 5: Allow a computer to act as a delegate by using Set-Item</span></span>

<span data-ttu-id="871d6-139">In dit voor beeld kan een computer fungeren als een gemachtigde voor een andere computer.</span><span class="sxs-lookup"><span data-stu-id="871d6-139">This example allows a computer to act as a delegate for another computer.</span></span> <span data-ttu-id="871d6-140">De `Enable-WSManCredSSP` opdrachten, die worden weer gegeven in de eerdere voor beelden, maken CredSSP-verificatie alleen op de client computer en geven de externe computers op die namens de client computer kunnen optreden.</span><span class="sxs-lookup"><span data-stu-id="871d6-140">The `Enable-WSManCredSSP` commands, shown in the earlier examples, enable CredSSP authentication only on the client computer, and they specify the remote computers that can act on behalf of the client computer.</span></span> <span data-ttu-id="871d6-141">Als u wilt dat de externe computer als gemachtigde fungeert voor de client computer, moet het CredSSP-item in de service Directory van de WSMan-provider worden ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="871d6-141">For the remote computer to act as a delegate for the client computer, the CredSSP item in the Service directory of the WSMan provider must be set to true.</span></span>

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

<span data-ttu-id="871d6-142">`Connect-WSMan` Hiermee maakt u een verbinding met de externe computer, server02.</span><span class="sxs-lookup"><span data-stu-id="871d6-142">`Connect-WSMan` creates a connection to the remote computer, server02.</span></span> <span data-ttu-id="871d6-143">`Set-Item` maakt gebruik van de para meter **Path** om de locatie van de **WSMan** -provider op te geven.</span><span class="sxs-lookup"><span data-stu-id="871d6-143">`Set-Item` uses the **Path** parameter to specify the **WSMan** provider's location.</span></span> <span data-ttu-id="871d6-144">De **waarde** para meter stelt de **service** -instelling in op waar.</span><span class="sxs-lookup"><span data-stu-id="871d6-144">The **Value** parameter sets the **Service** setting to true.</span></span>

## <span data-ttu-id="871d6-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="871d6-145">PARAMETERS</span></span>

### <span data-ttu-id="871d6-146">-DelegateComputer</span><span class="sxs-lookup"><span data-stu-id="871d6-146">-DelegateComputer</span></span>

<span data-ttu-id="871d6-147">Hiermee geeft u de servers aan waarnaar de client referenties worden gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="871d6-147">Specifies servers to which client credentials are delegated.</span></span> <span data-ttu-id="871d6-148">De best practice is het gebruik van volledig gekwalificeerde domein namen.</span><span class="sxs-lookup"><span data-stu-id="871d6-148">The best practice is to use fully qualified domain names.</span></span>

<span data-ttu-id="871d6-149">Joker tekens worden geaccepteerd, maar kunnen CredSSP inschakelen op meer computers dan nodig zijn.</span><span class="sxs-lookup"><span data-stu-id="871d6-149">Wildcards are accepted, but can enable CredSSP on more computers than necessary.</span></span>

<span data-ttu-id="871d6-150">Als de  para meter Role **client** is, moet u deze para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="871d6-150">If the **Role** parameter is **Client**, you must specify this parameter.</span></span> <span data-ttu-id="871d6-151">Als  de rol **Server** is, geeft u deze para meter niet op.</span><span class="sxs-lookup"><span data-stu-id="871d6-151">If **Role** is **Server**, don't specify this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="871d6-152">-Force</span><span class="sxs-lookup"><span data-stu-id="871d6-152">-Force</span></span>

<span data-ttu-id="871d6-153">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="871d6-153">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="871d6-154">-Rol</span><span class="sxs-lookup"><span data-stu-id="871d6-154">-Role</span></span>

<span data-ttu-id="871d6-155">Hiermee geeft u op of CredSSP moet worden ingeschakeld als een client of als server.</span><span class="sxs-lookup"><span data-stu-id="871d6-155">Specifies whether to enable CredSSP as a client or as a server.</span></span> <span data-ttu-id="871d6-156">De acceptabele waarden voor deze para meter zijn: **client** en **Server**.</span><span class="sxs-lookup"><span data-stu-id="871d6-156">The acceptable values for this parameter are: **Client** and **Server**.</span></span>

<span data-ttu-id="871d6-157">Als u **client** opgeeft, worden de volgende acties uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="871d6-157">If you specify **Client**, the following actions are performed.</span></span> <span data-ttu-id="871d6-158">Met deze instellingen kan de client expliciete referenties delegeren aan een server wanneer Server verificatie wordt bereikt.</span><span class="sxs-lookup"><span data-stu-id="871d6-158">These settings allow the client to delegate explicit credentials to a server when server authentication is achieved.</span></span>

- <span data-ttu-id="871d6-159">CredSSP wordt ingeschakeld op de client.</span><span class="sxs-lookup"><span data-stu-id="871d6-159">Enables CredSSP on the client.</span></span>
- <span data-ttu-id="871d6-160">Hiermee stelt u de WS-Management-instelling `\<localhost|computername\>\Client\Auth\CredSSP` in op waar.</span><span class="sxs-lookup"><span data-stu-id="871d6-160">Sets the WS-Management setting `\<localhost|computername\>\Client\Auth\CredSSP` to true.</span></span>
- <span data-ttu-id="871d6-161">Hiermee stelt u de **AllowFreshCredentials** van het Windows-CredSSP-beleid in op **WSMan/delegeren** op de client.</span><span class="sxs-lookup"><span data-stu-id="871d6-161">Sets the Windows CredSSP policy **AllowFreshCredentials** to **WSMan/Delegate** on the client.</span></span>

<span data-ttu-id="871d6-162">Als u **Server** opgeeft, worden de volgende acties uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="871d6-162">If you specify **Server**, the following actions are performed.</span></span> <span data-ttu-id="871d6-163">Met deze beleids instelling kan de server fungeren als gemachtigde voor clients.</span><span class="sxs-lookup"><span data-stu-id="871d6-163">This policy setting allows the server to act as a delegate for clients.</span></span>

- <span data-ttu-id="871d6-164">Hiermee schakelt u CredSSP op de server in.</span><span class="sxs-lookup"><span data-stu-id="871d6-164">Enables CredSSP on the server.</span></span>
- <span data-ttu-id="871d6-165">Hiermee stelt u de WS-Management-instelling `\<localhost|computername\>\Service\Auth\CredSSP` in op waar.</span><span class="sxs-lookup"><span data-stu-id="871d6-165">Sets the WS-Management setting `\<localhost|computername\>\Service\Auth\CredSSP` to true.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="871d6-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="871d6-166">CommonParameters</span></span>

<span data-ttu-id="871d6-167">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="871d6-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="871d6-168">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="871d6-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="871d6-169">INVOER</span><span class="sxs-lookup"><span data-stu-id="871d6-169">INPUTS</span></span>

### <span data-ttu-id="871d6-170">Geen</span><span class="sxs-lookup"><span data-stu-id="871d6-170">None</span></span>

<span data-ttu-id="871d6-171">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="871d6-171">This cmdlet doesn't accept any input.</span></span>

## <span data-ttu-id="871d6-172">UITVOER</span><span class="sxs-lookup"><span data-stu-id="871d6-172">OUTPUTS</span></span>

### <span data-ttu-id="871d6-173">System.Xml.Xml-element</span><span class="sxs-lookup"><span data-stu-id="871d6-173">System.Xml.XmlElement</span></span>

<span data-ttu-id="871d6-174">Als CredSSP-verificatie is ingeschakeld, wordt met deze cmdlet een **XMLElement** -object gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="871d6-174">If CredSSP authentication is successfully enabled, this cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="871d6-175">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="871d6-175">NOTES</span></span>

<span data-ttu-id="871d6-176">Als u CredSSP-verificatie wilt uitschakelen, gebruikt u de `Disable-WSManCredSSP` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="871d6-176">To disable CredSSP authentication, use the `Disable-WSManCredSSP` cmdlet.</span></span>

## <span data-ttu-id="871d6-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="871d6-177">RELATED LINKS</span></span>

[<span data-ttu-id="871d6-178">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="871d6-178">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="871d6-179">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="871d6-179">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="871d6-180">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="871d6-180">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="871d6-181">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="871d6-181">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="871d6-182">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="871d6-182">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="871d6-183">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="871d6-183">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="871d6-184">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="871d6-184">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="871d6-185">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="871d6-185">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="871d6-186">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="871d6-186">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="871d6-187">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="871d6-187">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="871d6-188">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="871d6-188">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="871d6-189">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="871d6-189">Test-WSMan</span></span>](Test-WSMan.md)

