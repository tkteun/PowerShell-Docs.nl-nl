---
ms.date: 09/13/2016
ms.topic: reference
title: Een Windows PowerShell-containerprovider maken
description: Een Windows PowerShell-containerprovider maken
ms.openlocfilehash: 999bd69e3c16bfc0a74519986654ec15bbc0da6d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645357"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Een Windows PowerShell-containerprovider maken

In dit onderwerp wordt beschreven hoe u een Windows Power shell-provider maakt die kan worden gebruikt voor gegevens opslag met meerdere lagen. Voor dit type gegevens archief bevat het hoogste niveau van de Store de hoofd items en elk volgend niveau wordt een knoop punt van onderliggende items genoemd. Door de gebruiker toe te staan om deze onderliggende knoop punten te gebruiken, kan een gebruiker hiërarchisch communiceren via het gegevens archief.

Providers die kunnen werken op gegevens archieven met meerdere niveaus worden aangeduid als Windows Power shell-container providers. Houd er echter rekening mee dat een Windows Power shell-container provider alleen kan worden gebruikt als er één container (geen geneste containers) met items bevat. Als er geneste containers zijn, moet u een Windows Power shell-navigatie provider implementeren. Zie [een Windows Power shell-navigatie provider maken](./creating-a-windows-powershell-navigation-provider.md)voor meer informatie over het implementeren van een Windows Power shell-navigatie provider.

> [!NOTE]
> U kunt het C#-bron bestand (AccessDBSampleProvider04.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map. Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.

De Windows Power shell-container provider die hier wordt beschreven, definieert de Data Base als één container, waarbij de tabellen en rijen van de Data Base zijn gedefinieerd als items van de container.

> [!CAUTION]
> Houd er rekening mee dat in dit ontwerp wordt uitgegaan van een Data Base met een veld met de naam-ID en dat het type van het veld LongInteger is.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Een Windows Power shell-container provider klasse definiëren

Een Windows Power shell-container provider moet een .NET-klasse definiëren die is afgeleid van de basis klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Hier volgt de klassedefinitie voor de Windows Power shell-container provider die in deze sectie wordt beschreven.

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
public class AccessDBProvider : ContainerCmdletProvider
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="34-35":::

Merk op dat in deze klassedefinitie, het kenmerk [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) twee para meters bevat. De eerste para meter geeft u een beschrijvende naam op voor de provider die wordt gebruikt door Windows Power shell. Met de tweede para meter geeft u de specifieke Windows Power shell-mogelijkheden op die de provider beschikbaar maakt voor de Windows Power shell-runtime tijdens het verwerken van opdrachten. Voor deze provider zijn er geen specifieke Windows Power shell-functies die worden toegevoegd.

## <a name="defining-base-functionality"></a>Basis functionaliteit definiëren

Zoals beschreven in het [ontwerpen van uw Windows Power shell-provider](./designing-your-windows-powershell-provider.md), is de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) afgeleid van verschillende andere klassen die een andere provider functionaliteit hebben verschaft. Voor een Windows Power shell-container provider moet daarom alle functionaliteit worden gedefinieerd die door deze klassen wordt opgegeven.

Zie [een eenvoudige Windows Power shell-provider maken](./creating-a-basic-windows-powershell-provider.md)voor informatie over het implementeren van de functionaliteit voor het toevoegen van toepassingsspecifieke initialisatie gegevens en voor het vrijgeven van resources die worden gebruikt door de provider.
De meeste providers (met inbegrip van de hier beschreven provider) kunnen echter gebruikmaken van de standaard implementatie van deze functionaliteit die wordt verschaft door Windows Power shell.

Om toegang te krijgen tot het gegevens archief, moet de provider de methoden van de basis klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) implementeren. Zie [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md)voor meer informatie over het implementeren van deze methoden.

Voor het bewerken van de items van een gegevens archief, zoals het ophalen, instellen en wissen van items, moet de provider de methoden implementeren die worden verschaft door de basis klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Zie [een Windows Power shell-item provider maken](./creating-a-windows-powershell-item-provider.md)voor meer informatie over het implementeren van deze methoden.

## <a name="retrieving-child-items"></a>Onderliggende items ophalen

