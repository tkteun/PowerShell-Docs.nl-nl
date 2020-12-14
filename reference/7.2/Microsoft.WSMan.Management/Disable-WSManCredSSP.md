---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 3260c88d57e98c0072af8621600a02901c561acb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706006"
---
# <span data-ttu-id="3e4ee-102">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3e4ee-102">Disable-WSManCredSSP</span></span>

## <span data-ttu-id="3e4ee-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3e4ee-103">SYNOPSIS</span></span>
<span data-ttu-id="3e4ee-104">Hiermee schakelt u CredSSP-verificatie op een computer uit.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-104">Disables CredSSP authentication on a computer.</span></span>

## <span data-ttu-id="3e4ee-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3e4ee-105">SYNTAX</span></span>

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="3e4ee-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3e4ee-106">DESCRIPTION</span></span>
<span data-ttu-id="3e4ee-107">Met de cmdlet **Disable-WSManCredSSP** wordt CredSSP-verificatie (Credential Security Support Provider) uitgeschakeld op een client of op een Server computer.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-107">The **Disable-WSManCredSSP** cmdlet disables Credential Security Support Provider (CredSSP) authentication on a client or on a server computer.</span></span>
<span data-ttu-id="3e4ee-108">Wanneer CredSSP-verificatie wordt gebruikt, worden de gebruikers referenties door gegeven aan een externe computer die moet worden geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-108">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span>

<span data-ttu-id="3e4ee-109">Gebruik deze cmdlet om CredSSP op de client uit te scha kelen door de client op te geven in de para meter *Role* .</span><span class="sxs-lookup"><span data-stu-id="3e4ee-109">Use this cmdlet to disable CredSSP on the client by specifying Client in the *Role* parameter.</span></span>
<span data-ttu-id="3e4ee-110">Met deze cmdlet worden de volgende acties uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="3e4ee-110">This cmdlet performs the following actions:</span></span>

- <span data-ttu-id="3e4ee-111">Hiermee schakelt u CredSSP op de client uit.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-111">Disables CredSSP on the client.</span></span> <span data-ttu-id="3e4ee-112">Met deze cmdlet wordt de WS-Management instelling **\<localhost|computername\> \Client\Auth\CredSSP** ingesteld op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-112">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="3e4ee-113">Hiermee verwijdert u elke WSMan/\*-instelling uit de **AllowFreshCredentials** van het Windows-CredSSP-beleid op de client.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-113">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="3e4ee-114">Gebruik deze cmdlet om CredSSP op de server uit te scha kelen door de server *functie* op te geven.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-114">Use this cmdlet to disable CredSSP on the server by specifying Server in *Role*.</span></span>
<span data-ttu-id="3e4ee-115">Met deze cmdlet wordt de volgende actie uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="3e4ee-115">This cmdlet performs the following action:</span></span>

- <span data-ttu-id="3e4ee-116">Hiermee schakelt u CredSSP op de server uit.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-116">Disables CredSSP on the server.</span></span> <span data-ttu-id="3e4ee-117">Met deze cmdlet wordt de WS-Management instelling **\<localhost|computername\> \Service\Auth\CredSSP** ingesteld op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-117">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

<span data-ttu-id="3e4ee-118">Let op: CredSSP-verificatie delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="3e4ee-119">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="3e4ee-120">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="3e4ee-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3e4ee-121">EXAMPLES</span></span>

### <span data-ttu-id="3e4ee-122">Voor beeld 1: CredSSP uitschakelen op een client</span><span class="sxs-lookup"><span data-stu-id="3e4ee-122">Example 1: Disable CredSSP on a client</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Client
```

<span data-ttu-id="3e4ee-123">Met deze opdracht wordt CredSSP op de client uitgeschakeld, waardoor overdracht naar servers wordt voor komen.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-123">This command disables CredSSP on the client, which prevents delegation to servers.</span></span>

### <span data-ttu-id="3e4ee-124">Voor beeld 2: CredSSP uitschakelen op een server</span><span class="sxs-lookup"><span data-stu-id="3e4ee-124">Example 2: Disable CredSSP on a server</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Server
```

