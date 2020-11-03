---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: ce2046a9df5d4d02d718d6408c7a196a753c9914
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253138"
---
# <span data-ttu-id="548dd-103">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="548dd-103">Get-WSManCredSSP</span></span>

## <span data-ttu-id="548dd-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="548dd-104">SYNOPSIS</span></span>
<span data-ttu-id="548dd-105">Hiermee wordt de configuratie van de provider met referentie beveiligings ondersteuning voor de client opgehaald.</span><span class="sxs-lookup"><span data-stu-id="548dd-105">Gets the Credential Security Support Provider-related configuration for the client.</span></span>

## <span data-ttu-id="548dd-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="548dd-106">SYNTAX</span></span>

```
Get-WSManCredSSP [<CommonParameters>]
```

## <span data-ttu-id="548dd-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="548dd-107">DESCRIPTION</span></span>
<span data-ttu-id="548dd-108">Met de cmdlet **Get-WSManCredSSP** wordt de configuratie van de client en de server met referentie beveiligings ondersteuning opgehaald.</span><span class="sxs-lookup"><span data-stu-id="548dd-108">The **Get-WSManCredSSP** cmdlet gets the Credential Security Support Provider-related configuration of the client and the server.</span></span>
<span data-ttu-id="548dd-109">De uitvoer geeft aan of de CredSSP-verificatie (Credential Security Support Provider) is ingeschakeld of uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="548dd-109">The output indicates whether Credential Security Support Provider (CredSSP) authentication is enabled or disabled.</span></span>
<span data-ttu-id="548dd-110">Met deze cmdlet worden ook configuratie-informatie weer gegeven voor het **AllowFreshCredentials** -beleid van CredSSP.</span><span class="sxs-lookup"><span data-stu-id="548dd-110">This cmdlet also displays configuration information for the **AllowFreshCredentials** policy of CredSSP.</span></span>

<span data-ttu-id="548dd-111">Wanneer u CredSSP-verificatie gebruikt, worden de gebruikers referenties door gegeven aan een externe computer die moet worden geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="548dd-111">When you use CredSSP authentication, the user credentials are passed to a remote computer to be authenticated.</span></span>
<span data-ttu-id="548dd-112">Dit type verificatie is ontworpen voor opdrachten die een externe sessie vanuit een andere externe sessie maken.</span><span class="sxs-lookup"><span data-stu-id="548dd-112">This type of authentication is designed for commands that create a remote session from another remote session.</span></span>
<span data-ttu-id="548dd-113">Als u bijvoorbeeld een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u dit type verificatie.</span><span class="sxs-lookup"><span data-stu-id="548dd-113">For example, if you want to run a background job on a remote computer, use this kind of authentication.</span></span>

<span data-ttu-id="548dd-114">De cmdlet voert de volgende acties uit:</span><span class="sxs-lookup"><span data-stu-id="548dd-114">The cmdlet performs the following actions:</span></span>

- <span data-ttu-id="548dd-115">Hiermee wordt de WS-Management CredSSP-instelling op de client ( **\<localhost|computername\> \Client\Auth\CredSSP** ) opgehaald.</span><span class="sxs-lookup"><span data-stu-id="548dd-115">Gets the WS-Management CredSSP setting on the client ( **\<localhost|computername\>\Client\Auth\CredSSP** ).</span></span>
- <span data-ttu-id="548dd-116">Hiermee wordt de Windows CredSSP-beleids instelling **AllowFreshCredentials** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="548dd-116">Gets the Windows CredSSP policy setting **AllowFreshCredentials**.</span></span>
- <span data-ttu-id="548dd-117">Hiermee wordt de WS-Management CredSSP-instelling op de server opgehaald ( **\<localhost|computername\> \Service\Auth\CredSSP** ).</span><span class="sxs-lookup"><span data-stu-id="548dd-117">Gets the WS-Management CredSSP setting on the server ( **\<localhost|computername\>\Service\Auth\CredSSP** ).</span></span>

<span data-ttu-id="548dd-118">Let op: CredSSP-verificatie delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="548dd-118">Caution: CredSSP authentication delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="548dd-119">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="548dd-119">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="548dd-120">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="548dd-120">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

## <span data-ttu-id="548dd-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="548dd-121">EXAMPLES</span></span>

### <span data-ttu-id="548dd-122">Voor beeld 1: CredSSP-configuratie weer geven</span><span class="sxs-lookup"><span data-stu-id="548dd-122">Example 1: Display CredSSP configuration</span></span>

```
PS C:\> Get-WSManCredSSP
```

<span data-ttu-id="548dd-123">Met deze opdracht worden CredSSP-configuratie gegevens weer gegeven voor zowel de client als de server.</span><span class="sxs-lookup"><span data-stu-id="548dd-123">This command displays CredSSP configuration information for both the client and server.</span></span>

<span data-ttu-id="548dd-124">De uitvoer geeft aan dat deze computer of niet is geconfigureerd voor CredSSP.</span><span class="sxs-lookup"><span data-stu-id="548dd-124">The output identifies that this computer is or is not configured for CredSSP.</span></span>

<span data-ttu-id="548dd-125">Als de computer is geconfigureerd voor CredSSP, is dit de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="548dd-125">If the computer is configured for CredSSP, this is the output:</span></span>

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

<span data-ttu-id="548dd-126">Als de computer niet is geconfigureerd voor CredSSP, is dit de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="548dd-126">If the computer is not configured for CredSSP, this is the output:</span></span>

`The machine is not configured to allow delegating fresh credentials.`

## <span data-ttu-id="548dd-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="548dd-127">PARAMETERS</span></span>

### <span data-ttu-id="548dd-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="548dd-128">CommonParameters</span></span>
<span data-ttu-id="548dd-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="548dd-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="548dd-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="548dd-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="548dd-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="548dd-131">INPUTS</span></span>

### <span data-ttu-id="548dd-132">Geen</span><span class="sxs-lookup"><span data-stu-id="548dd-132">None</span></span>
<span data-ttu-id="548dd-133">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="548dd-133">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="548dd-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="548dd-134">OUTPUTS</span></span>

### <span data-ttu-id="548dd-135">Geen</span><span class="sxs-lookup"><span data-stu-id="548dd-135">None</span></span>
<span data-ttu-id="548dd-136">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="548dd-136">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="548dd-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="548dd-137">NOTES</span></span>

* <span data-ttu-id="548dd-138">Als u CredSSP-verificatie wilt uitschakelen, gebruikt u de Disable-WSManCredSSP-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="548dd-138">To disable CredSSP authentication, use the Disable-WSManCredSSP cmdlet.</span></span> <span data-ttu-id="548dd-139">Gebruik de cmdlet Enable-WSManCredSSP om CredSSP-verificatie in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="548dd-139">To enable CredSSP authentication, use the Enable-WSManCredSSP cmdlet.</span></span>

## <span data-ttu-id="548dd-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="548dd-140">RELATED LINKS</span></span>

[<span data-ttu-id="548dd-141">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="548dd-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="548dd-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="548dd-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="548dd-143">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="548dd-143">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="548dd-144">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="548dd-144">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="548dd-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="548dd-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="548dd-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="548dd-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="548dd-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="548dd-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="548dd-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="548dd-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="548dd-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="548dd-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="548dd-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="548dd-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="548dd-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="548dd-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="548dd-152">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="548dd-152">Test-WSMan</span></span>](Test-WSMan.md)
