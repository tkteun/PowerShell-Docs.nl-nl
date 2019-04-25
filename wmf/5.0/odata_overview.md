---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 1153738fdf6f926d5d819bbf91450408dcb17f71
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057805"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a>PowerShell-cmdlets genereren op basis van OData-eindpunt

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a>Windows PowerShell-cmdlets op basis van een OData-eindpunt genereren

**Exporteren-ODataEndpointProxy** is een cmdlet die een set van Windows PowerShell-cmdlets op basis van de functionaliteit die door een opgegeven OData-eindpunt genereert.

Het volgende voorbeeld laat zien hoe het gebruik van deze nieuwe cmdlet:

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

Er zijn nog steeds delen met belangrijke use cases in de ontwikkeling van deze functionaliteit wilt gebruiken, met inbegrip van, maar niet beperkt tot:
-   Koppelingen
-   Doorgeven van stromen

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Windows PowerShell-cmdlets op basis van een OData-eindpunt met ODataUtils genereren

De module ODataUtils kunt genereren van Windows PowerShell-cmdlets van REST-eindpunten die ondersteuning bieden voor OData. De volgende incrementele verbeteringen zijn in de Microsoft.PowerShell.ODataUtils Windows PowerShell-module.
-   Aanvullende informatie van server-side-eindpunt voor client-side-Channel.
-   Client-side-ondersteuning voor paginering
-   Serverzijde filteren met behulp van de - Select-parameters
-   Ondersteuning voor web-aanvraagheaders

De proxy-cmdlets die worden gegenereerd door de cmdlet Export-ODataEndPointProxy bevatten aanvullende informatie (niet in de $metadata gebruikt tijdens het genereren van de client-side-proxy genoemd) van de server side OData-eindpunt op de gegevensstroom (een nieuwe Windows PowerShell 5.0-functie). Hier volgt een voorbeeld van hoe u die informatie.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

De records krijgt u vanaf de server in batches met behulp van de client-side-ondersteuning voor paginering. Dit is handig als u een grote hoeveelheid gegevens uit de server via het netwerk ophalen moet.

```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

De gegenereerde proxy-cmdlets bieden ondersteuning voor de Select-parameters die u als een filter gebruiken kunt voor het ontvangen van de recordeigenschappen die de client nodig heeft. Dit vermindert de hoeveelheid gegevens die worden overgedragen via het netwerk, omdat het filteren op de server wordt uitgevoerd.

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

De cmdlet Export-ODataEndpointProxy en de webtoepassingsproxy-cmdlets die worden gegenereerd door, bieden nu ondersteuning voor de parameter Headers (supply waarden als een hash-tabel), die u gebruiken kunt voor aanvullende informatie die wordt verwacht door het OData-eindpunt voor server-side-channel. In het volgende voorbeeld, kunt u een abonnementssleutel via Headers voor services die een abonnementssleutel voor verificatie verwacht kanaal.

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
