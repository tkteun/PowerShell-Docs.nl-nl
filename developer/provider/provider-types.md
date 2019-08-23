---
title: Provider typen | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 0a9bfe5dd0978ffce66db1b18ef4d82be6c1a7f2
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986654"
---
# <a name="provider-types"></a>Typen providers

Providers definiëren hun basis functionaliteit door te wijzigen hoe de provider-cmdlets, die door Power shell worden meegeleverd, hun acties uitvoeren. Providers kunnen bijvoorbeeld gebruikmaken van de standaard functionaliteit van de `Get-Item` cmdlet of ze kunnen wijzigen hoe die cmdlet werkt bij het ophalen van items uit het gegevens archief. De functionaliteit van de provider die in dit document wordt beschreven, bevat functionaliteit die is gedefinieerd door methoden te overschrijven van specifieke basis klassen en-interfaces van de provider.

> [!NOTE]
> Zie [provider mogelijkheden](/previous-versions//ee126189(v=vs.85))voor Provider functies die vooraf zijn gedefinieerd door Power shell.

## <a name="drive-enabled-providers"></a>Providers met stations

Providers met stations opgeven de standaard stations die beschikbaar zijn voor de gebruiker en kunnen de gebruiker toestaan om stations toe te voegen of te verwijderen. In de meeste gevallen zijn providers providers waarvoor een station is ingeschakeld, omdat er een standaard station nodig is om toegang te krijgen tot het gegevens archief. Wanneer u echter uw eigen provider schrijft, wilt u misschien wel of niet toestaan dat de gebruiker stations kan maken en verwijderen.

Voor het maken van een provider met een station moet uw provider klasse zijn afgeleid van de klasse [System. Management. Automation. provider. DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) of een andere klasse die is afgeleid van deze klasse. De klasse **System. Management. Automation. provider. DriveCmdletProvider** definieert de volgende methoden voor het implementeren van de standaard stations van de provider `New-PSDrive` en `Remove-PSDrive` het ondersteunen van de-en-cmdlets. In de meeste gevallen moet u, ter ondersteuning van een provider-cmdlet, de methode overschrijven die door de Power shell-engine wordt aangeroepen `NewDrive` om de cmdlet `New-PSDrive` aan te roepen, zoals de methode voor de cmdlet, en u kunt `NewDriveDynamicParameters` desgewenst een tweede methode overschrijven, zoals , voor het toevoegen van dynamische para meters aan de cmdlet.

- De methode [System. Management. Automation. provider. DriveCmdletProvider. InitializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) definieert de standaard stations die beschikbaar zijn voor de gebruiker wanneer de provider wordt gebruikt.

- De methoden [System. Management. Automation. provider. DriveCmdletProvider. NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. DriveCmdletProvider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) bepalen hoe uw provider ondersteuning biedt voor de `New-PSDrive`provider-cmdlet. Met deze cmdlet kan de gebruiker stations maken om toegang te krijgen tot het gegevens archief.

- De methode [System. Management. Automation. provider. DriveCmdletProvider. RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) definieert hoe uw provider de `Remove-PSDrive` provider-cmdlet ondersteunt. Met deze cmdlet kan de gebruiker stations uit het gegevens archief verwijderen.

## <a name="item-enabled-providers"></a>Providers waarvoor een item is ingeschakeld

Met item providers kan de gebruiker de items in het gegevens archief ophalen, instellen of wissen. Een ' item ' is een element van het gegevens archief dat de gebruiker onafhankelijk kan openen of beheren. Als u een provider voor item invoer wilt maken, moet uw provider klasse zijn afgeleid van de klasse [System. Management. Automation. provider. ItemCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) of een andere klasse die is afgeleid van deze klasse.

De klasse **System. Management. Automation. provider. ItemCmdletProvider** definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets. In de meeste gevallen moet u, ter ondersteuning van een provider-cmdlet, de methode overschrijven die door de Power shell-engine wordt aangeroepen `ClearItem` om de cmdlet `Clear-Item` aan te roepen, zoals de methode voor de cmdlet, en u kunt `ClearItemDynamicParameters` desgewenst een tweede methode overschrijven, zoals , voor het toevoegen van dynamische para meters aan de cmdlet.

- De methoden [System. Management. Automation. provider. ItemCmdletProvider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) en [System. Management. Automation. provider. ItemCmdletProvider. ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) bepalen hoe uw provider de `Clear-Item`provider-cmdlet. Met deze cmdlet kan de gebruiker de waarde van een item in het gegevens archief verwijderen.

- De methoden [System. Management. Automation. provider. ItemCmdletProvider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [System. Management. Automation. provider. ItemCmdletProvider. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) bepalen hoe uw provider `Get-Item` de provider-cmdlet. Met deze cmdlet kan de gebruiker gegevens ophalen uit het gegevens archief.

- De methoden [System. Management. Automation. provider. ItemCmdletProvider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) en [System. Management. Automation. provider. ItemCmdletProvider. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) bepalen hoe uw provider `Set-Item` de provider-cmdlet. Met deze cmdlet kan de gebruiker de waarden van items in het gegevens archief bijwerken.

- De methoden [System. Management. Automation. provider. Itemcmdletprovider. InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) en [System. Management. Automation. provider. Itemcmdletprovider. InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters) bepalen hoe uw provider ondersteunt de `Invoke-Item` provider-cmdlet. Met deze cmdlet kan de gebruiker de standaard actie uitvoeren die door het item is opgegeven.

- De methoden [System. Management. Automation. provider. ItemCmdletProvider. ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) en [System. Management. Automation. provider. ItemCmdletProvider. ItemExistsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) bepalen hoe uw provider de `Test-Path`provider-cmdlet. Met deze cmdlet kan de gebruiker bepalen of alle elementen van een pad bestaan.

Naast de methoden die worden gebruikt voor het implementeren van provider-cmdlets, worden met de klasse **System. Management. Automation. provider. ItemCmdletProvider** ook de volgende methoden gedefinieerd:

- Met de methode [System. Management. Automation. provider. ItemCmdletProvider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) kan de gebruiker joker tekens gebruiken bij het opgeven van het pad van de provider.

- De [System. Management. Automation. provider. ItemCmdletProvider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) wordt gebruikt om te bepalen of een pad syntactisch en semantisch geldig is voor de provider.

## <a name="container-enabled-providers"></a>Container-providers

Met container-ingeschakelde providers kunnen gebruikers items beheren die containers zijn. Een container is een groep onderliggende items onder een gemeen schappelijk bovenliggend item. Als u een provider wilt maken die als container is ingeschakeld, moet uw provider klasse zijn afgeleid van de klasse [System. Management. Automation. provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) of een andere klasse die is afgeleid van deze klasse.

> [!IMPORTANT]
> Met container ingeschakelde providers hebben geen toegang tot gegevens archieven die geneste containers bevatten. Als een onderliggend item van een container een andere container is, moet u een provider met navigatie functionaliteit implementeren.

De klasse **System. Management. Automation. provider. ContainerCmdletProvider** definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets. In de meeste gevallen moet u, ter ondersteuning van een provider-cmdlet, de methode overschrijven die door de Power shell-engine wordt aangeroepen `CopyItem` om de cmdlet `Copy-Item` aan te roepen, zoals de methode voor de cmdlet, en u kunt `CopyItemDynamicParameters` desgewenst een tweede methode overschrijven, zoals , voor het toevoegen van dynamische para meters aan de cmdlet.

- De methoden [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) en [System. Management. Automation. provider. ContainerCmdletProvider. CopyItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) bepalen hoe uw provider de `Copy-Item` provider-cmdlet. Met deze cmdlet kan de gebruiker een item kopiëren van de ene locatie naar een andere.

- De methoden [System. Management. Automation. provider. ContainerCmdletProvider. GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) en [System. Management. Automation. provider. ContainerCmdletProvider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) bepalen hoe uw provider ondersteunt de `Get-ChildItem` provider-cmdlet. Met deze cmdlet kan de gebruiker de onderliggende items van het bovenliggende item ophalen.

- De methoden [System. Management. Automation. provider. ContainerCmdletProvider. GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) en [System. Management. Automation. provider. ContainerCmdletProvider. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) bepalen hoe uw provider ondersteunt de `Get-ChildItem` provider-cmdlet als `Name` de para meter is opgegeven.

- De methoden [System. Management. Automation. provider. ContainerCmdletProvider. NewItem mag](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) en [System. Management. Automation. provider. ContainerCmdletProvider. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) bepalen hoe uw provider de `New-Item` provider-cmdlet. Met deze cmdlet kan de gebruiker nieuwe items in het gegevens archief maken.

- De methoden [System. Management. Automation. provider. ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) en [System. Management. Automation. provider. ContainerCmdletProvider. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) bepalen hoe uw provider de `Remove-Item` provider-cmdlet. Met deze cmdlet kan de gebruiker items uit het gegevens archief verwijderen.

- De methoden [System. Management. Automation. provider. ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) en [System. Management. Automation. provider. ContainerCmdletProvider. RenameItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) bepalen hoe uw provider de `Rename-Item` provider-cmdlet. Met deze cmdlet kan de gebruiker de naam van items in het gegevens archief wijzigen.

Naast de methoden die worden gebruikt voor het implementeren van provider-cmdlets, worden met de klasse **System. Management. Automation. provider. ContainerCmdletProvider** ook de volgende methoden gedefinieerd:

- De methode [System. Management. Automation. provider. ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) kan worden gebruikt door de provider klasse om te bepalen of een item onderliggende items heeft.

- De methode [System. Management. Automation. provider. ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) kan worden gebruikt door de provider klasse om een nieuw providerspecifieke pad te maken op basis van een opgegeven pad.

## <a name="navigation-enabled-providers"></a>Providers met navigatie mogelijkheden

Met navigatie providers kunnen gebruikers items in het gegevens archief verplaatsen. Als u een provider voor navigatie ingeschakeld wilt maken, moet uw provider klasse zijn afgeleid van de klasse [System. Management. Automation. provider. NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

De klasse **System. Management. Automation. provider. NavigationCmdletProvider** definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets. In de meeste gevallen moet u, ter ondersteuning van een provider-cmdlet, de methode overschrijven die door de Power shell-engine wordt aangeroepen `MoveItem` om de cmdlet `Move-Item` aan te roepen, zoals de methode voor de cmdlet, en u kunt `MoveItemDynamicParameters` desgewenst een tweede methode overschrijven, zoals , voor het toevoegen van dynamische para meters aan de cmdlet.

- De methoden [System. Management. Automation. provider. NavigationCmdletProvider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) en [System. Management. Automation. provider. NavigationCmdletProvider. MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) bepalen hoe uw provider de `Move-Item` provider-cmdlet. Met deze cmdlet kan de gebruiker een item verplaatsen van de ene locatie in de Store naar een andere locatie.

- De methode [System. Management. Automation. provider. NavigationCmdletProvider. MakePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) definieert hoe uw provider de `Join-Path` provider-cmdlet ondersteunt. Met deze cmdlet kan de gebruiker een bovenliggend en onderliggend padsegment combi neren om een provider-intern pad te maken.

Naast de methoden die worden gebruikt voor het implementeren van provider-cmdlets, worden met de klasse **System. Management. Automation. provider. NavigationCmdletProvider** ook de volgende methoden gedefinieerd:

- De methode [System. Management. Automation. provider. NavigationCmdletProvider. GetChildName](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) extraheert de naam van het onderliggende knoop punt van een pad.

- De methode [System. Management. Automation. provider. NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) haalt het bovenliggende deel van een pad op.

- De methode [System. Management. Automation. provider. NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) bepaalt of het item een container item is. In deze context is een container een groep onderliggende items onder een gemeen schappelijk bovenliggend item.

- De methode [System. Management. Automation. provider. NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) retourneert een pad naar een item dat relatief is ten opzichte van een opgegeven basispad.

## <a name="content-enabled-providers"></a>Aanbieders van inhoud

Met providers voor inhouds voorzieningen kan de gebruiker de inhoud van items in een gegevens archief wissen, ophalen of instellen.
Zo kunt u met de File System Provider de inhoud van bestanden in het bestands systeem wissen, ophalen en instellen. Als u een provider voor het inschakelen van inhoud wilt maken, moet uw provider klasse de methoden van de interface [System. Management. Automation. provider. IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) implementeren.

De interface **System. Management. Automation. provider. IContentCmdletProvider** definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets. In de meeste gevallen moet u, ter ondersteuning van een provider-cmdlet, de methode overschrijven die door de Power shell-engine wordt aangeroepen `ClearContent` om de cmdlet `Clear-Content` aan te roepen, zoals de methode voor de cmdlet, en u kunt `ClearContentDynamicParameters` desgewenst een tweede methode overschrijven, zoals , voor het toevoegen van dynamische para meters aan de cmdlet.

- De methoden [System. Management. Automation. provider. IContentCmdletProvider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) en [System. Management. Automation. provider. IContentCmdletProvider. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) bepalen hoe uw provider ondersteunt de `Clear-Content` provider-cmdlet. Met deze cmdlet kan de gebruiker de inhoud van een item verwijderen zonder het item te verwijderen.

- De methoden [System. Management. Automation. provider. IContentCmdletProvider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) en [System. Management. Automation. provider. IContentCmdletProvider. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) bepalen hoe uw provider ondersteunt de `Get-Content` provider-cmdlet. Met deze cmdlet kan de gebruiker de inhoud van een item ophalen. De `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader` methode retourneert de interface [System. Management. Automation. provider. IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader) waarmee de methoden worden gedefinieerd die worden gebruikt om de inhoud te lezen.

- De methoden [System. Management. Automation. provider. IContentCmdletProvider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) en [System. Management. Automation. provider. IContentCmdletProvider. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) bepalen hoe uw provider ondersteunt de `Set-Content` provider-cmdlet. Met deze cmdlet kan de gebruiker de inhoud van een item bijwerken. De `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter` methode retourneert de interface [System. Management. Automation. provider. IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) waarmee de methoden worden gedefinieerd die worden gebruikt om de inhoud te schrijven.

## <a name="property-enabled-providers"></a>Providers met eigenschappen

Met eigenschappen ingeschakelde providers kunnen gebruikers de eigenschappen van de items in het gegevens archief beheren.
Voor het maken van een provider met een eigenschap, moet uw provider klasse de methoden van [System. Management. Automation. provider. IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) en [System. Management. Automation. provider. IDynamicPropertyCmdletProvider implementeren. ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)interfaces. In de meeste gevallen moet u, ter ondersteuning van een provider-cmdlet, de methode overschrijven die door de Power shell-engine wordt aangeroepen `ClearProperty` om de cmdlet aan te roepen, zoals de methode voor de cmdlet Clear-Property, en u kunt `ClearPropertyDynamicParameters` desgewenst een tweede methode overschrijven, zoals , voor het toevoegen van dynamische para meters aan de cmdlet.

De interface **System. Management. Automation. provider. IPropertyCmdletProvider** definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets:

- De methoden [System. Management. Automation. provider. IPropertyCmdletProvider. ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) en [System. Management. Automation. provider. IPropertyCmdletProvider. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) bepalen hoe uw provider ondersteunt de `Clear-ItemProperty` provider-cmdlet. Met deze cmdlet kan de gebruiker de waarde van een eigenschap verwijderen.

- De methoden [System. Management. Automation. provider. IPropertyCmdletProvider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) en [System. Management. Automation. provider. IPropertyCmdletProvider. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) bepalen hoe uw provider ondersteunt de `Get-ItemProperty` provider-cmdlet. Met deze cmdlet kan de gebruiker de eigenschap van een item ophalen.

- De methoden [System. Management. Automation. provider. IPropertyCmdletProvider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) en [System. Management. Automation. provider. IPropertyCmdletProvider. SetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) bepalen hoe uw provider ondersteunt de `Set-ItemProperty` provider-cmdlet. Met deze cmdlet kan de gebruiker de eigenschappen van een item bijwerken.

  De interface **System. Management. Automation. provider. IDynamicPropertyCmdletProvider** definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets:

- De methoden [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) en [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) bepalen hoe uw provider ondersteunt de `Copy-ItemProperty` provider-cmdlet. Met deze cmdlet kan de gebruiker een eigenschap en de waarde ervan kopiëren van de ene locatie naar een andere.

- De methoden [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) en [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) bepalen hoe uw provider ondersteunt de `Move-ItemProperty` provider-cmdlet. Met deze cmdlet kan de gebruiker een eigenschap en de waarde ervan verplaatsen van de ene locatie naar een andere.

- De methoden [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) en [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) bepalen hoe uw provider ondersteunt de `New-ItemProperty` provider-cmdlet. Met deze cmdlet kan de gebruiker een nieuwe eigenschap maken en de waarde ervan instellen.

- De methoden [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) en [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) bepalen hoe uw provider ondersteunt de `Remove-ItemProperty` cmdlet. Met deze cmdlet kan de gebruiker een eigenschap en de waarde ervan verwijderen.

- De methoden [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) en [System. Management. Automation. provider. IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) bepalen hoe uw provider ondersteunt de `Rename-ItemProperty` cmdlet. Met deze cmdlet kan de gebruiker de naam van een eigenschap wijzigen.

## <a name="see-also"></a>Zie ook

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[Een Windows Power shell-provider schrijven](./writing-a-windows-powershell-provider.md)
