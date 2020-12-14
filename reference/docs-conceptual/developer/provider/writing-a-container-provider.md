---
ms.date: 09/13/2016
ms.topic: reference
title: Een containerprovider schrijven
description: Een containerprovider schrijven
ms.openlocfilehash: 17ec3e11258ee77a8e569df1af3a0e9bcd9798b6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93354929"
---
# <a name="writing-a-container-provider"></a><span data-ttu-id="f26fd-103">Een containerprovider schrijven</span><span class="sxs-lookup"><span data-stu-id="f26fd-103">Writing a container provider</span></span>

<span data-ttu-id="f26fd-104">In dit onderwerp wordt beschreven hoe u de methoden van een Windows Power shell-provider implementeert die ondersteuning bieden voor items die andere items bevatten, zoals mappen in de bestandssysteem provider.</span><span class="sxs-lookup"><span data-stu-id="f26fd-104">This topic describes how to implement the methods of a Windows PowerShell provider that support items that contain other items, such as folders in the file system provider.</span></span> <span data-ttu-id="f26fd-105">Om containers te kunnen ondersteunen, moet een provider zijn afgeleid van de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="f26fd-105">To be able to support containers, a provider must derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

<span data-ttu-id="f26fd-106">De provider in de voor beelden in dit onderwerp gebruikt een Access-Data Base als gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="f26fd-106">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="f26fd-107">Er zijn verschillende hulp methoden en klassen die worden gebruikt voor interactie met de-data base.</span><span class="sxs-lookup"><span data-stu-id="f26fd-107">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="f26fd-108">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md)voor het volledige voor beeld dat de Help-methoden bevat.</span><span class="sxs-lookup"><span data-stu-id="f26fd-108">For the complete sample that includes the helper methods, see [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>

<span data-ttu-id="f26fd-109">Zie [Windows Power shell provider Overview](./windows-powershell-provider-overview.md)(Engelstalig) voor meer informatie over Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="f26fd-109">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-container-methods"></a><span data-ttu-id="f26fd-110">Container methoden implementeren</span><span class="sxs-lookup"><span data-stu-id="f26fd-110">Implementing container methods</span></span>

<span data-ttu-id="f26fd-111">De klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) implementeert methoden die ondersteuning bieden voor containers en maken, kopiëren en verwijderen van items.</span><span class="sxs-lookup"><span data-stu-id="f26fd-111">The [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class implements methods that support containers, and create, copy, and remove items.</span></span> <span data-ttu-id="f26fd-112">Zie [System. Management. Automation. provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider#methods)voor een volledige lijst van deze methoden.</span><span class="sxs-lookup"><span data-stu-id="f26fd-112">For a complete list of these methods, see [System.Management.Automation.Provider.ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="f26fd-113">Dit onderwerp is gebaseerd op de informatie in de Quick Start van de [Windows Power shell-provider](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="f26fd-113">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="f26fd-114">Dit onderwerp heeft geen betrekking op de basis beginselen van het instellen van een provider project of het implementeren van de methoden die zijn overgenomen van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) die stations maken en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f26fd-114">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="f26fd-115">In dit onderwerp wordt ook beschreven hoe u methoden implementeert die worden weer gegeven door de klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="f26fd-115">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="f26fd-116">Zie [een item provider schrijven](./writing-an-item-provider.md)voor een voor beeld waarin wordt getoond hoe u cmdlets voor items implementeert.</span><span class="sxs-lookup"><span data-stu-id="f26fd-116">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="f26fd-117">De provider klasse declareren</span><span class="sxs-lookup"><span data-stu-id="f26fd-117">Declaring the provider class</span></span>

<span data-ttu-id="f26fd-118">Declareer de provider die moet worden afgeleid van de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) en verdecoreer deze met [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="f26fd-118">Declare the provider to derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
   {

   }
```

### <a name="implementing-getchilditems"></a><span data-ttu-id="f26fd-119">GetChildItems implementeren</span><span class="sxs-lookup"><span data-stu-id="f26fd-119">Implementing GetChildItems</span></span>

<span data-ttu-id="f26fd-120">De Power shell-engine roept de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) aan wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. GetChildItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.Getchilditemcommand) aanroept.</span><span class="sxs-lookup"><span data-stu-id="f26fd-120">The PowerShell engine calls the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method when a user calls the [Microsoft.PowerShell.Commands.GetChildItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.Getchilditemcommand) cmdlet.</span></span> <span data-ttu-id="f26fd-121">Met deze methode worden de items opgehaald die de onderliggende elementen zijn van het item op het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="f26fd-121">This method gets the items that are the children of the item at the specified path.</span></span>

<span data-ttu-id="f26fd-122">In het voor beeld van de Access-Data Base is het gedrag van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) afhankelijk van het type van het opgegeven item.</span><span class="sxs-lookup"><span data-stu-id="f26fd-122">In the Access database example, the behavior of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method depends on the type of the specified item.</span></span> <span data-ttu-id="f26fd-123">Als het item het station is, zijn de onderliggende tabellen en de methode retourneert de set tabellen uit de data base.</span><span class="sxs-lookup"><span data-stu-id="f26fd-123">If the item is the drive, then the children are tables, and the method returns the set of tables from the database.</span></span> <span data-ttu-id="f26fd-124">Als het opgegeven item een tabel is, zijn de onderliggende items de rijen van die tabel.</span><span class="sxs-lookup"><span data-stu-id="f26fd-124">If the specified item is a table, then the children are the rows of that table.</span></span> <span data-ttu-id="f26fd-125">Als het item een rij is, zijn er geen onderliggende items en retourneert de methode die rij alleen.</span><span class="sxs-lookup"><span data-stu-id="f26fd-125">If the item is a row, then it has no children, and the method returns that row only.</span></span> <span data-ttu-id="f26fd-126">Alle onderliggende items worden teruggestuurd naar de Power shell-Engine door de methode [System. Management. Automation. provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .</span><span class="sxs-lookup"><span data-stu-id="f26fd-126">All child items are sent back to the PowerShell engine by the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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
       }
```

### <a name="implementing-getchildnames"></a><span data-ttu-id="f26fd-127">GetChildNames implementeren</span><span class="sxs-lookup"><span data-stu-id="f26fd-127">Implementing GetChildNames</span></span>

<span data-ttu-id="f26fd-128">De methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) is vergelijkbaar met de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) , behalve dat hiermee alleen de eigenschap name van de items wordt geretourneerd en niet de items zelf.</span><span class="sxs-lookup"><span data-stu-id="f26fd-128">The [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method is similar to the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method, except that it returns only the name property of the items, and not the items themselves.</span></span>

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
       }
