---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 948b870948f51bd51424beaeca45ed2b2d195891
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706005"
---
# <span data-ttu-id="bd211-102">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="bd211-102">Disconnect-WSMan</span></span>

## <span data-ttu-id="bd211-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bd211-103">SYNOPSIS</span></span>
<span data-ttu-id="bd211-104">Verbreekt de verbinding tussen de client en de WinRM-service op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="bd211-104">Disconnects the client from the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="bd211-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bd211-105">SYNTAX</span></span>

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="bd211-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bd211-106">DESCRIPTION</span></span>
<span data-ttu-id="bd211-107">Met de cmdlet **Disconnect-WSMan** wordt de verbinding tussen de client en de WinRM-service op een externe computer verbroken.</span><span class="sxs-lookup"><span data-stu-id="bd211-107">The **Disconnect-WSMan** cmdlet disconnects the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="bd211-108">Als u de WS-Management-sessie in een variabele hebt opgeslagen, blijft het sessie object in de variabele, maar wordt de status van de WS-Management sessie gesloten.</span><span class="sxs-lookup"><span data-stu-id="bd211-108">If you saved the WS-Management session in a variable, the session object remains in the variable, but the state of the WS-Management session is Closed.</span></span>
<span data-ttu-id="bd211-109">U kunt deze cmdlet in de context van de WSMan-provider gebruiken om de client te verbreken van de WinRM-service op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="bd211-109">You can use this cmdlet within the context of the WSMan provider to disconnect the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="bd211-110">U kunt deze cmdlet echter ook gebruiken om de verbinding met de WinRM-service op externe computers te verbreken voordat u overschakelt naar de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="bd211-110">However, you can also use this cmdlet to disconnect from the WinRM service on remote computers before you change to the WSMan provider.</span></span>

<span data-ttu-id="bd211-111">Zie Connect-WSMan voor meer informatie over het maken van een verbinding met de WinRM-service op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="bd211-111">For more information about how to connect to the WinRM service on a remote computer, see Connect-WSMan.</span></span>

## <span data-ttu-id="bd211-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bd211-112">EXAMPLES</span></span>

### <span data-ttu-id="bd211-113">Voor beeld 1: een verbinding met een externe computer verwijderen</span><span class="sxs-lookup"><span data-stu-id="bd211-113">Example 1: Delete a connection to a remote computer</span></span>

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

<span data-ttu-id="bd211-114">Met deze opdracht wordt de verbinding met de externe computer met de naam Server01 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="bd211-114">This command deletes the connection to the remote computer named server01.</span></span>

<span data-ttu-id="bd211-115">Deze cmdlet wordt doorgaans gebruikt in de context van de WSMan-provider om de verbinding met een externe computer te verbreken, in dit geval de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="bd211-115">This cmdlet is generally used within the context of the WSMan provider to disconnect from a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="bd211-116">U kunt echter ook **Disconnect-WSMan** gebruiken om verbindingen met externe computers te verwijderen voordat u overschakelt naar de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="bd211-116">However, you can also use **Disconnect-WSMan** to remove connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="bd211-117">Deze verbindingen worden niet weer gegeven in de lijst computer naam.</span><span class="sxs-lookup"><span data-stu-id="bd211-117">Those connections do not appear in the ComputerName list.</span></span>

## <span data-ttu-id="bd211-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd211-118">PARAMETERS</span></span>

### <span data-ttu-id="bd211-119">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bd211-119">-ComputerName</span></span>
<span data-ttu-id="bd211-120">Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bd211-120">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="bd211-121">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="bd211-121">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="bd211-122">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="bd211-122">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="bd211-123">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="bd211-123">The local computer is the default.</span></span>
<span data-ttu-id="bd211-124">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bd211-124">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="bd211-125">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bd211-125">You can pipe a value for this parameter to the cmdlet.</span></span>

<span data-ttu-id="bd211-126">U kunt de verbinding met de lokale host niet verbreken.</span><span class="sxs-lookup"><span data-stu-id="bd211-126">You cannot disconnect from the local host.</span></span>
<span data-ttu-id="bd211-127">Dat wil zeggen dat u de standaard verbinding met de lokale computer niet kunt verbreken.</span><span class="sxs-lookup"><span data-stu-id="bd211-127">That is, you cannot disconnect the default connection to the local computer.</span></span>
<span data-ttu-id="bd211-128">Als u echter een afzonderlijke verbinding maakt met de lokale computer, bijvoorbeeld met behulp van de computer naam.</span><span class="sxs-lookup"><span data-stu-id="bd211-128">However, if you create a separate connection to the local computer, for example, by using the computer name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd211-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd211-129">CommonParameters</span></span>
<span data-ttu-id="bd211-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd211-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd211-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd211-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd211-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="bd211-132">INPUTS</span></span>

### <span data-ttu-id="bd211-133">Geen</span><span class="sxs-lookup"><span data-stu-id="bd211-133">None</span></span>
<span data-ttu-id="bd211-134">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="bd211-134">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="bd211-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bd211-135">OUTPUTS</span></span>

### <span data-ttu-id="bd211-136">Geen</span><span class="sxs-lookup"><span data-stu-id="bd211-136">None</span></span>
<span data-ttu-id="bd211-137">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="bd211-137">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bd211-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="bd211-138">NOTES</span></span>

## <span data-ttu-id="bd211-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="bd211-139">RELATED LINKS</span></span>

[<span data-ttu-id="bd211-140">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="bd211-140">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="bd211-141">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="bd211-141">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="bd211-142">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="bd211-142">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="bd211-143">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="bd211-143">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="bd211-144">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bd211-144">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="bd211-145">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="bd211-145">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="bd211-146">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bd211-146">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="bd211-147">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="bd211-147">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="bd211-148">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bd211-148">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="bd211-149">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="bd211-149">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="bd211-150">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="bd211-150">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="bd211-151">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="bd211-151">Test-WSMan</span></span>](Test-WSMan.md)

