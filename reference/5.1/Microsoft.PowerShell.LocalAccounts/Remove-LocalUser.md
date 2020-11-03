---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalUser
ms.openlocfilehash: de1054971dab19f8cfae654208488ca9ce5e17e4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250850"
---
# <span data-ttu-id="b5c8e-103">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="b5c8e-103">Remove-LocalUser</span></span>

## <span data-ttu-id="b5c8e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b5c8e-104">SYNOPSIS</span></span>
<span data-ttu-id="b5c8e-105">Lokale gebruikers accounts worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-105">Deletes local user accounts.</span></span>

## <span data-ttu-id="b5c8e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b5c8e-106">SYNTAX</span></span>

### <span data-ttu-id="b5c8e-107">Input object</span><span class="sxs-lookup"><span data-stu-id="b5c8e-107">InputObject</span></span>

```
Remove-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5c8e-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="b5c8e-108">Default</span></span>

```
Remove-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b5c8e-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="b5c8e-109">SecurityIdentifier</span></span>

```
Remove-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b5c8e-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b5c8e-110">DESCRIPTION</span></span>
<span data-ttu-id="b5c8e-111">Met de cmdlet **Remove-lokalegebruiker** worden lokale gebruikers accounts verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-111">The **Remove-LocalUser** cmdlet deletes local user accounts.</span></span>

## <span data-ttu-id="b5c8e-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b5c8e-112">EXAMPLES</span></span>

### <span data-ttu-id="b5c8e-113">Voor beeld 1: een gebruikers account verwijderen</span><span class="sxs-lookup"><span data-stu-id="b5c8e-113">Example 1: Delete a user account</span></span>

```
PS C:\> Remove-LocalUser -Name "AdminContoso02"
```

<span data-ttu-id="b5c8e-114">Met deze opdracht wordt het gebruikers account met de naam AdminContoso02 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-114">This command deletes the user account named AdminContoso02.</span></span>

> [!NOTE]
> <span data-ttu-id="b5c8e-115">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="b5c8e-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5c8e-116">PARAMETERS</span></span>

### <span data-ttu-id="b5c8e-117">-Input object</span><span class="sxs-lookup"><span data-stu-id="b5c8e-117">-InputObject</span></span>
<span data-ttu-id="b5c8e-118">Hiermee geeft u een matrix op met gebruikers accounts die met deze cmdlet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-118">Specifies an array of user accounts that this cmdlet deletes.</span></span>
<span data-ttu-id="b5c8e-119">Gebruik de cmdlet Get-LocalUser om een gebruikers account te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-119">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

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

### <span data-ttu-id="b5c8e-120">-Name</span><span class="sxs-lookup"><span data-stu-id="b5c8e-120">-Name</span></span>
<span data-ttu-id="b5c8e-121">Hiermee geeft u een matrix met namen op van de gebruikers accounts die met deze cmdlet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-121">Specifies an array of names of the user accounts that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="b5c8e-122">-SID</span><span class="sxs-lookup"><span data-stu-id="b5c8e-122">-SID</span></span>
<span data-ttu-id="b5c8e-123">Hiermee geeft u een matrix met beveiligings-Id's (Sid's) op van gebruikers accounts die met deze cmdlet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-123">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="b5c8e-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b5c8e-124">-Confirm</span></span>
<span data-ttu-id="b5c8e-125">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b5c8e-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b5c8e-126">-WhatIf</span></span>
<span data-ttu-id="b5c8e-127">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b5c8e-128">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b5c8e-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5c8e-129">CommonParameters</span></span>
<span data-ttu-id="b5c8e-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5c8e-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5c8e-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="b5c8e-132">INPUTS</span></span>

### <span data-ttu-id="b5c8e-133">System. Management. Automation. SecurityAccountsManager. Lokalegebruiker, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="b5c8e-133">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="b5c8e-134">U kunt een lokale gebruiker, een teken reeks of een SID door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-134">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="b5c8e-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b5c8e-135">OUTPUTS</span></span>

### <span data-ttu-id="b5c8e-136">Geen</span><span class="sxs-lookup"><span data-stu-id="b5c8e-136">None</span></span>
<span data-ttu-id="b5c8e-137">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-137">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b5c8e-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b5c8e-138">NOTES</span></span>

* <span data-ttu-id="b5c8e-139">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-139">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="b5c8e-140">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="b5c8e-140">The possible sources are as follows:</span></span>

- <span data-ttu-id="b5c8e-141">Lokaal</span><span class="sxs-lookup"><span data-stu-id="b5c8e-141">Local</span></span>
- <span data-ttu-id="b5c8e-142">Active Directory</span><span class="sxs-lookup"><span data-stu-id="b5c8e-142">Active Directory</span></span>
- <span data-ttu-id="b5c8e-143">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="b5c8e-143">Azure Active Directory group</span></span>
- <span data-ttu-id="b5c8e-144">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="b5c8e-144">Microsoft Account</span></span>

<span data-ttu-id="b5c8e-145">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-145">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="b5c8e-146">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="b5c8e-146">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="b5c8e-147">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b5c8e-147">RELATED LINKS</span></span>

[<span data-ttu-id="b5c8e-148">Disable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b5c8e-148">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="b5c8e-149">Enable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b5c8e-149">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="b5c8e-150">Get-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b5c8e-150">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="b5c8e-151">New-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b5c8e-151">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="b5c8e-152">Naam wijzigen-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b5c8e-152">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="b5c8e-153">Set-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="b5c8e-153">Set-LocalUser</span></span>](Set-LocalUser.md)
