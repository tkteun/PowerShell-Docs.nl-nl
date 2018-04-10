---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De Windows PowerShell 2.0-engine installeren
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: 0b3282a1a67886509e749af0f499c47fe7a99411
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="installing-the-windows-powershell-20-engine"></a>De Windows PowerShell 2.0-engine installeren
In dit onderwerp wordt uitgelegd hoe de Engine voor Windows PowerShell 2.0 installeren.

Windows PowerShell 3.0 is ontworpen voor achterwaartse compatibiliteit met Windows PowerShell 2.0. Cmdlets, providers-modules, modules en scripts die zijn geschreven voor Windows PowerShell 2.0 worden uitgevoerd in Windows PowerShell 3.0 en Windows PowerShell 4.0 ongewijzigd. Echter, vanwege een wijziging in de runtime activering-beleid in Microsoft .NET Framework 4, Windows PowerShell host programma's die zijn geschreven voor Windows PowerShell 2.0 en gecompileerd met Common Language Runtime (CLR) 2.0 kunnen niet worden uitgevoerd zonder aanpassingen in later versies van Windows PowerShell, die is gecompileerd met CLR-4.0.

Achterwaartse compatibiliteit met opdrachten en host-programma's die worden beïnvloed door deze wijzigingen, worden de Windows PowerShell 2.0, Windows PowerShell 3.0 en Windows PowerShell 4.0-engines ontworpen om te naast elkaar. De Engine voor Windows PowerShell 2.0 is ook opgenomen in Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 en Windows Management Framework 3.0. De Engine voor Windows PowerShell 2.0 is bedoeld om te worden alleen gebruikt als een bestaand script of hostprogramma kan niet worden uitgevoerd omdat deze niet compatibel met Windows PowerShell 3.0, Windows PowerShell 4.0 of Microsoft .NET Framework 4 is. Dergelijke gevallen worden zelden verwacht.

De Engine voor Windows PowerShell 2.0 is een optionele functie van Windows Server 2012 R2, Windows 8.1, Windows® 8 en Windows Server® 2012. In eerdere versies van Windows tijdens de installatie van Windows Management Framework 3.0, vervangt de installatie van Windows PowerShell 3.0 volledig de Windows PowerShell 2.0-installatie in de installatiemap van Windows PowerShell. De Engine voor Windows PowerShell 2.0 is blijft echter behouden.

Zie voor meer informatie over het starten van de Windows PowerShell 2.0-Engine [starten van de Windows PowerShell 2.0 motor](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>Op Windows 8.1 en Windows 8
Voor Windows 8.1 en Windows 8, is de Windows PowerShell 2.0-Engine-functie standaard ingeschakeld. Als u wilt gebruiken, moet u echter inschakelen met de optie voor Microsoft .NET Framework 3.5, die is vereist. Deze sectie wordt ook uitgelegd hoe schakel de functie in Windows PowerShell 2.0-Engine in- of uitschakelen.

#### <a name="to-turn-on-net-framework-35"></a>.NET Framework 3.5 inschakelen

1. Op de **Start** Typ **Windows-onderdelen**.

2. Op de **Apps** balk op **instellingen**, en klik vervolgens op **Windows-onderdelen in- of uitschakelen**.

3. In de **Windows-onderdelen** Klik **.NET Framework 3.5 (inclusief .NET 2.0 en 3.0** om deze te selecteren.

    Wanneer u selecteert **.NET Framework 3.5 (inclusief .NET 2.0 en 3.0**, het selectievakje vult om aan te geven dat slechts een deel van de functie is ingeschakeld. Dit is echter voldoende voor de Windows PowerShell 2.0-Engine.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>De Engine voor Windows PowerShell 2.0 inschakelen en uitschakelen

1. Op de **Start** Typ **Windows-onderdelen**.

2. Op de **Apps** balk op **instellingen**, en klik vervolgens op **Windows-onderdelen in- of uitschakelen**.

3. In de **Windows-onderdelen** Vouw de **Windows PowerShell 2.0** knooppunt en klik op de **Windows PowerShell 2.0-Engine** in om te selecteren of wissen.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>Op Windows Server 2012 R2 en WindowsServer 2012
Gebruik de volgende procedures om toe te voegen van de Windows PowerShell 2.0-Engine en Microsoft .NET Framework 3.5-onderdelen. De Engine voor Windows PowerShell 2.0 vereist Microsoft .NET Framework 2.0.50727 minimaal. Deze vereiste wordt voldaan door Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>De functie .NET Framework 3.5 toe te voegen

1. In **Serverbeheer**, uit de **beheren** selecteert u **functies en onderdelen toevoegen**.

    Of in **Serverbeheer**, klikt u op **alle Servers**, met de rechtermuisknop op de naam van een server en selecteer vervolgens **functies en onderdelen toevoegen**.

2. Op de **installatietype** pagina **op basis van functie of onderdeel gebaseerde installatie**.

3. Op de **functies** pagina uit, vouw de **.NET Framework 3.5-onderdelen** uit en selecteer **.NET Framework 3.5 (inclusief .NET 2.0 en 3.0)**.

    De overige opties onder dat knooppunt zijn niet vereist voor de Windows PowerShell 2.0-Engine.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>De Windows PowerShell 2.0-Engine-functie toe te voegen

- In **Serverbeheer**, uit de **beheren** selecteert u **functies en onderdelen toevoegen**.

    Of **Serverbeheer**, klikt u op **alle Servers**, met de rechtermuisknop op de naam van een server en selecteer vervolgens **functies en onderdelen toevoegen**.

- Op de **installatietype** pagina **op basis van functie of onderdeel gebaseerde installatie**.

- Op de **functies** pagina uit, vouw de **Windows PowerShell (geïnstalleerd)** uit en selecteer **Windows PowerShell 2.0-Engine**.

Zie voor meer informatie over het starten van de Windows PowerShell 2.0-Engine [starten van de Windows PowerShell 2.0 motor](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>Op oudere systemen
De [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) -pakket voor Windows PowerShell 4.0 is geïnstalleerd op Windows 7, Windows Server 2008 R2 en Windows Server 2012 bevat de Engine voor Windows PowerShell 2.0. De Engine voor Windows PowerShell 2.0 is ingeschakeld en gereed voor gebruik, indien nodig, zonder aanvullende installatie, installatie of configuratie.

Het Windows PowerShell 3.0 is geïnstalleerd op Windows 7, Windows Server 2008 R2 en Windows Server 2008, Windows Management Framework 3.0-pakket bevat de Engine voor Windows PowerShell 2.0. De Engine voor Windows PowerShell 2.0 is ingeschakeld en gereed voor gebruik, indien nodig, zonder aanvullende installatie, installatie of configuratie.

## <a name="see-also"></a>Zie ook
- [Systeemvereisten voor Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Windows PowerShell installeren](Installing-Windows-PowerShell.md)
- [Windows PowerShell starten](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [De Windows PowerShell 2.0-engine starten](Starting-the-Windows-PowerShell-2.0-Engine.md)