---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEFileCollection-object
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684596"
---
# <a name="the-isefilecollection-object"></a>Het ISEFileCollection-object

De **ISEFileCollection** object is een verzameling van **ISEFile** objecten. Een voorbeeld is de verzameling $psISE.CurrentPowerShellTab.Files.

## <a name="methods"></a>Methoden

### <a name="add-fullpath-"></a>Voeg\( \[fullPath\] \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Maakt en retourneert een nieuwe naamloos bestand en toegevoegd aan de verzameling. De **IsUntitled** eigenschap van het zojuist gemaakte bestand is **$true**.

**\[fullPath\]**  - optioneel het volledig opgegeven pad van het bestand de tekenreeks. Een uitzondering wordt gegenereerd als u de **fullPath** parameter en een relatief pad, of als u een bestandsnaam in plaats van het volledige pad gebruiken.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Verwijder\( bestand \[forceren\] \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee verwijdert u een opgegeven bestand van het huidige PowerShell-tabblad.

**Bestand** -tekenreeks het ISEFile-bestand dat u wilt verwijderen uit de verzameling. Als het bestand niet is opgeslagen, wordt met deze methode een uitzondering genereert. Gebruik de **forceren** overschakelen van de parameter als u wilt afdwingen dat het verwijderen van een niet-opgeslagen bestand.

**\[Force\]**  -optionele Booleaanse als ingesteld op **$true**, een machtiging verleend voor het verwijderen van het bestand, zelfs als deze niet na het laatst hebt gebruikt opgeslagen is. De standaardwaarde is **$false**.

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

**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile het ISEFile-bestand dat u wilt selecteren.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Zie ook

- [Het ISEFile-Object](The-ISEFile-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)