---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-LocalGroupMember
ms.openlocfilehash: 06993c8f6618472f4809e37fbf83d298d13ae515
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249933"
---
# <span data-ttu-id="aeae5-103">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="aeae5-103">Add-LocalGroupMember</span></span>

## <span data-ttu-id="aeae5-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="aeae5-104">SYNOPSIS</span></span>
<span data-ttu-id="aeae5-105">Hiermee voegt u leden toe aan een lokale groep.</span><span class="sxs-lookup"><span data-stu-id="aeae5-105">Adds members to a local group.</span></span>

## <span data-ttu-id="aeae5-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="aeae5-106">SYNTAX</span></span>

### <span data-ttu-id="aeae5-107">Groep</span><span class="sxs-lookup"><span data-stu-id="aeae5-107">Group</span></span>

```
Add-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="aeae5-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="aeae5-108">Default</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aeae5-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="aeae5-109">SecurityIdentifier</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="aeae5-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aeae5-110">DESCRIPTION</span></span>

<span data-ttu-id="aeae5-111">De `Add-LocalGroupMember` cmdlet voegt gebruikers of groepen toe aan een lokale beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="aeae5-111">The `Add-LocalGroupMember` cmdlet adds users or groups to a local security group.</span></span> <span data-ttu-id="aeae5-112">Alle rechten en machtigingen die aan een groep zijn toegewezen, worden toegewezen aan alle leden van die groep.</span><span class="sxs-lookup"><span data-stu-id="aeae5-112">All the rights and permissions that are assigned to a group are assigned to all members of that group.</span></span>

<span data-ttu-id="aeae5-113">Leden van de groep Administrators op een lokale computer hebben machtigingen voor volledig beheer op die computer.</span><span class="sxs-lookup"><span data-stu-id="aeae5-113">Members of the Administrators group on a local computer have Full Control permissions on that computer.</span></span> <span data-ttu-id="aeae5-114">Beperk het aantal gebruikers in de groep Administrators.</span><span class="sxs-lookup"><span data-stu-id="aeae5-114">Limit the number of users in the Administrators group.</span></span>

<span data-ttu-id="aeae5-115">Als de computer lid is van een domein, kunt u gebruikers accounts, computer accounts en groeps accounts uit dat domein en uit vertrouwde domeinen toevoegen aan een lokale groep.</span><span class="sxs-lookup"><span data-stu-id="aeae5-115">If the computer is joined to a domain, you can add user accounts, computer accounts, and group accounts from that domain and from trusted domains to a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="aeae5-116">Als de computer lid is van een domein en u probeert een lokale gebruiker toe te voegen die dezelfde naam heeft als een lid van het domein, voegt deze het domeinlid toe.</span><span class="sxs-lookup"><span data-stu-id="aeae5-116">If the computer is joined to a domain and you try to add a local user that has the same name as a member of the domain it adds the domain member.</span></span>

## <span data-ttu-id="aeae5-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="aeae5-117">EXAMPLES</span></span>

### <span data-ttu-id="aeae5-118">Voor beeld 1: leden toevoegen aan de groep Administrators</span><span class="sxs-lookup"><span data-stu-id="aeae5-118">Example 1: Add members to the Administrators group</span></span>

<span data-ttu-id="aeae5-119">Met deze opdracht worden verschillende leden toegevoegd aan de lokale groep Administrators.</span><span class="sxs-lookup"><span data-stu-id="aeae5-119">This command adds several members to the local Administrators group.</span></span> <span data-ttu-id="aeae5-120">De nieuwe leden bevatten een lokale gebruikers account, een Microsoft-account, een Azure Active Directory account en een domein groep.</span><span class="sxs-lookup"><span data-stu-id="aeae5-120">The new members include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span> <span data-ttu-id="aeae5-121">In dit voor beeld wordt een tijdelijke aanduiding gebruikt voor de gebruikers naam van een account op Outlook.com.</span><span class="sxs-lookup"><span data-stu-id="aeae5-121">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

## <span data-ttu-id="aeae5-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aeae5-122">PARAMETERS</span></span>

### <span data-ttu-id="aeae5-123">-Group</span><span class="sxs-lookup"><span data-stu-id="aeae5-123">-Group</span></span>

<span data-ttu-id="aeae5-124">Hiermee geeft u de beveiligings groep waaraan deze cmdlet leden toevoegt.</span><span class="sxs-lookup"><span data-stu-id="aeae5-124">Specifies the security group to which this cmdlet adds members.</span></span>

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

### <span data-ttu-id="aeae5-125">-Lid</span><span class="sxs-lookup"><span data-stu-id="aeae5-125">-Member</span></span>

<span data-ttu-id="aeae5-126">Hiermee geeft u een matrix van gebruikers of groepen die met deze cmdlet worden toegevoegd aan een beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="aeae5-126">Specifies an array of users or groups that this cmdlet adds to a security group.</span></span> <span data-ttu-id="aeae5-127">U kunt gebruikers of groepen opgeven op naam, beveiligings-ID (SID) of **LocalPrincipal** -objecten.</span><span class="sxs-lookup"><span data-stu-id="aeae5-127">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>

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

### <span data-ttu-id="aeae5-128">-Name</span><span class="sxs-lookup"><span data-stu-id="aeae5-128">-Name</span></span>

<span data-ttu-id="aeae5-129">Hiermee geeft u de naam van de beveiligings groep waaraan deze cmdlet leden toevoegt.</span><span class="sxs-lookup"><span data-stu-id="aeae5-129">Specifies the name of the security group to which this cmdlet adds members.</span></span>

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

### <span data-ttu-id="aeae5-130">-SID</span><span class="sxs-lookup"><span data-stu-id="aeae5-130">-SID</span></span>

<span data-ttu-id="aeae5-131">Hiermee geeft u de beveiligings-ID op van de beveiligings groep waaraan deze cmdlet leden toevoegt.</span><span class="sxs-lookup"><span data-stu-id="aeae5-131">Specifies the security ID of the security group to which this cmdlet adds members.</span></span>

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

### <span data-ttu-id="aeae5-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aeae5-132">-Confirm</span></span>

<span data-ttu-id="aeae5-133">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="aeae5-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="aeae5-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aeae5-134">-WhatIf</span></span>

<span data-ttu-id="aeae5-135">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="aeae5-135">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="aeae5-136">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aeae5-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="aeae5-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aeae5-137">CommonParameters</span></span>

<span data-ttu-id="aeae5-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aeae5-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aeae5-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aeae5-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aeae5-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="aeae5-140">INPUTS</span></span>

### <span data-ttu-id="aeae5-141">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="aeae5-141">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="aeae5-142">U kunt een lokale Principal, een teken reeks of een SID door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aeae5-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="aeae5-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="aeae5-143">OUTPUTS</span></span>

### <span data-ttu-id="aeae5-144">Geen</span><span class="sxs-lookup"><span data-stu-id="aeae5-144">None</span></span>

<span data-ttu-id="aeae5-145">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="aeae5-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="aeae5-146">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="aeae5-146">NOTES</span></span>

<span data-ttu-id="aeae5-147">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="aeae5-147">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

<span data-ttu-id="aeae5-148">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="aeae5-148">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="aeae5-149">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="aeae5-149">The possible sources are as follows:</span></span>

- <span data-ttu-id="aeae5-150">Lokaal</span><span class="sxs-lookup"><span data-stu-id="aeae5-150">Local</span></span>
- <span data-ttu-id="aeae5-151">Active Directory</span><span class="sxs-lookup"><span data-stu-id="aeae5-151">Active Directory</span></span>
- <span data-ttu-id="aeae5-152">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="aeae5-152">Azure Active Directory group</span></span>
- <span data-ttu-id="aeae5-153">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="aeae5-153">Microsoft Account</span></span>

<span data-ttu-id="aeae5-154">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="aeae5-154">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="aeae5-155">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="aeae5-155">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="aeae5-156">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="aeae5-156">RELATED LINKS</span></span>

[<span data-ttu-id="aeae5-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="aeae5-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="aeae5-158">Nieuw-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="aeae5-158">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="aeae5-159">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="aeae5-159">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
