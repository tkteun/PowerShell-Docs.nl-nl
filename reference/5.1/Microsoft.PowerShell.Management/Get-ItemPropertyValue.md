---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 2dbbbfeac3810f79b976b6a68ab3089e91707fb3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250795"
---
# <span data-ttu-id="89642-103">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="89642-103">Get-ItemPropertyValue</span></span>

## <span data-ttu-id="89642-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="89642-104">SYNOPSIS</span></span>
<span data-ttu-id="89642-105">Hiermee wordt de waarde voor een of meer eigenschappen van een opgegeven item opgehaald.</span><span class="sxs-lookup"><span data-stu-id="89642-105">Gets the value for one or more properties of a specified item.</span></span>

## <span data-ttu-id="89642-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="89642-106">SYNTAX</span></span>

### <span data-ttu-id="89642-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="89642-107">Path (Default)</span></span>

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="89642-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="89642-108">LiteralPath</span></span>

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="89642-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="89642-109">DESCRIPTION</span></span>

<span data-ttu-id="89642-110">De `Get-ItemPropertyValue` haalt de huidige waarde op voor een eigenschap die u opgeeft wanneer u de para meter *name* gebruikt, die zich bevindt in een pad dat u opgeeft met de *pad* -of *LiteralPath* -para meters.</span><span class="sxs-lookup"><span data-stu-id="89642-110">The `Get-ItemPropertyValue` gets the current value for a property that you specify when you use the *Name* parameter, located in a path that you specify with either the *Path* or *LiteralPath* parameters.</span></span>

## <span data-ttu-id="89642-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="89642-111">EXAMPLES</span></span>

### <span data-ttu-id="89642-112">Voor beeld 1: de waarde van de eigenschap ProductID ophalen</span><span class="sxs-lookup"><span data-stu-id="89642-112">Example 1: Get the value of the ProductID property</span></span>

<span data-ttu-id="89642-113">Met deze opdracht wordt de waarde van de eigenschap **ProductID** van het object ' \SOFTWARE\Microsoft\Windows NT\CurrentVersion ' in de Windows-register provider opgehaald.</span><span class="sxs-lookup"><span data-stu-id="89642-113">This command gets the value of the **ProductID** property of the "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" object in the Windows Registry provider.</span></span>

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### <span data-ttu-id="89642-114">Voor beeld 2: de laatste schrijf tijd van een bestand of map ophalen</span><span class="sxs-lookup"><span data-stu-id="89642-114">Example 2: Get the last write time of a file or folder</span></span>

<span data-ttu-id="89642-115">Met deze opdracht wordt de waarde van de eigenschap **LastWriteTime** opgehaald, of de laatste keer dat een bestand of map is gewijzigd, in de map "C:\Users\Test\Documents\ModuleToAssembly", die in de File System Provider werkt.</span><span class="sxs-lookup"><span data-stu-id="89642-115">This command gets the value of the **LastWriteTime** property, or the last time a file or folder was changed, from the "C:\Users\Test\Documents\ModuleToAssembly" folder, working in the FileSystem provider.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### <span data-ttu-id="89642-116">Voor beeld 3: meerdere eigenschaps waarden van een bestand of map ophalen</span><span class="sxs-lookup"><span data-stu-id="89642-116">Example 3: Get multiple property values of a file or folder</span></span>

<span data-ttu-id="89642-117">Met deze opdracht worden de waarden van de **LastWriteTime** -, **CreationTime** -en **root** -eigenschappen van een map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="89642-117">This command gets the values of the **LastWriteTime** , **CreationTime** , and **Root** properties of a folder.</span></span>
<span data-ttu-id="89642-118">De eigenschapwaarden worden geretourneerd in de volg orde waarin u de eigenschapnamen hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="89642-118">The property values are returned in the order in which you specified the property names.</span></span>

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## <span data-ttu-id="89642-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="89642-119">PARAMETERS</span></span>

### <span data-ttu-id="89642-120">-Credential</span><span class="sxs-lookup"><span data-stu-id="89642-120">-Credential</span></span>

<span data-ttu-id="89642-121">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="89642-121">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="89642-122">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="89642-122">The default is the current user.</span></span>

