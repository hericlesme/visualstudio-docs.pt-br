---
title: IDebugDocumentPosition2::GetRange | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4a80bebba1000c73af2d7e2cfd05e67fa44b1b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtém o intervalo para essa posição do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBegPosition`  
 [out no] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura que é preenchida com a posição inicial. Defina este argumento como um valor nulo se essas informações não são necessárias.  
  
 `pEndPosition`  
 [out no] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura que é preenchida com a posição final. Defina este argumento como um valor nulo se essas informações não são necessárias.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O intervalo especificado em uma posição de documento para um ponto de interrupção de local é usado pelo mecanismo de depuração (DE) para procurar uma instrução que realmente contribui código em frente. Por exemplo, considere o seguinte código:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Linha 5 não contribui nenhum código para o programa que está sendo depurado. Se desejar que o depurador que define o ponto de interrupção na linha 5 DE para procurar uma determinada quantidade para a primeira linha que contribui com o código, o depurador deve especificar um intervalo que inclui linhas de candidato adicionais em que um ponto de interrupção pode ser posicionado corretamente. O DE seria, em seguida, avance a pesquisa por essas linhas até que ela encontrou uma linha que pode aceitar um ponto de interrupção.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)