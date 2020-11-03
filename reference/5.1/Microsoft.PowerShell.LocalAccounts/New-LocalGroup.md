---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalGroup
ms.openlocfilehash: de66ad724d3cfee2d296d3b431618768a9cd38da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250615"
---
# <span data-ttu-id="40b78-103">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="40b78-103">New-LocalGroup</span></span>

## <span data-ttu-id="40b78-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="40b78-104">SYNOPSIS</span></span>
<span data-ttu-id="40b78-105">Hiermee maakt u een lokale beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="40b78-105">Creates a local security group.</span></span>

## <span data-ttu-id="40b78-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="40b78-106">SYNTAX</span></span>

```
New-LocalGroup [-Description <String>] [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="40b78-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="40b78-107">DESCRIPTION</span></span>
<span data-ttu-id="40b78-108">Met de cmdlet **New-LocalGroup** maakt u een lokale beveiligings groep in de SAM.</span><span class="sxs-lookup"><span data-stu-id="40b78-108">The **New-LocalGroup** cmdlet creates a local security group in the Security Account Manager.</span></span>

> [!NOTE]
> <span data-ttu-id="40b78-109">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="40b78-109">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="40b78-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="40b78-110">EXAMPLES</span></span>

### <span data-ttu-id="40b78-111">Voor beeld 1: een beveiligings groep maken</span><span class="sxs-lookup"><span data-stu-id="40b78-111">Example 1: Create a security group</span></span>

```
PS C:\> New-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="40b78-112">Met deze opdracht maakt u een groep met de naam SecurityGroup04.</span><span class="sxs-lookup"><span data-stu-id="40b78-112">This command creates a group named SecurityGroup04.</span></span>

## <span data-ttu-id="40b78-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="40b78-113">PARAMETERS</span></span>

### <span data-ttu-id="40b78-114">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="40b78-114">-Description</span></span>
<span data-ttu-id="40b78-115">Hiermee geeft u een opmerking voor de groep op.</span><span class="sxs-lookup"><span data-stu-id="40b78-115">Specifies a comment for the group.</span></span>
<span data-ttu-id="40b78-116">De maximale lengte is 48 tekens.</span><span class="sxs-lookup"><span data-stu-id="40b78-116">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="40b78-117">-Name</span><span class="sxs-lookup"><span data-stu-id="40b78-117">-Name</span></span>
<span data-ttu-id="40b78-118">Hiermee geeft u een naam op voor de groep.</span><span class="sxs-lookup"><span data-stu-id="40b78-118">Specifies a name for the group.</span></span>
<span data-ttu-id="40b78-119">De maximale lengte is 256 tekens.</span><span class="sxs-lookup"><span data-stu-id="40b78-119">The maximum length is 256 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="40b78-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="40b78-120">-Confirm</span></span>
<span data-ttu-id="40b78-121">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="40b78-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="40b78-122">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="40b78-122">-WhatIf</span></span>
<span data-ttu-id="40b78-123">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="40b78-123">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="40b78-124">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="40b78-124">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="40b78-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="40b78-125">CommonParameters</span></span>
<span data-ttu-id="40b78-126">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="40b78-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="40b78-127">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="40b78-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="40b78-128">INVOER</span><span class="sxs-lookup"><span data-stu-id="40b78-128">INPUTS</span></span>

### <span data-ttu-id="40b78-129">System. String</span><span class="sxs-lookup"><span data-stu-id="40b78-129">System.String</span></span>
<span data-ttu-id="40b78-130">U kunt een teken reeks door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40b78-130">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="40b78-131">UITVOER</span><span class="sxs-lookup"><span data-stu-id="40b78-131">OUTPUTS</span></span>

### <span data-ttu-id="40b78-132">System. Management. Automation. SecurityAccountsManager. LocalGroup</span><span class="sxs-lookup"><span data-stu-id="40b78-132">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="40b78-133">Met deze cmdlet wordt een beveiligings groep geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="40b78-133">This cmdlet returns a security group.</span></span>

## <span data-ttu-id="40b78-134">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="40b78-134">NOTES</span></span>

* <span data-ttu-id="40b78-135">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="40b78-135">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="40b78-136">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="40b78-136">The possible sources are as follows:</span></span>

- <span data-ttu-id="40b78-137">Lokaal</span><span class="sxs-lookup"><span data-stu-id="40b78-137">Local</span></span>
- <span data-ttu-id="40b78-138">Active Directory</span><span class="sxs-lookup"><span data-stu-id="40b78-138">Active Directory</span></span>
- <span data-ttu-id="40b78-139">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="40b78-139">Azure Active Directory group</span></span>
- <span data-ttu-id="40b78-140">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="40b78-140">Microsoft Account</span></span>

<span data-ttu-id="40b78-141">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="40b78-141">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="40b78-142">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="40b78-142">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="40b78-143">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="40b78-143">RELATED LINKS</span></span>

[<span data-ttu-id="40b78-144">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="40b78-144">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="40b78-145">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="40b78-145">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="40b78-146">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="40b78-146">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="40b78-147">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="40b78-147">Set-LocalGroup</span></span>](Set-LocalGroup.md)
