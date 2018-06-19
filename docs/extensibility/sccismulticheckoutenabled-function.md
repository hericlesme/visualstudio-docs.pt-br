---
title: Função SccIsMultiCheckoutEnabled | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af7102a049cd3db072506cbf492799908196df32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136764"
---
# <a name="sccismulticheckoutenabled-function"></a>Função SccIsMultiCheckoutEnabled
Essa função verifica se o plug-in de controle de origem permite vários check-outs em um arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 pbMultiCheckout  
 [out] Especifica se vários check-outs estão habilitados para este projeto (diferente de zero significa que vários check-outs têm suporte).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A verificação foi bem-sucedida.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 O IDE faz duas verificações para determinar se arquivos podem fazer check-out simultaneamente por mais de um usuário. Primeiro, o sistema de controle de origem deve dar suporte a vários check-outs. O plug-in de controle de origem pode especificar esse recurso durante a inicialização, especificando o `SCC_CAP_MULTICHECKOUT`. Depois disso, como uma segunda verificação, o IDE chama esta função para determinar se o projeto atual dá suporte a vários check-outs. Se vários check-outs têm suporte para o projeto selecionado, a plug-in retorna um caso de sucesso de código e define `pbMultiCheckout` como diferente de zero (`TRUE`) ou `FALSE`.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)