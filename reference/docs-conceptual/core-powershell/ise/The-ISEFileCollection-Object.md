---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: 60bf4dae33f3a71c31e7fdbed0f4fd6ab27a8bd1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefilecollection-object"></a>Het Object ISEFileCollection
  De **ISEFileCollection** object is een verzameling **ISEFile** objecten. Een voorbeeld is de verzameling $psISE.CurrentPowerShellTab.Files.

## <a name="methods"></a>Methoden

### <a name="add-fullpath-"></a>Voeg\( \[fullPath\]\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Maakt een nieuw bestand naamloze retourneert en voegt het toe aan de verzameling. De **IsUntitled** eigenschap van het nieuwe bestand is **$true**.

 **\[fullPath\]**  : optioneel het volledig opgegeven pad van het bestand string. Er is een uitzondering gegenereerd als u de **fullPath** parameter en een relatief pad, of als u een bestandsnaam in plaats van het volledige pad gebruikt.

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a>Verwijder\( bestand \[Force\]\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Verwijdert een opgegeven bestand uit het huidige PowerShell-tabblad.

 **Bestand** -tekenreeks de ISEFile-bestand dat u wilt verwijderen uit de verzameling. Als het bestand niet opgeslagen is, is deze methode er een uitzondering gegenereerd. Gebruik de **forceren** overschakelen van de parameter voor het afdwingen van het verwijderen van een niet-opgeslagen bestand.

 **\[Force\]**  -optionele Booleaanse als ingesteld op **$true**, verleent u machtiging voor het verwijderen van het bestand, zelfs als deze niet na de laatste keer is opgeslagen. De standaardwaarde is **$false**.

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Hiermee selecteert u het bestand dat is opgegeven door de **selectedFile** parameter.

 **selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile de ISEFile-bestand dat u wilt selecteren.

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a>Zie ook
- [Het Object ISEFile](The-ISEFile-Object.md) 
- [De Windows PowerShell ISE-objectmodel Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Naslaginformatie voor Windows PowerShell ISE-objectmodel](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [De hiërarchie ISE](The-ISE-Object-Model-Hierarchy.md)
