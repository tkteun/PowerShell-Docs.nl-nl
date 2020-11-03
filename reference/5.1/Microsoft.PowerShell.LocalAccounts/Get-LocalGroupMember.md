---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroupMember
ms.openlocfilehash: 200368c5d13bd027302ad824533e6c187906ed0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249924"
---
# <span data-ttu-id="8dfb9-103">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="8dfb9-103">Get-LocalGroupMember</span></span>

## <span data-ttu-id="8dfb9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8dfb9-104">SYNOPSIS</span></span>
<span data-ttu-id="8dfb9-105">Hiermee worden leden opgehaald uit een lokale groep.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-105">Gets members from a local group.</span></span>

## <span data-ttu-id="8dfb9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8dfb9-106">SYNTAX</span></span>

### <span data-ttu-id="8dfb9-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="8dfb9-107">Default (Default)</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-Name] <String> [<CommonParameters>]
```

### <span data-ttu-id="8dfb9-108">Groep</span><span class="sxs-lookup"><span data-stu-id="8dfb9-108">Group</span></span>

```
Get-LocalGroupMember [-Group] <LocalGroup> [[-Member] <String>] [<CommonParameters>]
```

### <span data-ttu-id="8dfb9-109">Behoren</span><span class="sxs-lookup"><span data-stu-id="8dfb9-109">SecurityIdentifier</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-SID] <SecurityIdentifier> [<CommonParameters>]
```

## <span data-ttu-id="8dfb9-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8dfb9-110">DESCRIPTION</span></span>
<span data-ttu-id="8dfb9-111">De cmdlet **Get-LocalGroupMember** krijgt leden van een lokale groep.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-111">The **Get-LocalGroupMember** cmdlet gets members from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="8dfb9-112">De module micro soft. Power shell. LocalAccounts is niet beschikbaar in 32-bits Power shell op een 64-bits systeem.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="8dfb9-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8dfb9-113">EXAMPLES</span></span>

### <span data-ttu-id="8dfb9-114">Voor beeld 1: alle leden van de groep Administrators ophalen</span><span class="sxs-lookup"><span data-stu-id="8dfb9-114">Example 1: Get all members of the Administrators group</span></span>

```
PS C:\> Get-LocalGroupMember -Group "Administrators"
ObjectClass Name                    PrincipalSource
----------- ----                    ---------------
User        CONTOSOPC\Administrator Local
User        CONTOSOPC\LocalAdmin    Local
```

<span data-ttu-id="8dfb9-115">Met deze opdracht worden alle leden van de lokale groep Administrators opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-115">This command gets all the members of the local Administrators group.</span></span>

## <span data-ttu-id="8dfb9-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8dfb9-116">PARAMETERS</span></span>

### <span data-ttu-id="8dfb9-117">-Group</span><span class="sxs-lookup"><span data-stu-id="8dfb9-117">-Group</span></span>
<span data-ttu-id="8dfb9-118">Hiermee geeft u de beveiligings groep op waarvan deze cmdlet leden ophaalt.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-118">Specifies the security group from which this cmdlet gets members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8dfb9-119">-Lid</span><span class="sxs-lookup"><span data-stu-id="8dfb9-119">-Member</span></span>
<span data-ttu-id="8dfb9-120">Hiermee geeft u een gebruiker of groep op die met deze cmdlet wordt opgehaald van een beveiligings groep.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-120">Specifies a user or group that this cmdlet gets from a security group.</span></span>
<span data-ttu-id="8dfb9-121">U kunt gebruikers of groepen opgeven op naam of beveiligings-ID (SID).</span><span class="sxs-lookup"><span data-stu-id="8dfb9-121">You can specify users or groups by name or security ID (SID).</span></span>
<span data-ttu-id="8dfb9-122">Geef SID-teken reeksen op in S-R-I-S-S.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-122">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="8dfb9-123">.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-123">.</span></span> <span data-ttu-id="8dfb9-124">.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-124">.</span></span>
<span data-ttu-id="8dfb9-125">als indeling.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-125">format.</span></span>
<span data-ttu-id="8dfb9-126">U kunt joker tekens gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-126">You can use wildcard characters.</span></span>
<span data-ttu-id="8dfb9-127">Als u deze para meter niet opgeeft, haalt de cmdlet alle leden van de groep op.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-127">If you do not specify this parameter, the cmdlet gets all members of the group.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8dfb9-128">-Name</span><span class="sxs-lookup"><span data-stu-id="8dfb9-128">-Name</span></span>
<span data-ttu-id="8dfb9-129">Hiermee geeft u de naam van de beveiligings groep op waarvan deze cmdlet leden ophaalt.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-129">Specifies the name of the security group from which this cmdlet gets members.</span></span>

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

### <span data-ttu-id="8dfb9-130">-SID</span><span class="sxs-lookup"><span data-stu-id="8dfb9-130">-SID</span></span>
<span data-ttu-id="8dfb9-131">Hiermee geeft u de beveiligings-ID op van de beveiligings groep waarvan de cmdlet leden ophaalt.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-131">Specifies the security ID of the security group from which this cmdlet gets members.</span></span>

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

### <span data-ttu-id="8dfb9-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8dfb9-132">CommonParameters</span></span>
<span data-ttu-id="8dfb9-133">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8dfb9-134">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8dfb9-135">INVOER</span><span class="sxs-lookup"><span data-stu-id="8dfb9-135">INPUTS</span></span>

### <span data-ttu-id="8dfb9-136">System. Management. Automation. SecurityAccountsManager. LocalGroup, System. String, System. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="8dfb9-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="8dfb9-137">U kunt een lokale groep, een teken reeks of een SID door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-137">You can pipe a local group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="8dfb9-138">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8dfb9-138">OUTPUTS</span></span>

### <span data-ttu-id="8dfb9-139">Micro soft. SecurityAccountsManager. LocalPrincipal</span><span class="sxs-lookup"><span data-stu-id="8dfb9-139">Microsoft.SecurityAccountsManager.LocalPrincipal</span></span>
<span data-ttu-id="8dfb9-140">Met deze cmdlet worden lokale principals geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-140">This cmdlet returns local principals.</span></span>

## <span data-ttu-id="8dfb9-141">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8dfb9-141">NOTES</span></span>

* <span data-ttu-id="8dfb9-142">De eigenschap **PrincipalSource** is een eigenschap van de objecten **lokalegebruiker** , **LocalGroup** en **LocalPrincipal** waarmee de bron van het object wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="8dfb9-143">De mogelijke bronnen zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="8dfb9-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="8dfb9-144">Lokaal</span><span class="sxs-lookup"><span data-stu-id="8dfb9-144">Local</span></span>
- <span data-ttu-id="8dfb9-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="8dfb9-145">Active Directory</span></span>
- <span data-ttu-id="8dfb9-146">Azure Active Directory-groep</span><span class="sxs-lookup"><span data-stu-id="8dfb9-146">Azure Active Directory group</span></span>
- <span data-ttu-id="8dfb9-147">Microsoft-account</span><span class="sxs-lookup"><span data-stu-id="8dfb9-147">Microsoft Account</span></span>

<span data-ttu-id="8dfb9-148">**PrincipalSource** wordt alleen ondersteund door Windows 10, windows server 2016 en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="8dfb9-149">De eigenschap is leeg voor eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="8dfb9-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="8dfb9-150">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8dfb9-150">RELATED LINKS</span></span>

[<span data-ttu-id="8dfb9-151">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="8dfb9-151">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="8dfb9-152">Nieuw-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="8dfb9-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="8dfb9-153">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="8dfb9-153">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
