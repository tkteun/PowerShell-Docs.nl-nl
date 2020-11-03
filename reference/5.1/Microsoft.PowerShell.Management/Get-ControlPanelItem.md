---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250810"
---
# <span data-ttu-id="cc620-103">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="cc620-103">Get-ControlPanelItem</span></span>

## <span data-ttu-id="cc620-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cc620-104">SYNOPSIS</span></span>
<span data-ttu-id="cc620-105">Hiermee worden de onderdelen van het configuratie scherm opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-105">Gets control panel items.</span></span>

## <span data-ttu-id="cc620-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cc620-106">SYNTAX</span></span>

### <span data-ttu-id="cc620-107">Regulierenaam (standaard)</span><span class="sxs-lookup"><span data-stu-id="cc620-107">RegularName (Default)</span></span>

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="cc620-108">Canoniekenaam</span><span class="sxs-lookup"><span data-stu-id="cc620-108">CanonicalName</span></span>

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="cc620-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cc620-109">DESCRIPTION</span></span>

<span data-ttu-id="cc620-110">`Get-ControlPanelItem`Met de cmdlet worden configuratie scherm-onderdelen op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-110">The `Get-ControlPanelItem` cmdlet gets control panel items on the local computer.</span></span> <span data-ttu-id="cc620-111">U kunt het gebruiken om de onderdelen van het configuratie scherm te vinden op naam, categorie of beschrijving, zelfs op systemen die geen gebruikers interface hebben.</span><span class="sxs-lookup"><span data-stu-id="cc620-111">You can use it to find control panel items by name, category, or description, even on systems that do not have a user interface.</span></span>

<span data-ttu-id="cc620-112">Met deze cmdlet worden alleen de onderdelen van het configuratie scherm opgehaald die op het systeem kunnen worden geopend.</span><span class="sxs-lookup"><span data-stu-id="cc620-112">This cmdlet gets only the control panel items that can be opened on the system.</span></span> <span data-ttu-id="cc620-113">Op computers die geen configuratie scherm of bestanden Verkenner hebben, worden met deze cmdlet alleen de onderdelen van het configuratie scherm weer gegeven die zonder deze onderdelen kunnen worden geopend.</span><span class="sxs-lookup"><span data-stu-id="cc620-113">On computers that do not have Control Panel or File Explorer, this cmdlet gets only control panel items that can open without these components.</span></span>

<span data-ttu-id="cc620-114">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc620-114">This cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="cc620-115">Het werkt alleen op Windows 8 en Windows Server 2012 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="cc620-115">It works only on Windows 8 and Windows Server 2012 and newer.</span></span>

## <span data-ttu-id="cc620-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cc620-116">EXAMPLES</span></span>

### <span data-ttu-id="cc620-117">Voor beeld 1: alle configuratie scherm-items ophalen</span><span class="sxs-lookup"><span data-stu-id="cc620-117">Example 1: Get all control panel items</span></span>

<span data-ttu-id="cc620-118">Met deze opdracht worden alle configuratie scherm-onderdelen op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-118">This command gets all control panel items on the local computer.</span></span>

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### <span data-ttu-id="cc620-119">Voor beeld 2: onderdelen van het configuratie scherm op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="cc620-119">Example 2: Get control panel items by name</span></span>

<span data-ttu-id="cc620-120">In dit voor beeld worden de onderdelen van het configuratie scherm met het programma of de app in hun naam opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-120">This example gets control panel items that have Program or App in their names.</span></span>

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### <span data-ttu-id="cc620-121">Voor beeld 3: onderdelen van het configuratie scherm op categorie ophalen</span><span class="sxs-lookup"><span data-stu-id="cc620-121">Example 3: Get control panel items by category</span></span>

<span data-ttu-id="cc620-122">Met deze opdracht worden alle configuratie scherm-items in categorieën met beveiliging in hun namen.</span><span class="sxs-lookup"><span data-stu-id="cc620-122">This command gets all control panel items in categories that have Security in their names.</span></span>

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### <span data-ttu-id="cc620-123">Voor beeld 4: een configuratie scherm-item openen</span><span class="sxs-lookup"><span data-stu-id="cc620-123">Example 4: Open a control panel item</span></span>

<span data-ttu-id="cc620-124">In dit voor beeld wordt het onderdeel Windows Firewall configuratie scherm op de lokale computer geopend.</span><span class="sxs-lookup"><span data-stu-id="cc620-124">This example opens the Windows Firewall control panel item on the local computer.</span></span>

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="cc620-125">`Get-ControlPanelItem`Met de cmdlet wordt het onderdeel van het configuratie scherm opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-125">The `Get-ControlPanelItem` cmdlet gets the control panel item.</span></span> <span data-ttu-id="cc620-126">De `Show-ControlPanelItem` cmdlet wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="cc620-126">The `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="cc620-127">Voor beeld 5: onderdelen van het configuratie scherm ophalen op een externe computer</span><span class="sxs-lookup"><span data-stu-id="cc620-127">Example 5: Get control panel items on a remote computer</span></span>

<span data-ttu-id="cc620-128">In dit voor beeld wordt het BitLocker-stationsversleuteling onderdeel van het configuratie scherm op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="cc620-128">This example gets the BitLocker Drive Encryption control panel item on the Server01 remote computer.</span></span>
<span data-ttu-id="cc620-129">De `Invoke-Command` cmdlet voert de `Get-ControlPanelItem` cmdlet op afstand uit.</span><span class="sxs-lookup"><span data-stu-id="cc620-129">The `Invoke-Command` cmdlet runs the `Get-ControlPanelItem` cmdlet remotely.</span></span>

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### <span data-ttu-id="cc620-130">Voor beeld 6: zoeken in de beschrijvingen van de onderdelen van het configuratie scherm</span><span class="sxs-lookup"><span data-stu-id="cc620-130">Example 6: Search the descriptions of control panel items</span></span>

