---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: a29eab449e567f78d1e54a6716ca91d87aa08405
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705805"
---
# <span data-ttu-id="860f9-102">Test-Json</span><span class="sxs-lookup"><span data-stu-id="860f9-102">Test-Json</span></span>

## <span data-ttu-id="860f9-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="860f9-103">SYNOPSIS</span></span>
<span data-ttu-id="860f9-104">Test of een teken reeks een geldig JSON-document is</span><span class="sxs-lookup"><span data-stu-id="860f9-104">Tests whether a string is a valid JSON document</span></span>

## <span data-ttu-id="860f9-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="860f9-105">SYNTAX</span></span>

### <span data-ttu-id="860f9-106">__AllParameterSets (standaard)</span><span class="sxs-lookup"><span data-stu-id="860f9-106">__AllParameterSets (Default)</span></span>
```
Test-Json [-Json] <String> [<CommonParameters>]
```

### <span data-ttu-id="860f9-107">SchemaString</span><span class="sxs-lookup"><span data-stu-id="860f9-107">SchemaString</span></span>
```
Test-Json [-Json] <String> [[-Schema] <String>] [<CommonParameters>]
```

### <span data-ttu-id="860f9-108">SchemaFile</span><span class="sxs-lookup"><span data-stu-id="860f9-108">SchemaFile</span></span>
```
Test-Json [-Json] <String> [-SchemaFile <String>] [<CommonParameters>]
```

## <span data-ttu-id="860f9-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="860f9-109">DESCRIPTION</span></span>

<span data-ttu-id="860f9-110">De `Test-Json` cmdlet test of een teken reeks een geldig JavaScript object Notation (JSON)-document is en kan eventueel het JSON-document controleren op basis van een bijkomend schema.</span><span class="sxs-lookup"><span data-stu-id="860f9-110">The `Test-Json` cmdlet tests whether a string is a valid JavaScript Object Notation (JSON) document and can optionally verify that JSON document against a provided schema.</span></span>

<span data-ttu-id="860f9-111">De gecontroleerde teken reeks kan vervolgens worden gebruikt met de `ConvertFrom-Json` cmdlet Converteer een JSON-indelings teken reeks naar een JSON-object, dat eenvoudig kan worden beheerd in Power shell of wordt verzonden naar een ander programma of een webservice die toegang heeft tot JSON-invoer.</span><span class="sxs-lookup"><span data-stu-id="860f9-111">The verified string can then be used with the `ConvertFrom-Json` cmdlet convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell or sent to another program or web service that access JSON input.</span></span>

<span data-ttu-id="860f9-112">Veel websites gebruiken JSON in plaats van XML om gegevens te serialiseren voor communicatie tussen servers en web-apps.</span><span class="sxs-lookup"><span data-stu-id="860f9-112">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="860f9-113">Deze cmdlet is geïntroduceerd in Power shell 6,1</span><span class="sxs-lookup"><span data-stu-id="860f9-113">This cmdlet was introduced in PowerShell 6.1</span></span>

## <span data-ttu-id="860f9-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="860f9-114">EXAMPLES</span></span>

### <span data-ttu-id="860f9-115">Voor beeld 1: testen of een object een geldige JSON is</span><span class="sxs-lookup"><span data-stu-id="860f9-115">Example 1: Test if an object is valid JSON</span></span>

<span data-ttu-id="860f9-116">In dit voor beeld wordt getest of de invoer teken reeks een geldig JSON-document is.</span><span class="sxs-lookup"><span data-stu-id="860f9-116">This example tests whether the input string is a valid JSON document.</span></span>

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### <span data-ttu-id="860f9-117">Voor beeld 2: een object testen op basis van een bijkomend schema</span><span class="sxs-lookup"><span data-stu-id="860f9-117">Example 2: Test an object against a provided schema</span></span>

<span data-ttu-id="860f9-118">In dit voor beeld wordt een teken reeks met een JSON-schema gebruikt en vergeleken met een invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="860f9-118">This example takes a string containing a JSON schema and compares it to an input string.</span></span>

