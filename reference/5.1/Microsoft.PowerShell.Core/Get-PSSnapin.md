---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 472a4c8fbb9eb0d37827aff4fcfd6bb9a67f4743
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249951"
---
# Get-PSSnapin

## SAMENVATTING
Hiermee worden de Windows Power shell-modules op de computer opgehaald.

## SYNTAXIS

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Get-PSSnapin** haalt de Windows Power shell-modules op die zijn toegevoegd aan de huidige sessie of die zijn geregistreerd op het systeem.
Met deze cmdlet worden de modules weer gegeven in de volg orde waarin ze worden gedetecteerd.

**Get-PSSnapin** haalt alleen geregistreerde modules op. Als u een Windows Power shell-module wilt registreren, gebruikt u het InstallUtil-hulp programma dat is opgenomen in het Microsoft .NET Framework 2,0.
Zie [cmdlets, providers en hosttoepassingen registreren](https://go.microsoft.com/fwlink/?LinkID=143619) in de MSDN-bibliotheek voor meer informatie.

Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn opgenomen in Windows Power shell, verpakt in modules.
De uitzonde ring is **micro soft. Power shell. core** , een module (PSSnapin).
Standaard wordt alleen de module **micro soft. Power shell. core** toegevoegd aan de sessie.
Modules worden automatisch geïmporteerd bij het eerste gebruik en u kunt de cmdlet Import-Module gebruiken om ze te importeren.

## VOORBEELDEN

### Voor beeld 1: modules ophalen die momenteel zijn geladen

```
PS C:\> Get-PSSnapIn
```

Met deze opdracht worden de Windows Power shell-modules opgehaald die momenteel in de sessie zijn geladen.
Dit omvat de modules die worden geïnstalleerd met Windows Power shell en die zijn toegevoegd aan de sessie.

### Voor beeld 2: modules ophalen die zijn geregistreerd

```
PS C:\> get-PSSnapIn -Registered
```

Met deze opdracht worden de Windows Power shell-modules opgehaald die zijn geregistreerd op de computer, inclusief de invoeg toepassingen die al zijn toegevoegd aan de sessie.
De uitvoer bevat geen modules die zijn geïnstalleerd met Windows Power shell of Windows Power shell-module Dynamic-Link Libraries (Dll's) die nog niet zijn geregistreerd op het systeem.

### Voor beeld 3: huidige modules ophalen die overeenkomen met een teken reeks

```
PS C:\> Get-PSSnapIn -Name smp*
```

Met deze opdracht worden de Windows Power shell-modules in de huidige sessie opgehaald met namen die beginnen met smp.

## PARAMETERS

### -Name
Hiermee geeft u een matrix met module namen op.
Met deze cmdlet worden alleen de opgegeven Windows Power shell-modules opgehaald. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Geregistreerd
Hiermee wordt aangegeven dat met deze cmdlet de Windows Power shell-modules worden opgehaald die zijn geregistreerd op het systeem, zelfs als ze nog niet zijn toegevoegd aan de sessie.

De modules die met Windows Power shell zijn geïnstalleerd, worden niet in deze lijst weer gegeven.

Zonder deze para meter haalt **Get-PSSnapin** de Windows Power shell-modules die zijn toegevoegd aan de sessie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSSnapInInfo
Get-PSSnapin retourneert een object voor elke module die wordt opgehaald.

## OPMERKINGEN

* Vanaf Windows Power Shell 3,0 worden de kern opdrachten die met Windows Power shell zijn geïnstalleerd, verpakt in modules. In Windows Power Shell 2,0, en in host-Program ma's die oudere sessies maken in latere versies van Windows Power shell, worden de kern opdrachten verpakt in modules ( **PSSnapin** ). De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module. Externe sessies, zoals computers die zijn gestart door de New-PSSession cmdlet, zijn ook oudere sessies met kern modules.

  Zie de [methode CreateDefault2](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) in de MSDN-bibliotheek voor meer informatie over de **CreateDefault2** -methode voor het maken van nieuwere sessies met kern modules.

## GERELATEERDE KOPPELINGEN

[Add-PSSnapin](Add-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
