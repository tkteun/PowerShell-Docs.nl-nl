---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: a3ff2132c531df1ab19bf7149a55ea0df4a787a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705394"
---
# <span data-ttu-id="4fb22-102">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="4fb22-102">Remove-CimSession</span></span>

## <span data-ttu-id="4fb22-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4fb22-103">SYNOPSIS</span></span>
<span data-ttu-id="4fb22-104">Hiermee verwijdert u een of meer CIM-sessies.</span><span class="sxs-lookup"><span data-stu-id="4fb22-104">Removes one or more CIM sessions.</span></span>

## <span data-ttu-id="4fb22-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4fb22-105">SYNTAX</span></span>

### <span data-ttu-id="4fb22-106">CimSessionSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="4fb22-106">CimSessionSet (Default)</span></span>

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4fb22-107">ComputerNameSet</span><span class="sxs-lookup"><span data-stu-id="4fb22-107">ComputerNameSet</span></span>

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4fb22-108">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="4fb22-108">SessionIdSet</span></span>

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4fb22-109">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="4fb22-109">InstanceIdSet</span></span>

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4fb22-110">Naamset</span><span class="sxs-lookup"><span data-stu-id="4fb22-110">NameSet</span></span>

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4fb22-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4fb22-111">DESCRIPTION</span></span>

<span data-ttu-id="4fb22-112">`Remove-CimSession`Met de cmdlet worden een of meer CIM-sessie objecten uit de lokale Power shell-sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4fb22-112">The `Remove-CimSession` cmdlet removes one or more CIM session objects from the local PowerShell session.</span></span>

## <span data-ttu-id="4fb22-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4fb22-113">EXAMPLES</span></span>

### <span data-ttu-id="4fb22-114">Voor beeld 1: alle CIM-sessies verwijderen</span><span class="sxs-lookup"><span data-stu-id="4fb22-114">Example 1: Remove all the CIM sessions</span></span>

<span data-ttu-id="4fb22-115">In dit voor beeld worden alle beschik bare CIM-sessies op de lokale computer opgehaald met behulp van de cmdlet [Get-CimSession](Get-CimSession.md) en worden deze vervolgens verwijderd met behulp van `Remove-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="4fb22-115">This example retrieves all the available CIM sessions on the local computer using the [Get-CimSession](Get-CimSession.md) cmdlet, and then removes them using the `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

### <span data-ttu-id="4fb22-116">Voor beeld 2: een specifieke CIM-sessie verwijderen</span><span class="sxs-lookup"><span data-stu-id="4fb22-116">Example 2: Remove a specific CIM session</span></span>

<span data-ttu-id="4fb22-117">In dit voor beeld wordt de CIM-sessie met de **id-** waarde 5 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4fb22-117">This example removes the CIM session that has an **Id** value of 5.</span></span>

```powershell
Remove-CimSession -Id 5
```

### <span data-ttu-id="4fb22-118">Voor beeld 3: de lijst met te verwijderen CIM-sessies weer geven met behulp van de para meter WhatIf</span><span class="sxs-lookup"><span data-stu-id="4fb22-118">Example 3: Show the list of CIM sessions to remove by using the WhatIf parameter</span></span>

<span data-ttu-id="4fb22-119">In dit voor beeld wordt gebruikgemaakt van de algemene para meter **WhatIf** om op te geven dat de verwijdering niet moet worden uitgevoerd, maar alleen output wat er zou gebeuren als deze is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4fb22-119">This example uses the common parameter **WhatIf** to specify that the removal should not be done, but only output what would happen if it were done.</span></span>

```powershell
Remove-CimSession -Name a* -WhatIf
```

## <span data-ttu-id="4fb22-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4fb22-120">PARAMETERS</span></span>

### <span data-ttu-id="4fb22-121">-CimSession</span><span class="sxs-lookup"><span data-stu-id="4fb22-121">-CimSession</span></span>

<span data-ttu-id="4fb22-122">Hiermee geeft u de sessie objecten op van de CIM-sessies die moeten worden gesloten.</span><span class="sxs-lookup"><span data-stu-id="4fb22-122">Specifies the session objects of the CIM sessions to close.</span></span>

