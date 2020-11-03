---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: 5adba912d91369250ee9891ee2bb2ca0f8cba796
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249982"
---
# Add-PSSnapin

## SAMENVATTING
Hiermee voegt u een of meer Windows Power shell-modules toe aan de huidige sessie.

## SYNTAXIS

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## BESCHRIJVING

De `Add-PSSnapin` cmdlet voegt geregistreerde Windows Power shell-modules toe aan de huidige sessie. Nadat de modules zijn toegevoegd, kunt u de cmdlets en providers gebruiken die door de modules worden ondersteund in de huidige sessie.

Als u de module wilt toevoegen aan alle toekomstige Windows Power shell-sessies, voegt u een `Add-PSSnapin` opdracht toe aan uw Windows Power shell-profiel. Zie [about_Profiles](about/about_Profiles.md)voor meer informatie.

Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn opgenomen in Windows Power shell, verpakt in modules. De uitzonde ring is **micro soft. Power shell. core** , een module (PSSnapin).
Standaard wordt alleen de module **micro soft. Power shell. core** toegevoegd aan de sessie. Modules worden automatisch geïmporteerd bij het eerste gebruik en u kunt de cmdlet Import-Module gebruiken om ze te importeren.

## VOORBEELDEN

### Voor beeld 1: modules toevoegen

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

Met deze opdracht worden de modules micro soft Exchange en Active Directory toegevoegd aan de huidige sessie.

### Voor beeld 2: alle geregistreerde modules toevoegen

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

Met deze opdracht worden alle geregistreerde Windows Power shell-modules toegevoegd aan de sessie. Er wordt gebruikgemaakt van de cmdlet Get-PSSnapin met de para meter **geregistreerd** om objecten op te halen die elk van de geregistreerde modules vertegenwoordigen. Met de pijplijn operator (|) wordt het resultaat door gegeven aan `Add-PSSnapin` , waardoor ze aan de sessie worden toegevoegd. De para meter **PassThru** retourneert objecten die elk van de toegevoegde modules vertegenwoordigen.

### Voor beeld 3: een module registreren en toevoegen

Met de eerste opdracht worden modules opgehaald die zijn toegevoegd aan de huidige sessie, waaronder de modules die worden geïnstalleerd met Windows Power shell. In dit voor beeld wordt ManagementFeatures niet geretourneerd. Dit geeft aan dat deze niet is toegevoegd aan de sessie.

Met de tweede opdracht worden modules opgehaald die op uw systeem zijn geregistreerd, inclusief de modules die al zijn toegevoegd aan de sessie. De module bevat geen invoeg toepassingen die worden geïnstalleerd met Windows Power shell. In dit geval retourneert de opdracht geen modules. Dit geeft aan dat de ManagementFeatures-module niet is geregistreerd op het systeem.

Met de derde opdracht maakt u een alias, InstallUtil, voor het pad van het InstallUtil-hulp programma in .NET Framework.

De vierde opdracht maakt gebruik van het InstallUtil-hulp programma om de module te registreren. Met de opdracht geeft u het pad op van ManagementCmdlets.dll, de bestands naam of module van de module.

De vijfde opdracht is hetzelfde als de tweede opdracht. Deze keer gebruikt u deze om te controleren of de module ManagementCmdlets is geregistreerd.

De zesde opdracht gebruikt de `Add-PSSnapin` cmdlet om de module ManagementFeatures toe te voegen aan de sessie. Hiermee geeft u de naam van de module, ManagementFeatures, niet de bestands naam.

Om te controleren of de module aan de sessie is toegevoegd, gebruikt de zevende opdracht de **module** parameter van de cmdlet Get-Command. Hiermee worden de items weer gegeven die zijn toegevoegd aan de sessie door een module of module.

U kunt ook de eigenschap **PSSnapin** van het object gebruiken dat door de `Get-Command` cmdlet wordt geretourneerd om de module of module te vinden waarin een cmdlet afkomstig is. De achtste opdracht maakt gebruik van de punt notatie om de waarde van de eigenschap PSSnapin van de cmdlet Set-Alias te vinden.

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

In dit voor beeld wordt het proces van het registreren van een module op uw systeem gedemonstreerd en vervolgens toegevoegd aan uw sessie. Er wordt gebruikgemaakt van ManagementFeatures, een fictieve module die is geïmplementeerd in een bestand met de naam ManagementCmdlets.dll.

## PARAMETERS

### -Name

Hiermee geeft u de naam van de module. Dit is de naam, niet de Assemblyname of de module. Joker tekens zijn toegestaan.

Als u de namen van de geregistreerde modules op uw systeem wilt zoeken, typt u `Get-PSSnapin -Registered` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

Geeft aan dat deze cmdlet een object retourneert dat elke toegevoegde module vertegenwoordigt. Deze cmdlet genereert standaard geen uitvoer.

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
U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Geen of System. Management. Automation. PSSnapInInfo

Met deze cmdlet wordt een PSSnapInInfo-object geretourneerd dat de module vertegenwoordigt als u de para meter **PassThru** opgeeft. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* Vanaf Windows Power Shell 3,0 worden de kern opdrachten die met Windows Power shell zijn geïnstalleerd, verpakt in modules. In Windows Power Shell 2,0, en in host-Program ma's die oudere sessies maken in latere versies van Windows Power shell, worden de kern opdrachten verpakt in modules (PSSnapins). De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module. Externe sessies, zoals computers die zijn gestart door de New-PSSession cmdlet, zijn ook oudere sessies met kern modules.

  Zie de [methode CreateDefault2](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) in de MSDN-bibliotheek voor meer informatie over de **CreateDefault2** -methode voor het maken van nieuwere sessies met kern modules.

* Zie [about_PSSnapins](About/about_PSSnapins.md) en [een Windows Power shell-module maken](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in)voor meer informatie over modules.
* `Add-PSSnapin` Hiermee wordt de module alleen toegevoegd aan de huidige sessie. Als u de module wilt toevoegen aan alle Windows Power shell-sessies, voegt u deze toe aan uw Windows Power shell-profiel. Zie about_Profiles voor meer informatie.
* U kunt elke module die is geregistreerd met behulp van het hulp programma voor installatie van Microsoft .NET Framework toevoegen. Zie voor meer informatie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85)).
* Als u een lijst wilt weer geven met modules die zijn geregistreerd op uw computer, typt u `Get-PSSnapin -Registered` .
* Voordat u een module toevoegt, `Add-PSSnapin` controleert u de versie van de module om te controleren of deze compatibel is met de huidige versie van Windows Power shell. Als de invoeg toepassing de versie controle mislukt, wordt een fout gerapporteerd in Windows Power shell.

## GERELATEERDE KOPPELINGEN

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
