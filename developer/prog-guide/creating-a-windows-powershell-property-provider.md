---
title: Het maken van een Windows PowerShell-eigenschap Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: 4ed15dabffa933dee9becf2f839887eb9108775d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430006"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Een Windows PowerShell-eigenschapsprovider maken

In dit onderwerp wordt beschreven hoe u een provider waarmee de gebruiker voor het bewerken van de eigenschappen van items in een gegevensarchief maken. Als gevolg hiervan, wordt dit type provider aangeduid als een Windows PowerShell-provider voor de eigenschap. Bijvoorbeeld, de registerprovider geleverd door Windows PowerShell-ingangen-registersleutelwaarden als eigenschappen van het register sleutel item. Dit type provider moet toevoegen de [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface voor de implementatie van de .NET-klasse.

> [!NOTE]
> Windows PowerShell biedt een sjabloon voor bestanden die u gebruiken kunt voor het ontwikkelen van een Windows PowerShell-provider. Het bestand TemplateProvider.cs is beschikbaar op de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De gedownloade sjabloon is beschikbaar in de  **\<voorbeelden van PowerShell >** directory. U moet een kopie van dit bestand en de kopie gebruiken voor het maken van een nieuwe Windows PowerShell-provider, alle functionaliteit die u niet hoeft verwijderen.
>
> Zie voor meer informatie over andere Windows PowerShell-provider-implementaties, [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> De methoden van de Eigenschappenprovider moeten schrijven alle objecten met behulp van de [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) methode.

De volgende lijst bevat de secties in dit onderwerp. Als u niet bekend bent met het schrijven van een Windows PowerShell-provider voor de eigenschap, leest u deze informatie in de volgorde waarin deze wordt weergegeven. Echter, als u bekend bent met het schrijven van een Windows PowerShell-provider voor de eigenschap, gaat u rechtstreeks naar de informatie die u nodig hebt.

- [De Windows PowerShell-Provider te definiëren](#Defining-the-Windows-PowerShell-provider)

- [Basisfunctionaliteit definiëren](#Defining-Base-Functionality)

- [Bij het ophalen van eigenschappen](#Retrieving-Properties)

- [Bezig met koppelen van dynamische Parameters voor de `Get-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [Instellingseigenschappen](#Setting-Properties)

- [Bezig met koppelen van dynamische Parameters voor de `Set-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [Een eigenschap wissen](#Clearing-Properties)

- [Bezig met koppelen van dynamische Parameters voor de `Clear-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Het bouwen van de Windows PowerShell-Provider](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>De Windows PowerShell-provider te definiëren

Een Eigenschappenprovider moet maakt u een .NET-klasse die ondersteuning biedt voor de [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface. Hier volgt de declaratie van de klasse standaard uit het bestand TemplateProvider.cs is geleverd door Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Basisfunctionaliteit definiëren

De [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface kan worden gekoppeld aan een van de provider-basisklassen, met uitzondering van de [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse. Toevoegen van de functionaliteit die is vereist voor de basisklasse die u gebruikt. Zie voor meer informatie over basisklassen [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Bij het ophalen van eigenschappen

Om op te halen eigenschappen, de provider moet implementeren de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) methode voor de ondersteuning van aanroepen vanuit de `Get-ItemProperty` cmdlet. Deze methode worden de eigenschappen van het item dat zich bevindt in de opgegeven provider interne pad (volledig gekwalificeerde) opgehaald.

De `providerSpecificPickList` parameter geeft aan welke eigenschappen om op te halen. Als deze parameter `null` of leeg is, wordt de methode moet alle eigenschappen ophalen. Bovendien [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) schrijft u een exemplaar van een [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) -object met een de eigenschappenverzameling van de eigenschappen opgehaald. De methode moet er niets worden geretourneerd.

Het wordt aanbevolen dat de implementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) biedt ondersteuning voor de jokerteken-uitbreiding van de namen van eigenschappen voor elk element in de selectielijst. U doet dit door gebruik van de [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) klasse om uit te voeren de jokertekens.

Hier volgt de standaardimplementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) uit het bestand TemplateProvider.cs is geleverd door Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Om te onthouden over het implementeren van GetProperty

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Bij het definiëren van de providerklasse, een Windows PowerShell-provider voor de eigenschap provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) methode vereist om ervoor te zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet ophalen van een lezer voor objecten die door de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Een fout moet worden geschreven als het pad staat voor een item dat is verborgen voor de gebruiker en [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Get-ItemProperty

De `Get-ItemProperty` cmdlet mogelijk extra parameters die dynamisch zijn opgegeven tijdens runtime. Voor deze dynamische parameters, de Windows PowerShell-provider voor de eigenschap moet worden geïmplementeerd de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) methode. De `path` parameter geeft aan dat een volledig gekwalificeerde provider interne pad, terwijl de `providerSpecificPickList` parameter geeft u de provider-specifieke eigenschappen ingevoerd op de opdrachtregel. Deze parameter mogelijk `null` of leeg zijn als de eigenschappen worden doorgesluisd naar de cmdlet. In dit geval wordt deze methode retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object de parameters toevoegen aan de cmdlet.

Hier volgt de standaardimplementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) uit het bestand TemplateProvider.cs is geleverd door Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Instellingseigenschappen

Als u wilt instellen, de Windows PowerShell-provider voor de eigenschap moet worden geïmplementeerd de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) methode voor de ondersteuning van aanroepen vanuit de `Set-ItemProperty` cmdlet. Deze methode Hiermee stelt u een of meer eigenschappen van het item in het opgegeven pad, en zo nodig de opgegeven eigenschappen worden overschreven. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) ook schrijft een exemplaar van een [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) -object met een eigenschappenverzameling van de bijgewerkte de eigenschappen.

Hier volgt de standaardimplementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) uit het bestand TemplateProvider.cs is geleverd door Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Om te onthouden over het implementeren van Set-ItemProperty

De volgende voorwaarden mogelijk van toepassing op een implementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Bij het definiëren van de providerklasse, een Windows PowerShell-provider voor de eigenschap provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) methode moet ervoor zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet ophalen van een lezer voor objecten die door de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Een fout moet worden geschreven als het pad staat voor een item dat is verborgen voor de gebruiker en [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false`.

- De implementatie van de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) en controleer of de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Deze methode wordt gebruikt om te bevestigen van de uitvoering van een bewerking wanneer een wijziging wordt aangebracht in de systeemstatus, bijvoorbeeld bestandsnamen. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource moet worden gewijzigd voor de gebruiker, met de Windows PowerShell-runtime en verwerking opdrachtregel instellingen of voorkeursvariabelen in bepalen wat moet worden weergegeven.

  Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`als kunnen mogelijk schadelijke system wijzigingen worden aangebracht, de [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode. Deze methode verzendt een bevestigingsbericht wordt weergegeven aan de gebruiker om toe te staan aanvullende feedback om aan te geven dat de bewerking moet worden voortgezet.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Dynamische Parameters koppelen voor de Cmdlet Set-ItemProperty

De `Set-ItemProperty` cmdlet mogelijk extra parameters die dynamisch zijn opgegeven tijdens runtime. Voor deze dynamische parameters, de Windows PowerShell-provider voor de eigenschap moet worden geïmplementeerd de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) methode. Deze methode retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De `null` waarde kan worden geretourneerd als er geen dynamische parameters moeten worden toegevoegd.

Hier volgt de standaardimplementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) uit het bestand TemplateProvider.cs is geleverd door Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Wissen van eigenschappen

Als u wilt wissen eigenschappen, de Windows PowerShell-provider voor de eigenschap moet worden geïmplementeerd de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) methode voor de ondersteuning van aanroepen vanuit de `Clear-ItemProperty` cmdlet. Deze methode stelt een of meer eigenschappen voor het item dat zich bevindt in het opgegeven pad.

Hier volgt de standaardimplementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) uit het bestand TemplateProvider.cs is geleverd door Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Dingen om te weten over het implementeren van ClearProperty

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Bij het definiëren van de providerklasse, een Windows PowerShell-provider voor de eigenschap provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) methode vereist om ervoor te zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet ophalen van een lezer voor objecten die door de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Een fout moet worden geschreven als het pad staat voor een item dat is verborgen voor de gebruiker en [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false`.

- De implementatie van de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) en controleer of de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Deze methode wordt gebruikt om de uitvoering van een bewerking te bevestigen voordat een wijziging wordt aangebracht in de systeemstatus, zoals het wissen van inhoud. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource moet worden gewijzigd voor de gebruiker met de Windows PowerShell-runtime rekening houdend met instellingen vanaf de opdrachtregel of voorkeursvariabelen in bepalen wat moet worden weergegeven.

  Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`als kunnen mogelijk schadelijke system wijzigingen worden aangebracht, de [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode. Deze methode verzendt een bevestigingsbericht wordt weergegeven aan de gebruiker om toe te staan aanvullende feedback om aan te geven dat de schadelijke werking moet worden voortgezet.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet wissen ItemProperty

De `Clear-ItemProperty` cmdlet mogelijk extra parameters die dynamisch zijn opgegeven tijdens runtime. Voor deze dynamische parameters, de Windows PowerShell-provider voor de eigenschap moet worden geïmplementeerd de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) methode. Deze methode retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De `null` waarde kan worden geretourneerd als er geen dynamische parameters moeten worden toegevoegd.

Hier volgt de standaardimplementatie van [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) uit het bestand TemplateProvider.cs is geleverd door Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Het bouwen van de Windows PowerShell-provider

Zie [over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Zie ook

[Windows PowerShell-provider](./designing-your-windows-powershell-provider.md)

[Ontwerp uw Windows PowerShell-provider](./designing-your-windows-powershell-provider.md)

[Objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)