```powershell
$schema = @'
{
  "definitions": {},
  "$schema": "http://json-schema.org/draft-07/schema#",
  "$id": "http://example.com/root.json",
  "type": "object",
  "title": "The Root Schema",
  "required": [
    "name",
    "age"
  ],
  "properties": {
    "name": {
      "$id": "#/properties/name",
      "type": "string",
      "title": "The Name Schema",
      "default": "",
      "examples": [
        "Ashley"
      ],
      "pattern": "^(.*)$"
    },
    "age": {
      "$id": "#/properties/age",
      "type": "integer",
      "title": "The Age Schema",
      "default": 0,
      "examples": [
        25
      ]
    }
  }
}
'@
"{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
```

```Output
Test-Json : IntegerExpected: #/age
At line:1 char:37
+ "{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
+                                     ~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (:) [Test-Json], Exception
+ FullyQualifiedErrorId : InvalidJsonAgainstSchema,Microsoft.PowerShell.Commands.TestJsonCommand
False
```

<span data-ttu-id="860f9-119">In dit voor beeld wordt er een fout bericht weer geven omdat het schema een geheel getal voor de **leeftijd** verwacht, maar de JSON-invoer die we hebben getest, gebruikt een teken reeks waarde.</span><span class="sxs-lookup"><span data-stu-id="860f9-119">In this example, we get an error because the schema expects an integer for **age** but the JSON input we tested uses a string value instead.</span></span>

