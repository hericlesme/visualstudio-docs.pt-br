---
title: Dicas de acessibilidade e truques do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: a4ac0c709f2b7f9dfded7c6781dda9831e457fa5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Dicas de acessibilidade e truques do Visual Studio
> [!TIP]
> Para saber mais sobre atualizações de acessibilidade recentes, confira a postagem no blog [Accessibility improvements in Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Aprimoramentos de acessibilidade no Visual Studio 2017 versão 15.3).

O Visual Studio tem recursos internos de acessibilidade que são compatíveis com leitores de tela e outras tecnologias assistenciais. Este tópico lista combinações de teclas de atalho comum que você pode usar para executar tarefas apenas com o teclado e inclui informações de como usar temas de alto contraste para melhorar a visibilidade. Além disso, mostra como usar anotações para revelar informações úteis sobre o código e como configurar indicações de som para eventos de build e de ponto de interrupção.

## <a name="save-your-ide-settings"></a>Salvar as configurações do IDE  
 É possível personalizar sua experiência no IDE salvando seu layout de janela, esquema de mapeamento de teclado e outras preferências. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modificar o IDE para exibição de alto contraste
Para algumas pessoas, algumas cores são mais difíceis de enxergar. Se você deseja mais contraste ao codificar, mas não quer usar os temas típicos de "Alto Contraste", agora nós oferecemos um tema "Azul (Contraste extra)".

  ![Compare o tema Azul e o tema Azul de Contraste Extra](media/blue-extra-contrast-theme.png "Veja a diferença entre o tema Azul e o tema Azul de Contraste Extra")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Usar anotações para revelar informações úteis sobre o código

O editor do Visual Studio inclui vários "adornos" de texto que permitem saber as características e os recursos em determinados pontos em uma linha de código, como lâmpadas, "linhas sinuosas" de erros e avisos, indicadores e assim por diante. Você pode usar o conjunto de comandos "Mostrar Anotações de Linha" para ajudá-lo a descobrir esses adornos e, em seguida, navegar entre eles.

  ![Usar o conjunto de comandos Mostrar Anotações de Linha](media/show-line-annotations-command-set.png "Mostra como definir o conjunto de comandos Mostrar Anotações de Linha")

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>Acessar as barras de ferramentas usando combinações de teclas de atalho
O Visual Studio IDE tem barras de ferramentas, assim como tem muitas janelas de ferramentas. As combinações de teclas de atalho a seguir ajudarão você a acessá-las.

|Recurso|Descrição|Combinação de teclas|  
|-------------|-----------------|---------------------|  
|Barras de ferramentas do IDE|Selecione o primeiro botão na barra de ferramentas Standard.|**ALT**, **CTRL** + **TAB**|  
|Barras de ferramentas da janela de ferramentas|Mova o foco para a barra de ferramentas em uma janela de ferramentas. <br> <br> **OBSERVAÇÃO:** isso funciona para a maioria das janelas de ferramentas, mas somente quando o foco está em uma janela de ferramentas. Além disso, você deve escolher a tecla SHIFT antes da tecla ALT. Em algumas janelas de ferramentas, como a Team Explorer, você deve manter a tecla SHIFT pressionada por um momento antes de escolher a tecla ALT.|**SHIFT** + **ALT**|
|Barras de ferramentas|Acesse o primeiro item na barra de ferramentas Avançar (quando uma barra de ferramentas tem foco).|**CTRL** + **TAB**|

### <a name="other-useful-shortcut-key-combinations"></a>Outras combinações de teclas de atalho úteis  
Algumas outras combinações de teclas de atalho úteis incluem o seguinte.

|Recurso|Descrição|Combinação de teclas|  
|-------------|-----------------|---------------------|  
|IDE|Ativar e desativar o alto contraste. <br> <br> **OBSERVAÇÃO:** atalho padrão do Windows|**ALT esquerdo + SHIFT esquerdo + PRINT SCREEN**|  
|Caixa de diálogo|Marque ou desmarque a opção da caixa de seleção em uma caixa de diálogo. <br> <br> **OBSERVAÇÃO:** atalho padrão do Windows|**BARRA DE ESPAÇO**|  
|Menus de contexto|Abra um menu de contexto (clique com o botão direito do mouse). <br> <br> **OBSERVAÇÃO:** atalho padrão do Windows|**SHIFT** + **F10**|
|Menus|Acesse rapidamente um item de menu usando as teclas de aceleração. Escolha a tecla **ALT** seguida pelas letras sublinhadas em um menu de atalho para ativar o comando. Por exemplo, para exibir a caixa de diálogo Abrir Projeto no Visual Studio, você escolheria **ALT** + **F** + **O** + **P**.  <br><br> **OBSERVAÇÃO:** atalho padrão do Windows|**ALT** + **[carta]**|
|Janela caixa de ferramentas|Mover-se entre guias da Caixa de ferramentas.|**CTRL** + **SETA PARA CIMA**<br /><br /> e<br /><br /> **CTRL** + **SETA PARA BAIXO**|  
|Janela caixa de ferramentas|Adicionar um controle da Caixa de ferramentas a um formulário ou designer.|**ENTER**|  
|Caixa de diálogo Teclado, Ambiente, Opções|Excluir uma combinação de teclas inserida na opção **Pressionar teclas de atalho**.|**BACKSPACE**|  

> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.  


## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Use o miniaplicativo de som para definir indicações de build e de ponto de interrupção
Você pode usar o miniaplicativo de som no Windows para atribuir um som a eventos do programa Visual Studio. Especificamente, você pode atribuir sons aos seguintes eventos do programa:

 * Ocorrências de ponto de interrupção
 * Build cancelado
 * Build com falha
 * Build bem-sucedido

Veja como.

1. Na caixa **Pesquisar** em um computador executando o Windows 10, digite **Alterar sons do sistema**.

  ![Caixa de pesquisa no Windows 10](media/type-here-to-search.png "Digite sons na caixa Pesquisar em um computador executando o Windows 10")

  (Como alternativa, se você tiver habilitado a Cortana, diga "Ei Cortana" e, em seguida, diga "Alterar sons do sistema".)

2. Clique duas vezes em **Alterar sons do sistema**.

  ![Resultados da pesquisa no Windows 10](media/change-system-sounds.png "Clique duas vezes em Alterar sons do sistema nos Resultados da pesquisa")

3. Na caixa de diálogo **Som**, clique na guia **Sons**. <br><br>
 Em seguida, em **Eventos do Programa**, role até **Microsoft Visual Studio** e selecione os sons que você deseja aplicar aos eventos escolhidos.

  ![Guia sons do miniaplicativo de som no Windows 10](media/sound-applet.png "Clique duas vezes em Alterar sons do sistema nos Resultados da pesquisa")

4. Clique em **OK**.



## <a name="see-also"></a>Consulte também  
* [Recursos de Acessibilidade do Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
  * [Como personalizar menus e barras de ferramentas no Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Acessibilidade da Microsoft](https://www.microsoft.com/Accessibility)
