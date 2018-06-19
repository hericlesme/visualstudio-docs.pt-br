---
title: Função SccDirQueryInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1de32b8502e40c953bd7080d64e56047e6bb5ce9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140362"
---
# <a name="sccdirqueryinfo-function"></a>Função SccDirQueryInfo
Essa função examina uma lista de diretórios totalmente qualificados para o seu status atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 nDirs  
 [in] O número de diretórios selecionados a serem consultados.  
  
 lpDirNames  
 [in] Uma matriz de caminhos totalmente qualificados dos diretórios a serem consultados.  
  
 lpStatus  
 [out no] Uma estrutura de matriz para o plug-in para retornar os sinalizadores de status de controle de origem (consulte [código de Status do diretório](../extensibility/directory-status-code-enumerator.md) para obter detalhes).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A consulta foi bem-sucedida.|  
|SCC_E_OPNOTSUPPORTED|O sistema de controle do código fonte não oferece suporte a esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 A função preenche uma matriz de retorno com uma máscara de bits de bits do `SCC_DIRSTATUS` família (consulte [código de Status do diretório](../extensibility/directory-status-code-enumerator.md)), uma entrada para cada diretório fornecido. A matriz de status é alocada pelo chamador.  
  
 O IDE usa essa função antes de um diretório é renomeado para verificar se o diretório está sob controle do código-fonte consultando se ele tem um projeto correspondente. Se o diretório não está sob controle do código-fonte, o IDE pode fornecer o aviso apropriado para o usuário.  
  
> [!NOTE]
>  Se um plug-in de controle de origem optar por não implementar uma ou mais dos valores de status, o bits não implementadas devem ser definidos como zero.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de Status do diretório](../extensibility/directory-status-code-enumerator.md)