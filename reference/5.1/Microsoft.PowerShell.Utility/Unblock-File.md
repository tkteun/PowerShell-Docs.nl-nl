---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 57c8c6f2ceda124b3dc89c363c6cf942680781ca
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344504"
---
# Unblock-File

## SAMENVATTING
De blok kering van bestanden die zijn gedownload van het internet.

## SYNTAXIS

### ByPath (standaard)

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Unblock-File`Met de cmdlet kunt u bestanden openen die zijn gedownload van het internet. Power shell-script bestanden die zijn gedownload van het Internet, worden gedeblokkeerd, zodat u ze kunt uitvoeren, zelfs wanneer het Power shell-uitvoerings beleid **RemoteSigned** is. Deze bestanden worden standaard geblokkeerd om de computer te beschermen tegen niet-vertrouwde bestanden.

Voordat u de `Unblock-File` cmdlet gebruikt, controleert u het bestand en de bron en controleert u of het veilig is om te openen.

Intern verwijdert de `Unblock-File` cmdlet de zone. id alternatieve gegevens stroom, met de waarde ' 3 ' om aan te geven dat deze is gedownload van het internet.

Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)voor meer informatie over het uitvoeren van Power shell-uitvoerings beleid.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: de blok kering van een bestand opheffen

Met deze opdracht wordt het bestand PowerShellTips. chm gedeblokkeerd.

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### Voor beeld 2: meerdere bestanden deblokkeren

Met deze opdracht wordt de blok kering van alle bestanden in de map met de `C:\Downloads` naam Power shell opgeheven. Voer een opdracht zoals deze pas uit nadat u hebt gecontroleerd of alle bestanden veilig zijn.

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### Voor beeld 3: scripts zoeken en deblokkeren

Met deze opdracht wordt uitgelegd hoe u Power shell-scripts kunt vinden en deblokkeren.

In de eerste opdracht wordt de para meter **Stream** van de cmdlet *Get-item* gebruikt voor het ophalen van bestanden met de zone. id-stroom.

Met de tweede opdracht wordt aangegeven wat er gebeurt wanneer u een geblokkeerd script uitvoert in een Power shell-sessie waarin het uitvoerings beleid is **RemoteSigned**. Het RemoteSigned-beleid voor komt dat u scripts kunt uitvoeren die van Internet worden gedownload, tenzij ze digitaal zijn ondertekend.

De derde opdracht gebruikt de `Unblock-File` cmdlet om het script uit te blok keren zodat dit in de sessie kan worden uitgevoerd.

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## PARAMETERS

### -LiteralPath

Hiermee geeft u de bestanden op die u wilt deblokkeren. In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u de bestanden op die u wilt deblokkeren. Joker tekens worden ondersteund.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een bestandspad door sluizen naar `Unblock-File` .

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

- De `Unblock-File` cmdlet werkt alleen op stations met een bestands systeem.
- `Unblock-File` voert dezelfde bewerking uit als de knop voor het **opheffen van de blok kering** in het dialoog venster **Eigenschappen** in Verkenner.
- Als u de `Unblock-File` cmdlet gebruikt voor een bestand dat niet is geblokkeerd, heeft de opdracht geen effect op het niet-geblokkeerde bestand en worden er geen fouten gegenereerd door de cmdlet.

## GERELATEERDE KOPPELINGEN

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Get-item](../Microsoft.PowerShell.Management/Get-Item.md)

[Out-file](Out-File.md)

[Bestandssysteem provider](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
