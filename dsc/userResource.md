---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-gebruikersbron
ms.openlocfilehash: a4e4e8af4fcfe5c997c460613174d8583261dedf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
#<a name="dsc-user-resource"></a>Gebruiker van de DSC-Resource #

 
>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0


De __gebruiker__ in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van lokale gebruikersaccounts in het doelknooppunt.


##<a name="syntax"></a>Syntaxis ##

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
| Beschrijving| Hiermee geeft u de beschrijving die u wilt gebruiken voor het gebruikersaccount.| 
| Disabled| Hiermee wordt aangegeven of het account is ingeschakeld. Deze eigenschap instellen op __$true__ om ervoor te zorgen dat dit account is uitgeschakeld en stel deze in op __$false__ om ervoor te zorgen dat deze is ingeschakeld.| 
| Zorg ervoor dat| Hiermee wordt aangegeven of het account bestaat. Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het account bestaat en stel deze in op 'Ontbreekt' om ervoor te zorgen dat het account niet bestaat.| 
| Volledige naam| Hiermee geeft u een tekenreeks met de volledige naam die u wilt gebruiken voor het gebruikersaccount.| 
| Wachtwoord| Geeft het wachtwoord dat u wilt gebruiken voor dit account. | 
| PasswordChangeNotAllowed| Hiermee wordt aangegeven als de gebruiker het wachtwoord kunt wijzigen. Deze eigenschap instellen op __$true__ om ervoor te zorgen dat de gebruiker kan het wachtwoord wijzigen en stel deze in op __$false__ zodat de gebruiker het wachtwoord te wijzigen. De standaardwaarde is __$false__.| 
| PasswordChangeRequired| Hiermee wordt aangegeven als de gebruiker bij de volgende aanmelding in het wachtwoord moet wijzigen. Deze eigenschap instellen op __$true__ als de gebruiker het wachtwoord moet wijzigen. De standaardwaarde is __$true__.| 
| PasswordNeverExpires| Hiermee wordt aangegeven als het wachtwoord vervalt. Om ervoor te zorgen dat het wachtwoord voor dit account nooit verloopt, deze eigenschap instellen op __$true__, en wordt ingesteld op __$false__ als het wachtwoord verloopt. De standaardwaarde is __$false__.| 
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 

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

