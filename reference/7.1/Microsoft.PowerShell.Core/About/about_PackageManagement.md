---
description: Package Management is een aggregator voor software pakket beheerders.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 5af3095675015eb043ca3299f5e44b0bc7ac4aa1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252926"
---
# <a name="about-packagemanagement"></a>Over Package Management

## <a name="short-description"></a>KORTE BESCHRIJVING
Package Management is een aggregator voor software pakket beheerders.

## <a name="long-description"></a>LANGE BESCHRIJVING

De functionaliteit van Package Management is geïntroduceerd in Windows Power shell 5,0.

Package Management is een geïntegreerde interface voor beheer systemen voor software pakketten; u kunt Package Management-cmdlets uitvoeren om software ontdekking-, installatie-en inventarisatie taken (SDII) uit te voeren. Ongeacht de onderliggende installatie technologie kunt u de algemene cmdlets uitvoeren in de package management-module om pakketten te zoeken, te installeren of te verwijderen; pakket opslagplaatsen toevoegen, verwijderen en opvragen; en query's uitvoeren op een computer om te bepalen welke software pakketten zijn geïnstalleerd.

Package Management ondersteunt een flexibel invoeg toepassings model dat ondersteuning biedt voor andere software pakket beheer systemen.

De package management-module is opgenomen in Windows Power shell 5,0 en latere releases van Power shell en werkt op drie niveaus van de pakket beheer structuur: pakket providers, pakket bronnen en de pakketten zelf. Laat ons enkele voor waarden definiëren:

- Pakket beheer: software pakketbeheersysteem. In Package Management-voor waarden is dit een pakket provider.
- Pakket provider: Package Management term voor een pakket Manager. Voor beelden hiervan zijn Windows Installer, Choco lade en anderen.
- Pakket Bron: een URL, een lokale map of een gedeelde netwerkmap die u voor het configureren van pakket providers kunt gebruiken als opslag plaats.
- Pakket: een stukje software dat een pakket provider beheert en dat is opgeslagen in een specifieke pakket bron.

De package management-module bevat de volgende cmdlets. Zie de [Package Management](/powershell/module/packagemanagement) -Help voor meer informatie.

- `Get-PackageProvider`: Retourneert een lijst met pakket providers die zijn verbonden met Package Management.
- `Get-PackageSource`: Hiermee wordt een lijst met pakket bronnen opgehaald die zijn geregistreerd voor een pakket provider.
- `Register-PackageSource`: Hiermee voegt u een pakket bron voor een opgegeven pakket provider toe.
- `Set-PackageSource`: Hiermee stelt u eigenschappen in voor een bestaande pakket bron.
- `Unregister-PackageSource`: Hiermee verwijdert u een geregistreerde pakket bron.
- `Get-Package`: Retourneert een lijst met geïnstalleerde software pakketten.
- `Find-Package`: Zoeken naar software pakketten in beschik bare pakket bronnen.
- `Install-Package`: Hiermee worden een of meer software pakketten geïnstalleerd.
- `Save-Package`: Hiermee worden pakketten op de lokale computer opgeslagen zonder dat ze worden geïnstalleerd.
- `Uninstall-Package`: Hiermee verwijdert u een of meer software pakketten.

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a>Boots trap-en dynamische cmdlet-para meters van pakket provider

Package Management wordt standaard geleverd met een kern Boots trap-provider. U kunt aanvullende pakket providers installeren wanneer u deze nodig hebt door de providers te Boots trappen; dat wil zeggen dat er wordt gereageerd op een prompt om de provider automatisch te installeren vanuit een webservice. U kunt een pakket provider met een wille keurige Package Management-cmdlet opgeven. Als de opgegeven provider niet beschikbaar is, wordt u door Package Management gevraagd om de provider te Boots trapen (of automatisch te installeren). Als de chocolade-provider nog niet is geïnstalleerd in de volgende voor beelden, installeert Package Management Boots trap ping de provider.

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

Als de chocolade-provider nog niet is geïnstalleerd, wordt u gevraagd deze te installeren wanneer u de voor gaande opdracht uitvoert.

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

Als de chocolade-provider nog niet is geïnstalleerd, wordt de provider geïnstalleerd wanneer u de voor gaande opdracht uitvoert. maar omdat de para meter ForceBootstrap is toegevoegd aan de opdracht, wordt u niet gevraagd om deze te installeren. zowel de provider als het pakket worden automatisch geïnstalleerd.

Wanneer u een pakket probeert te installeren, als u de ondersteunende provider nog niet hebt geïnstalleerd en u de para meter ForceBootstrap niet aan uw opdracht toevoegt, wordt u door Package Management gevraagd de provider te installeren.

Het opgeven van een pakket provider in de Package Management-opdracht kan dynamische para meters beschikbaar maken die specifiek zijn voor die pakket provider. Wanneer u Get-Help uitvoert voor een specifieke Package Management-cmdlet, wordt een lijst met parameter sets geretourneerd, waarbij dynamische para meters voor beschik bare pakket providers in afzonderlijke parameter sets worden gegroepeerd.

Meer informatie over het package management-project

Voor meer informatie over het package management Open Development project, met inbegrip van het maken van een package management-pakket provider, raadpleegt u het package management-project op GitHub op https://oneget.org .

## <a name="see-also"></a>ZIE OOK

[Get-PackageProvider](xref:PackageManagement.Get-PackageProvider)

[Get-PackageSource](xref:PackageManagement.Get-PackageSource)

[REGI ster-PackageSource](xref:PackageManagement.Register-PackageSource)

[Set-PackageSource](xref:PackageManagement.Set-PackageSource)

[Registratie ongedaan maken-PackageSource](xref:PackageManagement.Unregister-PackageSource)

[Get-Package](xref:PackageManagement.Get-Package)

[Zoeken-pakket](xref:PackageManagement.Find-Package)

[Install-Package](xref:PackageManagement.Install-Package)

[Opslaan-pakket](xref:PackageManagement.Save-Package)

[Uninstall-pakket](xref:PackageManagement.Uninstall-Package)

