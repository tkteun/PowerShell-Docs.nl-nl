---
ms.date: 12/31/2019
title: Het ISEFileCollection-object
description: Het ISEFileCollection-object is een verzameling ISEFile-objecten.
ms.openlocfilehash: 2feef1200c611d5181bcbc55d5464a0bd390084e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646747"
---
# <a name="the-isefilecollection-object"></a>Het ISEFileCollection-object

Het **ISEFileCollection** -object is een verzameling **ISEFile** -objecten. Een voor beeld is de `$psISE.CurrentPowerShellTab.Files` verzameling.

## <a name="methods"></a>Methoden

### <a name="add-fullpath-"></a>\( \[ FullPath \] toevoegen\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Maakt en retourneert een nieuw naamloos bestand en voegt het toe aan de verzameling. De eigenschap **IsUntitled** van het zojuist gemaakte bestand is `$true` .

**\[ FullPath \]** -optionele teken reeks het volledig opgegeven pad van het bestand. Er wordt een uitzonde ring gegenereerd als u de para meter **FullPath** en een relatief pad opneemt, of als u een bestands naam gebruikt in plaats van het volledige pad.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>\(Bestand verwijderen, \[ forceren \]\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee verwijdert u een opgegeven bestand van het huidige Power shell-tabblad.

**File** -teken reeks het ISEFile-bestand dat u wilt verwijderen uit de verzameling. Als het bestand niet is opgeslagen, genereert deze methode een uitzonde ring. Gebruik de para meter **forceren** om het verwijderen van een niet-opgeslagen bestand af te dwingen.

**\[ Force \]** -optionele Booleaanse waarde indien ingesteld op `$true` , geeft toestemming voor het verwijderen van het bestand, zelfs als het niet is opgeslagen na het laatste gebruik. De standaardwaarde is `$false`.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile \( selectedFile \)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee selecteert u het bestand dat is opgegeven door de para meter **SelectedFile** .

**SelectedFile** : micro soft. Power shell. host. ISE. ISEFile het ISEFile-bestand dat u wilt selecteren.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Zie ook

- [Het ISEFile-object](The-ISEFile-Object.md)
- [Doel van het scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De ISE-object model hi??rarchie](The-ISE-Object-Model-Hierarchy.md)
