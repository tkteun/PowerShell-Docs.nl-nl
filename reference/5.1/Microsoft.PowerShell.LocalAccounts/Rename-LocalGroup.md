---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalGroup
ms.openlocfilehash: 566d33bdeb52323cca41fa9757d36334b40f1654
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250847"
---
# <span data-ttu-id="5e91e-103">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5e91e-103">Rename-LocalGroup</span></span>

## <span data-ttu-id="5e91e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5e91e-104">SYNOPSIS</span></span>
<span data-ttu-id="5e91e-105">De naam van een lokale beveiligings groep wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="5e91e-105">Renames a local security group.</span></span>

## <span data-ttu-id="5e91e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5e91e-106">SYNTAX</span></span>

### <span data-ttu-id="5e91e-107">Input object</span><span class="sxs-lookup"><span data-stu-id="5e91e-107">InputObject</span></span>

```
Rename-LocalGroup [-InputObject] <LocalGroup> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5e91e-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="5e91e-108">Default</span></span>

```
Rename-LocalGroup [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5e91e-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="5e91e-109">SecurityIdentifier</span></span>

```
Rename-LocalGroup [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5e91e-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5e91e-110">DESCRIPTION</span></span>
<span data-ttu-id="5e91e-111">De cmdlet **Rename-LocalGroup** wijzigt de naam van een lokale beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="5e91e-111">The **Rename-LocalGroup** cmdlet renames a local security group.</span></span>

> [!NOTE]
> <span data-ttu-id="5e91e-112">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="5e91e-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="5e91e-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5e91e-113">EXAMPLES</span></span>

### <span data-ttu-id="5e91e-114">Voor beeld 1: de naam van een groep wijzigen</span><span class="sxs-lookup"><span data-stu-id="5e91e-114">Example 1: Change the name of a group</span></span>

```
PS C:\> Rename-LocalGroup -Name "SecurityGroup" -NewName "SecurityGroup04"
```

<span data-ttu-id="5e91e-115">Met deze opdracht wordt de naam gewijzigd van een beveiligings groep genaamd beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="5e91e-115">This command renames a security group named SecurityGroup.</span></span>

## <span data-ttu-id="5e91e-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5e91e-116">PARAMETERS</span></span>

### <span data-ttu-id="5e91e-117">-Input object</span><span class="sxs-lookup"><span data-stu-id="5e91e-117">-InputObject</span></span>
<span data-ttu-id="5e91e-118">Hiermee geeft u de beveiligings groep op die met deze cmdlet wordt hernoemd.</span><span class="sxs-lookup"><span data-stu-id="5e91e-118">Specifies the security group that this cmdlet renames.</span></span>
<span data-ttu-id="5e91e-119">Gebruik de cmdlet Get-LocalGroup om een beveiligings groep te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="5e91e-119">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5e91e-120">-Name</span><span class="sxs-lookup"><span data-stu-id="5e91e-120">-Name</span></span>
<span data-ttu-id="5e91e-121">Hiermee geeft u de naam van de beveiligings groep die met deze cmdlet wordt hernoemd.</span><span class="sxs-lookup"><span data-stu-id="5e91e-121">Specifies the name of the security group that this cmdlet renames.</span></span>

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

### <span data-ttu-id="5e91e-122">-NewName</span><span class="sxs-lookup"><span data-stu-id="5e91e-122">-NewName</span></span>
<span data-ttu-id="5e91e-123">Hiermee geeft u een nieuwe naam op voor de beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="5e91e-123">Specifies a new name for the security group.</span></span>

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

### <span data-ttu-id="5e91e-124">-SID</span><span class="sxs-lookup"><span data-stu-id="5e91e-124">-SID</span></span>
<span data-ttu-id="5e91e-125">Hiermee geeft u de beveiligings-ID (SID) van een beveiligings groep op die met deze cmdlet wordt hernoemd.</span><span class="sxs-lookup"><span data-stu-id="5e91e-125">Specifies the security ID (SID) of a security group that this cmdlet renames.</span></span>

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

### <span data-ttu-id="5e91e-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5e91e-126">-Confirm</span></span>
<span data-ttu-id="5e91e-127">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5e91e-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5e91e-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5e91e-128">-WhatIf</span></span>
<span data-ttu-id="5e91e-129">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5e91e-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5e91e-130">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5e91e-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5e91e-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5e91e-131">CommonParameters</span></span>
<span data-ttu-id="5e91e-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5e91e-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5e91e-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5e91e-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5e91e-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="5e91e-134">INPUTS</span></span>

### <span data-ttu-id="5e91e-135">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="5e91e-135">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="5e91e-136">U kunt een beveiligings groep, een teken reeks of een SID door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e91e-136">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="5e91e-137">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5e91e-137">OUTPUTS</span></span>

### <span data-ttu-id="5e91e-138">Geen</span><span class="sxs-lookup"><span data-stu-id="5e91e-138">None</span></span>
<span data-ttu-id="5e91e-139">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="5e91e-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5e91e-140">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5e91e-140">NOTES</span></span>

* <span data-ttu-id="5e91e-141">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="5e91e-141">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="5e91e-142">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="5e91e-142">The possible sources are as follows:</span></span>

- <span data-ttu-id="5e91e-143">Lokaal</span><span class="sxs-lookup"><span data-stu-id="5e91e-143">Local</span></span>
- <span data-ttu-id="5e91e-144">Active Directory</span><span class="sxs-lookup"><span data-stu-id="5e91e-144">Active Directory</span></span>
- <span data-ttu-id="5e91e-145">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="5e91e-145">Azure Active Directory group</span></span>
- <span data-ttu-id="5e91e-146">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="5e91e-146">Microsoft Account</span></span>

<span data-ttu-id="5e91e-147">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="5e91e-147">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="5e91e-148">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="5e91e-148">For earlier  versions, the property is blank.</span></span>

## <span data-ttu-id="5e91e-149">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5e91e-149">RELATED LINKS</span></span>

[<span data-ttu-id="5e91e-150">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5e91e-150">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="5e91e-151">Nieuw-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5e91e-151">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="5e91e-152">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5e91e-152">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="5e91e-153">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="5e91e-153">Set-LocalGroup</span></span>](Set-LocalGroup.md)
