---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: e461c07360b3d9eaf7d9a3c8875d34cd1fc841e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705961"
---
# <span data-ttu-id="7fed8-102">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="7fed8-102">ConvertTo-Xml</span></span>

## <span data-ttu-id="7fed8-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7fed8-103">SYNOPSIS</span></span>
<span data-ttu-id="7fed8-104">Hiermee maakt u een XML-weer gave van een object.</span><span class="sxs-lookup"><span data-stu-id="7fed8-104">Creates an XML-based representation of an object.</span></span>

## <span data-ttu-id="7fed8-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7fed8-105">SYNTAX</span></span>

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="7fed8-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7fed8-106">DESCRIPTION</span></span>

<span data-ttu-id="7fed8-107">De `ConvertTo-Xml` cmdlet maakt een [op XML gebaseerde](/dotnet/api/system.xml.xmldocument) weer gave van een of meer .net-objecten.</span><span class="sxs-lookup"><span data-stu-id="7fed8-107">The `ConvertTo-Xml` cmdlet creates an [XML-based](/dotnet/api/system.xml.xmldocument) representation of one or more more .NET objects.</span></span> <span data-ttu-id="7fed8-108">Als u deze cmdlet wilt gebruiken, pipet u een of meer objecten aan de cmdlet of gebruikt u de para meter **input object** om het object op te geven.</span><span class="sxs-lookup"><span data-stu-id="7fed8-108">To use this cmdlet, pipe one or more objects to the cmdlet, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="7fed8-109">Wanneer u meerdere objecten naar een pipet `ConvertTo-Xml` of de para meter **input object** gebruikt voor het verzenden van meerdere objecten, `ConvertTo-Xml` retourneert een enkel XML-document in het geheugen dat de weer gaven van alle objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="7fed8-109">When you pipe multiple objects to `ConvertTo-Xml` or use the **InputObject** parameter to submit multiple objects, `ConvertTo-Xml` returns a single, in-memory XML document that includes representations of all of the objects.</span></span>

