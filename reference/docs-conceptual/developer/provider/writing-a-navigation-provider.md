---
title: Een navigatie provider schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352323"
---
# <a name="writing-a-navigation-provider"></a>Een navigatieprovider schrijven

In dit onderwerp wordt beschreven hoe u de methoden van een Windows Power shell-provider implementeert die ondersteuning bieden voor geneste containers (gegevens archieven met meerdere niveaus), verplaatsen van items en relatieve paden. Een navigatie provider moet zijn afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

De provider in de voor beelden in dit onderwerp gebruikt een Access-Data Base als gegevens archief. Er zijn verschillende hulp methoden en klassen die worden gebruikt voor interactie met de-data base. Zie [AccessDBProviderSample05](./accessdbprovidersample05.md)voor het volledige voor beeld dat de Help-methoden bevat.

Zie [Windows Power shell provider Overview](./windows-powershell-provider-overview.md)(Engelstalig) voor meer informatie over Windows Power shell-providers.

## <a name="implementing-navigation-methods"></a>Navigatie methoden implementeren

De klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implementeert methoden die ondersteuning bieden voor geneste containers, relatieve paden en het verplaatsen van items. Zie [NavigationCmdletProvider-methoden](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods)voor een volledige lijst van deze methoden.

> [!NOTE]
> Dit onderwerp is gebaseerd op de informatie in de Quick Start van de [Windows Power shell-provider](./windows-powershell-provider-quickstart.md). Dit onderwerp heeft geen betrekking op de basis beginselen van het instellen van een provider project of het implementeren van de methoden die zijn overgenomen van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) die stations maken en verwijderen. In dit onderwerp wordt ook beschreven hoe u methoden implementeert die worden weer gegeven door de klassen [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) of [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Zie [een item provider schrijven](./writing-an-item-provider.md)voor een voor beeld waarin wordt getoond hoe u cmdlets voor items implementeert. Zie [een container provider schrijven](./writing-a-container-provider.md)voor een voor beeld waarin wordt getoond hoe u container-cmdlets implementeert.

### <a name="declaring-the-provider-class"></a>De provider klasse declareren

Declareer de provider die moet worden afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) en verdecoreer deze met [System. Management. Automation. provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>IsItemContainer implementeren

Met de methode [System. Management. Automation. provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) wordt gecontroleerd of het item op het opgegeven pad een container is.

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

### <a name="implementing-getchildname"></a>GetChildName implementeren

De methode [System. Management. Automation. provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) haalt de eigenschap name van het onderliggende item op het opgegeven pad op. Als het item op het opgegeven pad geen onderliggend element van een container is, moet deze methode het pad retour neren.

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

### <a name="implementing-getparentpath"></a>GetParentPath implementeren

Met de methode [System. Management. Automation. provider. Navigationcmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) wordt het pad naar het bovenliggende item van het opgegeven pad opgehaald. Als het item op het opgegeven pad de hoofdmap is van het gegevens archief (zodat het geen bovenliggend pad heeft), zou deze methode het hoofdpad moeten retour neren.

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

### <a name="implementing-makepath"></a>MakePath implementeren

De methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) wordt toegevoegd aan een opgegeven bovenliggend pad en een opgegeven onderliggend pad voor het maken van een provider-intern pad (Zie voor informatie over typen paden die providers kunnen ondersteunen [Overzicht van Windows Power shell-provider](./windows-powershell-provider-overview.md). De Power shell-engine roept deze methode aan wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) aanroept.

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

### <a name="implementing-normalizerelativepath"></a>NormalizeRelativePath implementeren

De methode [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) neemt `path`-en `basepath`-para meters en retourneert een genormaliseerd pad dat gelijk is aan de `path` para meter en ten opzichte van de `basepath` bepaalde.

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

### <a name="implementing-moveitem"></a>MoveItem implementeren

Met de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) wordt een item uit het opgegeven pad verplaatst naar het opgegeven doelpad. De Power shell-engine roept deze methode aan wanneer een gebruiker de cmdlet [micro soft. Power shell. commands. MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) aanroept.

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

## <a name="see-also"></a>Zie ook

[Een container provider schrijven](./writing-a-container-provider.md)

[Overzicht van Windows Power shell-provider](./windows-powershell-provider-overview.md)