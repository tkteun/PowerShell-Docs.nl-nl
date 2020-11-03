---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroup
ms.openlocfilehash: 2cd77c2766840527825b0ccf68abaac3c2ea6c16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249927"
---
# <span data-ttu-id="73492-103">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="73492-103">Get-LocalGroup</span></span>

## <span data-ttu-id="73492-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="73492-104">SYNOPSIS</span></span>
<span data-ttu-id="73492-105">Hiermee haalt u de lokale beveiligings groepen op.</span><span class="sxs-lookup"><span data-stu-id="73492-105">Gets the local security groups.</span></span>

## <span data-ttu-id="73492-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="73492-106">SYNTAX</span></span>

### <span data-ttu-id="73492-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="73492-107">Default (Default)</span></span>

```
Get-LocalGroup [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="73492-108">Behoren</span><span class="sxs-lookup"><span data-stu-id="73492-108">SecurityIdentifier</span></span>

```
Get-LocalGroup [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="73492-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="73492-109">DESCRIPTION</span></span>
<span data-ttu-id="73492-110">Met de cmdlet **Get-LocalGroup** worden lokale beveiligings groepen in de SAM-account opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73492-110">The **Get-LocalGroup** cmdlet gets local security groups in Security Account Manager.</span></span>
<span data-ttu-id="73492-111">Met deze cmdlet worden standaard ingebouwde groepen en lokale beveiligings groepen opgehaald die u maakt.</span><span class="sxs-lookup"><span data-stu-id="73492-111">This cmdlet gets default built-in groups and local security groups that you create.</span></span>

> [!NOTE]
> <span data-ttu-id="73492-112">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="73492-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="73492-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="73492-113">EXAMPLES</span></span>

### <span data-ttu-id="73492-114">Voor beeld 1: de groep Administrators ophalen</span><span class="sxs-lookup"><span data-stu-id="73492-114">Example 1: Get the Administrators group</span></span>

```
PS C:\> Get-LocalGroup -Name "Administrators"
Name           Description
----           -----------
Administrators Administrators have complete and unrestricted access to the computer/domain
```

<span data-ttu-id="73492-115">Met deze opdracht wordt de lokale groep Administrators opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73492-115">This command gets the local Administrators group.</span></span>
<span data-ttu-id="73492-116">Met de opdracht worden de eigenschappen van de groep in de-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="73492-116">The command displays properties of the group in the console.</span></span>

## <span data-ttu-id="73492-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73492-117">PARAMETERS</span></span>

### <span data-ttu-id="73492-118">-Name</span><span class="sxs-lookup"><span data-stu-id="73492-118">-Name</span></span>
<span data-ttu-id="73492-119">Hiermee geeft u een matrix met namen van beveiligings groepen op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73492-119">Specifies an array of names of security groups that this cmdlet gets.</span></span>
<span data-ttu-id="73492-120">U kunt het Joker teken gebruiken.</span><span class="sxs-lookup"><span data-stu-id="73492-120">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="73492-121">-SID</span><span class="sxs-lookup"><span data-stu-id="73492-121">-SID</span></span>
<span data-ttu-id="73492-122">Hiermee geeft u een matrix met beveiligings-Id's (Sid's) op van beveiligings groepen die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73492-122">Specifies an array of security IDs (SIDs) of security groups that this cmdlet gets.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="73492-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73492-123">CommonParameters</span></span>
<span data-ttu-id="73492-124">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73492-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73492-125">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73492-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73492-126">INVOER</span><span class="sxs-lookup"><span data-stu-id="73492-126">INPUTS</span></span>

### <span data-ttu-id="73492-127">System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="73492-127">System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="73492-128">U kunt een teken reeks of SID door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="73492-128">You can pipe a string or a SID to this cmdlet.</span></span>

## <span data-ttu-id="73492-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="73492-129">OUTPUTS</span></span>

### <span data-ttu-id="73492-130">System. Management. Automation. SecurityAccountsManager. LocalGroup</span><span class="sxs-lookup"><span data-stu-id="73492-130">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="73492-131">Met deze cmdlet wordt een lokale groep geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="73492-131">This cmdlet returns a local group.</span></span>

## <span data-ttu-id="73492-132">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="73492-132">NOTES</span></span>

* <span data-ttu-id="73492-133">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="73492-133">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="73492-134">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="73492-134">The possible sources are as follows:</span></span>

- <span data-ttu-id="73492-135">Lokaal</span><span class="sxs-lookup"><span data-stu-id="73492-135">Local</span></span>
- <span data-ttu-id="73492-136">Active Directory</span><span class="sxs-lookup"><span data-stu-id="73492-136">Active Directory</span></span>
- <span data-ttu-id="73492-137">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="73492-137">Azure Active Directory group</span></span>
- <span data-ttu-id="73492-138">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="73492-138">Microsoft Account</span></span>

<span data-ttu-id="73492-139">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="73492-139">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="73492-140">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="73492-140">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="73492-141">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="73492-141">RELATED LINKS</span></span>

[<span data-ttu-id="73492-142">Nieuw-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="73492-142">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="73492-143">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="73492-143">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="73492-144">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="73492-144">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="73492-145">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="73492-145">Set-LocalGroup</span></span>](Set-LocalGroup.md)
