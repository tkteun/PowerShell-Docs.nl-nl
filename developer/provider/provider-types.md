---
title: Providertypen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 25b604621c90f1aa88bc1eea365e47db66e98c3d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848494"
---
# <a name="provider-types"></a>Typen providers

De basisfunctionaliteit definiëren providers door te wijzigen hoe de provider-cmdlets (geleverd door Windows PowerShell) hun acties uitvoeren. Providers kunt bijvoorbeeld de standaardfunctionaliteit van de `Get-Item` cmdlet, of dat ze kunnen wijzigen hoe deze cmdlet werkt bij het ophalen van items uit het gegevensarchief. De provider-functionaliteit die worden beschreven in dit onderwerp bevat functionaliteit die is gedefinieerd door de methoden van specifieke provider basisklassen en interfaces worden overschreven.

> [!NOTE]
> Zie voor de functies van resourceproviders die vooraf zijn gedefinieerd door de Windows PowerShell, [Provider mogelijkheden](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6).

## <a name="drive-enabled-providers"></a>Station ingeschakelde Providers

Station ingeschakelde providers opgeven van de stations standaard beschikbaar voor de gebruiker en toestaan dat de gebruiker toevoegen of verwijderen van schijven. In de meeste gevallen zijn providers station ingeschakelde providers omdat deze vereisen sommige standaardstation dat voor toegang tot het gegevensarchief. Echter bij het schrijven van uw eigen provider u mogelijk of mogelijk niet wilt toestaan dat de gebruiker maken en verwijderen van schijven.

