---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuratie gegevens gebruiken
description: In dit onderwerp wordt de structuur van de ConfigurationData hashtabel beschreven. Hierdoor kunt u één configuratie maken die kan worden gebruikt voor meerdere knoop punten of voor verschillende omgevingen.
ms.openlocfilehash: aa4a0545aec529dbc923908612d2e1f9e60b3c9c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647110"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="a173e-105">Configuratie gegevens gebruiken in DSC</span><span class="sxs-lookup"><span data-stu-id="a173e-105">Using configuration data in DSC</span></span>

> <span data-ttu-id="a173e-106">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="a173e-106">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a173e-107">Met de ingebouwde DSC **ConfigurationData** para meter kunt u gegevens definiëren die in een configuratie kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a173e-107">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span> <span data-ttu-id="a173e-108">Hierdoor kunt u één configuratie maken die kan worden gebruikt voor meerdere knoop punten of voor verschillende omgevingen.</span><span class="sxs-lookup"><span data-stu-id="a173e-108">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span> <span data-ttu-id="a173e-109">Als u bijvoorbeeld een toepassing ontwikkelt, kunt u een configuratie gebruiken voor zowel ontwikkel-als productie omgevingen en configuratie gegevens gebruiken om gegevens op te geven voor elke omgeving.</span><span class="sxs-lookup"><span data-stu-id="a173e-109">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="a173e-110">In dit onderwerp wordt de structuur van de **ConfigurationData** hashtabel beschreven.</span><span class="sxs-lookup"><span data-stu-id="a173e-110">This topic describes the structure of the **ConfigurationData** hashtable.</span></span> <span data-ttu-id="a173e-111">Zie [configuratie-en omgevings gegevens scheiden](separatingEnvData.md)voor voor beelden van het gebruik van configuratie gegevens.</span><span class="sxs-lookup"><span data-stu-id="a173e-111">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="a173e-112">De algemene para meter ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="a173e-112">The ConfigurationData common parameter</span></span>

