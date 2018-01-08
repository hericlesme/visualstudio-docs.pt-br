---
title: "Como: usar transações para atualizar o modelo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: "7"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e117b6fad7a558d002bf0e8689c56dbc2947644f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Como usar transações para atualizar o modelo
Transações Certifique-se de que as alterações feitas no armazenamento são tratadas como um grupo. As alterações que são agrupadas podem ser confirmadas ou revertidas como uma única unidade.  
  
 Sempre que o código de programa modifica, adiciona ou exclui qualquer elemento no repositório [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] visualização e modelagem de SDK, ele deve fazer isso dentro de uma transação. Deve haver uma instância ativa do <xref:Microsoft.VisualStudio.Modeling.Transaction> associado à loja quando ocorre a alteração. Isso se aplica a todos os elementos de modelo, relações, formas, diagramas e suas propriedades.  
  
 O mecanismo de transação ajuda a evitar estados inconsistentes. Se ocorrer um erro durante uma transação, todas as alterações serão revertidas. Se o usuário executa um comando Desfazer, cada transação recente é tratada como uma única etapa. O usuário não pode desfazer partes de uma alteração recente, a menos que você explicitamente colocá-los em transações separadas.  
  
## <a name="opening-a-transaction"></a>Abrir uma transação  
 É o método mais conveniente de gerenciar uma transação com um `using` instrução incluída em um `try...catch` instrução:  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 Se uma exceção que impede que o último `Commit()` ocorre durante as alterações, o repositório será redefinido para seu estado anterior. Isso ajuda a garantir que os erros de não deixar o modelo em um estado inconsistente.  
  
 Você pode tornar qualquer número de alterações dentro de uma transação. Você pode abrir novas transações dentro de uma transação ativa. As transações aninhadas devem confirmar ou reverter antes do término da transação que contém. Para obter mais informações, consulte o exemplo para o <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> propriedade.  
  
 Para tornar as alterações permanentes, você deve `Commit` a transação antes de ser descartado. Se ocorrer uma exceção que não é capturado dentro da transação, o repositório será redefinido para seu estado antes das alterações.  
  
## <a name="rolling-back-a-transaction"></a>Reverter uma transação  
 Para garantir que o armazenamento permanece no ou será revertido para seu estado antes da transação, você pode usar qualquer uma dessas táticas:  
  
1.  Gere uma exceção não detectado dentro do escopo da transação.  
  
2.  Explicitamente reverta a transação:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>As transações não afetam a não armazenar objetos  
 Transações somente controlam o estado do repositório. Eles não é possível desfazer alterações parciais que foram feitas para itens externos como arquivos, bancos de dados ou objetos que você tenha declarado com tipos comuns de fora da definição de DSL.  
  
 Se uma exceção pode deixar essa alteração inconsistente com o armazenamento, você deve lidar com essa possibilidade no manipulador de exceção. Uma maneira de garantir que os recursos externos permanecerem sincronizados com os objetos de armazenamento é acoplar cada objeto externo a um elemento na loja usando manipuladores de eventos. Para obter mais informações, consulte [manipuladores de propagar alterações fora do modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Regras de incêndio no final de uma transação  
 No final de uma transação antes da transação é descartada, as regras anexadas a elementos no repositório são disparadas. Cada regra é um método que é aplicado a um elemento de modelo que foi alterado. Por exemplo, há regras "corrigir" que atualizar o estado de uma forma quando o elemento de modelo foi alterada e que criam uma forma, quando um elemento de modelo é criado. Não há nenhuma ordem de acionamento especificado. Outra regra pode ser acionado por uma alteração feita por uma regra.  
  
 Você pode definir suas próprias regras. Para obter mais informações sobre regras, consulte [respondendo a e propagando alterações](../modeling/responding-to-and-propagating-changes.md).  
  
 As regras não são acionados após um Desfazer, uma restauração ou um comando de reversão.  
  
## <a name="transaction-context"></a>Contexto de transação  
 Cada transação tem um dicionário no qual você pode armazenar informações que você deseja:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Isso é especialmente útil para transferir informações entre as regras.  
  
## <a name="transaction-state"></a>Estado de transação  
 Em alguns casos, que você precisa evitar propagar uma alteração, se a alteração é causada por desfazer ou refazer uma transação. Isso pode acontecer, por exemplo, se você gravar um manipulador de valor de propriedade que pode atualizar o outro valor no repositório. Porque a operação de desfazer redefine todos os valores no armazenamento para seus estados anteriores, não é necessário calcular valores atualizados. Use este código:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Regras podem ser acionado quando o armazenamento está sendo carregado inicialmente de um arquivo. Para evitar a responder a essas alterações, use:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```