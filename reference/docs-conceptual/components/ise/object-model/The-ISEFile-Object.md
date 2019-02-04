---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEFile-object
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 24549720b8bc35435882533b0eb138de432ede65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685135"
---
# <a name="the-isefile-object"></a>Het ISEFile-object

Een **ISEFile** object vertegenwoordigt een bestand in Windows PowerShell® Integrated Scripting Environment (ISE). Het is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEFile. In dit onderwerp bevat de methoden en lideigenschappen. De **$psISE.CurrentFile** en de bestanden in de verzameling bestanden in een PowerShell-tabblad zijn alle exemplaren van de klasse Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Methoden

### <a name="save-saveencoding-"></a>Sla\( \[saveEncoding\] \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee slaat u het bestand op schijf.

**\[saveEncoding\]**  - optioneel [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering parameter moet worden gebruikt voor het opgeslagen bestand. De standaardwaarde is **UTF8**.

### <a name="exceptions"></a>Uitzonderingen

- **System.IO.IOException**: Het bestand kan niet worden opgeslagen.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>Opslaan\(filename, \[saveEncoding\]\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee slaat u het bestand met de opgegeven bestandsnaam en de codering.

**FileName** -tekenreeks van de naam moet worden gebruikt om op te slaan van het bestand.

**\[saveEncoding\]**  - optioneel [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering parameter moet worden gebruikt voor het opgeslagen bestand. De standaardwaarde is **UTF8**.

### <a name="exceptions"></a>Uitzonderingen

- **System.ArgumentNullException**: De **filename** -parameter is null.
- **System.ArgumentException**: De **filename** parameter is leeg.
- **System.IO.IOException**: Het bestand kan niet worden opgeslagen.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Eigenschappen

### <a name="displayname"></a>DisplayName

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de tekenreeks zijn met de naam van dit bestand opgehaald. De naam wordt weergegeven op de **bestand** tabblad aan de bovenkant van de editor. De aanwezigheid van een sterretje \( \* \) aan het einde van de naam van de geeft aan dat het bestand heeft die niet zijn opgeslagen.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Editor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die krijgt de [editor-object](The-ISEEditor-Object.md) die wordt gebruikt voor het opgegeven bestand.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Encoding

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de oorspronkelijke bestandscodering opgehaald. Dit is een **System.Text.Encoding** object.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de tekenreeks die Hiermee geeft u het volledige pad van het geopende bestand opgehaald.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen Booleaanse eigenschap waarmee wordt geretourneerd **$true** als het bestand is opgeslagen nadat het laatst is gewijzigd.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die retourneert **$true** als het bestand nooit een titel ontvangen heeft.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Zie ook

- [De ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)