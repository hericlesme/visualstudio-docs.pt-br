---
title: Caixa de diálogo de definição de CorrelatesOn | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 930f291f68e62e70c4d2a03f490f84fd8d36f657
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="correlateson-definition-dialog-box"></a>Caixa de diálogo definição de CorrelatesOn
O **CorrelatesOn** no Designer de fluxo de trabalho do Windows, a caixa de diálogo é usada para editar o <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriedade de um <xref:System.ServiceModel.Activities.Receive> atividade. Para obter mais informações, consulte o [Receive](../workflow-designer/receive-activity-designer.md) tópico.

 Correlação entre atividades de <xref:System.ServiceModel.Activities.Receive> especifica como as operações de serviço diferentes conectam entre si em um fluxo de trabalho.

 A tabela a seguir descreve os elementos de interface de usuário do **CorrelatesOn** caixa de diálogo.

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle> que é usado para rotear a mensagem à instância apropriado de fluxo de trabalho.|
|**Consultas XPath**|Um par chave/valor que contém as consultas usadas para extrair dados de correlação das mensagens de entrada. Isso corresponde à propriedade de <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> . Consultas XPath estão contidas em um objeto de <xref:System.ServiceModel.MessageQuerySet> .|

## <a name="to-launch-the-correlateson-dialog-box"></a>Para iniciar a caixa de diálogo CorrelatesOn
 O **Receive** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com <xref:System.Activities.Activity.DisplayName%2A> padrão Receive. Selecione o **Receive** designer de atividade e clique no botão de reticências ao lado do texto (coleção) para o **CorrelatesOn** propriedade na grade de propriedade para o **definição de CorrelatesOn**  caixa de diálogo.

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Receive>
- [Caixa de diálogo Adicionar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Adicionar caixa de diálogo correlação](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Caixa de diálogo Inicializar Correlação](../workflow-designer/initialize-correlation-dialog-box.md)