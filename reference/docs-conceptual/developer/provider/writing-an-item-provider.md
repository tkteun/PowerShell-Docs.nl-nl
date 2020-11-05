---
ms.date: 09/13/2016
ms.topic: reference
title: Een itemprovider schrijven
description: Een itemprovider schrijven
ms.openlocfilehash: f70c6ee50277988c4e3b7c255dc4548bc30319dd
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355201"
---
# <a name="writing-an-item-provider"></a>Een itemprovider schrijven

In dit onderwerp wordt beschreven hoe u de methoden van een Windows Power shell-provider implementeert waarmee items in het gegevens archief worden geopend en gemanipuleerd. Om toegang te kunnen krijgen tot items, moet een provider zijn afgeleid van de klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

De provider in de voor beelden in dit onderwerp gebruikt een Access-Data Base als gegevens archief. Er zijn verschillende hulp methoden en klassen die worden gebruikt voor interactie met de-data base. Zie [AccessDBProviderSample03](./accessdbprovidersample03.md) voor het volledige voor beeld dat de Help-methoden bevat.

Zie [Windows Power shell provider Overview](./windows-powershell-provider-overview.md)(Engelstalig) voor meer informatie over Windows Power shell-providers.

## <a name="implementing-item-methods"></a>Artikel methoden implementeren

De klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) biedt verschillende methoden die kunnen worden gebruikt voor toegang tot en het bewerken van de items in een gegevens archief.
Zie [ItemCmdletProvider-methoden](/dotnet/api/system.management.automation.provider.itemcmdletprovider#methods)voor een volledige lijst van deze methoden.
In dit voor beeld worden vier van deze methoden geïmplementeerd.
[System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) haalt een item op in een opgegeven pad.
[System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) stelt de waarde van het opgegeven item in.
[System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) controleert of een item bestaat op het opgegeven pad.
[System. Management. Automation. provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) controleert een pad om te zien of het is toegewezen aan een locatie in het gegevens archief.

> [!NOTE]
> Dit onderwerp is gebaseerd op de informatie in de Quick Start van de [Windows Power shell-provider](./windows-powershell-provider-quickstart.md). Dit onderwerp heeft geen betrekking op de basis beginselen van het instellen van een provider project of het implementeren van de methoden die zijn overgenomen van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) die stations maken en verwijderen.

### <a name="declaring-the-provider-class"></a>De provider klasse declareren

Declareer de provider die moet worden afgeleid van de klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) en verdecoreer deze met [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>GetItem implementeren

[System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) wordt aangeroepen door de Power shell-engine wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) aanroept voor uw provider. De methode retourneert het item op het opgegeven pad. In het voor beeld van de Access-Data Base controleert de methode of het item het station zelf is, een tabel in de data base of een rij in de-data base. De methode verzendt het item naar de Power shell-Engine door de methode [System. Management. Automation. provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) aan te roepen.

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

De methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) wordt aangeroepen door de Power shell-engine aanroepen wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) aanroept. De waarde van het item wordt ingesteld op het opgegeven pad.

In het voor beeld van de Access-Data Base is het zinvol om de waarde van een item in te stellen als dat item een rij is, waardoor de methode [NotSupportedException](/dotnet/api/system.notsupportedexception) genereert wanneer het item geen rij is.

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

De methode [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) wordt aangeroepen door de Power shell-engine wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) aanroept. De methode bepaalt of er een item op het opgegeven pad aanwezig is. Als het item bestaat, wordt dit door de-methode aan de Power shell-Engine door gegeven door [System. Management. Automation. provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)aan te roepen.

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

Met de methode [System. Management. Automation. provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) wordt gecontroleerd of het opgegeven pad syntactisch geldig is voor de huidige provider. Er wordt niet gecontroleerd of een item op het pad bestaat.

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

Een typische Real-World-provider is in staat om items te ondersteunen die andere items bevatten en van het verplaatsen van items van het ene pad naar het andere in het station. Zie [een container provider schrijven](./writing-a-container-provider.md)voor een voor beeld van een provider die containers ondersteunt. Zie [een navigatie provider schrijven](./writing-a-navigation-provider.md)voor een voor beeld van een provider die het verplaatsen van items ondersteunt.

## <a name="see-also"></a>Zie ook

[Een containerprovider schrijven](./writing-a-container-provider.md)

[Een navigatieprovider schrijven](./writing-a-navigation-provider.md)

[Overzicht van Windows PowerShell-providers](./windows-powershell-provider-overview.md)
