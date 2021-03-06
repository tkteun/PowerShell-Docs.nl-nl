---
ms.date: 09/13/2016
ms.topic: reference
title: Een Windows PowerShell-eigenschapsprovider maken
description: Een Windows PowerShell-eigenschapsprovider maken
ms.openlocfilehash: 5370624afa784598ca784b201f7e7345eb958ff9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390912"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Een Windows PowerShell-eigenschapsprovider maken

In dit onderwerp wordt beschreven hoe u een provider maakt waarmee de gebruiker de eigenschappen van items in een gegevens archief kan bewerken. Als gevolg hiervan wordt dit type provider aangeduid als een Windows Power shell-eigenschaps provider. De register provider van Windows Power shell verwerkt bijvoorbeeld register sleutel waarden als eigenschappen van het register sleutel item. Dit type provider moet de interface [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) toevoegen aan de implementatie van de .net-klasse.

> [!NOTE]
> Windows Power shell biedt een sjabloon bestand dat u kunt gebruiken voor het ontwikkelen van een Windows Power shell-provider. Het TemplateProvider.cs-bestand is beschikbaar op de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade sjabloon is beschikbaar in de **\<PowerShell Samples>** map. U moet een kopie van dit bestand maken en de kopie voor het maken van een nieuwe Windows Power shell-provider gebruiken, waarbij u alle functionaliteit verwijdert die u niet nodig hebt. Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.

> [!CAUTION]
> De methoden van uw eigendoms provider moeten objecten schrijven met behulp van de methode [System. Management. Automation. provider. Cmdletprovider. Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) .

## <a name="defining-the-windows-powershell-provider"></a>De Windows Power shell-provider defini??ren

Een eigenschaps provider moet een .NET-klasse maken die de interface [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) ondersteunt. Hier volgt de standaard klassen declaratie van het TemplateProvider.cs-bestand dat wordt meegeleverd met Windows Power shell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Basis functionaliteit defini??ren

De interface [System. Management. Automation. provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) kan worden gekoppeld aan een van de basis klassen van de provider, met uitzonde ring van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Voeg de basis functionaliteit toe die vereist is voor de basis klasse die u gebruikt. Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over basis klassen.

## <a name="retrieving-properties"></a>Eigenschappen ophalen

Als u eigenschappen wilt ophalen, moet de provider de methode [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) implementeren voor het ondersteunen van aanroepen van de `Get-ItemProperty` cmdlet. Met deze methode worden de eigenschappen opgehaald van het item dat zich op de opgegeven provider bevindt: intern pad (volledig gekwalificeerd).

De `providerSpecificPickList` para meter geeft aan welke eigenschappen moeten worden opgehaald. Als deze para meter `null` of leeg is, moet de methode alle eigenschappen ophalen. Daarnaast schrijft [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) een exemplaar van een [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -object dat een eigenschappen verzameling van de opgehaalde eigenschappen vertegenwoordigt. De methode moet Nothing retour neren.

Het is raadzaam om de implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) ondersteunt de uitbrei ding van namen van eigenschappen voor elk element in de keuze lijst. Gebruik hiervoor de klasse [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) om het Joker teken patroon te vergelijken.