```

### <a name="implementing-newitem"></a><span data-ttu-id="f26fd-129">NewItem mag implementeren</span><span class="sxs-lookup"><span data-stu-id="f26fd-129">Implementing NewItem</span></span>

<span data-ttu-id="f26fd-130">De methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) maakt een nieuw item van het opgegeven type op het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="f26fd-130">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method creates a new item of the specified type at the specified path.</span></span> <span data-ttu-id="f26fd-131">De Power shell-engine roept deze methode aan wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. NewItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.newitemcommand) aanroept.</span><span class="sxs-lookup"><span data-stu-id="f26fd-131">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.NewItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.newitemcommand) cmdlet.</span></span>

<span data-ttu-id="f26fd-132">In dit voor beeld implementeert de methode logica om te bepalen of het pad en het type overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="f26fd-132">In this example, the method implements logic to determine that the path and type match.</span></span> <span data-ttu-id="f26fd-133">Dat wil zeggen dat alleen een tabel direct onder het station (de data base) kan worden gemaakt en dat er alleen een rij kan worden gemaakt onder een tabel.</span><span class="sxs-lookup"><span data-stu-id="f26fd-133">That is, only a table can be created directly under the drive (the database), and only a row can be created under a table.</span></span> <span data-ttu-id="f26fd-134">Als het opgegeven pad en item type niet op deze manier overeenkomen, genereert de methode een uitzonde ring.</span><span class="sxs-lookup"><span data-stu-id="f26fd-134">If the specified path and item type don't match in this way, the method throws an exception.</span></span>

```csharp
protected override void NewItem(string path, string type,
                                   object newItemValue)
       {
           string tableName;
           int rowNumber;

           PathType pt = GetNamesFromPath(path, out tableName, out rowNumber);

           if (pt == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           // Check if type is either "table" or "row", if not throw an
           // exception
           if (!String.Equals(type, "table", StringComparison.OrdinalIgnoreCase)
               && !String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
           {
               WriteError(new ErrorRecord
                                 (new ArgumentException("Type must be either a table or row"),
                                     "CannotCreateSpecifiedObject",
                                        ErrorCategory.InvalidArgument,
                                             path
                                  )
                         );

               throw new ArgumentException("This provider can only create items of type \"table\" or \"row\"");
           }

           // Path type is the type of path of the container. So if a drive
           // is specified, then a table can be created under it and if a table
           // is specified, then a row can be created under it. For the sake of
           // completeness, if a row is specified, then if the row specified by
           // the path does not exist, a new row is created. However, the row
           // number may not match as the row numbers only get incremented based
           // on the number of rows

           if (PathIsDrive(path))
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   // Execute command using ODBC connection to create a table
                   try
                   {
                       // create the table using an sql statement
                       string newTableName = newItemValue.ToString();

                       if (!TableNameIsValid(newTableName))
                       {
                           return;
                       }
                       string sql = "create table " + newTableName
                                            + " (ID INT)";

                       // Create the table using the Odbc connection from the
                       // drive.
                       AccessDBPSDriveInfo di = this.PSDriveInfo as AccessDBPSDriveInfo;

                       if (di == null)
                       {
                           return;
                       }
                       OdbcConnection connection = di.Connection;

                       if (ShouldProcess(newTableName, "create"))
                       {
                           OdbcCommand cmd = new OdbcCommand(sql, connection);
                           cmd.ExecuteScalar();
                       }
                   }
                   catch (Exception ex)
                   {
                       WriteError(new ErrorRecord(ex, "CannotCreateSpecifiedTable",
                                 ErrorCategory.InvalidOperation, path)
                                 );
                   }
               } // if (String...
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   throw new
                       ArgumentException("A row cannot be created under a database, specify a path that represents a Table");
               }
           }// if (PathIsDrive...
           else
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   if (rowNumber < 0)
                   {
                       throw new
                           ArgumentException("A table cannot be created within another table, specify a path that represents a database");
                   }
                   else
                   {
                       throw new
                           ArgumentException("A table cannot be created inside a row, specify a path that represents a database");
                   }
               } //if (String.Equals....
               // if path specified is a row, create a new row
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   // The user is required to specify the values to be inserted
                   // into the table in a single string separated by commas
                   string value = newItemValue as string;

                   if (String.IsNullOrEmpty(value))
                   {
                       throw new
                           ArgumentException("Value argument must have comma separated values of each column in a row");
                   }
                   string[] rowValues = value.Split(',');

                   OdbcDataAdapter da = GetAdapterForTable(tableName);

                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   if (rowValues.Length != table.Columns.Count)
                   {
                       string message =
                            String.Format(CultureInfo.CurrentCulture,
                                            "The table has {0} columns and the value specified must have so many comma separated values",
                                                table.Columns.Count);

                       throw new ArgumentException(message);
                   }

                   if (!Force && (rowNumber >=0 && rowNumber < table.Rows.Count))
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                                        "The row {0} already exists. To create a new row specify row number as {1}, or specify path to a table, or use the -Force parameter",
                                                            rowNumber, table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   if (rowNumber > table.Rows.Count)
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                            "To create a new row specify row number as {0}, or specify path to a table",
                                                table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   // Create a new row and update the row with the input
                   // provided by the user
                   DataRow row = table.NewRow();
                   for (int i = 0; i < rowValues.Length; i++)
                   {
                       row[i] = rowValues[i];
                   }
                   table.Rows.Add(row);

                   if (ShouldProcess(tableName, "update rows"))
                   {
                       // Update the table from memory back to the data source
                       da.Update(ds, tableName);
                   }

               }// else if (String...
           }// else ...

       }