<span data-ttu-id="860f9-120">Zie [JSON-schema](https://json-schema.org/)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="860f9-120">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

### <span data-ttu-id="860f9-121">Voor beeld 3: een object testen op basis van een schema van het bestand</span><span class="sxs-lookup"><span data-stu-id="860f9-121">Example 3: Test an object against a schema from file</span></span>

<span data-ttu-id="860f9-122">JSON-schema kan verwijzen naar definities met behulp van een `$ref` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="860f9-122">JSON schema can reference definitions using `$ref` keyword.</span></span> <span data-ttu-id="860f9-123">De `$ref` kan worden omgezet naar een URI die verwijst naar een ander bestand.</span><span class="sxs-lookup"><span data-stu-id="860f9-123">The `$ref` can resolve to a URI that references another file.</span></span> <span data-ttu-id="860f9-124">De `SchemaFile` para meter accepteert letterlijk pad naar het JSON-schema bestand en maakt het mogelijk json-bestanden te valideren op basis van dergelijke schema's.</span><span class="sxs-lookup"><span data-stu-id="860f9-124">The `SchemaFile` parameter accepts literal path to the JSON schema file and allows JSON files to be validated against such schemas.</span></span>

<span data-ttu-id="860f9-125">In dit voor beeld hebben we een `schema.json` bestand waarnaar wordt verwezen `definitions.json` .</span><span class="sxs-lookup"><span data-stu-id="860f9-125">In this example we have `schema.json` file which references `definitions.json`.</span></span>

```powershell
PS> Get-Content schema.json

{
  "description":"A person",
  "type":"object",
  "properties":{
    "name":{
      "$ref":"definitions.json#/definitions/name"
    },
    "hobbies":{
      "$ref":"definitions.json#/definitions/hobbies"
    }
  }
}

PS> Get-Content definitions.json

{
  "definitions":{
    "name":{
      "type":"string"
    },
    "hobbies":{
      "type":"array",
      "items":{
        "type":"string"
      }
    }
  }
}

'{"name": "James", "hobbies": [".NET", "Blogging"]}' | Test-Json -SchemaFile 'schema.json'
```

```Output
True
```

<span data-ttu-id="860f9-126">Zie [een complex schema structureren](https://json-schema.org/understanding-json-schema/structuring.html)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="860f9-126">For more information, see [Structuring a complex schema](https://json-schema.org/understanding-json-schema/structuring.html).</span></span>

## <span data-ttu-id="860f9-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="860f9-127">PARAMETERS</span></span>

### <span data-ttu-id="860f9-128">-JSON</span><span class="sxs-lookup"><span data-stu-id="860f9-128">-Json</span></span>

<span data-ttu-id="860f9-129">Hiermee geeft u de JSON-teken reeks op die u wilt testen op geldigheid.</span><span class="sxs-lookup"><span data-stu-id="860f9-129">Specifies the JSON string to test for validity.</span></span> <span data-ttu-id="860f9-130">Voer een variabele in die de teken reeks bevat, of typ een opdracht of expressie die de teken reeks ophaalt.</span><span class="sxs-lookup"><span data-stu-id="860f9-130">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="860f9-131">U kunt ook een teken reeks aan een pipe door geven `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="860f9-131">You can also pipe a string to `Test-Json`.</span></span>

<span data-ttu-id="860f9-132">De **JSON** -para meter is vereist.</span><span class="sxs-lookup"><span data-stu-id="860f9-132">The **Json** parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="860f9-133">-Schema</span><span class="sxs-lookup"><span data-stu-id="860f9-133">-Schema</span></span>

<span data-ttu-id="860f9-134">Hiermee geeft u een schema op voor het valideren van de JSON-invoer.</span><span class="sxs-lookup"><span data-stu-id="860f9-134">Specifies a Schema to validate the JSON input against.</span></span> <span data-ttu-id="860f9-135">Als door gegeven `Test-Json` wordt gecontroleerd of de JSON-invoer voldoet aan de specificatie die is opgegeven door de **schema** parameter en retour neren `$True` als de invoer voldoet aan het opgegeven schema.</span><span class="sxs-lookup"><span data-stu-id="860f9-135">If passed `Test-Json` will validate that the Json input conforms to the spec specified by the **Schema** parameter and return `$True` only if the input conforms to the provided Schema.</span></span>

<span data-ttu-id="860f9-136">Zie [JSON-schema](https://json-schema.org/)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="860f9-136">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

```yaml
Type: System.String
Parameter Sets: SchemaString
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="860f9-137">-SchemaFile</span><span class="sxs-lookup"><span data-stu-id="860f9-137">-SchemaFile</span></span>

<span data-ttu-id="860f9-138">Hiermee geeft u een schema bestand op dat wordt gebruikt voor het valideren van de JSON-invoer.</span><span class="sxs-lookup"><span data-stu-id="860f9-138">Specifies a schema file used to validate the JSON input.</span></span> <span data-ttu-id="860f9-139">Als de JSON-invoer wordt gebruikt, `Test-Json` wordt deze `$True` alleen geretourneerd als deze voldoet aan het schema dat is gedefinieerd in het bestand dat is opgegeven door de para meter **SchemaFile** .</span><span class="sxs-lookup"><span data-stu-id="860f9-139">When used, the `Test-Json` returns `$True` only if the JSON input conforms to the Schema defined in the file specified by the **SchemaFile** parameter.</span></span>

<span data-ttu-id="860f9-140">Zie [JSON-schema](https://json-schema.org/)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="860f9-140">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

```yaml
Type: System.String
Parameter Sets: SchemaFile
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="860f9-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="860f9-141">CommonParameters</span></span>

<span data-ttu-id="860f9-142">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="860f9-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="860f9-143">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="860f9-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="860f9-144">INVOER</span><span class="sxs-lookup"><span data-stu-id="860f9-144">INPUTS</span></span>

### <span data-ttu-id="860f9-145">System. String</span><span class="sxs-lookup"><span data-stu-id="860f9-145">System.String</span></span>

<span data-ttu-id="860f9-146">U kunt een JSON-teken reeks door sluizen naar `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="860f9-146">You can pipe a JSON string to `Test-Json`.</span></span>

## <span data-ttu-id="860f9-147">UITVOER</span><span class="sxs-lookup"><span data-stu-id="860f9-147">OUTPUTS</span></span>

### <span data-ttu-id="860f9-148">Booleaans</span><span class="sxs-lookup"><span data-stu-id="860f9-148">Boolean</span></span>

## <span data-ttu-id="860f9-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="860f9-149">NOTES</span></span>

<span data-ttu-id="860f9-150">De `Test-Json` cmdlet wordt geïmplementeerd met behulp van de [NJsonSchema-klasse](https://github.com/RSuter/NJsonSchema).</span><span class="sxs-lookup"><span data-stu-id="860f9-150">The `Test-Json` cmdlet is implemented by using the [NJsonSchema Class](https://github.com/RSuter/NJsonSchema).</span></span>

## <span data-ttu-id="860f9-151">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="860f9-151">RELATED LINKS</span></span>

<span data-ttu-id="860f9-152">[Een inleiding tot JavaScript Object Notation (JSON) in Java script en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="860f9-152">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="860f9-153">Aanvullende details van het JSON-schema</span><span class="sxs-lookup"><span data-stu-id="860f9-153">Additional JSON Schema Details</span></span>](https://json-schema.org/)

[<span data-ttu-id="860f9-154">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="860f9-154">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="860f9-155">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="860f9-155">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="860f9-156">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="860f9-156">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
