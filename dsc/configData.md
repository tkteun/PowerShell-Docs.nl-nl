---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Met behulp van configuratiegegevens
ms.openlocfilehash: d42c43fddb54050adcbac949e7f67f3b41b540f1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="919bc-103">Met behulp van de configuratiegegevens in DSC</span><span class="sxs-lookup"><span data-stu-id="919bc-103">Using configuration data in DSC</span></span>

><span data-ttu-id="919bc-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="919bc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="919bc-105">Met behulp van de ingebouwde DSC **ConfigurationData** parameter, kunt u gegevens die kunnen worden gebruikt in een configuratie definiëren.</span><span class="sxs-lookup"><span data-stu-id="919bc-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="919bc-106">Hiermee kunt u voor het maken van een configuratie voor één die kan worden gebruikt voor meerdere knooppunten of voor verschillende omgevingen.</span><span class="sxs-lookup"><span data-stu-id="919bc-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="919bc-107">Bijvoorbeeld, als u een toepassing ontwikkelt, kunt u één configuratie gebruiken voor ontwikkel- en productie-omgevingen en configuratiegegevens gebruiken om op te geven gegevens voor elke omgeving.</span><span class="sxs-lookup"><span data-stu-id="919bc-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="919bc-108">Dit onderwerp beschrijft de structuur van de **ConfigurationData** hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="919bc-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="919bc-109">Zie voor voorbeelden van het gebruik van configuratiegegevens [scheiden van gegevens en de omgeving](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="919bc-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="919bc-110">De algemene parameter ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="919bc-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="919bc-111">Een DSC-configuratie heeft een algemene parameter **ConfigurationData**, dat u opgeeft wanneer u de configuratie compileren.</span><span class="sxs-lookup"><span data-stu-id="919bc-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="919bc-112">Zie voor meer informatie over het compileren van configuraties [DSC-configuraties](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="919bc-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="919bc-113">De **ConfigurationData** -parameter is een hasthtable waarvoor ten minste één sleutel met de naam moet **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="919bc-113">The **ConfigurationData** parameter is a hasthtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="919bc-114">Het kan ook een of meer sleutels hebben.</span><span class="sxs-lookup"><span data-stu-id="919bc-114">It can also have one or more other keys.</span></span>

><span data-ttu-id="919bc-115">**Opmerking:** de voorbeelden in dit onderwerp gebruiken één extra sleutel (anders dan de benoemde **AllNodes** key) met de naam `NonNodeData`, maar u kunt een willekeurig aantal aanvullende sleutels bevatten en naam elke gewenste.</span><span class="sxs-lookup"><span data-stu-id="919bc-115">**Note:** The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="919bc-116">De waarde van de **AllNodes** sleutel is een matrix.</span><span class="sxs-lookup"><span data-stu-id="919bc-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="919bc-117">Elk element van deze matrix is ook een hashtabel die ten minste één sleutel met de naam moet hebben **NodeName**:</span><span class="sxs-lookup"><span data-stu-id="919bc-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

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

<span data-ttu-id="919bc-118">U kunt andere sleutels toevoegen aan elk hash-tabel:</span><span class="sxs-lookup"><span data-stu-id="919bc-118">You can add other keys to each hash table as well:</span></span>

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

<span data-ttu-id="919bc-119">Als u wilt een eigenschap van toepassing op alle knooppunten, kunt u een lid van de **AllNodes** matrix heeft een **NodeName** van `*`.</span><span class="sxs-lookup"><span data-stu-id="919bc-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="919bc-120">Bijvoorbeeld, voor elk knooppunt een `LogPath` eigenschap, u kunt dit doen:</span><span class="sxs-lookup"><span data-stu-id="919bc-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

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

<span data-ttu-id="919bc-121">Dit is het equivalent van het toevoegen van een eigenschap met de naam `LogPath` met een waarde van `"C:\Logs"` aan elk van de andere blokken (`VM-1`, `VM-2`, en `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="919bc-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="919bc-122">De hashtabel ConfigurationData definiëren</span><span class="sxs-lookup"><span data-stu-id="919bc-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="919bc-123">U kunt definiëren **ConfigurationData** als een variabele binnen hetzelfde scriptbestand als een configuratie (zoals in het vorige voorbeeld) of in een afzonderlijke `.psd1` bestand.</span><span class="sxs-lookup"><span data-stu-id="919bc-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="919bc-124">Voor het definiëren van **ConfigurationData** in een `.psd1` bestand, maakt u een bestand met alleen de hash-tabel die de configuratiegegevens vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="919bc-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="919bc-125">U kunt bijvoorbeeld een bestand met de naam maken `MyData.psd1` met de volgende inhoud:</span><span class="sxs-lookup"><span data-stu-id="919bc-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

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

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="919bc-126">Een configuratie met configuratiegegevens compileren</span><span class="sxs-lookup"><span data-stu-id="919bc-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="919bc-127">Samengesteld op basis van een configuratie waarvoor u configuratiegegevens hebt gedefinieerd, geeft u de configuratiegegevens als de waarde van de **ConfigurationData** parameter.</span><span class="sxs-lookup"><span data-stu-id="919bc-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="919bc-128">Hiermee maakt u een MOF-bestand voor elk item in de **AllNodes** matrix.</span><span class="sxs-lookup"><span data-stu-id="919bc-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="919bc-129">Elke MOF-bestand worden benoemd met de `NodeName` eigenschap van de bijbehorende matrixvermelding.</span><span class="sxs-lookup"><span data-stu-id="919bc-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="919bc-130">Bijvoorbeeld, als het definiëren van configuratiegegevens, zoals in de `MyData.psd1` bestand hierboven, een configuratie compileren maakt zowel `VM-1.mof` en `VM-2.mof` bestanden.</span><span class="sxs-lookup"><span data-stu-id="919bc-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="919bc-131">Compileren van een configuratie met configuratiegegevens met behulp van een variabele</span><span class="sxs-lookup"><span data-stu-id="919bc-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="919bc-132">Gebruik van de configuratiegegevens die is gedefinieerd als een variabele in dezelfde `.ps1` bestand als de configuratie, geeft u de variabele naam als de waarde van de **ConfigurationData** parameter bij het compileren van de configuratie:</span><span class="sxs-lookup"><span data-stu-id="919bc-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="919bc-133">Compileren van een configuratie met configuratiegegevens met een gegevensbestand</span><span class="sxs-lookup"><span data-stu-id="919bc-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="919bc-134">Voor het gebruik van de configuratiegegevens die is gedefinieerd in een bestand .psd1 u geeft het pad en bestandsnaam van het bestand als de waarde van de **ConfigurationData** parameter bij het compileren van de configuratie:</span><span class="sxs-lookup"><span data-stu-id="919bc-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="919bc-135">ConfigurationData variabelen gebruiken in een configuratie</span><span class="sxs-lookup"><span data-stu-id="919bc-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="919bc-136">DSC biedt drie speciale variabelen die kunnen worden gebruikt in een configuratiescript: **$AllNodes**, **$Node**, en **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="919bc-136">DSC provides three special variables that can be used in a configuration script: **$AllNodes**, **$Node**, and **$ConfigurationData**.</span></span>

- <span data-ttu-id="919bc-137">**$AllNodes** verwijst naar de volledige verzameling van knooppunten die zijn gedefinieerd in **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="919bc-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="919bc-138">U kunt filteren de **AllNodes** verzameling met behulp van **. WHERE()** en **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="919bc-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="919bc-139">**Knooppunt** verwijst naar een bepaald item in de **AllNodes** verzameling nadat deze is gefilterd met behulp van **. WHERE()** of **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="919bc-139">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
- <span data-ttu-id="919bc-140">**ConfigurationData** verwijst naar de volledige hash-tabel die is doorgegeven als parameter bij het compileren van een configuratie.</span><span class="sxs-lookup"><span data-stu-id="919bc-140">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="919bc-141">Met behulp van de gegevens niet-knooppunt</span><span class="sxs-lookup"><span data-stu-id="919bc-141">Using non-node data</span></span>

<span data-ttu-id="919bc-142">Als er in de eerdere voorbeelden hebt gezien de **ConfigurationData** hashtabel kan een of meer sleutels naast de vereiste hebben **AllNodes** sleutel.</span><span class="sxs-lookup"><span data-stu-id="919bc-142">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="919bc-143">In de voorbeelden in dit onderwerp, hebben we slechts één extra knooppunt gebruikt en met de naam `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="919bc-143">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="919bc-144">U kunt echter een aantal aanvullende sleutels opgeven en elke gewenste naam.</span><span class="sxs-lookup"><span data-stu-id="919bc-144">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="919bc-145">Zie voor een voorbeeld van het gebruik van niet-knooppuntgegevens [scheiden van gegevens en de omgeving](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="919bc-145">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="919bc-146">Zie ook</span><span class="sxs-lookup"><span data-stu-id="919bc-146">See Also</span></span>
- [<span data-ttu-id="919bc-147">Referentieopties in configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="919bc-147">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="919bc-148">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="919bc-148">DSC Configurations</span></span>](configurations.md)