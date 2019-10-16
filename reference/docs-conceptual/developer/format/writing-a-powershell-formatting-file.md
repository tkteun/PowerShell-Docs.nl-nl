---
title: Een Power shell-indelings bestand schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353408"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="e5e13-102">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="e5e13-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="e5e13-103">' Schrijven van een Power shell-indelings bestand ' is voor opdracht ontwikkelaars die cmdlets schrijven of functies die objecten uitvoeren op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="e5e13-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="e5e13-104">Indelings bestanden bepalen hoe Power shell die objecten weergeeft op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="e5e13-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="e5e13-105">Deze documentatie bevat een overzicht van de indelings bestanden, een uitleg van de concepten die u moet begrijpen bij het schrijven van deze bestanden, voor beelden van XML die worden gebruikt in deze bestanden en een referentie sectie voor de XML-elementen.</span><span class="sxs-lookup"><span data-stu-id="e5e13-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e5e13-106">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="e5e13-106">In This Section</span></span>

<span data-ttu-id="e5e13-107">[Overzicht van het format teren van bestanden](./formatting-file-overview.md) Beschrijft wat een indelings bestand is en de algemene onderdelen van een opmaak bestand, met inbegrip van algemene functies die in het bestand kunnen worden gedefinieerd, de verschillende typen opmaak weergaven die kunnen worden gedefinieerd voor .NET-objecten en een vereenvoudigd voor beeld van de XML die wordt gebruikt voor het definiëren van een tabel v Details.</span><span class="sxs-lookup"><span data-stu-id="e5e13-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="e5e13-108">[Bestands concepten opmaken](./formatting-file-concepts.md) Bevat informatie die u mogelijk moet kennen bij het maken van uw eigen indelings bestanden, zoals de verschillende typen weer gaven die u kunt definiëren en speciale onderdelen van deze weer gaven.</span><span class="sxs-lookup"><span data-stu-id="e5e13-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="e5e13-109">[Voor beelden van het format teren van bestanden](./examples-of-formatting-files.md) Biedt XML-voor beelden van verschillende opmaak bestanden, waaronder voor beelden van een tabel weergave, een lijst weergave en een brede weer gave, evenals voor beelden die laten zien hoe u functies kunt definiëren zoals selectie sets, selectie omstandigheden en algemene besturings elementen.</span><span class="sxs-lookup"><span data-stu-id="e5e13-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="e5e13-110">[Verwijzing naar XML-indeling](./format-schema-xml-reference.md) Bevat naslag onderwerpen voor de XML-elementen die worden gebruikt in een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="e5e13-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
