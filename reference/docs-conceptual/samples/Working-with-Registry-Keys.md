---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Met registersleutels werken
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736842"
---
# <a name="working-with-registry-keys"></a>Met registersleutels werken

Omdat register sleutels items op Power Shell-stations zijn, is het samen werken met bestanden en mappen vergelijkbaar. Een belang rijk verschil is dat elk item op een op het REGI ster gebaseerd Power Shell-station een container is, net als een map op een bestandssysteem station. Register vermeldingen en de bijbehorende waarden zijn echter eigenschappen van de items, niet de afzonderlijke items.

## <a name="listing-all-subkeys-of-a-registry-key"></a>Alle subsleutels van een register sleutel weer geven

U kunt alle items rechtstreeks in een register sleutel weer geven met behulp van `Get-ChildItem`. Voeg de optionele **Force** -para meter toe om verborgen of systeem items weer te geven. Met deze opdracht worden bijvoorbeeld de items rechtstreeks weer gegeven in het Power Shell-station `HKCU:`, dat overeenkomt met de `HKEY_CURRENT_USER` register component:

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

Dit zijn de sleutels op het hoogste niveau die zichtbaar zijn onder `HKEY_CURRENT_USER` in de REGI ster-editor (Regedit. exe).

U kunt dit registerpad ook opgeven door de naam van de register provider op te geven, gevolgd door `::`. De volledige naam van de register provider is `Microsoft.PowerShell.Core\Registry`, maar dit kan worden inge kort tot alleen `Registry`. Met een van de volgende opdrachten wordt de inhoud direct onder `HKCU:`weer geven.

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Met deze opdrachten worden alleen de rechtstreeks opgenomen items weer geven, vergelijkbaar met het gebruik van `DIR` in **cmd. exe** of `ls` in een Unix-shell. Als u opgenomen items wilt weer geven, moet u de para meter **recursief** opgeven. Als u alle register sleutels in `HKCU:`wilt weer geven, gebruikt u de volgende opdracht.

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

`Get-ChildItem` kunt complexe filter mogelijkheden uitvoeren met de para meters **Path**, **filter**, **include**en **exclude** , maar die para meters zijn doorgaans alleen gebaseerd op naam. U kunt complexe filtering op basis van andere eigenschappen van items uitvoeren met behulp van de cmdlet `Where-Object`. Met de volgende opdracht worden alle sleutels in `HKCU:\Software` gevonden die niet meer dan één subsleutel hebben en ook precies vier waarden hebben:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>Sleutels kopiëren

Kopiëren wordt uitgevoerd met `Copy-Item`. In het volgende voor beeld wordt de `CurrentVersion` subsleutel van `HKLM:\SOFTWARE\Microsoft\Windows\` en alle bijbehorende eigenschappen naar `HKCU:\`gekopieerd.

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

Als u deze nieuwe sleutel in de REGI ster-Editor bekijkt of `Get-ChildItem`gebruikt, ziet u dat er geen kopieën van de subsleutels in de nieuwe locatie aanwezig zijn. Als u de gehele inhoud van een container wilt kopiëren, moet u de para meter **recursief** opgeven. Als u de voor gaande Kopieer opdracht recursief wilt maken, gebruikt u deze opdracht:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

U kunt nog steeds gebruikmaken van andere hulpprogram ma's die u al beschikbaar hebt voor het uitvoeren van bestandssysteem kopieën. Register bewerkings Programma's, zoals **reg. exe**, **Regini. exe**, **regedit. exe**en COM-objecten die ondersteuning bieden voor het bewerken van het REGI ster, zoals **WScript. shell** en WMI-klasse **StdRegProv** , kunnen worden gebruikt vanuit Windows Power shell.

## <a name="creating-keys"></a>Sleutels maken

Het maken van nieuwe sleutels in het REGI ster is eenvoudiger dan het maken van een nieuw item in een bestands systeem. Omdat alle register sleutels containers zijn, hoeft u het item type niet op te geven. u hoeft alleen maar een expliciet pad op te geven, zoals:

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

U kunt ook een op een provider gebaseerd pad gebruiken om een sleutel op te geven:

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a>Sleutels verwijderen

Het verwijderen van items is in wezen hetzelfde voor alle providers. Met de volgende opdrachten worden items op de achtergrond verwijderd:

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>Verwijderen van alle sleutels onder een bepaalde sleutel

U kunt opgenomen items verwijderen door gebruik te maken van `Remove-Item`, maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat. Als we bijvoorbeeld proberen de `HKCU:\CurrentVersion` subsleutel te verwijderen, zien we dit:

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Als u opgenomen items zonder vragen wilt verwijderen, geeft u de para meter **recursief** op:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Als u alle items in `HKCU:\CurrentVersion` wilt verwijderen, maar niet `HKCU:\CurrentVersion` zelf, kunt u in plaats daarvan het volgende gebruiken:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
