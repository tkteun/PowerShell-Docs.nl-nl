---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 3202e21b5f002610557f827f3a5f65659dec6823
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249669"
---
# <span data-ttu-id="c615a-103">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="c615a-103">Disable-WSManCredSSP</span></span>

## <span data-ttu-id="c615a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c615a-104">SYNOPSIS</span></span>
<span data-ttu-id="c615a-105">Hiermee schakelt u CredSSP-verificatie op een computer uit.</span><span class="sxs-lookup"><span data-stu-id="c615a-105">Disables CredSSP authentication on a computer.</span></span>

## <span data-ttu-id="c615a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c615a-106">SYNTAX</span></span>

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## <span data-ttu-id="c615a-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c615a-107">DESCRIPTION</span></span>
<span data-ttu-id="c615a-108">Met de cmdlet **Disable-WSManCredSSP** wordt CredSSP-verificatie (Credential Security Support Provider) uitgeschakeld op een client of op een Server computer.</span><span class="sxs-lookup"><span data-stu-id="c615a-108">The **Disable-WSManCredSSP** cmdlet disables Credential Security Support Provider (CredSSP) authentication on a client or on a server computer.</span></span>
<span data-ttu-id="c615a-109">Wanneer CredSSP-verificatie wordt gebruikt, worden de gebruikers referenties door gegeven aan een externe computer die moet worden geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="c615a-109">When CredSSP authentication is used, the user credentials are passed to a remote computer to be authenticated.</span></span>

<span data-ttu-id="c615a-110">Gebruik deze cmdlet om CredSSP op de client uit te scha kelen door de client op te geven in de para meter *Role* .</span><span class="sxs-lookup"><span data-stu-id="c615a-110">Use this cmdlet to disable CredSSP on the client by specifying Client in the *Role* parameter.</span></span>
<span data-ttu-id="c615a-111">Met deze cmdlet worden de volgende acties uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="c615a-111">This cmdlet performs the following actions:</span></span>

- <span data-ttu-id="c615a-112">Hiermee schakelt u CredSSP op de client uit.</span><span class="sxs-lookup"><span data-stu-id="c615a-112">Disables CredSSP on the client.</span></span> <span data-ttu-id="c615a-113">Met deze cmdlet wordt de WS-Management instelling **\<localhost|computername\> \Client\Auth\CredSSP** ingesteld op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="c615a-113">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="c615a-114">Hiermee verwijdert u elke WSMan/\*-instelling uit de **AllowFreshCredentials** van het Windows-CredSSP-beleid op de client.</span><span class="sxs-lookup"><span data-stu-id="c615a-114">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="c615a-115">Gebruik deze cmdlet om CredSSP op de server uit te scha kelen door de server *functie* op te geven.</span><span class="sxs-lookup"><span data-stu-id="c615a-115">Use this cmdlet to disable CredSSP on the server by specifying Server in *Role*.</span></span>
<span data-ttu-id="c615a-116">Met deze cmdlet wordt de volgende actie uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="c615a-116">This cmdlet performs the following action:</span></span>

- <span data-ttu-id="c615a-117">Hiermee schakelt u CredSSP op de server uit.</span><span class="sxs-lookup"><span data-stu-id="c615a-117">Disables CredSSP on the server.</span></span> <span data-ttu-id="c615a-118">Met deze cmdlet wordt de WS-Management instelling **\<localhost|computername\> \Service\Auth\CredSSP** ingesteld op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="c615a-118">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

<span data-ttu-id="c615a-119">Let op: CredSSP-verificatie delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="c615a-119">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="c615a-120">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="c615a-120">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="c615a-121">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="c615a-121">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="c615a-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c615a-122">EXAMPLES</span></span>

