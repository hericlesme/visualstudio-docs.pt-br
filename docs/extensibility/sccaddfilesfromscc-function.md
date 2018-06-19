---
title: Função SccAddFilesFromSCC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc42a7be878ce52f4d951171c6b5cb08e195d564
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137853"
---
# <a name="sccaddfilesfromscc-function"></a>Função SccAddFilesFromSCC
Essa função adiciona uma lista de arquivos do controle de origem para o projeto aberto no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 hWnd  
 [in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.  
  
 lpUser  
 [out no] O nome de usuário (até SCC_USER_SIZE, incluindo o terminador nulo).  
  
 lpAuxProjPath  
 [out no] Auxiliar cadeia de caracteres que identifica o projeto (até `SCC_PRJPATH_`tamanho, incluindo o terminador nulo).  
  
 cFiles  
 [in] Número de arquivos fornecido pelo `lpFilePaths`.  
  
 lpFilePaths  
 [out no] Matriz de nomes de arquivo para adicionar ao projeto atual.  
  
 lpDestination  
 [in] O caminho de destino onde os arquivos devem ser gravados.  
  
 lpComment  
 [in] O comentário a ser aplicado a cada um dos arquivos que está sendo adicionados.  
  
 pbResults  
 [out no] Matriz de sinalizadores de conjunto para indicar êxito (diferente de zero ou verdadeiro) ou falha (zero ou FALSE) para cada arquivo (tamanho da matriz deve ser pelo menos `cFiles` longo).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Projeto não está aberto.|  
|SCC_E_OPNOTPERFORMED|Conexão não está no mesmo projeto, conforme especificado pelo `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Usuário não está autorizado a atualizar o banco de dados.|  
|SCC_E_NONSPECIFICERROR|Erro desconhecido.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)