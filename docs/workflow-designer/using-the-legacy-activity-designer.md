---
title: Designer de fluxo de trabalho - usando o Designer de atividade herdado
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdf7ae585697db19293362a31c5751d44c7421c5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="using-the-legacy-activity-designer"></a>Usando o designer herdado de atividades

Este tópico descreve como usar o designer de atividade no Designer de fluxo de trabalho herdado do Windows. Use o designer herdado durante o direcionamento do .NET Framework versão 3.5 ou o WinFX.

O designer de atividade permite que você crie suas próprias atividades personalizados.

## <a name="creating-a-custom-activity"></a>Criando uma atividade personalizado

Siga estas etapas para criar uma atividade personalizado utilizando o designer de atividade:

1.  Sobre o **projeto** menu, clique em **Adicionar atividade**.

2.  Selecione o **atividade** ou **atividade (com separação de código)** modelo.

    1.  Use o **atividade** modelo para criar uma atividade com a definição de atividade e o código do usuário no mesmo arquivo de código.

    2.  Use o **atividade (com separação de código)** modelo para criar uma atividade com a definição de atividade, expressada como a marcação de fluxo de trabalho e o código do usuário em um arquivo de código separado.

3.  Digite um nome de atividade ou mantenha o nome padrão e, em seguida, clique em **adicionar**.

Você também pode criar um conjunto de atividades personalizadas, criando um novo projeto do tipo **biblioteca de atividades de fluxo de trabalho**. Para obter mais informações sobre esse tipo de projeto, consulte [como: criar uma biblioteca de atividades de fluxo de trabalho (legados)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Configurando uma atividade

Quando o designer de atividade estiver ativo, você pode usar o navegador de propriedade para configurar as propriedades listadas na tabela a seguir.

|Propriedade|Comentários|
|--------------|--------------|
|**Nome**|Nome da atividade.|
|**Classe base**|Classe base que a atividade deriva. A classe base padrão é [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). No **propriedades** janela, clique no **classe Base** reticências **[...]**  para selecionar outra classe base no [procurar e selecione uma caixa de diálogo de tipo .NET (legados)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Descrição**|Descrição definido pelo usuário de atividade.|
|**Habilitado**|Definido como **True** por padrão para habilitar a validação e execução da atividade. Definido como **False** para desabilitar a execução da atividade e a validação. Para obter informações sobre a execução da atividade e a validação, consulte [atividades de fluxo de trabalho de desenvolvimento](http://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Adicionando atividades filhos

Você pode arrastar atividades filhos da caixa de ferramentas para a atividade que você está criando. Você pode então configurar cada atividade filho usando o navegador de propriedade.

## <a name="see-also"></a>Consulte também

- [Desenvolvimento de atividades de fluxo de trabalho](http://go.microsoft.com/fwlink?LinkID=65024)
- [Criação de atividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65021)
- [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)
- [Exemplos de atividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65022)
- [Como criar uma biblioteca de atividade de fluxo de trabalho (herdado)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)
- [Usando o Designer de Fluxo de Trabalho herdado](../workflow-designer/using-the-legacy-workflow-designer.md)