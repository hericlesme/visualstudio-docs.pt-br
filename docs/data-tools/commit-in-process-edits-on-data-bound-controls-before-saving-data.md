---
title: "Confirmar edições em processo em controles associados a dados antes de salvar dados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 191206e9cc16271e64abbeaba87d86ac0108924b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Confirmar edições em processo em controles associados a dados antes de salvar dados
Ao editar valores em controles associados a dados, os usuários devem navegar fora do registro atual para confirmar o valor atualizado à fonte de dados subjacente que o controle está vinculado. Quando você arrasta itens do [janela fontes de dados](add-new-data-sources.md) para um formulário, o primeiro item que você solta gera código para o **salvar** eventos de clique de botão de <xref:System.Windows.Forms.BindingNavigator>. Esse código chama o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método o <xref:System.Windows.Forms.BindingSource>. Portanto, a chamada para o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método é gerado somente para o primeiro <xref:System.Windows.Forms.BindingSource> que é adicionado ao formulário.  
  
 O <xref:System.Windows.Forms.BindingSource.EndEdit%2A> chamada confirma as alterações que estão em processo em controles associados a dados que estão sendo editados atualmente. Portanto, se um controle associado a dados ainda tem foco e clique no **salvar** botão, todas as edições pendentes nesse controle são confirmadas antes de salvar (o `TableAdapterManager.UpdateAll` método).  
  
 Você pode configurar seu aplicativo para confirmar as alterações, automaticamente, mesmo se um usuário tenta salvar dados sem confirmar as alterações, como parte do salvamento processo.  
  
> [!NOTE]
>  O designer adiciona o `BindingSource.EndEdit` código somente para o primeiro item descartado em um formulário. Portanto, você precisa adicionar uma linha de código para chamar o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> no formulário. Você pode adicionar manualmente uma linha de código para chamar o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource>. Como alternativa, você pode adicionar o `EndEditOnAllBindingSources` método para o formulário e chamá-lo antes de salvar.  
  
 O código a seguir usa uma [LINQ (consulta integrada à linguagem)](http://msdn.microsoft.com/Library/a73c4aec-5d15-4e98-b962-1274021ea93d) consulta para iterar todas <xref:System.Windows.Forms.BindingSource> componentes e a chamada a <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método para cada <xref:System.Windows.Forms.BindingSource> em um formulário.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Para chamar EndEdit para todos os componentes BindingSource em um formulário  
  
1.  Adicione o seguinte código ao formulário que contém o <xref:System.Windows.Forms.BindingSource> componentes.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]  
  
2.  Adicione a seguinte linha de código imediatamente antes de qualquer chamada para salvar os dados do formulário (o `TableAdapterManager.UpdateAll()` método):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Atualização hierárquica](../data-tools/hierarchical-update.md)