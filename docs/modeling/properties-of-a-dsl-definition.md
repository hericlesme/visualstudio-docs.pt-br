---
title: "Propriedades de uma definição de DSL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5ccf6937aa3c317feb81a907348d41e4d322d346
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-a-dsl-definition"></a>Propriedades de uma definição de DSL
Definem propriedades de DslDefinition *linguagem específica de domínio* propriedades de definição, como numeração de versão. As propriedades de DslDefinition aparecem no **propriedades** janela quando você clica em uma área aberta do diagrama no *Designer de linguagem específica de domínio*.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition tem as propriedades na tabela a seguir:  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Modificador de acesso|Determina se o modificador de acesso para a classe de domínio público ou interno.|públicos|  
|Atributos personalizados|Atributos para a classe de domínio de definição personalizada.<br /><br /> **Observação** Use o botão Procurar para adicionar um atributo.|\<none>|  
|Nome da empresa|O nome do nome da empresa no registro do sistema.|Nome da empresa atual|  
|Nome|O nome desta classe de domínio.|Nome atual|  
|Namespace|O namespace associado a essa classe de domínio.|Namespace atual|  
|Guid do pacote|O guid para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gerado para este DSL de pacote.|\<none>|  
|Namespace do pacote|O namespace para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gerado para este DSL de pacote.|\<none>|  
|Nome do produto|O nome do produto que será registrado para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gerado para este DSL de pacote.|\<none>|  
|Observações|Anotações associadas a essa classe de domínio.|\<none>|  
|Descrição|Descrição para esta classe de domínio.|\<none>|  
|Nome de Exibição|O nome que será exibido no designer gerado para esta classe de domínio.|\<none>|  
|Palavra-chave de ajuda|A palavra-chave ajuda associada a essa classe de domínio.|\<none>|  
|Build|O número de compilação incremental para esta definição de linguagem específica de domínio.|0|  
|Versão principal|O número de compilação principal incrementais para esta definição de linguagem específica de domínio.|1|  
|Versão secundária|O número de compilação secundária incrementais para esta definição de linguagem específica de domínio.|0|  
|Revisão|A versão incremental build número para esta definição de linguagem específica de domínio.|0|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)