<span data-ttu-id="4fb22-123">Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de [`New-CimSession`](New-CimSession.md) of cmdlets, maakt of ontvangt [`Get-CimSession`](Get-CimSession.md) .</span><span class="sxs-lookup"><span data-stu-id="4fb22-123">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the [`New-CimSession`](New-CimSession.md) or [`Get-CimSession`](Get-CimSession.md) cmdlets.</span></span>
<span data-ttu-id="4fb22-124">Zie [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4fb22-124">For more information, see [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="4fb22-125">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4fb22-125">-ComputerName</span></span>

<span data-ttu-id="4fb22-126">Hiermee geeft u een matrix met namen van computers op.</span><span class="sxs-lookup"><span data-stu-id="4fb22-126">Specifies an array of names of computers.</span></span> <span data-ttu-id="4fb22-127">Hiermee verwijdert u de sessies die verbinding maken met de opgegeven computers.</span><span class="sxs-lookup"><span data-stu-id="4fb22-127">Removes the sessions that connect to the specified computers.</span></span> <span data-ttu-id="4fb22-128">U kunt een Fully Qualified Domain Name (FQDN) of een NetBIOS-naam opgeven.</span><span class="sxs-lookup"><span data-stu-id="4fb22-128">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

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

### <span data-ttu-id="4fb22-129">-Id</span><span class="sxs-lookup"><span data-stu-id="4fb22-129">-Id</span></span>

<span data-ttu-id="4fb22-130">Hiermee geeft u de ID op van de CIM-sessie die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="4fb22-130">Specifies the ID of the CIM session to remove.</span></span> <span data-ttu-id="4fb22-131">Geef een of meer Id's op, gescheiden door komma's, of gebruik de operator Range ( `..` ) om een reeks id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="4fb22-131">Specify one or more IDs separated by commas, or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="4fb22-132">Een **id** is een geheel getal dat de CIM-sessie in de huidige Power shell-sessie uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="4fb22-132">An **Id** is an integer that uniquely identifies the CIM session in the current PowerShell session.</span></span>

<span data-ttu-id="4fb22-133">Zie [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)voor meer informatie over de operator Range.</span><span class="sxs-lookup"><span data-stu-id="4fb22-133">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

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

### <span data-ttu-id="4fb22-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="4fb22-134">-InstanceId</span></span>

<span data-ttu-id="4fb22-135">Hiermee geeft u de exemplaar-ID op van de CIM-sessie die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="4fb22-135">Specifies the instance ID of the CIM session to remove.</span></span> <span data-ttu-id="4fb22-136">**InstanceId** is een GUID (Globally Unique Identifier) waarmee een CIM-sessie uniek wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="4fb22-136">**InstanceId** is a Globally Unique Identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="4fb22-137">De **InstanceId** is uniek, zelfs wanneer er meerdere sessies in Power shell worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4fb22-137">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="4fb22-138">De **InstanceId** wordt opgeslagen in de eigenschap **InstanceId** van het object dat een CIM-sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4fb22-138">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

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

### <span data-ttu-id="4fb22-139">-Name</span><span class="sxs-lookup"><span data-stu-id="4fb22-139">-Name</span></span>

<span data-ttu-id="4fb22-140">Hiermee geeft u de beschrijvende naam op van de CIM-sessie die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="4fb22-140">Specifies the friendly name of the CIM session to remove.</span></span> <span data-ttu-id="4fb22-141">U kunt joker tekens gebruiken met deze para meter.</span><span class="sxs-lookup"><span data-stu-id="4fb22-141">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="4fb22-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4fb22-142">-Confirm</span></span>

<span data-ttu-id="4fb22-143">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4fb22-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4fb22-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4fb22-144">-WhatIf</span></span>

<span data-ttu-id="4fb22-145">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4fb22-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4fb22-146">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4fb22-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4fb22-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4fb22-147">CommonParameters</span></span>

<span data-ttu-id="4fb22-148">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4fb22-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4fb22-149">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4fb22-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4fb22-150">INVOER</span><span class="sxs-lookup"><span data-stu-id="4fb22-150">INPUTS</span></span>

### <span data-ttu-id="4fb22-151">Geen</span><span class="sxs-lookup"><span data-stu-id="4fb22-151">None</span></span>

<span data-ttu-id="4fb22-152">Deze cmdlet accepteert geen invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="4fb22-152">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="4fb22-153">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4fb22-153">OUTPUTS</span></span>

### <span data-ttu-id="4fb22-154">System. object</span><span class="sxs-lookup"><span data-stu-id="4fb22-154">System.Object</span></span>

<span data-ttu-id="4fb22-155">Met deze cmdlet wordt een object geretourneerd dat informatie over CIM-sessies bevat.</span><span class="sxs-lookup"><span data-stu-id="4fb22-155">This cmdlet returns an object that contains CIM session information.</span></span>

## <span data-ttu-id="4fb22-156">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4fb22-156">NOTES</span></span>

## <span data-ttu-id="4fb22-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4fb22-157">RELATED LINKS</span></span>

[<span data-ttu-id="4fb22-158">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="4fb22-158">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="4fb22-159">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="4fb22-159">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="4fb22-160">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="4fb22-160">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)

