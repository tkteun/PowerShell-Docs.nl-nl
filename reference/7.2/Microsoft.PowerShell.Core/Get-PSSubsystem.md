---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
schema: 2.0.0
ms.openlocfilehash: 5cb8ddbd06f8b7fdbadae0b7c738e26a68ff5c48
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706197"
---
# Get-PSSubsystem

## SAMENVATTING
Haalt informatie op over de subsystemen die zijn geregistreerd in Power shell.

## SYNTAXIS

### GetAllSet (standaard)

```
Get-PSSubsystem [<CommonParameters>]
```

### GetByKindSet

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### GetByTypeSet

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## BESCHRIJVING

Haalt informatie op over de subsystemen die zijn geregistreerd in Power shell.

> [!NOTE]
> Dit is een experimentele functie. Deze cmdlet is alleen beschikbaar wanneer de `PSSubsystemPluginModel` functie is ingeschakeld. Zie [experimentele functies gebruiken](/powershell/scripting/learn/experimental-features)voor meer informatie.

De functie maakt het mogelijk om onderdelen van te scheiden `System.Management.Automation.dll` in afzonderlijke subsystemen die zich in hun eigen assembly bevinden. Deze schei ding vermindert het schijf gebruik van de kern-Power shell-engine en maakt het mogelijk dat deze onderdelen optionele functies worden voor een minimale Power shell-installatie.

Op dit moment wordt alleen het subsysteem **CommandPredictor** ondersteund. Dit subsysteem wordt samen met de PSReadLine-module gebruikt om aangepaste Voorspellings-invoeg toepassingen te bieden. In de toekomst kunnen **Job**, **CommandCompleter**, **Remoting** en andere onderdelen worden gescheiden in subsysteem-assembly's buiten `System.Management.Automation.dll` .

## VOORBEELDEN

### Voor beeld 1: alle beschik bare subsystemen weer geven

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### Voor beeld 2: alle beschik bare subsystemen van een specifiek type weer geven

```powershell
PS> Get-PSSubsystem -Kind CommandPredictor | Format-List
```

```Output
Kind                      : CommandPredictor
SubsystemType             : System.Management.Automation.Subsystem.ICommandPredictor
AllowUnregistration       : True
AllowMultipleRegistration : True
RequiredCmdlets           : {}
RequiredFunctions         : {}
IsRegistered              : False
Implementations           : {}
```

## PARAMETERS

### -Soort


Hiermee geeft u het soort subsysteem moet worden geretourneerd. Geldige waarden zijn: `CommandPredictor` .

```yaml
Type: System.Management.Automation.Subsystem.SubsystemKind
Parameter Sets: GetByKindSet
Aliases:
Accepted values: CommandPredictor

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -SubsystemType

Hiermee geeft u het type subsysteem moet worden geretourneerd.

```yaml
Type: System.Type
Parameter Sets: GetByTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. subsysteem. SubsystemKind

### System. type

## UITVOER

### System. Management. Automation. subsysteem. SubsystemInfo

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_experimental_features](about/about_experimental_features.md)

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Enable-ExperimentalFeature](Get-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)

[Experimentele functies gebruiken](/powershell/scripting/learn/experimental-features)
