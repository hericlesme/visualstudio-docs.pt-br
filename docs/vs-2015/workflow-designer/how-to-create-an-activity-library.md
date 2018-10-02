---
title: 'Como: criar uma biblioteca de atividades | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8e3579061b65d142fdfb0cc992813ffc45663464
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475857"
---
# <a name="how-to-create-an-activity-library"></a>Como: Crie uma biblioteca de atividade
As atividades personalizados são usadas para modelar seus processos comerciais específicos em um fluxo de trabalho. O modelo biblioteca de atividade em [!INCLUDE[vs2010](../includes/vs2010-md.md)] foi fornecido para permite que você crie como atividades personalizados que usam visualmente [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
### <a name="to-create-a-workflow-activity-library"></a>Para criar uma biblioteca de atividade de fluxo de trabalho  
  
1.  Inicie o [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Sobre o **arquivo** , aponte para **New**e, em seguida, selecione **projeto...** .  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  No **tipos de projeto** painel, selecione **fluxo de trabalho** de qualquer um os **Visual c#** projetos ou **Visual Basic** agrupamentos dependendo da sua preferência de idioma.  
  
4.  No **modelos** painel, selecione **biblioteca de atividades**.  
  
5.  No **nome** caixa, digite um nome descritivo para o seu projeto para torná-lo mais fácil identificar.  
  
6.  No **local** caixa, digite o diretório no qual você deseja salvar seu projeto ou clique em **procurar** para navegar até ele.  
  
7.  No **Solution** caixa, digite um nome descritivo para sua solução e clique **Okey**.  
  
    > [!NOTE]
    >  Se você deseja adicionar um aplicativo de console do fluxo de trabalho a uma solução existente, abra essa solução na [!INCLUDE[vs2010](../includes/vs2010-md.md)], clique com botão direito na solução **Gerenciador de soluções**e selecione **Add**, em seguida,  **Novo projeto...** Para abrir o **novo projeto** caixa de diálogo. Continuar conforme descrito acima neste procedimento.  
  
8.  O modelo de projeto cria uma definição de atividade em XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] abre e exibe a tela para a atividade personalizado.  
  
9. Arraste uma atividade do **caixa de ferramentas** para a superfície de design para incluí-lo em sua atividade personalizada.  
  
    > [!CAUTION]
    >  Uma atividade é permitida você só filho no corpo da atividade personalizado; no entanto, a atividade filho pode ser uma atividade de composição, como uma atividade de <xref:System.Activities.Statements.Sequence> ou a atividade de <xref:System.Activities.Statements.Flowchart> .  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar uma atividade](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Criando um projeto de fluxo de trabalho](../workflow-designer/creating-a-workflow-project.md)