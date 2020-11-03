---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: a754b6530ecd8b3153d82327a246cbb387d53dd5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249667"
---
# <span data-ttu-id="58be0-103">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="58be0-103">Disconnect-WSMan</span></span>

## <span data-ttu-id="58be0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="58be0-104">SYNOPSIS</span></span>
<span data-ttu-id="58be0-105">Verbreekt de verbinding tussen de client en de WinRM-service op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="58be0-105">Disconnects the client from the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="58be0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="58be0-106">SYNTAX</span></span>

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="58be0-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="58be0-107">DESCRIPTION</span></span>
<span data-ttu-id="58be0-108">Met de cmdlet **Disconnect-WSMan** wordt de verbinding tussen de client en de WinRM-service op een externe computer verbroken.</span><span class="sxs-lookup"><span data-stu-id="58be0-108">The **Disconnect-WSMan** cmdlet disconnects the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="58be0-109">Als u de WS-Management-sessie in een variabele hebt opgeslagen, blijft het sessie object in de variabele, maar wordt de status van de WS-Management sessie gesloten.</span><span class="sxs-lookup"><span data-stu-id="58be0-109">If you saved the WS-Management session in a variable, the session object remains in the variable, but the state of the WS-Management session is Closed.</span></span>
<span data-ttu-id="58be0-110">U kunt deze cmdlet in de context van de WSMan-provider gebruiken om de client te verbreken van de WinRM-service op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="58be0-110">You can use this cmdlet within the context of the WSMan provider to disconnect the client from the WinRM service on a remote computer.</span></span>
<span data-ttu-id="58be0-111">U kunt deze cmdlet echter ook gebruiken om de verbinding met de WinRM-service op externe computers te verbreken voordat u overschakelt naar de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="58be0-111">However, you can also use this cmdlet to disconnect from the WinRM service on remote computers before you change to the WSMan provider.</span></span>

<span data-ttu-id="58be0-112">Zie Connect-WSMan voor meer informatie over het maken van een verbinding met de WinRM-service op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="58be0-112">For more information about how to connect to the WinRM service on a remote computer, see Connect-WSMan.</span></span>

## <span data-ttu-id="58be0-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="58be0-113">EXAMPLES</span></span>

### <span data-ttu-id="58be0-114">Voor beeld 1: een verbinding met een externe computer verwijderen</span><span class="sxs-lookup"><span data-stu-id="58be0-114">Example 1: Delete a connection to a remote computer</span></span>

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

<span data-ttu-id="58be0-115">Met deze opdracht wordt de verbinding met de externe computer met de naam Server01 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="58be0-115">This command deletes the connection to the remote computer named server01.</span></span>

<span data-ttu-id="58be0-116">Deze cmdlet wordt doorgaans gebruikt in de context van de WSMan-provider om de verbinding met een externe computer te verbreken, in dit geval de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="58be0-116">This cmdlet is generally used within the context of the WSMan provider to disconnect from a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="58be0-117">U kunt echter ook **Disconnect-WSMan** gebruiken om verbindingen met externe computers te verwijderen voordat u overschakelt naar de WSMan-provider.</span><span class="sxs-lookup"><span data-stu-id="58be0-117">However, you can also use **Disconnect-WSMan** to remove connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="58be0-118">Deze verbindingen worden niet weer gegeven in de lijst computer naam.</span><span class="sxs-lookup"><span data-stu-id="58be0-118">Those connections do not appear in the ComputerName list.</span></span>

## <span data-ttu-id="58be0-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="58be0-119">PARAMETERS</span></span>

### <span data-ttu-id="58be0-120">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="58be0-120">-ComputerName</span></span>
<span data-ttu-id="58be0-121">Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="58be0-121">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="58be0-122">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="58be0-122">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="58be0-123">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="58be0-123">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="58be0-124">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="58be0-124">The local computer is the default.</span></span>
<span data-ttu-id="58be0-125">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="58be0-125">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="58be0-126">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="58be0-126">You can pipe a value for this parameter to the cmdlet.</span></span>

<span data-ttu-id="58be0-127">U kunt de verbinding met de lokale host niet verbreken.</span><span class="sxs-lookup"><span data-stu-id="58be0-127">You cannot disconnect from the local host.</span></span>
<span data-ttu-id="58be0-128">Dat wil zeggen dat u de standaard verbinding met de lokale computer niet kunt verbreken.</span><span class="sxs-lookup"><span data-stu-id="58be0-128">That is, you cannot disconnect the default connection to the local computer.</span></span>
<span data-ttu-id="58be0-129">Als u echter een afzonderlijke verbinding maakt met de lokale computer, bijvoorbeeld met behulp van de computer naam.</span><span class="sxs-lookup"><span data-stu-id="58be0-129">However, if you create a separate connection to the local computer, for example, by using the computer name.</span></span>

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

### <span data-ttu-id="58be0-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="58be0-130">CommonParameters</span></span>
<span data-ttu-id="58be0-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="58be0-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="58be0-132">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="58be0-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="58be0-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="58be0-133">INPUTS</span></span>

### <span data-ttu-id="58be0-134">Geen</span><span class="sxs-lookup"><span data-stu-id="58be0-134">None</span></span>
<span data-ttu-id="58be0-135">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="58be0-135">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="58be0-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="58be0-136">OUTPUTS</span></span>

### <span data-ttu-id="58be0-137">Geen</span><span class="sxs-lookup"><span data-stu-id="58be0-137">None</span></span>
<span data-ttu-id="58be0-138">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="58be0-138">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="58be0-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="58be0-139">NOTES</span></span>

## <span data-ttu-id="58be0-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="58be0-140">RELATED LINKS</span></span>

[<span data-ttu-id="58be0-141">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="58be0-141">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="58be0-142">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="58be0-142">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="58be0-143">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="58be0-143">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="58be0-144">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="58be0-144">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="58be0-145">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="58be0-145">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="58be0-146">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="58be0-146">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="58be0-147">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="58be0-147">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="58be0-148">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="58be0-148">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="58be0-149">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="58be0-149">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="58be0-150">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="58be0-150">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="58be0-151">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="58be0-151">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="58be0-152">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="58be0-152">Test-WSMan</span></span>](Test-WSMan.md)
