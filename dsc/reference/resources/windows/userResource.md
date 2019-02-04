---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Gebruiker van de DSC-Resource
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687501"
---
# <a name="dsc-user-resource"></a>Gebruiker van de DSC-Resource

Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **gebruiker** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van lokale gebruikersaccounts op het doelknooppunt.

## <a name="syntax"></a>Syntaxis

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| UserName| Geeft de accountnaam waarvan u wilt om te controleren of een specifieke status.|
| Beschrijving| Geeft aan dat de beschrijving die u wilt gebruiken voor het gebruikersaccount.|
| Uitgeschakeld| Geeft aan of het account is ingeschakeld. Deze eigenschap instellen op `$true` om ervoor te zorgen dat dit account is uitgeschakeld, en stel deze in op `$false` om ervoor te zorgen dat deze is ingeschakeld.|
| Zorg ervoor dat| Geeft aan of het account bestaat. Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het account bestaat en stel deze in op 'Ontbreekt' om ervoor te zorgen dat het account niet bestaat.|
| FullName| Hiermee geeft u een tekenreeks zijn met de volledige naam die u wilt gebruiken voor het gebruikersaccount.|
| Wachtwoord| Geeft het wachtwoord die u wilt gebruiken voor dit account. |
| PasswordChangeNotAllowed| Hiermee wordt aangegeven als de gebruiker het wachtwoord kunt wijzigen. Deze eigenschap instellen op `$true` om ervoor te zorgen dat de gebruiker kan niet het wachtwoord wijzigen en stel deze in op `$false` zodat de gebruiker het wachtwoord te wijzigen. De standaardwaarde is `$false`.|
| PasswordChangeRequired| Hiermee wordt aangegeven als de gebruiker het wachtwoord bij de volgende aanmelding moet wijzigen. Deze eigenschap instellen op `$true` als de gebruiker het wachtwoord moet wijzigen. De standaardwaarde is `$true`.|
| PasswordNeverExpires| Hiermee wordt aangegeven als het wachtwoord verloopt. Om ervoor te zorgen dat het wachtwoord voor dit account nooit verloopt, deze eigenschap instellen op `$true`, en stel deze in op `$false` als het wachtwoord verloopt. De standaardwaarde is `$false`.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```