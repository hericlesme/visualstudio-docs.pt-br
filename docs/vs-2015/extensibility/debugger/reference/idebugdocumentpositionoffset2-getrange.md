---
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e00fd6bbc86992d8f3a79810857e1d7496f025b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460464"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugDocumentPositionOffset2::GetRange](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange).  
  
Recupera o intervalo para a posição atual do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwBegOffset`  
 [no, out] Deslocamento da posição inicial do intervalo. Defina esse parâmetro como um valor nulo se essa informação não é necessária.  
  
 `pdwEndOffset`  
 [no, out] Deslocamento para a posição final do intervalo. Defina esse parâmetro como um valor nulo se essa informação não é necessária.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O intervalo especificado em uma posição de documento para um ponto de interrupção de local é usado pelo mecanismo de depuração (DE) para procurar uma instrução que contribui, na verdade, o código com antecedência. Por exemplo, considere o seguinte código:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Linha 5 contribui com nenhum código para o programa que está sendo depurado. Se quiser que o depurador que define o ponto de interrupção na linha 5 DE para pesquisar adiante uma certa quantidade para a primeira linha que contribui com o código, o depurador seria especificar um intervalo que inclui linhas de candidato adicional em que um ponto de interrupção pode ser colocado corretamente. O DE, em seguida, pesquisaria para frente por meio dessas linhas até que ela encontrou uma linha que poderia aceitar um ponto de interrupção.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)

