---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 9830d1feb31e9cca735a7ac8d2ed9d2ec50380b5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704727"
---
# <span data-ttu-id="ef179-102">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ef179-102">Get-WSManCredSSP</span></span>

## <span data-ttu-id="ef179-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ef179-103">SYNOPSIS</span></span>
<span data-ttu-id="ef179-104">Hiermee wordt de configuratie van de provider met referentie beveiligings ondersteuning voor de client opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ef179-104">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="ef179-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ef179-105">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="ef179-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ef179-106">DESCRIPTION</span></span>
<span data-ttu-id="ef179-107">Met de cmdlet **Get-WSManCredSSP** wordt de configuratie van de client en de server met referentie beveiligings ondersteuning opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ef179-107">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="ef179-108">De uitvoer geeft aan of de CredSSP-verificatie (Credential Security Support Provider) is ingeschakeld of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="ef179-108">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="ef179-109">Met deze cmdlet worden ook configuratie-informatie weer gegeven voor het **AllowFreshCredentials** -beleid van CredSSP.</span><span class="sxs-lookup"><span data-stu-id="ef179-109">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="ef179-110">Wanneer u CredSSP-verificatie gebruikt, worden de gebruikers referenties door gegeven aan een externe computer die moet worden geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="ef179-110">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="ef179-111">Dit type verificatie is ontworpen voor opdrachten die een externe sessie vanuit een andere externe sessie maken.</span><span class="sxs-lookup"><span data-stu-id="ef179-111">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="ef179-112">Als u bijvoorbeeld een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u dit type verificatie.</span><span class="sxs-lookup"><span data-stu-id="ef179-112">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="ef179-113">De cmdlet voert de volgende acties uit:</span><span class="sxs-lookup"><span data-stu-id="ef179-113">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="ef179-114">Hiermee wordt de WS-Management CredSSP-instelling op de client (**\<localhost|computername\> \Client\Auth\CredSSP**) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ef179-114">Gets the WS-Management CredSSP setting on the client (**\<localhost|computername\>\Client\Auth\CredSSP**).</span></span>
- <span data-ttu-id="ef179-115">Hiermee wordt de Windows CredSSP-beleids instelling **AllowFreshCredentials** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ef179-115">Gets the Windows CredSSP policy setting **AllowFreshCredentials**.</span></span>
- <span data-ttu-id="ef179-116">Hiermee wordt de WS-Management CredSSP-instelling op de server opgehaald (**\<localhost|computername\> \Service\Auth\CredSSP**).</span><span class="sxs-lookup"><span data-stu-id="ef179-116">Gets the WS-Management CredSSP setting on the server (**\<localhost|computername\>\Service\Auth\CredSSP**).</span></span>

<span data-ttu-id="ef179-117">Let op: CredSSP-verificatie delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="ef179-117">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="ef179-118">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="ef179-118">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="ef179-119">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef179-119">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="ef179-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ef179-120">EXAMPLES</span></span>

### <span data-ttu-id="ef179-121">Voor beeld 1: CredSSP-configuratie weer geven</span><span class="sxs-lookup"><span data-stu-id="ef179-121">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="ef179-122">Met deze opdracht worden CredSSP-configuratie gegevens weer gegeven voor zowel de client als de server.</span><span class="sxs-lookup"><span data-stu-id="ef179-122">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="ef179-123">De uitvoer geeft aan dat deze computer of niet is geconfigureerd voor CredSSP.</span><span class="sxs-lookup"><span data-stu-id="ef179-123">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="ef179-124">Als de computer is geconfigureerd voor CredSSP, is dit de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="ef179-124">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="ef179-125">Als de computer niet is geconfigureerd voor CredSSP, is dit de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="ef179-125">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="ef179-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ef179-126">PARAMETERS</span></span>

### <span data-ttu-id="ef179-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef179-127">CommonParameters</span></span>
<span data-ttu-id="ef179-128">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef179-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef179-129">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ef179-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef179-130">INVOER</span><span class="sxs-lookup"><span data-stu-id="ef179-130">INPUTS</span></span>

### <span data-ttu-id="ef179-131">Geen</span><span class="sxs-lookup"><span data-stu-id="ef179-131">None</span></span>
<span data-ttu-id="ef179-132">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="ef179-132">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="ef179-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ef179-133">OUTPUTS</span></span>

### <span data-ttu-id="ef179-134">Geen</span><span class="sxs-lookup"><span data-stu-id="ef179-134">None</span></span>
<span data-ttu-id="ef179-135">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ef179-135">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ef179-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ef179-136">NOTES</span></span>

* <span data-ttu-id="ef179-137">Als u CredSSP-verificatie wilt uitschakelen, gebruikt u de Disable-WSManCredSSP-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef179-137">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="ef179-138">Gebruik de cmdlet Enable-WSManCredSSP om CredSSP-verificatie in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="ef179-138">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="ef179-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ef179-139">RELATED LINKS</span></span>

[<span data-ttu-id="ef179-140">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="ef179-140">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="ef179-141">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ef179-141">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="ef179-142">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="ef179-142">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="ef179-143">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="ef179-143">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="ef179-144">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ef179-144">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="ef179-145">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="ef179-145">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="ef179-146">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ef179-146">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="ef179-147">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="ef179-147">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="ef179-148">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ef179-148">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="ef179-149">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="ef179-149">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="ef179-150">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="ef179-150">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="ef179-151">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="ef179-151">Test-WSMan</span></span>](Test-WSMan.md)

