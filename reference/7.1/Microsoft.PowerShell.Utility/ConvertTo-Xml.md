---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: 2e7ebe3a528095873dc7ba5ba0deba2905f531ee
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250905"
---
# <span data-ttu-id="f99f9-103">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="f99f9-103">ConvertTo-Xml</span></span>

## <span data-ttu-id="f99f9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f99f9-104">SYNOPSIS</span></span>
<span data-ttu-id="f99f9-105">Hiermee maakt u een XML-weer gave van een object.</span><span class="sxs-lookup"><span data-stu-id="f99f9-105">Creates an XML-based representation of an object.</span></span>

## <span data-ttu-id="f99f9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f99f9-106">SYNTAX</span></span>

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="f99f9-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f99f9-107">DESCRIPTION</span></span>

<span data-ttu-id="f99f9-108">De `ConvertTo-Xml` cmdlet maakt een [op XML gebaseerde](/dotnet/api/system.xml.xmldocument) weer gave van een of meer .net-objecten.</span><span class="sxs-lookup"><span data-stu-id="f99f9-108">The `ConvertTo-Xml` cmdlet creates an [XML-based](/dotnet/api/system.xml.xmldocument) representation of one or more more .NET objects.</span></span> <span data-ttu-id="f99f9-109">Als u deze cmdlet wilt gebruiken, pipet u een of meer objecten aan de cmdlet of gebruikt u de para meter **input object** om het object op te geven.</span><span class="sxs-lookup"><span data-stu-id="f99f9-109">To use this cmdlet, pipe one or more objects to the cmdlet, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="f99f9-110">Wanneer u meerdere objecten naar een pipet `ConvertTo-Xml` of de para meter **input object** gebruikt voor het verzenden van meerdere objecten, `ConvertTo-Xml` retourneert een enkel XML-document in het geheugen dat de weer gaven van alle objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="f99f9-110">When you pipe multiple objects to `ConvertTo-Xml` or use the **InputObject** parameter to submit multiple objects, `ConvertTo-Xml` returns a single, in-memory XML document that includes representations of all of the objects.</span></span>

