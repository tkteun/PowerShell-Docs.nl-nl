---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een PowerShell-tabblad maken in Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 080fe89bf1443f51460589b445431913fa20b4b8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688131"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Een PowerShell-tabblad maken in Windows PowerShell ISE

Tabbladen in de Windows PowerShell Integrated Scripting Environment (ISE) kunnen u tegelijkertijd maken en gebruiken van verschillende omgevingen binnen dezelfde toepassing.
Elk tabblad PowerShell overeenkomt met een afzonderlijke uitvoeringsomgeving of -sessie.

> [!NOTE]
> Variabelen, functies en -aliassen die u op een tabblad maakt doen niet meegenomen naar een andere. Ze zijn andere Windows PowerShell-sessies.

Gebruik de volgende stappen uit om te openen of sluiten van een tabblad in Windows PowerShell.
Wijzig de naam van een tabblad, stel de [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) eigenschap op het Windows PowerShell-tabblad scripting-object.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Het maken en gebruiken van een nieuwe PowerShell-tabblad

Op de **bestand** menu, klikt u op **nieuwe PowerShell-tabblad**. De nieuwe PowerShell-tabblad is altijd wordt geopend als het actieve venster.
PowerShell-tabbladen zijn incrementeel genummerd in de volgorde waarin ze worden geopend.
Elk tabblad is gekoppeld aan een eigen Windows PowerShell-consolevenster.
Er kunnen maximaal 32 PowerShell tabbladen met hun eigen sessie openen op een tijdstip (dit is beperkt tot 8 in Windows PowerShell ISE 2.0).

Houd er rekening mee dat te klikken op de **nieuw** of **Open** pictogrammen op de werkbalk maakt geen een nieuw tabblad met een aparte-sessie.
Deze knoppen openen in plaats daarvan een nieuw of bestaand scriptbestand op het actieve tabblad met een sessie.
U kunt meerdere bestanden worden geopend met elk tabblad en sessie-script hebben.
De tabbladen van het script voor een sessie wordt alleen weergegeven onder de tabbladen sessie wanneer de bijbehorende sessie actief is.

Als u wilt een PowerShell-tabblad activeren, klikt u op het tabblad. Selecteren uit alle PowerShell-tabbladen die zijn geopend op de **weergave** menu, klikt u op de PowerShell-tabblad dat u wilt gebruiken.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Het maken en gebruiken van een nieuwe externe PowerShell-tabblad

Op de **bestand** menu, klikt u op **nieuwe externe PowerShell-tabblad** tot stand brengen van een sessie op een externe computer.
Een dialoogvenster wordt weergegeven en vraagt u om in te voeren van gegevens die zijn vereist om de externe verbinding te maken.
De functies van het tabblad Extern net als bij een lokale PowerShell-tabblad, maar de opdrachten en scripts die worden uitgevoerd op de externe computer.

## <a name="to-close-a-powershell-tab"></a>Om een PowerShell-tabblad te sluiten

Als u wilt een tabblad sluit, kunt u een van de volgende technieken gebruiken:

- Klik op het tabblad dat u wilt sluiten.

- Op de **bestand** menu, klikt u op **PowerShell-tabblad sluit**, of klik op de knop Sluiten (**X**) op een actieve tabblad om het tabblad te sluiten.

Als u hebt niet-opgeslagen bestanden worden geopend in de PowerShell-tabblad dat u wilt sluiten, wordt u gevraagd op te slaan of ze negeren.
Zie voor meer informatie over het opslaan van een script [hoe u een Script opslaan](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Zie ook

- [Maak kennis met de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Het consolevenster gebruiken in de Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)