```

### <a name="implementing-copyitem"></a><span data-ttu-id="f26fd-135">CopyItem implementeren</span><span class="sxs-lookup"><span data-stu-id="f26fd-135">Implementing CopyItem</span></span>

<span data-ttu-id="f26fd-136">De [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) kopieert het opgegeven item naar het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="f26fd-136">The [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) copies the specified item to the specified path.</span></span> <span data-ttu-id="f26fd-137">De Power shell-engine roept deze methode aan wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. CopyItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.copyitemcommand) aanroept.</span><span class="sxs-lookup"><span data-stu-id="f26fd-137">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.CopyItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.copyitemcommand) cmdlet.</span></span> <span data-ttu-id="f26fd-138">Deze methode kan ook recursief zijn, waarbij alle onderliggende items naast het item zelf worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="f26fd-138">This method can also be recursive, copying all of the items children in addition to the item itself.</span></span>

<span data-ttu-id="f26fd-139">Net als de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) voert deze methode een logica uit om ervoor te zorgen dat het opgegeven item van het juiste type is voor het pad waarnaar het wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="f26fd-139">Similarly to the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method, this method performs logic to make sure that the specified item is of the correct type for the path to which it is being copied.</span></span> <span data-ttu-id="f26fd-140">Als het doelpad bijvoorbeeld een tabel is, moet het item dat moet worden gekopieerd een rij zijn.</span><span class="sxs-lookup"><span data-stu-id="f26fd-140">For example, if the destination path is a table, the item to be copied must be a row.</span></span>

```csharp
protected override void CopyItem(string path, string copyPath, bool recurse)
       {
           string tableName, copyTableName;
           int rowNumber, copyRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);
           PathType copyType = GetNamesFromPath(copyPath, out copyTableName, out copyRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(copyPath);
           }

           // Get the table and the table to copy to
           OdbcDataAdapter da = GetAdapterForTable(tableName);
           if (da == null)
           {
               return;
           }

           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           OdbcDataAdapter cda = GetAdapterForTable(copyTableName);
           if (cda == null)
           {
               return;
           }

           DataSet cds = GetDataSetForTable(cda, copyTableName);
           DataTable copyTable = GetDataTable(cds, copyTableName);

           // if source represents a table
           if (type == PathType.Table)
           {
               // if copyPath does not represent a table
               if (copyType != PathType.Table)
               {
                   ArgumentException e = new ArgumentException("Table can only be copied on to another table location");

                   WriteError(new ErrorRecord(e, "PathNotValid",
                       ErrorCategory.InvalidArgument, copyPath));

                   throw e;
               }

               // if table already exists then force parameter should be set
               // to force a copy
               if (!Force && GetTable(copyTableName) != null)
               {
                   throw new ArgumentException("Specified path already exists");
               }

               for (int i = 0; i < table.Rows.Count; i++)
               {
                   DataRow row = table.Rows[i];
                   DataRow copyRow = copyTable.NewRow();

                   copyRow.ItemArray = row.ItemArray;
                   copyTable.Rows.Add(copyRow);
               }
           } // if (type == ...
           // if source represents a row
           else
           {
               if (copyType == PathType.Row)
               {
                   if (!Force && (copyRowNumber < copyTable.Rows.Count))
                   {
                       throw new ArgumentException("Specified path already exists.");
                   }

                   DataRow row = table.Rows[rowNumber];
                   DataRow copyRow = null;

                   if (copyRowNumber < copyTable.Rows.Count)
                   {
                       // copy to an existing row
                       copyRow = copyTable.Rows[copyRowNumber];
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                   }
                   else if (copyRowNumber == copyTable.Rows.Count)
                   {
                       // copy to the next row in the table that will
                       // be created
                       copyRow = copyTable.NewRow();
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                       copyTable.Rows.Add(copyRow);
                   }
                   else
                   {
                       // attempting to copy to a nonexistent row or a row
                       // that cannot be created now - throw an exception
                       string message = String.Format(CultureInfo.CurrentCulture,
                                             "The item cannot be specified to the copied row. Specify row number as {0}, or specify a path to the table.",
                                                    table.Rows.Count);

                       throw new ArgumentException(message);
                   }
               }
               else
               {
                   // destination path specified represents a table,
                   // create a new row and copy the item
                   DataRow copyRow = copyTable.NewRow();
                   copyRow.ItemArray = table.Rows[rowNumber].ItemArray;
                   copyRow[0] = GetNextID(copyTable);
                   copyTable.Rows.Add(copyRow);
               }
           }

           if (ShouldProcess(copyTableName, "CopyItems"))
           {
               cda.Update(cds, copyTableName);
           }

       } //CopyItem
