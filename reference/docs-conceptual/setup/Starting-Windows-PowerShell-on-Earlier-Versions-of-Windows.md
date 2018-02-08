---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Windows PowerShell op oudere versies van Windows wordt gestart
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a>Windows PowerShell op oudere versies van Windows wordt gestart
Deze sectie wordt uitgelegd hoe u Windows PowerShell en Windows PowerShell Integrated Scripting Environment (ISE) starten op Windows® 7, Windows Server® 2008 R2 en Windows Server® 2008. Ook wordt uitgelegd hoe u de optionele functie inschakelt voor Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server® 2008 R2 en Windows Server® 2008.

Windows PowerShell 4.0 installeren op ondersteunde systemen, downloaden en installeren [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Zie voor meer informatie [Windows PowerShell installeren](Installing-Windows-PowerShell.md).

Windows PowerShell 3.0 installeren op ondersteunde systemen, downloaden en installeren [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Zie voor meer informatie [Windows PowerShell installeren](Installing-Windows-PowerShell.md).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Het starten van Windows PowerShell op oudere versies van Windows
Een van de volgende methoden gebruiken om te starten van de geïnstalleerde versie van Windows PowerShell 3.0 of 4.0 voor Windows PowerShell, indien van toepassing.

#### <a name="from-the-start-menu"></a>Vanuit het startmenu

- Klik op **Start**, type **PowerShell**, en klik vervolgens op **Windows PowerShell**.

- Van de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Bij de opdrachtprompt

- In Cmd.exe, Windows PowerShell of Windows PowerShell ISE voor het starten van Windows PowerShell typt u:

    ```
    PowerShell
    ```

    U kunt ook de parameters van het programma PowerShell.exe gebruiken voor het aanpassen van de sessie. Zie voor meer informatie [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Met Administrative bevoegdheden ('als administrator uitvoeren")

1. Klik op **Start**, type **PowerShell**, met de rechtermuisknop op **Windows PowerShell**, en klik vervolgens op **als administrator uitvoeren**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Het starten van Windows PowerShell ISE voor eerdere versies van Windows
Gebruik een van de volgende methoden om te starten van Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Vanuit het startmenu

- Klik op **Start**, type **ISE**, en klik vervolgens op **Windows PowerShell ISE**.

- Van de **Start** menu, klikt u op **Start**, klikt u op **alle programma's**, klikt u op **accessoires**, klikt u op de **Windows PowerShell**  map en klik vervolgens op **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>Bij de opdrachtprompt

- In Cmd.exe, Windows PowerShell of Windows PowerShell ISE voor het starten van Windows PowerShell typt u:

    ```
    PowerShell_ISE
    ```

    of

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Met Administrative bevoegdheden ('als administrator uitvoeren")

1. Klik op **Start**, type **ISE**, met de rechtermuisknop op **Windows PowerShell ISE**, en klik vervolgens op **als administrator uitvoeren**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Het inschakelen van Windows PowerShell ISE voor eerdere versies van Windows
In Windows PowerShell 4.0 en Windows PowerShell 3.0, is Windows PowerShell ISE standaard ingeschakeld op alle versies van Windows. Als deze nog niet is ingeschakeld, schakelt Windows Management Framework 4.0 of Windows Management Framework 3.0 deze.

In Windows PowerShell 2.0, is Windows PowerShell ISE standaard ingeschakeld op Windows 7. Op Windows Server 2008 R2 en Windows Server 2008 is het echter een optionele functie.

Gebruik de volgende procedure om Windows PowerShell ISE in Windows PowerShell 2.0 op Windows Server 2008 R2 of Windows Server 2008.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Integrated Scripting Environment (ISE) inschakelen

1. Start Serverbeheer.

2. Klik op **functies** en klik vervolgens op **onderdelen toevoegen**.

3. Klik in de onderdelen selecteren op Windows PowerShell Integrated Scripting Environment (ISE).

