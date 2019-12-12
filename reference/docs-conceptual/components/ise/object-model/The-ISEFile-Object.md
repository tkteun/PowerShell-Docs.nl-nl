---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISEFile-object
ms.openlocfilehash: ebb5a35f6ea9d93eab633b9f4e6c84e4fddd6ae8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028959"
---
# <a name="the-isefile-object"></a>Het ISEFile-object

Een **ISEFile** -object vertegenwoordigt een bestand in Windows power shell® Integrated Scripting Environment (ISE). Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEFile. In dit onderwerp worden de methoden en lideigenschappen van leden vermeld. De **$psISE. CurrentFile** en de bestanden in de verzameling bestanden in een Power shell-tabblad zijn alle exemplaren van de klasse micro soft. Power shell. host. ISE. ISEFile.

## <a name="methods"></a>Methoden

### <a name="save-saveencoding-"></a>\( \[saveEncoding\] opslaan \)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee slaat u het bestand op schijf.

**\[saveEncoding\]** -optioneel [System. Text. encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optionele teken coderings parameter die moet worden gebruikt voor het opgeslagen bestand. De standaard waarde is **utf8**.

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

### <a name="saveasfilename-saveencoding"></a>SaveAs\(filename, \[saveEncoding\]\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee slaat u het bestand op met de opgegeven bestands naam en-code ring.

**Bestands naam** : de naam van de teken reeks die moet worden gebruikt om het bestand op te slaan.

**\[saveEncoding\]** -optioneel [System. Text. encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optionele teken coderings parameter die moet worden gebruikt voor het opgeslagen bestand. De standaard waarde is **utf8**.

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

De alleen-lezen eigenschap waarmee de teken reeks wordt opgehaald die de weergave naam van dit bestand bevat. De naam wordt weer gegeven op het tabblad **bestand** boven aan de editor. De aanwezigheid van een asterisk \(\*\) aan het einde van de naam geeft aan dat het bestand wijzigingen bevat die niet zijn opgeslagen.

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

De alleen-lezen Booleaanse eigenschap die **$True** retourneert als het bestand is opgeslagen nadat het voor het laatst is gewijzigd.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap die **$True** retourneert als er nooit een titel is opgegeven voor het bestand.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Zie ook

- [De ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
