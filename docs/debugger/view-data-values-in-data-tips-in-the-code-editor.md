---
title: "Exibir valores de dados em DataTips no editor de código | Microsoft Docs"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 178bd1768474eaaaf760e2ef4feecfe0e1519bee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Exibir os valores de dados em DataTips no editor de códigos
Os DataTips fornecem um modo conveniente de exibir informações sobre variáveis em seu programa durante a depuração. Os DataTips funcionam apenas no modo de interrupção e apenas com variáveis que estejam no escopo de execução atual.
  
### <a name="to-display-a-datatip"></a>Para exibir um DataTip  
  
1. Definir um ponto de interrupção e iniciar a depuração (pressione **F5**).

2. Onde está em pausa no depurador, coloque o ponteiro do mouse sobre qualquer variável no escopo atual.
  
     Um DataTip aparece.
  
3.  O DataTip desaparecerá quando você remover o ponteiro do mouse. Para fixar o DataTip para que ela permaneça aberta, clique o **Pin a fonte de** ícone ou o botão direito do mouse em uma variável, em seguida, clique em **Pin a fonte**.

    ![Fixar uma dica de dados](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > Os DataTips são sempre avaliados no contexto onde a execução é suspensa e não por onde o cursor está passando. Se você passar o mouse sobre uma variável em outra função com o mesmo nome de uma variável que está no contexto atual, o valor da variável na outra função será exibido como o valor da variável no contexto atual.
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Para desafixar um DataTip e fazê-lo flutuar  
  
-   Em um DataTip fixo, clique no **Desafixar do código-fonte** ícone.  
  
     O ícone de fixar é alterado para a posição desafixada. O DataTip agora flutua sobre todas as janelas abertas. O DataTip flutuante é fechado quando a sessão de depuração termina.  
  
### <a name="to-repin-a-floating-datatip"></a>Ao refixar um DataTip flutuante  
  
-   Em um DataTip, clique no ícone de fixar.  
  
     O ícone de fixar é alterado para a posição fixada. Se o DataTip estiver fora de uma janela de origem, o ícone de fixar estará desabilitado e o DataTip não poderá ser fixado.  
  
### <a name="to-close-a-datatip"></a>Para fechar um DataTip  
  
-   Posicione o ponteiro do mouse sobre um DataTip e, em seguida, clique no **fechar** ícone.  
  
### <a name="to-close-all-datatips"></a>Para fechar todos os DataTips  
  
-   Sobre o **depurar** menu, clique em **limpar todos os DataTips**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Para fechar todos os DataTips para um arquivo específico  
  
-   Sobre o **depurar** menu, clique em **limpar todos os DataTips fixos em** *arquivo*.  
  
## <a name="expand-and-edit-information"></a>Expandir e editar as informações  
 Você pode usar os DataTips para expandir uma matriz, uma estrutura ou um objeto para exibir seus membros. Você também pode editar o valor de uma variável de um DataTip.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Para expandir uma variável para ver seus elementos  
  
-   Em um DataTip, coloque o ponteiro do mouse o  **+**  entrada que antecede o nome da variável.  
  
    A variável expande para mostrar seus elementos na forma da árvore.

    ![Exibir uma dica de dados](../debugger/media/dbg-tour-data-tips.gif "exibir uma dica de dados")
  
    Quando a variável é expandida, você poderá usar as teclas de direção no teclado para mover para cima e para baixo. Outra opção é usar o mouse.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Para editar o valor de uma variável usando um DataTip  
  
1.  Em um DataTip, clique no valor. Isso está desabilitado para valores somente leitura.  
  
2.  Digite um novo valor e pressione ENTER.  
  
## <a name="making-a-datatip-transparent"></a>Criando um DataTip transparente  
 Se quiser ver o código que está por trás de um DataTip, poderá criar o DataTip temporariamente transparente. Isso não se aplica a DataTips fixados ou flutuantes.  
  
#### <a name="to-make-a-datatip-transparent"></a>Para criar um DataTip transparente  
  
-   Em um DataTip, pressione CTRL.  
  
     O DataTip permanecerá transparente enquanto você mantiver pressionada a tecla CTRL.  
  
## <a name="visualize-complex-data-types"></a>Visualize os tipos de dados complexos  
 Se um ícone de Lupa aparece ao lado de um nome de variável em um DataTip, um ou mais [visualizadores](../debugger/create-custom-visualizers-of-data.md), como o [visualizadores de cadeia de caracteres](../debugger/string-visualizer-dialog-box.md), estão disponíveis para as variáveis desse tipo de dados. Você pode usar um visualizador para exibir informações de uma maneira mais significativa, geralmente gráfica.
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Para exibir o conteúdo de uma variável usando um visualizador  
  
-   Clique no ícone de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ícone visualizador") para selecionar o visualizador padrão para o tipo de dados.  
  
     -ou-  
  
     Clique na seta do menu suspenso ao lado do visualizador para selecionar de uma lista de visualizadores apropriados para o tipo de dados.  
  
     Um visualizador exibe as informações.  
  
## <a name="add-information-to-a-watch-window"></a>Adicionar informações a uma janela Inspecionar  
 Se você quiser continuar assistir a uma variável em uma exibição de lista, você pode adicionar a variável para o **inspecionar** janela a partir de um DataTip.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Para adicionar uma variável à janela Inspeção  
  
-   Clique um DataTip e, em seguida, clique em **Adicionar inspeção**.  
  
     A variável é adicionada para o **inspecionar** janela. Se você estiver usando uma edição que dá suporte a vários **inspecionar** windows, a variável é adicionada ao **inspecionar 1.**  
  
## <a name="import-and-export-datatips"></a>Importar e exportar DataTips  
 Você pode exportar DataTips para um arquivo XML, que pode ser compartilhado com um colega ou editado por um editor de texto.  
  
#### <a name="to-export-datatips"></a>Para exportar DataTips  
  
1.  No menu Depurar, clique em **exportar DataTips**.  
  
     O **exportar DataTips** caixa de diálogo é exibida.  
  
2.  Use técnicas padrão de arquivos para navegar até o local onde deseja salvar o arquivo XML, digite um nome para o arquivo de **nome de arquivo** caixa e, em seguida, clique em **Okey**.  
  
#### <a name="to-import-datatips"></a>Para importar DataTips  
  
1.  No menu Depurar, clique em **importar DataTips**.  
  
     O **importar DataTips** caixa de diálogo é exibida.  
  
2.  Use a caixa de diálogo para localizar o arquivo XML que você deseja abrir e clique em **Okey**.  
  
## <a name="see-also"></a>Consulte também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Inspecionar e Windows QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   