---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: 4c7de7a8ad3ae2a9e69cf4a00f9b9140a4294f4e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250724"
---
# <span data-ttu-id="e1b60-103">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="e1b60-103">Remove-CimSession</span></span>

## <span data-ttu-id="e1b60-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e1b60-104">SYNOPSIS</span></span>
<span data-ttu-id="e1b60-105">Hiermee verwijdert u een of meer CIM-sessies.</span><span class="sxs-lookup"><span data-stu-id="e1b60-105">Removes one or more CIM sessions.</span></span>

## <span data-ttu-id="e1b60-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e1b60-106">SYNTAX</span></span>

### <span data-ttu-id="e1b60-107">CimSessionSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="e1b60-107">CimSessionSet (Default)</span></span>

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b60-108">ComputerNameSet</span><span class="sxs-lookup"><span data-stu-id="e1b60-108">ComputerNameSet</span></span>

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b60-109">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="e1b60-109">SessionIdSet</span></span>

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b60-110">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="e1b60-110">InstanceIdSet</span></span>

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1b60-111">Naamset</span><span class="sxs-lookup"><span data-stu-id="e1b60-111">NameSet</span></span>

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e1b60-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e1b60-112">DESCRIPTION</span></span>

<span data-ttu-id="e1b60-113">`Remove-CimSession`Met de cmdlet worden een of meer CIM-sessie objecten uit de lokale Power shell-sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e1b60-113">The `Remove-CimSession` cmdlet removes one or more CIM session objects from the local PowerShell session.</span></span>

## <span data-ttu-id="e1b60-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e1b60-114">EXAMPLES</span></span>

### <span data-ttu-id="e1b60-115">Voor beeld 1: alle CIM-sessies verwijderen</span><span class="sxs-lookup"><span data-stu-id="e1b60-115">Example 1: Remove all the CIM sessions</span></span>

<span data-ttu-id="e1b60-116">In dit voor beeld worden alle beschik bare CIM-sessies op de lokale computer opgehaald met behulp van de cmdlet [Get-CimSession](Get-CimSession.md) en worden deze vervolgens verwijderd met behulp van `Remove-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="e1b60-116">This example retrieves all the available CIM sessions on the local computer using the [Get-CimSession](Get-CimSession.md) cmdlet, and then removes them using the `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

### <span data-ttu-id="e1b60-117">Voor beeld 2: een specifieke CIM-sessie verwijderen</span><span class="sxs-lookup"><span data-stu-id="e1b60-117">Example 2: Remove a specific CIM session</span></span>

<span data-ttu-id="e1b60-118">In dit voor beeld wordt de CIM-sessie met de **id-** waarde 5 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e1b60-118">This example removes the CIM session that has an **Id** value of 5.</span></span>

```powershell
Remove-CimSession -Id 5
```

### <span data-ttu-id="e1b60-119">Voor beeld 3: de lijst met te verwijderen CIM-sessies weer geven met behulp van de para meter WhatIf</span><span class="sxs-lookup"><span data-stu-id="e1b60-119">Example 3: Show the list of CIM sessions to remove by using the WhatIf parameter</span></span>

<span data-ttu-id="e1b60-120">In dit voor beeld wordt gebruikgemaakt van de algemene para meter **WhatIf** om op te geven dat de verwijdering niet moet worden uitgevoerd, maar alleen output wat er zou gebeuren als deze is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e1b60-120">This example uses the common parameter **WhatIf** to specify that the removal should not be done, but only output what would happen if it were done.</span></span>

```powershell
Remove-CimSession -Name a* -WhatIf
```

## <span data-ttu-id="e1b60-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1b60-121">PARAMETERS</span></span>

### <span data-ttu-id="e1b60-122">-CimSession</span><span class="sxs-lookup"><span data-stu-id="e1b60-122">-CimSession</span></span>

<span data-ttu-id="e1b60-123">Hiermee geeft u de sessie objecten op van de CIM-sessies die moeten worden gesloten.</span><span class="sxs-lookup"><span data-stu-id="e1b60-123">Specifies the session objects of the CIM sessions to close.</span></span>

