---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: d3ff6fe599873edafdda04b3fe17ae01d88c049d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250365"
---
# Show-Command

## SAMENVATTING
Hiermee worden de Power shell-opdracht gegevens in een grafisch venster weer gegeven.

## SYNTAXIS

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## BESCHRIJVING

`Show-Command`Met de cmdlet kunt u een Power shell-opdracht in een opdracht venster maken. U kunt de functies van het opdracht venster gebruiken om de opdracht uit te voeren of de opdracht naar u te retour neren.

`Show-Command` is een zeer nuttig hulp programma voor onderwijs en leer. `Show-Command` werkt op alle opdracht typen, inclusief cmdlets, functies, werk stromen en CIM-opdrachten.

Zonder para meters `Show-Command` wordt een opdracht venster weer gegeven met een lijst met alle beschik bare opdrachten in alle geïnstalleerde modules. Als u de opdrachten in een module wilt zoeken, selecteert u de module in de vervolg keuzelijst modules. Als u een opdracht wilt selecteren, klikt u op de naam van de opdracht.

Als u het opdracht venster wilt gebruiken, selecteert u een opdracht door de naam te gebruiken of door te klikken op de naam van de opdracht in de lijst **opdrachten** . Elke parameterset wordt weer gegeven op een afzonderlijk tabblad. Sterretjes geven de verplichte para meters aan. Als u waarden voor een para meter wilt invoeren, typt u de waarde in het tekstvak of selecteert u de waarde in de vervolg keuzelijst. Als u een para meter switch wilt toevoegen, schakelt u het selectie vakje voor de para meter in.

Wanneer u klaar bent, klikt u op **kopiëren** om de opdracht die u hebt gemaakt naar het klem bord te kopiëren. u kunt ook op **uitvoeren** klikken om de opdracht uit te voeren. U kunt ook de para meter **PassThru** gebruiken om de opdracht te retour neren naar het host-programma, zoals de Power shell-console. Als u de opdracht selectie wilt annuleren en wilt terugkeren naar de weer gave waarin alle opdrachten worden weer gegeven, drukt u op CTRL en klikt u op de geselecteerde opdracht.

In Power shell Integrated Scripting Environment (ISE) wordt standaard een variant van het `Show-Command` venster weer gegeven. Zie de Help-onderwerpen over Power shell ISE voor meer informatie over het gebruik van dit opdracht venster.

Deze cmdlet is geïntroduceerd in Power Shell 3,0.

Omdat deze cmdlet een gebruikers interface vereist, werkt deze niet op Windows Server Core of Windows nano server. Deze cmdlet is alleen beschikbaar op Windows-systemen die ondersteuning bieden voor het Windows-bureau blad.

## VOORBEELDEN

### Voor beeld 1: het venster opdrachten openen

In dit voor beeld wordt de standaard weergave van het venster weer gegeven `Show-Command` . In het venster **opdrachten** wordt een lijst weer gegeven met alle opdrachten in alle modules die op de computer zijn geïnstalleerd.

```powershell
Show-Command
```

### Voor beeld 2: een cmdlet openen in het venster opdrachten

In dit voor beeld wordt de cmdlet weer gegeven `Invoke-Command` in het **opdracht** venster. U kunt deze weer gave gebruiken om opdrachten uit te voeren `Invoke-Command` .

```powershell
Show-Command -Name "Invoke-Command"
```

### Voor beeld 3: een cmdlet met opgegeven para meters openen

Met deze opdracht wordt een `Show-Command` venster geopend voor de `Connect-PSSession` cmdlet.

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

De para meters **Height** en **width** geven de dimensie van het opdracht venster op. Met de para meter **ErrorPopup** wordt het venster met de fout opdracht weer gegeven.

Wanneer u op **uitvoeren** klikt, `Connect-PSSession` wordt de opdracht uitgevoerd, net zoals wanneer u de `Connect-PSSession` opdracht op de opdracht regel hebt getypt.

### Voor beeld 4: nieuwe standaard parameter waarden voor een cmdlet opgeven

In dit voor beeld wordt de `$PSDefaultParameterValues` Automatische variabele gebruikt om nieuwe standaard waarden in te stellen voor de para meters **Height** , **width** en **ErrorPopup** van de `Show-Command` cmdlet.

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

Wanneer u nu een `Show-Command` opdracht uitvoert, worden de nieuwe standaard waarden automatisch toegepast. Als u deze standaard waarden in elke Power shell-sessie wilt gebruiken, voegt u de `$PSDefaultParameterValues` variabele toe aan uw Power shell-profiel. Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) en [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md)voor meer informatie.

### Voor beeld 5: uitvoer naar een raster weergave verzenden

Met deze opdracht wordt aangegeven hoe u `Show-Command` de `Out-GridView` cmdlets en samen gebruikt.

```powershell
Show-Command Get-ChildItem | Out-GridView
```

De opdracht gebruikt de `Show-Command` cmdlet voor het openen van een opdracht venster voor de `Get-ChildItem` cmdlet.
Wanneer u op de knop **uitvoeren** klikt, `Get-ChildItem` wordt de opdracht uitgevoerd en wordt uitvoer gegenereerd. De pijplijn operator (|) verzendt de uitvoer van de `Get-ChildItem` opdracht naar de `Out-GridView` cmdlet, waarmee de `Get-ChildItem` uitvoer in een interactief venster wordt weer gegeven.

