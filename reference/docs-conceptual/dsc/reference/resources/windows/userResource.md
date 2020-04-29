---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-gebruikers resource
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941283"
---
# <a name="dsc-user-resource"></a>DSC-gebruikers resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **gebruikers** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van lokale gebruikers accounts op het doel knooppunt.

## <a name="syntax"></a>Syntaxis

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|UserName |Hiermee wordt de account naam aangegeven waarvoor u een specifieke status wilt waarborgen. |
|Beschrijving |Hiermee geeft u de beschrijving op die u wilt gebruiken voor het gebruikers account. |
|Uitgeschakeld |Hiermee wordt aangegeven of het account is ingeschakeld. Stel deze eigenschap in `$true` op om ervoor te zorgen dat dit account is uitgeschakeld en stel `$false` dit in op om ervoor te zorgen dat deze is ingeschakeld. |
|FullName |Hiermee geeft u een teken reeks met de volledige naam die u wilt gebruiken voor het gebruikers account. |
|Wachtwoord |Hiermee geeft u het wacht woord op dat u wilt gebruiken voor dit account. |
|PasswordChangeNotAllowed |Hiermee wordt aangegeven of de gebruiker het wacht woord kan wijzigen. Stel deze eigenschap in `$true` op om ervoor te zorgen dat de gebruiker het wacht woord niet kan wijzigen `$false` en stel in om de gebruiker in staat te stellen het wacht woord te wijzigen. De standaardwaarde is `$false`. |
|PasswordChangeRequired |Hiermee wordt aangegeven of de gebruiker het wacht woord moet wijzigen bij de volgende aanmelding. Stel deze eigenschap in `$true` op als de gebruiker het wacht woord moet wijzigen. De standaardwaarde is `$true`. |
|PasswordNeverExpires |Hiermee wordt aangegeven of het wacht woord verloopt. Stel deze eigenschap in `$true`op om ervoor te zorgen dat het wacht woord voor dit account nooit verloopt. Stel deze waarde `$false` in op als het wacht woord verloopt. De standaardwaarde is `$false`. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt aangegeven of het account bestaat. Stel deze eigenschap in op aanwezig om er zeker van te **zijn** dat het account bestaat en stel het in op **afwezig** om ervoor te zorgen dat het account niet bestaat. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

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