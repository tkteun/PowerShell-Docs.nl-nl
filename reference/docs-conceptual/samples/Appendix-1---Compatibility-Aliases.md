---
ms.date: 09/09/2019
keywords: Power shell, cmdlet
title: Bijlage 1 - Compatibiliteitsaliassen
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848161"
---
# <a name="appendix-1---compatibility-aliases"></a>Bijlage 1-compatibiliteits aliassen

Power Shell heeft verschillende aliassen waarmee **UNIX** -en **cmd. exe** -gebruikers bekende opdrachten kunnen gebruiken.
De opdrachten en hun bijbehorende Power shell-cmdlet-en Power shell-alias worden weer gegeven in de volgende tabel:

|opdracht cmd. exe|UNIX-opdracht|Power shell-cmdlet|Power shell-alias|
|---------------|----------------|--------------|------------|
|**compatibiliteit**|**Maak**|`Clear-Host`functieassembly|`cls`|
|**Kopieer**|**p**|`Copy-Item`|`cpi`|
|**dir**|**1**|`Get-ChildItem`|`gci`|
|**type**|**cat**|`Get-Content`|`gc`|
|**Ga**|**MV**|`Move-Item`|`mi`|
|**MD**|**mkdir**|`New-Item`|`ni`|
|**pushd**|**pushd**|`Push-Location`|`pushd`|
|**popd**|**popd**|`Pop-Location`|`popd`|
|**del**, **wissen**, **RD**, **rmdir**|**RM**|`Remove-Item`|`ri`|
|**Outlook**|**MV**|`Rename-Item`|`rni`|
|**cd**, **chdir**|**-**|`Set-Location`|`sl`|

Als u de Power shell-aliassen wilt vinden, gebruikt u de cmdlet [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) . Als u de aliassen van een cmdlet wilt weer geven, gebruikt u de para meter **definitie** en geeft u de naam van de cmdlet op.
Als u de naam van de cmdlet van een alias wilt zoeken, gebruikt u de para meter **name** en geeft u de alias op.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
