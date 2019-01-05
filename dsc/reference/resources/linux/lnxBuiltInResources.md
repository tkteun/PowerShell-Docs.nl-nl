---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Ingebouwde Desired State Configuration Resources voor Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048298"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Ingebouwde Desired State Configuration Resources voor Linux

Resources zijn bouwstenen die u gebruiken kunt om een script PowerShell Desired State Configuration (DSC) te schrijven. DSC voor Linux wordt geleverd met een set ingebouwde functionaliteit voor het configureren van resources, zoals bestanden en mappen, pakketten, omgevingsvariabelen en -services en processen.

## <a name="built-in-resources"></a>Ingebouwde resources

De volgende tabel geeft een lijst van deze resources en koppelingen naar onderwerpen waarin deze worden in detail beschreven.

* [nxArchive-Resource](lnxArchiveResource.md)--biedt een mechanisme voor het uitpakken van bestanden te archiveren (.tar, .zip) op een specifiek pad.
* [nxEnvironment-Resource](lnxEnvironmentResource.md)--omgevingsvariabelen op doelknooppunten beheert.
* [nxFile-Resource](lnxFileResource.md)--beheert Linux-bestanden en mappen.
* [nxFileLine-Resource](lnxFileLineResource.md)--beheert afzonderlijke regels in een Linux-bestand.
* [nxGroup-Resource](lnxGroupResource.md)--lokale Linux-groepen worden beheerd.
* [nxPackage-Resource](lnxPackageResource.md)--pakketten op Linux-knooppunten beheert.
* [nxScript Resource](lnxScriptResource.md)--scripts uitvoert op doelknooppunten.
* [nxService-Resource](lnxServiceResource.md)--beheert Linux-services (daemons).
* [nxSshAuthorizedKeys-Resource](lnxSshAuthorizedKeysResource.md)--beheert openbare ssh-sleutels voor een Linux-gebruiker.
* [nxUser-Resource](lnxUserResource.md)--lokale Linux-gebruikers beheert.