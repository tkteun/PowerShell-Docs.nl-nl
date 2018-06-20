---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: dfc171f9a3471f8fe7801283dd4a9b06860781a2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225722"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="92a71-102">Aangepaste typen maken met PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="92a71-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="92a71-103">We hebben de PowerShell-taal voor het definiëren van klassen en andere door de gebruiker gedefinieerde typen met behulp van formele syntaxis en de semantiek die vergelijkbaar met andere objectgeoriënteerde programmeertalen zijn verbeterd.</span><span class="sxs-lookup"><span data-stu-id="92a71-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="92a71-104">Het doel is om in te schakelen van ontwikkelaars en IT-professionals Profiteer van PowerShell voor een breed scala aan gebruiksvoorbeelden, ontwikkeling van PowerShell-artefacten (zoals DSC-resources) te vereenvoudigen en dekking van management vlakken versnellen.</span><span class="sxs-lookup"><span data-stu-id="92a71-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="92a71-105">Ondersteunde scenario's in deze release</span><span class="sxs-lookup"><span data-stu-id="92a71-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="92a71-106">DSC-resources en hun bijbehorende typen definiëren met behulp van de PowerShell-taal</span><span class="sxs-lookup"><span data-stu-id="92a71-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="92a71-107">Aangepaste typen in PowerShell definiëren met behulp van bekende objectgeoriënteerde programming constructs, zoals klassen, eigenschappen, methoden, enz.</span><span class="sxs-lookup"><span data-stu-id="92a71-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="92a71-108">Ondersteuning voor overname met de klasse in PowerShell en klasse base DSC-resource</span><span class="sxs-lookup"><span data-stu-id="92a71-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="92a71-109">Fouten opsporen in typen met behulp van de PowerShell-taal</span><span class="sxs-lookup"><span data-stu-id="92a71-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="92a71-110">Genereren en verwerken van uitzonderingen met behulp van formele mechanismen en op het juiste niveau</span><span class="sxs-lookup"><span data-stu-id="92a71-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
