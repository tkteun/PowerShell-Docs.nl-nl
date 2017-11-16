---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a>Het Object ISEFile
  Een **ISEFile** object vertegenwoordigt een bestand in Windows PowerShell® Integrated Scripting Environment (ISE). Er is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEFile. In dit onderwerp bevat de methoden en eigenschappen van lid. De **$psISE.CurrentFile** en de bestanden in de verzameling bestanden op een tabblad PowerShell zijn alle exemplaren van de klasse Microsoft.PowerShell.Host.ISE.ISEFile.

## <a name="methods"></a>Methoden

### <a name="save-saveencoding-"></a>Sla\( \[saveEncoding\]\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Het bestand opslaat op schijf.

 **\[saveEncoding\]**  : optioneel [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering van de parameter moet worden gebruikt voor het opgeslagen bestand. De standaardwaarde is **UTF8**.

 **Uitzonderingen**
 -   **System.IO.IOException**: het bestand kan niet worden opgeslagen.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(bestandsnaam, \[saveEncoding\]\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Hiermee slaat u het bestand met de opgegeven bestandsnaam en de codering.

 **bestandsnaam** -tekenreeks van de naam die moet worden gebruikt voor het opslaan van het bestand.

 **\[saveEncoding\]**  : optioneel [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering van de parameter moet worden gebruikt voor het opgeslagen bestand. De standaardwaarde is **UTF8**.

 **Uitzonderingen**
 -   **System.ArgumentNullException**: de **filename** -parameter is null.

- **System.ArgumentException**: de **filename** parameter is leeg.

- **System.IO.IOException**: het bestand kan niet worden opgeslagen.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a>Eigenschappen

### <a name="displayname"></a>DisplayName
  In Windows PowerShell ISE 2.0 en hoger ondersteund.

 De alleen-lezen eigenschap waarin de tekenreeks met de weergavenaam van dit bestand worden opgehaald. De naam wordt weergegeven op de **bestand** boven op het tabblad van de editor. De aanwezigheid van een sterretje \( \* \) aan het einde van de naam geeft aan dat het bestand wijzigingen die niet zijn opgeslagen.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a>Editor
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 De alleen-lezen eigenschap die krijgt de [editor-object](The-ISEEditor-Object.md) die wordt gebruikt voor het opgegeven bestand.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a>Codering
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 De alleen-lezen eigenschap die de oorspronkelijke bestandscodering opgehaald. Dit is een **System.Text.Encoding** object.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a>FullPath
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 De alleen-lezen eigenschap die de tekenreeks die opgeeft van het volledige pad van het geopende bestand opgehaald.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a>IsSaved
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 De alleen-lezen Boole-eigenschap die als resultaat geeft **$true** als het bestand is opgeslagen nadat het laatst is gewijzigd.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a>IsUntitled
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 De alleen-lezen eigenschap die retourneert **$true** als het bestand nooit een titel gegeven is.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a>Zie ook
- [De ISEFileCollectionObject](The-ISEFileCollection-Object.md) 
- [De Windows PowerShell ISE-objectmodel Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Naslaginformatie voor Windows PowerShell ISE-objectmodel](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [De hiërarchie ISE](The-ISE-Object-Model-Hierarchy.md)
