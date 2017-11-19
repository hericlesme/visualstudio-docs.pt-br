---
title: 'Como: criar uma biblioteca de fluxo de trabalho sequencial (legados) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 52c78a49a468be929e93946b3b162c31370558dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Como: Criar uma biblioteca sequencial de fluxo de trabalho (o legados)
Siga estas etapas para criar um projeto sequencial de biblioteca de fluxo de trabalho usando [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] herdado fornecido por [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-sequential-workflow-library-project"></a>Para criar um projeto sequencial de biblioteca de fluxo de trabalho  
  
1.  Inicie o Visual Studio.  
  
2.  Sobre o **arquivo** , aponte para **novo**e, em seguida, selecione **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  Selecione o **.NET Framework 3.0** opção ou **.NET Framework 3.5** opção no menu suspenso na parte superior da lista da **novo projeto** janela para acessar o designer herdado.  
  
    > [!NOTE]
    >  A opção padrão na [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] é **.NET Framework 4**. Essa opção é usada criar aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que direcionam [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e usa o designer herdado.  
  
4.  No **tipos de projeto** painel, selecione Visual c# ou Visual Basic (em **outras linguagens**) e, em seguida, selecione **fluxo de trabalho**.  
  
5.  No **modelos** painel, selecione **biblioteca de fluxo de trabalho sequencial**.  
  
6.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.  
  
7.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.  
  
     Se você desejar um diretório da solução para o projeto, selecione o **criar diretório para solução** caixa de seleção e insira um nome no **nome da solução** caixa.  
  
8.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Criando projetos de fluxo de trabalho herdado](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Estilos de criação de fluxo de trabalho](http://msdn.microsoft.com/en-us/aacf4ec6-da05-4974-958a-974769dda739)