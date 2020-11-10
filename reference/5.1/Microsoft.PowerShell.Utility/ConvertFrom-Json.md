---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: e1bab9250269dadf0d899f9e172e8a4a8387271d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388124"
---
# ConvertFrom-Json

## SAMENVATTING
Converteert een teken reeks in JSON-indeling naar een aangepast object.

## SYNTAXIS

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## BESCHRIJVING

Met de `ConvertFrom-Json` cmdlet wordt een met JavaScript object Notation (JSON) opgemaakte teken reeks geconverteerd naar een aangepast **PSCustomObject** -object met een eigenschap voor elk veld in de JSON-teken reeks. JSON wordt doorgaans door websites gebruikt om een tekstuele representatie van objecten te bieden. De JSON-standaard verhindert niet het gebruik dat is verboden met een **PSCustomObject**. Als de JSON-teken reeks bijvoorbeeld dubbele sleutels bevat, wordt alleen de laatste sleutel gebruikt door deze cmdlet. Zie andere voor beelden hieronder.

Als u een JSON-teken reeks wilt genereren vanuit een wille keurig object, gebruikt u de `ConvertTo-Json` cmdlet.

Deze cmdlet is geïntroduceerd in Power Shell 3,0.

> [!NOTE]
> Deze cmdlet biedt geen ondersteuning voor JSON met opmerkingen.

## VOORBEELDEN

### Voor beeld 1: een DateTime-object converteren naar een JSON-object

Met deze opdracht worden de- `ConvertTo-Json` en- `ConvertFrom-Json` cmdlets gebruikt om een **DateTime** -object van de cmdlet om te zetten naar een JSON- `Get-Date` object en vervolgens naar een **PSCustomObject**.

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

In het voor beeld wordt de `Select-Object` cmdlet gebruikt om alle eigenschappen van het **DateTime** -object op te halen. De cmdlet wordt gebruikt `ConvertTo-Json` om het **DateTime** -object te converteren naar een teken reeks die is OPGEMAAKT als een JSON-object en de `ConvertFrom-Json` cmdlet om de teken reeks in JSON-indeling te converteren naar een **PSCustomObject** -object.

### Voor beeld 2: JSON-teken reeksen ophalen van een webservice en deze converteren naar Power shell-objecten

Met deze opdracht wordt de `Invoke-WebRequest` cmdlet gebruikt om JSON-teken reeksen op te halen uit een webservice en wordt vervolgens de `ConvertFrom-Json` cmdlet gebruikt om JSON-inhoud te converteren naar objecten die kunnen worden beheerd in Power shell.

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

U kunt ook de `Invoke-RestMethod` cmdlet gebruiken, waarmee JSON-inhoud automatisch naar objecten wordt geconverteerd.

### Voor beeld 3: een JSON-teken reeks converteren naar een aangepast object

In dit voor beeld ziet u hoe u de `ConvertFrom-Json` cmdlet gebruikt om een JSON-bestand te converteren naar een aangepast Power shell-object.

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

De opdracht gebruikt Get-Content cmdlet om de teken reeksen in een JSON-bestand op te halen. Vervolgens wordt de pijplijn operator gebruikt voor het verzenden van de gescheiden teken reeks naar de `ConvertFrom-Json` cmdlet, die deze converteert naar een aangepast object.

## PARAMETERS

### -Input object

Hiermee geeft u de JSON-teken reeksen op die moeten worden geconverteerd naar JSON-objecten. Voer een variabele in die de teken reeks bevat, of typ een opdracht of expressie die de teken reeks ophaalt. U kunt ook een teken reeks aan een pipe door geven `ConvertFrom-Json` .

De para meter **input object** is vereist, maar de waarde kan een lege teken reeks zijn. Wanneer het invoer object een lege teken reeks is, wordt `ConvertFrom-Json` er geen uitvoer gegenereerd. De **input object** -waarde kan niet zijn `$null` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een JSON-teken reeks door sluizen naar `ConvertFrom-Json` .

## UITVOER

### PSCustomObject

## OPMERKINGEN

De `ConvertFrom-Json` cmdlet wordt geïmplementeerd met behulp van de [JavaScriptSerializer-klasse](/dotnet/api/system.web.script.serialization.javascriptserializer).

## GERELATEERDE KOPPELINGEN

[Een inleiding tot JavaScript Object Notation (JSON) in Java script en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
