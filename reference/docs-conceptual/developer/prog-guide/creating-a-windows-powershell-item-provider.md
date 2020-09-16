---
title: Een Windows Power shell-item provider maken | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.openlocfilehash: b00af7d6fbb75b08027dc18ee6647472d23b83b7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779039"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Een Windows PowerShell-itemprovider maken

In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt waarmee u de gegevens in een gegevens archief kunt bewerken. In dit onderwerp worden de elementen van de gegevens in de Store aangeduid als de "items" van het gegevens archief. Als gevolg hiervan wordt een provider die de gegevens in de Store kan bewerken, een Windows Power shell-item provider genoemd.

> [!NOTE]
> U kunt het C#-bron bestand (AccessDBSampleProvider03.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map. Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.

De Windows Power shell-item provider die in dit onderwerp wordt beschreven, haalt gegevens op uit een Access-Data Base. In dit geval is een ' item ' een tabel in de Access-Data Base of een rij in een tabel.

## <a name="defining-the-windows-powershell-item-provider-class"></a>De klasse van de Windows Power shell-item provider definiëren

Een Windows Power shell-item provider moet een .NET-klasse definiëren die is afgeleid van de basis klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Hier volgt de klassedefinitie voor de item provider die in deze sectie wordt beschreven.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs" range="34-36":::

Houd er rekening mee dat in deze klassedefinitie het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) twee para meters bevat. De eerste para meter geeft u een beschrijvende naam op voor de provider die wordt gebruikt door Windows Power shell. Met de tweede para meter geeft u de specifieke Windows Power shell-mogelijkheden op die de provider beschikbaar maakt voor de Windows Power shell-runtime tijdens het verwerken van opdrachten. Voor deze provider zijn er geen specifieke Windows Power shell-functies toegevoegd.

## <a name="defining-base-functionality"></a>Basis functionaliteit definiëren

Zoals beschreven in het [ontwerp van uw Windows Power shell-provider](./designing-your-windows-powershell-provider.md), is de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) afgeleid van verschillende andere klassen die een andere provider functionaliteit hebben verschaft. Een Windows Power shell-item provider moet daarom alle functionaliteit definiëren die door deze klassen wordt opgegeven.

Zie [een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md)voor meer informatie over het implementeren van functionaliteit voor het toevoegen van sessie-specifieke initialisatie gegevens en voor het vrijgeven van resources die worden gebruikt door de provider.
De meeste providers, met inbegrip van de hier beschreven provider, kunnen echter gebruikmaken van de standaard implementatie van deze functionaliteit van Windows Power shell.

Voordat de Windows Power shell-item provider de items in de Store kan bewerken, moeten de methoden van de basis klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) worden geïmplementeerd om toegang te krijgen tot het gegevens archief. Zie [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md)voor meer informatie over het implementeren van deze klasse.

## <a name="checking-for-path-validity"></a>Geldigheid van pad controleren

Wanneer u op zoek bent naar een gegevens item, verzorgt de Windows Power shell-runtime een Windows Power shell-pad naar de provider, zoals gedefinieerd in de sectie ' PSPath-concepten ' van de werking van [Windows Power shell](/previous-versions/ms714658(v=vs.85)).
Een Windows Power shell-item provider moet de syntaxis en de semantische geldigheid van alle door gegeven paden controleren door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) . Deze methode retourneert `true` of het pad geldig is en `false` anders. Houd er rekening mee dat de implementatie van deze methode het bestaan van het item op het pad niet mag controleren, maar alleen dat het pad syntactisch en correct is.

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) voor deze provider. Houd er rekening mee dat deze implementatie een NormalizePath-hulp methode aanroept om alle scheidings tekens in het pad naar een uniforme te converteren.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs" range="274-298":::

## <a name="determining-if-an-item-exists"></a>Bepalen of een item bestaat

