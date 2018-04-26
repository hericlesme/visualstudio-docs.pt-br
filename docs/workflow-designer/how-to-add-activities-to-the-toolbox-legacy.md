---
title: 'Designer de fluxo de trabalho - como: adicionar atividades à caixa de ferramentas (o legados)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99a8e1cef2ff5ddd526133355c608fa5218573d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Como: Adicione atividades a caixa de ferramentas (o legados)

Ao criar uma solução de fluxo de trabalho com o Designer de fluxo de trabalho herdado do Windows que tem como alvo o .NET Framework versão 3.5 ou o WinFX, atividades personalizadas podem ser adicionadas ao projeto de fluxo de trabalho e seus designers colocada no **caixa de ferramentas** para facilitar o acesso. Você também pode adicionar atividades diretamente para o **caixa de ferramentas** de uma biblioteca de vínculo dinâmico (DLL).

## <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Para adicionar uma atividade à caixa de ferramentas de uma DLL

1.  Clique com botão direito a superfície da janela da caixa de ferramentas em **Windows Workflow**e, em seguida, clique em **escolher itens**.

2.  No **escolher itens da caixa de ferramentas** caixa de diálogo, clique o **componentes do System. Activities** guia e, em seguida, clique em **procurar** do lado direito inferior da janela.

3.  Selecione o diretório do arquivo que contém a implementação da atividade personalizada para adicionar a DLL de **caixa de ferramentas**e, em seguida, clique em **abrir**.

4.  Clique em **Okey** para terminar de adicionar a atividade à caixa de ferramentas.

## <a name="see-also"></a>Consulte também

- [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)
- [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)