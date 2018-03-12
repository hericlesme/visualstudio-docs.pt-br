---
title: "Vincular a uma atividade&#39;caixa de diálogo de propriedade s (herdado) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6ee80d096cc0df6092811fa7fba17125c5af380f
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Vincular a uma atividade&#39;caixa de diálogo de propriedade s (herdado)
Este tópico descreve como usar o **associar a propriedade de uma atividade** caixa de diálogo no Designer de fluxo de trabalho herdado do Windows. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Um tipo de instância de propriedade de dependência pode ser associado a propriedade pública ou ao evento de outra atividade. Para obter mais informações sobre associação de atividade, consulte [usando propriedades de dependência](http://go.microsoft.com/fwlink?LinkID=65007).

 Selecione uma propriedade para associar ao usar o **associar a propriedade de uma atividade** caixa de diálogo. Abra essa caixa de diálogo clicando no botão de reticências **[...]**  no final da caixa de texto da propriedade selecionada no **propriedades** janela, ou clicando no ícone de exclamação azul que aparece ao lado do nome da propriedade no navegador de propriedade.

 A tabela a seguir descreve os elementos de interface de usuário do **associar a propriedade de uma atividade** caixa de diálogo.

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Vincular a um membro existente**|Selecione um membro que você deseja associar no painel modo de exibição de árvore. O painel abaixo de exibição de árvore exibe uma mensagem que indica se o membro é um tipo válido para associar a ou não. Clique em **Okey** para associar ao membro válido selecionado.|
|**Vincular a um novo membro**|Crie um novo campo ou propriedade de membro para associação. Insira um **nome do novo membro**. Escolha se deseja criar uma propriedade de dependência ou um campo público selecionando **criar campo** ou **criar propriedade**. Clique em **Okey** para criar o novo membro.|

## <a name="see-also"></a>Consulte também

- [Usando propriedades de atividade](http://go.microsoft.com/fwlink?LinkID=65013)
- [Usando propriedades de dependência](http://go.microsoft.com/fwlink?LinkID=65007)
- [Designer herdado para a ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)