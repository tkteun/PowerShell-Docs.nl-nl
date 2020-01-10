---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISEFileCollection-object
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736212"
---
# <a name="the-isefilecollection-object"></a>Het ISEFileCollection-object

Het **ISEFileCollection** -object is een verzameling **ISEFile** -objecten. Een voor beeld is de verzameling `$psISE.CurrentPowerShellTab.Files`.

## <a name="methods"></a>Methoden

### <a name="add-fullpath-"></a>\( \[FullPath\] \) toevoegen

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Maakt en retourneert een nieuw naamloos bestand en voegt het toe aan de verzameling. De eigenschap **IsUntitled** van het zojuist gemaakte bestand is `$true`.

**\[FullPath\]** -optionele teken reeks het volledig opgegeven pad van het bestand. Er wordt een uitzonde ring gegenereerd als u de para meter **FullPath** en een relatief pad opneemt, of als u een bestands naam gebruikt in plaats van het volledige pad.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>\(-bestand verwijderen \[forceren\] \)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee verwijdert u een opgegeven bestand van het huidige Power shell-tabblad.

**File** -teken reeks het ISEFile-bestand dat u wilt verwijderen uit de verzameling. Als het bestand niet is opgeslagen, genereert deze methode een uitzonde ring. Gebruik de para meter **forceren** om het verwijderen van een niet-opgeslagen bestand af te dwingen.

**\[dwing\]** -optionele Booleaanse waarde toe als deze is ingesteld op `$true`, geeft toestemming voor het verwijderen van het bestand, zelfs als het niet is opgeslagen na het laatst gebruikt. De standaardwaarde is `$false`.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

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
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
