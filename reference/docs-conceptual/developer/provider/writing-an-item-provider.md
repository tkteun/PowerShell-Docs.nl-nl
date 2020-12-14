---
ms.date: 09/13/2016
ms.topic: reference
title: Een itemprovider schrijven
description: Een itemprovider schrijven
ms.openlocfilehash: f70c6ee50277988c4e3b7c255dc4548bc30319dd
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355201"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="ba062-103">Een itemprovider schrijven</span><span class="sxs-lookup"><span data-stu-id="ba062-103">Writing an item provider</span></span>

<span data-ttu-id="ba062-104">In dit onderwerp wordt beschreven hoe u de methoden van een Windows Power shell-provider implementeert waarmee items in het gegevens archief worden geopend en gemanipuleerd.</span><span class="sxs-lookup"><span data-stu-id="ba062-104">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="ba062-105">Om toegang te kunnen krijgen tot items, moet een provider zijn afgeleid van de klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="ba062-105">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="ba062-106">De provider in de voor beelden in dit onderwerp gebruikt een Access-Data Base als gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="ba062-106">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="ba062-107">Er zijn verschillende hulp methoden en klassen die worden gebruikt voor interactie met de-data base.</span><span class="sxs-lookup"><span data-stu-id="ba062-107">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="ba062-108">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md) voor het volledige voor beeld dat de Help-methoden bevat.</span><span class="sxs-lookup"><span data-stu-id="ba062-108">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="ba062-109">Zie [Windows Power shell provider Overview](./windows-powershell-provider-overview.md)(Engelstalig) voor meer informatie over Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="ba062-109">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="ba062-110">Artikel methoden implementeren</span><span class="sxs-lookup"><span data-stu-id="ba062-110">Implementing item methods</span></span>

<span data-ttu-id="ba062-111">De klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) biedt verschillende methoden die kunnen worden gebruikt voor toegang tot en het bewerken van de items in een gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="ba062-111">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span>
<span data-ttu-id="ba062-112">Zie [ItemCmdletProvider-methoden](/dotnet/api/system.management.automation.provider.itemcmdletprovider#methods)voor een volledige lijst van deze methoden.</span><span class="sxs-lookup"><span data-stu-id="ba062-112">For a complete list of these methods, see [ItemCmdletProvider Methods](/dotnet/api/system.management.automation.provider.itemcmdletprovider#methods).</span></span>
<span data-ttu-id="ba062-113">In dit voor beeld worden vier van deze methoden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="ba062-113">In this example, we will implement four of these methods.</span></span>
<span data-ttu-id="ba062-114">[System. Management. Automation. provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) haalt een item op in een opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="ba062-114">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span>
<span data-ttu-id="ba062-115">[System. Management. Automation. provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) stelt de waarde van het opgegeven item in.</span><span class="sxs-lookup"><span data-stu-id="ba062-115">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span>
<span data-ttu-id="ba062-116">[System. Management. Automation. provider. Itemcmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) controleert of een item bestaat op het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="ba062-116">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span>
<span data-ttu-id="ba062-117">[System. Management. Automation. provider. Itemcmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) controleert een pad om te zien of het is toegewezen aan een locatie in het gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="ba062-117">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="ba062-118">Dit onderwerp is gebaseerd op de informatie in de Quick Start van de [Windows Power shell-provider](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="ba062-118">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="ba062-119">Dit onderwerp heeft geen betrekking op de basis beginselen van het instellen van een provider project of het implementeren van de methoden die zijn overgenomen van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) die stations maken en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ba062-119">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="ba062-120">De provider klasse declareren</span><span class="sxs-lookup"><span data-stu-id="ba062-120">Declaring the provider class</span></span>

<span data-ttu-id="ba062-121">Declareer de provider die moet worden afgeleid van de klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) en verdecoreer deze met [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="ba062-121">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="ba062-122">GetItem implementeren</span><span class="sxs-lookup"><span data-stu-id="ba062-122">Implementing GetItem</span></span>

<span data-ttu-id="ba062-123">[System. Management. Automation. provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) wordt aangeroepen door de Power shell-engine wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) aanroept voor uw provider.</span><span class="sxs-lookup"><span data-stu-id="ba062-123">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet on your provider.</span></span> <span data-ttu-id="ba062-124">De methode retourneert het item op het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="ba062-124">The method returns the item at the specified path.</span></span> <span data-ttu-id="ba062-125">In het voor beeld van de Access-Data Base controleert de methode of het item het station zelf is, een tabel in de data base of een rij in de-data base.</span><span class="sxs-lookup"><span data-stu-id="ba062-125">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="ba062-126">De methode verzendt het item naar de Power shell-Engine door de methode [System. Management. Automation. provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="ba062-126">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="ba062-127">SetItem implementeren</span><span class="sxs-lookup"><span data-stu-id="ba062-127">Implementing SetItem</span></span>

<span data-ttu-id="ba062-128">De methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) wordt aangeroepen door de Power shell-engine aanroepen wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) aanroept.</span><span class="sxs-lookup"><span data-stu-id="ba062-128">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) cmdlet.</span></span> <span data-ttu-id="ba062-129">De waarde van het item wordt ingesteld op het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="ba062-129">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="ba062-130">In het voor beeld van de Access-Data Base is het zinvol om de waarde van een item in te stellen als dat item een rij is, waardoor de methode [NotSupportedException](/dotnet/api/system.notsupportedexception) genereert wanneer het item geen rij is.</span><span class="sxs-lookup"><span data-stu-id="ba062-130">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](/dotnet/api/system.notsupportedexception) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="ba062-131">ItemExists implementeren</span><span class="sxs-lookup"><span data-stu-id="ba062-131">Implementing ItemExists</span></span>

