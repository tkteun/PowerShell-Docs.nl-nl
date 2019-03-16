---
title: Schrijven van een provider artikel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058183"
---
# <a name="writing-an-item-provider"></a>Een itemprovider schrijven

Dit onderwerp wordt beschreven hoe u voor het implementeren van de methoden van een Windows PowerShell-provider die openen en te bewerken van items in het gegevensarchief. Als u voor toegang tot items, een provider moet zijn afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse.

De provider in de voorbeelden in dit onderwerp maakt gebruik van een Access-database als de gegevensopslag. Er zijn verschillende methoden en klassen die worden gebruikt om te communiceren met de database. Zie voor het complete voorbeeld met de Help-methoden, [AccessDBProviderSample03](./accessdbprovidersample03.md)

Zie voor meer informatie over Windows PowerShell-providers, [overzicht van Windows PowerShell-Provider](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementeren van item methoden

De [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse beschrijft de verschillende methoden die kunnen worden gebruikt voor toegang tot en manipuleren van de items in een gegevensarchief. Zie voor een volledige lijst van deze methoden, [ItemCmdletProvider methoden](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx). In dit voorbeeld zullen we vier van deze methoden implementeren. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) opgehaald van een item in een opgegeven pad. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) stelt de waarde van het opgegeven item. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) wordt gecontroleerd of er een item in het opgegeven pad bestaat. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) controleert of een pad om te zien als het wordt toegewezen aan een locatie in het gegevensarchief.

> [!NOTE]
> In dit onderwerp bouwt voort op de informatie in [Quick Start Windows PowerShell-Provider](./windows-powershell-provider-quickstart.md). In dit onderwerp heeft geen betrekking op de basisprincipes van het instellen van een provider-project, of het implementeren van de methoden die zijn overgenomen van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse die u maakt en schijven verwijderen.

### <a name="declaring-the-provider-class"></a>De providerklasse declareren

Declareer de provider worden afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse en opmaken met de [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>GetItem implementeren

De [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) door de PowerShell-engine wordt aangeroepen wanneer een gebruiker roept de [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet uit op uw de provider. De methode retourneert het item in het opgegeven pad. In het voorbeeld van de database toegang met de methode gecontroleerd of het item het station zelf, een tabel in de database, of een rij in de database wordt. De methode verzendt het item naar de PowerShell-engine door het aanroepen van de [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) methode.

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>SetItem implementeren

De [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methode wordt aangeroepen door het aanroepen van de PowerShell-engine als een gebruiker roept de [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet . De waarde van het item wordt ingesteld op het opgegeven pad.

In het voorbeeld van de database toegang tot het verstandig om de waarde van een item alleen als dit item een rij is, genereert de methode [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) wanneer het item is niet een rij.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>ItemExists implementeren

De [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) methode wordt aangeroepen door de PowerShell-engine als een gebruiker roept de [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet. De methode bepaalt of er een item in het opgegeven pad is. Als het item bestaat, de methode geeft deze terug naar de PowerShell-engine door het aanroepen van [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>IsValidPath implementeren

De [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) methode wordt gecontroleerd of het opgegeven pad een ongeldige syntaxis voor de huidige provider is. Er wordt niet gecontroleerd of een item in het pad bestaat.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Volgende stappen

Een typische real-world-provider is kan ondersteunen van items die andere items bevatten, en van het verplaatsen van items uit een pad naar de andere in het station. Zie voor een voorbeeld van een provider die ondersteuning biedt voor containers, [schrijven van een provider container](./writing-a-container-provider.md). Zie voor een voorbeeld van een provider die ondersteuning biedt voor items verplaatsen [schrijven van een provider navigatie](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Zie ook

[Schrijven van een container-provider](./writing-a-container-provider.md)

[Schrijven van een provider navigatie](./writing-a-navigation-provider.md)

[Overzicht van Windows PowerShell-Provider](./windows-powershell-provider-overview.md)