<span data-ttu-id="89642-123">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="89642-123">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="89642-124">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="89642-124">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="89642-125">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="89642-125">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="89642-126">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="89642-126">-Exclude</span></span>

<span data-ttu-id="89642-127">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="89642-127">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="89642-128">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="89642-128">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="89642-129">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="89642-129">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="89642-130">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="89642-130">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="89642-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="89642-131">-Filter</span></span>

<span data-ttu-id="89642-132">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="89642-132">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="89642-133">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="89642-133">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="89642-134">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="89642-134">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="89642-135">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="89642-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="89642-136">-Include</span><span class="sxs-lookup"><span data-stu-id="89642-136">-Include</span></span>

<span data-ttu-id="89642-137">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="89642-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="89642-138">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="89642-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="89642-139">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="89642-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="89642-140">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="89642-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="89642-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="89642-141">-LiteralPath</span></span>

<span data-ttu-id="89642-142">Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="89642-142">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="89642-143">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="89642-143">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="89642-144">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="89642-144">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="89642-145">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="89642-145">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="89642-146">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="89642-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="89642-147">-Name</span><span class="sxs-lookup"><span data-stu-id="89642-147">-Name</span></span>

<span data-ttu-id="89642-148">Hiermee geeft u de naam op van de eigenschap of eigenschappen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="89642-148">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89642-149">-Path</span><span class="sxs-lookup"><span data-stu-id="89642-149">-Path</span></span>

<span data-ttu-id="89642-150">Hiermee geeft u het pad op naar het item of de items.</span><span class="sxs-lookup"><span data-stu-id="89642-150">Specifies the path to the item or items.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="89642-151">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="89642-151">-UseTransaction</span></span>

<span data-ttu-id="89642-152">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="89642-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="89642-153">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="89642-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="89642-154">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="89642-154">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89642-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="89642-155">CommonParameters</span></span>

<span data-ttu-id="89642-156">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="89642-156">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="89642-157">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="89642-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="89642-158">INVOER</span><span class="sxs-lookup"><span data-stu-id="89642-158">INPUTS</span></span>

### <span data-ttu-id="89642-159">System. String</span><span class="sxs-lookup"><span data-stu-id="89642-159">System.String</span></span>

<span data-ttu-id="89642-160">U kunt een teken reeks met een pad naar deze cmdlet door sluizen.</span><span class="sxs-lookup"><span data-stu-id="89642-160">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="89642-161">UITVOER</span><span class="sxs-lookup"><span data-stu-id="89642-161">OUTPUTS</span></span>

### <span data-ttu-id="89642-162">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="89642-162">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="89642-163">Met deze cmdlet wordt een object geretourneerd voor elke eigenschaps waarde van een item die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="89642-163">This cmdlet returns an object for each item property value that it gets.</span></span>
<span data-ttu-id="89642-164">Het object type is afhankelijk van de eigenschaps waarde die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="89642-164">The object type depends on the property value that is retrieved.</span></span>
<span data-ttu-id="89642-165">In een bestandssysteem station kan de cmdlet bijvoorbeeld een bestand of map retour neren.</span><span class="sxs-lookup"><span data-stu-id="89642-165">For example, in a file system drive, the cmdlet might return a file or folder.</span></span>

## <span data-ttu-id="89642-166">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="89642-166">NOTES</span></span>

<span data-ttu-id="89642-167">Deze cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="89642-167">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="89642-168">Voer de cmdlet uit om de providers weer te geven die beschikbaar zijn in uw sessie `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="89642-168">To list the providers available in your session, run the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="89642-169">Zie about_Providers voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="89642-169">For more information, see about_Providers.</span></span>

## <span data-ttu-id="89642-170">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="89642-170">RELATED LINKS</span></span>

[<span data-ttu-id="89642-171">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="89642-171">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="89642-172">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="89642-172">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="89642-173">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="89642-173">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="89642-174">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="89642-174">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="89642-175">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="89642-175">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="89642-176">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="89642-176">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="89642-177">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="89642-177">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="89642-178">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="89642-178">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="89642-179">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="89642-179">Get-PSProvider</span></span>](Get-PSProvider.md)