<span data-ttu-id="ba062-132">De methode [System. Management. Automation. provider. Itemcmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) wordt aangeroepen door de Power shell-engine wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) aanroept.</span><span class="sxs-lookup"><span data-stu-id="ba062-132">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) cmdlet.</span></span> <span data-ttu-id="ba062-133">De methode bepaalt of er een item op het opgegeven pad aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="ba062-133">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="ba062-134">Als het item bestaat, wordt dit door de-methode aan de Power shell-Engine door gegeven door [System. Management. Automation. provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="ba062-134">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="ba062-135">IsValidPath implementeren</span><span class="sxs-lookup"><span data-stu-id="ba062-135">Implementing IsValidPath</span></span>

<span data-ttu-id="ba062-136">Met de methode [System. Management. Automation. provider. Itemcmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) wordt gecontroleerd of het opgegeven pad syntactisch geldig is voor de huidige provider.</span><span class="sxs-lookup"><span data-stu-id="ba062-136">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="ba062-137">Er wordt niet gecontroleerd of een item op het pad bestaat.</span><span class="sxs-lookup"><span data-stu-id="ba062-137">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="ba062-138">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="ba062-138">Next steps</span></span>

<span data-ttu-id="ba062-139">Een typische Real-World-provider is in staat om items te ondersteunen die andere items bevatten en van het verplaatsen van items van het ene pad naar het andere in het station.</span><span class="sxs-lookup"><span data-stu-id="ba062-139">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="ba062-140">Zie [een container provider schrijven](./writing-a-container-provider.md)voor een voor beeld van een provider die containers ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="ba062-140">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="ba062-141">Zie [een navigatie provider schrijven](./writing-a-navigation-provider.md)voor een voor beeld van een provider die het verplaatsen van items ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="ba062-141">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba062-142">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ba062-142">See Also</span></span>

[<span data-ttu-id="ba062-143">Een containerprovider schrijven</span><span class="sxs-lookup"><span data-stu-id="ba062-143">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="ba062-144">Een navigatieprovider schrijven</span><span class="sxs-lookup"><span data-stu-id="ba062-144">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="ba062-145">Overzicht van Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="ba062-145">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