<span data-ttu-id="3e4ee-125">Met deze opdracht wordt CredSSP op de server uitgeschakeld, waardoor delegering van clients wordt voor komen.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-125">This command disables CredSSP on the server, which prevents delegation from clients.</span></span>

## <span data-ttu-id="3e4ee-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e4ee-126">PARAMETERS</span></span>

### <span data-ttu-id="3e4ee-127">-Rol</span><span class="sxs-lookup"><span data-stu-id="3e4ee-127">-Role</span></span>
<span data-ttu-id="3e4ee-128">Hiermee wordt aangegeven of CredSSP moet worden uitgeschakeld als een client of als server.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-128">Specifies whether to disable CredSSP as a client or as a server.</span></span>
<span data-ttu-id="3e4ee-129">De acceptabele waarden voor deze para meter zijn: client en server.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-129">The acceptable values for this parameter are: Client and Server.</span></span>

<span data-ttu-id="3e4ee-130">Als u de client opgeeft, voert deze cmdlet de volgende acties uit:</span><span class="sxs-lookup"><span data-stu-id="3e4ee-130">If you specify Client, this cmdlet performs the following actions:</span></span>

- <span data-ttu-id="3e4ee-131">Hiermee schakelt u CredSSP op de client uit.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-131">Disables CredSSP on the client.</span></span> <span data-ttu-id="3e4ee-132">Met deze cmdlet wordt WS-Management instelling **\<localhost|computername\> \Client\Auth\CredSSP** ingesteld op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-132">This cmdlet sets WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="3e4ee-133">Hiermee verwijdert u elke WSMan/\*-instelling uit de **AllowFreshCredentials** van het Windows-CredSSP-beleid op de client.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-133">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="3e4ee-134">Als u server opgeeft, voert deze cmdlet de volgende actie uit:</span><span class="sxs-lookup"><span data-stu-id="3e4ee-134">If you specify Server, this cmdlet performs the following action:</span></span>

- <span data-ttu-id="3e4ee-135">Hiermee schakelt u CredSSP op de server uit.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-135">Disables CredSSP on the server.</span></span> <span data-ttu-id="3e4ee-136">Met deze cmdlet wordt de WS-Management instelling **\<localhost|computername\> \Service\Auth\CredSSP** ingesteld op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-136">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

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

### <span data-ttu-id="3e4ee-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e4ee-137">CommonParameters</span></span>
<span data-ttu-id="3e4ee-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e4ee-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e4ee-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="3e4ee-140">INPUTS</span></span>

### <span data-ttu-id="3e4ee-141">Geen</span><span class="sxs-lookup"><span data-stu-id="3e4ee-141">None</span></span>
<span data-ttu-id="3e4ee-142">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-142">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="3e4ee-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3e4ee-143">OUTPUTS</span></span>

### <span data-ttu-id="3e4ee-144">Geen</span><span class="sxs-lookup"><span data-stu-id="3e4ee-144">None</span></span>
<span data-ttu-id="3e4ee-145">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3e4ee-146">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3e4ee-146">NOTES</span></span>

* <span data-ttu-id="3e4ee-147">Gebruik de cmdlet Enable-WSManCredSSP om CredSSP-verificatie in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="3e4ee-147">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

*

## <span data-ttu-id="3e4ee-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3e4ee-148">RELATED LINKS</span></span>

[<span data-ttu-id="3e4ee-149">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="3e4ee-149">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="3e4ee-150">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="3e4ee-150">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="3e4ee-151">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3e4ee-151">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="3e4ee-152">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3e4ee-152">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="3e4ee-153">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e4ee-153">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="3e4ee-154">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="3e4ee-154">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="3e4ee-155">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e4ee-155">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="3e4ee-156">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="3e4ee-156">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="3e4ee-157">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e4ee-157">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="3e4ee-158">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e4ee-158">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="3e4ee-159">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="3e4ee-159">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="3e4ee-160">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="3e4ee-160">Test-WSMan</span></span>](Test-WSMan.md)

