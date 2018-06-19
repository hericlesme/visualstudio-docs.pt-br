---
title: Função SccDirDiff | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d2bea7816375da1131f557ebcbe206056f347f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138016"
---
# <a name="sccdirdiff-function"></a>Função SccDirDiff
Esta função exibe as diferenças entre o diretório local atual no disco do cliente e o projeto correspondente no controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 lpDirName  
 [in] Caminho totalmente qualificado para o diretório local para o qual mostram uma diferença de visual.  
  
 dwFlags  
 [in] Sinalizadores de comando (consulte comentários seção).  
  
 pvOptions  
 [in] Opções de plug-in específico de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|O diretório em disco é o mesmo que o projeto no controle do código fonte.|  
|SCC_I_FILESDIFFER|O diretório em disco é diferente do projeto no controle do código fonte.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
|SCC_E_FILENOTCONTROLLED|O diretório não está sob controle do código fonte.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção. Recomenda-se uma nova tentativa.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha não específica.|  
|SCC_E_FILENOTEXIST|Não foi possível encontrar o diretório local.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é usada para instruir o plug-in para exibir ao usuário uma lista de alterações para um diretório especificado do controle de origem. O plug-in abre sua própria janela, em um formato de sua escolha, para exibir as diferenças entre o diretório do usuário no disco e o projeto correspondente sob controle de versão.  
  
 Se o plug-in oferece suporte à comparação de diretórios em todos os, deve suportar comparação dos diretórios em uma base de nome de arquivo mesmo se não há suporte para as opções "comparação rápida".  
  
|`dwFlags`|Interpretação|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Comparação de maiusculas e minúsculas (pode ser usado para comparação rápida ou visual).|  
|SCC_DIFF_IGNORESPACE|Ignora o espaço em branco (pode ser usado para comparação rápida ou visual).|  
|SCC_DIFF_QD_CONTENTS|Se o plug-in de controle de origem com suporte, silenciosamente compara o diretório, byte por byte.|  
|SCC_DIFF_QD_CHECKSUM|Se suportado pelo plug-in, silenciosamente compara o diretório por meio de uma soma de verificação ou, se não houver suporte, volta ao SCC_DIFF_QD_CONTENTS.|  
|SCC_DIFF_QD_TIME|Se suportado pelo plug-in, silenciosamente compara o diretório por meio de seu carimbo de hora ou, se não houver suporte, volta em SCC_DIFF_QD_CHECKSUM ou SCC_DIFF_QD_CONTENTS.|  
  
> [!NOTE]
>  Essa função usa os mesmos sinalizadores de comando como o [SccDiff](../extensibility/sccdiff-function.md). No entanto, um plug-in de controle de origem pode optar por não dar suporte à operação de "comparação rápida" para diretórios.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)