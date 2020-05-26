---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Het ISEFile-object
ms.openlocfilehash: 1069e46aa586b8df2050129194a909b90f77b745
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811224"
---
# <a name="the-isefile-object"></a>Het ISEFile-object

Een **ISEFile** -object vertegenwoordigt een bestand in Windows power shell® Integrated Scripting Environment (ISE). Het is een exemplaar van de klasse **micro soft. Power shell. host. ISE. ISEFile** . In dit onderwerp worden de methoden en lideigenschappen van leden vermeld. De `$psISE.CurrentFile` bestanden in de verzameling bestanden in een Power shell-tabblad zijn alle exemplaren van de klasse * * * * micro soft. Power shell. host. ISE. ISEFile * *.

## <a name="methods"></a>Methoden

### <a name="save-saveencoding-"></a>\( \[ SaveEncoding \] opslaan\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee slaat u het bestand op schijf.

** \[ saveEncoding \] ** -optioneel [System. Text. encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optionele teken coderings parameter die moet worden gebruikt voor het opgeslagen bestand. De standaard waarde is **utf8**.

### <a name="exceptions"></a>Uitzonderingen

- **System. io. IOException**: het bestand kan niet worden opgeslagen.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>\(Bestands naam: opslaan als, \[ saveEncoding\]\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee slaat u het bestand op met de opgegeven bestands naam en-code ring.

**Bestands naam** : de naam van de teken reeks die moet worden gebruikt om het bestand op te slaan.

** \[ saveEncoding \] ** -optioneel [System. Text. encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optionele teken coderings parameter die moet worden gebruikt voor het opgeslagen bestand. De standaard waarde is **utf8**.

### <a name="exceptions"></a>Uitzonderingen

- **System. ArgumentNullException**: de **filename** -para meter is null.
- **System. ArgumentException**: de **filename** -para meter is leeg.
- **System. io. IOException**: het bestand kan niet worden opgeslagen.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Eigenschappen

### <a name="displayname"></a>DisplayName

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de teken reeks wordt opgehaald die de weergave naam van dit bestand bevat. De naam wordt weer gegeven op het tabblad **bestand** boven aan de editor. De aanwezigheid van een sterretje `(*)` aan het einde van de naam geeft aan dat het bestand wijzigingen bevat die niet zijn opgeslagen.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Editor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee het [object editor](The-ISEEditor-Object.md) wordt opgehaald dat voor het opgegeven bestand wordt gebruikt.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Encoding

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de oorspronkelijke bestands codering wordt opgehaald. Dit is een **System. Text. encoding** -object.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>Pad

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de teken reeks wordt opgehaald die het volledige pad van het geopende bestand opgeeft.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen Booleaanse eigenschap die retourneert `$true` als het bestand is opgeslagen nadat het voor het laatst is gewijzigd.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap die retourneert `$true` als er nooit een titel is opgegeven voor het bestand.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Zie ook

- [De ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Doel van het scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De ISE-object model hiërarchie](The-ISE-Object-Model-Hierarchy.md)
