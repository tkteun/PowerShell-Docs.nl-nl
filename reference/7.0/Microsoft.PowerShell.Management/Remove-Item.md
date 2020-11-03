---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: ddb3f8d1889887e01db8663e21cdb0323e6d4084
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249416"
---
# Remove-Item

## SAMENVATTING
Hiermee verwijdert u de opgegeven items.

## SYNTAXIS

### Pad (standaard)

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

### LiteralPath

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

## BESCHRIJVING

Met de `Remove-Item` cmdlet worden een of meer items verwijderd. Omdat het wordt ondersteund door veel providers, kan het veel verschillende typen items verwijderen, waaronder bestanden, mappen, register sleutels, variabelen, aliassen en functies.

## VOORBEELDEN

### Voor beeld 1: bestanden met de bestandsnaam extensie verwijderen

In dit voor beeld worden alle bestanden met namen die een punt ( `.` ) van de map bevatten verwijderd `C:\Test` . Omdat de opdracht een punt opgeeft, verwijdert de opdracht geen mappen of bestanden die geen bestandsnaam extensie hebben.

```powershell
Remove-Item C:\Test\*.*
```

### Voor beeld 2: een aantal van de document bestanden in een map verwijderen

In dit voor beeld worden alle bestanden die een `.doc` bestandsnaam extensie hebben en een naam die niet is inbegrepen, verwijderd uit de huidige map `*1*` .

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

Het Joker teken () wordt gebruikt `*` om de inhoud van de huidige map op te geven. Hierbij worden de para meters **opnemen** en **uitsluiten** gebruikt om de bestanden op te geven die moeten worden verwijderd.

### Voor beeld 3: verborgen, alleen-lezen bestanden verwijderen

Met deze opdracht wordt een bestand verwijderd dat zowel *verborgen* als *alleen-lezen* is.

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

De para meter **Path** wordt gebruikt om het bestand op te geven. De para meter **Force** wordt gebruikt om deze te verwijderen. Zonder **forceren** kunt u _alleen-lezen_ of _verborgen_ bestanden verwijderen.

### Voor beeld 4: bestanden in submappen recursief verwijderen

Met deze opdracht worden alle CSV-bestanden in de huidige map en alle submappen recursief verwijderd.

Omdat de **recursieve** para meter in `Remove-Item` een bekend probleem heeft, gebruikt de opdracht in dit voor beeld `Get-ChildItem` om de gewenste bestanden op te halen. vervolgens wordt de pijplijn operator gebruikt om deze door te geven aan `Remove-Item` .

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

In de `Get-ChildItem` opdracht heeft **Path** de waarde ( `*` ), die de inhoud van de huidige map vertegenwoordigt. Het maakt **gebruik van** het BESTANDS type CSV en maakt gebruik van **recursie** om het ophalen te recursief maken. Als u het bestands type opgeeft, zoals, wordt door `-Path *.csv` de cmdlet het onderwerp van de zoek opdracht geïnterpreteerd als een bestand zonder onderliggende items en mislukt het opnieuw. **Recurse**

### Voor beeld 5: subsleutels recursief verwijderen

Met deze opdracht worden de register sleutel ' OldApp ' en alle bijbehorende subsleutels en waarden verwijderd. `Remove-Item`De code wordt gebruikt om de sleutel te verwijderen. Het pad is opgegeven, maar de optionele parameter naam ( **pad** ) wordt wegge laten.

Met de **recursieve** para meter wordt alle inhoud van de sleutel ' OldApp ' recursief verwijderd. Als de sleutel subsleutels bevat en u de para meter **recursief** weglaat, wordt u gevraagd om te bevestigen dat u de inhoud van de sleutel wilt verwijderen.

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### Voor beeld 6: bestanden met speciale tekens verwijderen

In het volgende voor beeld ziet u hoe u bestanden verwijdert die speciale tekens bevatten, zoals haakjes of haakjes.

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### Voor beeld 7: een alternatieve gegevens stroom verwijderen

Dit voor beeld laat zien hoe u de dynamische **Stream** -para meter van de cmdlet kunt gebruiken `Remove-Item` om een alternatieve gegevens stroom te verwijderen. De stream-para meter is geïntroduceerd in Windows Power Shell 3,0.

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

De **Stream** -para meter `Get-Item` haalt de **zone. id** -stroom van het `Copy-Script.ps1` bestand op. `Remove-Item` maakt gebruik van de para meter **Stream** om de **zone. id** -stroom van het bestand te verwijderen. Ten slotte `Get-Item` ziet de cmdlet dat de **zone. id** -stroom is verwijderd.

## PARAMETERS

### -Credential

> [!NOTE]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.
> Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.

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

Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `*.txt` . Joker tekens zijn toegestaan. De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Hiermee geeft u een filter op om de para meter **Path** te kwalificeren. De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt. U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.
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

### -Force

Hiermee wordt de cmdlet gedwongen om items te verwijderen die anders niet kunnen worden gewijzigd, zoals verborgen of alleen-lezen bestanden of alleen-lezen-aliassen of-variabelen. De cmdlet kan geen constante aliassen of variabelen verwijderen.
De implementatie varieert van provider tot provider. Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie. Zelfs met behulp van de para meter **forceren** , kan de cmdlet geen beveiligings beperkingen opheffen.

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

### -Include

Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `"*.txt"` . Joker tekens zijn toegestaan. De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

Hiermee geeft u een pad naar een of meer locaties. De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u een pad op van de items die worden verwijderd.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Recursief

Geeft aan dat met deze cmdlet de items in de opgegeven locaties en alle onderliggende items van de locaties worden verwijderd.

Als deze wordt gebruikt in combi natie met de para meter **include** , kunnen de **recursieve** para meter niet alle submappen of alle onderliggende items verwijderen. Dit is een bekend probleem. Als tijdelijke oplossing kunt u de resultaten van de `Get-ChildItem -Recurse` opdracht Afdrukken naar `Remove-Item` , zoals beschreven in ' voor beeld 4 ' in dit onderwerp.

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

### -Stream

De **Stream** -para meter is een dynamische para meter waaraan de File System Provider toevoegt `Remove-Item` .
Deze para meter werkt alleen op stations met een bestands systeem.

U kunt gebruiken `Remove-Item` om een alternatieve gegevens stroom te verwijderen. Het is echter niet de aanbevolen manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd. Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert. Raadpleeg voor meer informatie de volgende artikelen:

- [about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

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

U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

De `Remove-Item` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

Wanneer u probeert een map te verwijderen die items bevat zonder de para meter **recursieve** te gebruiken, wordt door de cmdlet om bevestiging gevraagd. Met behulp van `-Confirm:$false` wordt de prompt niet onderdrukt. Dit is standaard.

## GERELATEERDE KOPPELINGEN

[Wissen-item](Clear-Item.md)

[Kopie-item](Copy-Item.md)

[Get-item](Get-Item.md)

[Invoke-item](Invoke-Item.md)

[Item verplaatsen](Move-Item.md)

[Nieuw-item](New-Item.md)

[Verwijderen-item Property](Remove-ItemProperty.md)

[Naam wijzigen-item](Rename-Item.md)

[Set-item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)
