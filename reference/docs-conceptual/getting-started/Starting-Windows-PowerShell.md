---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Windows PowerShell starten
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404446"
---
# <a name="starting-windows-powershell"></a>Windows PowerShell starten
PowerShell is een scripting engine dll die is ingesloten in meerdere hosts.  De meest voorkomende host die u wilt beginnen zijn de interactieve opdrachtregel PowerShell.exe en de interactieve Scripting omgeving PowerShell_ISE.exe.

Zie voor informatie over het starten van Windows PowerShell® op Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 en Windows 8 [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Starten van Windows PowerShell op oudere versies van Windows

In deze sectie wordt uitgelegd hoe u start Windows PowerShell en Windows PowerShell Integrated Scripting Environment (ISE) op Windows® 7, Windows Server® 2008 R2 en Windows Server® 2008. Hierin wordt ook uitgelegd hoe u de optionele functie inschakelt voor Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server® 2008 R2 en Windows Server® 2008.

Een van de volgende methoden gebruiken om te beginnen de geïnstalleerde versie van Windows PowerShell 3.0 of 4.0 voor Windows PowerShell, indien van toepassing.

#### <a name="from-the-start-menu"></a>Vanuit het startmenu

- Klik op **Start**, type **PowerShell**, en klik vervolgens op **Windows PowerShell**.
- Uit de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Bij de opdrachtprompt

In Cmd.exe, de Windows PowerShell of Windows PowerShell ISE, voor het starten van Windows PowerShell, typt u:

```
PowerShell
```

U kunt de parameters van het programma PowerShell.exe ook gebruiken om aan te passen van de sessie. Zie voor meer informatie, [PowerShell.exe-opdrachtregel Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Met Administrative bevoegdheden ('als administrator uitvoeren")

Klik op **Start**, type **PowerShell**, met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als administrator uitvoeren**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Windows PowerShell ISE starten op eerdere versies van Windows

Gebruik een van de volgende methoden om te starten van Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Vanuit het startmenu

- Klik op **Start**, type **ISE**, en klik vervolgens op **Windows PowerShell ISE**.
- Uit de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>Bij de opdrachtprompt

In Cmd.exe, de Windows PowerShell of Windows PowerShell ISE, voor het starten van Windows PowerShell, typt u:

```
PowerShell_ISE
```

of

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Met Administrative bevoegdheden ('als administrator uitvoeren")

Klik op **Start**, type **ISE**, met de rechtermuisknop op **Windows PowerShell ISE**, en klik vervolgens op **als administrator uitvoeren**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Windows PowerShell ISE op eerdere versies van Windows inschakelen

In Windows PowerShell 4.0 en Windows PowerShell 3.0, is Windows PowerShell ISE standaard ingeschakeld op alle versies van Windows. Als deze nog niet is ingeschakeld, Windows Management Framework 4.0 of Windows Management Framework 3.0 ingeschakeld.

In Windows PowerShell 2.0, is Windows PowerShell ISE standaard ingeschakeld op Windows 7. Op Windows Server 2008 R2 en Windows Server 2008 is het echter een optionele functie.

Gebruik de volgende procedure om in te schakelen in Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server 2008 R2 of Windows Server 2008.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Om in te schakelen van Windows PowerShell Integrated Scripting Environment (ISE)

1. Start Serverbeheer.
2. Klik op **functies** en klik vervolgens op **onderdelen toevoegen**.
3. Klik in onderdelen selecteren op de Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>De 32-bits versie van Windows PowerShell starten

Wanneer u Windows PowerShell op een 64-bits computer installeert **Windows PowerShell (x86)**, een 32-bits versie van Windows PowerShell is geïnstalleerd naast de 64-bits versie. Wanneer u Windows PowerShell uitvoert, wordt standaard de 64-bits versie uitgevoerd.

Moet u mogelijk af en toe om uit te voeren **Windows PowerShell (x86)**, zoals wanneer u van een module gebruikmaakt die de 32-bits versie vereist of als u op afstand verbinding met een 32-bits computer.

Gebruik een van de volgende procedures voor het starten van een 32-bits versie van Windows PowerShell.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- Op de **Start** scherm, typt u **Windows PowerShell (x86)**. Klik op de **Windows PowerShell x86** tegel.
- In **Serverbeheer**, uit de **extra** in het menu **Windows PowerShell (x86)**.
- Op het bureaublad van de cursor verplaatsen naar de rechterbovenhoek, klikt u op **zoeken**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.
- Via de opdrachtregel, typ: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- Op de **Start** scherm, typt u **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.
- In **Serverbeheer**, uit de **extra** in het menu **Windows PowerShell (x86)**.
- Op het bureaublad van de cursor verplaatsen naar de rechterbovenhoek, klikt u op **zoeken**, type **PowerShell** en klik vervolgens op **Windows PowerShell (x86)**.
- Via de opdrachtregel, typ: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>In Windows® 8.1

- Op de **Start** scherm, typt u **Windows PowerShell (x86)**. Klik op de **Windows PowerShell x86** tegel.
- Als u werkt met [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) voor Windows 8.1, kunt u ook Windows PowerShell x86 vanuit openen de **Server ManagerTools** menu.
  Selecteer **Windows PowerShell (x86)**.
- Op het bureaublad van de cursor verplaatsen naar de rechterbovenhoek, klikt u op **zoeken**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.
- Via de opdrachtregel, typ: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- Op de **Start** scherm, plaatst u de cursor op de rechter bovenhoek, klikt u op **instellingen**, klikt u op **tegels**, sluiten en verplaatst u de **weergeven Systeembeheer** schuifregelaar op Ja. Typ vervolgens **PowerShell** en klikt u op **Windows PowerShell (x86)**.
- Als u werkt met [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) voor Windows 8, kunt u ook Windows PowerShell x86 vanuit openen de **Server ManagerTools** menu. Selecteer **Windows PowerShell (x86)**.
- Op de **Start** scherm of het bureaublad, typt u **PowerShell (x86)** en klik vervolgens op **Windows PowerShell (x86)**.
- Via de opdrachtregel, typ: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`