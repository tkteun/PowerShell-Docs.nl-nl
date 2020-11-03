---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalUser
ms.openlocfilehash: fc5740e52e08ad2146981799a4e1659cd420b321
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250849"
---
# <span data-ttu-id="7b4f3-103">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="7b4f3-103">Rename-LocalUser</span></span>

## <span data-ttu-id="7b4f3-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7b4f3-104">SYNOPSIS</span></span>
<span data-ttu-id="7b4f3-105">De naam van een lokale gebruikers account wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-105">Renames a local user account.</span></span>

## <span data-ttu-id="7b4f3-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7b4f3-106">SYNTAX</span></span>

### <span data-ttu-id="7b4f3-107">Input object</span><span class="sxs-lookup"><span data-stu-id="7b4f3-107">InputObject</span></span>

```
Rename-LocalUser [-InputObject] <LocalUser> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7b4f3-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="7b4f3-108">Default</span></span>

```
Rename-LocalUser [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7b4f3-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="7b4f3-109">SecurityIdentifier</span></span>

```
Rename-LocalUser [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7b4f3-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7b4f3-110">DESCRIPTION</span></span>
<span data-ttu-id="7b4f3-111">De naam van de cmdlet **Rename-lokalegebruiker** wijzigt een lokale gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-111">The **Rename-LocalUser** cmdlet renames a local user account.</span></span>

> [!NOTE]
> <span data-ttu-id="7b4f3-112">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="7b4f3-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7b4f3-113">EXAMPLES</span></span>

### <span data-ttu-id="7b4f3-114">Voor beeld 1: de naam van een gebruikers account wijzigen</span><span class="sxs-lookup"><span data-stu-id="7b4f3-114">Example 1: Rename a user account</span></span>

```
PS C:\> Rename-LocalUser -Name "Admin02" -NewName "AdminContoso02"
```

<span data-ttu-id="7b4f3-115">Met deze opdracht wordt de naam gewijzigd van het gebruikers account met de naam Admin02.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-115">This command renames the user account named Admin02.</span></span>

## <span data-ttu-id="7b4f3-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7b4f3-116">PARAMETERS</span></span>

### <span data-ttu-id="7b4f3-117">-Input object</span><span class="sxs-lookup"><span data-stu-id="7b4f3-117">-InputObject</span></span>
<span data-ttu-id="7b4f3-118">Hiermee geeft u het gebruikers account op dat met deze cmdlet wordt hernoemd.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-118">Specifies the user account that this cmdlet renames.</span></span>
<span data-ttu-id="7b4f3-119">Gebruik de cmdlet Get-LocalUser om een gebruikers account te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-119">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7b4f3-120">-Name</span><span class="sxs-lookup"><span data-stu-id="7b4f3-120">-Name</span></span>
<span data-ttu-id="7b4f3-121">Hiermee geeft u de naam van het gebruikers account dat door deze cmdlet wordt hernoemd.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-121">Specifies the name of the user account that this cmdlet renames.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7b4f3-122">-NewName</span><span class="sxs-lookup"><span data-stu-id="7b4f3-122">-NewName</span></span>
<span data-ttu-id="7b4f3-123">Hiermee geeft u een nieuwe naam op voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-123">Specifies a new name for the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7b4f3-124">-SID</span><span class="sxs-lookup"><span data-stu-id="7b4f3-124">-SID</span></span>
<span data-ttu-id="7b4f3-125">Hiermee geeft u de beveiligings-ID (SID) van een gebruikers account op die door deze cmdlet wordt hernoemd.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-125">Specifies the security ID (SID) of a user accounts that this cmdlet renames.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7b4f3-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7b4f3-126">-Confirm</span></span>
<span data-ttu-id="7b4f3-127">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7b4f3-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7b4f3-128">-WhatIf</span></span>
<span data-ttu-id="7b4f3-129">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7b4f3-130">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7b4f3-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7b4f3-131">CommonParameters</span></span>
<span data-ttu-id="7b4f3-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7b4f3-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7b4f3-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="7b4f3-134">INPUTS</span></span>

### <span data-ttu-id="7b4f3-135">System. Management. Automation. SecurityAccountsManager. Lokalegebruiker, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="7b4f3-135">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="7b4f3-136">U kunt een lokale gebruiker, een teken reeks of een SID door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-136">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="7b4f3-137">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7b4f3-137">OUTPUTS</span></span>

### <span data-ttu-id="7b4f3-138">Geen</span><span class="sxs-lookup"><span data-stu-id="7b4f3-138">None</span></span>
<span data-ttu-id="7b4f3-139">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7b4f3-140">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7b4f3-140">NOTES</span></span>

* <span data-ttu-id="7b4f3-141">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-141">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="7b4f3-142">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="7b4f3-142">The possible sources are as follows:</span></span>

- <span data-ttu-id="7b4f3-143">Lokaal</span><span class="sxs-lookup"><span data-stu-id="7b4f3-143">Local</span></span>
- <span data-ttu-id="7b4f3-144">Active Directory</span><span class="sxs-lookup"><span data-stu-id="7b4f3-144">Active Directory</span></span>
- <span data-ttu-id="7b4f3-145">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="7b4f3-145">Azure Active Directory group</span></span>
- <span data-ttu-id="7b4f3-146">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="7b4f3-146">Microsoft Account</span></span>

<span data-ttu-id="7b4f3-147">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-147">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="7b4f3-148">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="7b4f3-148">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="7b4f3-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7b4f3-149">RELATED LINKS</span></span>

[<span data-ttu-id="7b4f3-150">Disable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="7b4f3-150">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="7b4f3-151">Enable-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="7b4f3-151">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="7b4f3-152">Get-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="7b4f3-152">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="7b4f3-153">New-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="7b4f3-153">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="7b4f3-154">Remove-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="7b4f3-154">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="7b4f3-155">Set-Lokalegebruiker</span><span class="sxs-lookup"><span data-stu-id="7b4f3-155">Set-LocalUser</span></span>](Set-LocalUser.md)
