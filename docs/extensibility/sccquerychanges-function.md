---
title: Função SccQueryChanges | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d887c0cea989fa6a955edc2f39b9667e7421093d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="sccquerychanges-function"></a>Função SccQueryChanges
Essa função enumera uma lista de arquivos, fornecendo informações sobre as alterações de nome para cada arquivo por meio de uma função de retorno de chamada especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 nFiles  
 [in] Número de arquivos em `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nomes de arquivo para obter informações sobre.  
  
 pfnCallback  
 [in] Função de retorno de chamada a ser chamada para cada nome de arquivo na lista (consulte [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) para obter detalhes).  
  
 pvCallerData  
 [in] Valor que será passado inalterados para a função de retorno de chamada.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|O processo de consulta foi concluído com êxito.|  
|SCC_E_PROJNOTOPEN|O projeto não foi aberto no controle de origem.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle de origem, provavelmente devido a problemas de rede ou de contenção.|  
|SCC_E_NONSPECIFICERROR|Ocorreu um erro geral ou não especificado.|  
  
## <a name="remarks"></a>Comentários  
 As alterações que está sendo consultadas para são para o namespace: especificamente, renomear, adicionando e removendo um arquivo.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Códigos de erro](../extensibility/error-codes.md)