---
title: 'Como: depurar um controle ActiveX | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 932ccf7bdbea8fa68d0c2883d0ae8fd77eedf5bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-an-activex-control"></a>Como depurar um controle ActiveX
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Para depurar seu controle ActiveX, você deverá especificar um contêiner (executável) em que o controle será executado.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Para especificar um contêiner para a sessão de depuração  
  
1.  No Gerenciador de Soluções, selecione o projeto.  
  
2.  Do **exibição** menu, escolha **páginas de propriedade**.  
  
3.  No **páginas de propriedades do projeto** caixa de diálogo, abra o **propriedades de configuração** pasta e selecione **depuração**.  
  
4.  Sob o **depuração** categoria, localize o **comando** propriedade.  
  
5.  Especifique o nome do caminho para o contêiner. Por exemplo, C:\Arquivos de Programas\Internet Explorer\IEXPLORE.EXE.  
  
6.  Se você especificar o Internet Explorer como o contêiner e você estiver usando a área de trabalho ativa, digite `/new` no **argumentos de comando** caixa.  
  
7.  Clique em **OK**.  
  
     Se você não especificar um contêiner no **páginas de propriedades do projeto** caixa de diálogo, você pode especificar o contêiner ao iniciar a depuração. Quando você seleciona um comando de execução para iniciar a depuração, o [executável para a caixa de diálogo de sessão de depuração](../debugger/executable-for-debugging-session-dialog-box.md) é exibida. Especifique o nome do caminho do contêiner na caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Controles ActiveX](/cpp/mfc/activex-controls)   
 [Testando propriedades e eventos com contêiner de teste](/cpp/mfc/testing-properties-and-events-with-test-container)   
 [COM e ActiveX depuração](../debugger/com-and-activex-debugging.md)   
 [Depurando no Visual Studio](../debugger/index.md)  
 [Tour dos recursos do depurador](../debugger/debugger-feature-tour.md)