<span data-ttu-id="e1b60-124">Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de [`New-CimSession`](New-CimSession.md) of cmdlets, maakt of ontvangt [`Get-CimSession`](Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="e1b60-124">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the [`New-CimSession`](New-CimSession.md) or [`Get-CimSession`](Get-CimSession.md) cmdlets.</span></span>
<span data-ttu-id="e1b60-125">Zie [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e1b60-125">For more information, see [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e1b60-126">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e1b60-126">-ComputerName</span></span>

<span data-ttu-id="e1b60-127">Hiermee geeft u een matrix met namen van computers op.</span><span class="sxs-lookup"><span data-stu-id="e1b60-127">Specifies an array of names of computers.</span></span> <span data-ttu-id="e1b60-128">Hiermee verwijdert u de sessies die verbinding maken met de opgegeven computers.</span><span class="sxs-lookup"><span data-stu-id="e1b60-128">Removes the sessions that connect to the specified computers.</span></span> <span data-ttu-id="e1b60-129">U kunt een Fully Qualified Domain Name (FQDN) of een NetBIOS-naam opgeven.</span><span class="sxs-lookup"><span data-stu-id="e1b60-129">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e1b60-130">-Id</span><span class="sxs-lookup"><span data-stu-id="e1b60-130">-Id</span></span>

<span data-ttu-id="e1b60-131">Hiermee geeft u de ID op van de CIM-sessie die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e1b60-131">Specifies the ID of the CIM session to remove.</span></span> <span data-ttu-id="e1b60-132">Geef een of meer Id's op, gescheiden door komma's, of gebruik de operator Range ( `..` ) om een reeks id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="e1b60-132">Specify one or more IDs separated by commas, or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="e1b60-133">Een **id** is een geheel getal dat de CIM-sessie in de huidige Power shell-sessie uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="e1b60-133">An **Id** is an integer that uniquely identifies the CIM session in the current PowerShell session.</span></span>

<span data-ttu-id="e1b60-134">Zie [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)voor meer informatie over de operator Range.</span><span class="sxs-lookup"><span data-stu-id="e1b60-134">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1b60-135">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="e1b60-135">-InstanceId</span></span>

<span data-ttu-id="e1b60-136">Hiermee geeft u de exemplaar-ID op van de CIM-sessie die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e1b60-136">Specifies the instance ID of the CIM session to remove.</span></span> <span data-ttu-id="e1b60-137">**InstanceId** is een GUID (Globally Unique Identifier) waarmee een CIM-sessie uniek wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="e1b60-137">**InstanceId** is a Globally Unique Identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="e1b60-138">De **InstanceId** is uniek, zelfs wanneer er meerdere sessies in Power shell worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e1b60-138">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="e1b60-139">De **InstanceId** wordt opgeslagen in de eigenschap **InstanceId** van het object dat een CIM-sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="e1b60-139">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1b60-140">-Name</span><span class="sxs-lookup"><span data-stu-id="e1b60-140">-Name</span></span>

<span data-ttu-id="e1b60-141">Hiermee geeft u de beschrijvende naam op van de CIM-sessie die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e1b60-141">Specifies the friendly name of the CIM session to remove.</span></span> <span data-ttu-id="e1b60-142">U kunt joker tekens gebruiken met deze para meter.</span><span class="sxs-lookup"><span data-stu-id="e1b60-142">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e1b60-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e1b60-143">-Confirm</span></span>

<span data-ttu-id="e1b60-144">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e1b60-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e1b60-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e1b60-145">-WhatIf</span></span>

<span data-ttu-id="e1b60-146">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e1b60-146">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e1b60-147">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e1b60-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e1b60-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1b60-148">CommonParameters</span></span>

<span data-ttu-id="e1b60-149">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e1b60-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1b60-150">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e1b60-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1b60-151">INVOER</span><span class="sxs-lookup"><span data-stu-id="e1b60-151">INPUTS</span></span>

### <span data-ttu-id="e1b60-152">Geen</span><span class="sxs-lookup"><span data-stu-id="e1b60-152">None</span></span>

<span data-ttu-id="e1b60-153">Deze cmdlet accepteert geen invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="e1b60-153">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="e1b60-154">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e1b60-154">OUTPUTS</span></span>

### <span data-ttu-id="e1b60-155">System. object</span><span class="sxs-lookup"><span data-stu-id="e1b60-155">System.Object</span></span>

<span data-ttu-id="e1b60-156">Met deze cmdlet wordt een object geretourneerd dat informatie over CIM-sessies bevat.</span><span class="sxs-lookup"><span data-stu-id="e1b60-156">This cmdlet returns an object that contains CIM session information.</span></span>

## <span data-ttu-id="e1b60-157">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e1b60-157">NOTES</span></span>

## <span data-ttu-id="e1b60-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e1b60-158">RELATED LINKS</span></span>

[<span data-ttu-id="e1b60-159">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="e1b60-159">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="e1b60-160">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="e1b60-160">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="e1b60-161">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="e1b60-161">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)
