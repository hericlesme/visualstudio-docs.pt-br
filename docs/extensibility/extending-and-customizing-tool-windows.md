---
title: Estender e personalizar as janelas de ferramentas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 74616bf92b1424b4749354d1f0a7b3232e66a335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-and-customizing-tool-windows"></a>Estender e personalizar as janelas de ferramentas
Visual Studio fornece vários tipos diferentes de windows, por exemplo, janelas de ferramentas, janelas de documento e caixa de diálogo. Outras janelas, como a janela Propriedades, a janela de saída e a janela lista de tarefas, são tipos de janelas de ferramentas.  
  
## <a name="tool-windows"></a>Janelas de ferramentas  
 Janelas de ferramentas do Visual Studio são geralmente somente leitura windows que não são baseados em arquivo. Nelas diferem de janelas de documentos, quais arquivos são exibidos no modo de leitura / gravação. O **caixa de ferramentas**, **Solution Explorer**, **propriedades** janela, e **navegador da Web** são exemplos de janelas de ferramenta.  
  
 Para saber como criar uma janela de ferramenta simples, consulte [adicionando uma janela de ferramenta](../extensibility/adding-a-tool-window.md).  
  
 Para registrar uma janela de ferramenta com o Visual Studio, consulte [registrando uma janela de ferramenta](../extensibility/registering-a-tool-window.md).  
  
 Janelas de ferramentas são a única instância por padrão, que significa que apenas uma instância da janela de ferramentas pode ser aberto por vez. Depois que uma janela de ferramenta de instância única é aberta, ela permanecerá aberta até que o IDE seja fechado. Quando você fechar uma janela de ferramenta de instância única, somente sua visibilidade é alterado. Você também pode criar várias instâncias janelas de ferramentas, de modo que várias instâncias da janela podem ser abertas simultaneamente. Consulte [criação de uma janela de ferramenta com várias instâncias](../extensibility/creating-a-multi-instance-tool-window.md) para obter mais informações.  
  
 Janelas de ferramentas podem ser *dinâmico*, que significa que elas são visíveis, sempre que seu contexto de interface do usuário relacionado se aplica. O uso de visibilidade automática pode reduzir a desordem do windows no IDE. Para obter mais informações, consulte [abrindo uma janela de ferramenta dinâmico](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Janelas de ferramentas podem ser encaixada, flutuante ou com guias na estrutura do documento. O quadro de janela de ferramenta é fornecido pelo IDE e é usado para controlar o tamanho, local, estado de ancoragem e outras propriedades persistentes. O painel de janela de ferramenta exibe o conteúdo. O tamanho padrão e o local se aplicam somente quando a janela da ferramenta é aberto pela primeira vez; Depois que o estado da janela de ferramenta é persistente.  
  
 Painéis de janela de ferramenta podem hospedar controles de usuário do WPF e barras de ferramentas de suporte. Você pode substituir o <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> propriedade para retornar o identificador do controle hospedado.  
  
 Você pode adicionar diversos recursos diferentes para janelas de ferramentas. Por exemplo, você pode adicionar uma barra de ferramentas: [adicionando uma barra de ferramentas para uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md) ou um menu de atalho: [adicionando um Menu de atalho em uma janela de ferramenta](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Você pode adicionar um controle de pesquisa que permite pesquisar itens dentro de sua janela de ferramenta: [adicionando a pesquisa uma janela de ferramenta](../extensibility/adding-search-to-a-tool-window.md).  
  
 Você pode assinar eventos da janela de ferramenta: [assinar um evento](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Estendendo as janelas de ferramentas existente  
 Você pode adicionar informações sobre a janela de ferramenta para uma nova **opções** página e uma nova configuração no **propriedades** página, gravar o **lista de tarefas** e **saída**  windows. Para obter mais informações, consulte [estendendo propriedades, lista de tarefas, saída e opções Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) e [estendendo propriedades, lista de tarefas, saída e opções Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Caixas de diálogo modais  
 Em uma extensão do Visual Studio, você deve criar caixas de diálogo modais derivando de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, que permite que você controle-los e o restante da interface do usuário. Para obter mais informações, consulte. [Criar e gerenciar caixas de diálogo modais](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criar uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md)