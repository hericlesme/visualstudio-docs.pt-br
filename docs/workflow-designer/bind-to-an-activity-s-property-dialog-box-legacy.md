---
title: Designer de fluxo de trabalho - associar a uma atividade&#39;caixa de diálogo de propriedade s (herdado)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8922864a32c08d8feaed11e530314176557a785f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="bind-to-an-activitys-property-dialog-box-legacy"></a>Associar à caixa de diálogo de propriedade de uma atividade (legados)

Este tópico descreve como usar o **associar a propriedade de uma atividade** caixa de diálogo no Designer de fluxo de trabalho herdado do Windows. Use o Designer de fluxo de trabalho herdado quando você precisa direcionar o .NET Framework versão 3.5 ou o WinFX.

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