---
title: Autorisatie op basis van rollen configureren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080676"
---
# <a name="configuring-role-based-authorization"></a>Autorisatie op basis van rollen configureren

In dit onderwerp ziet u hoe u het autorisatiebeleid voor de voorbeeldimplementatie op basis van rollen configureren de [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface die worden beschreven in [aangepaste implementeren Autorisatie voor Management OData IIS-extensie](./implementing-custom-authorization-for-a-management-odata-web-service.md).

In dit voorbeeld configureert u een XML-bestand dat wordt gebruikt door de voorbeeld-Management OData-toepassing voor het definiëren van het autorisatiebeleid. U twee rollen maken en koppelen van andere Windows PowerShell-modules die werkstromen met deze rollen bevatten. Het schema waarmee het XML-bestand wordt vermeld op [configuratieschema voor autorisatie op basis van rollen](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Wijzigen van het bestand RBacConfiguration.xml

Dit bestand definieert het autorisatiebeleid voor de toepassing. Rollen worden gedefinieerd met behulp van `Group` knooppunten. Een `Group` knooppunt definieert de Windows PowerShell-opdrachten die kunnen worden uitgevoerd door gebruikers die zijn toegewezen aan die groep. Gebruikers zijn toegewezen aan groepen met behulp van `User` knooppunten.

In deze voorbeelden, voegt u een module voor de beheerder `Group` knooppunt, en een gebruiker toevoegen aan elke groep.

#### <a name="adding-a-module-to-a-group-node"></a>Een Module toe te voegen aan een groepsknooppunt

1. Maak een bestand met de naam **RBacConfiguration.xml** in een teksteditor. Dit bestand moet worden opgeslagen in de map van de hoofdtoepassing voor uw webservice. Voeg de volgende tekst in het bestand.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. Het bestand bevat twee `Group` knooppunten. Dit zijn de twee rollen in dit voorbeeld gebruikt de `NonAdminGroup` en de `AdminGroup` rollen.

   Direct na de afsluitende `Cmdlets` tag op in de eerste `Group` knooppunt het volgende XML-bestand toevoegen:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Een gebruiker toe te voegen aan een groepsknooppunt

1. Open de **RBacConfiguration.xml** bestand in een teksteditor. Dit bestand bevindt zich in de map C:\\\inetpub\wwwroot\Modata als u de naam van het eindpunt voor de installatie niet hebt gewijzigd.

2. Direct na de eindcode in de `Users` knooppunt het volgende XML-bestand toevoegen:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Rechtstreeks toevoegen nadat het XML-bestand in de vorige stap hebt toegevoegd, de volgende XML:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```