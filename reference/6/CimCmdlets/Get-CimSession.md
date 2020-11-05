---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: c40367d0458c3670b9d684cd0c3b4b2a3631b3e4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250731"
---
# <span data-ttu-id="7d582-103">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="7d582-103">Get-CimSession</span></span>

## <span data-ttu-id="7d582-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7d582-104">SYNOPSIS</span></span>
<span data-ttu-id="7d582-105">Hiermee haalt u de CIM-sessie objecten op uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="7d582-105">Gets the CIM session objects from the current session.</span></span>

## <span data-ttu-id="7d582-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7d582-106">SYNTAX</span></span>

### <span data-ttu-id="7d582-107">ComputerNameSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="7d582-107">ComputerNameSet (Default)</span></span>

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="7d582-108">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="7d582-108">SessionIdSet</span></span>

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### <span data-ttu-id="7d582-109">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="7d582-109">InstanceIdSet</span></span>

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="7d582-110">Naamset</span><span class="sxs-lookup"><span data-stu-id="7d582-110">NameSet</span></span>

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## <span data-ttu-id="7d582-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7d582-111">DESCRIPTION</span></span>

<span data-ttu-id="7d582-112">Standaard worden alle CIM-sessies die zijn gemaakt in de huidige Power shell-sessie door de cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7d582-112">By default, the cmdlet gets all of the CIM sessions created in the current PowerShell session.</span></span> <span data-ttu-id="7d582-113">U kunt de para meters van gebruiken `Get-CimSession` om de sessies op te halen voor bepaalde computers, of u kunt sessies identificeren met hun namen of andere id's.</span><span class="sxs-lookup"><span data-stu-id="7d582-113">You can use the parameters of `Get-CimSession` to get the sessions that are for particular computers, or you can identify sessions by their names or other identifiers.</span></span> <span data-ttu-id="7d582-114">`Get-CimSession` ontvangt geen CIM-sessies die zijn gemaakt in andere Power shell-sessies of die zijn gemaakt op andere computers.</span><span class="sxs-lookup"><span data-stu-id="7d582-114">`Get-CimSession` does not get CIM sessions that were created in other PowerShell sessions or that were created on other computers.</span></span>

<span data-ttu-id="7d582-115">Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie over CIM-sessies.</span><span class="sxs-lookup"><span data-stu-id="7d582-115">For more information about CIM sessions, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

## <span data-ttu-id="7d582-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7d582-116">EXAMPLES</span></span>

### <span data-ttu-id="7d582-117">Voor beeld 1: CIM-sessies ophalen uit de huidige Power shell-sessie</span><span class="sxs-lookup"><span data-stu-id="7d582-117">Example 1: Get CIM sessions from the current PowerShell session</span></span>

