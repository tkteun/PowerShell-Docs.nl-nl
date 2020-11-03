---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250612"
---
# <span data-ttu-id="5f3f9-103">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5f3f9-103">Remove-LocalGroup</span></span>

## <span data-ttu-id="5f3f9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5f3f9-104">SYNOPSIS</span></span>
<span data-ttu-id="5f3f9-105">Hiermee verwijdert u lokale beveiligings groepen.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-105">Deletes local security groups.</span></span>

## <span data-ttu-id="5f3f9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5f3f9-106">SYNTAX</span></span>

### <span data-ttu-id="5f3f9-107">Input object</span><span class="sxs-lookup"><span data-stu-id="5f3f9-107">InputObject</span></span>

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5f3f9-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="5f3f9-108">Default</span></span>

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5f3f9-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="5f3f9-109">SecurityIdentifier</span></span>

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5f3f9-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5f3f9-110">DESCRIPTION</span></span>
<span data-ttu-id="5f3f9-111">Met de cmdlet **Remove-LocalGroup** worden lokale beveiligings groepen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-111">The **Remove-LocalGroup** cmdlet deletes local security groups.</span></span>
<span data-ttu-id="5f3f9-112">Met deze cmdlet wordt alleen een lokale groep verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-112">This cmdlet deletes only a local group.</span></span>
<span data-ttu-id="5f3f9-113">De gebruikers accounts, computer accounts of groeps accounts die deel uitmaken van deze groep worden niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-113">It does not delete the user accounts, computer accounts, or group accounts that belong to that group.</span></span>
<span data-ttu-id="5f3f9-114">U kunt een verwijderde groep niet herstellen.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-114">You cannot recover a deleted group.</span></span>

<span data-ttu-id="5f3f9-115">Als u een groep verwijdert en vervolgens een andere groep met dezelfde groeps naam maakt, moet u nieuwe machtigingen voor de nieuwe groep instellen.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-115">If you delete a group and then create another group that has the same group name, you must set new permissions for the new group.</span></span>
<span data-ttu-id="5f3f9-116">De nieuwe groep neemt niet de machtigingen over die aan de groep zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-116">The new group does not inherit the permissions that were assigned to the group.</span></span>

> [!NOTE]
> <span data-ttu-id="5f3f9-117">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-117">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="5f3f9-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5f3f9-118">EXAMPLES</span></span>

### <span data-ttu-id="5f3f9-119">Voor beeld 1: een beveiligings groep verwijderen</span><span class="sxs-lookup"><span data-stu-id="5f3f9-119">Example 1: Delete a security group</span></span>

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="5f3f9-120">Met deze opdracht wordt de groep met de naam SecurityGroup04 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-120">This command deletes the group named SecurityGroup04.</span></span>

## <span data-ttu-id="5f3f9-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5f3f9-121">PARAMETERS</span></span>

### <span data-ttu-id="5f3f9-122">-Input object</span><span class="sxs-lookup"><span data-stu-id="5f3f9-122">-InputObject</span></span>
<span data-ttu-id="5f3f9-123">Hiermee geeft u een matrix van beveiligings groepen op die met deze cmdlet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-123">Specifies an array of security groups that this cmdlet deletes.</span></span>
<span data-ttu-id="5f3f9-124">Gebruik de cmdlet Get-LocalGroup om groepen te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-124">To obtain groups, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5f3f9-125">-Name</span><span class="sxs-lookup"><span data-stu-id="5f3f9-125">-Name</span></span>
<span data-ttu-id="5f3f9-126">Hiermee geeft u een matrix met namen op van de beveiligings groepen die met deze cmdlet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-126">Specifies an array of names of the security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="5f3f9-127">-SID</span><span class="sxs-lookup"><span data-stu-id="5f3f9-127">-SID</span></span>
<span data-ttu-id="5f3f9-128">Hiermee geeft u een matrix met beveiligings-Id's (Sid's) op van beveiligings groepen die met deze cmdlet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-128">Specifies an array of security IDs (SIDs) of security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="5f3f9-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5f3f9-129">-Confirm</span></span>
<span data-ttu-id="5f3f9-130">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5f3f9-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5f3f9-131">-WhatIf</span></span>
<span data-ttu-id="5f3f9-132">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5f3f9-133">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5f3f9-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f3f9-134">CommonParameters</span></span>
<span data-ttu-id="5f3f9-135">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f3f9-136">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f3f9-137">INVOER</span><span class="sxs-lookup"><span data-stu-id="5f3f9-137">INPUTS</span></span>

### <span data-ttu-id="5f3f9-138">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="5f3f9-138">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="5f3f9-139">U kunt een beveiligings groep, een teken reeks of een SID door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-139">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="5f3f9-140">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5f3f9-140">OUTPUTS</span></span>

