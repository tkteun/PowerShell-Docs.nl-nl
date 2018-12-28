---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met registersleutels werken
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404616"
---
# <a name="working-with-registry-keys"></a>Met registersleutels werken

Omdat registersleutels artikelen op Windows PowerShell-stations zijn, is werken met hen vergelijkbaar met het werken met bestanden en mappen. Een belangrijke verschil is dat elk item in een register op basis van Windows PowerShell-station een container, net als bij een map op een bestandssysteemstation is. Registervermeldingen en de bijbehorende waarden zijn echter eigenschappen van de items, geen afzonderlijke items.

### <a name="listing-all-subkeys-of-a-registry-key"></a>Lijst van alle subsleutels van een registersleutel

U kunt alle items rechtstreeks in een registersleutel weergeven met behulp van **Get-ChildItem**. Voeg de optionele **Force** parameter verborgen weergeven of items van system. Met deze opdracht wordt bijvoorbeeld weergegeven voor items direct in Windows PowerShell-station HKCU:, dat overeenkomt met de registercomponent HKEY_CURRENT_USER:

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

U kunt ook deze registerpad opgeven door op te geven de naam van de registerprovider, gevolgd door '**::**'. De volledige naam van de registerprovider is **Microsoft.PowerShell.Core\\register**, maar dit kan worden ingekort om just **register**. Een van de volgende opdrachten wordt een lijst van de inhoud rechtstreeks onder HKCU:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Deze opdrachten worden alleen de rechtstreeks opgenomen items, net als met behulp van Cmd.exe **DIR** opdracht of **ls** in een UNIX-shell. Als u de opgenomen items weergeven, moet u opgeven de **Recurse** parameter. Als u alle registersleutels in HKCU, gebruik de volgende opdracht uit (deze bewerking kan een extreem lange tijd duren.):

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** kunt uitvoeren van complexe filters gebruiken om mogelijkheden via de **pad**, **Filter**, **opnemen**, en **uitsluiten**parameters, maar deze parameters zijn doorgaans alleen gebaseerd op naam. U kunt uitvoeren met het complex filteren op basis van andere eigenschappen van items met behulp van de **Where-Object** cmdlet. De volgende opdracht worden alle sleutels in HKCU gevonden:\\Software die niet meer dan één subsleutel en beschikt ook over exact vier waarden hebben:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Kopiëren van sleutels

Kopiëren is klaar met **Copy-Item**. De volgende opdracht kopieert HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion en alle bijbehorende eigenschappen aan HKCU:\\, het maken van een nieuwe sleutel met de naam 'CurrentVersion':

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Als u deze nieuwe sleutel in de Register-editor of met behulp van controleert **Get-ChildItem**, zult u merken dat u geen exemplaren van de ingesloten subsleutels in de nieuwe locatie. Als u wilt alle van de inhoud van een container hebt gekopieerd, moet u opgeven de **Recurse** parameter. Als u de voorgaande opdracht recursieve voor kopiëren, gebruikt u deze opdracht:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

U kunt nog steeds andere hulpprogramma's die u al hebt beschikbaar om uit te voeren bestandssysteem kopieën gebruiken. Alle Registerbewerkingsprogramma's, met inbegrip van reg.exe regini.exe en regedit.exe—and COM-objecten die ondersteuning bieden voor bewerken van het register (zoals instantie en de WMI-klasse van StdRegProv) kan worden gebruikt vanuit Windows PowerShell.

### <a name="creating-keys"></a>Het maken van sleutels

Het maken van nieuwe sleutels in het register is eenvoudiger dan het maken van een nieuw item in een bestandssysteem. Omdat alle registersleutels containers zijn, hoeft u niet om op te geven van het itemtype. u simpelweg een expliciete pad, zoals:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

U kunt ook een pad op basis van een provider van een sleutel op te geven:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>Verwijderen van sleutels

Items verwijderen is in wezen hetzelfde voor alle providers. De volgende opdrachten worden de items op de achtergrond verwijderd:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Alle sleutels onder een specifieke sleutel verwijderen

U kunt de opgenomen items verwijderen met behulp van **Remove-Item**, maar u wordt gevraagd om te bevestigen van de verwijzing wordt verwijderd als het item iets anders bevat. Bijvoorbeeld, als we proberen te verwijderen van de HKCU:\\CurrentVersion subsleutel we hebben gemaakt, zien we dit:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Ingesloten om items te verwijderen zonder dat u wordt gevraagd, geeft de **-Recurse** parameter:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Als u wilt verwijderen van alle items in HKCU:\\CurrentVersion, maar niet HKCU:\\CurrentVersion zelf, die u in plaats daarvan kunt gebruiken:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```