---
title: Função SccUninitialize | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9cec726eaad2e69ea3adfc850df452c2a06f8059
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475060"
---
# <a name="sccuninitialize-function"></a>Função SccUninitialize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [função SccUninitialize](https://docs.microsoft.com/visualstudio/extensibility/sccuninitialize-function).  
  
Essa função limpa alocações ou abra conexões criadas por uma chamada anterior para o [SccInitialize](../extensibility/sccinitialize-function.md) em preparação para desligar o plug-in de controle do código-fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] O ponteiro para a estrutura de contexto plug-in de controle do código-fonte criado na [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A limpeza foi concluída com êxito.|  
  
## <a name="remarks"></a>Comentários  
 O plug-in de controle do código-fonte é responsável por se preparando para ser desligar e liberar memória que o plug-in foi alocada para a estrutura de contexto. A função é chamada uma vez para cada determinada instância de um plug-in. Uma chamada para o [SccInitialize](../extensibility/sccinitialize-function.md) precede essa chamada. Não há projetos ainda podem ser abertos no momento da chamada para `SccUninitialize`.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)

