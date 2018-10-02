---
title: Função SccBackgroundGet | Microsoft Docs
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
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 162bbc427b48ee10ea3a0b88837cf012f1c3fd07
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460709"
---
# <a name="sccbackgroundget-function"></a>Função SccBackgroundGet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [função SccBackgroundGet](https://docs.microsoft.com/visualstudio/extensibility/sccbackgroundget-function).  
  
Essa função recupera do controle de origem cada dos arquivos especificados sem interação do usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle do código-fonte.  
  
 nFiles  
 [in] Número de arquivos especificados no `lpFileNames` matriz.  
  
 lpFileNames  
 [no, out] Matriz de nomes de arquivos a serem recuperados.  
  
> [!NOTE]
>  Os nomes devem ser totalmente qualificado de nomes de arquivos local.  
  
 dwFlags  
 [in] Sinalizadores de comando (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Um valor exclusivo associado a esta operação.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Operação concluída com êxito.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Recuperação de um plano de fundo já está em andamento (o plug-in de controle do código-fonte deve retornar isso somente se ele não oferece suporte a operações em lotes simultâneos).|  
|SCC_I_OPERATIONCANCELED|Operação foi cancelada antes de serem concluídas.|  
  
## <a name="remarks"></a>Comentários  
 Essa função sempre é chamada em um thread diferente daquele que carregar o plug-in de controle do código-fonte. Essa função não deve retornar até que ela seja feita; No entanto, ele pode ser chamado várias vezes com várias listas de arquivos, todos ao mesmo tempo.  
  
 O uso do `dwFlags` argumento for igual a [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)

