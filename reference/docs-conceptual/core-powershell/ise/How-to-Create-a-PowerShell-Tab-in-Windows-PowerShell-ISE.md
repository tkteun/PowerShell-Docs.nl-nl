---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een PowerShell-tabblad maken in Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 4d4388d889f2178b2cd24cb0f3350aee37327625
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Een PowerShell-tabblad maken in Windows PowerShell ISE

Tabbladen in de Windows PowerShell Integrated Scripting Environment (ISE) kunt u tegelijkertijd maken en gebruiken van verschillende uitvoeringsomgevingen binnen dezelfde toepassing.
Elk tabblad PowerShell overeenkomt met een afzonderlijke uitvoeringsomgeving of de sessie.

> **OPMERKING**:
>
> Variabelen, functies en aliassen die u op een tabblad maakt uitvoeren niet via naar een andere. Andere Windows PowerShell-sessies zijn.

Gebruik de volgende stappen uit om te openen of sluiten van een tabblad in Windows PowerShell.
Wijzig de naam van een tabblad, stel de [DisplayName](The-PowerShellTab-Object.md#displayname) -eigenschap op het tabblad voor Windows PowerShell-scripting-object.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Maken en gebruiken van een nieuw PowerShell-tabblad

Op de **bestand** menu, klikt u op **nieuw PowerShell-tabblad**. Het nieuwe PowerShell-tabblad is altijd wordt geopend als het actieve venster.
PowerShell tabbladen worden stapsgewijs genummerd in de volgorde waarin ze worden geopend.
Elk tabblad is gekoppeld aan een eigen Windows PowerShell-consolevenster.
Er kunnen maximaal 32 PowerShell tabbladen met hun eigen sessie niet openen op een tijdstip (dit is beperkt tot 8 op Windows PowerShell ISE 2.0).

Houd er rekening mee dat te klikken op de **nieuw** of **Open** pictogrammen op de werkbalk maakt een nieuw tabblad niet met een afzonderlijke sessie.
Deze knoppen openen in plaats daarvan een nieuw of bestaand scriptbestand op het momenteel geselecteerde tabblad met een sessie.
U kunt meerdere script bestanden met elk tabblad en sessie openen hebben.
Het script voor een sessie alleen tabbladen onder de tabbladen sessie wanneer de bijbehorende sessie actief is.

Klik op het tabblad om een PowerShell-tabblad te activeren. Om te selecteren uit alle PowerShell tabbladen die zijn geopend op de **weergave** menu, klikt u op het PowerShell-tabblad dat u wilt gebruiken.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Maken en gebruiken van een nieuw tabblad van de externe PowerShell

Op de **bestand** menu, klikt u op **nieuwe externe PowerShell-tabblad** een sessie op een externe computer tot stand brengen.
Een dialoogvenster wordt weergegeven en u wordt gevraagd om de gegevens die zijn vereist voor het maken van de externe verbinding invoeren.
Het tabblad Extern functies net als bij een lokale PowerShell-tabblad, maar de opdrachten en scripts worden uitgevoerd op de externe computer.

## <a name="to-close-a-powershell-tab"></a>Een PowerShell-tabblad sluiten

U kunt een van de volgende technieken gebruiken een tabblad om af te sluiten:

- Klik op het tabblad dat u wilt sluiten.

- Op de **bestand** menu, klikt u op **PowerShell tabblad sluiten**, of klik op de knop Sluiten (**X**) op een actieve tabblad te sluiten van het tabblad.

Als u hebt niet-opgeslagen openen bestanden op het tabblad PowerShell dat u wilt sluiten, wordt u gevraagd op te slaan of deze verwijderen.
Zie voor meer informatie over het opslaan van een script [hoe een Script opslaat](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).

## <a name="see-also"></a>Zie ook

- [Introducing the Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Het gebruik van het consolevenster in de Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)