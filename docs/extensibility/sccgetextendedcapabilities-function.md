---
title: Função SccGetExtendedCapabilities | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7fd4a42b9c94cb2470f6e7dc7b4904aa890e8a6
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637780"
---
# <a name="sccgetextendedcapabilities-function"></a>Função SccGetExtendedCapabilities
Essa função retorna a recursos adicionais, compatíveis com o plug-in de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle do código-fonte.  
  
 lSccExCaps  
 [in] Um sinalizador que especifica uma funcionalidade estendida para o qual testar (consulte a tabela de código de funcionalidade estendida na [sinalizadores de recurso](../extensibility/capability-flags.md) para os possíveis sinalizadores).  
  
 pbSupported  
 [out] Retorna não zero (`TRUE`) se houver suporte para o recurso especificado; caso contrário, retorna zero (`FALSE`).  
  
## <a name="return-value"></a>Valor retornado  
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A operação de recurso get foi concluída com êxito.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Erro desconhecido ou não especificado ocorreu.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado por demanda. ou seja, quando um recurso precisa ser testado, esse método é chamado para determinar se que o recurso tem suporte. Sinalizador de apenas um por vez é especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in da controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de erro](../extensibility/error-codes.md)   
 [Sinalizadores de recurso](../extensibility/capability-flags.md)