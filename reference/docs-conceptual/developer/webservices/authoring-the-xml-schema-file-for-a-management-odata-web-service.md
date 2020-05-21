---
title: Het XML-schema bestand voor een management OData-webservice ontwerpen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: 7ccdeeb2833b79cabc7c77d1a400e0c9132b2dcd
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561461"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="6daff-102">Het XML-schemabestand maken voor een Management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="6daff-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="6daff-103">Nadat u de resources hebt gedefinieerd die uw webservice beschikbaar maakt (Zie [het MOF-schema bestand voor een management OData-webservice](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), wijst u deze resources toe aan de onderliggende Windows Power shell-cmdlets die de ondersteunde bewerkingen voor elke resource implementeren door een XML-bestand te maken dat voldoet aan het [schema voor bron toewijzing](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="6daff-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="6daff-104">In het XML-bestand worden ook de Url's opgegeven die door de client worden gebruikt om toegang te krijgen tot de resources.</span><span class="sxs-lookup"><span data-stu-id="6daff-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="6daff-105">Mappng bronnen naar Url's</span><span class="sxs-lookup"><span data-stu-id="6daff-105">Mappng resources to URLs</span></span>

<span data-ttu-id="6daff-106">Het eerste deel van het XML-bestand wijst de resources die zijn gedefinieerd in het MOF-schema bestand toe aan de Url's die worden gebruikt voor toegang tot de bestanden.</span><span class="sxs-lookup"><span data-stu-id="6daff-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="6daff-107">In het volgende voor beeld wordt deze toewijzing weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6daff-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="https://schemas.microsoft.com/powershell-web-services/2010/09">
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

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="6daff-108">Cmdlets toewijzen aan ruwe bewerkingen</span><span class="sxs-lookup"><span data-stu-id="6daff-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="6daff-109">Vervolgens geeft u de cmdlets op die overeenkomen met de ruwe (maken, lezen, bijwerken en verwijderen) bewerkingen die door de resources worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="6daff-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="6daff-110">In het management OData- [resource toewijzings schema](./resource-mapping-schema.md)worden de ruwe bewerkingen als volgt toegewezen.</span><span class="sxs-lookup"><span data-stu-id="6daff-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="6daff-111">RUWE opdracht</span><span class="sxs-lookup"><span data-stu-id="6daff-111">CRUD command</span></span>|<span data-ttu-id="6daff-112">XML-element</span><span class="sxs-lookup"><span data-stu-id="6daff-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="6daff-113">Maken</span><span class="sxs-lookup"><span data-stu-id="6daff-113">Create</span></span>|<span data-ttu-id="6daff-114">Maken</span><span class="sxs-lookup"><span data-stu-id="6daff-114">Create</span></span>|
|<span data-ttu-id="6daff-115">Lezen</span><span class="sxs-lookup"><span data-stu-id="6daff-115">Read</span></span>|<span data-ttu-id="6daff-116">Query’s uitvoeren</span><span class="sxs-lookup"><span data-stu-id="6daff-116">Query</span></span>|
|<span data-ttu-id="6daff-117">Bijwerken</span><span class="sxs-lookup"><span data-stu-id="6daff-117">Update</span></span>|<span data-ttu-id="6daff-118">Bijwerken</span><span class="sxs-lookup"><span data-stu-id="6daff-118">Update</span></span>|
|<span data-ttu-id="6daff-119">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="6daff-119">Delete</span></span>|<span data-ttu-id="6daff-120">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="6daff-120">Delete</span></span>|

<span data-ttu-id="6daff-121">In het volgende voor beeld ziet u de toewijzingen voor de bewerkingen Create, Read en update voor de `Service` resource.</span><span class="sxs-lookup"><span data-stu-id="6daff-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6daff-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6daff-122">See Also</span></span>

[<span data-ttu-id="6daff-123">Het MOF-schemabestand maken voor een Management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="6daff-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="6daff-124">Schema voor resourcetoewijzing</span><span class="sxs-lookup"><span data-stu-id="6daff-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="6daff-125">Een Management OData-webservice maken</span><span class="sxs-lookup"><span data-stu-id="6daff-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)