Als u een onderliggend item wilt ophalen, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) overschrijven om aanroepen van de cmdlet te ondersteunen `Get-ChildItem` . Deze methode haalt onderliggende items van het gegevens archief op en schrijft deze naar de pijp lijn als objecten. Als de `recurse` para meter van de cmdlet is opgegeven, haalt de methode alle onderliggende items op, ongeacht het niveau waarin ze zich bevinden. Als de `recurse` para meter niet is opgegeven, haalt de methode slechts één niveau van onderliggende items op.

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) voor deze provider. U ziet dat met deze methode de onderliggende items in alle database tabellen worden opgehaald wanneer het pad de Access-Data Base aangeeft, en worden de onderliggende items opgehaald uit de rijen van de tabel als het pad een gegevens tabel aangeeft.

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="311-362":::

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Wat u moet weten over implementatie van GetChildItems

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Voor de implementatie van deze methode moet rekening worden gehouden met elke vorm van toegang tot het item die het item mogelijk zichtbaar maakt voor de gebruiker. Bijvoorbeeld, als een gebruiker schrijf toegang heeft tot een bestand via de bestandssysteem provider (geleverd door Windows Power shell), maar geen lees toegang, het bestand nog bestaat en [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) wordt geretourneerd `true` . Voor uw implementatie moet mogelijk een bovenliggend item worden gecontroleerd om te zien of de onderliggende items kunnen worden geïnventariseerd.

- Bij het schrijven van meerdere items kan de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) enige tijd duren. U kunt uw provider zo ontwerpen dat de items met de methode [System. Management. Automation. provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) per keer worden geschreven. Met deze techniek worden de items aan de gebruiker in een stroom gepresenteerd.

- Uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) is verantwoordelijk voor het voor komen van oneindige recursie wanneer er circulaire koppelingen zijn en het soort gelijke. Er moet een geschikte afsluit uitzondering worden gegenereerd om een dergelijke voor waarde weer te geven.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Dynamische para meters aan de Get-ChildItem-cmdlet koppelen

Soms `Get-ChildItem` vereist de cmdlet die [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) aanroept, extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) implementeren. Met deze methode worden dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Get-ChildItem` cmdlet.

Deze methode wordt niet door deze Windows Power shell-container provider geïmplementeerd. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Onderliggend item namen ophalen

Als u de namen van onderliggende items wilt ophalen, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) overschrijven om aanroepen van de cmdlet te ondersteunen `Get-ChildItem` wanneer de `Name` para meter is opgegeven. Met deze methode worden de namen van de onderliggende items voor het opgegeven pad of onderliggende item namen voor alle containers opgehaald als de `returnAllContainers` para meter van de cmdlet is opgegeven. Een onderliggende naam is het Leaf-gedeelte van een pad. De onderliggende naam voor het pad c:\windows\system32\abc.dll bijvoorbeeld ' abc.dll ' is. De onderliggende naam voor de map c:\Windows\System32 is ' system32 '.

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) voor deze provider. U ziet dat met de methode tabel namen worden opgehaald als in het opgegeven pad de Access-Data Base (station) en de rijnummers worden aangegeven als het pad een tabel aangeeft.

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="369-411":::

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Wat u moet weten over implementatie van GetChildNames

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

  > [!NOTE]
  > Een uitzonde ring op deze regel treedt op wanneer de `returnAllContainers` para meter van de cmdlet is opgegeven. In dit geval moet de methode een onderliggende naam voor een container ophalen, zelfs als deze niet overeenkomt met de waarden van [System. Management. Automation. provider. Cmdletprovider. filter *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), System. Management. Automation. provider. [Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), of [System. beheer. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) eigenschappen.

- Standaard moeten onderdrukkingen van deze methode geen namen ophalen van objecten die doorgaans verborgen zijn voor de gebruiker, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is opgegeven. Als het opgegeven pad een container aangeeft, is de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) niet vereist.

- Uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) is verantwoordelijk voor het voor komen van oneindige recursie wanneer er circulaire koppelingen zijn en het soort gelijke. Er moet een geschikte afsluit uitzondering worden gegenereerd om een dergelijke voor waarde weer te geven.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Dynamische para meters aan de Get-ChildItem-cmdlet (naam) koppelen

Soms `Get-ChildItem` vereist de cmdlet (met de `Name` para meter) extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) implementeren. Met deze methode worden de dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Get-ChildItem` cmdlet.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Naam van items wijzigen

