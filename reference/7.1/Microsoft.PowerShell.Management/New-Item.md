---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 50a7dba8c4e9cb1cfabd42f39e9fdfb43f22f9b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249856"
---
# New-Item

## SAMENVATTING
Hiermee maakt u een nieuw item.

## SYNTAXIS

### padset (standaard)

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### naamset

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `New-Item` cmdlet maakt een nieuw item en stelt de waarde ervan in. De typen items die kunnen worden gemaakt, zijn afhankelijk van de locatie van het item. In het bestands systeem `New-Item` maakt bijvoorbeeld bestanden en mappen. In het REGI ster worden `New-Item` register sleutels en vermeldingen gemaakt.

`New-Item` kan ook de waarde instellen van de items die het maakt. Als er bijvoorbeeld een nieuw bestand wordt gemaakt, `New-Item` kan de eerste inhoud aan het bestand worden toegevoegd.

## VOORBEELDEN

### Voor beeld 1: een bestand in de huidige map maken

Met deze opdracht maakt u een tekst bestand met de naam ' testfile1.txt ' in de huidige map. De punt ('. ') in de waarde van de para meter **Path** geeft aan dat de huidige map is. De aanhalings tekens die volgen op de **waarde** para meter wordt toegevoegd aan het bestand als inhoud.

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### Voor beeld 2: een directory maken

Met deze opdracht maakt u een map met de naam Logboeken in het `C:` station. De para meter **item** type geeft aan dat het nieuwe item een map is, niet een bestand of een ander bestandssysteem object.

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### Voor beeld 3: een profiel maken

Met deze opdracht maakt u een Power shell-profiel in het pad dat is opgegeven door de `$profile` variabele.

U kunt profielen gebruiken om Power shell aan te passen. `$profile` is een automatische (ingebouwde) variabele waarmee het pad en de bestands naam van het profiel ' CurrentUser/CurrentHost ' worden opgeslagen. Het profiel bestaat standaard niet, hoewel in Power shell een pad en een bestands naam worden opgeslagen.

In deze opdracht vertegenwoordigt de `$profile` variabele het pad van het bestand. **Item** type-para meter geeft aan dat met de opdracht een bestand wordt gemaakt. Met de para meter **Force** kunt u een bestand in het profielpad maken, zelfs wanneer de mappen in het pad niet bestaan.

