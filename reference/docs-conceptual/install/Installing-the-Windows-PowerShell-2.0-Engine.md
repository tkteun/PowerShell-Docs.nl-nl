---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: De Windows PowerShell 2.0-engine installeren
ms.openlocfilehash: 24bca7bd18fd33392f4f79b958189d3251ec35c1
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870537"
---
# <a name="installing-the-windows-powershell-20-engine"></a>De Windows PowerShell 2.0-engine installeren

In dit onderwerp wordt uitgelegd hoe u de Windows Power Shell 2,0-engine installeert.

Windows Power Shell 3,0 is ontworpen om achterwaarts compatibel te zijn met Windows Power Shell 2,0. Cmdlets, providers, modules, modules en scripts die zijn geschreven voor Windows Power Shell 2,0, worden ongewijzigd uitgevoerd in Windows Power Shell 3,0 en Windows Power Shell 4,0. Als gevolg van een wijziging in het runtime-activerings beleid in Microsoft .NET Framework 4, Windows Power shell-host-Program ma's die zijn geschreven voor Windows Power Shell 2,0 en gecompileerd met common language runtime (CLR) 2,0 kunnen niet zonder aanpassing in latere versies worden uitgevoerd releases van Windows Power shell, die zijn gecompileerd met CLR 4,0.

Om achterwaartse compatibiliteit te behouden met opdrachten en host-Program ma's die worden beïnvloed door deze wijzigingen, zijn de Windows Power Shell 2,0-, Windows Power Shell 3,0-en Windows Power Shell 4,0-engines ontworpen om naast elkaar te worden uitgevoerd. Daarnaast is de Windows Power Shell 2,0-engine opgenomen in Windows Server 2012 R2, Windows 8,1, Windows 8, Windows Server 2012 en Windows Management Framework 3,0. De Windows Power Shell 2,0-engine is alleen bedoeld voor gebruik wanneer een bestaand script of hostprogramma niet kan worden uitgevoerd omdat het niet compatibel is met Windows Power Shell 3,0, Windows Power Shell 4,0 of Microsoft .NET Framework 4. Dergelijke gevallen worden naar verwachting zeldzaam.

De Windows Power Shell 2,0-engine is een optionele functie van Windows Server 2012 R2, Windows 8,1, Windows® 8 en Windows Server® 2012. Bij eerdere versies van Windows wordt bij het installeren van Windows Management Framework 3,0 de Windows Power Shell 3,0-installatie volledig vervangen door de installatie van Windows Power Shell 2,0 in de installatiemap van Windows Power shell. De Windows Power Shell 2,0-engine blijft echter behouden.

Zie [Start the Windows Power shell 2,0 engine](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)(Engelstalig) voor meer informatie over het starten van de Windows power Shell 2,0-engine.

## <a name="on-windows-81-and-windows-8"></a>In Windows 8,1 en Windows 8

In Windows 8,1 en Windows 8 is de functie Windows Power Shell 2,0 engine standaard ingeschakeld.
Om het te gebruiken, moet u echter de optie inschakelen voor Microsoft .NET Framework 3,5, dat nodig is. In deze sectie wordt ook uitgelegd hoe u de Windows Power Shell 2,0 engine-functie in-of uitschakelen.

#### <a name="to-turn-on-net-framework-35"></a>Om .NET Framework 3,5 in te scha kelen

1. Op de **Start** scherm, typt u **Windows-onderdelen**.
2. Klik op de balk **apps** op **instellingen**en klik vervolgens op **Windows-onderdelen in-of uitschakelen**.
3. Klik in het vak **Windows-functies** op **.NET Framework 3,5 (inclusief .net 2,0 en 3,0** om het te selecteren.

   Wanneer u **.NET Framework 3,5 (inclusief .net 2,0 en 3,0**) selecteert, wordt in het vak gevuld om aan te geven dat slechts een deel van de functie is geselecteerd. Dit is echter wel voldoende voor de Windows Power Shell 2,0-engine.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>De Windows Power Shell 2,0-engine inschakelen en uitschakelen

1. Op de **Start** scherm, typt u **Windows-onderdelen**.

2. Klik op de balk **apps** op **instellingen**en klik vervolgens op **Windows-onderdelen in-of uitschakelen**.

3. Vouw in het dialoog venster **Windows-functies** het knoop punt **windows Power Shell 2,0** uit en klik op het vak **Windows Power Shell 2,0-engine** om het in of uit te scha kelen.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>In Windows Server 2012 R2 en Windows Server 2012

Gebruik de volgende procedures om de Windows Power Shell 2,0-engine en Microsoft .NET Framework 3,5-functies toe te voegen. De Windows Power Shell 2,0-engine vereist Microsoft .NET Framework 2.0.50727 mini maal. Aan deze eis wordt voldaan door Microsoft .NET Framework 3,5.

#### <a name="to-add-the-net-framework-35-feature"></a>De functie .NET Framework 3,5 toevoegen

1. In **Serverbeheer**klikt u in het menu **beheren** op **functies en onderdelen toevoegen**.

    Of in **Serverbeheer**op **alle servers**, klik met de rechter muisknop op een server naam en selecteer vervolgens **functies en onderdelen toevoegen**.

2. Selecteer op de pagina **installatie type** de optie installatie die op de **functie of het onderdeel is gebaseerd**.

3. Vouw op de pagina **functies** het knoop punt **.net 3,5 Framework-functies** uit en selecteer **.NET Framework 3,5 (inclusief .net 2,0 en 3,0)** .

   De andere opties onder dat knoop punt zijn niet vereist voor de Windows Power Shell 2,0-engine.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>De functie Windows Power Shell 2,0 engine toevoegen

- In **Serverbeheer**klikt u in het menu **beheren** op **functies en onderdelen toevoegen**.

  Of **Serverbeheer**op **alle servers**, klik met de rechter muisknop op een server naam en selecteer vervolgens **functies en onderdelen toevoegen**.

- Selecteer op de pagina **installatie type** de optie installatie die op de **functie of het onderdeel is gebaseerd**.

- Vouw op de pagina **functies** het knoop punt **Windows Power shell (geïnstalleerd)** uit en selecteer **Windows Power Shell 2,0 engine**.

Zie [Start the Windows Power shell 2,0 engine](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)(Engelstalig) voor meer informatie over het starten van de Windows power Shell 2,0-engine.

## <a name="on-earlier-systems"></a>Op eerdere systemen

Het [Windows Management Framework 4,0](https://go.microsoft.com/fwlink/?LinkID=293881) -pakket dat Windows power Shell 4,0 installeert op Windows 7, windows server 2008 R2 en windows server 2012, bevat de Windows power Shell 2,0-engine. De Windows Power Shell 2,0-engine is ingeschakeld en klaar voor gebruik, indien nodig, zonder aanvullende installatie, configuratie of configuratie.

Het Windows Management Framework 3,0-pakket dat Windows Power Shell 3,0 installeert op Windows 7, Windows Server 2008 R2 en Windows Server 2008, bevat de Windows Power Shell 2,0-engine. De Windows Power Shell 2,0-engine is ingeschakeld en klaar voor gebruik, indien nodig, zonder aanvullende installatie, configuratie of configuratie.

## <a name="see-also"></a>Zie ook

- [Systeem vereisten voor Windows Power shell](Windows-PowerShell-System-Requirements.md)
- [Windows Power Shell installeren](Installing-Windows-PowerShell.md)
- [Windows Power shell starten](/previous-versions/ms714415(v=vs.85))
- [De Windows PowerShell 2.0-engine starten](../getting-started/Starting-the-Windows-PowerShell-2.0-Engine.md)
