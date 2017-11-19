---
title: 'Como: criar aplicativos de Console de fluxo de trabalho sequencial (herdado) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e9732334f422b4042f2cd581afaea06bf99ab16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Como: Criar aplicativos de console sequenciais de fluxo de trabalho (o legados)
Siga estas etapas para criar um projeto de aplicativo de console sequencial de fluxo de trabalho usando [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] herdado fornecido por [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>Para criar um aplicativo de console sequencial de fluxo de trabalho  
  
1.  Inicie o Visual Studio.  
  
2.  Sobre o **arquivo** , aponte para **novo**e, em seguida, selecione **projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  Selecione o **.NET Framework 3.0** opção ou **.NET Framework 3.5** opção no menu suspenso na parte superior da lista da **novo projeto** janela para acessar o designer herdado.  
  
    > [!NOTE]
    >  A opção padrão na [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] é **.NET Framework 4**. Essa opção é usada criar aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que direcionam [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e usa o designer herdado.  
  
4.  No **tipos de projeto** painel, selecione projetos do Visual c# ou projetos do Visual Basic (em **outras linguagens**) e, em seguida, selecione **fluxo de trabalho**.  
  
5.  No **modelos** painel, selecione **aplicativo de Console de fluxo de trabalho sequencial**.  
  
6.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.  
  
7.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.  
  
     O designer do Windows Forms abre e exibe o Form1 do projeto que você criou.  
  
8.  Clique em **OK**.  
  
     Designer de Fluxo de Trabalho abre e exibe a superfície de design de fluxo de trabalho de fluxo de trabalho sequencial que você criou.  
  
9. Arraste uma atividade do **caixa de ferramentas** à superfície de design no **descartar atividade** designado área.  
  
## <a name="see-also"></a>Consulte também  
 [Criando projetos de fluxo de trabalho herdado](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Fluxos de trabalho de desenvolvimento](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)