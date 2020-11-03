---
title: about_Character_Encoding
description: Hierin wordt beschreven hoe teken codering in Power shell wordt gebruikt voor invoer en uitvoer van teken reeks gegevens.
ms.date: 10/21/2020
Locale: en-US
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
ms.openlocfilehash: 6e2f515f774d7bc333baf6346cd6c8bd517cb6fa
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/23/2020
ms.locfileid: "93253217"
---
# <a name="about_character_encoding"></a>about_Character_Encoding

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe teken codering in Power shell wordt gebruikt voor invoer en uitvoer van teken reeks gegevens.

## <a name="long-description"></a>Lange beschrijving

Unicode is een wereld wijde teken coderings standaard. Het systeem gebruikt Unicode uitsluitend voor teken-en teken reeks manipulatie. Raadpleeg [de Unicode-standaard](https://www.unicode.org/standard/standard.html)voor een gedetailleerde beschrijving van alle aspecten van Unicode.

Windows ondersteunt Unicode-en traditionele teken sets. Traditionele teken sets, zoals Windows-code pagina's, gebruiken 8-bits waarden of combi Naties van 8-bits waarden om de tekens weer te geven die worden gebruikt in een specifieke taal of instellingen voor geografische regio's.

Power Shell maakt standaard gebruik van een Unicode-tekenset. Meerdere cmdlets hebben echter een **Encoding** -para meter waarmee u code ring kunt opgeven voor een andere tekenset. Met deze para meter kunt u de specifieke teken codering kiezen die u nodig hebt voor interoperabiliteit met andere systemen en toepassingen.

De volgende cmdlets hebben de para meter **Encoding** :

- Micro soft. Power shell. Management
  - Add-Content
  - Get-Content
  - Set-Content
- Microsoft.PowerShell.Utility
  - Export-Clixml
  - Export-Csv
  - Export-PSSession
  - Format-Hex
  - Import-Csv
  - Out-File
  - Select-String
  - Send-MailMessage

## <a name="the-byte-order-mark"></a>De byte volgorde markering

De byte-order-Mark (BOM) is een _Unicode-hand tekening_ in de eerste paar bytes van een bestand of tekst stroom die aangeeft welke Unicode-code ring voor de gegevens wordt gebruikt. Zie het artikel [Byte Order Mark](https://wikipedia.org/wiki/Byte_order_mark) in Wikipedia voor meer informatie.

In Windows Power Shell maakt Unicode-code ring, behalve `UTF7` , altijd een stuk lijst. Power shell core wordt standaard ingesteld op `utf8NoBOM` alle tekst uitvoer.

Voor de beste algemene compatibiliteit kunt u geen stuk lijsten gebruiken in UTF-8-bestanden. UNIX-platforms en UNIX-erfgoed-hulpprogram ma's die ook worden gebruikt op Windows-platforms ondersteunen geen stuk lijsten.

Op dezelfde manier `UTF7` moet de code ring worden vermeden. UTF-7 is geen standaard Unicode-code ring en wordt zonder een stuk lijst in alle versies van Power shell geschreven.

Het maken van Power shell-scripts op een UNIX-soortgelijk platform of het gebruik van een platformoverschrijdende editor in Windows, zoals Visual Studio code, resulteert in een bestand dat is gecodeerd met `UTF8NoBOM` . Deze bestanden werken prima op Power shell core, maar kunnen in Windows Power shell worden verbroken als het bestand niet-ASCII-tekens bevat.

Als u niet-ASCII-tekens in uw scripts moet gebruiken, slaat u ze op als UTF-8 met een stuk lijst. Zonder de stuk lijst interpreteert Windows Power shell uw script niet op dezelfde manier als in de verouderde code ring ' ANSI '. Daarentegen kunnen bestanden met de UTF-8-stuk lijst problemen ondervinden op UNIX-achtige platformen. Veel Unix-hulpprogram ma's zoals `cat` ,, `sed` `awk` en sommige editors, zoals `gedit` weet niet hoe de stuk lijst moet worden behandeld.

## <a name="character-encoding-in-windows-powershell"></a>Teken codering in Windows Power shell

In Power shell 5,1 ondersteunt de para meter **Encoding** de volgende waarden:

- `Ascii` Maakt gebruik van ASCII-tekenset (7-bits).
- `BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.
- `BigEndianUTF32` Maakt gebruik van UTF-32 met de byte volgorde big endian.
- `Byte` Codeert een reeks tekens in een reeks bytes.
- `Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).
- `Oem` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.
- `String` Hetzelfde als `Unicode` .
- `Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.
- `Unknown` Hetzelfde als `Unicode` .
- `UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.
- `UTF7` Maakt gebruik van UTF-7.
- `UTF8` Maakt gebruik van UTF-8 (met stuk lijst).

In het algemeen maakt Windows Power Shell standaard gebruik van de Unicode [UTF-16LE-](https://wikipedia.org/wiki/UTF-16) code ring. De standaard codering die door cmdlets in Windows Power shell wordt gebruikt, is echter niet consistent.

> [!NOTE]
> Het gebruik van Unicode-code ring, behalve `UTF7` , maakt altijd een stuk lijst.

Voor cmdlets die uitvoer naar bestanden schrijven:

- `Out-File` en de omleidings operatoren `>` en `>>` maken UTF-16LE, die met name afwijken van `Set-Content` en `Add-Content` .

- `New-ModuleManifest` en `Export-CliXml` maken ook UTF-16LE-bestanden.

- Wanneer het doel bestand leeg is of niet bestaat, `Set-Content` en `Add-Content` gebruikmaakt van `Default` code ring. `Default` is de code ring die is opgegeven door de ANSI legacy-code tabel van het actieve systeem.

- `Export-Csv` Hiermee maakt `Ascii` u bestanden, maar gebruikt u een andere code ring wanneer u **Append** para meter gebruikt (zie hieronder).

- `Export-PSSession` maakt standaard UTF-8-bestanden met een stuk lijst.

- `New-Item -Type File -Value` Hiermee maakt u een stuk lijst zonder UTF-8-bestand.

- `Send-MailMessage` maakt gebruik `Default` van code ring standaard.

- `Start-Transcript` Hiermee maakt u `Utf8` bestanden met een stuk lijst. Wanneer de para meter **Append** wordt gebruikt, kan de code ring verschillen (zie hieronder).

Voor opdrachten die worden toegevoegd aan een bestaand bestand:

- `Out-File -Append` de `>>` omleidings operator maakt geen poging om de code ring van de bestaande inhoud van het doel bestand te vergelijken. In plaats daarvan gebruiken ze de standaard codering tenzij de para meter **Encoding** wordt gebruikt. U moet de bestanden originele code ring gebruiken bij het toevoegen van inhoud.

- Als er geen expliciete **Encoding** -para meter is, `Add-Content` detecteert de bestaande code ring en past deze automatisch toe op de nieuwe inhoud. Als de bestaande inhoud geen stuk lijst heeft, `Default` wordt ANSI-code ring gebruikt. Het gedrag van `Add-Content` is hetzelfde in Power shell core (V6 en hoger), met uitzonde ring van de standaard codering `Utf8` .

- `Export-Csv -Append` komt overeen met de bestaande code ring wanneer het doel bestand een stuk lijst bevat. Als er geen stuk lijst is, wordt `Utf8` code ring gebruikt.

- `Start-Transcript -Append` komt overeen met de bestaande code ring van bestanden die een stuk lijst bevatten. Als er geen stuk lijst wordt gebruikt, wordt de standaard waarde `Ascii` gecodeerd. Deze code ring kan leiden tot gegevens verlies of beschadiging van het teken als de gegevens in de transcripten multi byte-tekens bevatten.

Voor cmdlets die teken reeks gegevens lezen in afwezigheid van een stuk lijst:

- `Get-Content` en `Import-PowerShellDataFile` maakt gebruik van de `Default` ANSI-code ring. ANSI is ook wat de Power shell-engine gebruikt bij het lezen van de bron code van bestanden.

- `Import-Csv`, `Import-CliXml` en `Select-String` ervan uitgaan dat `Utf8` er geen stuk lijst is.

## <a name="character-encoding-in-powershell-core"></a>Teken codering in Power shell core

In Power shell core (V6 en hoger) ondersteunt de para meter **Encoding** de volgende waarden:

- `ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).
- `bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.
- `oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.
- `unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.
- `utf7`: Wordt gecodeerd in de indeling UTF-7.
- `utf8`: Wordt gecodeerd in UTF-8-indeling (geen stuk lijst).
- `utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)
- `utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)
- `utf32`: Gecodeerd in UTF-32-indeling.

Power shell Core is standaard ingesteld op `utf8NoBOM` alle uitvoer.

Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` . Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage)voor meer informatie.

## <a name="changing-the-default-encoding"></a>De standaard codering wijzigen

Power Shell heeft twee standaard variabelen die kunnen worden gebruikt om het standaard coderings gedrag te wijzigen.

- `$PSDefaultParameterValues`
- `$OutputEncoding`

Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie.

Vanaf Power shell 5,1 roept de omleidings operator ( `>` en `>>` ) de `Out-File` cmdlet aan. Daarom kunt u de standaard codering instellen met behulp van de `$PSDefaultParameterValues` Voorkeurs variabele, zoals wordt weer gegeven in dit voor beeld:

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

Gebruik de volgende instructie om de standaard codering te wijzigen voor alle cmdlets die de para meter **Encoding** hebben.

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> Als u deze opdracht in uw Power shell-profiel plaatst, wordt de voor keur een sessie-algemene instelling die van invloed is op alle opdrachten en scripts die geen expliciete code ring opgeven.
>
> Daarnaast moet u dergelijke opdrachten in uw scripts of modules insluiten die op dezelfde manier werken. Met deze opdrachten zorgt u ervoor dat cmdlets op dezelfde manier werken, zelfs wanneer ze worden uitgevoerd door een andere gebruiker, op een andere computer of in een andere versie van Power shell.

De automatische variabele `$OutputEncoding` is van invloed op de code ring Power shell die wordt gebruikt om te communiceren met externe Program ma's. Dit heeft geen invloed op de code ring die door de Opera tors voor uitvoer omleiding en Power shell-cmdlets wordt gebruikt om bestanden op te slaan.

## <a name="see-also"></a>Zie ook

- [Inleiding tot teken codering in .NET](/dotnet/standard/base-types/character-encoding-introduction)
- [Code pagina's-Win32-apps](/windows/win32/intl/code-pages)
- [De Unicode-standaard](https://www.unicode.org/standard/standard.html)
- [Encoding. code tabel](/dotnet/api/system.text.encoding.codepage)
- [UTF-16LE](https://wikipedia.org/wiki/UTF-16)
- [Byte order markering](https://wikipedia.org/wiki/Byte_order_mark)
- [about_Preference_Variables](about_Preference_Variables.md)
