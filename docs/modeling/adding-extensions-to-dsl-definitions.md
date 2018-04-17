---
title: Adicionando extensões para definições de DSL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a689d902a58eb747cbaec0bf7cebd740ade3e9bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="adding-extensions-to-dsl-definitions"></a>Adicionando extensões a definições de DSL
Extensão de definição de DSL permite que você crie um pacote de extensões para uma domínio específico DSL (linguagem). Extensão de DSL, que está contido em um Visual Studio Integration extensão (VSIX), pode ser instalado no computador do usuário da mesma maneira como uma DSL. Os recursos adicionais podem ser habilitados e desabilitados em tempo de execução dinamicamente. DSLs não precisam ser explicitamente criado para a extensão e as extensões podem ser criadas mais tarde ou por terceiros sem alterar o DSL estendida.  
  
 Os recursos adicionais podem incluir o seguinte:  
  
-   Propriedades de elementos de modelo e apresentação  
  
-   Decoradores para formas e conectores  
  
-   Classes, relacionamentos, formas e conectores  
  
-   Restrições de validação  
  
-   Guias e itens de caixa de ferramentas  
  
 Um usuário de uma DSL estendido pode criar e salvar um modelo que contém as instâncias dos recursos adicionais, e eles podem ser lidos por outros usuários que tenham instalado a extensão apropriada. Os usuários que não instalaram a extensão não é possível usar os recursos adicionais, mas eles podem atualizar e salvar um modelo sem perder os recursos adicionais.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Consulte também  
 [Postagens de blog relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
