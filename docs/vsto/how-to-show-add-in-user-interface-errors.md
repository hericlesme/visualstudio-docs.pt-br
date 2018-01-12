---
title: "Como: Mostrar erros de Interface do usuário do suplemento | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4ce5204855cd6ebe468d652b8420cddc7fd19a1a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Como mostrar erros de interface do usuário do suplemento
  Por padrão, se um suplemento do VSTO tentar manipular a interface de usuário (IU) do Microsoft Office e falhar, nenhuma mensagem de erro é exibida. No entanto, você pode configurar aplicativos do Microsoft Office para exibir mensagens para erros relacionados à interface do usuário. Você pode usar essas mensagens para ajudar a determinar por que uma faixa de opções personalizada não aparece, ou por que aparece uma faixa de opções, mas não há controles aparecem.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-show-vsto-add-in-user-interface-errors"></a>Para mostrar erros de interface de usuário do suplemento do VSTO  
  
1.  Inicie o aplicativo.  
  
2.  Clique o **arquivo** guia.  
  
3.  Clique em **opções**.  
  
4.  No painel de categorias, clique em **avançado**.  
  
5.  No painel de detalhes, selecione **do suplemento do VSTO Mostrar erros de interface do usuário**e, em seguida, clique em **Okey**.  
  
    > [!NOTE]  
    >  Para o Outlook, o **do suplemento do VSTO Mostrar erros de interface do usuário** caixa de seleção está localizada no **desenvolvedor** seção do painel de detalhes. Para outros aplicativos, a caixa de seleção está localizada no **geral** seção do painel de detalhes.  
  
## <a name="see-also"></a>Consulte também  
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)   
 [Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)   
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Visão geral do painel Ações](../vsto/actions-pane-overview.md)  
  
  