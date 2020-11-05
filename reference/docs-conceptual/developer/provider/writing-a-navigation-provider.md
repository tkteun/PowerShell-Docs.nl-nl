---
ms.date: 09/13/2016
ms.topic: reference
title: Een navigatieprovider schrijven
description: Een navigatieprovider schrijven
ms.openlocfilehash: 3123672d3365c97714557bd0e72a6e444ac228a0
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355218"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="87711-103">Een navigatieprovider schrijven</span><span class="sxs-lookup"><span data-stu-id="87711-103">Writing a navigation provider</span></span>

<span data-ttu-id="87711-104">In dit onderwerp wordt beschreven hoe u de methoden van een Windows Power shell-provider implementeert die ondersteuning bieden voor geneste containers (gegevens archieven met meerdere niveaus), verplaatsen van items en relatieve paden.</span><span class="sxs-lookup"><span data-stu-id="87711-104">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="87711-105">Een navigatie provider moet zijn afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="87711-105">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="87711-106">De provider in de voor beelden in dit onderwerp gebruikt een Access-Data Base als gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="87711-106">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="87711-107">Er zijn verschillende hulp methoden en klassen die worden gebruikt voor interactie met de-data base.</span><span class="sxs-lookup"><span data-stu-id="87711-107">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="87711-108">Zie [AccessDBProviderSample05](./accessdbprovidersample05.md)voor het volledige voor beeld dat de Help-methoden bevat.</span><span class="sxs-lookup"><span data-stu-id="87711-108">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="87711-109">Zie [Windows Power shell provider Overview](./windows-powershell-provider-overview.md)(Engelstalig) voor meer informatie over Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="87711-109">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="87711-110">Navigatie methoden implementeren</span><span class="sxs-lookup"><span data-stu-id="87711-110">Implementing navigation methods</span></span>

<span data-ttu-id="87711-111">De klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implementeert methoden die ondersteuning bieden voor geneste containers, relatieve paden en het verplaatsen van items.</span><span class="sxs-lookup"><span data-stu-id="87711-111">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="87711-112">Zie [NavigationCmdletProvider-methoden](/dotnet/api/system.management.automation.provider.navigationcmdletprovider#methods)voor een volledige lijst van deze methoden.</span><span class="sxs-lookup"><span data-stu-id="87711-112">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="87711-113">Dit onderwerp is gebaseerd op de informatie in de Quick Start van de [Windows Power shell-provider](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="87711-113">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="87711-114">Dit onderwerp heeft geen betrekking op de basis beginselen van het instellen van een provider project of het implementeren van de methoden die zijn overgenomen van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) die stations maken en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="87711-114">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="87711-115">In dit onderwerp wordt ook beschreven hoe u methoden implementeert die worden weer gegeven door de klassen [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) of [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="87711-115">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="87711-116">Zie [een item provider schrijven](./writing-an-item-provider.md)voor een voor beeld waarin wordt getoond hoe u cmdlets voor items implementeert.</span><span class="sxs-lookup"><span data-stu-id="87711-116">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="87711-117">Zie [een container provider schrijven](./writing-a-container-provider.md)voor een voor beeld waarin wordt getoond hoe u container-cmdlets implementeert.</span><span class="sxs-lookup"><span data-stu-id="87711-117">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="87711-118">De provider klasse declareren</span><span class="sxs-lookup"><span data-stu-id="87711-118">Declaring the provider class</span></span>

<span data-ttu-id="87711-119">Declareer de provider die moet worden afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) en verdecoreer deze met [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="87711-119">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="87711-120">IsItemContainer implementeren</span><span class="sxs-lookup"><span data-stu-id="87711-120">Implementing IsItemContainer</span></span>

<span data-ttu-id="87711-121">Met de methode [System. Management. Automation. provider. Navigationcmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) wordt gecontroleerd of het item op het opgegeven pad een container is.</span><span class="sxs-lookup"><span data-stu-id="87711-121">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="87711-122">GetChildName implementeren</span><span class="sxs-lookup"><span data-stu-id="87711-122">Implementing GetChildName</span></span>

<span data-ttu-id="87711-123">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) haalt de eigenschap name van het onderliggende item op het opgegeven pad op.</span><span class="sxs-lookup"><span data-stu-id="87711-123">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="87711-124">Als het item op het opgegeven pad geen onderliggend element van een container is, moet deze methode het pad retour neren.</span><span class="sxs-lookup"><span data-stu-id="87711-124">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="87711-125">GetParentPath implementeren</span><span class="sxs-lookup"><span data-stu-id="87711-125">Implementing GetParentPath</span></span>

<span data-ttu-id="87711-126">Met de methode [System. Management. Automation. provider. Navigationcmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) wordt het pad naar het bovenliggende item van het opgegeven pad opgehaald.</span><span class="sxs-lookup"><span data-stu-id="87711-126">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="87711-127">Als het item op het opgegeven pad de hoofdmap is van het gegevens archief (zodat het geen bovenliggend pad heeft), zou deze methode het hoofdpad moeten retour neren.</span><span class="sxs-lookup"><span data-stu-id="87711-127">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="87711-128">MakePath implementeren</span><span class="sxs-lookup"><span data-stu-id="87711-128">Implementing MakePath</span></span>

<span data-ttu-id="87711-129">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) wordt toegevoegd aan een opgegeven bovenliggend pad en een opgegeven onderliggend pad om een provider-intern pad te maken (Zie [overzicht van Windows Power shell-providers](./windows-powershell-provider-overview.md)voor informatie over padtype die providers kunnen ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="87711-129">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="87711-130">De Power shell-engine roept deze methode aan wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) aanroept.</span><span class="sxs-lookup"><span data-stu-id="87711-130">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="87711-131">NormalizeRelativePath implementeren</span><span class="sxs-lookup"><span data-stu-id="87711-131">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="87711-132">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) accepteert `path` en `basepath` para meters en retourneert een genormaliseerd pad dat gelijk is aan de `path` para meter en ten opzichte van de `basepath` para meter.</span><span class="sxs-lookup"><span data-stu-id="87711-132">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="87711-133">MoveItem implementeren</span><span class="sxs-lookup"><span data-stu-id="87711-133">Implementing MoveItem</span></span>

<span data-ttu-id="87711-134">Met de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) wordt een item uit het opgegeven pad verplaatst naar het opgegeven doelpad.</span><span class="sxs-lookup"><span data-stu-id="87711-134">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="87711-135">De Power shell-engine roept deze methode aan wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) aanroept.</span><span class="sxs-lookup"><span data-stu-id="87711-135">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="87711-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="87711-136">See Also</span></span>

[<span data-ttu-id="87711-137">Een containerprovider schrijven</span><span class="sxs-lookup"><span data-stu-id="87711-137">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="87711-138">Overzicht van Windows PowerShell-providers</span><span class="sxs-lookup"><span data-stu-id="87711-138">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
