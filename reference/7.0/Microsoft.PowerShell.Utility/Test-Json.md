---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: 2e3d49700adb8115bf24ae505fbb00c14a774f15
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249803"
---
# Test-Json

## SAMENVATTING
Test of een teken reeks een geldig JSON-document is

## SYNTAXIS

```
Test-Json [-Json] <string> [[-Schema] <string>] [<CommonParameters>]
```

## BESCHRIJVING

De `Test-Json` cmdlet test of een teken reeks een geldig JavaScript object Notation (JSON)-document is en kan eventueel het JSON-document controleren op basis van een bijkomend schema.

De gecontroleerde teken reeks kan vervolgens worden gebruikt met de `ConvertFrom-Json` cmdlet Converteer een JSON-indelings teken reeks naar een JSON-object, dat eenvoudig kan worden beheerd in Power shell of wordt verzonden naar een ander programma of een webservice die toegang heeft tot JSON-invoer.

Veel websites gebruiken JSON in plaats van XML om gegevens te serialiseren voor communicatie tussen servers en web-apps.

Deze cmdlet is geïntroduceerd in Power shell 6,1

## VOORBEELDEN

### Voor beeld 1: testen of een object een geldige JSON is

In dit voor beeld wordt getest of de invoer teken reeks een geldig JSON-document is.

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### Voor beeld 2: een object testen op basis van een bijkomend schema

In dit voor beeld wordt een teken reeks met een JSON-schema gebruikt en vergeleken met een invoer teken reeks.

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

In dit voor beeld wordt er een fout bericht weer geven omdat het schema een geheel getal voor de **leeftijd** verwacht, maar de JSON-invoer die we hebben getest, gebruikt een teken reeks waarde.

Zie [JSON-schema](https://json-schema.org/)voor meer informatie.

## PARAMETERS

### -JSON

Hiermee geeft u de JSON-teken reeks op die u wilt testen op geldigheid. Voer een variabele in die de teken reeks bevat, of typ een opdracht of expressie die de teken reeks ophaalt. U kunt ook een teken reeks aan een pipe door geven `Test-Json` .

De **JSON** -para meter is vereist.

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

### -Schema

Hiermee geeft u een schema op voor het valideren van de JSON-invoer. Als door gegeven `Test-Json` wordt gecontroleerd of de JSON-invoer voldoet aan de specificatie die is opgegeven door de **schema** parameter en retour neren `$True` als de invoer voldoet aan het opgegeven schema.

Zie [JSON-schema](https://json-schema.org/)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een JSON-teken reeks door sluizen naar `Test-Json` .

## UITVOER

### Boolean-waarde

## OPMERKINGEN

De `Test-Json` cmdlet wordt geïmplementeerd met behulp van de [NJsonSchema-klasse](https://github.com/RSuter/NJsonSchema).

## GERELATEERDE KOPPELINGEN

[Een inleiding tot JavaScript Object Notation (JSON) in Java script en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[Aanvullende details van het JSON-schema](https://json-schema.org/)

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