<span data-ttu-id="f99f9-111">Deze cmdlet is vergelijkbaar met [exporteren-Clixml](./Export-Clixml.md) , behalve dat `Export-Clixml` de resulterende XML wordt opgeslagen in een [cli-XML-bestand (Common Language Infrastructure)](https://www.ecma-international.org/publications/standards/Ecma-335.htm) dat opnieuw kan worden geïmporteerd als objecten met [import-Clixml](./Import-Clixml.md).</span><span class="sxs-lookup"><span data-stu-id="f99f9-111">This cmdlet is similar to [Export-Clixml](./Export-Clixml.md) except that `Export-Clixml` stores the resulting XML in a [Common Language Infrastructure(CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) file that can be reimported as objects with [Import-Clixml](./Import-Clixml.md).</span></span> <span data-ttu-id="f99f9-112">`ConvertTo-Xml` retourneert een representatie in het geheugen van een XML-document, zodat u deze kunt blijven verwerken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="f99f9-112">`ConvertTo-Xml` returns an in-memory representation of an XML document, so you can continue to process it in PowerShell.</span></span> <span data-ttu-id="f99f9-113">`ConvertTo-Xml` heeft geen optie om objecten te converteren naar CLI XML.</span><span class="sxs-lookup"><span data-stu-id="f99f9-113">`ConvertTo-Xml` does not have an option to convert objects to CLI XML.</span></span>

## <span data-ttu-id="f99f9-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f99f9-114">EXAMPLES</span></span>

### <span data-ttu-id="f99f9-115">Voor beeld 1: een datum converteren naar XML</span><span class="sxs-lookup"><span data-stu-id="f99f9-115">Example 1: Convert a date to XML</span></span>

```
PS C:\> Get-Date | ConvertTo-Xml
```

<span data-ttu-id="f99f9-116">Met deze opdracht wordt de huidige datum (een **DateTime** -object) GECONVERTEERD naar XML.</span><span class="sxs-lookup"><span data-stu-id="f99f9-116">This command converts the current date (a **DateTime** object) to XML.</span></span>

### <span data-ttu-id="f99f9-117">Voor beeld 2: processen naar XML converteren</span><span class="sxs-lookup"><span data-stu-id="f99f9-117">Example 2: Convert processes to XML</span></span>

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

<span data-ttu-id="f99f9-118">Met deze opdracht worden de proces objecten geconverteerd die alle processen op de computer vertegenwoordigen in een XML-document.</span><span class="sxs-lookup"><span data-stu-id="f99f9-118">This command converts the process objects that represent all of the processes on the computer into an XML document.</span></span> <span data-ttu-id="f99f9-119">De objecten worden uitgebreid tot een diepte van drie niveaus.</span><span class="sxs-lookup"><span data-stu-id="f99f9-119">The objects are expanded to a depth of three levels.</span></span>

## <span data-ttu-id="f99f9-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f99f9-120">PARAMETERS</span></span>

### <span data-ttu-id="f99f9-121">-As</span><span class="sxs-lookup"><span data-stu-id="f99f9-121">-As</span></span>

<span data-ttu-id="f99f9-122">Bepaalt de uitvoer indeling.</span><span class="sxs-lookup"><span data-stu-id="f99f9-122">Determines the output format.</span></span>
<span data-ttu-id="f99f9-123">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f99f9-123">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f99f9-124">Tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="f99f9-124">String.</span></span>
<span data-ttu-id="f99f9-125">Retourneert één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="f99f9-125">Returns a single string.</span></span>
- <span data-ttu-id="f99f9-126">Bitsnelheid.</span><span class="sxs-lookup"><span data-stu-id="f99f9-126">Stream.</span></span>
<span data-ttu-id="f99f9-127">Retourneert een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f99f9-127">Returns an array of strings.</span></span>
- <span data-ttu-id="f99f9-128">Document.</span><span class="sxs-lookup"><span data-stu-id="f99f9-128">Document.</span></span>
<span data-ttu-id="f99f9-129">Retourneert een **XMLDocument** -object.</span><span class="sxs-lookup"><span data-stu-id="f99f9-129">Returns an **XmlDocument** object.</span></span>

<span data-ttu-id="f99f9-130">De standaard waarde is document.</span><span class="sxs-lookup"><span data-stu-id="f99f9-130">The default value is Document.</span></span>

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

### <span data-ttu-id="f99f9-131">-Diepte</span><span class="sxs-lookup"><span data-stu-id="f99f9-131">-Depth</span></span>

<span data-ttu-id="f99f9-132">Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de XML-weer gave.</span><span class="sxs-lookup"><span data-stu-id="f99f9-132">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="f99f9-133">De standaardwaarde is 1.</span><span class="sxs-lookup"><span data-stu-id="f99f9-133">The default value is 1.</span></span>

<span data-ttu-id="f99f9-134">Als de eigenschappen van het object bijvoorbeeld ook objecten bevatten, om een XML-weer gave van de eigenschappen van de Inge sloten objecten op te slaan, moet u een diepte van 2 opgeven.</span><span class="sxs-lookup"><span data-stu-id="f99f9-134">For example, if the object's properties also contain objects, to save an XML representation of the properties of the contained objects, you must specify a depth of 2.</span></span>

<span data-ttu-id="f99f9-135">De standaard waarde kan worden overschreven voor het object type in de Types.ps1XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="f99f9-135">The default value can be overridden for the object type in the Types.ps1xml files.</span></span> <span data-ttu-id="f99f9-136">Zie about_Types.ps1XML voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f99f9-136">For more information, see about_Types.ps1xml.</span></span>

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

### <span data-ttu-id="f99f9-137">-Input object</span><span class="sxs-lookup"><span data-stu-id="f99f9-137">-InputObject</span></span>

<span data-ttu-id="f99f9-138">Geeft het object aan dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="f99f9-138">Specifies the object to be converted.</span></span> <span data-ttu-id="f99f9-139">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f99f9-139">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="f99f9-140">U kunt ook objecten door sluizen naar **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="f99f9-140">You can also pipe objects to **ConvertTo-XML**.</span></span>

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

### <span data-ttu-id="f99f9-141">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="f99f9-141">-NoTypeInformation</span></span>

<span data-ttu-id="f99f9-142">Laat het kenmerk type van de object knooppunten.</span><span class="sxs-lookup"><span data-stu-id="f99f9-142">Omits the Type attribute from the object nodes.</span></span>

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

### <span data-ttu-id="f99f9-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f99f9-143">CommonParameters</span></span>

<span data-ttu-id="f99f9-144">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f99f9-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f99f9-145">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f99f9-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f99f9-146">INVOER</span><span class="sxs-lookup"><span data-stu-id="f99f9-146">INPUTS</span></span>

### <span data-ttu-id="f99f9-147">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="f99f9-147">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f99f9-148">U kunt elk object door sluizen naar **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="f99f9-148">You can pipe any object to **ConvertTo-XML**.</span></span>

## <span data-ttu-id="f99f9-149">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f99f9-149">OUTPUTS</span></span>

### <span data-ttu-id="f99f9-150">Systeem. teken reeks of System.Xml.Xmldocument</span><span class="sxs-lookup"><span data-stu-id="f99f9-150">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="f99f9-151">De waarde van de *as* -para meter bepaalt het type object dat **ConvertTo-XML** retourneert.</span><span class="sxs-lookup"><span data-stu-id="f99f9-151">The value of the *As* parameter determines the type of object that **ConvertTo-XML** returns.</span></span>

## <span data-ttu-id="f99f9-152">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f99f9-152">NOTES</span></span>

## <span data-ttu-id="f99f9-153">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f99f9-153">RELATED LINKS</span></span>

[<span data-ttu-id="f99f9-154">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="f99f9-154">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="f99f9-155">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="f99f9-155">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="f99f9-156">Exporteren-Clixml</span><span class="sxs-lookup"><span data-stu-id="f99f9-156">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="f99f9-157">Ophalen datum</span><span class="sxs-lookup"><span data-stu-id="f99f9-157">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="f99f9-158">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="f99f9-158">Import-Clixml</span></span>](Import-Clixml.md)

