---
title: "Conjunto de regras de caixa de diálogo Editor (herdado) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 1c0b55f1539526e9386df2d6de050c14fb8f59cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="rule-set-editor-dialog-box-legacy"></a>Caixa de diálogo do editor de regra (legados)
Este tópico descreve como usar o **Editor de conjunto de regras** caixa de diálogo no herdado [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 O **Editor de conjunto de regras** caixa de diálogo é usada para criar e modificar [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) regra conjuntos, que são serializados em um arquivo. rules.  
  
> [!NOTE]
>  Se você quiser abrir o arquivo. Rules com o **Editor XML com codificação**, primeiro você deve fechar a janela designer associada para o fluxo de trabalho ou atividade.  
  
 Para obter informações sobre como acessar o **Editor de conjunto de regras** caixa de diálogo, consulte [como: criar a regra um PolicyActivity definida (herdado)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).  
  
> [!WARNING]
>  O editor das regras de novas [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] que é usado para direcionar [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] não oferece suporte Multitargeting.  
  
 A tabela a seguir descreve os elementos de interface de usuário do **Editor de conjunto de regra** caixa de diálogo.  
  
|Elemento da Interface do Usuário|Descrição|  
|----------------|-----------------|  
|**Adicionar regra**|Adicione uma nova definição de regra ao conjunto de regras.|  
|**Excluir**|Exclui a regra selecionada do conjunto de regras.|  
|**Encadeamento**|Especifica que tipo de encadeamento frente para usar com o conjunto de regras. As opções disponíveis são:<br /><br /> -   **Completo encadeamento**, que especifica para usar encaminhar todos os mecanismos de encadeamento: atribuição implícita, de métodos e explícita usando um **atualização** função.<br />-   **Sequencial**, que especifica para não usar qualquer cadeia de encaminhamento.<br />-   **Atualização explícita apenas**, que especifica para executar apenas o encadeamento de encaminhamento em **atualização** ações.<br /><br /> Para obter mais informações sobre o encadeamento de encaminhamento, consulte [usando a atividade de PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|**Nome**|Regra título da coluna da lista. Clique para classificar por nome a lista de regras.|  
|**Prioridade**|Regra título da coluna da lista. Clique para classificar a lista de regras por prioridade.|  
|**Reavaliação**|Regra título da coluna da lista. Clique para classificar a lista de regras pelo tipo de reavaliação.|  
|**Visualização de regra**|Regra título da coluna da lista. Clique para classificar a lista de regras por visualização de condição e ações de uma regra.|  
|**Nome:**|Digite o nome da regra.|  
|**Prioridade:**|Insira uma prioridade para a regra. A prioridade padrão é 0.|  
|**Reavaliação:**|Especifica que tipo de reavaliação de regras para usar com a regra. As opções disponíveis são:<br /><br /> -   **Sempre**, que faz com que a regra para ser reavaliado conforme necessário.<br />-   **Nunca**, que faz com que a regra para nunca ser reavaliado. Neste caso uma regra executa somente uma vez.|  
|**Ativo**|Verifique para fazer a regra ativo.|  
|**Condição:**|Digite uma expressão para a condição de regra. Para obter informações sobre a sintaxe de expressão, consulte a seção “inserindo de expressões de condição e a ação” nessa página.|  
|**Em seguida, ações:**|Insira a expressão para ações. Para obter informações sobre a sintaxe de expressão, consulte a seção “inserindo de expressões de condição e a ação” nessa página.|  
|**Mais ações:**|Insira a expressão para outras ações. Para obter informações sobre a sintaxe de expressão, consulte a seção “inserindo de expressões de condição e a ação” nessa página.|  
|**OKEY**|Clique para salvar a regra definida como um arquivo de .rules.|  
  
 Para obter mais informações sobre conjuntos de regras, consulte [usando a atividade de PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="entering-condition-and-action-expressions"></a>Inserindo expressões de condição e de ação  
 Insira expressões para a condição e em seguida e Else ações como texto em seu respectivo texto nas caixas de **Editor de conjunto de regra** caixa de diálogo. Você pode digitar **isso.** para o editor para fazer referência a campos, propriedades e métodos usados no fluxo de trabalho, usando um tipo de IntelliSense do menu. Ou você pode digitar um nome de membro de fluxo de trabalho diretamente. Você pode chamar métodos estáticos em tipos referenciados digitando o nome da classe seguida do nome do método.  
  
 Você pode adicionar operadores lógicos a condição, como AND, OU, e NOT. Você também pode adicionar predicados. Um predicado é um operador binário e dois operandos. Os operadores binários com suporte são = =, >, \<, > = e < =. Os operandos são suportados valor constante, função aritmética, e membros públicos o escopo.  
  
 Você pode especificar o tipo de comparação, e você pode comparar e **nulo** ou uma cadeia de caracteres vazia. Você pode aninhar chamadas aos membros em uma variável que contém um tipo complexo, por exemplo, `this.Address.State == "WA"`.  
  
 As expressões dão suporte aos seguintes operadores:  
  
-   Operadores relacionais: ==, =! =  
  
-   Operadores de comparação: <, \<=, >, > =  
  
-   Operadores aritméticos: +, -, *,/, MODIFICAÇÃO  
  
-   Operadores lógicos: E, & &, OR, &#124; &#124; não,!  
  
-   Operadores bit a bit: &, &#124;  
  
 Precedência de operadores de expressão segue regras de precedência de operador C#.  
  
 Para obter mais informações sobre condições, consulte [usando condições em fluxos de trabalho](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77).  
  
### <a name="halt-and-update-functions"></a>Interromper e atualizar funções  
 **Em seguida, ações:** e **ações Else:** expressões dão suporte a **interromper** e **atualização** funções. Para usar o **interromper** de função, digite **interromper** em uma **, em seguida, a ação:** ou **ação Else:** caixa de texto. O **interromper** ação faz com que a execução do conjunto de regras interromper imediatamente, e o controle retorna para o código de chamada. Você usa o **atualização** função com o encadeamento de encaminhamento.  
  
 Um **atualização** instrução pode ser expresso no editor em uma das duas formas; ambos os formulários são mostrados no exemplo a seguir:  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 Para obter mais informações sobre como usar **atualização** com o encadeamento de encaminhamento, consulte [usando a atividade de PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).  
  
## <a name="see-also"></a>Consulte também  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Caixa de diálogo Definir selecione regra (herdado)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Usando a atividade de PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Usando condições em fluxos de trabalho](http://go.microsoft.com/fwlink?LinkID=65009)