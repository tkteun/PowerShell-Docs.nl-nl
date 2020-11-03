---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 814be4153687268123114b4036b640eeb0f0da71
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249254"
---
# <span data-ttu-id="05618-103">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="05618-103">Get-WSManCredSSP</span></span>

## <span data-ttu-id="05618-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="05618-104">SYNOPSIS</span></span>
<span data-ttu-id="05618-105">Hiermee wordt de configuratie van de provider met referentie beveiligings ondersteuning voor de client opgehaald.</span><span class="sxs-lookup"><span data-stu-id="05618-105">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="05618-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="05618-106">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="05618-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="05618-107">DESCRIPTION</span></span>
<span data-ttu-id="05618-108">Met de cmdlet **Get-WSManCredSSP** wordt de configuratie van de client en de server met referentie beveiligings ondersteuning opgehaald.</span><span class="sxs-lookup"><span data-stu-id="05618-108">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="05618-109">De uitvoer geeft aan of de CredSSP-verificatie (Credential Security Support Provider) is ingeschakeld of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="05618-109">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="05618-110">Met deze cmdlet worden ook configuratie-informatie weer gegeven voor het **AllowFreshCredentials** -beleid van CredSSP.</span><span class="sxs-lookup"><span data-stu-id="05618-110">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="05618-111">Wanneer u CredSSP-verificatie gebruikt, worden de gebruikers referenties door gegeven aan een externe computer die moet worden geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="05618-111">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="05618-112">Dit type verificatie is ontworpen voor opdrachten die een externe sessie vanuit een andere externe sessie maken.</span><span class="sxs-lookup"><span data-stu-id="05618-112">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="05618-113">Als u bijvoorbeeld een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u dit type verificatie.</span><span class="sxs-lookup"><span data-stu-id="05618-113">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="05618-114">De cmdlet voert de volgende acties uit:</span><span class="sxs-lookup"><span data-stu-id="05618-114">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="05618-115">Hiermee wordt de WS-Management CredSSP-instelling op de client ( **\<localhost|computername\> \Client\Auth\CredSSP** ) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="05618-115">Gets the WS-Management CredSSP setting on the client ( **\<localhost|computername\>\Client\Auth\CredSSP** ).</span></span>
- <span data-ttu-id="05618-116">Hiermee wordt de Windows CredSSP-beleids instelling **AllowFreshCredentials** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="05618-116">Gets the Windows CredSSP policy setting **AllowFreshCredentials**.</span></span>
- <span data-ttu-id="05618-117">Hiermee wordt de WS-Management CredSSP-instelling op de server opgehaald ( **\<localhost|computername\> \Service\Auth\CredSSP** ).</span><span class="sxs-lookup"><span data-stu-id="05618-117">Gets the WS-Management CredSSP setting on the server ( **\<localhost|computername\>\Service\Auth\CredSSP** ).</span></span>

<span data-ttu-id="05618-118">Let op: CredSSP-verificatie delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="05618-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="05618-119">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="05618-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="05618-120">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="05618-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="05618-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="05618-121">EXAMPLES</span></span>

### <span data-ttu-id="05618-122">Voor beeld 1: CredSSP-configuratie weer geven</span><span class="sxs-lookup"><span data-stu-id="05618-122">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="05618-123">Met deze opdracht worden CredSSP-configuratie gegevens weer gegeven voor zowel de client als de server.</span><span class="sxs-lookup"><span data-stu-id="05618-123">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="05618-124">De uitvoer geeft aan dat deze computer of niet is geconfigureerd voor CredSSP.</span><span class="sxs-lookup"><span data-stu-id="05618-124">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="05618-125">Als de computer is geconfigureerd voor CredSSP, is dit de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="05618-125">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="05618-126">Als de computer niet is geconfigureerd voor CredSSP, is dit de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="05618-126">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="05618-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="05618-127">PARAMETERS</span></span>

### <span data-ttu-id="05618-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="05618-128">CommonParameters</span></span>
<span data-ttu-id="05618-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="05618-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="05618-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="05618-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="05618-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="05618-131">INPUTS</span></span>

### <span data-ttu-id="05618-132">Geen</span><span class="sxs-lookup"><span data-stu-id="05618-132">None</span></span>
<span data-ttu-id="05618-133">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="05618-133">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="05618-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="05618-134">OUTPUTS</span></span>

### <span data-ttu-id="05618-135">Geen</span><span class="sxs-lookup"><span data-stu-id="05618-135">None</span></span>
<span data-ttu-id="05618-136">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="05618-136">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="05618-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="05618-137">NOTES</span></span>

* <span data-ttu-id="05618-138">Als u CredSSP-verificatie wilt uitschakelen, gebruikt u de Disable-WSManCredSSP-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05618-138">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="05618-139">Gebruik de cmdlet Enable-WSManCredSSP om CredSSP-verificatie in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="05618-139">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="05618-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="05618-140">RELATED LINKS</span></span>

[<span data-ttu-id="05618-141">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="05618-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="05618-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="05618-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="05618-143">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="05618-143">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="05618-144">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="05618-144">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="05618-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="05618-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="05618-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="05618-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="05618-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="05618-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="05618-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="05618-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="05618-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="05618-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="05618-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="05618-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="05618-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="05618-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="05618-152">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="05618-152">Test-WSMan</span></span>](Test-WSMan.md)
