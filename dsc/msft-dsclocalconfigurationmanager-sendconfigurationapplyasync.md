---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893890"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager

Het configuratiebestand voor asynchroon verzendt naar de beheerd knooppunt en maakt gebruik van de Agent configureren om toe te passen van de configuratie.

## <a name="syntax"></a>Syntaxis

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parameters

*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.

*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.

*jobId* \[in\] de ID van de taak voor voor het verzenden van de configuratie.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)