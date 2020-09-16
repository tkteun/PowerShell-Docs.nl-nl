---
ms.date: 08/09/2017
keywords: Power shell, cmdlet, down load, install, Setup, Windows 10, Windows 8,1, Windows 8.0, Windows 7
title: Windows PowerShell installeren
ms.openlocfilehash: 26675eb0b213818eaa72e148f0814545ee9f960e
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236217"
---
# <a name="installing-windows-powershell"></a>Windows PowerShell installeren

Windows Power shell wordt standaard geïnstalleerd in elke Windows, te beginnen met Windows 7 SP1 en Windows Server 2008 R2 SP1.

Als u geïnteresseerd bent in Power shell 6 en hoger, moet u Power shell Core installeren in plaats van Windows Power shell. Zie [Power shell Core installeren in Windows](../../install/Installing-PowerShell-Core-on-Windows.md)voor meer informatie.

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Power shell in Windows 10, 8,1, 8,0 en 7 zoeken

Soms is het zoeken naar een Power shell-console of ISE (Integrated Scripting Environment) in Windows lastig, omdat de locatie van de ene versie van Windows naar de volgende wordt verplaatst.

De volgende tabellen helpen u bij het vinden van Power shell in uw Windows-versie. Alle versies die hier worden vermeld, zijn de oorspronkelijke versie, zoals vrijgegeven, zonder updates.

### <a name="for-console"></a>Voor console

|     Versie      |                                                            Locatie                                                            |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Windows 10       | Klik op onderste hoek van het Windows-pictogram, start Power shell                                                                  |
| Windows 8.1, 8.0 | Typ Power shell in het Start scherm.<br/>Als op bureau blad, klikt u op onderste hoek van Windows-pictogram, begint u Power shell te typen |
| Windows 7 SP1    | Klik op onderste hoek van het Windows-pictogram in het zoekvak om Power shell te typen.                                                |

### <a name="for-ise"></a>Voor ISE

|     Versie      |                                                            Locatie                                                            |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Windows 10       | Klik op onderste hoek van het Windows-pictogram, begin met het typen van ISE                                                                         |
| Windows 8.1, 8.0 | Typ **Power shell ISE**in het Start scherm.<br/>Als op bureau blad, klikt u op onderste hoek van Windows-pictogram, typt u **Power shell ISE** |
| Windows 7 SP1    | Klik op onderste hoek van het Windows-pictogram in het zoekvak om Power shell te typen.                                                |

## <a name="finding-powershell-in-windows-server-versions"></a>Power shell zoeken in Windows Server-versies

Vanaf Windows Server 2008 R2 kan Windows-besturings systeem worden geïnstalleerd zonder de Graphical User Interface (GUI). Edities van Windows Server zonder GUI hebben de naam **kern** edities en edities met de gebruikers interface heet **bureau blad**.

### <a name="windows-server-core-editions"></a>Windows Server Core-edities

Wanneer u zich aanmeldt bij de server, wordt er in alle kern edities een Windows-opdracht prompt venster weer gegeven.

Typ `powershell` en druk op **Enter** om Power shell in de opdracht prompt sessie te starten. Typ `exit` om de Power shell-sessie te beëindigen en terug te keren naar de opdracht prompt.

### <a name="windows-server-desktop-editions"></a>Windows Server Desktop-edities

In alle Bureau bladen klikt u op het pictogram van de onderste hoek van Windows, start Power shell. U krijgt de opties console en ISE.

De enige uitzonde ring op de bovenstaande regel is de ISE in Windows Server 2008 R2 SP1; in dit geval klikt u op het pictogram van de onderste hoek Windows, typt u Power shell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>De versie van Power shell controleren

Als u wilt weten welke versie van Power shell u hebt geïnstalleerd, start u een Power shell-console (of de ISE) en typt u `$PSVersionTable` en drukt u op **Enter**. Zoek naar de `PSVersion` waarde.

## <a name="upgrading-existing-windows-powershell"></a>Bestaande Windows Power shell bijwerken

Het installatie pakket voor Power Shell bevindt zich in een WMF-installatie programma. De versie van het WMF-installatie programma komt overeen met de versie van Power shell. Er is geen zelfstandig installatie programma voor Windows Power shell.

Als u uw bestaande versie van Power shell in Windows wilt bijwerken, gebruikt u de volgende tabel om het installatie programma te vinden voor de versie van Power shell die u wilt bijwerken.

|                    Windows                     |                                  PS 3.0                                   |                                  PS 4.0                                   |                                  PS 5,0                                   |                                  PS 5.1                                   |
| ---------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Windows 10 (Zie Note1)<br/>Windows Server 2016 | -                                                                         | -                                                                         | -                                                                         | nstalleerd                                                                 |
| Windows 8.1<br/>Windows Server 2012 R2         | -                                                                         | nstalleerd                                                                 | [WMF 5.0](https://www.microsoft.com/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616) |
| Windows 8<br/>Windows Server 2012              | nstalleerd                                                                 | [WMF 4.0](https://www.microsoft.com/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616) |
| Windows 7 SP1<br/>Windows Server 2008 R2 SP1   | [WMF 3.0](https://www.microsoft.com/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/download/details.aspx?id=54616) |

> [!NOTE]
> Bij de eerste release van Windows 10, waarbij automatische updates is ingeschakeld, wordt Power shell bijgewerkt van versie 5,0 naar 5,1. Als de oorspronkelijke versie van Windows 10 niet wordt bijgewerkt via Windows-updates, is de versie van Power shell 5,0.

## <a name="need-azure-powershell"></a>Azure PowerShell nodig

Als u op zoek bent naar **Azure PowerShell**, kunt u beginnen met [overzicht van Azure PowerShell](/powershell/azure/overview).

Als dat niet het geval is, moet u [Azure PowerShell installeren en configureren](/powershell/azure/install-az-ps)

## <a name="see-also"></a>Zie ook

[Windows PowerShell-systeemvereisten](Windows-PowerShell-System-Requirements.md)

[Windows PowerShell starten](../Starting-Windows-PowerShell.md)
