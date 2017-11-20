# [Overzicht](overview.md)

## [Overzicht Desired State Configuration voor besluitvormers](decisionMaker.md)

## [Overzicht Desired State Configuration voor technici](DscForEngineers.md)

## [QuikStart voor DSC](quickStart.md)

# [Configuraties](configurations.md)

## [Configuraties doorvoeren](enactingConfigurations.md)

## [Configuratie- en omgevingsgegevens scheiden](separatingEnvData.md)

## [Resources met meerdere versies gebruiken](sxsResource.md)

## [DSC uitvoeren met gebruikersreferenties](runAsUser.md)

## [Afhankelijkheden van meerdere knooppunten opgeven](crossNodeDependencies.md)

## [Configuratiegegevens](configData.md)

### [Referentieopties in de configuratiegegevens](configDataCredentials.md)

## [Configuraties nesten](compositeConfigs.md)

## [Het MOF-configuratiebestand beveiligen](secureMOF.md)

## [Gedeeltelijke configuraties](partialConfigs.md)

## [Schrijfhulp voor DSC-configuraties](configHelp.md)

## [Een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md)

### [De registersleutel DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

# [Resources](resources.md)

## [Ingebouwde resources](builtInResource.md)

### [Archiefresource](archiveResource.md)

### [Omgevingsresource](environmentResource.md)

### [Bestandsresource](fileResource.md)

### [Groepsresource](groupResource.md)

### [GroupSet-resource](groupSetResource.md)

### [Logboekresource](logResource.md)

### [Pakketresource](packageResource.md)

### [ProcessSet-resource](processSetResource.md)

### [Registerresource](registryResource.md)

### [Scriptresource](scriptResource.md)

### [Serviceresource](serviceResource.md)

### [ServiceSet-resource](serviceSetResource.md)

### [Gebruikersresource](userResource.md)

### [WaitForAllResource](waitForAllResource.md)

### [WaitForAnyResource](waitForAnyResource.md)

### [WaitForSomeResource](waitForSomeResource.md)

### [WindowsFeature-resource](windowsfeatureResource.md)

### [WindowsFeatureSet-resource](windowsFeatureSetResource.md)

### [WindowsOptionalFeature-resource](windowsOptionalFeatureResource.md)

### [WindowsOptionalFeatureSet-resource](windowsOptionalFeatureSetResource.md)

### [WindowsPackageCab-resource](windowsPackageCabResource.md)

### [WindowsProcess-resource](windowsProcessResource.md)

## [Aangepaste resources ontwerpen](authoringResource.md) 

### [Aangepaste resources op basis van MOF](authoringResourceMOF.md)

#### [Resource in C# op basis van MOF](authoringResourceMofCS.md)

### [Aangepaste resources op basis van klassen](authoringResourceClass.md)

### [Samengestelde resources](authoringResourceComposite.md)

### [Een DSC-resource met één instantie schrijven (aanbevolen)](singleInstance.md)

### [Controlelijst voor het ontwerpen van resource](resourceAuthoringChecklist.md)

## [Foutopsporing voor DSC-resources](debugResource.md)

## [Methoden voor het rechtstreeks aanroepen van DSC-resources](directCallResource.md)

# Local Configuration Manager

## [De Local Configuration Manager (LCM) configureren](metaConfig.md)

## [De LCM configureren in PowerShell 4.0](metaConfig4.md)

# Het DSC-pull-model

## [Een web-pull-server instellen](pullServer.md)

## [Een DSC SMB-pull-server instellen](pullServerSMB.md)

## [Een pull-client instellen](pullClient.md)

### [Een pull-client instellen met behulp van configuratienamen](pullClientConfigNames.md)

### [Een pull-client instellen met behulp van het configuratie-id](pullClientConfigID.md)

## [Een DSC-rapportserver gebruiken](reportServer.md)

## [Best practices voor pull-servers](secureServer.md)

# [DSC-voorbeelden](dscExamples.md)

## [Een CI/CD-pijplijn met DSC, Pester en Visual Studio Team Services bouwen](dscCiCd.md)

## [Configuratie- en omgevingsgegevens scheiden](separatingEnvData.md)

# [Problemen met DSC oplossen](troubleshooting.md)

# [DSC gebruiken op Nano Server](nanoDsc.md)

# DSC op Linux

## [Aan de slag met DSC voor Linux](lnxGettingStarted.md)

## [Ingebouwde resources voor Linux](lnxBuiltInResources.md)

### [nxArchive-resource](lnxArchiveResource.md)

### [nxEnvironment-resource](lnxEnvironmentResource.md)

### [nxFile-resource](lnxFileResource.md)

### [nxFileLine-resource](lnxFileLineResource.md)

### [nxGroup-resource](lnxGroupResource.md)

### [nxPackage-resource](lnxPackageResource.md)

### [nxService-resource](lnxServiceResource.md)

### [nxSshAuthorizedKeys-resource](lnxSshAuthorizedKeysResource.md)

### [nxUser-resource](lnxUserResource.md)

# [DSC gebruiken op Microsoft Azure](azureDsc.md)

# Referentie voor DSC MOF

## [MSFT_DSCLocalConfigurationManager-klasse](msft-dsclocalconfigurationmanager.md)

### [De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-applyconfiguration.md)

### [De DisableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)

### [De EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)

### [De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfiguration.md)

### [De GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)

### [De GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)

### [De GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)

### [De PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)

### [De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-removeconfiguration.md)

### [De ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourceget.md)

### [De ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourceset.md)

### [De ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-resourcetest.md)

### [De RollBack-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-rollback.md)

### [De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfiguration.md)

### [De SendConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)

### [De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)

### [De SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)

### [De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-stopconfiguration.md)

### [De TestConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager](msft-dsclocalconfigurationmanager-testconfiguration.md)

# Meer resources

## [Whitepapers](whitepapers.md)
