---
title: "Função CvInitProvider | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 15abebb58382674bc7943d7949dfddbc62524c91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cvinitprovider-function"></a>Função CvInitProvider
Inicializa o provedor de marcador. Deve ser chamado antes das outras funções do SDK da Visualização Simultânea.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pGuid`  
 GUID do provedor. Não pode ser NULL.  
  
 `ppProvider`  
 Endereço de uma variável de saída que armazenará o contexto de provedor. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK quando o provedor é inicializado com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)