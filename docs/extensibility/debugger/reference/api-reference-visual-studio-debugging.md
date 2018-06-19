---
title: Referência da API (depuração no Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c9007d679e36e2aa6dbab41074338395434be42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103234"
---
# <a name="api-reference-visual-studio-debugging"></a>Referência da API (depuração no Visual Studio)
A seção de referência inclui uma visão geral conceitual da API, um guia que mostra a sintaxe e uso de todos os elementos de API e uma variedade de exemplos de código. Todas as referências são listadas em ordem alfabética por categoria.  
  
 A tabela a seguir mostra comuns `HRESULT` valores retornados pelos métodos.  
  
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
>  Quando um [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depuração método retorna `S_OK`, presume-se que todo ponteiros de parâmetro são válidos, ou seja, nenhuma validação é realizada no limite ponteiros de parâmetro quando `S_OK` é retornado.  
  
> [!NOTE]
>  Inválido ou `NULL` [parâmetros out] pode causar falhas no IDE.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Extensibilidade do depurador do Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)