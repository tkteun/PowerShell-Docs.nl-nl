---
description: Hierin worden de regels voor het gebruik van enkele en dubbele aanhalings tekens in Power shell beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 8d09171a1459a8ad03b54f2a4ef7a81c5983f6b8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252657"
---
# <a name="about-quoting-rules"></a>Over quot-regels

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de regels voor het gebruik van enkele en dubbele aanhalings tekens in Power shell beschreven.

## <a name="long-description"></a>LANGE BESCHRIJVING

Aanhalings tekens worden gebruikt om een letterlijke teken reeks op te geven. U kunt een teken reeks tussen enkele aanhalings tekens ( `'` ) of tussen dubbele aanhalings tekens plaatsen ( `"` ).

Aanhalings tekens worden ook gebruikt voor het maken van een hier-teken reeks. Een hier-teken reeks is een teken reeks met enkele aanhalings tekens of dubbele aanhalings tekens waarin de aanhaling markeringen letterlijk worden geïnterpreteerd. Een hier-teken reeks kan meerdere regels omvatten. Alle regels in een hier-teken reeks worden geïnterpreteerd als teken reeksen, zelfs als ze niet tussen aanhalings tekens staan.

In opdrachten voor externe computers definiëren de aanhalings tekens de onderdelen van de opdracht die worden uitgevoerd op de externe computer. In een externe sessie bepaalt u met aanhalings tekens ook of de variabelen in een opdracht eerst worden geïnterpreteerd op de lokale computer of op de externe computer.

### <a name="single-and-double-quoted-strings"></a>TEKEN REEKSEN MET ENKELE EN DUBBELE AANHALINGS TEKENS

Wanneer u een teken reeks tussen dubbele aanhalings tekens (een teken reeks met dubbele aanhalings tekens) plaatst, worden namen van variabelen die worden voorafgegaan door een dollar teken ( `$` ) vervangen door de waarde van de variabele voordat de teken reeks wordt door gegeven aan de opdracht voor verwerking.

Bijvoorbeeld:

```powershell
$i = 5
"The value of $i is $i."
```

De uitvoer van deze opdracht is:

```Output
The value of 5 is 5.
```

In een teken reeks met dubbele aanhalings tekens worden expressies ook geëvalueerd en wordt het resultaat in de teken reeks ingevoegd. Bijvoorbeeld:

```powershell
"The value of $(2+3) is 5."
```

De uitvoer van deze opdracht is:

```Output
The value of 5 is 5.
```

Wanneer u een teken reeks tussen enkele aanhalings tekens plaatst (een teken reeks met één aanhalings tekens), wordt de teken reeks door gegeven aan de opdracht exact zoals u deze typt. Er wordt geen vervanging uitgevoerd. Bijvoorbeeld:

```powershell
$i = 5
'The value of $i is $i.'
```

De uitvoer van deze opdracht is:

```Output
The value $i is $i.
```

Op dezelfde manier worden expressies in teken reeksen met enkele aanhalings tekens niet geëvalueerd. Ze worden geïnterpreteerd als letterlijke waarden. Bijvoorbeeld:

```powershell
'The value of $(2+3) is 5.'
```

De uitvoer van deze opdracht is:

```Output
The value of $(2+3) is 5.
```

