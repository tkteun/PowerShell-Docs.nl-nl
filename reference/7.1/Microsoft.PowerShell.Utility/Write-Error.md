---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: ad9e3daa7d67fc2bec6fa19a873573ce33dc609d
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253022"
---
# Write-Error

## SAMENVATTING
Schrijft een object naar de fout stroom.

## SYNTAXIS

### Except (standaard)

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### WithException

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### ErrorRecord

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## BESCHRIJVING

De `Write-Error` cmdlet declareert een niet-afsluit fout. Standaard worden fouten in de fout stroom naar het hostprogramma verzonden, samen met de uitvoer.

Als u een niet-afsluit fout wilt schrijven, voert u een teken reeks voor het fout bericht, een **ErrorRecord** -object of een **uitzonderings** object in. Gebruik de andere para meters van `Write-Error` om de fout record in te vullen.

Bij niet-afsluit fouten wordt een fout naar de fout stroom geschreven, maar de opdracht verwerking wordt niet gestopt.
Als een niet-afsluit fout wordt gedeclareerd voor één item in een verzameling invoer items, blijft de opdracht door gaan met het verwerken van de andere items in de verzameling.

Als u een afsluit fout wilt declareren, gebruikt u het `Throw` sleutel woord.
Zie [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: een fout voor RegistryKey-object schrijven

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

Met deze opdracht wordt een niet-afsluit fout gedeclareerd wanneer de `Get-ChildItem` cmdlet een `Microsoft.Win32.RegistryKey` object retourneert, zoals de objecten in de `HKLM:` of de `HKCU:` stations van de Power shell-register provider.

### Voor beeld 2: een fout bericht naar de console schrijven

```powershell
Write-Error "Access denied."
```

Met deze opdracht wordt een niet-afsluit fout gedeclareerd en wordt de fout ' toegang geweigerd ' geschreven. De opdracht gebruikt de para meter **Message** om het bericht op te geven, maar laat de optionele **bericht** parameter naam achterwege.

### Voor beeld 3: een fout naar de console schrijven en de categorie opgeven

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

Met deze opdracht wordt een niet-afsluit fout gedeclareerd en wordt een fout categorie opgegeven.

### Voor beeld 4: een fout schrijven met behulp van een uitzonderings object

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

Met deze opdracht wordt een **uitzonderings** object gebruikt om een niet-afsluit fout te declareren.

De eerste opdracht maakt gebruik van een hash-tabel om het object **System. Exception** te maken. Hiermee wordt het uitzonderings object in de `$E` variabele opgeslagen. U kunt een hash-tabel gebruiken om een object van een type te maken dat een null-constructor heeft.

De tweede opdracht gebruikt de `Write-Error` cmdlet om een niet-afsluit fout te declareren. De waarde van de **uitzonderings** parameter is het **uitzonderings** object in de `$E` variabele.

## PARAMETERS

### -Categorie

Hiermee geeft u de categorie van de fout op. De standaard waarde is **NotSpecified**. De aanvaardbare waarden voor deze parameter zijn:

- NotSpecified
- Openstaande fout
- CloseError
- DeviceError
- DeadlockDetected
- InvalidArgument
- InvalidData
- InvalidOperation
- InvalidResult
- InvalidType
- MetadataError
- Niet geïmplementeerd
- NotInstalled
- ObjectNotFound
- OperationStopped
- OperationTimeout
- SyntaxError
- ParserError
- PermissionDenied
- ResourceBusy
- ResourceExists
- ResourceUnavailable
- ReadError
- WriteError
- FromStdErr
- SecurityError
- ProtocolError
- ConnectionError
- AuthenticationError
- LimitsExceeded
- QuotaExceeded
- NotEnabled

Zie [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600)(Engelstalig) voor meer informatie over de fout categorieën.

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryActivity

Hiermee geeft u de actie op die de fout heeft veroorzaakt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryReason

Hiermee geeft u op hoe of waarom de activiteit de fout heeft veroorzaakt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetName

Hiermee geeft u de naam op van het object dat werd verwerkt toen de fout optrad.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetType

Hiermee geeft u het type van het object op dat werd verwerkt toen de fout optrad.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorId

Hiermee geeft u een ID-teken reeks op om de fout te identificeren. De teken reeks moet uniek zijn voor de fout.

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorRecord

Hiermee geeft u een fout record object op dat de fout vertegenwoordigt. Gebruik de eigenschappen van het object om de fout te beschrijven.

Als u een fout record object wilt maken, gebruikt u de `New-Object` cmdlet of haalt u een fout record object op uit de matrix in de `$Error` Automatische variabele.

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uitzonde ring

Hiermee geeft u een uitzonderings object op dat de fout vertegenwoordigt. Gebruik de eigenschappen van het object om de fout te beschrijven.

Als u een uitzonderings object wilt maken, gebruikt u een hash-tabel of gebruikt u de `New-Object` cmdlet.

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bericht

Hiermee geeft u de bericht tekst van de fout op. Als de tekst spaties of speciale tekens bevat, plaatst u deze tussen aanhalings tekens. U kunt ook een bericht teken reeks door sluizen naar `Write-Error` .

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -RecommendedAction

Hiermee geeft u de actie op die de gebruiker moet ondernemen om de fout op te lossen of te voor komen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Target object

Hiermee geeft u het object op dat werd verwerkt toen de fout optrad. Voer het object in, een variabele die het object bevat of een opdracht die het object ophaalt.

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
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

### System. String

U kunt een teken reeks die een fout bericht bevat door sluizen naar `Write-Error` .

## UITVOER

### Fout object

`Write-Error` schrijft alleen naar de fout stroom. Er worden geen objecten geretourneerd.

## OPMERKINGEN

`Write-Error` de waarde van de automatische variabele wordt niet gewijzigd `$?` , dus er wordt geen afsluitende fout weer gegeven. Als u een afsluitende fout wilt verzenden, gebruikt u de methode [$PSCmdlet. WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) .

## GERELATEERDE KOPPELINGEN

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Schrijf fouten opsporen](Write-Debug.md)

[Write-host](Write-Host.md)

[Write-output](Write-Output.md)

[Schrijf voortgang](Write-Progress.md)

[Write-verbose](Write-Verbose.md)

[Waarschuwing voor schrijven](Write-Warning.md)
