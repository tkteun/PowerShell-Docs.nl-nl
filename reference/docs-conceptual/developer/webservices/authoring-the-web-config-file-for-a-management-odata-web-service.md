---
title: Het web. config-bestand voor een management OData-webservice ontwerpen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352267"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Het Web.config-bestand maken voor een Management OData-webservice

Voordat u de Management OData-webservice kunt implementeren, moet u het bestand Web. config zodanig configureren dat deze verwijst naar de XML-schema bestanden en de Dll's die de [micro soft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) -en [System. Management. Automation. Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) -interfaces implementeren.

## <a name="sample-config-file"></a>Voorbeeld configuratie bestand

Hier volgt een voor beeld van hoe het web. config-bestand voor uw webservice eruitziet.

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

[Aangepaste autorisatie implementeren voor een management OData-webservice](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[SessionConfiguration implementeren voor een management OData-webservice](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[Het MOF-schema bestand voor een management OData-webservice ontwerpen](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[Het XML-schema bestand voor een management OData-webservice ontwerpen](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Een management OData-webservice maken](./creating-a-management-odata-web-service.md)