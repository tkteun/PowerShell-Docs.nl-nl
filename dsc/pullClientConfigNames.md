---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Een pull-client met behulp van configuratienamen instellen
ms.openlocfilehash: 11de53fc349ce0ebacf0d4855d82fa8a22d55c99
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="2da94-103">Een pull-client met behulp van configuratienamen instellen</span><span class="sxs-lookup"><span data-stu-id="2da94-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="2da94-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2da94-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="2da94-105">Elk doelknooppunt heeft adviseert het gebruik van pull-modus en de URL opgegeven waar deze contact opnemen met de pull-server configuraties ophalen.</span><span class="sxs-lookup"><span data-stu-id="2da94-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="2da94-106">U moet de lokale Configuration Manager (LCM) configureren met de benodigde informatie om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="2da94-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="2da94-107">Voor het configureren van de LCM die u maakt een speciaal soort configuratie, gedecoreerd worden met de **DSCLocalConfigurationManager** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="2da94-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="2da94-108">Zie voor meer informatie over het configureren van de LCM [configureren van de lokale Configuration Manager](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="2da94-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="2da94-109">**Opmerking**: dit onderwerp geldt voor PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="2da94-109">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="2da94-110">Zie voor meer informatie over het instellen van een pull-client in PowerShell 4.0 [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="2da94-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="2da94-111">Het volgende script voor het configureren van de LCM naar pull-configuraties van een server met de naam 'CONTOSO-PullSrv':</span><span class="sxs-lookup"><span data-stu-id="2da94-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="2da94-112">In het script wordt de **ConfigurationRepositoryWeb** blok definieert de pull-server.</span><span class="sxs-lookup"><span data-stu-id="2da94-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="2da94-113">De **ServerURL** eigenschap geeft u het eindpunt voor de pull-server.</span><span class="sxs-lookup"><span data-stu-id="2da94-113">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="2da94-114">De **RegistrationKey** eigenschap is een gedeelde sleutel tussen alle knooppunten van de client voor een pull-server en die pull-server.</span><span class="sxs-lookup"><span data-stu-id="2da94-114">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="2da94-115">Dezelfde waarde wordt opgeslagen in een bestand op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="2da94-115">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="2da94-116">De **ConfigurationNames** eigenschap is een matrix die Hiermee worden de namen van de configuraties die bedoeld zijn voor de clientknooppunt.</span><span class="sxs-lookup"><span data-stu-id="2da94-116">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="2da94-117">Op de pull-server de configuratie van de MOF-bestand van dit clientknooppunt moet de naam *ConfigurationNames*MOF, waarbij *ConfigurationNames* overeenkomt met de waarde van de **ConfigurationNames**  eigenschap die u in deze metaconfiguratie instellen.</span><span class="sxs-lookup"><span data-stu-id="2da94-117">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="2da94-118">**Opmerking:** als u opgeeft meer dan één waarde in de **ConfigurationNames**, moet u ook opgeven **PartialConfiguration** gegevensblokken die zich in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="2da94-118">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="2da94-119">Zie voor meer informatie over gedeeltelijke configuraties [PowerShell Desired State Configuration gedeeltelijke configuraties](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="2da94-119">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="2da94-120">Nadat dit script wordt uitgevoerd, maakt deze een nieuwe map voor uitvoer met de naam **PullClientConfigNames** en er een MOF-bestand metaconfiguratie plaatst.</span><span class="sxs-lookup"><span data-stu-id="2da94-120">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="2da94-121">In dit geval wordt het MOF-bestand metaconfiguratie worden benoemd `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="2da94-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="2da94-122">Aanroepen om toe te passen op de configuratie, de **Set DscLocalConfigurationManager** -cmdlet met de **pad** ingesteld op de locatie van het metaconfiguratie MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="2da94-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="2da94-123">**Opmerking**: registratiesleutels werken alleen met pull-webservers.</span><span class="sxs-lookup"><span data-stu-id="2da94-123">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="2da94-124">U moet nog steeds gebruiken **ConfigurationID** met een SMB-pull-server.</span><span class="sxs-lookup"><span data-stu-id="2da94-124">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="2da94-125">Voor informatie over het configureren van een pull-server met behulp van **ConfigurationID**, Zie [instellen van een pull-client met behulp van configuratie-ID](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="2da94-125">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="2da94-126">Bron- en -servers</span><span class="sxs-lookup"><span data-stu-id="2da94-126">Resource and report servers</span></span>

<span data-ttu-id="2da94-127">Als u alleen een **ConfigurationRepositoryWeb** of **ConfigurationRepositoryShare** blokkeren in uw configuratie LCM (zoals in het vorige voorbeeld), haalt de pull-client binnen resources uit de opgegeven server, maar wordt u rapporten niet naar verzenden.</span><span class="sxs-lookup"><span data-stu-id="2da94-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="2da94-128">U kunt een enkel pull-server gebruiken voor configuraties, bronnen en rapportage, maar u moet maken een **ReportRepositoryWeb** blok voor het instellen van rapportage.</span><span class="sxs-lookup"><span data-stu-id="2da94-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="2da94-129">Het volgende voorbeeld ziet een metaconfiguratie instellen van een client voor het pull-configuraties en resources en verzenden gegevens rapporteren aan een enkele pull-server.</span><span class="sxs-lookup"><span data-stu-id="2da94-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="2da94-130">U kunt ook verschillende pull-servers voor resources en rapportage opgeven.</span><span class="sxs-lookup"><span data-stu-id="2da94-130">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="2da94-131">Als u wilt opgeven van een resource-server u een gebruiken een **ResourceRepositoryWeb** (voor een pull-webserver) of een **ResourceRepositoryShare** blok (voor een SMB-pull-server).</span><span class="sxs-lookup"><span data-stu-id="2da94-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="2da94-132">Om een rapportserver die u gebruikt een **ReportRepositoryWeb** blok.</span><span class="sxs-lookup"><span data-stu-id="2da94-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="2da94-133">Een rapportserver mag niet een SMB-server.</span><span class="sxs-lookup"><span data-stu-id="2da94-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="2da94-134">De volgende metaconfiguratie configureert u een pull-client om de configuraties van **CONTOSO PullSrv** en de daarbij behorende bronnen uit **CONTOSO ResourceSrv**, en voor het verzenden van statusrapporten aan  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="2da94-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="2da94-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2da94-135">See Also</span></span>

* [<span data-ttu-id="2da94-136">Instellen van een pull-client met configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="2da94-136">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="2da94-137">Een DSC web pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="2da94-137">Setting up a DSC web pull server</span></span>](pullServer.md)

