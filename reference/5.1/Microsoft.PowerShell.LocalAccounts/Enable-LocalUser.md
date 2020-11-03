---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/enable-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-LocalUser
ms.openlocfilehash: 80d062578e7114b69e5cb5f3367b56da3871b9df
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249930"
---
# <span data-ttu-id="b6187-103">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="b6187-103">Enable-LocalUser</span></span>

## <span data-ttu-id="b6187-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b6187-104">SYNOPSIS</span></span>
<span data-ttu-id="b6187-105">Hiermee schakelt u een lokaal gebruikers account in.</span><span class="sxs-lookup"><span data-stu-id="b6187-105">Enables a local user account.</span></span>

## <span data-ttu-id="b6187-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b6187-106">SYNTAX</span></span>

### <span data-ttu-id="b6187-107">Input object</span><span class="sxs-lookup"><span data-stu-id="b6187-107">InputObject</span></span>

```
Enable-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b6187-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="b6187-108">Default</span></span>

```
Enable-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b6187-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="b6187-109">SecurityIdentifier</span></span>

```
Enable-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b6187-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b6187-110">DESCRIPTION</span></span>
<span data-ttu-id="b6187-111">Met de cmdlet **Enable-lokalegebruiker** worden lokale gebruikers accounts ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b6187-111">The **Enable-LocalUser** cmdlet enables local user accounts.</span></span>
<span data-ttu-id="b6187-112">Wanneer een gebruikers account is uitgeschakeld, kan de gebruiker zich niet aanmelden.</span><span class="sxs-lookup"><span data-stu-id="b6187-112">When a user account is disabled, the user cannot log on.</span></span>
<span data-ttu-id="b6187-113">Wanneer een gebruikers account is ingeschakeld, kan de gebruiker zich aanmelden.</span><span class="sxs-lookup"><span data-stu-id="b6187-113">When a user account is enabled, the user can log on.</span></span>

> [!NOTE]
> <span data-ttu-id="b6187-114">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="b6187-114">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="b6187-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b6187-115">EXAMPLES</span></span>

### <span data-ttu-id="b6187-116">Voor beeld 1: een account inschakelen door een naam op te geven</span><span class="sxs-lookup"><span data-stu-id="b6187-116">Example 1: Enable an account by specifying a name</span></span>

```
PS C:\> Enable-LocalUser -Name "Admin02"
```

<span data-ttu-id="b6187-117">Met deze opdracht wordt het gebruikers account met de naam Admin02 ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b6187-117">This command enables the user account named Admin02.</span></span>

### <span data-ttu-id="b6187-118">Voor beeld 2: een account inschakelen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="b6187-118">Example 2: Enable an account by using the pipeline</span></span>

```
PS C:\> Get-LocalUser -Name "Administrator" | Enable-LocalUser
```

<span data-ttu-id="b6187-119">Met deze opdracht wordt het ingebouwde Administrator-account opgehaald met behulp van **Get-lokalegebruiker** en wordt het vervolgens door gegeven aan de huidige cmdlet met behulp van de pijplijn operator.</span><span class="sxs-lookup"><span data-stu-id="b6187-119">This command gets the built-in Administrator account by using **Get-LocalUser** , and then passes it to the current cmdlet by using the pipeline operator.</span></span>
<span data-ttu-id="b6187-120">Met deze cmdlet wordt dat account ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b6187-120">That cmdlet enables that account.</span></span>

## <span data-ttu-id="b6187-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b6187-121">PARAMETERS</span></span>

### <span data-ttu-id="b6187-122">-Input object</span><span class="sxs-lookup"><span data-stu-id="b6187-122">-InputObject</span></span>
<span data-ttu-id="b6187-123">Hiermee geeft u een matrix van gebruikers accounts op die met deze cmdlet worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b6187-123">Specifies an array of user accounts that this cmdlet enables.</span></span>
<span data-ttu-id="b6187-124">Gebruik de cmdlet Get-LocalUser om een gebruikers account te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="b6187-124">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b6187-125">-Name</span><span class="sxs-lookup"><span data-stu-id="b6187-125">-Name</span></span>
<span data-ttu-id="b6187-126">Hiermee geeft u een matrix met namen op van de gebruikers accounts die met deze cmdlet worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b6187-126">Specifies an array of names of the user accounts that this cmdlet enables.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b6187-127">-SID</span><span class="sxs-lookup"><span data-stu-id="b6187-127">-SID</span></span>
<span data-ttu-id="b6187-128">Hiermee geeft u een matrix van gebruikers accounts op die met deze cmdlet worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b6187-128">Specifies an array of user accounts that this cmdlet enables.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b6187-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b6187-129">-Confirm</span></span>
<span data-ttu-id="b6187-130">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b6187-130">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b6187-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b6187-131">-WhatIf</span></span>
<span data-ttu-id="b6187-132">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b6187-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b6187-133">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b6187-133">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b6187-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b6187-134">CommonParameters</span></span>
<span data-ttu-id="b6187-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b6187-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b6187-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b6187-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b6187-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="b6187-137">INPUTS</span></span>

### <span data-ttu-id="b6187-138">System. Management. Automation. SecurityAccountsManager. Lokalegebruiker, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="b6187-138">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="b6187-139">U kunt een lokale gebruiker, een teken reeks of een SID door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6187-139">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="b6187-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b6187-140">OUTPUTS</span></span>

### <span data-ttu-id="b6187-141">Geen</span><span class="sxs-lookup"><span data-stu-id="b6187-141">None</span></span>
<span data-ttu-id="b6187-142">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b6187-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b6187-143">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b6187-143">NOTES</span></span>

* <span data-ttu-id="b6187-144">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="b6187-144">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="b6187-145">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="b6187-145">The possible sources are as follows:</span></span>

- <span data-ttu-id="b6187-146">Lokaal</span><span class="sxs-lookup"><span data-stu-id="b6187-146">Local</span></span>
- <span data-ttu-id="b6187-147">Active Directory</span><span class="sxs-lookup"><span data-stu-id="b6187-147">Active Directory</span></span>
- <span data-ttu-id="b6187-148">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="b6187-148">Azure Active Directory group</span></span>
- <span data-ttu-id="b6187-149">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="b6187-149">Microsoft Account</span></span>

<span data-ttu-id="b6187-150">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="b6187-150">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="b6187-151">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="b6187-151">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="b6187-152">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b6187-152">RELATED LINKS</span></span>

[<span data-ttu-id="b6187-153">Disable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b6187-153">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="b6187-154">Get-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b6187-154">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="b6187-155">New-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b6187-155">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="b6187-156">Remove-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b6187-156">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="b6187-157">Naam wijzigen-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b6187-157">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="b6187-158">Set-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b6187-158">Set-LocalUser</span></span>](Set-LocalUser.md)
