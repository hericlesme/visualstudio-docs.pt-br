---
title: Criar um mapa visual da pilha de chamadas | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6156be294c9b64c26a7488aef3f0c92d1f4ccffd
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36296056"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-in-visual-studio-enterprise"></a>Criar um mapa visual da pilha de chamadas durante a depuração no Visual Studio Enterprise
Crie um mapa de código para rastrear visualmente a pilha de chamadas durante a depuração. Você pode fazer anotações no mapa para acompanhar o que o código está fazendo, de modo a se concentrar na localização de bugs.

 Itens necessários:

-   [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

-   Código que você pode depurar, como Visual c#, Visual Basic, C++, JavaScript ou X + +

Aqui está uma rápida olhada um mapa de código:

 ![Depuração com pilhas de chamadas em mapas de códigos](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

 Consulte:

-   [Vídeo: Depurar visualmente com a integração do depurador mapa de códigos (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

-   [Mapear a pilha de chamadas](#MapStack)

-   [Fazer anotações sobre o código](#MakeNotes)

-   [Atualizar o mapa com a próxima pilha de chamadas](#UpdateMap)

-   [Adicionar código relacionado ao mapa](#AddRelatedCode)

-   [Localizar bugs usando o mapa](#FindBugs)

-   [P E R](#QA)

 Para obter detalhes sobre os comandos e ações que você pode usar ao trabalhar com mapas de código, consulte [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md).

##  <a name="MapStack"></a> Mapear a pilha de chamadas

1.  Inicie a depuração. (Teclado: **F5**)

2.  Depois que seu aplicativo entra em modo de interrupção ou entrar em uma função, escolha **mapa de código**. (Teclado: **Ctrl** + **Shift** + **`**)

     ![Escolha o mapa de código para iniciar a pilha de chamadas de mapeamento](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap_ChooseCodeMap")

     A pilha de chamadas atual aparece em laranja em um novo mapeamento de código:

     ![Ver a pilha de chamadas no mapa de códigos](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     O mapa será atualizado automaticamente enquanto você continua a depuração. Ver [atualizar o mapa com a próxima pilha de chamadas](#UpdateMap).

##  <a name="MakeNotes"></a> Fazer anotações sobre o código
 Adicione comentários para acompanhar o que está acontecendo no código. Para adicionar uma nova linha em um comentário, pressione **Shift + Return**.

 ![Adicionar comentário para a pilha de chamadas no mapa de códigos](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

##  <a name="UpdateMap"></a> Atualizar o mapa com a próxima pilha de chamadas
 Execute o aplicativo até o próximo ponto de interrupção ou siga uma função. O mapa adiciona uma nova pilha de chamadas.

 ![Mapa de código de atualização com a próxima pilha de chamadas](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

##  <a name="AddRelatedCode"></a> Adicionar código relacionado ao mapa
 Agora você tem um mapa - o que em seguida? Se você estiver trabalhando com o Visual c# ou Visual Basic, adicione itens, como campos, propriedades e outros métodos, para acompanhar o que está acontecendo no código.

 Clique duas vezes em um método para ver sua definição de código ou use o menu de atalho para o método. (Teclado: selecione o método no mapa e pressione **F12**)

 ![Ir para definição de código para um método no mapa de códigos](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Adicione os itens que você deseja rastrear no mapa.

 ![Mostrar campos em um método no mapa de códigos de pilha de chamadas](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
>  Por padrão, a adição de itens no mapa também adiciona os nós do grupo pai, como a classe, namespace e assembly. Embora isso seja útil, você pode manter o mapa simples desativando esse recurso usando o **incluem pais** botão na barra de ferramentas do mapa ou pressionando **CTRL** quando você adiciona itens.

 ![Campos relacionados a um método no mapa de códigos de pilha de chamadas](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

 Aqui, você pode visualizar facilmente quais métodos usam os mesmos campos. Os itens mais recentemente adicionados aparecem em verde.

 Continue criando o mapa para ver mais código.

 ![Consulte os métodos que usam um campo: mapa de códigos de pilha de chamadas](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Métodos que usam um campo no mapa de códigos de pilha de chamadas](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

##  <a name="FindBugs"></a> Localizar bugs usando o mapa
 Visualizar seu código pode ajudar a localizar bugs com mais rapidez. Por exemplo, suponha que você estiver investigando um bug em um programa de desenho. Quando você desenha uma linha e tenta desfazê-la, nada acontece até que você desenhe outra linha.

 Para que você define pontos de interrupção a `clear`, `undo`, e `Repaint` métodos, inicie a depuração e cria um mapa como este:

 ![Adicionar outra pilha de chamadas ao mapa de códigos](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Você observará que todos os gestos do usuário no mapa chamam `Repaint`, exceto para `undo`. Isso pode explicar o motivo `undo` não funcionar imediatamente.

 Após corrigir o bug e continuar executando o programa, o mapa adicionará a nova chamada de `undo` para `Repaint`:

 ![Adicionar nova pilha de chamada de método no mapa de códigos](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

##  <a name="QA"></a> Perguntas e respostas

-   **Nem todas as chamadas aparecem no mapa. Por quê?**

     Por padrão, somente seu próprio código aparece no mapa. Para ver o código externo, ativá-lo na **pilha de chamadas** janela:

     ![Exibir código externo usando a janela pilha de chamadas](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")

     ou desative **habilitar apenas meu código** em Opções de depuração do Visual Studio:

     ![Mostrar código externo usando a caixa de diálogo Opções](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

-   **Alterar o mapa afeta o código?**

     Alterar o mapeamento não afeta o código de forma alguma. Sinta-se à vontade para renomear, mover ou remover qualquer item no mapa.

-   **O que significa esta mensagem: "o diagrama pode ser baseado em uma versão mais antiga do código"?**

     O código pode ter sido alterado depois que você alterou o mapa pela última vez. Por exemplo, uma chamada no mapa pode não existir mais no código. Feche a mensagem e tente recriar a solução antes de atualizar o mapa outra vez.

-   **Como controlar o layout do mapa?**

     Abra o **Layout** menu na barra de ferramentas do mapa:

    -   Altere o layout padrão.

    -   Para parar de reorganizar o mapa automaticamente, desative **Layout automaticamente ao depurar**.

    -   Para reorganizar o mapa o mínimo possível quando você adicionar itens, desative **Layout Incremental**.

-   **Pode compartilhar o mapa com outras pessoas?**

     É possível exportar o mapa, enviá-lo a outras pessoas se tiver o Microsoft Outlook ou salvá-lo em sua solução para que você possa verificá-lo no Controle de versão do Team Foundation.

     ![Mapa de códigos de pilha de chamada de compartilhamento com outras pessoas](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap_ShareWithOthers")

-   **Como posso impedir que o mapa de adicionar novas pilhas de chamadas automaticamente?**

     Escolher ![botão &#45; pilha de chamadas de mostrar no mapa de códigos automaticamente](../debugger/media/debuggermap_automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") na barra de ferramentas do mapa. Para adicionar manualmente a pilha de chamadas atual ao mapa, pressione **Ctrl** + **Shift** + **`**.

     O mapa continuará realçando as pilhas de chamadas existentes no mapa enquanto você estiver depurando.

-   **O que os ícones de item e setas significam?**

     Para obter mais informações sobre um item, move o ponteiro do mouse sobre ele e examine a dica de ferramenta do item. Você também pode examinar a **legenda** para saber o que significa cada ícone.

     ![O que significam os ícones no mapa de código da pilha de chamada? ] (../debugger/media/debuggermap_showlegend.png "DebuggerMap_ShowLegend")

 Consulte:

-   [Mapear a pilha de chamadas](#MapStack)

-   [Fazer anotações sobre o código](#MakeNotes)

-   [Atualizar o mapa com a próxima pilha de chamadas](#UpdateMap)

-   [Adicionar código relacionado ao mapa](#AddRelatedCode)

-   [Localizar bugs usando o mapa](#FindBugs)

## <a name="see-also"></a>Consulte também
 [Mapear dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md) [mapas de código de uso para depurar seus aplicativos](../modeling/use-code-maps-to-debug-your-applications.md) [localizar possíveis problemas usando o código mapeiam analisadores](../modeling/find-potential-problems-using-code-map-analyzers.md) [procurar e reorganizar mapas de código](../modeling/browse-and-rearrange-code-maps.md)