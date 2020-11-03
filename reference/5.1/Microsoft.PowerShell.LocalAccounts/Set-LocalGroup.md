---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalGroup
ms.openlocfilehash: 471c3c7bc01bf26dfe9d8eec26e4414464cae02e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250848"
---
# <span data-ttu-id="02173-103">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="02173-103">Set-LocalGroup</span></span>

## <span data-ttu-id="02173-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="02173-104">SYNOPSIS</span></span>
<span data-ttu-id="02173-105">Hiermee wijzigt u een lokale beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="02173-105">Changes a local security group.</span></span>

## <span data-ttu-id="02173-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="02173-106">SYNTAX</span></span>

### <span data-ttu-id="02173-107">Input object</span><span class="sxs-lookup"><span data-stu-id="02173-107">InputObject</span></span>

```
Set-LocalGroup -Description <String> [-InputObject] <LocalGroup> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="02173-108">Standaard</span><span class="sxs-lookup"><span data-stu-id="02173-108">Default</span></span>

```
Set-LocalGroup -Description <String> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="02173-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="02173-109">SecurityIdentifier</span></span>

```
Set-LocalGroup -Description <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="02173-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="02173-110">DESCRIPTION</span></span>
<span data-ttu-id="02173-111">De cmdlet **set-LocalGroup** wijzigt een lokale beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="02173-111">The **Set-LocalGroup** cmdlet changes a local security group.</span></span>

## <span data-ttu-id="02173-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="02173-112">EXAMPLES</span></span>

### <span data-ttu-id="02173-113">Voor beeld 1: een groeps beschrijving wijzigen</span><span class="sxs-lookup"><span data-stu-id="02173-113">Example 1: Change a group description</span></span>

```
PS C:\> Set-LocalGroup -Name "SecurityGroup04" -Description "This is a sample description."
```

<span data-ttu-id="02173-114">Met deze opdracht wordt de beschrijving van een lokale groep gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="02173-114">This command changes the description of a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="02173-115">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="02173-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="02173-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="02173-116">PARAMETERS</span></span>

### <span data-ttu-id="02173-117">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="02173-117">-Description</span></span>
<span data-ttu-id="02173-118">Hiermee geeft u een opmerking voor de groep op.</span><span class="sxs-lookup"><span data-stu-id="02173-118">Specifies a comment for the group.</span></span>
<span data-ttu-id="02173-119">De maximale lengte is 48 tekens.</span><span class="sxs-lookup"><span data-stu-id="02173-119">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="02173-120">-Input object</span><span class="sxs-lookup"><span data-stu-id="02173-120">-InputObject</span></span>
<span data-ttu-id="02173-121">Hiermee geeft u de beveiligings groep op die met deze cmdlet wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="02173-121">Specifies the security group that this cmdlet changes.</span></span>
<span data-ttu-id="02173-122">Gebruik de cmdlet Get-LocalGroup om een beveiligings groep te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="02173-122">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

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

### <span data-ttu-id="02173-123">-Name</span><span class="sxs-lookup"><span data-stu-id="02173-123">-Name</span></span>
<span data-ttu-id="02173-124">Hiermee geeft u de naam van de beveiligings groep die met deze cmdlet wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="02173-124">Specifies the name of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="02173-125">-SID</span><span class="sxs-lookup"><span data-stu-id="02173-125">-SID</span></span>
<span data-ttu-id="02173-126">Hiermee geeft u de beveiligings-ID (SID) op van de beveiligings groep die met deze cmdlet wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="02173-126">Specifies the security ID (SID) of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="02173-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="02173-127">-Confirm</span></span>
<span data-ttu-id="02173-128">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02173-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="02173-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="02173-129">-WhatIf</span></span>
<span data-ttu-id="02173-130">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02173-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="02173-131">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="02173-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="02173-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="02173-132">CommonParameters</span></span>
<span data-ttu-id="02173-133">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="02173-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="02173-134">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02173-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="02173-135">INVOER</span><span class="sxs-lookup"><span data-stu-id="02173-135">INPUTS</span></span>

### <span data-ttu-id="02173-136">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="02173-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="02173-137">U kunt een beveiligings groep, een teken reeks of een SID door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02173-137">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="02173-138">UITVOER</span><span class="sxs-lookup"><span data-stu-id="02173-138">OUTPUTS</span></span>

### <span data-ttu-id="02173-139">Geen</span><span class="sxs-lookup"><span data-stu-id="02173-139">None</span></span>
<span data-ttu-id="02173-140">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="02173-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="02173-141">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="02173-141">NOTES</span></span>

* <span data-ttu-id="02173-142">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="02173-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="02173-143">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="02173-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="02173-144">Lokaal</span><span class="sxs-lookup"><span data-stu-id="02173-144">Local</span></span>
- <span data-ttu-id="02173-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="02173-145">Active Directory</span></span>
- <span data-ttu-id="02173-146">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="02173-146">Azure Active Directory group</span></span>
- <span data-ttu-id="02173-147">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="02173-147">Microsoft Account</span></span>

<span data-ttu-id="02173-148">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="02173-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="02173-149">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="02173-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="02173-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="02173-150">RELATED LINKS</span></span>

[<span data-ttu-id="02173-151">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="02173-151">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="02173-152">Nieuw-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="02173-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="02173-153">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="02173-153">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="02173-154">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="02173-154">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)
