---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Windows PowerShell starten
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 90f6992f47e62c1775cae216b4012f630e07558f
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/09/2018
---
# <a name="starting-windows-powershell"></a>Windows PowerShell starten
PowerShell is een scripting engine dll die is ingesloten in meerdere hosts.  De meest voorkomende host die u wilt beginnen met zijn de interactieve opdrachtregel PowerShell.exe en de interactieve Scripting omgeving PowerShell_ISE.exe.

Zie voor informatie over het starten van Windows PowerShell® op Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 en Windows 8 [Common Management Tasks and Navigation](http://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Het starten van Windows PowerShell op oudere versies van Windows

Deze sectie wordt uitgelegd hoe u Windows PowerShell en Windows PowerShell Integrated Scripting Environment (ISE) starten op Windows® 7, Windows Server® 2008 R2 en Windows Server® 2008. Ook wordt uitgelegd hoe u de optionele functie inschakelt voor Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server® 2008 R2 en Windows Server® 2008.

Een van de volgende methoden gebruiken om te starten van de geïnstalleerde versie van Windows PowerShell 3.0 of 4.0 voor Windows PowerShell, indien van toepassing.

#### <a name="from-the-start-menu"></a>Vanuit het startmenu

- Klik op **Start**, type **PowerShell**, en klik vervolgens op **Windows PowerShell**.
- Van de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Bij de opdrachtprompt

In Cmd.exe, Windows PowerShell of Windows PowerShell ISE voor het starten van Windows PowerShell typt u:

```
PowerShell
```

U kunt ook de parameters van het programma PowerShell.exe gebruiken voor het aanpassen van de sessie. Zie voor meer informatie [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Met Administrative bevoegdheden ('als administrator uitvoeren")

Klik op **Start**, type **PowerShell**, met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als administrator uitvoeren**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Het starten van Windows PowerShell ISE voor eerdere versies van Windows

Gebruik een van de volgende methoden om te starten van Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Vanuit het startmenu

- Klik op **Start**, type **ISE**, en klik vervolgens op **Windows PowerShell ISE**.
- Van de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>Bij de opdrachtprompt

In Cmd.exe, Windows PowerShell of Windows PowerShell ISE voor het starten van Windows PowerShell typt u:

```
PowerShell_ISE
```

of

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Met Administrative bevoegdheden ('als administrator uitvoeren")

Klik op **Start**, type **ISE**, met de rechtermuisknop op **Windows PowerShell ISE**, en klik vervolgens op **als administrator uitvoeren**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Het inschakelen van Windows PowerShell ISE voor eerdere versies van Windows

In Windows PowerShell 4.0 en Windows PowerShell 3.0, is Windows PowerShell ISE standaard ingeschakeld op alle versies van Windows. Als deze nog niet is ingeschakeld, schakelt Windows Management Framework 4.0 of Windows Management Framework 3.0 deze.

In Windows PowerShell 2.0, is Windows PowerShell ISE standaard ingeschakeld op Windows 7. Op Windows Server 2008 R2 en Windows Server 2008 is het echter een optionele functie.

Gebruik de volgende procedure om Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server 2008 R2 of Windows Server 2008.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Integrated Scripting Environment (ISE) inschakelen

1. Start Serverbeheer.
2. Klik op **functies** en klik vervolgens op **onderdelen toevoegen**.
3. Klik in de onderdelen selecteren op Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>De 32-bits versie van Windows PowerShell starten

Wanneer u Windows PowerShell op een 64-bits computer installeert **Windows PowerShell (x86)**, een 32-bits versie van Windows PowerShell naast de 64-bits versie is geïnstalleerd. Wanneer u Windows PowerShell uitvoert, wordt standaard de 64-bits versie uitgevoerd.

Hoeft u wellicht van tijd tot tijd worden uitgevoerd **Windows PowerShell (x86)**, zoals wanneer u een module die vereist dat de 32-bits-versie of wanneer u extern verbinding met een 32-bits computer maakt.

Gebruik een van de volgende procedures voor het starten van een 32-bits versie van Windows PowerShell.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- Op de **Start** Typ **Windows PowerShell (x86)**. Klik op de **Windows PowerShell x86** tegel.
- In **Serverbeheer**, uit de **extra** selecteert u **Windows PowerShell (x86)**.
- Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.
- Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- Op de **Start** Typ **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.
- In **Serverbeheer**, uit de **extra** selecteert u **Windows PowerShell (x86)**.
- Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.
- Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>In Windows® 8.1

- Op de **Start** Typ **Windows PowerShell (x86)**. Klik op de **Windows PowerShell x86** tegel.
- Als u werkt met [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) voor Windows 8.1, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu.
  Selecteer **Windows PowerShell (x86)**.
- Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.
- Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- Op de **Start** scherm, verplaatst de cursor naar de rechterbovenhoek en klik op **instellingen**, klikt u op **tegels**, en verplaats de **weergeven Systeembeheer** schuifregelaar op Ja. Typ vervolgens **PowerShell** en klik op **Windows PowerShell (x86)**.
- Als u werkt met [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) voor Windows 8, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu. Selecteer **Windows PowerShell (x86)**.
- Op de **Start** scherm of het bureaublad, typt u **PowerShell (x86)** en klik vervolgens op **Windows PowerShell (x86)**.
- Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