<span data-ttu-id="7d582-118">In dit voor beeld worden CIM-sessies gemaakt met [New-CimSession](New-CimSession.md)en worden vervolgens de CIM-sessies opgehaald met `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="7d582-118">This example creates CIM sessions using [New-CimSession](New-CimSession.md), and then gets the CIM sessions using `Get-CimSession`.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="7d582-119">Voor beeld 2: de CIM-sessies op een specifieke computer ophalen</span><span class="sxs-lookup"><span data-stu-id="7d582-119">Example 2: Get the CIM sessions to a specific computer</span></span>

<span data-ttu-id="7d582-120">In dit voor beeld worden de CIM-sessies opgehaald die zijn verbonden met de computer met de naam **Server02**.</span><span class="sxs-lookup"><span data-stu-id="7d582-120">This example gets the CIM sessions that are connected to the computer named **Server02**.</span></span>

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="7d582-121">Voor beeld 3: een lijst met CIM-sessies ophalen en vervolgens de lijst opmaken</span><span class="sxs-lookup"><span data-stu-id="7d582-121">Example 3: Get a list of CIM sessions and then format the list</span></span>

<span data-ttu-id="7d582-122">In dit voor beeld worden alle CIM-sessies in de huidige Power shell-sessie opgehaald en wordt een tabel met alleen de eigenschappen **ComputerName** en **InstanceId** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7d582-122">This example gets all CIM sessions in the current PowerShell session and displays a table containing only the **ComputerName** and **InstanceID** properties.</span></span>

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### <span data-ttu-id="7d582-123">Voor beeld 4: alle CIM-sessies met specifieke namen ophalen</span><span class="sxs-lookup"><span data-stu-id="7d582-123">Example 4: Get all the CIM sessions that have specific names</span></span>

<span data-ttu-id="7d582-124">In dit voor beeld worden alle CIM-sessies opgehaald die namen hebben die met **Serviceart** beginnen.</span><span class="sxs-lookup"><span data-stu-id="7d582-124">This example gets all CIM sessions that have names that begin with **serv**.</span></span>

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="7d582-125">Voor beeld 5: een specifieke CIM-sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="7d582-125">Example 5: Get a specific CIM session</span></span>

<span data-ttu-id="7d582-126">In dit voor beeld wordt de CIM-sessie met de **id** 2 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7d582-126">This example gets the CIM session that has an **Id** of 2.</span></span>

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## <span data-ttu-id="7d582-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7d582-127">PARAMETERS</span></span>

### <span data-ttu-id="7d582-128">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="7d582-128">-ComputerName</span></span>

<span data-ttu-id="7d582-129">Hiermee geeft u de naam op van de computer waarop CIM-sessies moeten worden aangesloten.</span><span class="sxs-lookup"><span data-stu-id="7d582-129">Specifies the name of the computer to get CIM sessions connected to.</span></span> <span data-ttu-id="7d582-130">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7d582-130">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="7d582-131">-Id</span><span class="sxs-lookup"><span data-stu-id="7d582-131">-Id</span></span>

<span data-ttu-id="7d582-132">Hiermee geeft u de id op van de CIM-sessie die u wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="7d582-132">Specifies the identifier of the CIM session to get.</span></span> <span data-ttu-id="7d582-133">Voor meerdere Id's gebruikt u komma's om de Id's van elkaar te scheiden of gebruikt u de operator Range ( `..` ) om een reeks id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="7d582-133">For multiple IDs, use commas to separate the IDs or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="7d582-134">Een **id** is een geheel getal dat de CIM-sessie in de huidige Power shell-sessie uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="7d582-134">An **Id** is an integer that uniquely identifies the CIM session within the current PowerShell session.</span></span>

<span data-ttu-id="7d582-135">Zie [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)voor meer informatie over de operator Range.</span><span class="sxs-lookup"><span data-stu-id="7d582-135">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

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

### <span data-ttu-id="7d582-136">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="7d582-136">-InstanceId</span></span>

<span data-ttu-id="7d582-137">Hiermee geeft u de exemplaar-Id's op van de CIM-sessie die u wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="7d582-137">Specifies the instance IDs of the CIM session to get.</span></span>

<span data-ttu-id="7d582-138">**InstanceId** is een GUID (Globally Unique Identifier) waarmee een CIM-sessie uniek wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="7d582-138">**InstanceId** is a globally-unique identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="7d582-139">De **InstanceId** is uniek, zelfs wanneer er meerdere sessies in Power shell worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7d582-139">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="7d582-140">De **InstanceId** wordt opgeslagen in de eigenschap **InstanceId** van het object dat een CIM-sessie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="7d582-140">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

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

### <span data-ttu-id="7d582-141">-Name</span><span class="sxs-lookup"><span data-stu-id="7d582-141">-Name</span></span>

<span data-ttu-id="7d582-142">Hiermee worden een of meer CIM-sessies opgehaald die de opgegeven beschrijvende namen bevatten.</span><span class="sxs-lookup"><span data-stu-id="7d582-142">Gets one or more CIM sessions which contain the specified friendly names.</span></span> <span data-ttu-id="7d582-143">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7d582-143">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="7d582-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7d582-144">CommonParameters</span></span>
<span data-ttu-id="7d582-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7d582-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7d582-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7d582-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7d582-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="7d582-147">INPUTS</span></span>

### <span data-ttu-id="7d582-148">Geen</span><span class="sxs-lookup"><span data-stu-id="7d582-148">None</span></span>

## <span data-ttu-id="7d582-149">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7d582-149">OUTPUTS</span></span>

### <span data-ttu-id="7d582-150">Micro soft. Management. Infrastructure. CimSession</span><span class="sxs-lookup"><span data-stu-id="7d582-150">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="7d582-151">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7d582-151">NOTES</span></span>

## <span data-ttu-id="7d582-152">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7d582-152">RELATED LINKS</span></span>

[<span data-ttu-id="7d582-153">Format-Table</span><span class="sxs-lookup"><span data-stu-id="7d582-153">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="7d582-154">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="7d582-154">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="7d582-155">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="7d582-155">Remove-CimSession</span></span>](remove-cimsession.md)

[<span data-ttu-id="7d582-156">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="7d582-156">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)