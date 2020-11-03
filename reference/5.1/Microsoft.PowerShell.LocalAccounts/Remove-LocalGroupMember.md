---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroupMember
ms.openlocfilehash: 6e6264a65c343657c2f2f87384d76cc3f1554d3d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250613"
---
# <span data-ttu-id="ab5f2-103">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="ab5f2-103">Remove-LocalGroupMember</span></span>

## <span data-ttu-id="ab5f2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ab5f2-104">SYNOPSIS</span></span>
<span data-ttu-id="ab5f2-105">Hiermee verwijdert u leden uit een lokale groep.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-105">Removes members from a local group.</span></span>

## <span data-ttu-id="ab5f2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ab5f2-106">SYNTAX</span></span>

### <span data-ttu-id="ab5f2-107">Groep</span><span class="sxs-lookup"><span data-stu-id="ab5f2-107">Group</span></span>

```
Remove-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="ab5f2-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="ab5f2-108">Default</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ab5f2-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="ab5f2-109">SecurityIdentifier</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="ab5f2-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ab5f2-110">DESCRIPTION</span></span>
<span data-ttu-id="ab5f2-111">De cmdlet **Remove-LocalGroupMember** verwijdert gebruikers of groepen uit een lokale groep.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-111">The **Remove-LocalGroupMember** cmdlet removes users or groups from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="ab5f2-112">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="ab5f2-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ab5f2-113">EXAMPLES</span></span>

### <span data-ttu-id="ab5f2-114">Voor beeld 1: leden verwijderen uit de groep Administrators</span><span class="sxs-lookup"><span data-stu-id="ab5f2-114">Example 1: Remove members from the Administrators group</span></span>

```
PS C:\> Remove-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

<span data-ttu-id="ab5f2-115">Met deze opdracht worden verschillende leden uit de lokale groep Administrators verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-115">This command removes several members from the local Administrators group.</span></span>
<span data-ttu-id="ab5f2-116">De leden die met deze cmdlet worden verwijderd, zijn onder andere een lokale gebruikers account, een Microsoft-account, een Azure Active Directory account en een domein groep.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-116">The members that this cmdlet removes include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span>
<span data-ttu-id="ab5f2-117">In dit voor beeld wordt een tijdelijke aanduiding gebruikt voor de gebruikers naam van een account op Outlook.com.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-117">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

## <span data-ttu-id="ab5f2-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ab5f2-118">PARAMETERS</span></span>

### <span data-ttu-id="ab5f2-119">-Group</span><span class="sxs-lookup"><span data-stu-id="ab5f2-119">-Group</span></span>
<span data-ttu-id="ab5f2-120">Hiermee geeft u de beveiligings groep op waarvan deze cmdlet leden verwijdert.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-120">Specifies the security group from which this cmdlet removes members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab5f2-121">-Lid</span><span class="sxs-lookup"><span data-stu-id="ab5f2-121">-Member</span></span>
<span data-ttu-id="ab5f2-122">Hiermee geeft u een matrix van gebruikers of groepen die met deze cmdlet worden verwijderd uit een beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-122">Specifies an array of users or groups that this cmdlet removes from a security group.</span></span>
<span data-ttu-id="ab5f2-123">U kunt gebruikers of groepen opgeven op naam, beveiligings-ID (SID) of **LocalPrincipal** -objecten.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-123">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>
<span data-ttu-id="ab5f2-124">Geef SID-teken reeksen op in S-R-I-S-S.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-124">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="ab5f2-125">.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-125">.</span></span> <span data-ttu-id="ab5f2-126">.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-126">.</span></span>
<span data-ttu-id="ab5f2-127">als indeling.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-127">format.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ab5f2-128">-Name</span><span class="sxs-lookup"><span data-stu-id="ab5f2-128">-Name</span></span>
<span data-ttu-id="ab5f2-129">Hiermee geeft u de naam van de beveiligings groep waaruit deze cmdlet leden verwijdert.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-129">Specifies the name of the security group from which this cmdlet removes members.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab5f2-130">-SID</span><span class="sxs-lookup"><span data-stu-id="ab5f2-130">-SID</span></span>
<span data-ttu-id="ab5f2-131">Hiermee geeft u de beveiligings-ID op van de beveiligings groep waaruit deze cmdlet leden verwijdert.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-131">Specifies the security ID of the security group from which this cmdlet removes members.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ab5f2-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ab5f2-132">-Confirm</span></span>
<span data-ttu-id="ab5f2-133">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ab5f2-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ab5f2-134">-WhatIf</span></span>
<span data-ttu-id="ab5f2-135">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ab5f2-136">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ab5f2-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab5f2-137">CommonParameters</span></span>
<span data-ttu-id="ab5f2-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab5f2-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab5f2-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="ab5f2-140">INPUTS</span></span>

### <span data-ttu-id="ab5f2-141">System. Management. Automation. SecurityAccountsManager. LocalPrincipal, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="ab5f2-141">System.Management.Automation.SecurityAccountsManager.LocalPrincipal, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="ab5f2-142">U kunt een lokale Principal, een teken reeks of een SID door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="ab5f2-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ab5f2-143">OUTPUTS</span></span>

### <span data-ttu-id="ab5f2-144">Geen</span><span class="sxs-lookup"><span data-stu-id="ab5f2-144">None</span></span>
<span data-ttu-id="ab5f2-145">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ab5f2-146">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ab5f2-146">NOTES</span></span>

* <span data-ttu-id="ab5f2-147">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-147">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="ab5f2-148">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="ab5f2-148">The possible sources are as follows:</span></span>

- <span data-ttu-id="ab5f2-149">Lokaal</span><span class="sxs-lookup"><span data-stu-id="ab5f2-149">Local</span></span>
- <span data-ttu-id="ab5f2-150">Active Directory</span><span class="sxs-lookup"><span data-stu-id="ab5f2-150">Active Directory</span></span>
- <span data-ttu-id="ab5f2-151">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="ab5f2-151">Azure Active Directory group</span></span>
- <span data-ttu-id="ab5f2-152">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="ab5f2-152">Microsoft Account</span></span>

<span data-ttu-id="ab5f2-153">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-153">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="ab5f2-154">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="ab5f2-154">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="ab5f2-155">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ab5f2-155">RELATED LINKS</span></span>

[<span data-ttu-id="ab5f2-156">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="ab5f2-156">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="ab5f2-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="ab5f2-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="ab5f2-158">Nieuw-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="ab5f2-158">New-LocalGroup</span></span>](New-LocalGroup.md)
