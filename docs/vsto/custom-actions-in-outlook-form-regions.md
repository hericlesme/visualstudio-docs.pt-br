---
title: "Regiões de formulário de ações personalizadas no Outlook | Microsoft Docs"
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
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 89b49139db9d91ba742caeb80308f9175195a843
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-actions-in-outlook-form-regions"></a>Personalizar ações em regiões de formulário do Outlook
  Ações exibem botões que permitem aos usuários responder a um item do Microsoft Office Outlook. Por exemplo, para responder a um item de email, os usuários clicam o **resposta**, **responder a todos**, ou **Forward** botões de ação. Cada uma dessas ações cria um novo item de email e preenche os campos do item usando as informações do item original.  
  
 Você pode criar uma ação personalizada que abre qualquer tipo de item do Outlook. Por exemplo, você pode adicionar uma ação personalizada que abre um novo item de compromisso ou tarefa. Definir as propriedades de uma ação personalizada ou use o código personalizado para preencher os campos do novo item. Ações personalizadas são exibidas no **ações personalizadas** lista suspensa de um item que está aberto em uma janela de Inspetor do Outlook.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-custom-actions-to-a-form-region"></a>Adicionar ações personalizadas para uma região de formulário  
 Para adicionar uma ação personalizada para uma região de formulário, use o **ações personalizadas** caixa de diálogo. Você pode abrir o **ações personalizadas** da caixa de diálogo **Solution Explorer** expandindo o **manifesto** nó, selecionando o **CustomActions**propriedade e, em seguida, clique no botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse do Designer de dispositivo móvel ASP.NET")).  
  
 Você pode usar o **ações personalizadas** caixa de diálogo para especificar um *formulário de destino*. Um formulário de destino é o que aparece quando o usuário executa a ação personalizada.  
  
 Você também pode usar o **ações personalizadas** caixa de diálogo para especificar como você deseja informações do item original apareça no formulário de destino.  
  
 A tabela a seguir descreve as propriedades que estão disponíveis no **ações personalizadas** caixa de diálogo.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|**AddressLike**|Especifica como o formulário de destino será resolvido.|  
|**Corpo**|Especifica como o corpo do item original é anexado ao formulário de destino.|  
|**Habilitado**|Indica se a ação personalizada está habilitada. Se essa propriedade é definida como **false**, a ação personalizada está desabilitada.|  
|**Método**|Especifica o tipo de resposta disponível quando a ação personalizada é executada. A ação personalizada pode enviar o formulário, abrir o formulário ou solicitar que o usuário se deseja enviar ou abrir o formulário.|  
|**Nome**|Especifica o nome interno que você pode usar para fazer referência a esta ação personalizada em código.|  
|**ShowOnRibbon**|Indica se deve exibir a ação personalizada na faixa de opções do item original.|  
|**SubjectPrefix**|Especifica o texto que é inserido no início da linha de assunto do formulário de destino.|  
|**TargetForm**|Especifica o nome de classe de mensagem do formulário de destino. Por exemplo, digite **IPM. Tarefa** para abrir um formulário de tarefa.|  
|**Título**|Especifica o rótulo do botão de ação personalizada.|  
  
## <a name="customizing-a-custom-action-at-run-time"></a>Personalizando uma ação personalizada em tempo de execução  
 Você também pode adicionar o comportamento para a ação personalizada usando o código. Por exemplo, você pode adicionar o código que usa os nomes de destinatários de email e adiciona esses nomes como participantes em um novo item de compromisso. Para fazer isso, manipule o [personalizada de](http://msdn.microsoft.com/library/office/ff862186.aspx) evento o [objeto MailItem](http://msdn.microsoft.com/library/office/ff861332.aspx).  
  
## <a name="see-also"></a>Consulte também  
 [Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)   
 [Passo a passo: Criando uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Associando uma região do formulário a uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  