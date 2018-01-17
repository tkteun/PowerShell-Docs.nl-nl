---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Ingebouwde Desired State Configuration Resources voor Linux
ms.openlocfilehash: e268cb2ee8a246f18216b34e5e2a6d512f15e18c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Ingebouwde Desired State Configuration Resources voor Linux

Resources zijn bouwstenen die u gebruiken kunt om een script PowerShell Desired State Configuration (DSC) te schrijven. DSC voor Linux wordt geleverd met een set ingebouwde functionaliteit voor het configureren van resources, zoals bestanden en mappen, pakketten, omgevingsvariabelen en services en processen.

## <a name="built-in-resources"></a>Ingebouwde resources 

De volgende tabel bevat een lijst van deze resources en koppelingen naar onderwerpen waarin ze in detail beschreven.

* [nxArchive Resource](lnxArchiveResource.md)--biedt een mechanisme voor het uitpakken van bestanden te archiveren (tar, .zip) op een specifiek pad.
* [nxEnvironment Resource](lnxEnvironmentResource.md)--omgevingsvariabelen op doelknooppunten beheert. 
* [nxFile Resource](lnxFileResource.md)--Linux beheert bestanden en mappen. 
* [nxFileLine Resource](lnxFileLineResource.md)--beheert afzonderlijke regels in een Linux-bestand. 
* [nxGroup Resource](lnxGroupResource.md)--beheert lokale Linux-groepen. 
* [nxPackage Resource](lnxPackageResource.md)--beheert pakketten op Linux-knooppunten.
* [nxScript Resource](lnxScriptResource.md)--scripts op de doelknooppunten wordt uitgevoerd.
* [nxService Resource](lnxServiceResource.md)--beheert Linux-services (daemons).
* [nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--beheert openbare ssh-sleutels voor een Linux-gebruiker. 
* [nxUser Resource](lnxUserResource.md)--lokale Linux-gebruikers beheert. 
  
