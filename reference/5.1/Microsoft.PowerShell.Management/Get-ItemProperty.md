---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250796"
---
# Get-ItemProperty

## SAMENVATTING
Hiermee worden de eigenschappen van een opgegeven item opgehaald.

## SYNTAXIS

### Pad (standaard)

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## BESCHRIJVING

`Get-ItemProperty`Met de cmdlet worden de eigenschappen van de opgegeven items opgehaald.
U kunt deze cmdlet bijvoorbeeld gebruiken om de waarde van de eigenschap LastAccessTime van een File-object op te halen.
U kunt deze cmdlet ook gebruiken om Register vermeldingen en hun waarden weer te geven.

## VOORBEELDEN

### Voor beeld 1: informatie over een specifieke directory ophalen

Met deze opdracht wordt informatie over de map C:\Windows opgehaald.

```powershell
Get-ItemProperty C:\Windows
```

### Voor beeld 2: de eigenschappen van een specifiek bestand ophalen

Met deze opdracht worden de eigenschappen van het bestand ' C:\Test\Weather.xls ' opgehaald.
Het resultaat wordt naar de cmdlet gepiped `Format-List` om de uitvoer als een lijst weer te geven.

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### Voor beeld 3: de waardenaam en gegevens van Register vermeldingen in een register sleutel weer geven

Met deze opdracht worden de naam en de gegevens van elk van de Register vermeldingen in de registersubsleutel ' CurrentVersion ' weer gegeven.
Houd er rekening mee dat de opdracht vereist dat er een Power Shell-station `HKLM:` met de naam wordt toegewezen aan de component HKEY_LOCAL_MACHINE van het REGI ster.
Een station met die naam en toewijzing is standaard beschikbaar in Power shell.
U kunt ook het pad naar deze registersubsleutel opgeven met behulp van het volgende alternatieve pad dat begint met de provider naam gevolgd door twee dubbele punten:

"REGI ster:: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion".

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### Voor beeld 4: de waardenaam en gegevens van een register vermelding in een registersubsleutel ophalen

Met deze opdracht worden de waardenaam en de gegevens van de register vermelding ' ProgramFilesDir ' in de registersubsleutel ' CurrentVersion ' opgehaald.
De opdracht gebruikt de para meter **Path** om de subsleutel en de para meter name op te geven om de waardenaam van het item op te geven.

De opdracht maakt gebruik van een schuine streep of accent grave ( \` ), het Power shell vervolg teken, om de opdracht op de tweede regel voort te zetten.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### Voor beeld 5: de waardenamen en gegevens van Register vermeldingen in een register sleutel ophalen

Met deze opdracht worden de waardenamen en gegevens van de Register vermeldingen in de register sleutel ' PowerShellEngine ' opgehaald.
De resultaten worden weer gegeven in de volgende voorbeeld uitvoer.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

### Voor beeld 6: de resultaten van register waarden en-gegevens ophalen, opmaken en weer geven

In dit voor beeld ziet u hoe u de uitvoer van een `Get-ItemProperty` opdracht in een lijst kunt opmaken, zodat u de register waarden en gegevens eenvoudig kunt zien en de resultaten gemakkelijk kunt interpreteren.

De eerste opdracht gebruikt de `Get-ItemProperty` cmdlet om de Register vermeldingen in de subsleutel **micro soft. Power shell** op te halen.
Met deze subsleutel worden de opties voor de standaard shell voor Power shell opgeslagen.
De resultaten worden weer gegeven in de volgende voorbeeld uitvoer.

In de uitvoer ziet u dat er twee Register vermeldingen, "pad" en "ExecutionPolicy" zijn.
Wanneer een register sleutel minder dan vijf vermeldingen bevat, wordt deze standaard weer gegeven in een tabel, maar het is vaak gemakkelijker om in een lijst te zien.

De tweede opdracht maakt gebruik van dezelfde `Get-ItemProperty` opdracht.
Deze keer gebruikt de opdracht echter een pijplijn operator ( `|` ) om de resultaten van de opdracht naar de cmdlet te verzenden `Format-List` .
De `Format-List` opdracht gebruikt de eigenschaps parameter met de waarde ' * ' (alle) om alle eigenschappen van de objecten in een lijst weer te geven.
De resultaten worden weer gegeven in de volgende voorbeeld uitvoer.

In het resulterende venster worden de Register vermeldingen ' pad ' en ' ExecutionPolicy ' weer gegeven, samen met een aantal minder bekende eigenschappen van het register sleutel object.
De andere eigenschappen, voorafgegaan door PS, zijn eigenschappen van aangepaste Power shell-objecten, zoals de objecten die de register sleutels vertegenwoordigen.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## PARAMETERS

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.
Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

> [!WARNING]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Windows Power shell.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Uitsluiten

Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten van de bewerking.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
Voer een element of patroon van een pad in, zoals *. txt.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Hiermee geeft u een filter op in de indeling of taal van de provider.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .

De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.
Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
Voer een element of patroon van een pad in, zoals *. txt.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.
In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam op van de eigenschap of eigenschappen die moeten worden opgehaald.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op naar het item of de items.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseTransaction

Hiermee wordt de opdracht opgenomen in de actieve transactie.
Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.
Zie de opdracht opnemen in de actieve trans actie voor meer informatie.
Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.
Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar door sluizen `Get-ItemProperty` .

## UITVOER

### System. Boolean, System. String, System. DateTime

`Get-ItemProperty` retourneert een object voor elke item eigenschap die wordt opgehaald.
Het object type is afhankelijk van het object dat wordt opgehaald.
Zo kan een bestand of map in een bestandssysteem station worden geretourneerd.

## OPMERKINGEN

De `Get-ItemProperty` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u " `Get-PSProvider` ". Zie about_Providers voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Wissen-item Property](Clear-ItemProperty.md)

[Kopiëren-item Property](Copy-ItemProperty.md)

[Verplaatsen-item Property](Move-ItemProperty.md)

[Nieuw-item Property](New-ItemProperty.md)

[Verwijderen-item Property](Remove-ItemProperty.md)

[Naam wijzigen-item Property](Rename-ItemProperty.md)

[Set-item Property](Set-ItemProperty.md)
