---
title: Het XML-schemabestand voor een Management OData-webservice ontwerpen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848193"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="f08d8-102">Het XML-schemabestand maken voor een Management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="f08d8-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="f08d8-103">Nadat u de resources definiëren de webservice wordt weergegeven (Zie [ontwerpen van het schema MOF-bestand voor een Management OData-webservice](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), u deze resources toewijzen aan de onderliggende Windows PowerShell-cmdlets die de ondersteunde implementeren bewerkingen voor elke resource met het maken van een XML-bestand dat voldoet aan de [Resource toewijzen Schema](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="f08d8-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="f08d8-104">Het XML-bestand bevat ook de URL's die door de client worden gebruikt voor toegang tot de resources.</span><span class="sxs-lookup"><span data-stu-id="f08d8-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="f08d8-105">Mappng resources naar URL 's</span><span class="sxs-lookup"><span data-stu-id="f08d8-105">Mappng resources to URLs</span></span>

<span data-ttu-id="f08d8-106">Het eerste deel van het XML-bestand wordt gedefinieerd in het schema MOF-bestand met de URL's die worden gebruikt voor toegang tot deze resources toegewezen.</span><span class="sxs-lookup"><span data-stu-id="f08d8-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="f08d8-107">Het volgende voorbeeld ziet dat toewijzing.</span><span class="sxs-lookup"><span data-stu-id="f08d8-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="f08d8-108">Toewijzing van cmdlets CRUD-bewerkingen</span><span class="sxs-lookup"><span data-stu-id="f08d8-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="f08d8-109">Vervolgens geeft u de cmdlets die met de CRUD overeenkomen (maken, lezen, bijwerken en verwijderen) bewerkingen die ondersteuning bieden voor de resources.</span><span class="sxs-lookup"><span data-stu-id="f08d8-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="f08d8-110">In de Management OData [Resource toewijzen Schema](./resource-mapping-schema.md), de CRUD-bewerkingen als volgt zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="f08d8-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="f08d8-111">CRUD-opdracht</span><span class="sxs-lookup"><span data-stu-id="f08d8-111">CRUD command</span></span>|<span data-ttu-id="f08d8-112">XML-element</span><span class="sxs-lookup"><span data-stu-id="f08d8-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="f08d8-113">Maken</span><span class="sxs-lookup"><span data-stu-id="f08d8-113">Create</span></span>|<span data-ttu-id="f08d8-114">Maken</span><span class="sxs-lookup"><span data-stu-id="f08d8-114">Create</span></span>|
|<span data-ttu-id="f08d8-115">Lezen</span><span class="sxs-lookup"><span data-stu-id="f08d8-115">Read</span></span>|<span data-ttu-id="f08d8-116">Query’s uitvoeren</span><span class="sxs-lookup"><span data-stu-id="f08d8-116">Query</span></span>|
|<span data-ttu-id="f08d8-117">Bijwerken</span><span class="sxs-lookup"><span data-stu-id="f08d8-117">Update</span></span>|<span data-ttu-id="f08d8-118">Bijwerken</span><span class="sxs-lookup"><span data-stu-id="f08d8-118">Update</span></span>|
|<span data-ttu-id="f08d8-119">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="f08d8-119">Delete</span></span>|<span data-ttu-id="f08d8-120">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="f08d8-120">Delete</span></span>|

<span data-ttu-id="f08d8-121">Het volgende voorbeeld ziet u de toewijzingen voor de bewerkingen maken, lezen en bijwerken op de `Service` resource.</span><span class="sxs-lookup"><span data-stu-id="f08d8-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="f08d8-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f08d8-122">See Also</span></span>

[<span data-ttu-id="f08d8-123">Het schema MOF-bestand voor een Management OData-webservice ontwerpen</span><span class="sxs-lookup"><span data-stu-id="f08d8-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="f08d8-124">Resource-koppelingsschema</span><span class="sxs-lookup"><span data-stu-id="f08d8-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="f08d8-125">Het maken van een Management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="f08d8-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)