---
ms.date: 01/02/2020
keywords: Power shell, cmdlet
title: Een PowerShell-tabblad maken in Windows PowerShell ISE
ms.openlocfilehash: 39df0b76c337bb7c02d36d66b325c5396afbbe00
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736263"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a>Een PowerShell-tabblad maken in Windows PowerShell ISE

Met de tabbladen in Windows Power shell Integrated Scripting Environment (ISE) kunt u gelijktijdig verschillende uitvoerings omgevingen maken en gebruiken in dezelfde toepassing. Elk Power shell-tabblad komt overeen met een afzonderlijke uitvoerings omgeving of-sessie.

> [!NOTE]
> Variabelen, functies en aliassen die u op één tabblad maakt, worden niet overgedragen naar een andere. Dit zijn verschillende Windows Power shell-sessies.

Gebruik de volgende stappen om een tabblad in Windows Power shell te openen of sluiten. Als u de naam van een tabblad wilt wijzigen, stelt u de eigenschap [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) op het script object Windows Power shell-tabblad in.

## <a name="to-create-and-use-a-new-powershell-tab"></a>Een nieuw Power shell-tabblad maken en gebruiken

Klik in het menu **bestand** op **Nieuw Power shell-tabblad**. Het nieuwe Power shell-tabblad wordt altijd geopend als het actieve venster. Power shell-tabbladen worden stapsgewijs genummerd in de volg orde waarin ze zijn geopend. Elk tabblad is gekoppeld aan een eigen Windows Power shell-console venster. U kunt Maxi maal 32 Power shell-tabbladen met een eigen sessie tegelijk openen (dit is beperkt tot 8 op Windows PowerShell ISE 2,0.)

Houd er rekening mee dat door te klikken op de pictogrammen **Nieuw** of **openen** op de werk balk geen nieuw tabblad met een afzonderlijke sessie wordt gemaakt. In plaats daarvan openen deze knoppen een nieuw of bestaand script bestand op het huidige actieve tabblad met een sessie. U kunt meerdere script bestanden openen met elk tabblad en elke sessie. De script tabbladen voor een sessie worden alleen onder de sessie tabbladen weer gegeven wanneer de bijbehorende sessie actief is.

Als u een Power shell-tabblad actief wilt maken, klikt u op het tabblad. Als u wilt selecteren uit alle Power shell-tabbladen die zijn geopend, klikt u in het menu **weer gave** op het Power shell-tabblad dat u wilt gebruiken.

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a>Een nieuw externe Power shell-tabblad maken en gebruiken

Klik in het menu **bestand** op **Nieuw externe Power shell-tabblad** om een sessie op een externe computer tot stand te brengen. Er wordt een dialoog venster weer gegeven waarin wordt gevraagd om de gegevens op te geven die nodig zijn om de externe verbinding tot stand te brengen. Het tabblad Extern werkt net als een lokale Power shell-tabblad, maar de opdrachten en scripts worden uitgevoerd op de externe computer.

## <a name="to-close-a-powershell-tab"></a>Een Power shell-tabblad sluiten

Als u een tabblad wilt sluiten, kunt u een van de volgende technieken gebruiken:

- Klik op het tabblad dat u wilt sluiten.

- Klik in het menu **bestand** op **Power shell-tabblad sluiten**of klik op de knop Sluiten (**X**) op een actief tabblad om het tabblad te sluiten.

Als u niet-opgeslagen bestanden hebt geopend op het Power shell-tabblad dat u wilt sluiten, wordt u gevraagd of u deze wilt opslaan of negeren. Zie [How to Save a script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script)(Engelstalig) voor meer informatie over het opslaan van een script.

## <a name="see-also"></a>Zie ook

- [Introductie van de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Het gebruik van het console venster in de Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
