---
title: "Funções de retorno de chamada implementadas pelo IDE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3c1845a82947286800145ff898f8f49f8c3c2477
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funções de retorno de chamada implementadas pelo IDE
Para fazer a integração com o ambiente de desenvolvimento integrado (IDE) como contínua possível e para fornecer uma experiência unificada do usuário final, o plug-in de controle de origem pode usar funções de retorno de chamada que são implementadas pelo IDE. O plug-in pode chamar essas funções em momentos apropriados durante uma operação de controle de origem para passar informações para o IDE; o IDE pode exibir essas informações como os elementos inseridos na sua UI nativo. O usuário tem uma experiência menos fragmentada neste cenário que se o plug-in empregado sua própria interface do usuário.  
  
 O arquivo de cabeçalho necessário é scc.h. O local padrão é \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Ele também está na pasta VSIP com a amostra de plug-in de controle do código-fonte em \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>Nesta seção  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccOpenProject](../extensibility/sccopenproject-function.md) para exibir mensagens de controle de origem de plug-in por meio do IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccPopulateList](../extensibility/sccpopulatelist-function.md) quando o IDE não tem acesso completo a informações que estão disponíveis somente para o plug-in como uma lista completa dos arquivos sob controle de versão de controle de origem.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccQueryChanges](../extensibility/sccquerychanges-function.md) operação.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operação.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Descreve a função de retorno de chamada definida por uma chamada para o [SccSetOption](../extensibility/sccsetoption-function.md) que permite que o plug-in para se comunicar alterações de nome de volta para o IDE de controle de origem.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Abre um projeto.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina a lista de arquivos para o seu status atual. Além disso, usa o `pfnPopulate` função para notificar o chamador quando um arquivo não corresponde aos critérios para o `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Examina uma lista de diretórios e arquivos em um projeto ou projetos que estão sob o controle de origem. Cada nome de diretório e arquivo encontrado é passado para uma função de retorno de chamada.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Examina as alterações de nome que foram feitas em uma lista de arquivos. Cada nome de arquivo é passado para uma função de retorno de chamada juntamente com seu status de alteração.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Define uma ampla variedade de opções. Cada opção inicia com `SCC_OPT_xxx` e tem seu próprio conjunto definido de valores.  
  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)  
 Descreve o conteúdo da seção de referência do SDK do plug-in de controle de origem.