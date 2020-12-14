---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 948b870948f51bd51424beaeca45ed2b2d195891
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706005"
---
# Disconnect-WSMan

## SAMENVATTING
Verbreekt de verbinding tussen de client en de WinRM-service op een externe computer.

## SYNTAXIS

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Disconnect-WSMan** wordt de verbinding tussen de client en de WinRM-service op een externe computer verbroken.
Als u de WS-Management-sessie in een variabele hebt opgeslagen, blijft het sessie object in de variabele, maar wordt de status van de WS-Management sessie gesloten.
U kunt deze cmdlet in de context van de WSMan-provider gebruiken om de client te verbreken van de WinRM-service op een externe computer.
U kunt deze cmdlet echter ook gebruiken om de verbinding met de WinRM-service op externe computers te verbreken voordat u overschakelt naar de WSMan-provider.

Zie Connect-WSMan voor meer informatie over het maken van een verbinding met de WinRM-service op een externe computer.

## VOORBEELDEN

### Voor beeld 1: een verbinding met een externe computer verwijderen

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

Met deze opdracht wordt de verbinding met de externe computer met de naam Server01 verwijderd.

Deze cmdlet wordt doorgaans gebruikt in de context van de WSMan-provider om de verbinding met een externe computer te verbreken, in dit geval de Server01-computer.
U kunt echter ook **Disconnect-WSMan** gebruiken om verbindingen met externe computers te verwijderen voordat u overschakelt naar de WSMan-provider.
Deze verbindingen worden niet weer gegeven in de lijst computer naam.

## PARAMETERS

### -ComputerName
Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.
De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.
Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.
De lokale computer is de standaard waarde.
Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.
U kunt een waarde voor deze para meter door geven aan de cmdlet.

U kunt de verbinding met de lokale host niet verbreken.
Dat wil zeggen dat u de standaard verbinding met de lokale computer niet kunt verbreken.
Als u echter een afzonderlijke verbinding maakt met de lokale computer, bijvoorbeeld met behulp van de computer naam.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
Deze cmdlet accepteert geen invoer.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Testen-WSMan](Test-WSMan.md)