<span data-ttu-id="a173e-113">Een DSC-configuratie gebruikt een gemeen schappelijke para meter, **ConfigurationData** , die u opgeeft wanneer u de configuratie compileert.</span><span class="sxs-lookup"><span data-stu-id="a173e-113">A DSC configuration takes a common parameter, **ConfigurationData** , that you specify when you compile the configuration.</span></span> <span data-ttu-id="a173e-114">Zie [DSC-configuraties](configurations.md)voor meer informatie over het compileren van configuraties.</span><span class="sxs-lookup"><span data-stu-id="a173e-114">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="a173e-115">De para meter **ConfigurationData** is een hashtabel die ten minste één sleutel met de naam **AllNodes** moet hebben.</span><span class="sxs-lookup"><span data-stu-id="a173e-115">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes** .</span></span> <span data-ttu-id="a173e-116">Het kan ook een of meer andere sleutels hebben.</span><span class="sxs-lookup"><span data-stu-id="a173e-116">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="a173e-117">In de voor beelden in dit onderwerp wordt een enkele extra sleutel (met uitzonde ring van de naam **AllNodes** Key) met de naam gebruikt `NonNodeData` , maar u kunt een wille keurig aantal extra sleutels toevoegen en deze een naam geven wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="a173e-117">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="a173e-118">De waarde van de sleutel **AllNodes** is een matrix.</span><span class="sxs-lookup"><span data-stu-id="a173e-118">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="a173e-119">Elk element van deze matrix is ook een hash-tabel die ten minste één sleutel met de naam **node** name moet hebben:</span><span class="sxs-lookup"><span data-stu-id="a173e-119">Each element of this array is also a hash table that must have at least one key named **NodeName** :</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="a173e-120">U kunt ook andere sleutels toevoegen aan elke hash-tabel:</span><span class="sxs-lookup"><span data-stu-id="a173e-120">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="a173e-121">Als u een eigenschap wilt Toep assen op alle knoop punten, kunt u een lid maken van de **AllNodes** -matrix met een **knooppunt** naam van `*` .</span><span class="sxs-lookup"><span data-stu-id="a173e-121">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span> <span data-ttu-id="a173e-122">U kunt bijvoorbeeld het volgende doen om elk knoop punt een eigenschap te geven `LogPath` :</span><span class="sxs-lookup"><span data-stu-id="a173e-122">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="a173e-123">Dit is het equivalent van het toevoegen van een eigenschap met de naam `LogPath` met de waarde `"C:\Logs"` voor elk van de andere blokken ( `VM-1` , `VM-2` , en `VM-3` ).</span><span class="sxs-lookup"><span data-stu-id="a173e-123">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="a173e-124">De ConfigurationData hashtabel definiëren</span><span class="sxs-lookup"><span data-stu-id="a173e-124">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="a173e-125">U kunt **ConfigurationData** definiëren als een variabele binnen hetzelfde script bestand als een configuratie (zoals in de voor gaande voor beelden) of in een afzonderlijk `.psd1` bestand.</span><span class="sxs-lookup"><span data-stu-id="a173e-125">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span> <span data-ttu-id="a173e-126">Als u **ConfigurationData** in een `.psd1` bestand wilt definiëren, maakt u een bestand dat alleen de hashtabel bevat die de configuratie gegevens vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a173e-126">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="a173e-127">U kunt bijvoorbeeld een bestand maken `MyData.psd1` met de naam met de volgende inhoud:</span><span class="sxs-lookup"><span data-stu-id="a173e-127">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="a173e-128">Een configuratie met configuratie gegevens compileren</span><span class="sxs-lookup"><span data-stu-id="a173e-128">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="a173e-129">Als u een configuratie wilt compileren waarvoor u configuratie gegevens hebt gedefinieerd, geeft u de configuratie gegevens op als de waarde van de para meter **ConfigurationData** .</span><span class="sxs-lookup"><span data-stu-id="a173e-129">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="a173e-130">Hiermee maakt u een MOF-bestand voor elke vermelding in de **AllNodes** -matrix.</span><span class="sxs-lookup"><span data-stu-id="a173e-130">This will create a MOF file for each entry in the **AllNodes** array.</span></span> <span data-ttu-id="a173e-131">Elk MOF-bestand krijgt een naam met de `NodeName` eigenschap van de bijbehorende matrix vermelding.</span><span class="sxs-lookup"><span data-stu-id="a173e-131">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="a173e-132">Als u bijvoorbeeld configuratie gegevens definieert zoals in het `MyData.psd1` bovenstaande bestand, worden met het compileren van een configuratie zowel `VM-1.mof` als `VM-2.mof` bestanden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a173e-132">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="a173e-133">Een configuratie met configuratie gegevens compileren met behulp van een variabele</span><span class="sxs-lookup"><span data-stu-id="a173e-133">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="a173e-134">Als u configuratie gegevens wilt gebruiken die zijn gedefinieerd als een variabele in hetzelfde `.ps1` bestand als de configuratie, geeft u de naam van de variabele door als de waarde van de para meter **ConfigurationData** bij het compileren van de configuratie:</span><span class="sxs-lookup"><span data-stu-id="a173e-134">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="a173e-135">Een configuratie met configuratie gegevens compileren met behulp van een gegevens bestand</span><span class="sxs-lookup"><span data-stu-id="a173e-135">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="a173e-136">Als u configuratie gegevens wilt gebruiken die zijn gedefinieerd in een. psd1-bestand, geeft u het pad en de naam van het bestand door als de waarde van de para meter **ConfigurationData** bij het compileren van de configuratie:</span><span class="sxs-lookup"><span data-stu-id="a173e-136">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="a173e-137">ConfigurationData-variabelen gebruiken in een configuratie</span><span class="sxs-lookup"><span data-stu-id="a173e-137">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="a173e-138">DSC biedt de volgende speciale variabelen die kunnen worden gebruikt in een configuratie script:</span><span class="sxs-lookup"><span data-stu-id="a173e-138">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="a173e-139">**$AllNodes** verwijst naar de volledige verzameling knoop punten die in **ConfigurationData** zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a173e-139">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData** .</span></span> <span data-ttu-id="a173e-140">U kunt de **AllNodes** -verzameling filteren met behulp van **. WHERE ()** en **. ForEach ()** .</span><span class="sxs-lookup"><span data-stu-id="a173e-140">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()** .</span></span>
- <span data-ttu-id="a173e-141">**ConfigurationData** verwijst naar de volledige hash-tabel die wordt door gegeven als de para meter bij het compileren van een configuratie.</span><span class="sxs-lookup"><span data-stu-id="a173e-141">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="a173e-142">**MyTypeName** bevat de [configuratie](configurations.md) naam waarin de variabele wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a173e-142">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="a173e-143">In de configuratie `MyDscConfiguration` heeft de bijvoorbeeld de `$MyTypeName` waarde `MyDscConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="a173e-143">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="a173e-144">Het **knoop punt** verwijst naar een bepaalde vermelding in de **AllNodes** -verzameling nadat deze is gefilterd met behulp van **. WHERE ()** of **. ForEach ()** .</span><span class="sxs-lookup"><span data-stu-id="a173e-144">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()** .</span></span>
  - <span data-ttu-id="a173e-145">Meer informatie over deze methoden vindt u in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span><span class="sxs-lookup"><span data-stu-id="a173e-145">You can read more about these methods in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="a173e-146">Niet-knooppunt gegevens gebruiken</span><span class="sxs-lookup"><span data-stu-id="a173e-146">Using non-node data</span></span>

<span data-ttu-id="a173e-147">Zoals we in eerdere voor beelden hebben gezien, kan de **ConfigurationData** hashtabel een of meer sleutels hebben naast de vereiste **AllNodes** -sleutel.</span><span class="sxs-lookup"><span data-stu-id="a173e-147">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span> <span data-ttu-id="a173e-148">In de voor beelden in dit onderwerp hebben we slechts één extra knoop punt gebruikt, met de naam `NonNodeData` .</span><span class="sxs-lookup"><span data-stu-id="a173e-148">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span> <span data-ttu-id="a173e-149">U kunt echter een wille keurig aantal extra sleutels definiëren en ze elke gewenste naam geven.</span><span class="sxs-lookup"><span data-stu-id="a173e-149">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="a173e-150">Zie [configuratie-en omgevings gegevens scheiden](separatingEnvData.md)voor een voor beeld van het gebruik van niet-knooppunt gegevens.</span><span class="sxs-lookup"><span data-stu-id="a173e-150">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a173e-151">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a173e-151">See Also</span></span>

- [<span data-ttu-id="a173e-152">Referenties opties in configuratie gegevens</span><span class="sxs-lookup"><span data-stu-id="a173e-152">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="a173e-153">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="a173e-153">DSC Configurations</span></span>](configurations.md)
