---
title: "Personalizando uma faixa de opções para Outlook | Microsoft Docs"
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
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f44d1d8c2982e23995a3625205eaa0bddf7adc4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-a-ribbon-for-outlook"></a>Personalizando uma faixa de opções para Outlook
  Quando você personaliza a faixa de opções no Microsoft Office Outlook, você deve considerar onde a faixa de opções personalizada será exibida no aplicativo. O Outlook exibe a faixa de opções na interface do usuário principal do aplicativo (UI) e no windows que são abertos quando os usuários executam determinadas tarefas, como a criação de mensagens de email. Essas janelas de aplicativo são nomeadas inspetores.  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer: usar o Designer de faixa de opções para personalizar a faixa de opções no Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-a-custom-ribbon-to-the-main-application-ui"></a>Adicionando uma faixa de opções personalizada para o aplicativo principal da interface do usuário  
 O aplicativo principal da interface do usuário no Outlook é chamado do Explorer. Se você estiver usando o **faixa de opções (Visual Designer)** item, você pode adicionar uma faixa de opções para o Gerenciador de clicando o **RibbonType** propriedade da faixa de opções no **propriedades** janela, e, em seguida, selecionando **Microsoft.Outlook.Explorer**.  
  
## <a name="assigning-a-ribbon-to-an-inspector"></a>Atribuir uma faixa de opções para um Inspetor  
 Identificar o Inspetor de que deseja personalizar, especificando o tipo de faixa de opções que corresponde à classe de mensagem para o Inspetor.  
  
 Se você estiver usando o **faixa de opções (Visual Designer)** item, clique no **RibbonType** propriedade da faixa de opções no **propriedades** janela e, em seguida, selecione uma ou mais IDs de faixa de opções a lista de valores.  
  
 Você pode adicionar mais de uma faixa de opções para um projeto. Se mais de uma faixa de opções compartilha um ID de faixa de opções, substituir o método CreateRibbonExtensibilityObject o `ThisAddin` classe do seu projeto para especificar qual faixa de opções para exibir em tempo de execução. Para obter mais informações, consulte [visão geral da faixa de opções](../vsto/ribbon-overview.md). Para obter mais informações sobre cada tipo de faixa de opções, consulte o artigo técnico [Personalizando a faixa de opções no Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Especificando o tipo de faixa de opções usando o XML da faixa de opções  
 Se você estiver usando o **da faixa de opções (XML)** item, verifique o valor do *ribbonID* parâmetro o <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> método e retorne a faixa de opções apropriada.  
  
 O <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> método é gerado automaticamente pelo Visual Studio no arquivo de código da faixa de opções. O *ribbonID* parâmetro é uma cadeia de caracteres que identifica o Explorer ou um tipo específico de Inspetor. Para obter uma lista dos possíveis valores da *ribbonID* parâmetro, consulte o artigo técnico [Personalizando a faixa de opções no Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 O exemplo de código a seguir demonstra como exibir um personalizado somente na faixa de opções de `Microsoft.Outlook.Mail.Compose` Inspetor. Este é o Inspetor que é aberto quando um usuário cria uma nova mensagem de email. Especificada na faixa de opções para exibir o `GetResourceText()` método, que é gerado o **faixa de opções** classe. Para obter mais informações sobre o **faixa de opções** de classe, consulte [XML da faixa de opções](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Acessando a faixa de opções em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Designer de faixa de opções](../vsto/ribbon-designer.md)   
 [XML da faixa de opções](../vsto/ribbon-xml.md)  
  
  