---
title: Het maken van een Windows PowerShell-Provider Container | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: e0d83a742eae2bcde2e691860a5f2b3e5862d2de
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430029"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Een Windows PowerShell-containerprovider maken

In dit onderwerp wordt beschreven hoe u een Windows PowerShell-provider die kan worden gebruikt voor gegevensopslag met meerdere lagen maken. Het hoogste niveau van de store bevat de items van de hoofdmap voor dit type gegevensarchief, en elke latere niveau wordt aangeduid als een knooppunt van het onderliggende items. Een gebruiker kan door de gebruiker om te werken op deze onderliggende knooppunten, hiërarchisch communiceren via het gegevensarchief.

Providers die kunnen worden gebruikt voor meerdere niveaus gegevensarchieven worden aangeduid als Windows PowerShell-container-providers. Wel rekening mee dat de provider van een Windows PowerShell-container kan worden gebruikt alleen wanneer er een container (geen geneste containers) met items erin. Als er geneste containers, moet u een Windows PowerShell-provider voor navigatie implementeren. Zie voor meer informatie over het implementeren van Windows PowerShell-navigatie-provider [het maken van een Windows PowerShell-Provider navigatie](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> U kunt downloaden de C# bronbestand (AccessDBSampleProvider04.cs) voor deze provider met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.
>
> Zie voor meer informatie over andere Windows PowerShell-provider-implementaties, [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

De Windows PowerShell-container-provider die hier worden beschreven definieert de database als de één container, met de tabellen en rijen van de database die is gedefinieerd als items van de container.

> [!CAUTION]
> Let erop dat dit ontwerp wordt ervan uitgegaan dat een database waarvoor een veld met de naam-ID en dat het type van het veld LongInteger is.

Hier volgt een lijst van de secties in dit onderwerp. Als u niet bekend bent met het schrijven van een Windows PowerShell-container-provider, leest u deze informatie in de volgorde waarin deze wordt weergegeven. Echter, als u bekend bent met het schrijven van een Windows PowerShell-container-provider, gaat u rechtstreeks naar de informatie die u nodig hebt.

- [Een Windows PowerShell-Container providerklasse definiëren](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [Basisfunctionaliteit definiëren]()

- [Bij het ophalen van onderliggende Items](#Retrieving-Child-Items)

- [Bezig met koppelen van dynamische Parameters voor de `Get-ChildItem` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [Bij het ophalen van namen van de onderliggende items](#Retrieving-Child-Item-Names)

- [Bezig met koppelen van dynamische Parameters voor de `Get-ChildItem` Cmdlet (naam)](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))

- [Naam van Items wijzigen](#Renaming-Items)

- [Bezig met koppelen van dynamische Parameters voor de `Rename-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [Het maken van nieuwe Items](#Creating-New-Items)

- [Bezig met koppelen van dynamische Parameters voor de `New-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [Een Items verwijderen](#Removing-Items)

- [Bezig met koppelen van dynamische Parameters voor de `Remove-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [Query's uitvoeren voor de onderliggende Items](#Querying-for-Child-Items)

- [Kopieert Items](#Copying-Items)

- [Bezig met koppelen van dynamische Parameters voor de `Copy-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [Voorbeeld van code](#Code-Sample)

- [Objecttype definiëren en opmaak]()

- [Het bouwen van de Windows PowerShell-Provider](#Building-the-Windows-PowerShell-Provider)

- [De Windows PowerShell-Provider testen](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a>Een Windows PowerShell-Container providerklasse definiëren

Een Windows PowerShell-container-provider moet definiëren van een .NET-klasse die is afgeleid van de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) basisklasse. Hier volgt de definitie van de klasse voor de Windows PowerShell-container-provider in deze sectie beschreven.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

U ziet dat in deze klassedefinitie, de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) kenmerk bevat twee parameters. De eerste parameter geeft u een gebruiksvriendelijke naam voor de provider die wordt gebruikt door Windows PowerShell. De tweede parameter geeft u de Windows PowerShell-specifieke mogelijkheden die de provider wordt aangegeven in de Windows PowerShell-runtime tijdens de verwerking van de opdracht. Er zijn geen specifieke mogelijkheden van Windows PowerShell die worden toegevoegd voor deze provider.

## <a name="defining-base-functionality"></a>Basisfunctionaliteit definiëren

Zoals beschreven in [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md), wordt de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse is afgeleid van diverse andere klassen die opgegeven functionaliteit van de andere provider. Daarom moet de provider van een Windows PowerShell-container, de functionaliteit van deze klassen te definiëren.

Zie voor het implementeren van de functionaliteit voor het toevoegen van informatie over de initialisatie van de sessie-specifieke en voor het vrijgeven van resources die worden gebruikt door de provider [het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md). De meeste providers (met inbegrip van de provider die hier worden beschreven) kunnen echter de standaardimplementatie van deze functionaliteit die wordt geleverd door Windows PowerShell gebruiken.

Voor toegang tot het gegevensarchief, moet de provider de methoden voor het implementeren van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basisklasse. Zie voor meer informatie over het implementeren van deze methoden [het maken van een Windows PowerShell station Provider](./creating-a-windows-powershell-drive-provider.md).

Als u wilt bewerken van de items van een gegevensarchief, zoals ophalen, instellen en items wissen, de provider van de methoden die door moet implementeren de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basisklasse. Zie voor meer informatie over het implementeren van deze methoden [het maken van een Windows PowerShell-Provider Item](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Bij het ophalen van onderliggende Items

Als u wilt ophalen van een onderliggend item, de Windows PowerShell-container-provider moet overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode voor de ondersteuning van aanroepen vanuit de `Get-ChildItem` cmdlet. Deze methode worden onderliggende items opgehaald uit het gegevensarchief en schrijft deze naar de pijplijn als objecten. Als de `recurse` parameter van de cmdlet is opgegeven, wordt de methode haalt alle items ongeacht welk niveau deze zijn. Als de `recurse` parameter niet wordt opgegeven, de methode wordt slechts één niveau van onderliggende items opgehaald.

Hier volgt de implementatie van de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode voor deze provider. U ziet dat door deze methode de onderliggende items in alle databasetabellen moet worden opgehaald wanneer het pad geeft aan de Access-database dat en de onderliggende items opgehaald uit de rijen van de tabel als het pad aangeeft een tabel met gegevens dat.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Om te onthouden over het implementeren van GetChildItems

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Bij het definiëren van de providerklasse, een Windows PowerShell-container-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode vereist om ervoor te zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- De uitvoering van deze methode moet rekening houden een vorm van toegang aan het item dat het item zichtbaar voor de gebruiker mogelijk maken. Bijvoorbeeld, als een gebruiker toegang voor schrijven naar een bestand via de bestandssysteem-provider heeft (geleverd door Windows PowerShell), maar niet de toegang lezen, het bestand nog bestaat en [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retourneert `true`. Uw implementatie mogelijk de controle van een bovenliggend item om te zien als het kind kan worden geïnventariseerd.

- Bij het schrijven van meerdere items, de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode kan enige tijd duren. U kunt uw provider om te schrijven van de artikelen met ontwerpen de [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) methode op een tijdstip. Met deze techniek om de items in een stroom aan de gebruiker te presenteren.

- De implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) is verantwoordelijk voor het voorkomen van oneindige recursie wanneer er circulaire koppelingen en dergelijke zijn. Een juiste afsluitende uitzondering moet worden gegenereerd om een voorwaarde weer te geven.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Get-ChildItem

Soms de `Get-ChildItem` cmdlet die worden aangeroepen [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) vereist extra parameters die dynamisch zijn opgegeven tijdens runtime. Voor deze dynamische parameters, de Windows PowerShell-container-provider moet implementeren de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) methode. Deze methode haalt dynamische parameters voor het item in het opgegeven pad op en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `Get-ChildItem` cmdlet.

Deze Windows PowerShell-container-provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Bij het ophalen van namen van de onderliggende items

Als u wilt ophalen van de namen van de onderliggende items, de Windows PowerShell-container-provider moet overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) methode voor de ondersteuning van aanroepen vanuit de `Get-ChildItem`cmdlet wanneer de `Name` parameter is opgegeven. Deze methode worden de namen van de onderliggende items voor het opgegeven pad of een onderliggend itemnamen voor alle containers opgehaald als de `returnAllContainers` parameter van de cmdlet is opgegeven. De naam van een onderliggende is het leaf-gedeelte van een pad. Bijvoorbeeld, is de naam van de onderliggende voor het pad c:\windows\system32\abc.dll 'abc.dll'. De naam van de onderliggende voor de map c:\windows\system32 is 'system32'.

Hier volgt de implementatie van de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) methode voor deze provider. U ziet dat de methode tabelnamen opgehaald als het opgegeven pad geeft aan dat de Access-database (station) en rijnummers als het pad aangeeft een tabel dat.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Om te onthouden over het implementeren van GetChildNames

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Bij het definiëren van de providerklasse, een Windows PowerShell-container-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode vereist om ervoor te zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

  > [!NOTE]
  > Een uitzondering op deze regel treedt op wanneer de `returnAllContainers` parameter van de cmdlet is opgegeven. In dit geval wordt de methode een willekeurige naam onderliggende voor een container moet ophalen, zelfs als deze komt niet overeen met de waarden van de [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), of [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) eigenschappen.

- Standaard onderdrukkingen van deze methode niet Haal de namen van objecten die in het algemeen van de gebruiker worden verborgen, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is opgegeven. Als het opgegeven pad geeft aan een container dat, de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is niet vereist.

- De implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) is verantwoordelijk voor het voorkomen van oneindige recursie wanneer er circulaire koppelingen en dergelijke zijn. Een juiste afsluitende uitzondering moet worden gegenereerd om een voorwaarde weer te geven.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Dynamische Parameters toevoegen aan de Cmdlet Get-ChildItem (naam)

Soms de `Get-ChildItem` cmdlet (met de `Name` parameter) is vereist extra parameters die dynamisch zijn opgegeven tijdens runtime. Voor deze dynamische parameters, de Windows PowerShell-container-provider moet implementeren de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) methode. Deze methode haalt de dynamische parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `Get-ChildItem` cmdlet.

Deze provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Naam van Items wijzigen

Wijzig de naam van een item, een Windows PowerShell-container-provider moet overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) methode voor de ondersteuning van aanroepen vanuit de `Rename-Item` cmdlet. Deze methode wordt de naam van het item in het opgegeven pad naar de nieuwe naam opgegeven. De nieuwe naam moet altijd ten opzichte van het bovenliggende item (container).

Deze provider wordt niet overschreven de [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) methode. Het volgende is echter de standaardimplementatie.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Om te onthouden over het implementeren van RenameItem

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Bij het definiëren van de providerklasse, een Windows PowerShell-container-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode vereist om ervoor te zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- De [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) methode is bedoeld voor het aanpassen van de naam van een item alleen en niet voor verplaatsingsbewerkingen. De implementatie van de methode een fout moet schrijven als de `newName` parameter padscheidingstekens bevat, of kan ertoe leiden dat het item te wijzigen van de bovenliggende locatie.

- Standaard onderdrukkingen van deze methode mag niet de naam van objecten, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is opgegeven. Als het opgegeven pad geeft aan een container dat, de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is niet vereist.

- De implementatie van de [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) en controleer de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Deze methode wordt gebruikt om te bevestigen van de uitvoering van een bewerking wanneer een wijziging wordt aangebracht in de systeemstatus, bijvoorbeeld bestandsnamen. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource moet worden gewijzigd voor de gebruiker met de Windows PowerShell-runtime rekening houdend met instellingen vanaf de opdrachtregel of voorkeursvariabelen in bepalen wat moet worden weergegeven.

  Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`, wordt de [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode. Deze methode verzendt een bericht verschijnt een bevestigingsbericht aan de gebruiker om toe te staan aanvullende feedback in te spreken als de bewerking moet worden voortgezet. Een provider moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) als een aanvullende controle voor wijzigingen die mogelijk schadelijke system.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Rename-Item

Soms de `Rename-Item` cmdlet extra parameters die dynamisch zijn opgegeven tijdens runtime is vereist. Voor deze dynamische parameters, Windows PowerShell-container-provider moet implementeren de [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) methode. Deze methode haalt de parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `Rename-Item` cmdlet.

Deze container-provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Het maken van nieuwe Items

Voor het maken van nieuwe items aanbieder van de container moet implementeren de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode voor de ondersteuning van aanroepen vanuit de `New-Item` cmdlet. Deze methode maakt u een gegevensitem dat zich bevindt in het opgegeven pad. De `type` parameter van de cmdlet het type provider gedefinieerd voor het nieuwe item bevat. De bestandssysteem-provider gebruikt bijvoorbeeld een `type` parameter met de waarde 'file' of 'directory'. De `newItemValue` parameter van de cmdlet geeft u een provider-specifieke waarde voor het nieuwe item.

Hier volgt de implementatie van de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode voor deze provider.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Om te onthouden over het implementeren van nieuw item

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- De [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode moet worden uitgevoerd door een niet-hoofdlettergevoelige vergelijking van de tekenreeks wordt de `type` parameter. Het moet ook toestaan voor minste niet-eenduidige overeenkomsten. Voor de typen 'file' en 'directory', bijvoorbeeld alleen de eerste letter vereist om op te heffen. Als de `type` parameter geeft aan dat een type dat de provider niet maken kan, de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode moet een ArgumentException met een bericht schrijven de typen die aangeeft kunt de provider maken.

- Voor de `newItemValue` parameter, de implementatie van de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode om te accepteren van tekenreeksen ten minste wordt aanbevolen. Deze ook toestemming moet geven het type object dat is opgehaald door de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) methode voor hetzelfde pad. De [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode kunt gebruiken de [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) methode voor het converteren van het type aan het gewenste type.

- De implementatie van de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) en controleer de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert ' True ', de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode als een aanvullende controle voor wijzigingen die mogelijk schadelijke system.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Nieuw Item

Soms de `New-Item` cmdlet extra parameters die dynamisch zijn opgegeven tijdens runtime is vereist. Voor deze dynamische parameters, de provider van de container moet implementeren de [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) methode. Deze methode haalt de parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `New-Item` cmdlet.

Deze provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Items verwijderen

Als u wilt verwijderen, de Windows PowerShell-provider moet overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) methode voor de ondersteuning van aanroepen vanuit de `Remove-Item` cmdlet. Deze methode wordt een item verwijderd uit het gegevensarchief in het opgegeven pad. Als de `recurse` parameter van de `Remove-Item` cmdlet is ingesteld op `true`, de methode verwijdert u alle onderliggende items, ongeacht hun niveau. Als de parameter is ingesteld op `false`, de methode verwijdert u slechts één item in het opgegeven pad.

Deze provider biedt geen ondersteuning voor het item verwijderen. De volgende code is echter de standaardimplementatie van [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Om te onthouden over het implementeren van RemoveItem

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Bij het definiëren van de providerklasse, een Windows PowerShell-container-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode vereist om ervoor te zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode moeten niet verwijderen, objecten, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op true. Als het opgegeven pad geeft aan een container dat, de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is niet vereist.

- De implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) is verantwoordelijk voor het voorkomen van oneindige recursie wanneer er circulaire koppelingen en dergelijke zijn. Een juiste afsluitende uitzondering moet worden gegenereerd om een voorwaarde weer te geven.

- De implementatie van de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) en controleer de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert `true`, wordt de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode als een aanvullende controle voor wijzigingen die mogelijk schadelijke system.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Remove-Item

Soms de `Remove-Item` cmdlet extra parameters die dynamisch zijn opgegeven tijdens runtime is vereist. Voor deze dynamische parameters, de provider van de container moet implementeren de [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) methode voor het afhandelen van deze parameters. Deze methode haalt de dynamische parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `Remove-Item` cmdlet.

Deze container-provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Query's uitvoeren voor de onderliggende Items

Als u wilt controleren om te zien als onderliggende items aanwezig zijn in het opgegeven pad, de Windows PowerShell-container-provider moet overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) methode. Deze methode retourneert `true` als het item onderliggende items heeft, en `false` anders. Voor een null of leeg pad, de methode rekening gehouden met alle items in het gegevensarchief moeten kinderen en retourneert `true`.

Hier volgt de onderdrukking voor de [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) methode. Als er meer dan twee onderdelen van het bestandspad die zijn gemaakt door de ChunkPath Help-methode te zijn, retourneert de methode `false`, aangezien alleen de databasecontainer van een en een container van de tabel zijn gedefinieerd. Zie voor meer informatie over deze Help-methode de methode ChunkPath wordt besproken in [het maken van een Windows PowerShell-Provider Item](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Om te onthouden over het implementeren van HasChildItems

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Als de container-provider wordt aangegeven dat een toegangspunt met interessante koppelpunten, de implementatie van de [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) methode moet retourneren `true`wanneer een null-waarde of een lege tekenreeks is doorgegeven voor het pad.

## <a name="copying-items"></a>Items kopiëren

Als u wilt kopiëren items, de provider van de container moet implementeren de [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) methode voor de ondersteuning van aanroepen vanuit de `Copy-Item` cmdlet. Deze methode wordt een gegevensitem gekopieerd vanaf de locatie die door de `path` parameter van de cmdlet naar de locatie die is aangegeven door de `copyPath` parameter. Als de `recurse` parameter is opgegeven, wordt de methode kopieert alle onderliggende containers. Als de parameter niet opgegeven is, wordt de methode slechts één niveau van items kopieert.

Deze provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Om te onthouden over het implementeren van CopyItem

De volgende voorwaarden mogelijk van toepassing op de implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Bij het definiëren van de providerklasse, een Windows PowerShell-container-provider provider mogelijkheden van ExpandWildcards, Filter, opnemen of uitsluiten, mogelijk declareren van de [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) opsomming. In dergelijke gevallen de uitvoering van de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode vereist om ervoor te zorgen dat het pad dat is doorgegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. U doet dit door de methode moet toegang tot de juiste eigenschap, bijvoorbeeld, de [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) eigenschappen.

- Standaard onderdrukkingen van deze methode mag niet worden gekopieerd objecten op bestaande objecten, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Bijvoorbeeld, de provider van het bestandssysteem worden niet gekopieerd c:\temp\abc.txt via een bestaand c:\abc.txt-bestand, tenzij de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is ingesteld op `true`. Als het pad opgegeven in de `copyPath` parameter bestaat en een container geeft aan dat de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) eigenschap is niet vereist. In dit geval [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) kopieert het item dat wordt aangegeven door de `path` parameter voor de container aangegeven door de `copyPath` parameter als een onderliggend element.

- De implementatie van [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) is verantwoordelijk voor het voorkomen van oneindige recursie wanneer er circulaire koppelingen en dergelijke zijn. Een juiste afsluitende uitzondering moet worden gegenereerd om een voorwaarde weer te geven.

- De implementatie van de [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) methode moet aanroepen [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) en controleer de geretourneerde waarde voordat u wijzigingen aanbrengt aan de gegevensopslag. Na het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourneert ' True ', de [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) methode moet aanroepen de [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) methode als een aanvullende controle voor wijzigingen die mogelijk schadelijke system. Zie voor meer informatie over het aanroepen van deze methoden [Items wijzigen](#Renaming-Items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Dynamische Parameters toevoegen aan de Cmdlet Copy-Item

Soms de `Copy-Item` cmdlet extra parameters die dynamisch zijn opgegeven tijdens runtime is vereist. Voor deze dynamische parameters, de Windows PowerShell-container-provider moet implementeren de [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) methode voor het afhandelen van deze de parameters. Deze methode haalt de parameters voor het item in het opgegeven pad en retourneert een object met eigenschappen en velden met het parseren van kenmerken die vergelijkbaar is met een cmdlet-klasse of een [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object. De Windows PowerShell-runtime maakt gebruik van het geretourneerde object om toe te voegen van de parameters voor de `Copy-Item` cmdlet.

Deze provider wordt niet geïmplementeerd voor deze methode. De volgende code is echter de standaardimplementatie van [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Voorbeeld van code

Zie voor een compleet voorbeeld van code, [AccessDbProviderSample04 codevoorbeeld](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Het bouwen van de Windows PowerShell-Provider

Zie [over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>De Windows PowerShell-Provider testen

Als uw Windows PowerShell-provider is geregistreerd met Windows PowerShell, kunt u deze testen door het uitvoeren van de ondersteunde cmdlets op de opdrachtregel. Let erop dat de volgende voorbeelduitvoer wordt gebruikt een fictieve Access-database.

1. Voer de `Get-ChildItem` cmdlet voor het ophalen van de lijst met onderliggende items uit een klantentabel in de Access-database.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   De volgende uitvoer wordt weergegeven.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Voer de `Get-ChildItem` cmdlet opnieuw uit voor het ophalen van de gegevens van een tabel.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   De volgende uitvoer wordt weergegeven.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Gebruik nu de `Get-Item` cmdlet voor het ophalen van de items in rij 0 in de tabel.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   De volgende uitvoer wordt weergegeven.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Hergebruik `Get-Item` om op te halen van de gegevens voor de items in de rij 0.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   De volgende uitvoer wordt weergegeven.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Gebruik nu de `New-Item` cmdlet om een rij toevoegt aan een bestaande tabel. De `Path` parameter Hiermee geeft u het volledige pad naar de rij en dient een rijnummer aan te geven dat groter is dan het bestaande aantal rijen in de tabel. De `Type` parameter geeft 'rij' als u wilt opgeven dat type item toe te voegen. Ten slotte de `Value` parameter geeft u een door komma's gescheiden lijst met waarden van de kolom voor de rij.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAdress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Controleer de juistheid van de bewerking van het nieuwe item als volgt.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   De volgende uitvoer wordt weergegeven.

   ```output
   ID        : 3
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
   ```

## <a name="see-also"></a>Zie ook

[Het maken van Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[Het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Implementatie van een Item Windows PowerShell-Provider](./creating-a-windows-powershell-item-provider.md)

[Implementatie van een Windows PowerShell-Provider van navigatie](./creating-a-windows-powershell-navigation-provider.md)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)