<span data-ttu-id="7fed8-110">Deze cmdlet is vergelijkbaar met [exporteren-Clixml](./Export-Clixml.md) , behalve dat `Export-Clixml` de resulterende XML wordt opgeslagen in een [cli-XML-bestand (Common Language Infrastructure)](https://www.ecma-international.org/publications/standards/Ecma-335.htm) dat opnieuw kan worden geïmporteerd als objecten met [import-Clixml](./Import-Clixml.md).</span><span class="sxs-lookup"><span data-stu-id="7fed8-110">This cmdlet is similar to [Export-Clixml](./Export-Clixml.md) except that `Export-Clixml` stores the resulting XML in a [Common Language Infrastructure(CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) file that can be reimported as objects with [Import-Clixml](./Import-Clixml.md).</span></span> <span data-ttu-id="7fed8-111">`ConvertTo-Xml` retourneert een representatie in het geheugen van een XML-document, zodat u deze kunt blijven verwerken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="7fed8-111">`ConvertTo-Xml` returns an in-memory representation of an XML document, so you can continue to process it in PowerShell.</span></span> <span data-ttu-id="7fed8-112">`ConvertTo-Xml` heeft geen optie om objecten te converteren naar CLI XML.</span><span class="sxs-lookup"><span data-stu-id="7fed8-112">`ConvertTo-Xml` does not have an option to convert objects to CLI XML.</span></span>

## <span data-ttu-id="7fed8-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7fed8-113">EXAMPLES</span></span>

### <span data-ttu-id="7fed8-114">Voor beeld 1: een datum converteren naar XML</span><span class="sxs-lookup"><span data-stu-id="7fed8-114">Example 1: Convert a date to XML</span></span>

```
PS C:\> Get-Date | ConvertTo-Xml
```

<span data-ttu-id="7fed8-115">Met deze opdracht wordt de huidige datum (een **DateTime** -object) GECONVERTEERD naar XML.</span><span class="sxs-lookup"><span data-stu-id="7fed8-115">This command converts the current date (a **DateTime** object) to XML.</span></span>

### <span data-ttu-id="7fed8-116">Voor beeld 2: processen naar XML converteren</span><span class="sxs-lookup"><span data-stu-id="7fed8-116">Example 2: Convert processes to XML</span></span>

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

<span data-ttu-id="7fed8-117">Met deze opdracht worden de proces objecten geconverteerd die alle processen op de computer vertegenwoordigen in een XML-document.</span><span class="sxs-lookup"><span data-stu-id="7fed8-117">This command converts the process objects that represent all of the processes on the computer into an XML document.</span></span> <span data-ttu-id="7fed8-118">De objecten worden uitgebreid tot een diepte van drie niveaus.</span><span class="sxs-lookup"><span data-stu-id="7fed8-118">The objects are expanded to a depth of three levels.</span></span>

## <span data-ttu-id="7fed8-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7fed8-119">PARAMETERS</span></span>

### <span data-ttu-id="7fed8-120">-As</span><span class="sxs-lookup"><span data-stu-id="7fed8-120">-As</span></span>

<span data-ttu-id="7fed8-121">Bepaalt de uitvoer indeling.</span><span class="sxs-lookup"><span data-stu-id="7fed8-121">Determines the output format.</span></span>
<span data-ttu-id="7fed8-122">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="7fed8-122">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7fed8-123">Tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="7fed8-123">String.</span></span>
<span data-ttu-id="7fed8-124">Retourneert één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="7fed8-124">Returns a single string.</span></span>
- <span data-ttu-id="7fed8-125">Bitsnelheid.</span><span class="sxs-lookup"><span data-stu-id="7fed8-125">Stream.</span></span>
<span data-ttu-id="7fed8-126">Retourneert een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="7fed8-126">Returns an array of strings.</span></span>
- <span data-ttu-id="7fed8-127">Document.</span><span class="sxs-lookup"><span data-stu-id="7fed8-127">Document.</span></span>
<span data-ttu-id="7fed8-128">Retourneert een **XMLDocument** -object.</span><span class="sxs-lookup"><span data-stu-id="7fed8-128">Returns an **XmlDocument** object.</span></span>

<span data-ttu-id="7fed8-129">De standaard waarde is document.</span><span class="sxs-lookup"><span data-stu-id="7fed8-129">The default value is Document.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fed8-130">-Diepte</span><span class="sxs-lookup"><span data-stu-id="7fed8-130">-Depth</span></span>

<span data-ttu-id="7fed8-131">Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de XML-weer gave.</span><span class="sxs-lookup"><span data-stu-id="7fed8-131">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="7fed8-132">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="7fed8-132">The default value is 1.</span></span>

<span data-ttu-id="7fed8-133">Als de eigenschappen van het object bijvoorbeeld ook objecten bevatten, om een XML-weer gave van de eigenschappen van de Inge sloten objecten op te slaan, moet u een diepte van 2 opgeven.</span><span class="sxs-lookup"><span data-stu-id="7fed8-133">For example, if the object's properties also contain objects, to save an XML representation of the properties of the contained objects, you must specify a depth of 2.</span></span>

<span data-ttu-id="7fed8-134">De standaard waarde kan worden overschreven voor het object type in de Types.ps1XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="7fed8-134">The default value can be overridden for the object type in the Types.ps1xml files.</span></span> <span data-ttu-id="7fed8-135">Zie about_Types.ps1XML voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7fed8-135">For more information, see about_Types.ps1xml.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fed8-136">-Input object</span><span class="sxs-lookup"><span data-stu-id="7fed8-136">-InputObject</span></span>

<span data-ttu-id="7fed8-137">Geeft het object aan dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="7fed8-137">Specifies the object to be converted.</span></span> <span data-ttu-id="7fed8-138">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7fed8-138">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="7fed8-139">U kunt ook objecten door sluizen naar **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="7fed8-139">You can also pipe objects to **ConvertTo-XML**.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7fed8-140">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="7fed8-140">-NoTypeInformation</span></span>

<span data-ttu-id="7fed8-141">Laat het kenmerk type van de object knooppunten.</span><span class="sxs-lookup"><span data-stu-id="7fed8-141">Omits the Type attribute from the object nodes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7fed8-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7fed8-142">CommonParameters</span></span>

<span data-ttu-id="7fed8-143">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7fed8-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7fed8-144">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7fed8-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7fed8-145">INVOER</span><span class="sxs-lookup"><span data-stu-id="7fed8-145">INPUTS</span></span>

### <span data-ttu-id="7fed8-146">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7fed8-146">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7fed8-147">U kunt elk object door sluizen naar **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="7fed8-147">You can pipe any object to **ConvertTo-XML**.</span></span>

## <span data-ttu-id="7fed8-148">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7fed8-148">OUTPUTS</span></span>

### <span data-ttu-id="7fed8-149">Systeem. teken reeks of System.Xml.Xmldocument</span><span class="sxs-lookup"><span data-stu-id="7fed8-149">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="7fed8-150">De waarde van de *as* -para meter bepaalt het type object dat **ConvertTo-XML** retourneert.</span><span class="sxs-lookup"><span data-stu-id="7fed8-150">The value of the *As* parameter determines the type of object that **ConvertTo-XML** returns.</span></span>

## <span data-ttu-id="7fed8-151">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7fed8-151">NOTES</span></span>

## <span data-ttu-id="7fed8-152">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7fed8-152">RELATED LINKS</span></span>

[<span data-ttu-id="7fed8-153">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="7fed8-153">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="7fed8-154">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="7fed8-154">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="7fed8-155">Exporteren-Clixml</span><span class="sxs-lookup"><span data-stu-id="7fed8-155">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="7fed8-156">Ophalen datum</span><span class="sxs-lookup"><span data-stu-id="7fed8-156">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="7fed8-157">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="7fed8-157">Import-Clixml</span></span>](Import-Clixml.md)

