---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: Bijlage 1 - Compatibiliteitsaliassen
ms.openlocfilehash: e5bd170fea6b6109d2ef4fd58863d6cc8a0e3ae1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758496"
---
# <a name="appendix-1---compatibility-aliases"></a>Bijlage 1-compatibiliteits aliassen

Power Shell heeft verschillende aliassen waarmee **UNIX** -en **cmd.exe** -gebruikers bekende opdrachten kunnen gebruiken.
De opdrachten en hun bijbehorende Power shell-cmdlet-en Power shell-alias worden weer gegeven in de volgende tabel:

|            cmd.exe opdracht            | UNIX-opdracht | Power shell-cmdlet | Power shell-alias |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| **cd**, **chdir**                     | **-**       | `Set-Location`    | `sl`             |
| **compatibiliteit**                               | **Maak**    | `Clear-Host`      | `cls`            |
| **Kopieer**                              | **p**       | `Copy-Item`       | `cpi`            |
| **del**, **wissen**, **RD**, **rmdir** | **RM**       | `Remove-Item`     | `ri`             |
| **dir**                               | **1**       | `Get-ChildItem`   | `gci`            |
| **echo**                              | **echo**     | `Write-Output`    | `write`          |
| **MD**                                | **mkdir**    | `New-Item`        | `ni`             |
| **Ga**                              | **MV**       | `Move-Item`       | `mi`             |
| **popd**                              | **popd**     | `Pop-Location`    | `popd`           |
| **pushd**                             | **pushd**    | `Push-Location`   | `pushd`          |
| **Outlook**                               | **MV**       | `Rename-Item`     | `rni`            |
| **type**                              | **Cat5**      | `Get-Content`     | `gc`             |

Als u de Power shell-aliassen wilt vinden, gebruikt u de cmdlet [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias) . Als u de aliassen van een cmdlet wilt weer geven, gebruikt u de para meter **definitie** en geeft u de naam van de cmdlet op.
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
