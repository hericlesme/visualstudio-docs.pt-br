---
title: Referência da API (depuração do Visual Studio) | Microsoft Docs
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
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a4348e6e60c722d8116b682386785a8cfba6cde
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466689"
---
# <a name="api-reference-visual-studio-debugging"></a>Referência de API (depuração no Visual Studio)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [referência da API (depuração do Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/api-reference-visual-studio-debugging).  
  
A seção de referência inclui uma visão geral conceitual da API, um guia que mostra a sintaxe e uso para todos os elementos de API e uma variedade de exemplos de código. Todas as referências são listadas em ordem alfabética por categoria.  
  
 A tabela a seguir mostra o comum `HRESULT` valores retornados pelos métodos.  
  
|Nome|Descrição|Valor|  
|----------|-----------------|-----------|  
|S_OK|Êxito.|0x00000000|  
|E_UNEXPECTED|Falha inesperada.|0x8000FFFF|  
|E_NOTIMPL|Não implementado.|0x80004001|  
|E_OUTOFMEMORY|Não há memória suficiente para concluir a operação.|0x8007000E|  
|E_INVALIDARG|Um ou mais argumentos são inválidos.|0x80070057|  
|E_NOINTERFACE|Não há suporte para essa interface.|0x80004002|  
|E_POINTER|Ponteiro inválido.|0x80004003|  
|E_HANDLE|Identificador inválido.|0x80070006|  
|E_ABORT|Operação anulada.|0x80004004|  
|E_FAIL|Falha inesperada.|0x80004005|  
|E_ACCESSDENIED|Erro de acesso geral negado.|0x80070005|  
  
> [!NOTE]
>  Quando um [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] depuração método retorna `S_OK`, supõe-se que todos os ponteiros de parâmetro são válidos, ou seja, nenhuma validação é realizada em out ponteiros de parâmetro quando `S_OK` é retornado.  
  
> [!NOTE]
>  Inválido ou `NULL` [parâmetros out] pode causar falhas no IDE.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Extensibilidade do depurador do Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)