Nadat het pad is geverifieerd, moet de Windows Power shell-runtime bepalen of er een gegevens item op dat pad bestaat. Ter ondersteuning van dit type query implementeert de Windows Power shell-item provider de methode [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) . Deze methode retourneert `true` een item dat is gevonden in het opgegeven pad en `false` (standaard).

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) voor deze provider. Houd er rekening mee dat deze methode de PathIsDrive-, ChunkPath-en getter-helper-methoden aanroept en gebruikmaakt van een door de provider gedefinieerd DatabaseTableInfo-object.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs" range="229-267":::

#### <a name="things-to-remember-about-implementing-itemexists"></a>Wat u moet weten over implementatie van ItemExists

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Bij het definiëren van de provider klasse kan een Windows Power shell-item provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De implementatie van deze methode moet elke vorm van toegang tot het item afhandelen waardoor het item zichtbaar voor de gebruiker kan worden gemaakt. Bijvoorbeeld, als een gebruiker schrijf toegang heeft tot een bestand via de bestandssysteem provider (geleverd door Windows Power shell), maar geen lees toegang, het bestand nog bestaat en [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) wordt geretourneerd `true` . Voor uw implementatie moet mogelijk een bovenliggend item worden gecontroleerd om te zien of het onderliggende item kan worden geïnventariseerd.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Dynamische para meters aan de cmdlet test-Path koppelen

Soms `Test-Path` vereist de cmdlet die [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) aanroept, extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-item provider de methode [System. Management. Automation. provider. Itemcmdletprovider. Itemexistsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) implementeren. Met deze methode worden de dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Test-Path` cmdlet.

Deze Windows Power shell-item provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Een item ophalen

Voor het ophalen van een item moet de provider van Windows Power shell-items [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) overschrijven om aanroepen van de cmdlet te ondersteunen `Get-Item` . Met deze methode schrijft u het item met behulp van de methode [System. Management. Automation. provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) voor deze provider. Houd er rekening mee dat met deze methode de methoden Gette en GetRow worden gebruikt voor het ophalen van items die bestaan uit tabellen in de Access-Data Base of rijen in een gegevens tabel.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs" range="132-163":::

#### <a name="things-to-remember-about-implementing-getitem"></a>Wat u moet weten over implementatie van GetItem

De volgende voor waarden zijn mogelijk van toepassing op een implementatie van [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Bij het definiëren van de provider klasse kan een Windows Power shell-item provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan deze vereisten. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen objecten ophalen die doorgaans verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . De methode [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) voor de File System Provider controleert bijvoorbeeld de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) voordat wordt geprobeerd [System. Management. Automation. provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) aan te roepen voor verborgen of systeem bestanden.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Dynamische para meters aan de Get-item-cmdlet koppelen

Soms `Get-Item` vereist de cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-item provider de methode [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) implementeren. Met deze methode worden de dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Get-Item` cmdlet.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Een item instellen

Voor het instellen van een item moet de provider van Windows Power shell-items de methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) overschrijven om aanroepen van de cmdlet te ondersteunen `Set-Item` . Met deze methode wordt de waarde van het item ingesteld op het opgegeven pad.

