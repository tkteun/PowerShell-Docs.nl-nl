---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEFileCollection-object
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="the-isefilecollection-object"></a>Het ISEFileCollection-object

De **ISEFileCollection** object is een verzameling **ISEFile** objecten. Een voorbeeld is de verzameling $psISE.CurrentPowerShellTab.Files.

## <a name="methods"></a>Methoden

### <a name="add-fullpath-"></a>Voeg\( \[fullPath\] \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Maakt een nieuw bestand naamloze retourneert en voegt het toe aan de verzameling. De **IsUntitled** eigenschap van het nieuwe bestand is **$true**.

**\[fullPath\]**  : optioneel het volledig opgegeven pad van het bestand string. Er is een uitzondering gegenereerd als u de **fullPath** parameter en een relatief pad, of als u een bestandsnaam in plaats van het volledige pad gebruikt.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Verwijder\( bestand \[forceren\] \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Verwijdert een opgegeven bestand uit het huidige PowerShell-tabblad.

**Bestand** -tekenreeks de ISEFile-bestand dat u wilt verwijderen uit de verzameling. Als het bestand niet opgeslagen is, is deze methode er een uitzondering gegenereerd. Gebruik de **forceren** overschakelen van de parameter voor het afdwingen van het verwijderen van een niet-opgeslagen bestand.

**\[Force\]**  -optionele Booleaanse als ingesteld op **$true**, verleent u machtiging voor het verwijderen van het bestand, zelfs als deze niet na de laatste keer is opgeslagen. De standaardwaarde is **$false**.

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

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee selecteert u het bestand dat is opgegeven door de **selectedFile** parameter.

**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile de ISEFile-bestand dat u wilt selecteren.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Zie ook

- [Het Object ISEFile](The-ISEFile-Object.md)
- [Doel van de Windows PowerShell ISE-objectmodel Scripting](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)