---
title: Criar um mapa visual da pilha de chamadas | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5fc0025c9d7870b0de042922d87d3a23d7728c5
ms.sourcegitcommit: 064f8678f4a918e1dce60285090a9803d37dc34b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2018
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-in-visual-studio-enterprise"></a>Criar um mapa visual da pilha de chamadas durante a depuração no Visual Studio Enterprise
Crie um mapa de código para rastrear visualmente a pilha de chamadas durante a depuração. Você pode fazer anotações no mapa para acompanhar o que o código está fazendo, de modo a se concentrar na localização de bugs.

 Itens necessários:  
  
-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   Código que você pode depurar, como Visual c#, Visual Basic, C++, JavaScript ou X + +  

Aqui está uma visão geral de um mapa de código:
  
 ![Depuração com pilhas de chamadas em mapas de código](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")  
  
 Consulte:  
  
-   [Vídeo: Depurar visualmente com a integração do depurador mapa de código (canal 9)](http://go.microsoft.com/fwlink/?LinkId=293418)  
  
-   [Mapear a pilha de chamadas](#MapStack)  
  
-   [Verifique as observações sobre o código](#MakeNotes)  
  
-   [Atualizar o mapa com a seguinte pilha de chamadas](#UpdateMap)  
  
-   [Adicione o código relacionado ao mapa](#AddRelatedCode)  
  
-   [Localizar erros usando o mapa](#FindBugs)  
  
-   [P E R](#QA)  
  
 Para obter detalhes sobre os comandos e as ações que você pode usar ao trabalhar com mapas de código, consulte [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).  
  
##  <a name="MapStack"></a> Mapear a pilha de chamadas  
  
1.  Inicie a depuração. (Teclado: **F5**)  
  
2.  Depois que o aplicativo entra no modo de interrupção ou entrar em uma função, escolha **mapa de código**. (Teclado: **Ctrl** + **Shift** + **`**)  
  
     ![Escolha o mapa de código para iniciar a pilha de chamadas de mapeamento](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap_ChooseCodeMap")  
  
     A pilha de chamadas atual aparece em laranja em um novo mapeamento de código:  
  
     ![Consulte a pilha de chamadas no mapa de códigos](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")  
  
     O mapa será atualizado automaticamente enquanto você continua a depuração. Consulte [atualizar o mapa com a seguinte pilha de chamadas](#UpdateMap).  
  
##  <a name="MakeNotes"></a> Verifique as observações sobre o código  
 Adicione comentários para acompanhar o que está acontecendo no código. Para adicionar uma nova linha em um comentário, pressione **Shift + Return**.  
  
 ![Adicione um comentário para a pilha de chamadas no mapa de códigos](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")  
  
##  <a name="UpdateMap"></a> Atualizar o mapa com a seguinte pilha de chamadas  
 Execute o aplicativo até o próximo ponto de interrupção ou siga uma função. O mapa adiciona uma nova pilha de chamadas.  
  
 ![Mapa de código de atualização com a seguinte pilha de chamadas](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")  
  
##  <a name="AddRelatedCode"></a> Adicione o código relacionado ao mapa  
 Agora você tem um mapa - o em seguida? Se você estiver trabalhando com Visual c# ou Visual Basic, adicione itens, como campos, propriedades e outros métodos, para controlar o que está acontecendo no código.  
  
 Clique duas vezes em um método para ver sua definição de código, ou use o menu de atalho para o método. (Teclado: selecione o método no mapa e pressione **F12**)  
  
 ![Ir para definição de código para um método no mapa de códigos](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")  
  
 Adicione os itens que você deseja rastrear no mapa.  
  
 ![Mostrar campos em um método no mapa de códigos de pilha de chamada](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")  
  
> [!NOTE]
>  Por padrão, a adição de itens no mapa também adiciona os nós do grupo pai, como a classe, o namespace e o assembly. Embora seja útil, você pode manter o mapa simples desativando esse recurso usando o **pais incluem** botão na barra de ferramentas do mapa ou pressionando **CTRL** para adicionar itens.  
  
 ![Campos relacionados a um método no mapa de códigos de pilha de chamada](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")  
  
 Aqui, você pode visualizar facilmente quais métodos usam os mesmos campos. Os itens mais recentemente adicionados aparecem em verde.  
  
 Continue criando o mapa para ver mais código.  
  
 ![Consulte os métodos que usam um campo: mapa de códigos de pilha de chamada](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")  
  
 ![Os métodos que usam um campo no mapa de códigos de pilha de chamada](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")  
  
##  <a name="FindBugs"></a> Localizar erros usando o mapa  
 Visualizar seu código pode ajudar a localizar bugs com mais rapidez. Por exemplo, suponha que você está investigando um bug em um programa de desenho. Quando você desenha uma linha e tenta desfazê-la, nada acontece até que você desenhe outra linha.  
  
 Para definir pontos de interrupção `clear`, `undo`, e `Repaint` métodos, iniciar a depuração e criar um mapa de como esta:  
  
 ![Adicionar outra pilha de chamadas para o mapa de códigos](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")  
  
 Você observará que todos os gestos do usuário no mapa chamam `Repaint`, exceto para `undo`. Isso pode explicar por que `undo` não funciona imediatamente.  
  
 Após corrigir o bug e continuar executando o programa, o mapa adicionará a nova chamada de `undo` para `Repaint`:  
  
 ![Adicionar nova pilha de chamada de método no mapa de códigos](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")  
  
##  <a name="QA"></a> Perguntas e respostas  
  
-   **Nem todas as chamadas aparecem no mapa. Por quê?**  
  
     Por padrão, somente seu próprio código aparece no mapa. Para ver o código externo, ligue- **pilha de chamadas** janela:  
  
     ![Exibir o código externo usando a janela pilha de chamadas](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")  
  
     ou desativar **habilitar apenas meu código** no Visual Studio, opções de depuração:  
  
     ![Mostrar código externo usando a caixa de diálogo Opções](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")  
  
-   **Alterar o mapa afeta o código?**  
  
     Alterar o mapa não afeta o código de forma alguma. Sinta-se à vontade para renomear, mover ou remover qualquer item no mapa.  
  
-   **O que significa esta mensagem: "o diagrama pode ser baseado em uma versão mais antiga do código"?**  
  
     O código pode ter sido alterado depois que você alterou o mapa pela última vez. Por exemplo, uma chamada no mapa pode não existir mais no código. Feche a mensagem e tente recriar a solução antes de atualizar o mapa outra vez.  
  
-   **Como controlar o layout do mapa?**  
  
     Abra o **Layout** menu na barra de ferramentas do mapa:  
  
    -   Altere o layout padrão.  
  
    -   Para interromper a reorganizar mapa automaticamente, desativar **Layout automaticamente ao depurar**.  
  
    -   Para reorganizar o mínimo possível de mapa quando você adicionar itens, desativar **Layout Incremental**.  
  
-   **É possível compartilhar o mapa com outras pessoas?**  
  
     É possível exportar o mapa, enviá-lo a outras pessoas se tiver o Microsoft Outlook ou salvá-lo em sua solução para que você possa verificá-lo no Controle de versão do Team Foundation.  
  
     ![Mapa de códigos de pilha de chamada de compartilhamento com outros](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap_ShareWithOthers")  
  
-   **Como posso impedir que o mapa da adição de pilhas de chamadas de novo automaticamente?**  
  
     Escolha ![botão &#45; pilha de chamadas Mostrar no mapa de códigos automaticamente](../debugger/media/debuggermap_automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") na barra de ferramentas do mapa. Para adicionar manualmente a pilha de chamadas atual no mapa, pressione **Ctrl** + **Shift** + **`**.  
  
     O mapa continuará realce pilhas de chamadas existente no mapa durante a depuração.  
  
-   **O que os ícones de item e setas significam?**  
  
     Para obter mais informações sobre um item, mova o ponteiro do mouse sobre ele e examine a dica de ferramenta do item. Você também pode examinar o **legenda** para saber o que significa que cada ícone.  
  
     ![O que significam os ícones no mapa de código da pilha de chamada? ] (../debugger/media/debuggermap_showlegend.png "DebuggerMap_ShowLegend")  
  
 Consulte:  
  
-   [Mapear a pilha de chamadas](#MapStack)
  
-   [Verifique as observações sobre o código](#MakeNotes)
  
-   [Atualizar o mapa com a seguinte pilha de chamadas](#UpdateMap)
  
-   [Adicione o código relacionado ao mapa](#AddRelatedCode)
  
-   [Localizar erros usando o mapa](#FindBugs)  
  
## <a name="see-also"></a>Consulte também  
 [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)   
 [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Encontrar possíveis problemas usando analisadores de mapa de código](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Procurar e reorganizar mapas de códigos](../modeling/browse-and-rearrange-code-maps.md)