---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Hef de registratie van PSRepository
ms.openlocfilehash: 7847e223ae7edd9ec2417d104e5e8130f92a59cf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="unregister-psrepository"></a>Hef de registratie van PSRepository

Heft de registratie van een opslagplaats.

## <a name="description"></a>Beschrijving

De cmdlet Unregister PSRepository heft de registratie van een opslagplaats voor de huidige gebruiker.
- Registratie verwijderen en opnieuw registreren van de opslagplaats PSGallery is toegestaan voor een ondernemings- en scenario's voor de verbinding verbroken.
- Gebruikers kunnen de PSGallery opnieuw registreren door het eenvoudig uitvoeren `Register-PSRepository -Default`
- Aangezien PSGallery is de standaardinstelling opslagplaats publiceren in cmdlets Publish-Module en Publish-Script, is een fout wordt gegenereerd als PSGallery is niet beschikbaar in de lijst met geregistreerde opslagplaats.

## <a name="cmdlet-syntax"></a>De syntaxis van cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Verwijzing naar het online help van cmdlet

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Voorbeeldopdrachten

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>Registratie verwijderen en opnieuw registreren van de opslagplaats PSGallery is toegestaan voor een ondernemings- en scenario's voor de verbinding verbroken.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```