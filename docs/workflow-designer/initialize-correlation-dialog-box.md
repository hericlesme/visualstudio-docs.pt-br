---
title: Designer de fluxo de trabalho - inicializar a caixa de diálogo de correlação
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93ce95c7a821d243af842170ba30ec82647933ab
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="initialize-correlation-dialog-box"></a>Inicializar a caixa de diálogo correlação

O **inicializar correlação** no Designer de fluxo de trabalho do Windows, a caixa de diálogo é usada para editar o <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade de um <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade. Para obter mais informações, consulte o [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) tópico.

 A tabela a seguir descreve os elementos de interface de usuário do **inicializar correlação** caixa de diálogo.

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Correlação**|<xref:System.ServiceModel.Activities.CorrelationHandle> de correlação para inicializar.|
|**Inicializar**|Um par chave/valor que contém os dados para inicializar. Isso corresponde à propriedade de <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . Um exemplo de um par chave/valor válido deve ser uma chave chamada "OrderID" emparelhado com uma variável chamada OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Para iniciar a caixa de diálogo correlação inicializar

-   Clique em **exibição** no **InitializeCorrelation** atividade designer ou selecione um <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade no Designer de fluxo de trabalho e, em seguida, clique no botão de reticências ao lado de <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriedade no grade de propriedade.

## <a name="see-also"></a>Consulte também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)