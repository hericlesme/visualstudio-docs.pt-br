---
title: Enumeradores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84102435092096b7154a46100e9d857a31537482
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127224"
---
# <a name="enumerators"></a>Enumeradores
Esta seção lista os tipos de dados em que a API de plug-in de controle de origem que o plug-in de controle de origem deve saber sobre enumerador.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Código de comando](../extensibility/command-code-enumerator.md)  
 Enumera as opções para o [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) funções.  
  
 [Message](../extensibility/message-enumerator.md)  
 Enumera os sinalizadores usados para o retorno de chamada de impressão, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Código de Status do arquivo](../extensibility/file-status-code-enumerator.md)  
 Contém valores de constantes nomeados que especificam o estado de um arquivo sob controle de origem.  
  
 [Código de Status do diretório](../extensibility/directory-status-code-enumerator.md)  
 Contém valores de constantes nomeados que especificam o estado de um diretório no controle de origem.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um plug-in de controle do código-fonte](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define o SDK de plug-in de controle de origem e descreve os recursos incluídos.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Solicita ao usuário para as opções avançadas para o comando fornecido.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina a lista de arquivos para o seu status atual. Além disso, usa o `pfnPopulate` função para notificar o chamador quando um arquivo não corresponde aos critérios para o `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccOpenProject](../extensibility/sccopenproject-function.md) para exibir mensagens de controle de origem de plug-in por meio do IDE.  
  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)  
 Fornece uma lista completa de todos os elementos da API de plug-in de controle de origem.