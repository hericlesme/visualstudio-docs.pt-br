---
title: "Como: adicionar atividades à caixa de ferramentas (herdado) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d6d7e817ae34b3e39d617ad5d12802cabd5cedc
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Como: Adicione atividades a caixa de ferramentas (o legados)
Ao criar uma solução de fluxo de trabalho com o Designer de fluxo de trabalho herdado do Windows que tem como destino o [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], atividades personalizadas podem ser adicionadas ao projeto de fluxo de trabalho e seus designers colocados no **caixa de ferramentas** para facilitar o acesso. Você também pode adicionar atividades diretamente para o **caixa de ferramentas** de uma biblioteca de vínculo dinâmico (DLL).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Para adicionar uma atividade à caixa de ferramentas de uma DLL

1.  Clique com botão direito a superfície da janela da caixa de ferramentas em **Windows Workflow**e, em seguida, clique em **escolher itens**.

2.  No **escolher itens da caixa de ferramentas** caixa de diálogo, clique o **componentes do System. Activities** guia e, em seguida, clique em **procurar** do lado direito inferior da janela.

3.  Selecione o diretório do arquivo que contém a implementação da atividade personalizada para adicionar a DLL de **caixa de ferramentas**e, em seguida, clique em **abrir**.

4.  Clique em **Okey** para terminar de adicionar a atividade à caixa de ferramentas.

## <a name="see-also"></a>Consulte também

- [Usando o designer de atividade herdado](../workflow-designer/using-the-legacy-activity-designer.md)
- [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)