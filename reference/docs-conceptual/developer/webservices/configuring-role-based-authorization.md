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
ms.openlocfilehash: 2c9d6040b7a9c17dc5204c8eb835fd69780f62c5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564254"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="88c84-102">Autorisatie op basis van rollen configureren</span><span class="sxs-lookup"><span data-stu-id="88c84-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="88c84-103">In dit onderwerp wordt beschreven hoe u het op rollen gebaseerde autorisatie beleid configureert voor de voor beeld-implementatie van de [micro soft. Management. Odata. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) -interface die in de [implementatie van aangepaste autorisatie voor management Odata IIS-extensie](./implementing-custom-authorization-for-a-management-odata-web-service.md)wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="88c84-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="88c84-104">In dit voor beeld configureert u een XML-bestand dat wordt gebruikt door de voor beeld-OData-toepassing om het autorisatie beleid te definiëren.</span><span class="sxs-lookup"><span data-stu-id="88c84-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="88c84-105">U kunt twee rollen maken en verschillende Windows Power shell-modules koppelen die werk stromen met die rollen bevatten.</span><span class="sxs-lookup"><span data-stu-id="88c84-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="88c84-106">Het schema dat het XML-bestand definieert, wordt vermeld op [basis van op rollen gebaseerd verificatie configuratie schema](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="88c84-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="88c84-107">Het bestand RBacConfiguration. xml wijzigen</span><span class="sxs-lookup"><span data-stu-id="88c84-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="88c84-108">Dit bestand definieert het autorisatie beleid voor de toepassing.</span><span class="sxs-lookup"><span data-stu-id="88c84-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="88c84-109">Rollen worden gedefinieerd met behulp van `Group` knoop punten.</span><span class="sxs-lookup"><span data-stu-id="88c84-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="88c84-110">Een `Group` knoop punt definieert de Windows Power shell-opdrachten die gebruikers die zijn toegewezen aan die groep kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="88c84-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="88c84-111">Gebruikers worden toegewezen aan groepen met behulp van `User` knoop punten.</span><span class="sxs-lookup"><span data-stu-id="88c84-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="88c84-112">In deze voor beelden gaat u een module toevoegen aan het beheerders `Group` knooppunt en een gebruiker toevoegen aan elke groep.</span><span class="sxs-lookup"><span data-stu-id="88c84-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="88c84-113">Een module toevoegen aan een groeps knooppunt</span><span class="sxs-lookup"><span data-stu-id="88c84-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="88c84-114">Maak een bestand met de naam **RBacConfiguration. XML** in een tekst editor.</span><span class="sxs-lookup"><span data-stu-id="88c84-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="88c84-115">Dit bestand moet worden opgeslagen in de hoofdmap van de toepassing voor uw webservice.</span><span class="sxs-lookup"><span data-stu-id="88c84-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="88c84-116">Voeg de volgende tekst in het bestand in.</span><span class="sxs-lookup"><span data-stu-id="88c84-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="88c84-117">Het bestand bevat twee `Group` knoop punten.</span><span class="sxs-lookup"><span data-stu-id="88c84-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="88c84-118">Dit zijn de twee rollen die in dit voor beeld worden gebruikt, `NonAdminGroup` evenals de `AdminGroup` rollen.</span><span class="sxs-lookup"><span data-stu-id="88c84-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="88c84-119">`Cmdlets` `Group` Voeg het volgende XML-bestand toe na de afsluit code in het eerste knoop punt:</span><span class="sxs-lookup"><span data-stu-id="88c84-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="88c84-120">Een gebruiker toevoegen aan een groeps knooppunt</span><span class="sxs-lookup"><span data-stu-id="88c84-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="88c84-121">Open het bestand **RBacConfiguration. XML** in een tekst editor.</span><span class="sxs-lookup"><span data-stu-id="88c84-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="88c84-122">Dit bestand bevindt zich in de map C: \\ \inetpub\wwwroot\Modata als u de naam van het eind punt niet hebt gewijzigd vóór de installatie.</span><span class="sxs-lookup"><span data-stu-id="88c84-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="88c84-123">Voeg, direct na het afsluitende label in het `Users` knoop punt, de volgende XML toe:</span><span class="sxs-lookup"><span data-stu-id="88c84-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="88c84-124">Voeg, direct na de XML die in de vorige stap is toegevoegd, de volgende XML toe:</span><span class="sxs-lookup"><span data-stu-id="88c84-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```