Als u de naam van een item wilt wijzigen, moet een Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) overschrijven om aanroepen van de cmdlet te ondersteunen `Rename-Item` . Met deze methode wordt de naam van het item op het opgegeven pad gewijzigd in de nieuwe naam die wordt opgegeven. De nieuwe naam moet altijd relatief zijn ten opzichte van het bovenliggende item (container).

Deze provider overschrijft de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) niet. Het volgende is echter de standaard implementatie.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Wat u moet weten over implementatie van RenameItem

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) is bedoeld voor het wijzigen van de naam van een item en niet voor move-bewerkingen.
  Uw implementatie van de methode moet een fout schrijven als de `newName` para meter pad scheidings tekens bevat of het item anders de bovenliggende locatie kan wijzigen.

- Standaard moeten onderdrukkingen van deze methode de naam van objecten alleen wijzigen als de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is opgegeven. Als het opgegeven pad een container aangeeft, is de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) niet vereist.

- Uw implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde controleren voordat wijzigingen in het gegevens archief worden aangebracht. Deze methode wordt gebruikt om de uitvoering van een bewerking te bevestigen wanneer een wijziging wordt aangebracht in de systeem status, bijvoorbeeld het wijzigen van de naam van bestanden.
  [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) verzendt de naam van de resource die moet worden gewijzigd naar de gebruiker, met de Windows Power shell-runtime, waarbij rekening wordt gehouden met alle opdracht regel instellingen of voorkeurs variabelen bij het bepalen van wat er moet worden weer gegeven.

  Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wordt geretourneerd `true` , moet de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) worden aangeroepen de methode [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Met deze methode wordt een bericht met een bevestigings bericht verzonden naar de gebruiker om extra feedback te geven om te zeggen dat de bewerking moet worden voortgezet. Een provider moet [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) aanroepen als extra controle op mogelijk schadelijke systeem wijzigingen.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Dynamische para meters aan de Rename-Item-cmdlet koppelen

Soms `Rename-Item` vereist de cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet u de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) implementeren. Met deze methode worden de para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Rename-Item` cmdlet.

Deze methode wordt niet door deze container provider geïmplementeerd. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Nieuwe items maken

Als u nieuwe items wilt maken, moet een container provider de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) implementeren ter ondersteuning van aanroepen van de `New-Item` cmdlet. Met deze methode maakt u een gegevens item dat zich op het opgegeven pad bevindt. De `type` para meter van de cmdlet bevat het type dat door de provider is gedefinieerd voor het nieuwe item. De File System Provider gebruikt bijvoorbeeld een `type` para meter met de waarde "file" of "directory". `newItemValue`Met de para meter van de cmdlet wordt een providerspecifieke waarde voor het nieuwe item opgegeven.

Hier volgt de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) voor deze provider.

```csharp
protected override void NewItem( string path, string type, object newItemValue )
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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="939-955":::

#### <a name="things-to-remember-about-implementing-newitem"></a>Wat u moet weten over implementatie van NewItem mag

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- De methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) moet een niet-hoofdletter gevoelige vergelijking uitvoeren van de teken reeks die wordt door gegeven in de `type` para meter.
  Het moet ook ten minste ambigue overeenkomsten toestaan. Voor de typen ' bestand ' en ' Directory ' is alleen de eerste letter vereist voor dubbel zinnigheid. Als de `type` para meter een type aangeeft dat uw provider niet kan maken, moet de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) een ArgumentException schrijven met een bericht dat aangeeft welke typen de provider kan maken.

- Voor de `newItemValue` para meter wordt de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) aanbevolen om teken reeksen ten minste te accepteren. Ook moet het type object dat wordt opgehaald door de methode [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) worden geaccepteerd voor hetzelfde pad. De methode System. [Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) kan de methode [System. Management. Automation. Languageprimitives. ConvertTo *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) gebruiken om typen te converteren naar het gewenste type.

- Uw implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde controleren voordat wijzigingen in het gegevens archief worden aangebracht. Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) is ingesteld op True, moet de [methode System](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) [. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) worden aangeroepen als extra controle op mogelijke schadelijke systeem wijzigingen.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Dynamische para meters aan de New-Item-cmdlet koppelen

