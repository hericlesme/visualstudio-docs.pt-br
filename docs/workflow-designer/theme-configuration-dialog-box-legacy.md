---
title: "Caixa de diálogo de configuração tema (legados) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ThemeConfigurationDialog.UI
helpviewer_keywords:
- themes, configuring
- Theme Configuration dialog box
ms.assetid: 9e6d182a-c4d9-4e71-b2b9-02f675fc2b29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4d59ffe46ed9b85eb64eeda39275b6566b1ca497
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="theme-configuration-dialog-box-legacy"></a>Caixa de diálogo de configuração tema (legados)
Este tópico descreve como usar o **configuração de tema** caixa de diálogo no Designer de fluxo de trabalho herdado do Windows. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Um tema define o plano de fundo e de primeiro plano as cores, estilos, ícones, e outros elementos visuais de um fluxo de trabalho. Você pode salvar temas para reutilização por outros fluxos de trabalho.

 Criar e editar temas usando o **configuração de tema** caixa de diálogo. Para abrir a caixa de diálogo, selecione **criar novo tema** no **fluxo de trabalho** menu ou com o botão direito do fluxo de trabalho superfície de design e selecione **criar novo tema**.

 A tabela a seguir descreve os elementos de interface de usuário do **configuração de tema** caixa de diálogo.

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Nome do tema:**|O nome que identifica o tema no [caixa de diálogo Opções de temas, Designer de fluxo de trabalho (legados)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md). Um nome de variável é gerado para novos temas.|
|**Local do tema:**|Nome de arquivo e caminho do arquivo de tema. Um nome de arquivo variável é gerado para novos temas gerado com base no nome do tema. Se você alterar o nome gerado de tema, convém alterar o nome de arquivo para corresponder ao nome do tema.|
|**...**|Clique para selecionar o local para salvar o arquivo de tema de fluxo de trabalho, que usa uma extensão de nome de arquivo .wtm. O caminho selecionado será visto no **local do tema** caixa de texto.|
|**Selecione o Designer e configurar as propriedades:**|O painel esquerdo lista um modo de exibição de árvore de atividades para que o tema pode ser personalizado. Selecione uma atividade no modo de exibição de árvore e propriedades de tema para atividades serão exibidas no painel de propriedades, que é à direita do painel modo de exibição de árvore. Clique em uma propriedade para alterar seu valor.|
|**Visualizar**|Clique para exibir uma janela para visualizar os efeitos de alterações de propriedade.|

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Temas, Designer de Fluxo de Trabalho, Opções (herdado)](../workflow-designer/themes-workflow-designer-options-dialog-box-legacy.md)
- [Designer herdado para a ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)