Deze provider biedt geen onderdrukking voor de methode  [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) . Het volgende is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Wat u moet weten over implementatie van SetItem

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Bij het definiëren van de provider klasse kan een Windows Power shell-item provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan deze vereisten. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen objecten instellen of schrijven die verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Er moet een fout worden verzonden naar de methode [System. Management. Automation. provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) als het pad een verborgen item en [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false` .

- Uw implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde verifiëren voordat wijzigingen in het gegevens archief worden aangebracht. Deze methode wordt gebruikt om de uitvoering van een bewerking te bevestigen wanneer een wijziging wordt aangebracht in het gegevens archief, bijvoorbeeld het verwijderen van bestanden. De methode [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, met de Windows Power shell-runtime, waarbij rekening wordt gehouden met opdracht regel instellingen of voorkeurs variabelen bij het bepalen van wat er moet worden weer gegeven.

  Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wordt geretourneerd `true` , moet de methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) worden aangeroepen de methode [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Met deze methode wordt een bericht verzonden naar de gebruiker om te controleren of de bewerking moet worden voortgezet. De aanroep van [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) biedt een extra controle op mogelijk schadelijke systeem wijzigingen.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Dynamische para meters ophalen voor SetItem

Soms `Set-Item` vereist de cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-item provider de methode [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) implementeren. Met deze methode worden de dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Set-Item` cmdlet.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Een item wissen

Als u een item wilt wissen, implementeert de provider van Windows Power shell-items de methode [System. Management. Automation. provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) ter ondersteuning van aanroepen van de `Clear-Item` cmdlet. Met deze methode wordt het gegevens item op het opgegeven pad gewist.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Wat u moet weten over implementatie van ClearItem

De volgende voor waarden zijn mogelijk van toepassing op een implementatie van [System. Management. Automation. provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Bij het definiëren van de provider klasse kan een Windows Power shell-item provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van [System. Management. Automation. provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan deze vereisten. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen objecten instellen of schrijven die verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Er moet een fout worden verzonden naar de methode [System. Management. Automation. provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) als het pad een item vertegenwoordigt dat verborgen is voor de gebruiker en [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false` .

- Uw implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde verifiëren voordat wijzigingen in het gegevens archief worden aangebracht. Deze methode wordt gebruikt om de uitvoering van een bewerking te bevestigen wanneer een wijziging wordt aangebracht in het gegevens archief, bijvoorbeeld het verwijderen van bestanden. De methode [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, met de Windows Power shell-runtime en verwerkt alle opdracht regel instellingen of voorkeurs variabelen bij het bepalen van wat er moet worden weer gegeven.

  Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wordt geretourneerd `true` , moet de methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) worden aangeroepen de methode [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Met deze methode wordt een bericht verzonden naar de gebruiker om te controleren of de bewerking moet worden voortgezet. De aanroep van [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) biedt een extra controle op mogelijk schadelijke systeem wijzigingen.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Dynamische para meters ophalen voor ClearItem

Soms `Clear-Item` vereist de cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-item provider de methode [System. Management. Automation. provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) implementeren. Met deze methode worden de dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Clear-Item` cmdlet.

Deze item provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Een standaard actie voor een item uitvoeren

Een Windows Power shell-item provider kan de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) implementeren ter ondersteuning van aanroepen van de `Invoke-Item` cmdlet, waardoor de provider een standaard actie kan uitvoeren voor het item op het opgegeven pad. De File System Provider kan deze methode bijvoorbeeld gebruiken om ShellExecute aan te roepen voor een specifiek item.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Wat u moet weten over implementatie van InvokeDefaultAction

De volgende voor waarden zijn mogelijk van toepassing op een implementatie van [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Bij het definiëren van de provider klasse kan een Windows Power shell-item provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan deze vereisten. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen objecten instellen of schrijven die verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Er moet een fout worden verzonden naar de methode [System. Management. Automation. provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) als het pad een item vertegenwoordigt dat verborgen is voor de gebruiker en [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false` .

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Dynamische para meters ophalen voor InvokeDefaultAction

Soms `Invoke-Item` vereist de cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-item provider de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) implementeren. Met deze methode worden de dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de dynamische para meters toe te voegen aan de `Invoke-Item` cmdlet.

Deze item provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Hulp methoden en klassen implementeren

Deze item provider implementeert diverse hulp methoden en klassen die worden gebruikt door de open bare onderdrukkings methoden die zijn gedefinieerd door Windows Power shell. De code voor deze Help-methoden en-klassen wordt weer gegeven in de sectie voor [beeld van code](#code-sample) .

### <a name="normalizepath-method"></a>Methode NormalizePath

Deze item provider implementeert een NormalizePath-hulp methode om ervoor te zorgen dat het pad een consistente indeling heeft. De opgegeven notatie maakt gebruik van een back slash ( \\ ) als scheidings teken.

### <a name="pathisdrive-method"></a>Methode PathIsDrive

Deze item provider implementeert een PathIsDrive-hulp methode om te bepalen of het opgegeven pad in feite de naam van het station is.

### <a name="chunkpath-method"></a>Methode ChunkPath

Deze item provider implementeert een ChunkPath-hulp methode die het opgegeven pad opsplitst, zodat de provider de afzonderlijke elementen kan identificeren. Er wordt een matrix geretourneerd die bestaat uit de elementen Path.

### <a name="gettable-method"></a>GetTable-methode

Deze item provider implementeert de GetTables-hulp methode die een DatabaseTableInfo-object retourneert dat informatie bevat over de tabel die is opgegeven in de aanroep.

### <a name="getrow-method"></a>Methode GetRow

De methode [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) van deze item provider roept de GetRows-helper-methode aan. Deze helper-methode haalt een DatabaseRowInfo-object op dat informatie bevat over de opgegeven rij in de tabel.

### <a name="databasetableinfo-class"></a>Klasse DatabaseTableInfo

Deze item provider definieert een DatabaseTableInfo-klasse die een verzameling gegevens in een gegevens tabel in de data base vertegenwoordigt. Deze klasse is vergelijkbaar met de klasse [System. io. Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) .

De provider van het voorbeeld item definieert een DatabaseTableInfo. GetTables-methode die een verzameling tabel gegevens objecten retourneert die de tabellen in de data base definiëren. Deze methode bevat een try/catch-blok om ervoor te zorgen dat een database fout wordt weer gegeven als een rij met nul vermeldingen.

### <a name="databaserowinfo-class"></a>Klasse DatabaseRowInfo

Deze item provider definieert de DatabaseRowInfo helper-klasse die een rij in een tabel van de data base vertegenwoordigt. Deze klasse is vergelijkbaar met de klasse [System. io. file info](/dotnet/api/System.IO.FileInfo) .

De voorbeeld provider definieert een DatabaseRowInfo. GetRows-methode voor het retour neren van een verzameling rij-informatie objecten voor de opgegeven tabel. Deze methode bevat een try/catch-blok om uitzonde ringen te onderscheppen. Eventuele fouten leiden tot geen informatie over de rij.

## <a name="code-sample"></a>Code voorbeeld

Zie [AccessDbProviderSample03 code sample](./accessdbprovidersample03-code-sample.md)voor een volledige voorbeeld code.

## <a name="defining-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Wanneer u een provider schrijft, kan het nodig zijn om leden toe te voegen aan bestaande objecten of nieuwe objecten te definiëren. Wanneer u klaar bent, maakt u een bestands typen bestand dat door Windows Power shell kan worden gebruikt om de leden van het object en een indelings bestand te identificeren dat definieert hoe het object wordt weer gegeven. Zie voor meer informatie over het [uitbreiden van object typen en-opmaak](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-windows-powershell-provider"></a>De Windows Power shell-provider bouwen

Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>De Windows Power shell-provider testen

Wanneer deze Windows Power shell-item provider is geregistreerd bij Windows Power shell, kunt u alleen de basis-en schijf functionaliteit van de provider testen. Als u de bewerking van items wilt testen, moet u ook de container functionaliteit implementeren die wordt beschreven in [een container Windows Power shell-provider implementeren](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows Power shell-providers maken](./how-to-create-a-windows-powershell-provider.md)

[Uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)

[Object typen en-opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))

[Hoe Windows Power shell werkt](/previous-versions/ms714658(v=vs.85))

[Een container Windows Power shell-provider maken](./creating-a-windows-powershell-container-provider.md)

[Een Windows Power shell-provider station maken](./creating-a-windows-powershell-drive-provider.md)

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))
