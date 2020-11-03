---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 353469a02a1580df6c9b238ca8db4ddb46cd18f1
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249802"
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

Met de cmdlet voor het **opheffen** van de bestanden kunt u bestand openen die vanaf internet zijn gedownload.
Power shell-script bestanden die zijn gedownload van het Internet, worden gedeblokkeerd, zodat u ze kunt uitvoeren, zelfs wanneer het Power shell-uitvoerings beleid **RemoteSigned** is.
Deze bestanden worden standaard geblokkeerd om de computer te beschermen tegen niet-vertrouwde bestanden.

Controleer het bestand en de bron en controleer of het veilig kan worden geopend voordat u de cmdlet voor **Deblokkerene bestanden** gebruikt.

Intern verwijdert de **deblokkerings bestand-** cmdlet de zone. alternatieve gegevens stroom van de id, die de waarde 3 heeft om aan te geven dat deze van Internet is gedownload.

Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)voor meer informatie over het uitvoeren van Power shell-uitvoerings beleid.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: de blok kering van een bestand opheffen

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

Met deze opdracht wordt het bestand PowerShellTips. chm gedeblokkeerd.

### Voor beeld 2: meerdere bestanden deblokkeren

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

Met deze opdracht wordt de blok kering van alle bestanden in de C:\Downloads-map waarvan de naam Power shell bevat.
Voer een opdracht zoals deze pas uit nadat u hebt gecontroleerd of alle bestanden veilig zijn.

### Voor beeld 3: scripts zoeken en deblokkeren

```
The first command uses the *Stream* parameter of the Get-Item cmdlet get files with the Zone.Identifier stream.Although you could pipe the output directly to the **Unblock-File** cmdlet (Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue | ForEach {Unblock-File $_.FileName}), it is prudent to review the file and confirm that it is safe before unblocking.
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**. The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.
PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

The third command uses the **Unblock-File** cmdlet to unblock the script so it can run in the session.
PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

Met deze opdracht wordt uitgelegd hoe u Power shell-scripts kunt vinden en deblokkeren.

## PARAMETERS

### -LiteralPath
Hiermee geeft u de bestanden op die u wilt deblokkeren.
In tegens telling tot *Path* wordt de waarde van de para meter *LiteralPath* exact gebruikt wanneer deze wordt getypt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

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
Hiermee geeft u de bestanden op die u wilt deblokkeren.
Joker tekens worden ondersteund.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een bestandspad voor het **deblokkeren van bestanden** door sluizen.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

- Ondersteuning voor macOS is toegevoegd in Power shell 7.
- De `Unblock-File` cmdlet werkt alleen op stations met een bestands systeem.
- `Unblock-File` voert dezelfde bewerking uit als de knop voor het **opheffen van de blok kering** in het dialoog venster **Eigenschappen** in Verkenner.
- Als u de `Unblock-File` cmdlet gebruikt voor een bestand dat niet is geblokkeerd, heeft de opdracht geen effect op het niet-geblokkeerde bestand en worden er geen fouten gegenereerd door de cmdlet.

## GERELATEERDE KOPPELINGEN

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Get-item](../Microsoft.PowerShell.Management/Get-Item.md)

[Out-file](Out-File.md)

[Bestandssysteem provider](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
