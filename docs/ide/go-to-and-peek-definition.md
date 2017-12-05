---
title: "Ir para Definição e Espiar Definição | Microsoft Docs"
ms.custom: 
ms.date: 10/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code editor, go to definition
- code editor, peek definition
- go to definition
- peek definition
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 467d119e67db254b6e15630c08c411bb15283351
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="go-to-definition-and-peek-definition"></a>Ir para Definição e Definição de Pico  
Os recursos Ir para Definição e Espiar Definição permitem exibir facilmente a definição de um tipo ou membro.

## <a name="go-to-definition"></a>Ir para definição  
O recurso Ir para Definição navega para a fonte de um tipo ou membro e abre o resultado em uma nova guia. Se você estiver usando um teclado, coloque o cursor de texto em algum lugar dentro do nome do símbolo e pressione **F12**. Se você estiver usando um mouse, selecione **Ir para Definição** no menu de contexto ou use a funcionalidade **Ctrl + clique** descrita abaixo.  

### <a name="ctrl-click-go-to-definition"></a>CTRL + clique para Ir para Definição  
No Visual Studio 2017 versão 15.4, há uma maneira mais fácil para os usuários de mouse acessarem Ir para Definição rapidamente. Os símbolos tornam-se clicáveis quando você pressiona **Ctrl** e passa o mouse sobre o tipo ou membro. Para navegar rapidamente para a definição de um símbolo, pressione a tecla **Ctrl** e, em seguida, clique nele. É fácil assim!

![Animação de Ir para Definição com o clique do mouse](../ide/media/click_gotodef.gif)

Você pode alterar a tecla modificadora do clique do mouse para **Ir para Definição** acessando **Ferramentas**, **Opções**, **Editor de Texto**, **Geral** e selecionando **Alt** ou **Ctrl + Alt** na lista suspensa **Usar tecla modificadora**. Você também pode desabilitar o clique do mouse para **Ir para Definição** desmarcando a caixa de seleção **Habilitar clique do mouse para Ir para Definição**.  

![Habilitando o clique do mouse para Ir para Definição](../ide/media/editor_options_mouse_click_gotodef.png)  

## <a name="peek-definition"></a>Inspecionar Definição
O recurso Espiar Definição permite visualizar a definição de um tipo sem sair do local atual no editor. Se você estiver usando um teclado, coloque o cursor de texto em algum lugar dentro do nome do tipo ou do membro e pressione **Alt + F12**. Se você estiver usando um mouse, selecione **Espiar Definição** no menu de contexto. No Visual Studio 2017 versão 15.4 e posteriores, há uma nova maneira de espiar a exibição de uma definição usando o mouse. Primeiro, acesse **Ferramentas**, **Opções**, **Editor de Texto**, **Geral**. Selecione a opção **Abrir definição na espiada de exibição** e clique em **OK** para fechar a caixa de diálogo **Opções**.  

![Configurando a opção de espiar definição com o clique do mouse](../ide/media/editor_options_peek_view.png)  

Em seguida, pressione **Ctrl** (ou qualquer outra tecla modificadora que estiver selecionada em **Opções**) e clique no tipo ou no membro.  

![Animação de espiar definição](../ide/media/peek_definition.gif)

Se você inspecionar outra definição da janela pop-up, iniciará um caminho de navegação estrutural no qual poderá navegar usando os círculos e setas que aparecem acima da janela pop-up.  

Para obter mais informações, consulte [How to: View and Edit Code by Using Peek Definition (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) (Como exibir e editar códigos usando Inspecionar Definição (Alt + F12)).  

## <a name="see-also"></a>Consulte também  
[Navegando no código](../ide/navigating-code.md)  
[Como exibir e editar o código usando Inspecionar Definição (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  
