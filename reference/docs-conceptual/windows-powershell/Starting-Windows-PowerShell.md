---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: Windows PowerShell starten
description: In dit artikel wordt uitgelegd hoe u verschillende versies van Power shell kunt starten.
ms.openlocfilehash: 47da7d85c9f7e6966a7f7e809c77979cd24cf129
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664018"
---
# <a name="starting-windows-powershell"></a>Windows PowerShell starten

Windows Power shell is een script engine `.DLL` die is inge sloten in meerdere hosts. De meest voorkomende hosts die u start, zijn de interactieve opdracht regel `powershell.exe` en de interactieve script omgeving `powershell_ise.exe` .

Als u Windows Power shell wilt starten &reg; op Windows server &reg; 2012 R2, Windows &reg; 8,1, Windows Server 2012 en Windows 8, raadpleegt u [algemene beheer taken en navigatie in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).

## <a name="powershell-core-has-renamed-binary"></a>De naam van de Power shell Core is gewijzigd in binary

Power shell core, aangeduid als Power shell, is versie 6 en hoger van de open source en maakt gebruik van .NET core. Ondersteunde versies zijn beschikbaar in Windows, macOS en Linux.

Vanaf Power shell 6 heette het binaire bestand van Power shell een andere naam gekregen `pwsh.exe` voor Windows en `pwsh` voor MacOS en Linux. U kunt Power shell Preview-versies starten met `pwsh-preview` . Zie [What's New in Power shell Core 6,0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) en [about pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh)(Engelstalig) voor meer informatie.

Gebruik de volgende koppelingen om de cmdlet-Naslag informatie en de installatie documentatie voor Power shell 7 te vinden:

| Document | Koppeling |
| ----- | ----- |
| Cmdlet-naslaginformatie | [PowerShell-modulebrowser](/powershell/module/) |
| Windows-installatie | [PowerShell Core in Windows installeren](/powershell/scripting/install/installing-powershell-core-on-windows) |
| macOS-installatie | [Installing PowerShell Core on macOS](/powershell/scripting/install/installing-powershell-core-on-macos) (PowerShell Core installeren in macOS) |
| Linux-installatie | [Installing PowerShell Core on Linux](/powershell/scripting/install/installing-powershell-core-on-linux) (PowerShell Core installeren in Linux) |

Zie [de Power shell-documentatie gebruiken](../how-to-use-docs.md)om inhoud voor andere Power shell-versies weer te geven.

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Windows Power shell starten op eerdere versies van Windows

In deze sectie wordt uitgelegd hoe u Windows Power shell en Windows Power shell Integrated Scripting Environment (ISE) start op Windows &reg; 7, Windows Server &reg; 2008 R2 en Windows Server &reg; 2008. Ook wordt uitgelegd hoe u de optionele functie inschakelt voor Windows PowerShell ISE in Windows Power Shell 2,0 op Windows Server &reg; 2008 R2 en Windows server &reg; 2008.

Gebruik een van de volgende methoden om de geïnstalleerde versie van Windows Power Shell 3,0 of Windows Power Shell 4,0 te starten, indien van toepassing.

#### <a name="from-the-start-menu"></a>Vanuit het menu Start

- Klik op **Start** , typ **Power shell** en klik vervolgens op **Windows Power shell** .
- Klik in het menu **Start** op **Start** , klik op **alle Program ma's** , klik op **accessoires** , klik op de **Windows Power shell** -map en klik vervolgens op **Windows Power shell** .

#### <a name="at-the-command-prompt"></a>Bij de opdracht prompt

In **cmd.exe** , Windows Power shell of Windows PowerShell ISE om Windows Power shell te starten, typt u:

```
PowerShell
```

U kunt ook de para meters van het `powershell.exe` programma gebruiken om de sessie aan te passen. Zie [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe)voor meer informatie.

#### <a name="with-administrative-privileges-run-as-administrator"></a>Met beheerders bevoegdheden (als administrator uitvoeren)

Klik op **Start** , typ **Power shell** , klik met de rechter muisknop op **Windows Power shell** en klik vervolgens op **als administrator uitvoeren** .

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Windows PowerShell ISE starten op eerdere versies van Windows

Gebruik een van de volgende methoden om Windows PowerShell ISE te starten.

#### <a name="from-the-start-menu"></a>Vanuit het menu Start

- Klik op **Start** , typ **ISE** en klik vervolgens op **Windows PowerShell ISE** .
- Klik in het menu **Start** op **Start** , klik op **alle Program ma's** , klik op **accessoires** , klik op de **Windows Power shell** -map en klik vervolgens op **Windows PowerShell ISE** .

#### <a name="at-the-command-prompt"></a>Bij de opdracht prompt

In `cmd.exe` , Windows Power shell of Windows PowerShell ISE om Windows Power shell te starten, typt u:

```
PowerShell_ISE
```

of

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Met beheerders bevoegdheden (als administrator uitvoeren)

Klik op **Start** , typ **ISE** , klik met de rechter muisknop op **Windows PowerShell ISE** en klik vervolgens op **als administrator uitvoeren** .

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Windows PowerShell ISE inschakelen op eerdere versies van Windows

In Windows Power Shell 4,0 en Windows Power Shell 3,0 is Windows PowerShell ISE standaard ingeschakeld in alle versies van Windows. Als dit nog niet is ingeschakeld, wordt het door Windows Management Framework 4,0 of Windows Management Framework 3,0 ingeschakeld.

In Windows Power Shell 2,0 is Windows PowerShell ISE standaard ingeschakeld in Windows 7. In Windows Server 2008 R2 en Windows Server 2008 is het echter een optionele functie.

Gebruik de volgende procedure om Windows PowerShell ISE in te scha kelen in Windows Power Shell 2,0 op Windows Server 2008 R2 of Windows Server 2008.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Windows Power shell Integrated Scripting Environment (ISE) inschakelen

1. Start Serverbeheer.
2. Klik op **functies** en klik vervolgens op **onderdelen toevoegen** .
3. In functies selecteren klikt u op Windows Power shell Integrated Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>De 32-bits versie van Windows Power shell starten

Wanneer u Windows Power shell installeert op een 64-bits computer, wordt **Windows Power shell (x86)** , een 32-bits versie van Windows Power shell, naast de 64-bits versie geïnstalleerd. Wanneer u Windows Power shell uitvoert, wordt standaard de 64-bits versie uitgevoerd.

Het kan echter ook voor komen dat u **Windows Power shell (x86)** moet uitvoeren, bijvoorbeeld wanneer u een module gebruikt waarvoor de 32-bits versie vereist is of wanneer u extern verbinding maakt met een 32-bits computer.

Als u een 32-bits versie van Windows Power shell wilt starten, gebruikt u een van de volgende procedures.

#### <a name="in-windows-serverreg-2012-r2"></a>In Windows Server &reg; 2012 R2

- Typ **Windows Power shell (x86)** in het **Start** scherm. Klik op de tegel **Windows Power shell x86** .
- In **Serverbeheer** , in het menu **extra** , selecteert u **Windows Power shell (x86)** .
- Verplaats de cursor op het bureau blad naar de rechter bovenhoek, klik op **zoeken** , typ **Power shell x86** en klik vervolgens op **Windows Power shell (x86)** .
- Voer vanaf de opdracht regel het volgende in: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-serverreg-2012"></a>In Windows Server &reg; 2012

- Typ **Power shell** in het **Start** scherm en klik vervolgens op **Windows Power shell (x86)** .
- In **Serverbeheer** , in het menu **extra** , selecteert u **Windows Power shell (x86)** .
- Verplaats de cursor op het bureau blad naar de rechter bovenhoek, klik op **zoeken** , typ **Power shell** en klik vervolgens op **Windows Power shell (x86)** .
- Voer vanaf de opdracht regel het volgende in: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windowsreg-81"></a>In Windows &reg; 8,1

- Typ **Windows Power shell (x86)** in het **Start** scherm. Klik op de tegel **Windows Power shell x86** .
- Als u [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) uitvoert voor Windows 8,1, kunt u ook Windows Power shell x86 openen vanuit het menu van **Server beheer** . Selecteer **Windows Power shell (x86)** .
- Verplaats de cursor op het bureau blad naar de rechter bovenhoek, klik op **zoeken** , typ **Power shell x86** en klik vervolgens op **Windows Power shell (x86)** .
- Voer vanaf de opdracht regel het volgende in: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windowsreg-8"></a>In Windows &reg; 8

- Verplaats de cursor in het **Start** scherm naar de rechter bovenhoek, klik op **instellingen** , klik op **tegels** en verplaats de schuif regelaar **systeem beheer weer geven** naar **Ja** . Vervolgens typt u **Power shell** en klikt u op **Windows Power shell (x86)** .
- Als u [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) voor Windows 8 uitvoert, kunt u ook Windows Power shell x86 openen vanuit het menu van **Server beheer** . Selecteer **Windows Power shell (x86)** .
- Typ **Power shell (x86)** op het **Start** scherm of op het bureau blad en klik vervolgens op **Windows Power shell (x86)** .
- Voer vanaf de opdracht regel het volgende in: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
