---
title: Het bestand Web.config voor een Management OData-webservice ontwerpen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080710"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Het Web.config-bestand maken voor een Management OData-webservice

Voordat u uw Management OData-webservice implementeren kunt, moet u het bestand web.config om te verwijzen naar de XML-schema-bestanden en het .dll-bestanden die worden geïmplementeerd configureren de [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) en [ System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.

## <a name="sample-config-file"></a>Voorbeeld-configuratiebestand

Hier volgt een voorbeeld van hoe het bestand web.config voor de webservice uitziet.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a>Zie ook

[Aangepaste autorisatie voor een Management OData-webservice implementeren](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[SessionConfiguration voor een Management OData-webservice implementeren](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[Het schema MOF-bestand voor een Management OData-webservice ontwerpen](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[Het XML-schemabestand voor een Management OData-webservice ontwerpen](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Het maken van een Management OData-webservice](./creating-a-management-odata-web-service.md)