---
title: Acessibilidade em projetos do Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 786926ff7608a487ea9fcd732e1457bb382a4bab
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="accessibility-in-office-projects"></a>Acessibilidade em projetos do Office
  Microsoft Visual Studio e o Microsoft Office incluem muitos recursos de acessibilidade que permitem criar soluções personalizadas que atendem aos requisitos de acessibilidade padrão. A Microsoft publica as diretrizes de acessibilidade na Web. Para obter detalhes, consulte o [site de acessibilidade da](http://go.microsoft.com/fwlink/?LinkID=37113).  

 Na maioria dos casos, projetos do Office no Visual Studio atende aos padrões ou expõe as propriedades de acessibilidade que você pode definir para disponibilizar suas soluções. No entanto, há alguns recursos que têm Acessibilidade limitada.  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>Acessibilidade no tempo de Design  

### <a name="using-shortcut-keys-in-document-level-projects"></a>Usando as teclas de atalho em projetos no nível de documento  
 Quando um documento do Microsoft Office Word ou uma pasta de trabalho do Microsoft Office Excel é aberta no Visual Studio, apenas um aplicativo em um momento recebe os comandos de teclas de atalho. Por padrão, o Visual Studio receberá todos os comandos de tecla de atalho, mas você pode fazer o Word ou Excel recebê-las quando o documento tem foco selecionando **esquema de teclado dinâmico** no **configurações de teclado** página do **opções** caixa de diálogo. Para obter mais informações, consulte [caixa de diálogo de opções de teclado do Word do Microsoft Office, configurações de teclado do Microsoft Office,](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) e [caixa de diálogo de opções de teclado do Microsoft Office Excel, configurações de teclado do Microsoft Office,](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  

### <a name="displaying-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Exibindo teclas de atalho para a faixa de opções em nível de documento  
 Quando um documento do Word ou uma pasta de trabalho do Excel é aberta no Visual Studio, você não pode pressionar a tecla Alt para exibir as teclas de atalho para as guias e controles da faixa de opções. Para exibir as teclas de atalho, enquanto o documento ou a pasta de trabalho estiver aberta no designer, execute as etapas a seguir.  

##### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Para exibir as teclas de atalho para guias de faixa de opções e os controles no designer  

1.  No Visual Studio, no **ferramentas** menu, clique em **opções**.  

2.  Expanda o **ferramentas Office** nó e selecione **teclado do Microsoft Office Excel** ou **teclado do Microsoft Office Word**, conforme apropriado.  

3.  Selecione **esquema de teclado dinâmico**.  

     Será exibida uma mensagem informando que você deve reiniciar o Visual Studio para que a alteração tenha efeito.  

4.  Clique em **OK**.  

5.  Reinicie o Visual Studio e, em seguida, reabra o projeto.  

6.  Abra o designer de documento ou pasta de trabalho para o seu projeto.  

7.  Pressione F6 para exibir as teclas de atalho para a faixa de opções.  

## <a name="accessibility-at-run-time"></a>Acessibilidade no tempo de execução  

### <a name="windows-forms-controls-on-office-documents"></a>Controles em documentos do Office do Windows Forms  
 Controles de Windows Forms expõem as propriedades de acessibilidade para fornecer informações sobre o controle de recursos de acessibilidade, como leitores de tela. Quando os controles estão em um documento do Office em uma personalização no nível do documento, você pode tirar proveito dessas propriedades de acessibilidade. Para obter mais informações, consulte [fornecendo informações de acessibilidade para controles em um Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  

 No entanto, há algumas limitações de acessibilidade em tempo de execução quando os controles de formulários do Windows são hospedados em uma pasta de trabalho do Excel ou um documento do Word:  

-   Você não pode guia de um controle para outro.  

-   Controles em um documento são desabilitados quando você alterar a configuração de zoom do documento para algo diferente de 100%.  

 Para obter informações sobre as limitações de controles de Windows Forms em documentos, consulte [limitações de controles dos Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  

### <a name="actions-panes-and-custom-task-panes"></a>Painéis de ações e painéis de tarefas personalizados  
 Quando um painel de ações ou o painel de tarefas personalizado tem foco, você acessa os controles da mesma forma que você acessaria controles em um aplicativo do Windows Forms. Para mover o cursor entre o painel de ações e o documento, você pode pressionar **F6**.  

 Para obter mais informações sobre painéis de ações e painéis de tarefas personalizados, consulte [visão geral do painel de ações](../vsto/actions-pane-overview.md) e [painéis de tarefas personalizados](../vsto/custom-task-panes.md).  

### <a name="display-modes"></a>Modos de exibição  
 O Visual Studio tem as seguintes limitações relacionadas a modos de exibição:  

-   Controles em um documento do Word ou planilha do Excel são desabilitados quando você alterar a configuração de zoom do documento para algo diferente de 100%.  

-   O **novo projeto** caixa de diálogo Exibir controles corretamente se um usuário altera as opções de acessibilidade do computador para **usar alto contraste**.  

 Você pode usar a Lente de aumento para superar essas limitações. Lente de aumento é um utilitário de exibição no Windows que cria uma janela separada que exibe uma parte ampliada da tela.  

## <a name="see-also"></a>Consulte também  
 [Desenvolvendo soluções do Office](../vsto/developing-office-solutions.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Acessibilidade para pessoas com deficiências](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Recursos de Acessibilidade do Visual Studio](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
