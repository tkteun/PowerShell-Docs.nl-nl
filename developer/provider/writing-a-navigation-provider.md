---
title: Schrijven van een provider navigatie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: f449c17e4c373c42f8a1d96fa9075940111c65bc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056585"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="809ff-102">Een navigatieprovider schrijven</span><span class="sxs-lookup"><span data-stu-id="809ff-102">Writing a navigation provider</span></span>

<span data-ttu-id="809ff-103">In dit onderwerp wordt beschreven hoe u de methoden van een Windows PowerShell-provider die ondersteuning bieden voor geneste containers (met meerdere niveaus gegevensarchieven), het verplaatsen van objecten en relatieve paden te implementeren.</span><span class="sxs-lookup"><span data-stu-id="809ff-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="809ff-104">Een navigatie-provider moet zijn afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="809ff-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="809ff-105">De provider in de voorbeelden in dit onderwerp maakt gebruik van een Access-database als de gegevensopslag.</span><span class="sxs-lookup"><span data-stu-id="809ff-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="809ff-106">Er zijn verschillende methoden en klassen die worden gebruikt om te communiceren met de database.</span><span class="sxs-lookup"><span data-stu-id="809ff-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="809ff-107">Zie voor het complete voorbeeld met de Help-methoden, [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="809ff-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="809ff-108">Zie voor meer informatie over Windows PowerShell-providers, [overzicht van Windows PowerShell-Provider](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="809ff-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="809ff-109">Navigatiemethoden implementeren</span><span class="sxs-lookup"><span data-stu-id="809ff-109">Implementing navigation methods</span></span>

<span data-ttu-id="809ff-110">De [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse implementeert methoden die ondersteuning bieden voor geneste containers, relatieve paden en items verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="809ff-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="809ff-111">Zie voor een volledige lijst van deze methoden, [NavigationCmdletProvider methoden](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="809ff-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="809ff-112">In dit onderwerp bouwt voort op de informatie in [Quick Start Windows PowerShell-Provider](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="809ff-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="809ff-113">In dit onderwerp heeft geen betrekking op de basisprincipes van het instellen van een provider-project, of het implementeren van de methoden die zijn overgenomen van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse die u maakt en schijven verwijderen.</span><span class="sxs-lookup"><span data-stu-id="809ff-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="809ff-114">In dit onderwerp wordt niet beschreven hoe u voor het implementeren van methoden die worden weergegeven door de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) of [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klassen.</span><span class="sxs-lookup"><span data-stu-id="809ff-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="809ff-115">Zie voor een voorbeeld waarin wordt uitgelegd hoe voor het implementeren van de item-cmdlets, [schrijven van een provider item](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="809ff-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="809ff-116">Zie voor een voorbeeld waarin wordt uitgelegd hoe voor het implementeren van container-cmdlets, [schrijven van een provider container](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="809ff-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="809ff-117">De providerklasse declareren</span><span class="sxs-lookup"><span data-stu-id="809ff-117">Declaring the provider class</span></span>

<span data-ttu-id="809ff-118">Declareer de provider worden afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse en opmaken met de [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="809ff-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="809ff-119">IsItemContainer implementeren</span><span class="sxs-lookup"><span data-stu-id="809ff-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="809ff-120">De [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) methode controleert of het item in het opgegeven pad een container is.</span><span class="sxs-lookup"><span data-stu-id="809ff-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a><span data-ttu-id="809ff-121">GetChildName implementeren</span><span class="sxs-lookup"><span data-stu-id="809ff-121">Implementing GetChildName</span></span>

<span data-ttu-id="809ff-122">De [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) methode haalt de naameigenschap van het onderliggende item in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="809ff-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="809ff-123">Als het item in het opgegeven pad geen onderliggende site van een container is, moet het pad geretourneerd door deze methode.</span><span class="sxs-lookup"><span data-stu-id="809ff-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a><span data-ttu-id="809ff-124">GetParentPath implementeren</span><span class="sxs-lookup"><span data-stu-id="809ff-124">Implementing GetParentPath</span></span>

<span data-ttu-id="809ff-125">De [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) methode haalt u het pad van het bovenliggende item van het item in het opgegeven pad.</span><span class="sxs-lookup"><span data-stu-id="809ff-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="809ff-126">Als het item in het opgegeven pad is de hoofdmap van het gegevensarchief (zodat er geen bovenliggende), moet deze methode pad naar de hoofdmap retourneren.</span><span class="sxs-lookup"><span data-stu-id="809ff-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a><span data-ttu-id="809ff-127">MakePath implementeren</span><span class="sxs-lookup"><span data-stu-id="809ff-127">Implementing MakePath</span></span>

<span data-ttu-id="809ff-128">De [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) methode lid wordt van een opgegeven bovenliggende pad en een pad opgegeven onderliggende voor het maken van een provider interne pad (voor informatie over het pad van het type dat providers kan ondersteunen, Zie [overzicht van Windows PowerShell-Provider](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="809ff-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="809ff-129">De PowerShell-engine roept deze methode wanneer een gebruiker roept de [Microsoft.PowerShell.Commands.Join-Path](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="809ff-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.Join-Path](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span></span>

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="809ff-130">Implementing NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="809ff-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="809ff-131">De [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) methode duurt `path` en `basepath` parameters, en retourneert een genormaliseerde pad die gelijk is aan de `path`parameter en ten opzichte van de `basepath` parameter.</span><span class="sxs-lookup"><span data-stu-id="809ff-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a><span data-ttu-id="809ff-132">MoveItem implementeren</span><span class="sxs-lookup"><span data-stu-id="809ff-132">Implementing MoveItem</span></span>

<span data-ttu-id="809ff-133">De [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) methode verplaatst u een item uit het opgegeven pad naar het opgegeven doelpad.</span><span class="sxs-lookup"><span data-stu-id="809ff-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="809ff-134">De PowerShell-engine roept deze methode wanneer een gebruiker roept de [Microsoft.PowerShell.Commands.Move-Item](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="809ff-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.Move-Item](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span></span>

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a><span data-ttu-id="809ff-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="809ff-135">See Also</span></span>

[<span data-ttu-id="809ff-136">Schrijven van een container-provider</span><span class="sxs-lookup"><span data-stu-id="809ff-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="809ff-137">Overzicht van Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="809ff-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)