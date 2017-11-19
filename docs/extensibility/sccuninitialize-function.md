---
title: "Função SccUninitialize | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUninitialize
helpviewer_keywords: SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 434987489feccd5f576e04d69afbb4b39e1dc754
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="sccuninitialize-function"></a>Função SccUninitialize
Essa função limpa qualquer alocações ou criadas por uma chamada anterior para as conexões abertas a [SccInitialize](../extensibility/sccinitialize-function.md) em preparação para desligar o plug-in de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] O ponteiro para a estrutura de contexto de plug-in de controle de origem criado na [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A limpeza foi concluída com êxito.|  
  
## <a name="remarks"></a>Comentários  
 O plug-in de controle de origem é responsável para preparar a ser desligada e liberar memória que o plug-in foi alocada para a estrutura de contexto. A função é chamada uma vez para cada determinada instância de um plug-in. Uma chamada para o [SccInitialize](../extensibility/sccinitialize-function.md) precede esta chamada. Não há projetos ainda podem ser abertos no momento da chamada para `SccUninitialize`.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)