Als u wilt voor komen dat een variabele waarde in een teken reeks met dubbele aanhalings tekens wordt vervangen, gebruikt u het teken () apostroffen ( `` ` `` ) (ASCII 96). Dit is het Power shell-escape-teken.

In het volgende voor beeld wordt het apostroffen-teken dat voorafgaat aan de eerste $i variabele, voor komt dat Power shell de naam van de variabele vervangt door de waarde ervan.
Bijvoorbeeld:

```powershell
$i = 5
"The value of `$i is $i."
```

De uitvoer van deze opdracht is:

```Output
The value $i is 5.
```

Als u dubbele aanhalings tekens in een teken reeks wilt weer geven, plaatst u de hele teken reeks tussen enkele aanhalings tekens. Bijvoorbeeld:

```powershell
'As they say, "live and learn."'
```

De uitvoer van deze opdracht is:

```Output
As they say, "live and learn."
```

U kunt ook een teken reeks met enkele aanhalings tekens insluiten in een teken reeks met dubbele aanhalings tekens. Bijvoorbeeld:

```powershell
"As they say, 'live and learn.'"
```

De uitvoer van deze opdracht is:

```Output
As they say, 'live and learn.'
```

U kunt ook dubbele aanhalings tekens plaatsen rond een tekst met dubbele aanhalings tekens. Bijvoorbeeld:

```powershell
"As they say, ""live and learn."""
```

De uitvoer van deze opdracht is:

```Output
As they say, "live and learn."
```

Als u één aanhalings teken wilt gebruiken in een teken reeks met één waarde, gebruikt u een tweede opeenvolgende enkele aanhalings tekens. Bijvoorbeeld:

```powershell
'don''t'
```

De uitvoer van deze opdracht is:

```Output
don't
```

Als u wilt forceren dat Power shell een dubbele aanhalings tekens letterlijk interpreteert, gebruikt u een apostroffen-teken. Dit voor komt dat Power shell het aanhalings teken interpreteert als teken reeks scheiding. Bijvoorbeeld:

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

Omdat de inhoud van teken reeksen met enkele aanhalings tekens letterlijk wordt geïnterpreteerd, wordt het apostroffen-teken beschouwd als een letterlijke teken en weer gegeven in de uitvoer.

### <a name="here-strings"></a>HIER-TEKEN REEKSEN

De offerte regels voor hier-teken reeksen zijn iets anders.

Een hier-teken reeks is een teken reeks met enkele aanhalings tekens of dubbele aanhalings tekens waarin de aanhaling markeringen letterlijk worden geïnterpreteerd. Een hier-teken reeks kan meerdere regels omvatten. Alle regels in een hier-teken reeks worden geïnterpreteerd als teken reeksen, zelfs als ze niet tussen aanhalings tekens staan.

Net als bij reguliere teken reeksen worden variabelen vervangen door hun waarden in dubbele aanhalings tekens. In een enkel aanhalings teken, worden variabelen niet vervangen door hun waarden.

U kunt hier teken reeksen voor elke tekst gebruiken, maar deze zijn vooral handig voor de volgende soorten tekst:

- Tekst die letterlijke aanhalings tekens bevat
- Meerdere tekst regels, zoals de tekst in een HTML-of XML-bestand
- De Help-tekst voor een script of functie document

Een hier-teken reeks kan een van de volgende indelingen hebben, waarbij `<Enter>` de nieuwe regel of het verborgen teken van de voor waarde die wordt toegevoegd, wordt weer gegeven wanneer u op de <kbd>Enter</kbd> -toets drukt.

Dubbele aanhalings tekens:

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

Enkele aanhalings tekens:

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

In beide indelingen moet het aanhalings teken sluiten het eerste teken in de regel zijn.

Een hier-teken reeks bevat alle tekst tussen de twee verborgen tekens. In de teken reeks hier worden alle aanhalings tekens letterlijk geïnterpreteerd. Bijvoorbeeld:

```powershell
@"
For help, type "get-help"
"@
```

De uitvoer van deze opdracht is:

```Output
For help, type "get-help"
```

Het gebruik van een hier-teken reeks kan vereenvoudigen met een teken reeks in een opdracht. Bijvoorbeeld:

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

De uitvoer van deze opdracht is:

```Output
Use a quotation mark (') to begin a string.
```

In hier worden enkele aanhalings tekens, variabelen worden letterlijk geïnterpreteerd en precies gereproduceerd. Bijvoorbeeld:

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

De uitvoer van deze opdracht is:

```Output
The $profile variable contains the path
of your PowerShell profile.
```

In dubbele aanhalings tekens, variabelen worden vervangen door hun waarden. Bijvoorbeeld:

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

De uitvoer van deze opdracht is:

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

Hier-teken reeksen worden meestal gebruikt om meerdere regels aan een variabele toe te wijzen. Met de volgende teken reeks wordt bijvoorbeeld een pagina met XML toegewezen aan de variabele $page.

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

Hier zijn teken reeksen ook een handige indeling voor de invoer van de `ConvertFrom-StringData` cmdlet, die hier teken reeksen converteert naar hash-tabellen.
Voor meer informatie raadpleegt u `ConvertFrom-StringData`.

## <a name="see-also"></a>ZIE OOK

[about_Special_Characters](about_Special_Characters.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
