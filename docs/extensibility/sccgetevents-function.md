---
title: Função SccGetEvents | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79e517d87acd61eafcd2eb0a12f5a8978912db81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136738"
---
# <a name="sccgetevents-function"></a>Função SccGetEvents
Essa função recupera um evento de status na fila.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 [in] A estrutura de contexto de plug-in de controle de origem.  
  
 lpFileName  
 [out no] O buffer em que o plug-in de controle de origem coloca o nome de arquivo retornado (até caracteres MAX_PATH).  
  
 lpStatus  
 [out no] Retorna o código de status (consulte [código de Status do arquivo](../extensibility/file-status-code-enumerator.md) possíveis valores).  
  
 pnEventsRemaining  
 [out no] Retorna o número de entradas de permanecer na fila após esta chamada. Se esse número for grande, o chamador pode decidir chamar o [SccQueryInfo](../extensibility/sccqueryinfo-function.md) para obter as informações de uma vez.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Obter eventos foi bem-sucedida.|  
|SCC_E_OPNOTSUPPORTED|Não há suporte para essa função.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada durante o processamento ocioso para ver se houve todas as atualizações de status de arquivos sob controle de origem. O plug-in de controle do código-fonte mantém o status de todos os arquivos que ele conheça e sempre que uma alteração de status é indicado pelo plug-in, o status e o arquivo associado são armazenadas em uma fila. Quando `SccGetEvents` é chamado, a parte superior elemento da fila é recuperado e retornado. Essa função é restrito para retornar somente informações armazenadas em cache anteriormente e deve ter um retorno muito rápido (ou seja, nenhuma leitura do disco ou solicitar o sistema de controle de origem do status); Caso contrário, o desempenho do IDE pode começar a ser degradada.  
  
 Se não houver nenhuma atualização de status para o relatório, o plug-in de controle de origem armazena uma cadeia de caracteres vazia no buffer apontado pelo `lpFileName`. Caso contrário, o plug-in armazena o nome de caminho completo do arquivo para o qual as informações de status foi alterado e retorna o código de status apropriado (um dos valores detalhados em [código de Status do arquivo](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Código de Status do arquivo](../extensibility/file-status-code-enumerator.md)