### <span data-ttu-id="5f3f9-141">Geen</span><span class="sxs-lookup"><span data-stu-id="5f3f9-141">None</span></span>
<span data-ttu-id="5f3f9-142">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5f3f9-143">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5f3f9-143">NOTES</span></span>

* <span data-ttu-id="5f3f9-144">Met deze cmdlet kunnen de volgende standaard groepen niet worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="5f3f9-144">This cmdlet cannot delete the following default groups:</span></span>

- <span data-ttu-id="5f3f9-145">Beheerders</span><span class="sxs-lookup"><span data-stu-id="5f3f9-145">Administrators</span></span>
- <span data-ttu-id="5f3f9-146">Back-upoperators</span><span class="sxs-lookup"><span data-stu-id="5f3f9-146">Backup Operators</span></span>
- <span data-ttu-id="5f3f9-147">Cryptografische Operators</span><span class="sxs-lookup"><span data-stu-id="5f3f9-147">Cryptographic Operators</span></span>
- <span data-ttu-id="5f3f9-148">Gedistribueerde COM-gebruikers</span><span class="sxs-lookup"><span data-stu-id="5f3f9-148">Distributed COM Users</span></span>
- <span data-ttu-id="5f3f9-149">Gebeurtenislogboek-lezers</span><span class="sxs-lookup"><span data-stu-id="5f3f9-149">Event Log Readers</span></span>
- <span data-ttu-id="5f3f9-150">Gasten</span><span class="sxs-lookup"><span data-stu-id="5f3f9-150">Guests</span></span>
- <span data-ttu-id="5f3f9-151">Hyper-V-beheerders</span><span class="sxs-lookup"><span data-stu-id="5f3f9-151">Hyper-V Administrators</span></span>
- <span data-ttu-id="5f3f9-152">IIS_IUSRS</span><span class="sxs-lookup"><span data-stu-id="5f3f9-152">IIS_IUSRS</span></span>
- <span data-ttu-id="5f3f9-153">Network Configuration Operators</span><span class="sxs-lookup"><span data-stu-id="5f3f9-153">Network Configuration Operators</span></span>
- <span data-ttu-id="5f3f9-154">Prestatielogboekgebruikers</span><span class="sxs-lookup"><span data-stu-id="5f3f9-154">Performance Log Users</span></span>
- <span data-ttu-id="5f3f9-155">Prestatiemetergebruikers</span><span class="sxs-lookup"><span data-stu-id="5f3f9-155">Performance Monitor Users</span></span>
- <span data-ttu-id="5f3f9-156">Hoofdgebruikers</span><span class="sxs-lookup"><span data-stu-id="5f3f9-156">Power Users</span></span>
- <span data-ttu-id="5f3f9-157">Extern bureaublad-gebruikers</span><span class="sxs-lookup"><span data-stu-id="5f3f9-157">Remote Desktop Users</span></span>
- <span data-ttu-id="5f3f9-158">Gebruikers van extern beheer</span><span class="sxs-lookup"><span data-stu-id="5f3f9-158">Remote Management Users</span></span>
- <span data-ttu-id="5f3f9-159">Replicator</span><span class="sxs-lookup"><span data-stu-id="5f3f9-159">Replicator</span></span>
- <span data-ttu-id="5f3f9-160">Gebruikers</span><span class="sxs-lookup"><span data-stu-id="5f3f9-160">Users</span></span>
- <span data-ttu-id="5f3f9-161">WinRMRemoteWMIUsers__</span><span class="sxs-lookup"><span data-stu-id="5f3f9-161">WinRMRemoteWMIUsers__</span></span>

* <span data-ttu-id="5f3f9-162">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-162">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="5f3f9-163">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="5f3f9-163">The possible sources are as follows:</span></span>

- <span data-ttu-id="5f3f9-164">Lokaal</span><span class="sxs-lookup"><span data-stu-id="5f3f9-164">Local</span></span>
- <span data-ttu-id="5f3f9-165">Active Directory</span><span class="sxs-lookup"><span data-stu-id="5f3f9-165">Active Directory</span></span>
- <span data-ttu-id="5f3f9-166">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="5f3f9-166">Azure Active Directory group</span></span>
- <span data-ttu-id="5f3f9-167">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="5f3f9-167">Microsoft Account</span></span>

<span data-ttu-id="5f3f9-168">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-168">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="5f3f9-169">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="5f3f9-169">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="5f3f9-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5f3f9-170">RELATED LINKS</span></span>

[<span data-ttu-id="5f3f9-171">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5f3f9-171">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="5f3f9-172">Nieuw-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5f3f9-172">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="5f3f9-173">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5f3f9-173">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="5f3f9-174">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5f3f9-174">Set-LocalGroup</span></span>](Set-LocalGroup.md)
