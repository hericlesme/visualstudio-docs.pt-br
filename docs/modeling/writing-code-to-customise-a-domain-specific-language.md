---
title: "Escrevendo código para personalizar uma linguagem específica do domínio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: "29"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e7b5fc639e93061a4abd0acbfc1425223d673282
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Escrevendo código para personalizar uma linguagem específica do domínio
Esta seção mostra como usar código personalizado para acessar, modificar ou criar um modelo em uma linguagem específica de domínio.  
  
 Há vários contextos nos quais você pode escrever código que funciona com uma DSL:  
  
-   **Comandos personalizados.** Você pode criar um comando que os usuários podem chamar clicando no diagrama, e que pode modificar o modelo. Para obter mais informações, consulte [como: adicionar um comando no menu de atalho](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
-   **Validação.** Você pode escrever código que verifica se o modelo está no estado correto. Para obter mais informações, consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **Substituindo o comportamento padrão.** Você pode modificar os vários aspectos do código que é gerado a partir de DslDefinition.dsl. Para obter mais informações, consulte [substituir e estender as Classes geradas pelo](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Transformação de texto.** Você pode criar modelos de texto que contêm código que acessa um modelo e gera um arquivo de texto, por exemplo, para gerar o código do programa. Para obter mais informações, consulte [código de geração de uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **Outras extensões do Visual Studio.** Você pode escrever extensões VSIX separadas que ler e modificar modelos. Para obter mais informações, consulte [como: abrir um modelo de arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Instâncias de classes que você define no DslDefinition.dsl são mantidas em uma estrutura de dados chamada o *armazenamento em memória* (IMS) ou *repositório*. As classes que definem uma DSL sempre usam um repositório de como um argumento para o construtor. Por exemplo, se seu DSL define uma classe chamada de exemplo:  
  
 `Example element = new Example (theStore);`  
  
 Manter objetos no armazenamento (em vez de objetos apenas como comuns) oferece vários benefícios.  
  
-   **Transações**. Você pode agrupar uma série de alterações relacionadas em uma transação:  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Se ocorrer uma exceção durante as alterações, para que o final Commit () não é executada, o repositório será redefinido para seu estado anterior. Isso ajuda a garantir que os erros de não deixar o modelo em um estado inconsistente. Para obter mais informações, consulte [navegar e atualizar um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Relações binárias**. Se você definir uma relação entre duas classes, instâncias em ambas as extremidades têm uma propriedade que navega para a outra extremidade. As duas extremidades sempre são sincronizadas. Por exemplo, se você definir uma relação de parenthood com funções nomeadas pais e filhos, você poderia escrever:  
  
     `John.Children.Add(Mary)`  
  
     Ambas as expressões a seguir forem verdadeiras:  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     Você também pode obter o mesmo efeito por meio da gravação:  
  
     `Mary.Parents.Add(John)`  
  
     Para obter mais informações, consulte [navegar e atualizar um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Regras e eventos**. Você pode definir regras que é acionam sempre que forem feitas alterações especificadas. As regras são usadas, por exemplo, para manter as formas no diagrama atualizado com os elementos de modelo que apresentam. Para obter mais informações, consulte [respondendo a e propagando alterações](../modeling/responding-to-and-propagating-changes.md).  
  
-   **Serialização**. O armazenamento fornece uma maneira padrão para serializar os objetos que ele contém um arquivo. Você pode personalizar as regras para serialização e desserialização. Para obter mais informações, consulte [serialização de XML e armazenamento de arquivo personalizando](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md)