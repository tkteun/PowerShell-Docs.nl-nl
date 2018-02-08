---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: De 32-bits versie van Windows PowerShell starten
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>De 32-bits versie van Windows PowerShell starten
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

- Als u werkt met [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) voor Windows 8.1, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu. Selecteer **Windows PowerShell (x86)**.

- Klik op het bureaublad verplaatst de cursor naar de rechterbovenhoek op **Search**, type **PowerShell x86** en klik vervolgens op **Windows PowerShell (x86)**.
   
- Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- Op de **Start** scherm, verplaatst de cursor naar de rechterbovenhoek en klik op **instellingen**, klikt u op **tegels**, en verplaats de **weergeven Systeembeheer** schuifregelaar op Ja. Typ vervolgens **PowerShell** en klik op **Windows PowerShell (x86)**.

- Als u werkt met [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) voor Windows 8, kunt u ook Windows PowerShell x86 van openen de **Server ManagerTools** menu. Selecteer **Windows PowerShell (x86)**.

- Op de **Start** scherm of het bureaublad, typt u **PowerShell (x86)** en klik vervolgens op **Windows PowerShell (x86)**.

- Geef op via de opdrachtregel:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