Soms `New-Item` vereist de cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) implementeren. Met deze methode worden de para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `New-Item` cmdlet.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van deze methode.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Items verwijderen

Als u items wilt verwijderen, moet de Windows Power shell-provider de methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) overschrijven om aanroepen van de cmdlet te ondersteunen `Remove-Item` . Met deze methode wordt een item uit het gegevens archief op het opgegeven pad verwijderd. Als de `recurse` para meter van de `Remove-Item` cmdlet is ingesteld op `true` , verwijdert de methode alle onderliggende items, ongeacht hun niveau. Als de para meter is ingesteld op `false` , wordt met de methode slechts één item uit het opgegeven pad verwijderd.

Deze provider biedt geen ondersteuning voor het verwijderen van items. De volgende code is echter de standaard implementatie van [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Wat u moet weten over het implementeren van RemoveItem

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen objecten verwijderen, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op True. Als het opgegeven pad een container aangeeft, is de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) niet vereist.

- Uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) is verantwoordelijk voor het voor komen van oneindige recursie wanneer er circulaire koppelingen zijn en het soort gelijke. Er moet een geschikte afsluit uitzondering worden gegenereerd om een dergelijke voor waarde weer te geven.

- Uw implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde controleren voordat wijzigingen in het gegevens archief worden aangebracht. Nadat de aanroep van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wordt geretourneerd `true` , moet de methode [System](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) [. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) worden aangeroepen als extra controle op mogelijke schadelijke systeem wijzigingen.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Dynamische para meters aan de Remove-Item-cmdlet koppelen

