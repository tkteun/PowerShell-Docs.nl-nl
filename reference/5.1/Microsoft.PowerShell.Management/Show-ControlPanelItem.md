---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250544"
---
# <span data-ttu-id="ab8a2-103">Show-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="ab8a2-103">Show-ControlPanelItem</span></span>

## <span data-ttu-id="ab8a2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ab8a2-104">SYNOPSIS</span></span>
<span data-ttu-id="ab8a2-105">Hiermee opent u configuratie scherm-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-105">Opens control panel items.</span></span>

## <span data-ttu-id="ab8a2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ab8a2-106">SYNTAX</span></span>

### <span data-ttu-id="ab8a2-107">Regulierenaam (standaard)</span><span class="sxs-lookup"><span data-stu-id="ab8a2-107">RegularName (Default)</span></span>

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="ab8a2-108">Canoniekenaam</span><span class="sxs-lookup"><span data-stu-id="ab8a2-108">CanonicalName</span></span>

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="ab8a2-109">ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="ab8a2-109">ControlPanelItem</span></span>

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## <span data-ttu-id="ab8a2-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ab8a2-110">DESCRIPTION</span></span>

<span data-ttu-id="ab8a2-111">Met de cmdlet worden de `Show-ControlPanelItem` onderdelen van het configuratie scherm op de lokale computer geopend.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-111">The `Show-ControlPanelItem` cmdlet opens control panel items on the local computer.</span></span> <span data-ttu-id="ab8a2-112">U kunt het gebruiken om de onderdelen van het configuratie scherm te openen op naam, categorie of beschrijving, zelfs op systemen die geen gebruikers interface hebben.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-112">You can use it to open control panel items by name, category, or description, even on systems that do not have a user interface.</span></span> <span data-ttu-id="ab8a2-113">U kunt de onderdelen van het configuratie scherm van de `Get-ControlPanelItem` cmdlet naar gebruiken `Show-ControlPanelItem` .</span><span class="sxs-lookup"><span data-stu-id="ab8a2-113">You can pipe control panel items from the `Get-ControlPanelItem` cmdlet to `Show-ControlPanelItem`.</span></span>

<span data-ttu-id="ab8a2-114">`Show-ControlPanelItem` doorzoekt alleen configuratie scherm-items die kunnen worden geopend op het systeem.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-114">`Show-ControlPanelItem` searches only control panel items that can be opened on the system.</span></span> <span data-ttu-id="ab8a2-115">Op computers die geen **configuratie scherm** of **bestanden Verkenner** hebben, worden `Show-ControlPanelItem` alleen de configuratie scherm-items die zonder deze onderdelen kunnen worden geopend, doorzocht.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-115">On computers that do not have **Control Panel** or **File Explorer** , `Show-ControlPanelItem` searches only control panel items that can open without these components.</span></span>

<span data-ttu-id="ab8a2-116">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0 en werkt onder Windows 8, Windows Server 2012 en hogere versies.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-116">This cmdlet was introduced in Windows PowerShell 3.0 and works on Windows 8, Windows Server 2012, and higher versions.</span></span>

## <span data-ttu-id="ab8a2-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ab8a2-117">EXAMPLES</span></span>

### <span data-ttu-id="ab8a2-118">Voor beeld 1: een onderdeel van het configuratie scherm weer geven</span><span class="sxs-lookup"><span data-stu-id="ab8a2-118">Example 1: Show a control panel item</span></span>

<span data-ttu-id="ab8a2-119">In dit voor beeld wordt het onderdeel **AutoPlay** van het configuratie scherm gestart.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-119">This example launches the **AutoPlay** control panel item.</span></span>

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### <span data-ttu-id="ab8a2-120">Voor beeld 2: een item van het configuratie scherm naar deze cmdlet Pipeen</span><span class="sxs-lookup"><span data-stu-id="ab8a2-120">Example 2: Pipe a control panel item to this cmdlet</span></span>

<span data-ttu-id="ab8a2-121">In dit voor beeld wordt het onderdeel **Windows Defender firewall** -configuratie scherm op de lokale computer geopend.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-121">This example opens the **Windows Defender Firewall** control panel item on the local computer.</span></span>
<span data-ttu-id="ab8a2-122">De naam van het onderdeel Windows Firewall configuratie scherm is gewijzigd via de Windows-versies.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-122">The name of the Windows Firewall control panel item has changed over the versions of Windows.</span></span> <span data-ttu-id="ab8a2-123">In dit voor beeld wordt een Joker patroon gebruikt om het onderdeel van het configuratie scherm te vinden.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-123">This example uses a wildcard pattern to find the control panel item.</span></span>

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

<span data-ttu-id="ab8a2-124">`Get-ControlPanelItem` Hiermee wordt het onderdeel van het configuratie scherm opgehaald en de `Show-ControlPanelItem` cmdlet wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-124">`Get-ControlPanelItem` gets the control panel item and the `Show-ControlPanelItem` cmdlet opens it.</span></span>

