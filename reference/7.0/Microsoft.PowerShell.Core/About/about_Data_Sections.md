---
description: Hierin worden gegevens secties uitgelegd, die teken reeksen en andere alleen-lezen gegevens van script logica isoleren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: b24ab9c47697ec62e1799784d4f0a3ae57351f2a
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879249"
---
# <a name="about-data-sections"></a>Gegevens secties

## <a name="short-description"></a>Korte beschrijving
Hierin worden gegevens secties uitgelegd, die teken reeksen en andere alleen-lezen gegevens van script logica isoleren.

## <a name="long-description"></a>Lange beschrijving

Scripts die zijn ontworpen voor Power shell kunnen een of meer gegevens secties hebben die alleen gegevens bevatten. U kunt een of meer gegevens secties in een script, functie of geavanceerde functie toevoegen. De inhoud van de sectie gegevens is beperkt tot een opgegeven subset van de Power shell-script taal.

Het scheiden van gegevens uit code logica maakt het gemakkelijker om zowel logica als gegevens te identificeren en beheren. U kunt hiermee afzonderlijke bron bestanden voor teken reeksen gebruiken voor tekst, zoals fout berichten en Help-teken reeksen. Ook wordt de code logica geïsoleerd, waardoor beveiligings-en validatie tests worden vergemakkelijkt.

In Power shell wordt de sectie gegevens gebruikt voor het ondersteunen van script intertalen.
U kunt gegevens secties gebruiken om het gemakkelijker te maken om teken reeksen te isoleren, te zoeken en te verwerken die worden vertaald in veel talen van de gebruikers interface (UI).

De sectie gegevens is een Power Shell 2,0-functie. Scripts met gegevens secties kunnen niet zonder revisie worden uitgevoerd in Power shell 1,0.

### <a name="syntax"></a>Syntax

De syntaxis voor een gegevens sectie is als volgt:

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

Het sleutel woord data is vereist. Het is niet hoofdletter gevoelig. De toegestane inhoud is beperkt tot de volgende elementen:

- Alle Power shell-Opera Tors, behalve `-match`
- `If`, `Else` en- `ElseIf` instructies
- De volgende automatische variabelen: `$PsCulture` , `$PsUICulture` , `$True` , `$False` en `$Null`
- Opmerkingen
- Pipelines
- Instructies gescheiden door punt komma's ( `;` )
- Letterlijke waarden, zoals de volgende:

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- Cmdlets die zijn toegestaan in een gegevens sectie. Standaard is alleen de `ConvertFrom-StringData` cmdlet toegestaan.
- Cmdlets die u in een gegevens sectie toestaat met behulp van de `-SupportedCommand` para meter.

Wanneer u de `ConvertFrom-StringData` cmdlet gebruikt in een gegevens gedeelte, kunt u de sleutel-waardeparen insluiten in teken reeksen met één of dubbele aanhalings tekens of in een enkele of dubbele aanhalings teken reeksen. Teken reeksen die variabelen en subexpressies bevatten, moeten echter worden inge sloten in teken reeksen met enkele aanhalings tekens of in een enkele aanhalings teken, zodat de variabelen niet worden uitgevouwen en de subexpressies niet uitvoerbaar zijn.

### <a name="-supportedcommand"></a>-SupportedCommand

`-SupportedCommand`Met de para meter kunt u aangeven dat een cmdlet of functie alleen gegevens genereert. Het is ontworpen om gebruikers toe te staan cmdlets en functies op te zetten in een gegevens sectie die ze hebben geschreven of getest.

De waarde van `-SupportedCommand` is een door komma's gescheiden lijst met een of meer cmdlets of functie namen.

De volgende gegevens sectie bevat bijvoorbeeld een door de gebruiker geschreven cmdlet, `Format-Xml` waarmee gegevens in een XML-bestand worden opgemaakt:

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a>Een gegevens sectie gebruiken

Als u de inhoud van een gegevens sectie wilt gebruiken, wijst u deze toe aan een variabele en gebruikt u een variabele notatie voor toegang tot de inhoud.

De volgende gegevens sectie bevat bijvoorbeeld een `ConvertFrom-StringData` opdracht waarmee de hier-teken reeks wordt omgezet in een hash-tabel. De hash-tabel is toegewezen aan de `$TextMsgs` variabele.

De `$TextMsgs` variabele maakt geen deel uit van de sectie gegevens.

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

Gebruik de volgende opdrachten om toegang te krijgen tot de sleutels en waarden in hash-tabel in `$TextMsgs` .

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

U kunt ook de naam van de variabele in de definitie van de sectie gegevens plaatsen. Bijvoorbeeld:

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

Het resultaat is hetzelfde als in het vorige voor beeld.

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a>Voorbeelden

Eenvoudige gegevens reeksen.

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

Teken reeksen die toegestane variabelen bevatten.

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

Een hier geciteerde teken reeks die gebruikmaakt van de `ConvertFrom-StringData` cmdlet:

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

Een dubbele aanhalings teken reeks die gebruikmaakt van de `ConvertFrom-StringData` cmdlet:

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

Een gegevens sectie die een door de gebruiker geschreven cmdlet bevat waarmee gegevens worden gegenereerd:

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a>Zie ook

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_If](about_If.md)

[about_Operators](about_Operators.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