Soms `Remove-Item` vereist de cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) implementeren om deze para meters af te handelen. Met deze methode worden de dynamische para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met het parseren van kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Remove-Item` cmdlet.

Deze methode wordt niet door deze container provider geïmplementeerd. De volgende code is echter de standaard implementatie van [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Query's uitvoeren op onderliggende items

Als u wilt controleren of onderliggende items bestaan op het opgegeven pad, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) overschrijven. Deze methode retourneert `true` of het item onderliggende items heeft en `false` anders. Voor een pad dat null of leeg is, houdt de methode in dat alle items in het gegevens archief kinderen en retour neren `true` .

Dit is de onderdrukking voor de methode [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . Als er meer dan twee padcomponenten zijn die door de ChunkPath-helper-methode worden gemaakt, retourneert de methode `false` , omdat er alleen een database container en een tabel container zijn gedefinieerd. Zie voor meer informatie over deze Help-methode de methode ChunkPath wordt besproken in [een Windows Power shell-item provider maken](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="1094-1097":::

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Wat u moet weten over implementatie van HasChildItems

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Als de container provider een hoofdmap aanbiedt die interessante koppel punten bevat, moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) `true` worden geretourneerd wanneer een null-of lege teken reeks wordt door gegeven voor het pad.

## <a name="copying-items"></a>Items kopiëren

Voor het kopiëren van items moet de container provider [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) -methode implementeren ter ondersteuning van aanroepen van de `Copy-Item` cmdlet. Met deze methode wordt een gegevens item gekopieerd van de locatie die wordt aangegeven door de `path` para meter van de cmdlet naar de locatie die wordt aangegeven door de `copyPath` para meter. Als de `recurse` para meter is opgegeven, kopieert de methode alle subcontainers. Als de para meter niet is opgegeven, wordt slechts één niveau van items gekopieerd met de methode.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Wat u moet weten over implementatie van CopyItem

De volgende voor waarden zijn mogelijk van toepassing op uw implementatie van [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Bij het definiëren van de provider klasse kan een Windows Power shell-container provider provider mogelijkheden van ExpandWildcards declareren, filteren, opnemen of uitsluiten van de inventarisatie van [System. Management. Automation. provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In deze gevallen moet de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ervoor zorgen dat het pad dat wordt door gegeven aan de methode voldoet aan de vereisten van de opgegeven mogelijkheden. Hiervoor moet de methode toegang krijgen tot de juiste eigenschap, bijvoorbeeld de eigenschappen [System. Management. Automation. provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) en [System. Management. Automation. provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Standaard moeten onderdrukkingen van deze methode geen objecten kopiëren over bestaande objecten tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . De provider van het bestands systeem kopieert bijvoorbeeld niet c:\temp\abc.txt over een bestaand c:\abc.txt bestand, tenzij de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) is ingesteld op `true` . Als het pad dat is opgegeven in de `copyPath` para meter bestaat en een container aangeeft, is de eigenschap [System. Management. Automation. provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) niet vereist. In dit geval moet [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) het item dat door de para meter wordt aangegeven, kopiëren `path` naar de container die door de `copyPath` para meter als onderliggend is aangeduid.

- Uw implementatie van [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) is verantwoordelijk voor het voor komen van oneindige recursie wanneer er circulaire koppelingen zijn en het soort gelijke. Er moet een geschikte afsluit uitzondering worden gegenereerd om een dergelijke voor waarde weer te geven.

- Uw implementatie van de methode [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) moet [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aanroepen en de geretourneerde waarde controleren voordat wijzigingen in het gegevens archief worden aangebracht. Nadat het aanroepen van [System. Management. Automation. provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) is ingesteld op True, moet de methode [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) de methode [System. Management. Automation. provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) aanroepen als een extra controle op mogelijk schadelijke systeem wijzigingen. Zie [items van een andere naam wijzigen](#renaming-items)voor meer informatie over het aanroepen van deze methoden.

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Dynamische para meters aan de Copy-Item-cmdlet koppelen

Soms `Copy-Item` vereist de cmdlet extra para meters die dynamisch worden opgegeven tijdens runtime. Als u deze dynamische para meters wilt opgeven, moet de Windows Power shell-container provider de methode [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) implementeren om deze para meters af te handelen. Met deze methode worden de para meters voor het item op het aangegeven pad opgehaald en wordt een object geretourneerd dat eigenschappen en velden bevat met kenmerken die vergelijkbaar zijn met een cmdlet-klasse of een [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -object. De Windows Power shell-runtime maakt gebruik van het geretourneerde object om de para meters toe te voegen aan de `Copy-Item` cmdlet.

Deze provider implementeert deze methode niet. De volgende code is echter de standaard implementatie van [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Code voorbeeld

Zie [AccessDbProviderSample04 code sample](./accessdbprovidersample04-code-sample.md)voor een volledige voorbeeld code.

## <a name="building-the-windows-powershell-provider"></a>De Windows Power shell-provider bouwen

Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>De Windows Power shell-provider testen

Wanneer uw Windows Power shell-provider is geregistreerd bij Windows Power shell, kunt u deze testen door de ondersteunde cmdlets uit te voeren op de opdracht regel. Houd er rekening mee dat de volgende voorbeeld uitvoer een fictieve Access-data base gebruikt.

1. Voer de `Get-ChildItem` cmdlet uit om de lijst met onderliggende items uit een tabel klanten in de Access-Data Base op te halen.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   De volgende uitvoer wordt weer gegeven.

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

2. Voer de `Get-ChildItem` cmdlet opnieuw uit om de gegevens van een tabel op te halen.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   De volgende uitvoer wordt weer gegeven.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Gebruik nu de `Get-Item` cmdlet om de items op rij 0 op te halen in de gegevens tabel.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   De volgende uitvoer wordt weer gegeven.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Hergebruiken `Get-Item` om de gegevens voor de items in rij 0 op te halen.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   De volgende uitvoer wordt weer gegeven.

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

5. Gebruik nu de `New-Item` cmdlet om een rij toe te voegen aan een bestaande tabel. Met de `Path` para meter wordt het volledige pad naar de rij opgegeven en moet het rijnummer worden aangegeven dat groter is dan het bestaande aantal rijen in de tabel. De `Type` para meter geeft aan dat het type item moet worden toegevoegd.
   Ten slotte `Value` specificeert de para meter een door komma's gescheiden lijst met kolom waarden voor de rij.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Controleer als volgt of de bewerking voor het nieuwe item juist is.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   De volgende uitvoer wordt weer gegeven.

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

[Windows Power shell-providers maken](./how-to-create-a-windows-powershell-provider.md)

[Uw Windows PowerShell-provider ontwerpen](./designing-your-windows-powershell-provider.md)

[Een Windows Power shell-provider voor het implementeren van een item](./creating-a-windows-powershell-item-provider.md)

[Een Windows Power shell-provider voor navigatie implementeren](./creating-a-windows-powershell-navigation-provider.md)

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)
