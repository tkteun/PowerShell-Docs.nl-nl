---
title: Een Windows PowerShell-inhoudsprovider maken
ms.date: 09/13/2016
ms.openlocfilehash: b4bc0c8d1f8ef9f85bd711fdc2770b54418bbf4a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779062"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Een Windows PowerShell-inhoudsprovider maken

In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt waarmee de gebruiker de inhoud van de items in een gegevens archief kan bewerken. Als gevolg hiervan wordt een provider die de inhoud van items kan bewerken, een Windows Power shell-inhouds provider genoemd.

> [!NOTE]
> U kunt het C#-bron bestand (AccessDBSampleProvider06.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map. Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.

## <a name="define-the-windows-powershell-content-provider-class"></a>De Windows Power shell-inhouds provider klasse definiëren

Een Windows Power shell-inhouds provider moet een .NET-klasse maken die ondersteuning biedt voor de interface [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) . Hier volgt de klassedefinitie voor de item provider die in deze sectie wordt beschreven.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="32-33":::

Houd er rekening mee dat in deze klassedefinitie het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) twee para meters bevat. De eerste para meter geeft u een beschrijvende naam op voor de provider die wordt gebruikt door Windows Power shell. Met de tweede para meter geeft u de specifieke Windows Power shell-mogelijkheden op die de provider beschikbaar maakt voor de Windows Power shell-runtime tijdens het verwerken van opdrachten. Voor deze provider zijn er geen specifieke Windows Power shell-functies toegevoegd.

## <a name="define-functionality-of-base-class"></a>Functionaliteit van basis klasse definiëren

Zoals beschreven in het [ontwerp van uw Windows Power shell-provider](./designing-your-windows-powershell-provider.md), is de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) afgeleid van verschillende andere klassen die een andere provider functionaliteit hebben verschaft. Een Windows Power shell-inhouds provider definieert daarom doorgaans alle functionaliteiten die door deze klassen worden verschaft.

Zie [een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md)voor meer informatie over het implementeren van functionaliteit voor het toevoegen van sessie-specifieke initialisatie gegevens en voor het vrijgeven van resources die worden gebruikt door de provider.
De meeste providers, met inbegrip van de hier beschreven provider, kunnen echter gebruikmaken van de standaard implementatie van deze functionaliteit van Windows Power shell.

Voor toegang tot het gegevens archief moet de provider de methoden van de basis klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) implementeren. Zie [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md)voor meer informatie over het implementeren van deze methoden.

Voor het bewerken van de items van een gegevens archief, zoals het ophalen, instellen en wissen van items, moet de provider de methoden implementeren die worden verschaft door de basis klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Zie [een Windows Power shell-item provider maken](./creating-a-windows-powershell-item-provider.md)voor meer informatie over het implementeren van deze methoden.

Voor het werken met gegevens archieven met meerdere lagen moet de provider de methoden implementeren die worden verschaft door de basis klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Zie [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md)voor meer informatie over het implementeren van deze methoden.

Voor ondersteuning van recursieve opdrachten, geneste containers en relatieve paden moet de provider de basis klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implementeren. Deze Windows Power shell-inhouds provider kan bovendien de interface [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) koppelen aan de basis klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) en moet daarom de methoden implementeren die door deze klasse worden verschaft. Zie de implementatie van deze methoden voor meer informatie. Zie [een navigatie van een Windows Power shell-provider implementeren](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Een inhouds lezer implementeren

Voor het lezen van inhoud van een item moet een provider een inhouds lezer-klasse implementeren die is afgeleid van [System. Management. Automation. provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).
De inhouds lezer voor deze provider biedt toegang tot de inhoud van een rij in een gegevens tabel. De klasse inhouds lezer definieert een **Lees** methode voor het ophalen van gegevens uit de aangegeven rij en retourneert een lijst die die gegevens vertegenwoordigt, een **Zoek** methode waarmee de inhouds lezer wordt verplaatst, een **Close** -methode die de inhouds lezer sluit en een **afstoten** methode heeft.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="2115-2241":::

## <a name="implementing-a-content-writer"></a>Een inhouds schrijver implementeren

Als u inhoud naar een item wilt schrijven, moet een provider een klasse Content Writer implementeren die is afgeleid van [System. Management. Automation. provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).
De klasse Content Writer definieert een **Schrijf** methode voor het schrijven van de opgegeven rij-inhoud, een **Zoek** methode waarmee de schrijver van de inhoud wordt verplaatst, een **Close** **-methode die** de schrijver van de inhoud sluit en een verwerkings methode.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="2250-2394":::

## <a name="retrieving-the-content-reader"></a>De inhouds lezer wordt opgehaald

Als u inhoud van een item wilt ophalen, moet de provider [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) implementeren ter ondersteuning van de `Get-Content` cmdlet. Deze methode retourneert de inhouds lezer voor het item dat zich op het opgegeven pad bevindt. Het lezerobject kan vervolgens worden geopend om de inhoud te lezen.

Hier volgt de implementatie van [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) voor deze methode voor deze provider.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1829-1846":::

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Wat u moet weten over implementatie van GetContentReader

De volgende voor waarden zijn mogelijk van toepassing op een implementatie van [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Bij het definiëren van de provider klasse kan een Windows Power shell-inhouds provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen lezer ophalen voor objecten die verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Er moet een fout worden geschreven als het pad een item vertegenwoordigt dat is verborgen voor de gebruiker en [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false` .

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Dynamische para meters aan de cmdlet Get-Content koppelen

`Get-Content`Voor de cmdlet zijn mogelijk aanvullende para meters vereist die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-inhouds provider de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) implementeren. Met deze methode worden dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de cmdlet.

Deze methode wordt niet door deze Windows Power shell-container provider geïmplementeerd. De volgende code is echter de standaard implementatie van deze methode.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1853-1856":::

## <a name="retrieving-the-content-writer"></a>De inhouds schrijver wordt opgehaald

Als u inhoud naar een item wilt schrijven, moet de provider [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) implementeren om `Set-Content` de `Add-Content` cmdlets en te ondersteunen. Deze methode retourneert de schrijver van inhoud voor het item dat zich op het opgegeven pad bevindt.

Hier volgt de implementatie van [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) voor deze methode.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1863-1880":::

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Wat u moet weten over implementatie van GetContentWriter

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Bij het definiëren van de provider klasse kan een Windows Power shell-inhouds provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen schrijver ophalen voor objecten die verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Er moet een fout worden geschreven als het pad een item vertegenwoordigt dat is verborgen voor de gebruiker en [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false` .

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Dynamische para meters koppelen aan de cmdlets Add-content en set-content

Voor `Add-Content` de `Set-Content` cmdlets en zijn mogelijk extra dynamische para meters vereist die een runtime toevoegen. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-inhouds provider de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) implementeren om deze para meters af te handelen. Met deze methode worden dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de cmdlets.

Deze methode wordt niet door deze Windows Power shell-container provider geïmplementeerd. De volgende code is echter de standaard implementatie van deze methode.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1887-1890":::

## <a name="clearing-content"></a>Inhoud wissen

Uw inhouds provider implementeert de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) ter ondersteuning van de `Clear-Content` cmdlet. Met deze methode wordt de inhoud van het item op het opgegeven pad verwijderd, maar blijft het item intact.

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) voor deze provider.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1775-1812":::

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Wat u moet weten over implementatie van ClearContent

