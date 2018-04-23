---
title: Plug-ins de controle de origem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a3395275938d78178f6f39ccd0f67dca01194bcc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-plug-ins"></a>Plug-ins de controle de origem
A seção de referência de SDK de plug-in de controle de origem contém a especificação de interface completa que permite que os sistemas de controle de origem ser integrado com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Especifica a sintaxe e semântica das várias funções e tipos de dados que o plug-in de controle de origem deve implementar a interface com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)  
 Lista as funções que devem ser implementadas pelo plug-in de controle de origem para manter a conformidade com a API de plug-in de controle de origem.  
  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Descreve as funções que o plug-in de controle de origem usa para passar informações para o IDE enquanto alguns comandos são executados.  
  
 [Enumeradores](../extensibility/enumerators.md)  
 Lista os tipos de dados em que a API de plug-in de controle de origem que o plug-in de controle de origem deve saber sobre enumerador.  
  
 [Sinalizadores de recurso](../extensibility/capability-flags.md)  
 Descreve o `SCC_CAP_xxx` sinalizadores, que são indicar recursos do provedor.  
  
 [Sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)  
 Lista os sinalizadores que são úteis no contexto de comandos específicos.  
  
 [Códigos de erro](../extensibility/error-codes.md)  
 Lista de valores de erro comuns retornados por funções como `SCCTRN`.  
  
 [Cadeias de caracteres usadas como chaves para localizar um plug-in de controle do código-fonte](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Descreve as chaves para acessar o registro para localizar o controle de origem plug-in.  
  
 [Arquivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Descreve um arquivo do lado do cliente que contém informações opacas para o IDE, mas que é usado pelo plug-in de controle do código-fonte para localizar a solução ou projeto no controle de versão.  
  
 [Práticas recomendadas para implementar um plug-in de controle do código-fonte](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Fornece uma coleção de lembretes técnicas importantes para lembrar enquanto você estiver implementando a API de plug-in de controle de origem.  
  
 [Restrições aos comprimentos de cadeia de caracteres](../extensibility/restrictions-on-string-lengths.md)  
 Descreve as limitações na API de plug-in de controle de origem nos comprimentos das cadeias de caracteres usadas em várias funções.  
  
 [Glossário](../extensibility/source-control-plug-in-glossary.md)  
 Fornece termos úteis e suas definições para ler a documentação do SDK de plug-in de controle de origem.  
  
 [Como desativar avisos de compatibilidade para plug-ins de controle do código-fonte](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Descreve como desabilitar avisos.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Exemplo de plug-in de controle do código-fonte](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Fornece um exemplo de recursos de plug-in de controle de origem.  
  
 [Guia de teste para plug-ins de controle do código-fonte](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Descreve os procedimentos de teste relacionados a um plug-in de controle de origem.  
  
 [Criar um plug-in de controle do código-fonte](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Discute como criar um plug-in de controle de origem que fornece funcionalidade de controle de origem enquanto você estiver usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface de usuário de controle de origem (UI).  
  
 [Referência do SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Apresenta uma lista de tópicos de referência.