---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 4703586008d9044ae68fd7375db65f0d0a9b9980
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/13/2020
ms.locfileid: "93251815"
---
# Invoke-DscResource

## SAMENVATTING
Hiermee wordt een methode uitgevoerd van een opgegeven DSC-resource (desired state Configuration) van Power shell.

## SYNTAXIS

```
Invoke-DscResource [[-Method] <Object>] [[-Name] <Object>] [[-Property] <Object>]
 [[-ModuleName] <Object>] [-AsJob] [<CommonParameters>]
```

## BESCHRIJVING

`Invoke-DscResource`Met de cmdlet wordt een methode uitgevoerd van een opgegeven DSC-resource (desired state Configuration) van Power shell.

Met deze cmdlet wordt een DSC-resource rechtstreeks aangeroepen zonder dat er een configuratie document wordt gemaakt. Met deze cmdlet kunnen Configuration Management-producten Windows of Linux beheren met behulp van DSC-resources. Met deze cmdlet schakelt u ook fout opsporing van resources in wanneer de DSC-engine wordt uitgevoerd met fout opsporing ingeschakeld.

> [!NOTE]
> `Invoke-DscResource` is een experimentele functie in Power shell 7. Als u de cmdlet wilt gebruiken, moet u deze inschakelen met de volgende opdracht.
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## VOORBEELDEN

### Voor beeld 1: de set-methode van een bron aanroepen door de verplichte eigenschappen op te geven

In dit voor beeld wordt de **set** -methode van een resource met de naam **WindowsProcess** aangeroepen en worden de eigenschappen van het verplichte **pad** en de **argumenten** geboden om het opgegeven Windows-proces te starten.

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### Voor beeld 2: de test methode van een resource aanroepen voor een opgegeven module

In dit voor beeld wordt de **test** methode aangeroepen van een resource met de naam **WindowsProcess** , die zich in de module met de naam **PSDesiredStateConfiguration** bevindt.

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## PARAMETERS

### -Methode

Hiermee geeft u de methode van de resource op die door deze cmdlet wordt aangeroepen. De acceptabele waarden voor deze para meter zijn: **Get** , **set** en **test**.

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module naam

Hiermee geeft u de naam van de module op waaruit deze cmdlet de opgegeven resource aanroept.

```yaml
Type: ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam op van de DSC-resource die moet worden gestart.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Eigenschap

Hiermee geeft u de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### Micro soft. Management. Infrastructure. CimInstance, System. Boolean

## OPMERKINGEN

- Voorheen werden Windows Power shell 5,1-bronnen uitgevoerd onder systeem context, tenzij ze zijn opgegeven met de gebruikers context met de Key **PsDscRunAsCredential**. In Power shell 7,0 worden resources uitgevoerd in de context van de gebruiker en wordt **PsDscRunAsCredential** niet meer ondersteund. Bij eerdere configuraties met deze sleutel wordt een uitzonde ring gegenereerd.

- Vanaf Power shell 7 `Invoke-DscResource` biedt geen ondersteuning meer voor het aanroepen van WMI DSC-resources. Dit omvat de **Bestands** -en **logboek** bronnen in **PSDesiredStateConfiguration**.

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-Dscresource bieden](Get-DscResource.md)
