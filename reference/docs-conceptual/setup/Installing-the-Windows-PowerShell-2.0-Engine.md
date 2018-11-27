---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De Windows PowerShell 2.0-engine installeren
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: fb5ed1a5508ddca6925e9281a53caf5e6701870f
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320496"
---
# <a name="installing-the-windows-powershell-20-engine"></a>De Windows PowerShell 2.0-engine installeren
In dit onderwerp wordt uitgelegd hoe u de Windows PowerShell 2.0-Engine installeren.

Windows PowerShell 3.0 is ontworpen om te worden ook compatibel met Windows PowerShell 2.0. -Cmdlets, providers, -modules, modules en scripts die zijn geschreven voor Windows PowerShell 2.0 uitvoeren in Windows PowerShell 3.0 en Windows PowerShell 4.0 ongewijzigd. Echter, vanwege een wijziging in het beleid van de runtime-activering in Microsoft .NET Framework 4, Windows PowerShell-host-programma's die zijn geschreven voor Windows PowerShell 2.0 en gecompileerd met Common Language Runtime (CLR) 2.0 kunnen niet worden uitgevoerd zonder aanpassingen in later versies van Windows PowerShell, die is gecompileerd met CLR-4.0.

Als u wilt behouden voor achterwaartse compatibiliteit met opdrachten en host-programma's die worden beïnvloed door deze wijzigingen, worden de engines voor Windows PowerShell 2.0, Windows PowerShell 3.0 en Windows PowerShell 4.0 ontworpen om uit te voeren side-by-side. De Windows PowerShell 2.0-Engine is ook opgenomen in Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 en Windows Management Framework 3.0. De Windows PowerShell 2.0-Engine moet worden gebruikt alleen wanneer een bestaand script is bedoeld of hostprogramma kan niet worden uitgevoerd omdat deze niet compatibel met Windows PowerShell 3.0, Windows PowerShell 4.0 of Microsoft .NET Framework 4 is. Dergelijke gevallen wordt wordt een zeldzaam verwacht.

De Windows PowerShell 2.0-Engine is een optionele functie van Windows Server 2012 R2, Windows 8.1, Windows® 8 en Windows Server® 2012. In eerdere versies van Windows tijdens de installatie van Windows Management Framework 3.0, vervangt de installatie van Windows PowerShell 3.0 volledig de Windows PowerShell 2.0-installatie in de installatiemap van Windows PowerShell. De Windows PowerShell 2.0-Engine wordt echter bewaard.

Zie voor meer informatie over het starten van de Windows PowerShell 2.0-Engine [vanaf de Windows PowerShell 2.0-Engine](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>Op Windows 8.1 en Windows 8
Op Windows 8.1 en Windows 8, is de Windows PowerShell 2.0-Engine-functie standaard ingeschakeld. Als u wilt gebruiken, moet u echter de optie inschakelen voor Microsoft .NET Framework 3.5, die vereist is. In deze sectie wordt ook uitgelegd hoe u de Windows PowerShell 2.0-Engine-functie inschakelen in of uit.

#### <a name="to-turn-on-net-framework-35"></a>.NET Framework 3.5 inschakelen

1. Op de **Start** scherm, typt u **Windows functies**.

2. Op de **Apps** klikt u op **instellingen**, en klik vervolgens op **schakelt u Windows-onderdelen in- of uitschakelen**.

3. In de **Windows functies** Klik **.NET Framework 3.5 (inclusief .NET 2.0 en 3.0** om deze te selecteren.

    Wanneer u selecteert **.NET Framework 3.5 (inclusief .NET 2.0 en 3.0**, het vak ingevuld om aan te geven dat slechts een deel van de functie is geselecteerd. Dit is echter voldoende voor de Windows PowerShell 2.0-Engine.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Om in te schakelen van de Windows PowerShell 2.0-Engine in- en uitschakelen

1. Op de **Start** scherm, typt u **Windows functies**.

2. Op de **Apps** klikt u op **instellingen**, en klik vervolgens op **schakelt u Windows-onderdelen in- of uitschakelen**.

3. In de **Windows functies** Vouw de **Windows PowerShell 2.0** knooppunt en klik op de **Windows PowerShell 2.0-Engine** in om te selecteren in- of uitschakelen.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>Op Windows Server 2012 R2 en WindowsServer 2012
Gebruik de volgende procedures voor de Windows PowerShell 2.0-Engine en Microsoft .NET Framework 3.5-onderdelen toevoegen. De Windows PowerShell 2.0-Engine is Microsoft .NET Framework, 2.0.50727 ten minste vereist. Deze vereiste wordt voldaan door Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>De functie .NET Framework 3.5 toe te voegen

1. In **Serverbeheer**, uit de **beheren** in het menu **functies en onderdelen toevoegen**.

    Of in **Serverbeheer**, klikt u op **alle Servers**, met de rechtermuisknop op de naam van een server en selecteer vervolgens **functies en onderdelen toevoegen**.

2. Op de **installatietype** weergeeft, schakelt **op basis van functie of onderdeel gebaseerde installatie**.

3. Op de **functies** pagina uit, vouw de **.NET Framework 3.5-onderdelen** knooppunt en selecteert u **.NET Framework 3.5 (inclusief .NET 2.0 en 3.0)**.

    De andere opties onder dat knooppunt zijn niet vereist voor de Windows PowerShell 2.0-Engine.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>De Windows PowerShell 2.0-Engine-functie toe te voegen

- In **Serverbeheer**, uit de **beheren** in het menu **functies en onderdelen toevoegen**.

    Of **Serverbeheer**, klikt u op **alle Servers**, met de rechtermuisknop op de naam van een server en selecteer vervolgens **functies en onderdelen toevoegen**.

- Op de **installatietype** weergeeft, schakelt **op basis van functie of onderdeel gebaseerde installatie**.

- Op de **functies** pagina uit, vouw de **Windows PowerShell (geïnstalleerd)** knooppunt en selecteert u **Windows PowerShell 2.0-Engine**.

Zie voor meer informatie over het starten van de Windows PowerShell 2.0-Engine [vanaf de Windows PowerShell 2.0-Engine](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>Op oudere systemen
De [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) -pakket voor Windows PowerShell 4.0 op Windows 7, Windows Server 2008 R2 en Windows Server 2012 installeren bevat de Windows PowerShell 2.0-Engine. De Windows PowerShell 2.0-Engine is ingeschakeld en gereed voor gebruik, indien nodig, zonder aanvullende installatie, installatie of configuratie.

Het pakket Windows Management Framework 3.0 voor Windows PowerShell 3.0 op Windows 7, Windows Server 2008 R2 en Windows Server 2008 installeert, bevat de Windows PowerShell 2.0-Engine. De Windows PowerShell 2.0-Engine is ingeschakeld en gereed voor gebruik, indien nodig, zonder aanvullende installatie, installatie of configuratie.

## <a name="see-also"></a>Zie ook
- [Windows PowerShell-systeemvereisten](Windows-PowerShell-System-Requirements.md)
- [Windows PowerShell installeren](Installing-Windows-PowerShell.md)
- [Windows PowerShell starten](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [De Windows PowerShell 2.0-engine starten](Starting-the-Windows-PowerShell-2.0-Engine.md)