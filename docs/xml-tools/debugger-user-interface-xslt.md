---
title: "Depurador de Interface do usuário (XSLT) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 422dd91a5b8e22bb9859d8ffa10160bdbe77a021
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2017
---
# <a name="debugger-user-interface-xslt"></a>Interface de usuário do depurador (XSLT)
Este tópico descreve as janelas e caixas de diálogo do depurador. Discute somente as partes da interface do usuário que têm o comportamento XSLT- específico de depuração.  
  
 Para obter mais informações, consulte o [referência de Interface de usuário de depuração](../debugger/debugging-user-interface-reference.md).  
  
## <a name="locals-window"></a>A janela locais  
 A janela locais exibe informações sobre todas as variáveis definidos na folha de estilos. A janela locais contém três colunas de informações:  
  
 **Nome**  
 Esta coluna contém os nomes de todos as variáveis locais no escopo atual. Conjuntos de nó têm um controle de árvore que você possa fazer pesquisa detalhadas para consultar suas subpastas.  
  
 **Value**  
 Esta coluna mostra o valor contido por cada variável. O atributo, a instrução de processamento, o comentário, texto, e os nós CDATA exibem o valor de texto do nó. Os nós de namespace exibem URI de namespace.  
  
 **Tipo**  
 Essa coluna identifica o tipo de dados de cada variável listada no **nome** coluna.  
  
 A janela locais também exibe as variáveis predefinidos de contexto que acompanham o contexto de transformação XSLT. A tabela a seguir descreve as variáveis predefinidos de contexto usados pelo depurador XSLT.  
  
|Nome|Descrição|  
|----------|-----------------|  
|`last()`|O tamanho do contexto.|  
|`position()`|A posição, ou número de índice, o nó de contexto, relativo ao tamanho do contexto.|  
|`self::node()`|O valor do nó de contexto.|  
  
## <a name="output-window"></a>Janela Saída  
 A janela de saída mostra todas as mensagens de erro ou exceções de segurança que ocorrem durante a depuração.  
  
 O depurador XSLT usa uma janela separada para exibir a saída do depurador. Essa é a mesma janela usada para exibir a saída de um **Show XSL Output** comando.  
  
## <a name="task-list"></a>Lista de Tarefas  
 A lista de tarefas lista todos os erros de compilação na folha de estilos. Clique duas vezes no erro leva o cursor para a linha com o erro.  
  
 A lista de tarefas inclui todos os erros que ocorrem nos blocos de script no arquivo fonte.  
  
> [!NOTE]
>  O depurador XSLT não tem nenhum aviso, o que nunca aparece na lista de tarefas.  
  
## <a name="breakpoints-window"></a>A janela de pontos de interrupção  
 A janela de pontos de interrupção mostra os pontos de interrupção definidos no projeto atual. Se um ponto de interrupção é adicionado quando a janela está em modo de exibição, a janela é atualizado automaticamente para mostrar o novo ponto de interrupção.  
  
 A janela de pontos de interrupção deve se comportar da mesma maneira que outros depuradores do Visual Studio.  
  
## <a name="command-windowimmediate-window"></a>Janela de comando/janela immediate  
 Não implementado nesta versão do depurador XSLT.  
  
## <a name="watch-window"></a>Observação de janela  
 A janela de observação é usada para avaliar as variáveis. Você também pode alterar os valores das variáveis.  
  
 Variáveis exibidos na janela de observação são para o contexto atual (o item top-most na pilha de chamadas). Se você alterar o contexto, a janela de observação atualiza e exibe as variáveis definidas para esse contexto.  
  
## <a name="call-stack-window"></a>A janela de pilha de chamadas  
 A janela a pilha de chamadas é usada para exibir os nomes de funções na pilha de chamadas, os tipos de parâmetro, e os valores de parâmetro. Informações de pilha de chamadas é mostrada somente quando o programa que está sendo depurado está em um estado de interrupção.  
  
 A pilha de chamadas representa os vários contextos que a execução de fonte está atravessando. Por exemplo, se houver um chamada de modelo “a” ao modelo “b”, o modelo “a” e o modelo “b” aparecem na janela de pilha de chamadas com o contexto atual na parte superior da lista. O usuário pode ver a consulta que está em execução atualmente.  
  
 Se os modelos não têm um nome para o arquivo XSLT, os nomes gerados pelo processador XSLT são usados.  
  
 Clique em um item diferente de aquele na parte superior da lista indica ao visualizador onde a ramificação de execução XSLT ocorreu usando realce padrão de verde e setas verde.  
  
## <a name="quickwatch-dialog-box"></a>Caixa de diálogo QuickWatch  
 O **QuickWatch** caixa de diálogo é usada para avaliar as expressões XPath 1.0. O nó de contexto (o nó de `self::node()` da janela locais) fornece o contexto para a execução da expressão XPath. O resultado de executar a expressão XPath é exibido na janela de observação.  
  
 A lista a seguir descreve algumas restrições na avaliação de expressão XPath.  
  
-   Somente as funções internas XPath são permitidas.  
  
-   XSLT interno funciona como `document()`, `key()`, não é permitido, e assim por diante.  
  
-   As funções definidas pelo usuário não são permitidas.  
  
Para obter mais informações, consulte [como: avalie uma expressão XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## <a name="disassembly-window"></a>A janela de desmontagem  
 A janela de desmontagem mostra o código do assembly que é gerado pelo compilador XSLT. Esta janela pode ser usada da mesma forma como quaisquer outras janelas de desmontagem do Visual Studio.  
  
 Para obter mais informações, [como: usar a janela de desmontagem](../debugger/how-to-use-the-disassembly-window.md).  
  
## <a name="see-also"></a>Consulte também  
 [Depuração XSLT](../xml-tools/debugging-xslt.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Inspecionar variáveis nos Autos e janelas de locais no Visual Studio](../debugger/autos-and-locals-windows.md)