Voor het maken van een station ingeschakeld-provider, klasse in uw provider moet zijn afgeleid van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse of een andere klasse die is afgeleid van die klasse. De [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse definieert de volgende methoden voor het implementeren van de standaard-stations van de provider en de ondersteunende de `New-PSDrive` en `Remove-PSDrive` cmdlets. Ter ondersteuning van een cmdlet provider in de meeste gevallen moet u de methode die de Windows PowerShell-engine roept de cmdlet, zoals aanroepen overschrijven de `NewDrive` methode voor het `New-PSDrive` cmdlet, en (optioneel) u kunt een tweede methode, zoals overschrijven`NewDriveDynamicParameters`, voor dynamische parameters toe te voegen aan de cmdlet.

- De [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) methode definieert u de standaard-stations die beschikbaar voor de gebruiker zijn wanneer de provider wordt gebruikt.

- De [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) methoden bepaalt hoe de provider ondersteunt de `New-PSDrive` provider-cmdlet. Deze cmdlet kan de gebruiker te maken van stations voor toegang tot het gegevensarchief.

- De [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode definieert hoe de provider ondersteunt de `Remove-PSDrive` provider-cmdlet. Deze cmdlet kan de gebruiker schijven verwijderen uit het gegevensarchief.

## <a name="item-enabled-providers"></a>Item ingeschakelde Providers

Item ingeschakelde providers toestaan dat de gebruiker ophalen, instellen of wissen van de items in het gegevensarchief. Een 'item' is een element van het gegevensarchief dat de gebruiker toegang tot of afzonderlijk beheren. Voor het maken van een item ingeschakeld-provider, klasse in uw provider moet zijn afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse of een andere klasse die is afgeleid van die klasse.

De [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets. Ter ondersteuning van een cmdlet provider in de meeste gevallen moet u de methode die de Windows PowerShell-engine roept de cmdlet, zoals aanroepen overschrijven de `ClearItem` methode voor het `Clear-Item` cmdlet, en (optioneel) u kunt een tweede methode, zoals overschrijven`ClearItemDynamicParameters`, voor dynamische parameters toe te voegen aan de cmdlet.

- De [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) en [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Clear-Item` provider-cmdlet. Deze cmdlet kan de gebruiker te verwijderen van de waarde van een item in het gegevensarchief.

- De [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) methoden definiëren hoe uw provider ondersteunt de `Get-Item` provider-cmdlet. Deze cmdlet kan de gebruiker voor het ophalen van gegevens uit het gegevensarchief.

- De [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) en [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) methoden definiëren hoe uw provider ondersteunt de `Set-Item` provider-cmdlet. Deze cmdlet kan de gebruiker om bij te werken van de waarden van items in het gegevensarchief.

- De [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) en [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) methoden definiëren hoe de provider ondersteunt de `Invoke-Item` provider-cmdlet. Deze cmdlet kan de gebruiker om uit te voeren van de standaardactie die is opgegeven door het item.

- De [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) en [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Test-Path` provider-cmdlet. Deze cmdlet kan de gebruiker om te bepalen of alle elementen van een pad bestaan.

  Naast de methoden voor het implementeren van de provider-cmdlets, de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse definieert ook de volgende methoden:

- De [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath) methode kan de gebruiker jokertekens gebruiken bij het opgeven van het pad naar de provider.

- De [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) wordt gebruikt om te bepalen of een pad syntactisch en semantisch ongeldig is voor de provider.

## <a name="container-enabled-providers"></a>Container ingeschakelde Providers

Container ingeschakelde providers toestaan dat de gebruiker voor het beheren van items die containers zijn. Een container is een groep van onderliggende items onder een gemeenschappelijk bovenliggend item. Voor het maken van een provider container is ingeschakeld, moet uw providerklasse zijn afgeleid van de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse of een andere klasse die is afgeleid van die klasse.

> [!IMPORTANT]
> Container ingeschakelde providers geen toegang tot gegevensarchieven die geneste containers bevatten. Als een onderliggend item van een container een andere container is, moet u een provider navigatie-functionaliteit implementeren.

De [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets. Ter ondersteuning van een cmdlet provider in de meeste gevallen moet u de methode die de Windows PowerShell-engine roept de cmdlet, zoals aanroepen overschrijven de `CopyItem` methode voor het `Copy-Item` cmdlet, en (optioneel) u kunt een tweede methode, zoals overschrijven`CopyItemDynamicParameters`, voor dynamische parameters toe te voegen aan de cmdlet.

- De [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) en [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Copy-Item` provider-cmdlet. Deze cmdlet kan de gebruiker een item te kopiëren van de ene locatie naar een andere.

- De [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) en [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Get-ChildItem` provider-cmdlet. Deze cmdlet kan de gebruiker om op te halen van de onderliggende items van het bovenliggende item.

- De [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) en [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Get-ChildItem` cmdlet provider als de `Name` parameter is opgegeven.

- De [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) en [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) methoden definiëren hoe de provider ondersteunt de `New-Item` provider-cmdlet. Deze cmdlet kan de gebruiker te maken van nieuwe items in het gegevensarchief.

- De [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) en [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Remove-Item` provider-cmdlet. Deze cmdlet kan de gebruiker om items te verwijderen uit het gegevensarchief.

- De [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) en [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Rename-Item` provider-cmdlet. Deze cmdlet kan de gebruiker om te wijzigen van items in het gegevensarchief.

  Naast de methoden voor het implementeren van de provider-cmdlets, de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse definieert ook de volgende methoden:

- De [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) methode kan worden gebruikt door de providerklasse om te bepalen of een item onderliggende items heeft.

- De [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) methode kan worden gebruikt door de providerklasse te maken van een nieuwe provider-specifieke pad van een opgegeven pad.

## <a name="navigation-enabled-providers"></a>Navigatie ingeschakelde Providers

Navigatie ingeschakelde providers toestaan dat de gebruiker om items te verplaatsen in het gegevensarchief. Voor het maken van een provider navigatie is ingeschakeld, moet uw providerklasse zijn afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse.

De [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets. Ter ondersteuning van een cmdlet provider in de meeste gevallen moet u de methode die de Windows PowerShell-engine roept de cmdlet, zoals aanroepen overschrijven de `MoveItem` methode voor het `Move-Item` cmdlet, en (optioneel) u kunt een tweede methode, zoals overschrijven`MoveItemDynamicParameters`, voor dynamische parameters toe te voegen aan de cmdlet.

- De [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) en [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Move-Item` provider-cmdlet. Deze cmdlet kan de gebruiker een item van de ene locatie in de store te verplaatsen naar een andere locatie.

- De [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) methode definieert hoe de provider ondersteunt de `Join-Path` provider-cmdlet. Deze cmdlet kan de gebruiker een bovenliggende en onderliggende padsegment voor het maken van een provider interne pad combineren.

  Naast de methoden voor het implementeren van de provider-cmdlets, de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse definieert ook de volgende methoden:

- De [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) methode haalt de naam van het onderliggende knooppunt van een pad.

- De [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) methode haalt het bovenliggende onderdeel van een pad.

- De [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) methode bepaalt of het item een container-item is. In deze context is een container in een groep van onderliggende items onder een gemeenschappelijk bovenliggend item.

- De [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) methode retourneert een pad naar een item dat is ten opzichte van een opgegeven basispad.

## <a name="content-enabled-providers"></a>Providers van inhoud ingeschakeld

Inhoud ingeschakelde providers toestaan dat de gebruiker om te wissen, ophalen of instellen van de inhoud van items in een gegevensarchief. Bijvoorbeeld, kunt de provider bestandssysteem u om te wissen, ophalen en instellen van de inhoud van bestanden in het bestandssysteem. Voor het maken van een provider van inhoud ingeschakeld, moet uw providerklasse de methoden voor het implementeren. de [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

De [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets. Ter ondersteuning van een cmdlet provider in de meeste gevallen moet u de methode die de Windows PowerShell-engine roept de cmdlet, zoals aanroepen overschrijven de `ClearContent` methode voor het `Clear-Content` cmdlet, en (optioneel) u kunt een tweede methode, zoals overschrijven`ClearContentDynamicParameters`, voor dynamische parameters toe te voegen aan de cmdlet.

- De [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) en [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)methoden definiëren hoe de provider ondersteunt de `Clear-Content` provider-cmdlet. Deze cmdlet kan de gebruiker de inhoud van een item verwijderen zonder te verwijderen van het item.

- De [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) en [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Get-Content` provider-cmdlet. Deze cmdlet kan de gebruiker om op te halen van de inhoud van een item. De [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) methode retourneert een [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interface waarmee wordt gedefinieerd de methoden die worden gebruikt om de inhoud te lezen.

- De [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) en [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Set-Content` provider-cmdlet. Deze cmdlet kan de gebruiker de inhoud van een item bijwerken. De [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) methode retourneert een [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interface waarmee wordt gedefinieerd de methoden die wordt gebruikt voor het schrijven van de inhoud.

## <a name="property-enabled-providers"></a>De eigenschap ingeschakelde Providers

De eigenschap ingeschakelde providers toestaan dat de gebruiker voor het beheren van de eigenschappen van de items in het gegevensarchief. Voor het maken van een provider voor de eigenschap is ingeschakeld, moet uw providerklasse de methoden voor het implementeren. de [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interfaces. Ter ondersteuning van een cmdlet provider in de meeste gevallen moet u de methode die de Windows PowerShell-engine roept de cmdlet, zoals aanroepen overschrijven de `ClearProperty` methode voor de cmdlet Clear-eigenschap, en (optioneel) u kunt een tweede methode, zoals overschrijven`ClearPropertyDynamicParameters`, voor dynamische parameters toe te voegen aan de cmdlet.

De [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets:

- De [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) en [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Clear-ItemProperty` provider-cmdlet. Deze cmdlet kan de gebruiker om de waarde van een eigenschap te verwijderen.

- De [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) en [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)methoden definiëren hoe de provider ondersteunt de `Get-ItemProperty` provider-cmdlet. Deze cmdlet kan de gebruiker om op te halen van de eigenschap van een item.

- De [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) en [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)methoden definiëren hoe de provider ondersteunt de `Set-ItemProperty` provider-cmdlet. Deze cmdlet kan de gebruiker om de eigenschappen van een item te werken.

  De [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interface definieert de volgende methoden voor het implementeren van specifieke provider-cmdlets:

- De [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Copy-ItemProperty` provider-cmdlet. Deze cmdlet kan de gebruiker naar een eigenschap en de waarde van de ene locatie naar de andere kopiëren.

- De [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Move-ItemProperty` provider-cmdlet. Deze cmdlet kan de gebruiker een eigenschap en de waarde van de ene locatie verplaatsen naar een andere.

- De [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) methoden definiëren hoe de provider ondersteunt de `New-ItemProperty` provider-cmdlet. Deze cmdlet kan de gebruiker te maken van een nieuwe eigenschap en stel de waarde.

- De [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Remove-ItemProperty` cmdlet. Deze cmdlet kan de gebruiker te verwijderen van een eigenschap en de waarde ervan.

- De [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) methoden definiëren hoe de provider ondersteunt de `Rename-ItemProperty` cmdlet. Deze cmdlet kan de gebruiker de naam van een eigenschap te wijzigen.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)