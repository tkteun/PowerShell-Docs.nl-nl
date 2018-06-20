---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEFile-object
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 276e8f04a827e18999b5b3ecb08f47de4f4b23b1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951389"
---
# <a name="the-isefile-object"></a>Het ISEFile-object

Een **ISEFile** object vertegenwoordigt een bestand in Windows PowerShell® Integrated Scripting Environment (ISE). Er is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEFile. In dit onderwerp bevat de methoden en eigenschappen van lid. De **$psISE.CurrentFile** en de bestanden in de verzameling bestanden op een tabblad PowerShell zijn alle exemplaren van de klasse Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Methoden

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Het bestand opslaat op schijf.

**\[saveEncoding\]**  : optioneel [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering van de parameter moet worden gebruikt voor het opgeslagen bestand. De standaardwaarde is **UTF8**.

### <a name="exceptions"></a>Uitzonderingen

- **System.IO.IOException**: het bestand kan niet worden opgeslagen.

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

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee slaat u het bestand met de opgegeven bestandsnaam en de codering.

**bestandsnaam** -tekenreeks van de naam die moet worden gebruikt voor het opslaan van het bestand.

**\[saveEncoding\]**  : optioneel [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering van de parameter moet worden gebruikt voor het opgeslagen bestand. De standaardwaarde is **UTF8**.

### <a name="exceptions"></a>Uitzonderingen

- **System.ArgumentNullException**: de **filename** -parameter is null.
- **System.ArgumentException**: de **filename** parameter is leeg.
- **System.IO.IOException**: het bestand kan niet worden opgeslagen.

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

De alleen-lezen eigenschap waarin de tekenreeks met de weergavenaam van dit bestand worden opgehaald. De naam wordt weergegeven op de **bestand** boven op het tabblad van de editor. De aanwezigheid van een sterretje \( \* \) aan het einde van de naam geeft aan dat het bestand wijzigingen die niet zijn opgeslagen.

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

### <a name="encoding"></a>Codering

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de oorspronkelijke bestandscodering opgehaald. Dit is een **System.Text.Encoding** object.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de tekenreeks die opgeeft van het volledige pad van het geopende bestand opgehaald.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen Boole-eigenschap die als resultaat geeft **$true** als het bestand is opgeslagen nadat het laatst is gewijzigd.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die retourneert **$true** als het bestand nooit een titel gegeven is.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Zie ook

- [De ISEFileCollectionObject](The-ISEFileCollection-Object.md)
- [Doel van de Windows PowerShell ISE-objectmodel Scripting](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)