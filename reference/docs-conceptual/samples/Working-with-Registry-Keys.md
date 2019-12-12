---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Met registersleutels werken
ms.openlocfilehash: 18daeaea2ee8917a709fef421d2b316f46bf7f4c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030653"
---
# <a name="working-with-registry-keys"></a>Met registersleutels werken

Omdat register sleutels items zijn op Windows Power Shell-stations, is het samen werken met bestanden en mappen vergelijkbaar. Een belang rijk verschil is dat elk item op een op het REGI ster gebaseerd Windows Power Shell-station een container is, net als een map op een bestandssysteem station. Register vermeldingen en de bijbehorende waarden zijn echter eigenschappen van de items, niet de afzonderlijke items.

## <a name="listing-all-subkeys-of-a-registry-key"></a>Alle subsleutels van een register sleutel weer geven

U kunt alle items rechtstreeks in een register sleutel weer geven met behulp van **Get-Child item**. Voeg de optionele **Force** -para meter toe om verborgen of systeem items weer te geven. Met deze opdracht worden bijvoorbeeld de items rechtstreeks in Windows Power Shell-station HKCU:, dat overeenkomt met de HKEY_CURRENT_USER register component:

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

Dit zijn de sleutels op het hoogste niveau die zichtbaar zijn onder HKEY_CURRENT_USER in de REGI ster-editor (Regedit. exe).

U kunt dit registerpad ook opgeven door de naam van de register provider op te geven, gevolgd door ' **::** '. De volledige naam van de register provider is **micro soft. Power shell. Core\\Registry**, maar dit kan worden inge kort tot alleen het **REGI ster**. Met een van de volgende opdrachten wordt de inhoud direct onder HKCU weer geven:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Met deze opdrachten worden alleen de direct opgenomen items weer geven, vergelijkbaar met het gebruik van de **dir** opdracht van cmd. exe of **ls** in een Unix-shell. Als u opgenomen items wilt weer geven, moet u de para meter **recursief** opgeven. Als u alle register sleutels in HKCU wilt weer geven, gebruikt u de volgende opdracht (deze bewerking kan erg lang duren):

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-Child item** kan complexe filter mogelijkheden uitvoeren met de para meters **Path**, **filter**, **include**en **exclude** , maar die para meters zijn doorgaans alleen gebaseerd op naam. U kunt complexe filtering op basis van andere eigenschappen van items uitvoeren met de cmdlet **where-object** . Met de volgende opdracht worden alle sleutels in HKCU gevonden:\\software die niet meer dan één subsleutel heeft en die ook precies vier waarden heeft:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>Sleutels kopiëren

Kopiëren is voltooid met **copy-item**. De volgende opdracht kopieert HKLM:\\SOFTWARE\\micro soft\\Windows\\CurrentVersion en alle bijbehorende eigenschappen naar HKCU:\\, waarbij een nieuwe sleutel met de naam ' CurrentVersion ' wordt gemaakt:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Als u deze nieuwe sleutel bekijkt in de REGI ster-editor of met behulp van **Get-Child item**, zult u merken dat u geen kopieën van de subsleutels in de nieuwe locatie hebt. Als u de gehele inhoud van een container wilt kopiëren, moet u de para meter **recursief** opgeven. Als u de voor gaande Kopieer opdracht recursief wilt maken, gebruikt u deze opdracht:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

U kunt nog steeds gebruikmaken van andere hulpprogram ma's die u al beschikbaar hebt voor het uitvoeren van bestandssysteem kopieën. Alle register bewerkings Programma's, waaronder reg. exe, regini. exe en Regedit. exe, en COM-objecten die ondersteuning bieden voor het bewerken van registers (zoals WScript. shell en WMI-klasse StdRegProv) kunnen worden gebruikt vanuit Windows Power shell.

## <a name="creating-keys"></a>Sleutels maken

Het maken van nieuwe sleutels in het REGI ster is eenvoudiger dan het maken van een nieuw item in een bestands systeem. Omdat alle register sleutels containers zijn, hoeft u het item type niet op te geven. u hoeft alleen maar een expliciet pad op te geven, zoals:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

U kunt ook een op een provider gebaseerd pad gebruiken om een sleutel op te geven:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

## <a name="deleting-keys"></a>Sleutels verwijderen

Het verwijderen van items is in wezen hetzelfde voor alle providers. Met de volgende opdrachten worden items op de achtergrond verwijderd:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>Verwijderen van alle sleutels onder een bepaalde sleutel

U kunt opgenomen items verwijderen met behulp van **Remove-item**, maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat. Als we bijvoorbeeld proberen de HKCU:\\CurrentVersion-subsleutel te verwijderen, zien we het volgende:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Als u opgenomen items zonder vragen wilt verwijderen, geeft u de para meter **-recursief** op:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Als u alle items in HKCU wilt verwijderen:\\CurrentVersion, maar niet HKCU:\\CurrentVersion zelf, kunt u in plaats daarvan het volgende gebruiken:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