### <span data-ttu-id="ab8a2-125">Voor beeld 3: een bestands naam gebruiken om een onderdeel van het configuratie scherm te openen</span><span class="sxs-lookup"><span data-stu-id="ab8a2-125">Example 3: Use a file name to open a control panel item</span></span>

<span data-ttu-id="ab8a2-126">In dit voor beeld wordt het onderdeel **Program ma's en onderdelen** van het configuratie scherm geopend met behulp van de toepassings naam.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-126">This example opens the **Programs and Features** control panel item by using its application name.</span></span>

```powershell
appwiz.cpl
```

<span data-ttu-id="ab8a2-127">Deze methode is een alternatief voor het gebruik van een `Show-ControlPanelItem` opdracht.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-127">This method is an alternative to using a `Show-ControlPanelItem` command.</span></span>

> [!NOTE]
> <span data-ttu-id="ab8a2-128">In Power shell kunt u de extensie. cpl voor configuratie scherm-bestanden weglaten, omdat deze deel uitmaakt van de waarde van de `$env:PathExt` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-128">In PowerShell, you can omit the .cpl file extension for control panel files because it's included in the value of the `$env:PathExt` environment variable.</span></span>

## <span data-ttu-id="ab8a2-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ab8a2-129">PARAMETERS</span></span>

### <span data-ttu-id="ab8a2-130">-Canoniekenaam</span><span class="sxs-lookup"><span data-stu-id="ab8a2-130">-CanonicalName</span></span>

<span data-ttu-id="ab8a2-131">Hiermee geeft u onderdelen van het configuratie scherm met behulp van de opgegeven canonieke namen of naam patronen.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-131">Specifies control panel items by using the specified canonical names or name patterns.</span></span> <span data-ttu-id="ab8a2-132">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-132">Wildcard characters are permitted.</span></span> <span data-ttu-id="ab8a2-133">Als u meerdere namen opgeeft, opent deze cmdlet configuratie scherm-items die overeenkomen met een van de namen, alsof de items in de naam lijst zijn gescheiden door een **or** -operator.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-133">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

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

### <span data-ttu-id="ab8a2-134">-Input object</span><span class="sxs-lookup"><span data-stu-id="ab8a2-134">-InputObject</span></span>

<span data-ttu-id="ab8a2-135">Hiermee geeft u de configuratie scherm-items die moeten worden geopend door het verzenden van item objecten van het configuratie scherm.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-135">Specifies control panel items to open by submitting control panel item objects.</span></span> <span data-ttu-id="ab8a2-136">Voer een variabele in die onderdeel objecten van het configuratie scherm bevat, of typ een opdracht of expressie waarmee de object objecten van het configuratie scherm worden opgehaald, zoals `Get-ControlPanelItem` .</span><span class="sxs-lookup"><span data-stu-id="ab8a2-136">Enter a variable that contains control panel item objects, or type a command or expression that gets control panel item objects, such as `Get-ControlPanelItem`.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ab8a2-137">-Name</span><span class="sxs-lookup"><span data-stu-id="ab8a2-137">-Name</span></span>

<span data-ttu-id="ab8a2-138">Hiermee geeft u de namen van de onderdelen van het configuratie scherm.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-138">Specifies names of control panel items.</span></span> <span data-ttu-id="ab8a2-139">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="ab8a2-140">Als u meerdere namen opgeeft, opent deze cmdlet configuratie scherm-items die overeenkomen met een van de namen, alsof de items in de naam lijst zijn gescheiden door een **or** -operator.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-140">If you enter multiple names, this cmdlet opens control panel items that match any of the names, as if the items in the name list were separated by an **OR** operator.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ab8a2-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab8a2-141">CommonParameters</span></span>

<span data-ttu-id="ab8a2-142">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab8a2-143">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab8a2-144">INVOER</span><span class="sxs-lookup"><span data-stu-id="ab8a2-144">INPUTS</span></span>

### <span data-ttu-id="ab8a2-145">System. String, micro soft. Power shell. commands. ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="ab8a2-145">System.String, Microsoft.PowerShell.Commands.ControlPanelItem</span></span>

<span data-ttu-id="ab8a2-146">U kunt een naam of item object van het configuratie scherm door geven aan deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-146">You can pipe a name or control panel item object to this cmdlet.</span></span>

## <span data-ttu-id="ab8a2-147">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ab8a2-147">OUTPUTS</span></span>

### <span data-ttu-id="ab8a2-148">Geen</span><span class="sxs-lookup"><span data-stu-id="ab8a2-148">None</span></span>

<span data-ttu-id="ab8a2-149">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-149">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="ab8a2-150">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ab8a2-150">NOTES</span></span>

## <span data-ttu-id="ab8a2-151">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ab8a2-151">RELATED LINKS</span></span>

[<span data-ttu-id="ab8a2-152">Get-ControlPanelItem</span><span class="sxs-lookup"><span data-stu-id="ab8a2-152">Get-ControlPanelItem</span></span>](Get-ControlPanelItem.md)
