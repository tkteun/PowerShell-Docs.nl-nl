---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met registersleutels werken
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-keys"></a>Met registersleutels werken

Omdat registersleutels items op Windows PowerShell-stations, lijkt werken met deze erg op werken met bestanden en mappen. Een kritieke verschil is dat elk item op een Windows PowerShell register gebaseerde station een container, net als een map op een bestandssysteemstation. Registervermeldingen en hun gekoppelde waarden zijn echter eigenschappen van de items, geen verschillende items.

### <a name="listing-all-subkeys-of-a-registry-key"></a>Lijst van alle subsleutels van een registersleutel

U kunt alle items rechtstreeks in een registersleutel weergeven met behulp van **Get-ChildItem**. Voeg de optionele **Force** parameter worden verborgen items van system. Met deze opdracht geeft bijvoorbeeld de items rechtstreeks in Windows PowerShell-station HKCU:, dat overeenkomt met het registeronderdeel HKEY_CURRENT_USER:

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

Dit zijn de op het hoogste niveau sleutels zichtbaar onder HKEY_CURRENT_USER in de Register-Editor (Regedit.exe).

U kunt ook dit registerpad opgeven door te geven van de naam van de registerprovider, gevolgd door '**::**'. Volledige naam van de registerprovider **Microsoft.PowerShell.Core\\register**, maar dit kan worden ingekort tot iets **register**. Een van de volgende opdrachten wordt de inhoud rechtstreeks onder HKCU weergeven:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Deze opdrachten alleen de lijst rechtstreeks opgenomen, vergelijkbaar met behulp van Cmd.exe **DIR** opdracht of **ls** in een UNIX-shell. Als de opgenomen items weergeven, moet u opgeven de **Recurse** parameter. Als alle registersleutels in HKCU weergeven, gebruikt u de volgende opdracht (deze bewerking kan een zeer lange tijd duren.):

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** kunt uitvoeren complexe filtermogelijkheden via de **pad**, **Filter**, **opnemen**, en **uitsluiten**parameters, maar deze parameters doorgaans alleen worden gebaseerd op naam. U kunt uitvoeren complexe filteren op basis van andere eigenschappen van items door de **Where-Object** cmdlet. De volgende opdracht worden alle sleutels binnen HKCU gevonden:\\Software die niet meer dan één subsleutels en hebben exact vier waarden hebben:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Kopiëren van sleutels

Kopiëren is klaar met **Copy-Item**. De volgende opdracht kopieert HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion en alle bijbehorende eigenschappen naar HKCU:\\, voor het maken van een nieuwe sleutel met de naam 'CurrentVersion':

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Als u deze nieuwe sleutel in de Register-editor of door onderzoeken **Get-ChildItem**, zult u zien dat er geen kopieën van de subsleutels opgenomen in de nieuwe locatie. Om te kopiëren alle van de inhoud van een container, moet u opgeven de **Recurse** parameter. Als u de voorgaande opdracht recursieve voor kopiëren, gebruikt u deze opdracht:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

U kunt nog andere hulpprogramma's die u hebt al beschikbaar voor het bestandssysteem te kopiëren. Een register bewerkingsopties, met inbegrip van reg.exe regini.exe en regedit.exe—and COM-objecten die ondersteuning bieden voor bewerken (zoals instantie en de WMI-klasse StdRegProv) van het register kan worden gebruikt vanuit Windows PowerShell.

### <a name="creating-keys"></a>Maken van sleutels

Nieuwe sleutels maken in het register is eenvoudiger dan het maken van een nieuw item in een bestandssysteem. Omdat alle registersleutels containers zijn, hoeft u niet het itemtype; opgeven u simpelweg een expliciet pad, zoals:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

U kunt ook een pad op basis van een provider gebruiken een sleutel op te geven:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>Verwijderen van sleutels

Verwijderen van items is in wezen hetzelfde voor alle providers. De volgende opdrachten worden items achtergrond verwijderd:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Alle sleutels onder een specifieke sleutel verwijderen

U kunt opgenomen items verwijderen met behulp van **Item verwijderen**, maar u wordt gevraagd om te bevestigen dat de verwijzing wordt verwijderd als het item iets anders bevat. Bijvoorbeeld, als we probeert te verwijderen van de HKCU:\\CurrentVersion subsleutel wordt gemaakt, zien we dit:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

De opgenomen als items wilt verwijderen zonder dat wordt gevraagd, geeft de **-Recurse** parameter:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Als u wilt verwijderen van alle artikelen in HKCU:\\CurrentVersion maar niet HKCU:\\CurrentVersion zelf, kunt u in plaats daarvan gebruiken:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```