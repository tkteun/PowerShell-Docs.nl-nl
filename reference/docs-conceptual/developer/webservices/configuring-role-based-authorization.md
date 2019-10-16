---
title: Verificatie op basis van rollen configureren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352253"
---
# <a name="configuring-role-based-authorization"></a>Autorisatie op basis van rollen configureren

In dit onderwerp wordt uitgelegd hoe u het op rollen gebaseerde autorisatie beleid configureert voor de voorbeeld implementatie van de interface [micro soft. Management. Odata. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) die wordt beschreven in [aangepaste autorisatie implementeren voor beheer OData IIS-extensie](./implementing-custom-authorization-for-a-management-odata-web-service.md).

In dit voor beeld configureert u een XML-bestand dat wordt gebruikt door de voor beeld-OData-toepassing om het autorisatie beleid te definiëren. U kunt twee rollen maken en verschillende Windows Power shell-modules koppelen die werk stromen met die rollen bevatten. Het schema dat het XML-bestand definieert, wordt vermeld op [basis van op rollen gebaseerd verificatie configuratie schema](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Het bestand RBacConfiguration. xml wijzigen

Dit bestand definieert het autorisatie beleid voor de toepassing. Rollen worden gedefinieerd door middel van `Group`-knoop punten. Een `Group`-knoop punt definieert de Windows Power shell-opdrachten die gebruikers die zijn toegewezen aan die groep kunnen uitvoeren. Gebruikers worden toegewezen aan groepen door gebruik te maken van `User`-knoop punten.

In deze voor beelden gaat u een module toevoegen aan het knoop punt beheerder `Group` en een gebruiker toevoegen aan elke groep.

#### <a name="adding-a-module-to-a-group-node"></a>Een module toevoegen aan een groeps knooppunt

1. Maak een bestand met de naam **RBacConfiguration. XML** in een tekst editor. Dit bestand moet worden opgeslagen in de hoofdmap van de toepassing voor uw webservice. Voeg de volgende tekst in het bestand in.

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

2. Het bestand bevat twee `Group`-knoop punten. Dit zijn de twee rollen die in dit voor beeld worden gebruikt, de `NonAdminGroup` en de `AdminGroup`-rollen.

   Voeg in het eerste `Group`-knoop punt direct na het sluiten van de tag `Cmdlets` de volgende XML toe:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Een gebruiker toevoegen aan een groeps knooppunt

1. Open het bestand **RBacConfiguration. XML** in een tekst editor. Dit bestand bevindt zich in de map C: \\ \ inetpub\wwwroot\Modata als u de naam van het eind punt niet hebt gewijzigd vóór de installatie.

2. Voeg de volgende XML toe aan het knoop punt `Users`, direct na het afsluitende label:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Voeg, direct na de XML die in de vorige stap is toegevoegd, de volgende XML toe:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```