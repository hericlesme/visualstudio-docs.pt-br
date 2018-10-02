---
title: Função SccGetUserOption | Microsoft Docs
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
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 567dbf987887d203a811a1dc965ecd4a472d5641
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472900"
---
# <a name="sccgetuseroption-function"></a>Função SccGetUserOption
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [função SccGetUserOption](https://docs.microsoft.com/visualstudio/extensibility/sccgetuseroption-function).  
  
Essa função recupera uma variedade de opções específicas do usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle do código-fonte.  
  
 nOption  
 [in] Opção de recuperação (consulte comentários para obter possíveis opções).  
  
 lpVal  
 [out] Valor associado com a opção.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Opção foi recuperada com êxito.|  
|SCC_E_OPNOTSUPPORTED|Não há suporte para a opção.|  
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado.|  
  
## <a name="remarks"></a>Comentários  
 As opções a seguir têm suporte por este comando:  
  
|Opção de usuário|Descrição|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se o usuário deseja fazer check-out da versão local dos arquivos. `lpVal` é atribuída `SCC_USEROPT_COLV_YES` (o usuário deseja fazer check-out de arquivos locais) ou `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de erro](../extensibility/error-codes.md)