De volgende voor waarden zijn mogelijk van toepassing op een implementatie van [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Bij het definiëren van de provider klasse kan een Windows Power shell-inhouds provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode de inhoud niet wissen van objecten die verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Er moet een fout worden geschreven als het pad een item vertegenwoordigt dat is verborgen voor de gebruiker en [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false` .

- Uw implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde verifiëren voordat wijzigingen in het gegevens archief worden aangebracht. Deze methode wordt gebruikt om de uitvoering van een bewerking te bevestigen wanneer een wijziging wordt aangebracht in het gegevens archief, zoals het wissen van inhoud. De methode [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, waarbij de Windows Power shell-runtime alle opdracht regel instellingen of voorkeurs variabelen afhandelt bij het bepalen van wat er moet worden weer gegeven.

  Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wordt geretourneerd `true` , moet de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) worden aangeroepen de methode [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Met deze methode wordt een bericht verzonden naar de gebruiker om te controleren of de bewerking moet worden voortgezet. De aanroep van [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) biedt een extra controle op mogelijk schadelijke systeem wijzigingen.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Dynamische para meters aan de cmdlet voor het wissen van inhoud koppelen

`Clear-Content`Voor de cmdlet zijn mogelijk extra dynamische para meters vereist die tijdens runtime worden toegevoegd. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-inhouds provider de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) implementeren om deze para meters af te handelen. Met deze methode worden de para meters voor het item op het aangegeven pad opgehaald. Met deze methode worden dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de cmdlet.

Deze methode wordt niet door deze Windows Power shell-container provider geïmplementeerd. De volgende code is echter de standaard implementatie van deze methode.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1819-1822":::

## <a name="code-sample"></a>Code voorbeeld

Zie [AccessDbProviderSample06 code sample](./accessdbprovidersample06-code-sample.md)voor een volledige voorbeeld code.

## <a name="defining-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Wanneer u een provider schrijft, kan het nodig zijn om leden toe te voegen aan bestaande objecten of nieuwe objecten te definiëren. Wanneer dit is gebeurd, moet u een bestands typen bestand maken dat door Windows Power shell kan worden gebruikt om de leden van het object en een indelings bestand te identificeren dat definieert hoe het object wordt weer gegeven. Zie [object typen en opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))voor meer informatie.

## <a name="building-the-windows-powershell-provider"></a>De Windows Power shell-provider bouwen

Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>De Windows Power shell-provider testen

Wanneer uw Windows Power shell-provider is geregistreerd bij Windows Power shell, kunt u deze testen door de ondersteunde cmdlets uit te voeren op de opdracht regel. Test bijvoorbeeld de voor beeld-inhouds provider.

Gebruik de `Get-Content` cmdlet om de inhoud van het opgegeven item in de database tabel op te halen in het pad dat is opgegeven door de `Path` para meter. `ReadCount`Met de para meter wordt het aantal items voor de gedefinieerde inhouds lezer opgegeven dat moet worden gelezen (standaard 1). Met de volgende opdracht wordt de cmdlet twee rijen (items) opgehaald uit de tabel en wordt de inhoud ervan weer gegeven. Houd er rekening mee dat in de volgende voorbeeld uitvoer een fictieve Access-Data Base wordt gebruikt.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```Output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Zie ook

[Windows Power shell-providers maken](./how-to-create-a-windows-powershell-provider.md)

[Uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)

[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))

[Een Windows Power shell-provider voor navigatie implementeren](./creating-a-windows-powershell-navigation-provider.md)

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)
