---
title: POPLISTFUNC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: POPDIRLISTFUNC
helpviewer_keywords: POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 281b18d1e4e802646635cfe354355762014ad40e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="poplistfunc"></a>POPLISTFUNC
Esse retorno de chamada é fornecido para o [SccPopulateList](../extensibility/sccpopulatelist-function.md) pelo IDE e é usada pelo plug-in de controle de origem para atualizar uma lista de arquivos ou diretórios (também é fornecido para o `SccPopulateList` função).  
  
 Quando um usuário escolhe o **obter** comando no IDE, o IDE exibe uma lista de todos os arquivos que o usuário pode obter. Infelizmente, o IDE não sabe a lista exata de todos os arquivos que o usuário pode obter; somente o plug-in tem essa lista. Se outros usuários adicionar arquivos ao projeto de controle do código fonte, esses arquivos devem aparecer na lista, mas o IDE não sabe sobre eles. O IDE criará uma lista dos arquivos que ele achar que o usuário pode obter. Antes de exibir essa lista para o usuário, ele chama o [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` fornecendo o plug-in de controle de origem a oportunidade de adicionar e excluir arquivos da lista.  
  
## <a name="signature"></a>Assinatura  
 O plug-in de controle de origem modifica a lista chamando uma função IDE implementado com o seguinte protótipo:  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pvCallerData  
 O `pvCallerData` parâmetro passado pelo chamador (IDE) para o [SccPopulateList](../extensibility/sccpopulatelist-function.md). O plug-in de controle de origem deve pressupor que nada sobre o conteúdo desse parâmetro.  
  
 fAddRemove  
 Se `TRUE`, `lpFileName` é um arquivo que deve ser adicionado à lista de arquivos. Se `FALSE`, `lpFileName` é um arquivo que deve ser excluído da lista de arquivos.  
  
 nStatus  
 Status de `lpFileName` (uma combinação da `SCC_STATUS` bits; consulte [código de Status do arquivo](../extensibility/file-status-code-enumerator.md) para obter detalhes).  
  
 lpFileName  
 Caminho completo do diretório do nome do arquivo para adicionar ou excluir da lista.  
  
## <a name="return-value"></a>Valor de retorno  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`TRUE`|O plug-in poderá chamar essa função.|  
|`FALSE`|Houve um problema no lado do IDE (como um fora da situação de memória). O plug-in deve interromper a operação.|  
  
## <a name="remarks"></a>Comentários  
 Para cada arquivo que deseja que o plug-in de controle de origem para adicionar ou excluir da lista de arquivos, ele chama esta função, passando o `lpFileName`. O `fAddRemove` sinalizador indica um novo arquivo para adicionar à lista ou um arquivo antigo a ser excluído. O `nStatus` parâmetro fornece o status do arquivo. Quando o plug-in do SCC concluiu a adição e exclusão de arquivos, ele retorna do [SccPopulateList](../extensibility/sccpopulatelist-function.md) chamar.  
  
> [!NOTE]
>  O `SCC_CAP_POPULATELIST` bit de recurso é necessária para o Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Código de Status do arquivo](../extensibility/file-status-code-enumerator.md)