Nadat u een profiel hebt gemaakt, kunt u aliassen, functies en scripts in het profiel invoeren om uw shell aan te passen.

Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) en [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### Voor beeld 4: een map in een andere Directory maken

In dit voor beeld wordt een nieuwe map scripts gemaakt in de map "C:\PS-Test".

De naam van het nieuwe directory-item, "scripts", is opgenomen in de waarde van de para meter **Path** , in plaats van dat wordt opgegeven in de waarde **naam**. Zoals aangegeven door de syntaxis, is het opdracht formulier geldig.

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### Voor beeld 5: meerdere bestanden maken

In dit voor beeld worden bestanden gemaakt in twee verschillende directory's. Omdat **Path** meerdere teken reeksen accepteert, kunt u deze gebruiken om meerdere items te maken.

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### Voor beeld 6: Joker tekens gebruiken om bestanden in meerdere mappen te maken

De `New-Item` cmdlet ondersteunt joker tekens in de para meter **Path** . Met de volgende opdracht maakt u een `temp.txt` bestand in alle directory's die zijn opgegeven met de joker tekens in de para meter **Path** .

```powershell
Get-ChildItem -Path C:\Temp\
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d-----        5/15/2019   6:45 AM        1   One
d-----        5/15/2019   6:45 AM        1   Two
d-----        5/15/2019   6:45 AM        1   Three
```

```powershell
New-Item -Path * -Name temp.txt -ItemType File | Select-Object FullName
```

```Output
FullName
--------
C:\Temp\One\temp.txt
C:\Temp\Three\temp.txt
C:\Temp\Two\temp.txt
```

Met de `Get-ChildItem` cmdlet worden drie mappen in de map weer gegeven `C:\Temp` . Joker tekens gebruiken met de `New-Item` cmdlet maakt u een `temp.txt` bestand in alle directory's onder de huidige map. De `New-Item` cmdlet voert de items uit die u hebt gemaakt, waarnaar wordt gepiped om `Select-Object` de paden van de zojuist gemaakte bestanden te controleren.

### Voor beeld 7: een symbolische koppeling naar een bestand of map maken

In dit voor beeld wordt een symbolische koppeling gemaakt naar het Notice.txt-bestand in de huidige map.

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

In dit voor beeld is **target** een alias voor de **waarde** -para meter. Het doel van de symbolische koppeling kan een relatief pad zijn. Vóór Power shell v 6.2 moet het doel een volledig pad zijn.

Vanaf Power shell 7,1 kunt u nu een **SymbolicLink** maken in een map in Windows met behulp van een relatief pad.

### Voor beeld 8: gebruik de para meter-Force om mappen opnieuw te maken

In dit voor beeld wordt een map gemaakt met een bestand in. Vervolgens wordt geprobeerd om dezelfde map te maken met `-Force` . De map wordt niet overschreven, maar er wordt gewoon het bestaande map-object geretourneerd waarbij het bestand intact is gemaakt.

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### Voor beeld 9: de para meter-Force gebruiken om bestaande bestanden te overschrijven

In dit voor beeld wordt een bestand gemaakt met een waarde en wordt het bestand vervolgens opnieuw gemaakt met `-Force` . Hiermee wordt het bestaande bestand overschreven, waardoor de inhoud verloren gaat, omdat u de eigenschap length kunt zien

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> Wanneer u gebruikt `New-Item` met de `-Force` switch om register sleutels te maken, werkt de opdracht hetzelfde als bij het overschrijven van een bestand. Als de register sleutel al bestaat, worden de sleutel en alle eigenschappen en waarden overschreven met een lege register sleutel.

## PARAMETERS

### -Credential

> [!NOTE]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell. Gebruik om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert `Invoke-Command` .

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

### -Force

Hiermee wordt de cmdlet gedwongen een item te maken dat over een bestaand alleen-lezen item schrijft. De implementatie varieert van provider tot provider. Zelfs met behulp van de para meter **forceren** , kan de cmdlet geen beveiligings beperkingen opheffen.

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

### -Item type

Hiermee wordt het type provider opgegeven van het nieuwe item. De beschik bare waarden van deze para meter zijn afhankelijk van de huidige provider die u gebruikt.

Als uw locatie zich in een station bevindt `FileSystem` , zijn de volgende waarden toegestaan:

- Bestand
- Directory
- SymbolicLink
- Verbinding
- Hard link

> [!NOTE]
> Het maken `SymbolicLink` van een type in Windows vereist uitbrei ding als beheerder. Windows 10 (build 14972 of nieuwer) waarvoor de ontwikkelaars modus is ingeschakeld, vereist echter niet langer de benodigde uitbrei ding voor het maken van symbolische koppelingen.

`Certificate`Dit zijn de waarden die u kunt opgeven in een station:

- Certificaat provider
- Certificaat
- Opslaan
- StoreLocation

Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam van het nieuwe item. U kunt de naam van het nieuwe item in de waarde van de para meter **name** of **Path** opgeven, en u kunt het pad van het nieuwe item opgeven in de **naam** of de waarde van het **pad** . Namen van items die worden door gegeven met de para meter **name** , worden gemaakt ten opzichte van de waarde van de para meter **Path** .

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad van de locatie van het nieuwe item. De standaard waarde is de huidige locatie wanneer het **pad** wordt wegge laten. U kunt de naam van het nieuwe item opgeven in de **naam** of het **pad** op te geven. Namen van items die worden door gegeven met de para meter **name** , worden gemaakt ten opzichte van de waarde van de para meter **Path** .

Voor deze cmdlet werkt de para meter **Path** als de **LiteralPath** -para meter van andere cmdlets.
Joker tekens worden niet geïnterpreteerd. Alle tekens worden door gegeven aan de provider van de locatie. De provider biedt mogelijk geen ondersteuning voor alle tekens. U kunt bijvoorbeeld geen bestands naam maken die een asterisk ()- `*` teken bevat.

```yaml
Type: System.String[]
Parameter Sets: pathSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Waarde

Hiermee geeft u de waarde van het nieuwe item op. U kunt ook een waarde door sluizen naar `New-Item` .

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

### System. object

U kunt een waarde voor het nieuwe item door sluizen naar deze cmdlet.

## UITVOER

### System. object

Met deze cmdlet wordt het item geretourneerd dat wordt gemaakt.

## OPMERKINGEN

`New-Item` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` . Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Wissen-item](Clear-Item.md)

[Kopie-item](Copy-Item.md)

[Get-item](Get-Item.md)

[Invoke-item](Invoke-Item.md)

[Item verplaatsen](Move-Item.md)

[Verwijderen-item](Remove-Item.md)

[Naam wijzigen-item](Rename-Item.md)

[Set-item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