### Voor beeld 6: een opdracht weer geven die u in het venster opdrachten hebt gemaakt

In dit voor beeld wordt de opdracht weer gegeven die u in het venster hebt gemaakt `Show-Command` . De opdracht maakt gebruik van de para meter **PassThru** , waarmee de `Show-Command` resultaten in een teken reeks worden geretourneerd.

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

Als u bijvoorbeeld het `Show-Command` venster gebruikt om een opdracht te maken `Get-EventLog` die de vijf nieuwste gebeurtenissen in het gebeurtenis logboek van Windows Power shell ophaalt en vervolgens op **OK** klikt, retourneert de opdracht de hierboven weer gegeven uitvoer. Het weer geven van de opdracht teken reeks helpt u bij het leren van Power shell.

### Voor beeld 7: een opdracht opslaan in een variabele

In dit voor beeld ziet u hoe u de opdracht teken reeks uitvoert die wordt weer gegeven wanneer u de para meter **PassThru** van de `Show-Command` cmdlet gebruikt. Met deze strategie kunt u de opdracht zien en gebruiken.

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

Met de eerste opdracht wordt de para meter **PassThru** van de `Show-Command` cmdlet gebruikt en worden de resultaten van de opdracht in de `$C` variabele opgeslagen. In dit geval gebruiken we het `Show-Command` venster om een opdracht te maken `Get-EventLog` waarmee de vijf nieuwste gebeurtenissen in het gebeurtenis logboek van Windows Power shell worden opgehaald. Wanneer u op **OK** klikt, `Show-Command` wordt de opdracht teken reeks geretourneerd die is opgeslagen in de `$C` variabele.

### Voor beeld 8: de uitvoer van een opdracht opslaan in een variabele

In dit voor beeld wordt de para meter **ErrorPopup** gebruikt om de uitvoer van een opdracht in een variabele op te slaan.

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

Naast het weer geven van fouten in een venster retourneert **ErrorPopup** de opdracht uitvoer naar de huidige opdracht, in plaats van een nieuwe opdracht te maken. Wanneer u deze opdracht uitvoert, `Show-Command` wordt het venster geopend. U kunt de venster functies gebruiken om parameter waarden in te stellen. Als u de opdracht wilt uitvoeren, klikt u op de knop **uitvoeren** in het `Show-Command` venster.

## PARAMETERS

### -ErrorPopup

Geeft aan dat de cmdlet fouten weergeeft in een pop-upvenster, naast de weer gave op de opdracht regel. Wanneer een opdracht die in een venster wordt uitgevoerd, standaard `Show-Command` een fout genereert, wordt de fout alleen weer gegeven op de opdracht regel.

Wanneer u de opdracht uitvoert (met behulp van de knop **uitvoeren** in het `Show-Command` venster), retourneert de para meter **ErrorPopup** de opdracht resultaten naar de huidige opdracht, in plaats van de opdracht uit te voeren en de uitvoer te retour neren naar een nieuwe opdracht. U kunt deze functie gebruiken om de opdracht resultaten in een variabele op te slaan.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Hoogte

Geeft de hoogte van het `Show-Command` venster in pixels. Voer een waarde in tussen 300 en het aantal pixels in de scherm resolutie. Als de waarde te groot is om het opdracht venster weer te geven op het scherm, wordt `Show-Command` er een fout gegenereerd. De standaard hoogte is 600 pixels. Voor een `Show-Command` opdracht die de para meter **name** bevat, is de standaard hoogte 300 pixels.

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee wordt een opdracht venster voor de opgegeven opdracht weer gegeven. Voer de naam van één opdracht in, zoals de naam van een cmdlet, functie of CIM-opdracht. Als u deze para meter weglaat, `Show-Command` wordt een opdracht venster weer gegeven met een lijst met alle Power shell-opdrachten in alle modules die op de computer zijn geïnstalleerd.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCommonParameter

Geeft aan dat deze cmdlet de sectie common para meters van de opdracht weergave weglaat. Standaard worden de algemene para meters weer gegeven in een uitbreidbaar gedeelte onder aan het opdracht venster.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Deze cmdlet genereert standaard geen uitvoer. Als u de opdracht teken reeks wilt uitvoeren, kopieert en plakt u deze bij de opdracht prompt of slaat u deze op in een variabele en gebruikt `Invoke-Expression` u de cmdlet om de teken reeks in de variabele uit te voeren.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Breedte

Geeft de breedte van het `Show-Command` venster in pixels aan. Voer een waarde in tussen 300 en het aantal pixels in de scherm resolutie. Als de waarde te groot is om het opdracht venster weer te geven op het scherm, wordt `Show-Command` er een fout gegenereerd. De standaard breedte is 300 pixels.

```yaml
Type: System.Double
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

U kunt geen pipe invoer naar `Show-Command` .

## UITVOER

### Geen, System. String, System. object

Wanneer u de para meter **PassThru** gebruikt, `Show-Command` wordt een opdracht reeks geretourneerd. Wanneer u de para meter **ErrorPopup** gebruikt, `Show-Command` wordt de uitvoer van de opdracht (een wille keurig object) geretourneerd. Anders `Show-Command` wordt er geen uitvoer gegenereerd.

## OPMERKINGEN

`Show-Command` werkt niet in externe sessies.

## GERELATEERDE KOPPELINGEN
