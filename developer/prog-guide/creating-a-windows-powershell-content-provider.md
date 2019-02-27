---
title: Het maken van een Provider van Windows PowerShell-inhoud | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 6e5d79487539d4f58922e2686f1fdba08797f305
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846324"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Een Windows PowerShell-inhoudsprovider maken

In dit onderwerp wordt beschreven hoe u een Windows PowerShell-provider waarmee de gebruiker voor het bewerken van de inhoud van de items in een gegevensarchief maken. Als gevolg hiervan wordt een provider die u kunt de inhoud van items bewerken aangeduid als een Windows PowerShell-inhoudsprovider.

> [!NOTE]
> U kunt downloaden de C# bronbestand (AccessDBSampleProvider06.cs) voor deze provider met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> U kunt downloaden de C# bronbestand (AccessDBSampleProvider06.cs) voor deze provider met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.
>
> Zie voor meer informatie over andere Windows PowerShell-provider-implementaties, [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

De volgende lijst bevat de secties in dit onderwerp. Als u niet bekend bent met het schrijven van een Windows PowerShell-inhoudsprovider, lees deze gedeeltes in de volgorde waarin ze worden weergegeven. Echter, als u bekend bent met het schrijven van een Windows PowerShell-inhoudsprovider, Ga rechtstreeks naar de informatie die u nodig hebt.

- [De klasse-Provider van Windows PowerShell-inhoud definiëren](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [Basisfunctionaliteit definiëren](#Define-Functionality-of-Base-Class)

- [Implementatie van een Content-lezer](#Implementing-a-Content-Reader)

- [Implementatie van een Content-schrijver](#Implementing-a-Content-Writer)

- [Bij het ophalen van de inhoud lezer](#Retrieving-the-Content-Reader)

- [Bezig met koppelen van dynamische Parameters voor de `Get-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [Bij het ophalen van de schrijver van inhoud](#Retrieving-the-Content-Writer)

- [Dynamische Parameters te koppelen aan de Add_Content en `Set-Content` Cmdlets](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [Inhoud wissen](#Clearing-Content)

- [Bezig met koppelen van dynamische Parameters voor de `Clear-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [Voorbeeld van code](#Code-Sample)

- [Objecttype definiëren en opmaak]()

- [Het bouwen van de Windows PowerShell-provider](#Building-the-Windows-PowerShell-Provider)

- [De Windows PowerShell-provider testen](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>De klasse-Provider van Windows PowerShell-inhoud definiëren

Een Windows PowerShell-inhoudsprovider moet maakt u een .NET-klasse die ondersteuning biedt voor de [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface. Hier volgt de definitie van de klasse voor de item-provider in deze sectie beschreven.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Houd er rekening mee dat in deze klassedefinitie, de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk bevat twee parameters. De eerste parameter geeft u een gebruiksvriendelijke naam voor de provider die wordt gebruikt door Windows PowerShell. De tweede parameter geeft u de Windows PowerShell-specifieke mogelijkheden die de provider wordt aangegeven in de Windows PowerShell-runtime tijdens de verwerking van de opdracht. Er zijn geen extra specifieke mogelijkheden van Windows PowerShell voor deze provider.

## <a name="define-functionality-of-base-class"></a>Functionaliteit van de basisklasse definiëren

Zoals beschreven in [ontwerp van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md), wordt de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse is afgeleid van diverse andere klassen die opgegeven functionaliteit van de andere provider. Een Windows PowerShell-inhoudsprovider, daarom doorgaans worden alle gedefinieerd van de functionaliteit van de bovenliggende klassen.

Zie voor meer informatie over het implementeren van de functionaliteit voor het toevoegen van informatie over de initialisatie van de sessie-specifieke en voor het vrijgeven van resources die worden gebruikt door de provider [het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md). De meeste providers, met inbegrip van de provider hier beschreven, kunnen echter de standaardimplementatie van deze functionaliteit die wordt geleverd door Windows PowerShell gebruiken.

Voor toegang tot het gegevensarchief, moet de provider de methoden voor het implementeren van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basisklasse. Zie voor meer informatie over het implementeren van deze methoden [het maken van een Windows PowerShell station Provider](./creating-a-windows-powershell-drive-provider.md).

Als u wilt bewerken van de items van een gegevensarchief, zoals ophalen, instellen en items wissen, de provider van de methoden die door moet implementeren de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basisklasse. Zie voor meer informatie over het implementeren van deze methoden [het maken van een Windows PowerShell-Provider Item](./creating-a-windows-powershell-item-provider.md).

Als u wilt werken met meerdere lagen gegevensarchieven, moet u de provider de methoden die door implementeren de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) basisklasse. Zie voor meer informatie over het implementeren van deze methoden [het maken van een Windows PowerShell-Provider Container](./creating-a-windows-powershell-container-provider.md).

Ter ondersteuning van recursieve opdrachten, geneste containers en relatieve paden, de provider moet implementeren de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basisklasse. Deze Windows PowerShell-inhoudsprovider kunnen bovendien wordt [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface met de [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basisklasse en de methoden die door deze klasse moet daarom worden geïmplementeerd. Zie voor meer informatie, uitvoering van deze methoden, Zie [implementeren van een Windows PowerShell-Provider van navigatie](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementatie van een Content-lezer

Als u wilt lezen inhoud van een item, een provider moet worden geïmplementeerd een inhoud reader-klasse die is afgeleid van [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). De inhoud lezer voor deze provider biedt toegang tot de inhoud van een rij in een tabel met gegevens. De inhoud reader-klasse definieert een **lezen** methode die de gegevens worden opgehaald uit de opgegeven rij en retourneert een lijst die gegevens vertegenwoordigt een **zoeken** methode die wordt verplaatst van de inhoud lezer, een  **Sluiten** methode waarmee de inhoud lezer wordt gesloten en een **buitengebruikstelling** methode.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementatie van een Content-schrijver

Als u wilt schrijf er inhoud naar een artikel, een provider een inhoud moet implementeren schrijver klasse is afgeleid van [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). De klasse inhoud schrijver definieert een **schrijven** methode die de inhoud van de opgegeven rij, schrijft een **zoeken** methode die wordt verplaatst van de inhoud schrijver een **sluiten** methode die wordt gesloten de schrijver van inhoud, en een **buitengebruikstelling** methode.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Bij het ophalen van de inhoud lezer

Als u de inhoud van een item, de provider moet implementeren de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) ter ondersteuning van de `Get-Content` cmdlet. Deze methode retourneert de inhoud lezer voor het item dat zich bevindt in het opgegeven pad. De reader-object kan vervolgens worden geopend om te lezen van de inhoud.

Hier volgt de implementatie van [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) voor deze methode voor deze provider.

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Om te onthouden over het implementeren van GetContentReader

De volgende voorwaarden mogelijk van toepassing op een implementatie van [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Bij het definiëren van de providerklasse, een Windows PowerShell-inhoudsprovider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) methode moet ervoor zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet ophalen van een lezer voor objecten die door de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Een fout moet worden geschreven als het pad staat voor een item dat is verborgen voor de gebruiker en [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Get-inhoud

De `Get-Content` cmdlet mogelijk extra parameters die dynamisch zijn opgegeven tijdens runtime. Voor deze dynamische parameters, de provider van de Windows PowerShell-inhoud moet worden geïmplementeerd de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) methode. Deze methode haalt dynamische parameters voor het item in het opgegeven pad op en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object de parameters toevoegen aan de cmdlet.

Deze Windows PowerShell-container-provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Bij het ophalen van de schrijver van inhoud

Als u wilt schrijf er inhoud naar een artikel, de provider moet implementeren de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) ter ondersteuning van de `Set-Content` en `Add-Content` cmdlets. Deze methode retourneert de inhoud-schrijver van het item dat zich bevindt in het opgegeven pad.

Hier volgt de implementatie van [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) voor deze methode.

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Om te onthouden over het implementeren van GetContentWriter

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Bij het definiëren van de providerklasse, een Windows PowerShell-inhoudsprovider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) methode moet ervoor zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet ophalen van een schrijver voor objecten die door de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Een fout moet worden geschreven als het pad staat voor een item dat is verborgen voor de gebruiker en [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Dynamische Parameters te koppelen aan de Cmdlets toevoegen-inhoud en Set-inhoud

De `Add-Content` en `Set-Content` cmdlets mogelijk extra dynamische parameters die een runtime worden toegevoegd. Voor deze dynamische parameters, de provider van de Windows PowerShell-inhoud moet worden geïmplementeerd de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) methode voor het afhandelen van deze de parameters. Deze methode haalt dynamische parameters voor het item in het opgegeven pad op en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object de parameters toevoegen aan de cmdlets.

Deze Windows PowerShell-container-provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Inhoud wissen

Uw inhoudsprovider implementeert de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) methode ter ondersteuning van de `Clear-Content` cmdlet. Deze methode wordt verwijderd van de inhoud van het item in het opgegeven pad, maar het item intact blijft.

Hier volgt de implementatie van de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) methode voor deze provider.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Om te onthouden over het implementeren van ClearContent

De volgende voorwaarden mogelijk van toepassing op een implementatie van [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Bij het definiëren van de providerklasse, een Windows PowerShell-inhoudsprovider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) methode moet ervoor zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard schakelt onderdrukkingen van deze methode moeten niet de inhoud van objecten die door de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Een fout moet worden geschreven als het pad staat voor een item dat is verborgen voor de gebruiker en [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `false`.

- De implementatie van de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) en controleer of de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Deze methode wordt gebruikt om te bevestigen van de uitvoering van een bewerking wanneer een wijziging wordt aangebracht in het gegevensarchief, zoals het wissen van inhoud. De [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) methode worden verzonden, de naam van de resource moet worden gewijzigd voor de gebruiker met de Windows PowerShell-runtime verwerking opdrachtregel instellingen of voorkeur de variabelen bij het bepalen van wat moet worden weergegeven.

  Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`, wordt de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode. Deze methode verzendt een bericht naar de gebruiker om toe te staan van feedback om te controleren of als de bewerking moet worden voortgezet. De aanroep van [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) kunt u een extra controle voor wijzigingen die mogelijk schadelijke system.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Clear-inhoud

De `Clear-Content` cmdlet mogelijk extra dynamische parameters die worden toegevoegd tijdens runtime. Voor deze dynamische parameters, de provider van de Windows PowerShell-inhoud moet worden geïmplementeerd de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) methode voor het afhandelen van deze de parameters. Deze methode haalt de parameters voor het item in het opgegeven pad. Deze methode haalt dynamische parameters voor het item in het opgegeven pad op en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object de parameters toevoegen aan de cmdlet.

Deze Windows PowerShell-container-provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Voorbeeld van code

Zie voor een compleet voorbeeld van code, [AccessDbProviderSample06 codevoorbeeld](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Objecttype definiëren en opmaak

Bij het schrijven van een provider, is het mogelijk dat het nodig zijn voor leden toevoegen aan bestaande objecten of nieuwe objecten te definiëren. Wanneer dit wordt gedaan, moet u een typen-bestand dat Windows PowerShell gebruiken om de leden van het object te identificeren en een indelingsbestand waarmee wordt gedefinieerd hoe het object wordt weergegeven. Zie voor meer informatie, [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).
Bij het schrijven van een provider, is het mogelijk dat het nodig zijn voor leden toevoegen aan bestaande objecten of nieuwe objecten te definiëren. Wanneer dit wordt gedaan, moet u een typen-bestand dat Windows PowerShell gebruiken om de leden van het object te identificeren en een indelingsbestand waarmee wordt gedefinieerd hoe het object wordt weergegeven. Zie voor meer informatie, [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Het bouwen van de Windows PowerShell-Provider

Zie [over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).
Zie [over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>De Windows PowerShell-Provider testen

Als uw Windows PowerShell-provider is geregistreerd met Windows PowerShell, kunt u deze testen door het uitvoeren van de ondersteunde cmdlets op de opdrachtregel. Bijvoorbeeld, de voorbeeld-inhoudsprovider testen.

Gebruik de `Get-Content` cmdlet voor het ophalen van de inhoud van het opgegeven item in de database-tabel in het pad dat is opgegeven door de `Path` parameter. De `ReadCount` parameter geeft u het aantal items voor de gedefinieerde inhoud lezer te lezen (standaard 1). Met de volgende vermelding van de opdracht wordt de cmdlet worden twee rijen (objecten) opgehaald uit de tabel en hun inhoud wordt weergegeven. Houd er rekening mee dat de volgende voorbeelduitvoer wordt gebruikt een fictieve Access-database.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
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

[Het maken van Windows PowerShell-providers](./how-to-create-a-windows-powershell-provider.md)

[Ontwerp uw Windows PowerShell-provider](./designing-your-windows-powershell-provider.md)

[Objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementatie van een navigatie Windows PowerShell-provider](./creating-a-windows-powershell-navigation-provider.md)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)