```

### <a name="implementing-removeitem"></a><span data-ttu-id="f26fd-141">Toep assen van RemoveItem</span><span class="sxs-lookup"><span data-stu-id="f26fd-141">Implementing RemoveItem</span></span>

<span data-ttu-id="f26fd-142">Met de methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) wordt het item op het opgegeven pad verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f26fd-142">The [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method removes the item at the specified path.</span></span> <span data-ttu-id="f26fd-143">De Power shell-engine roept deze methode aan wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. RemoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.removeitemcommand) aanroept.</span><span class="sxs-lookup"><span data-stu-id="f26fd-143">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.RemoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.removeitemcommand) cmdlet.</span></span>

```csharp
protected override void RemoveItem(string path, bool recurse)
       {
           string tableName;
           int rowNumber = 0;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               // if recurse flag has been specified, delete all the rows as well
               if (recurse)
               {
                   OdbcDataAdapter da = GetAdapterForTable(tableName);
                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   for (int i = 0; i < table.Rows.Count; i++)
                   {
                       table.Rows[i].Delete();
                   }

                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       da.Update(ds, tableName);
                       RemoveTable(tableName);
                   }
               }//if (recurse...
               else
               {
                   // Remove the table
                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       RemoveTable(tableName);
                   }
               }
           }
           else if (type == PathType.Row)
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               table.Rows[rowNumber].Delete();

               if (ShouldProcess(path, "RemoveItem"))
               {
                   da.Update(ds, tableName);
               }
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

## <a name="next-steps"></a><span data-ttu-id="f26fd-144">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="f26fd-144">Next steps</span></span>

<span data-ttu-id="f26fd-145">Een typische Real-World-provider kan items van het ene naar het andere pad verplaatsen binnen het station.</span><span class="sxs-lookup"><span data-stu-id="f26fd-145">A typical real-world provider is capable of moving items from one path to another within the drive.</span></span>
<span data-ttu-id="f26fd-146">Zie [een navigatie provider schrijven](./writing-a-navigation-provider.md)voor een voor beeld van een provider die het verplaatsen van items ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="f26fd-146">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f26fd-147">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f26fd-147">See Also</span></span>

[<span data-ttu-id="f26fd-148">Een navigatieprovider schrijven</span><span class="sxs-lookup"><span data-stu-id="f26fd-148">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="f26fd-149">Overzicht van Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="f26fd-149">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