Dit is de standaard implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) van het TemplateProvider.CS-bestand dat wordt meegeleverd met Windows Power shell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Wat u moet weten over de implementatie van GetProperty

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Bij het defini??ren van de provider klasse kan een Windows Power shell-eigenschaps provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen lezer ophalen voor objecten die verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Er moet een fout worden geschreven als het pad een item vertegenwoordigt dat is verborgen voor de gebruiker en [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false` .

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Dynamische para meters aan de Get-ItemProperty-cmdlet koppelen

`Get-ItemProperty`Voor de cmdlet zijn mogelijk aanvullende para meters vereist die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-eigenschaps provider de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) implementeren. De `path` para meter geeft een volledig gekwalificeerde provider (intern pad) aan, terwijl de `providerSpecificPickList` para meter de providerspecifieke eigenschappen specificeert die worden ingevoerd op de opdracht regel. Deze para meter kan `null` of leeg zijn als de eigenschappen worden gepiped naar de cmdlet. In dit geval retourneert deze methode een object met eigenschappen en velden met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de cmdlet.

Dit is de standaard implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) van het TemplateProvider.CS-bestand van Windows Power shell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Eigenschappen instellen

Voor het instellen van eigenschappen moet de Windows Power shell-eigenschaps provider de methode [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) implementeren om aanroepen van de cmdlet te ondersteunen `Set-ItemProperty` . Met deze methode worden een of meer eigenschappen van het item op het opgegeven pad ingesteld en worden de opgegeven eigenschappen als vereist overschreven.
[System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) schrijft ook een exemplaar van een [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -object dat een eigenschappen verzameling van de bijgewerkte eigenschappen vertegenwoordigt.

Dit is de standaard implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) van het TemplateProvider.CS-bestand dat wordt meegeleverd met Windows Power shell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Wat u moet weten over het implementeren van Set-ItemProperty

De volgende voor waarden zijn mogelijk van toepassing op een implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Bij het defini??ren van de provider klasse kan een Windows Power shell-eigenschaps provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen lezer ophalen voor objecten die verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Er moet een fout worden geschreven als het pad een item vertegenwoordigt dat is verborgen voor de gebruiker en [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false` .

- Uw implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde verifi??ren voordat wijzigingen in het gegevens archief worden aangebracht. Deze methode wordt gebruikt om de uitvoering van een bewerking te bevestigen wanneer een wijziging wordt aangebracht in de systeem status, bijvoorbeeld het wijzigen van de naam van bestanden.
  [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, met de Windows Power shell-runtime en het verwerken van opdracht regel instellingen of voorkeurs variabelen bij het bepalen van wat er moet worden weer gegeven.

  Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wordt geretourneerd `true` , moeten de methode System. Management. Automation [. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) worden aangeroepen als er mogelijk gevaarlijke systeem [](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) wijzigingen kunnen worden aangebracht. Met deze methode wordt een bevestigings bericht naar de gebruiker verzonden zodat er extra feedback kan worden gegeven om aan te geven dat de bewerking moet worden voortgezet.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Dynamische para meters voor de cmdlet Set-ItemProperty worden gekoppeld

`Set-ItemProperty`Voor de cmdlet zijn mogelijk aanvullende para meters vereist die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-eigenschaps provider de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) implementeren. Deze methode retourneert een object met eigenschappen en velden met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De `null` waarde kan worden geretourneerd als er geen dynamische para meters moeten worden toegevoegd.

Dit is de standaard implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) van het TemplateProvider.CS-bestand van Windows Power shell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Eigenschappen wissen

Voor het wissen van eigenschappen moet de Windows Power shell-eigenschaps provider de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) implementeren om aanroepen van de cmdlet te ondersteunen `Clear-ItemProperty` . Met deze methode worden een of meer eigenschappen ingesteld voor het item dat zich op het opgegeven pad bevindt.

Dit is de standaard implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) van het TemplateProvider.CS-bestand van Windows Power shell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Denk eraan over het implementeren van ClearProperty

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Bij het defini??ren van de provider klasse kan een Windows Power shell-eigenschaps provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen lezer ophalen voor objecten die verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Er moet een fout worden geschreven als het pad een item vertegenwoordigt dat is verborgen voor de gebruiker en [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false` .

- Uw implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde verifi??ren voordat wijzigingen in het gegevens archief worden aangebracht. Deze methode wordt gebruikt om de uitvoering van een bewerking te bevestigen voordat een wijziging wordt aangebracht in de systeem status, zoals het wissen van inhoud.
  [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, met de Windows Power shell-runtime, waarbij rekening wordt gehouden met alle opdracht regel instellingen of voorkeurs variabelen bij het bepalen van wat er moet worden weer gegeven.

  Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wordt geretourneerd `true` , moeten de methode System. Management. Automation [. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) worden aangeroepen als er mogelijk gevaarlijke systeem [](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) wijzigingen kunnen worden aangebracht. Met deze methode wordt een bevestigings bericht naar de gebruiker verzonden zodat er extra feedback kan worden gegeven om aan te geven dat de potentieel gevaarlijke bewerking moet worden voortgezet.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Dynamische para meters aan de Clear-ItemProperty-cmdlet koppelen

`Clear-ItemProperty`Voor de cmdlet zijn mogelijk aanvullende para meters vereist die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-eigenschaps provider de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) implementeren. Deze methode retourneert een object met eigenschappen en velden met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De `null` waarde kan worden geretourneerd als er geen dynamische para meters moeten worden toegevoegd.

Dit is de standaard implementatie van [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) van het TemplateProvider.CS-bestand van Windows Power shell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>De Windows Power shell-provider bouwen

Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85)).

## <a name="see-also"></a>Zie ook

[Windows Power shell-provider](./designing-your-windows-powershell-provider.md)

[Uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)

[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))
