---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WaitForSome Resource
ms.openlocfilehash: 3ea9dc51cbb00cf6158abf114fdb31fd91307df9
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2017
---
# <a name="dsc-waitforsome-resource"></a>DSC-WaitForSome Resource

> Van toepassing op: Windows PowerShell 5.0 en hoger

De **WaitForAny** Desired State Configuration (DSC)-bron kan worden gebruikt binnen een blok knooppunt in een [DSC-configuratie](configurations.md) afhankelijkheden opgeven voor de configuraties op andere knooppunten.

Deze resource is geslaagd als de resource is opgegeven door de **ResourceName** eigenschap bevindt zich in de gewenste status van een minimum aantal knooppunten (opgegeven door **NodeCount**) gedefinieerd door de **NodeName**  eigenschap. 


## <a name="syntax"></a>Syntaxis

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   | 
|---|---| 
| NodeCount| Het minimale aantal knooppunten dat moet zich in de gewenste status voor deze bron zou lukken.|
| nodeName| De doelknooppunten van afhankelijk zijn van de bron.| 
| resourceName| De naam van de resource afhangen van.| 
| RetryIntervalSec| Het aantal seconden alvorens het opnieuw proberen. Minimumwaarde is 1.| 
| retryCount| Het maximale aantal keren opnieuw proberen.| 
| ThrottleLimit| Het aantal machines tegelijk verbinding maken. Standaard is de nieuwe-cimsession standaardwaarde.| 
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| PsDscRunAsCredential | Zie [gebruik van DSC met gebruikersgegevens](https://docs.microsoft.com/en-us/powershell/dsc/runasuser) |


## <a name="example"></a>Voorbeeld

Zie voor een voorbeeld van het gebruik van deze resource [cross-knooppunt afhankelijkheden opgeven](crossNodeDependencies.md)
