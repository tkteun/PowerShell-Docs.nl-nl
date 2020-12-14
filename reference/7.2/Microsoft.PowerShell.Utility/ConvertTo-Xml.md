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
# ConvertTo-Xml

## SAMENVATTING
Hiermee maakt u een XML-weer gave van een object.

## SYNTAXIS

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `ConvertTo-Xml` cmdlet maakt een [op XML gebaseerde](/dotnet/api/system.xml.xmldocument) weer gave van een of meer .net-objecten. Als u deze cmdlet wilt gebruiken, pipet u een of meer objecten aan de cmdlet of gebruikt u de para meter **input object** om het object op te geven.

Wanneer u meerdere objecten naar een pipet `ConvertTo-Xml` of de para meter **input object** gebruikt voor het verzenden van meerdere objecten, `ConvertTo-Xml` retourneert een enkel XML-document in het geheugen dat de weer gaven van alle objecten bevat.

Deze cmdlet is vergelijkbaar met [exporteren-Clixml](./Export-Clixml.md) , behalve dat `Export-Clixml` de resulterende XML wordt opgeslagen in een [cli-XML-bestand (Common Language Infrastructure)](https://www.ecma-international.org/publications/standards/Ecma-335.htm) dat opnieuw kan worden geïmporteerd als objecten met [import-Clixml](./Import-Clixml.md). `ConvertTo-Xml` retourneert een representatie in het geheugen van een XML-document, zodat u deze kunt blijven verwerken in Power shell. `ConvertTo-Xml` heeft geen optie om objecten te converteren naar CLI XML.

## VOORBEELDEN

### Voor beeld 1: een datum converteren naar XML

```
PS C:\> Get-Date | ConvertTo-Xml
```

Met deze opdracht wordt de huidige datum (een **DateTime** -object) GECONVERTEERD naar XML.

### Voor beeld 2: processen naar XML converteren

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

Met deze opdracht worden de proces objecten geconverteerd die alle processen op de computer vertegenwoordigen in een XML-document. De objecten worden uitgebreid tot een diepte van drie niveaus.

## PARAMETERS

### -As

Bepaalt de uitvoer indeling.
De aanvaardbare waarden voor deze parameter zijn:

- Tekenreeks.
Retourneert één teken reeks.
- Bitsnelheid.
Retourneert een matrix met teken reeksen.
- Document.
Retourneert een **XMLDocument** -object.

De standaard waarde is document.

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

### -Diepte

Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de XML-weer gave. De standaardwaarde is 1.

Als de eigenschappen van het object bijvoorbeeld ook objecten bevatten, om een XML-weer gave van de eigenschappen van de Inge sloten objecten op te slaan, moet u een diepte van 2 opgeven.

De standaard waarde kan worden overschreven voor het object type in de Types.ps1XML-bestanden. Zie about_Types.ps1XML voor meer informatie.

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

### -Input object

Geeft het object aan dat moet worden geconverteerd. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald. U kunt ook objecten door sluizen naar **ConvertTo-XML**.

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

### -NoTypeInformation

Laat het kenmerk type van de object knooppunten.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt elk object door sluizen naar **ConvertTo-XML**.

## UITVOER

### Systeem. teken reeks of System.Xml.Xmldocument

De waarde van de *as* -para meter bepaalt het type object dat **ConvertTo-XML** retourneert.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Html](ConvertTo-Html.md)

[Exporteren-Clixml](Export-Clixml.md)

[Ophalen datum](Get-Date.md)

[Import-Clixml](Import-Clixml.md)

