---
title: Função SccWillCreateSccFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af6da09badf0ffea4846d35fe00b4ca146243d64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="sccwillcreatesccfile-function"></a>Função SccWillCreateSccFile
Esta função determina se o plug-in de controle de origem suporta a criação do MSSCCPRJ. Arquivos SCC para cada um dos arquivos de determinado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 nFiles  
 [in] O número de nomes de arquivos incluídos no `lpFileNames` de matriz, bem como o comprimento do `pbSccFiles` matriz.  
  
 lpFileNames  
 [in] Uma matriz de nomes de arquivo totalmente qualificado para verificar (matriz deve ser alocada pelo chamador).  
  
 pbSccFiles  
 [out no] Matriz na qual deseja armazenar os resultados.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Êxito.|  
|SCC_E_INVALIDFILEPATH|Um dos caminhos na matriz é inválido.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada com uma lista de arquivos para determinar se o plug-in de controle de origem fornece suporte a MSSCCPRJ. Arquivos SCC para cada um dos arquivos de determinado (para obter mais informações sobre o MSSCCPRJ. Arquivos SCC, consulte [MSSCCPRJ. Arquivos SCC](../extensibility/mssccprj-scc-file.md)). Plug-ins de controle de origem pode declarar se eles têm a capacidade de criar MSSCCPRJ. Arquivos SCC declarando `SCC_CAP_SCCFILE` durante a inicialização. Retorna a plug-in `TRUE` ou `FALSE` por arquivo no `pbSccFiles` array para indicar que os arquivos de determinado ter MSSCCPRJ. Suporte do SCC. Se o plug-in retorna um código de êxito da função, os valores na matriz de retorno são respeitados. Em caso de falha, a matriz é ignorada.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Arquivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)