### <span data-ttu-id="c615a-123">Voor beeld 1: CredSSP uitschakelen op een client</span><span class="sxs-lookup"><span data-stu-id="c615a-123">Example 1: Disable CredSSP on a client</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Client
```

<span data-ttu-id="c615a-124">Met deze opdracht wordt CredSSP op de client uitgeschakeld, waardoor overdracht naar servers wordt voor komen.</span><span class="sxs-lookup"><span data-stu-id="c615a-124">This command disables CredSSP on the client, which prevents delegation to servers.</span></span>

### <span data-ttu-id="c615a-125">Voor beeld 2: CredSSP uitschakelen op een server</span><span class="sxs-lookup"><span data-stu-id="c615a-125">Example 2: Disable CredSSP on a server</span></span>

```
PS C:\> Disable-WSManCredSSP -Role Server
```

<span data-ttu-id="c615a-126">Met deze opdracht wordt CredSSP op de server uitgeschakeld, waardoor delegering van clients wordt voor komen.</span><span class="sxs-lookup"><span data-stu-id="c615a-126">This command disables CredSSP on the server, which prevents delegation from clients.</span></span>

## <span data-ttu-id="c615a-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c615a-127">PARAMETERS</span></span>

### <span data-ttu-id="c615a-128">-Rol</span><span class="sxs-lookup"><span data-stu-id="c615a-128">-Role</span></span>
<span data-ttu-id="c615a-129">Hiermee wordt aangegeven of CredSSP moet worden uitgeschakeld als een client of als server.</span><span class="sxs-lookup"><span data-stu-id="c615a-129">Specifies whether to disable CredSSP as a client or as a server.</span></span>
<span data-ttu-id="c615a-130">De acceptabele waarden voor deze para meter zijn: client en server.</span><span class="sxs-lookup"><span data-stu-id="c615a-130">The acceptable values for this parameter are: Client and Server.</span></span>

<span data-ttu-id="c615a-131">Als u de client opgeeft, voert deze cmdlet de volgende acties uit:</span><span class="sxs-lookup"><span data-stu-id="c615a-131">If you specify Client, this cmdlet performs the following actions:</span></span>

- <span data-ttu-id="c615a-132">Hiermee schakelt u CredSSP op de client uit.</span><span class="sxs-lookup"><span data-stu-id="c615a-132">Disables CredSSP on the client.</span></span> <span data-ttu-id="c615a-133">Met deze cmdlet wordt WS-Management instelling **\<localhost|computername\> \Client\Auth\CredSSP** ingesteld op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="c615a-133">This cmdlet sets WS-Management setting **\<localhost|computername\>\Client\Auth\CredSSP** to false.</span></span>
- <span data-ttu-id="c615a-134">Hiermee verwijdert u elke WSMan/\*-instelling uit de **AllowFreshCredentials** van het Windows-CredSSP-beleid op de client.</span><span class="sxs-lookup"><span data-stu-id="c615a-134">Removes any WSMan/\* setting from the Windows CredSSP policy **AllowFreshCredentials** on the client.</span></span>

<span data-ttu-id="c615a-135">Als u server opgeeft, voert deze cmdlet de volgende actie uit:</span><span class="sxs-lookup"><span data-stu-id="c615a-135">If you specify Server, this cmdlet performs the following action:</span></span>

- <span data-ttu-id="c615a-136">Hiermee schakelt u CredSSP op de server uit.</span><span class="sxs-lookup"><span data-stu-id="c615a-136">Disables CredSSP on the server.</span></span> <span data-ttu-id="c615a-137">Met deze cmdlet wordt de WS-Management instelling **\<localhost|computername\> \Service\Auth\CredSSP** ingesteld op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="c615a-137">This cmdlet sets the WS-Management setting **\<localhost|computername\>\Service\Auth\CredSSP** to false.</span></span>

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

### <span data-ttu-id="c615a-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c615a-138">CommonParameters</span></span>
<span data-ttu-id="c615a-139">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c615a-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c615a-140">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c615a-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c615a-141">INVOER</span><span class="sxs-lookup"><span data-stu-id="c615a-141">INPUTS</span></span>

### <span data-ttu-id="c615a-142">Geen</span><span class="sxs-lookup"><span data-stu-id="c615a-142">None</span></span>
<span data-ttu-id="c615a-143">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="c615a-143">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="c615a-144">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c615a-144">OUTPUTS</span></span>

### <span data-ttu-id="c615a-145">Geen</span><span class="sxs-lookup"><span data-stu-id="c615a-145">None</span></span>
<span data-ttu-id="c615a-146">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c615a-146">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c615a-147">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c615a-147">NOTES</span></span>

* <span data-ttu-id="c615a-148">Gebruik de cmdlet Enable-WSManCredSSP om CredSSP-verificatie in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="c615a-148">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

*

## <span data-ttu-id="c615a-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c615a-149">RELATED LINKS</span></span>

[<span data-ttu-id="c615a-150">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="c615a-150">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="c615a-151">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="c615a-151">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="c615a-152">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="c615a-152">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="c615a-153">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="c615a-153">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="c615a-154">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c615a-154">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="c615a-155">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="c615a-155">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="c615a-156">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c615a-156">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="c615a-157">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="c615a-157">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="c615a-158">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c615a-158">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="c615a-159">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c615a-159">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="c615a-160">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="c615a-160">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="c615a-161">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="c615a-161">Test-WSMan</span></span>](Test-WSMan.md)