<span data-ttu-id="cc620-131">In dit voor beeld wordt gezocht naar de eigenschap **Description** van de onderdelen van het configuratie scherm om alleen de eigenschappen te verkrijgen die het naam **apparaat** bevatten.</span><span class="sxs-lookup"><span data-stu-id="cc620-131">This example searches the **Description** property of the control panel items to get only those that contain the name **Device**.</span></span>

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

<span data-ttu-id="cc620-132">`Get-ControlPanelItem`Met de cmdlet worden alle configuratie scherm-items opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-132">The `Get-ControlPanelItem` cmdlet gets all control panel items.</span></span> <span data-ttu-id="cc620-133">`Where-Object`Met de cmdlet worden de items gefilterd op de waarde van de eigenschap **Description** .</span><span class="sxs-lookup"><span data-stu-id="cc620-133">The `Where-Object` cmdlet filters the items by the value of the **Description** property.</span></span>

## <span data-ttu-id="cc620-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cc620-134">PARAMETERS</span></span>

### <span data-ttu-id="cc620-135">-Canoniekenaam</span><span class="sxs-lookup"><span data-stu-id="cc620-135">-CanonicalName</span></span>

<span data-ttu-id="cc620-136">Hiermee geeft u als een teken reeks matrix de onderdelen van het configuratie scherm op basis van hun canonieke namen of naam patronen die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-136">Specifies, as a string array, the control panel items by their canonical names or name patterns that this cmdlet gets.</span></span> <span data-ttu-id="cc620-137">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="cc620-137">Wildcards are permitted.</span></span> <span data-ttu-id="cc620-138">Als u meerdere namen opgeeft, haalt deze cmdlet configuratie scherm-items die overeenkomen met een van de namen, alsof de items in de naam lijst zijn gescheiden door een ' or '-operator.</span><span class="sxs-lookup"><span data-stu-id="cc620-138">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span>

<span data-ttu-id="cc620-139">Met deze cmdlet worden standaard alle configuratie scherm-onderdelen in het systeem opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-139">By default, this cmdlet gets all control panel items in the system.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="cc620-140">-Categorie</span><span class="sxs-lookup"><span data-stu-id="cc620-140">-Category</span></span>

<span data-ttu-id="cc620-141">Hiermee geeft u als een teken reeks matrix de categorieën van de onderdelen van het configuratie scherm in de opgegeven categorieën op die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-141">Specifies, as a string array, the categories of the control panel items in the specified categories that this cmdlet gets.</span></span> <span data-ttu-id="cc620-142">Voer een categorie naam of naam patroon in.</span><span class="sxs-lookup"><span data-stu-id="cc620-142">Enter a category name or name pattern.</span></span> <span data-ttu-id="cc620-143">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="cc620-143">Wildcards are permitted.</span></span> <span data-ttu-id="cc620-144">Als u meerdere namen opgeeft, haalt deze cmdlet configuratie scherm-items die overeenkomen met een van de namen, alsof de items in de naam lijst zijn gescheiden door een ' or '-operator.</span><span class="sxs-lookup"><span data-stu-id="cc620-144">If you enter multiple names, this cmdlet gets control panel items that match any of the names, as though the items in the name list were separated by an "or" operator.</span></span> <span data-ttu-id="cc620-145">Met deze cmdlet worden standaard alle configuratie scherm-onderdelen in het systeem opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-145">By default, this cmdlet gets all control panel items in the system.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="cc620-146">-Name</span><span class="sxs-lookup"><span data-stu-id="cc620-146">-Name</span></span>

<span data-ttu-id="cc620-147">Hiermee geeft u als een teken reeks matrix de namen of naam patronen van het configuratie scherm die met deze cmdlet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-147">Specifies, as a string array, the names or name patterns of the control panel that this cmdlet gets.</span></span>
<span data-ttu-id="cc620-148">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="cc620-148">Wildcards are permitted.</span></span> <span data-ttu-id="cc620-149">U kunt ook een naam-of naam patroon door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc620-149">You can also pipe a name or name pattern to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="cc620-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cc620-150">CommonParameters</span></span>

<span data-ttu-id="cc620-151">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cc620-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cc620-152">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cc620-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cc620-153">INVOER</span><span class="sxs-lookup"><span data-stu-id="cc620-153">INPUTS</span></span>

### <span data-ttu-id="cc620-154">System. String</span><span class="sxs-lookup"><span data-stu-id="cc620-154">System.String</span></span>

<span data-ttu-id="cc620-155">U kunt een naam-of naam patroon door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc620-155">You can pipe a name or name pattern to this cmdlet.</span></span>

## <span data-ttu-id="cc620-156">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cc620-156">OUTPUTS</span></span>

### <span data-ttu-id="cc620-157">Micro soft. Power shell. commands. ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="cc620-157">Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="cc620-158">Met deze cmdlet worden configuratie scherm-onderdelen op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cc620-158">This cmdlet gets control panel items on the local computer.</span></span>

## <span data-ttu-id="cc620-159">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cc620-159">NOTES</span></span>

## <span data-ttu-id="cc620-160">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cc620-160">RELATED LINKS</span></span>

[<span data-ttu-id="cc620-161">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="cc620-161">Show-ControlPanelItem</span></span>](Show-ControlPanelItem.md)
