---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: e64565cbc567ca42b190e143e065f9eddba2f311
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249420"
---
# Test-PSSessionConfigurationFile

## SAMENVATTING
Verifieert de sleutels en waarden in een sessie configuratie bestand.

## SYNTAXIS

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet wordt gecontroleerd of een sessie configuratie bestand geldige sleutels bevat en de waarden van het juiste type zijn. Voor opgesomde waarden controleert de cmdlet of de opgegeven waarden geldig zijn.

De cmdlet wordt geretourneerd `$True` als het bestand alle tests doorgeeft en `$False` als dit niet het geval is. Gebruik de para meter **uitgebreid** om eventuele fouten te vinden.

`Test-PSSessionConfigurationFile` verifieert de sessie configuratie bestanden, zoals die zijn gemaakt door de `New-PSSessionConfigurationFile` cmdlet. Zie [about_Session_Configurations](About/about_Session_Configurations.md)voor meer informatie over de configuratie van sessies. Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.

Deze cmdlet is geïntroduceerd in Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een configuratie bestand voor een sessie testen

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### Voor beeld 2: het sessie configuratie bestand van een sessie configuratie testen

In dit voor beeld testen we het configuratie bestand dat wordt gebruikt in de **beperkte** sessie configuratie.
De waarde van de para meter **Path** is het resultaat van de `Get-PSSessionConfiguration` opdracht die de **beperkte** sessie configuratie haalt. Het pad van het sessie configuratie bestand wordt opgeslagen in de waarde van de eigenschap **ConfigFilePath** van de sessie configuratie.

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### Voor beeld 3: alle sessie configuratie bestanden testen

Met de functie in dit voor beeld worden alle sessie configuratie bestanden op de lokale computer getest. De functie gebruikt de `Get-PSSessionConfiguration` cmdlet om alle sessie configuraties op te halen. Met de code in de `ForEach-Object` lus wordt het bestandspad weer gegeven en worden alle sessie configuraties getest.

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

De eigenschap **ConfigFilePath** van een sessie configuratie bevat het pad naar het sessie configuratie bestand dat in de sessie configuratie wordt gebruikt, indien aanwezig.

Als de waarde van de eigenschap **ConfigFilePath** is ingevuld (is waar), wordt met de opdracht de waarde van de eigenschap **ConfigFilePath** opgehaald (afgedrukt). Vervolgens wordt de `Test-PSSessionConfigurationFile` cmdlet gebruikt om het bestand te testen in de waarde **ConfigFilePath** . De para meter **uitgebreid** retourneert de bestands fout wanneer het bestand de test mislukt.

## PARAMETERS

### -Path

Hiermee geeft u het pad en de bestands naam van een sessie configuratie bestand (. pssc). Als u het pad weglaat, de standaard instelling is de huidige map. Joker tekens worden ondersteund, maar moeten worden omgezet in één bestand. U kunt ook een pad naar een sessie configuratie bestand door geven aan `Test-PSSessionConfigurationFile` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een pad naar een sessie configuratie bestand door geven aan `Test-PSSessionConfigurationFile` .

## UITVOER

### System. Boolean

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Registratie ongedaan maken-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
