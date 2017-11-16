---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Hef de registratie van PSRepository
ms.openlocfilehash: 91380210f262208fce39d596bd6c2ad05a819fbf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="unregister-psrepository"></a><span data-ttu-id="73020-103">Hef de registratie van PSRepository</span><span class="sxs-lookup"><span data-stu-id="73020-103">Unregister-PSRepository</span></span>

<span data-ttu-id="73020-104">Heft de registratie van een opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="73020-104">Unregisters a repository.</span></span>

## <a name="description"></a><span data-ttu-id="73020-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73020-105">Description</span></span>

<span data-ttu-id="73020-106">De cmdlet Unregister PSRepository heft de registratie van een opslagplaats voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="73020-106">The Unregister-PSRepository cmdlet unregisters a repository for the current user.</span></span>
- <span data-ttu-id="73020-107">Registratie verwijderen en opnieuw registreren van de opslagplaats PSGallery is toegestaan voor een ondernemings- en scenario's voor de verbinding verbroken.</span><span class="sxs-lookup"><span data-stu-id="73020-107">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
- <span data-ttu-id="73020-108">Gebruikers kunnen de PSGallery opnieuw registreren door het eenvoudig uitvoeren`Register-PSRepository -Default`</span><span class="sxs-lookup"><span data-stu-id="73020-108">Users can re-register the PSGallery by simply running `Register-PSRepository -Default`</span></span>
- <span data-ttu-id="73020-109">Aangezien PSGallery is de standaardinstelling opslagplaats publiceren in cmdlets Publish-Module en Publish-Script, is een fout wordt gegenereerd als PSGallery is niet beschikbaar in de lijst met geregistreerde opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="73020-109">Since PSGallery is the default publish repository in Publish-Module and Publish-Script cmdlets, an error will be thrown if PSGallery is not available in the registered repository list.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="73020-110">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="73020-110">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="73020-111">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="73020-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="73020-112">Hef de registratie van PSRepository</span><span class="sxs-lookup"><span data-stu-id="73020-112">Unregister-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a><span data-ttu-id="73020-113">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="73020-113">Example commands</span></span>

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a><span data-ttu-id="73020-114">Registratie verwijderen en opnieuw registreren van de opslagplaats PSGallery is toegestaan voor een ondernemings- en scenario's voor de verbinding verbroken.</span><span class="sxs-lookup"><span data-stu-id="73020-114">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
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

