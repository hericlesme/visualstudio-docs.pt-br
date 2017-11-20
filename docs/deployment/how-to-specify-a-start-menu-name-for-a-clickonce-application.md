---
title: 'Como: especificar um nome no Menu Iniciar para um aplicativo ClickOnce | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: b27cf6d67cef1098a54277d4857b75d3fba0ff65
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Como especificar um nome no menu Iniciar para um aplicativo ClickOnce
Quando um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo está instalado para utilização online e offline, uma entrada é adicionada para o **iniciar** menu e **adicionar ou remover programas** lista. Por padrão, o nome de exibição é igual ao nome do assembly de aplicativo, mas você pode alterar o nome de exibição, definindo **nome do produto** no **opções de publicação** caixa de diálogo.  
  
 **Nome do produto** será exibido na página Publish; para um aplicativo offline, ele será o nome da entrada no **iniciar** menu e ele também será o nome que aparece no **adicionar ou remover Programas**.  
  
 **Nome do publicador** aparecerá na página Publish acima **nome do produto**, e para um aplicativo offline, ele também será o nome da pasta que contém o ícone do aplicativo no **iniciar**  menu.  
  
 Você pode definir o **nome do produto** e **nome do publicador** propriedades o **opções de publicação** caixa de diálogo, disponível no **publicar** página do **Designer de projeto**.  
  
### <a name="to-specify-a-start-menu-name"></a>Para especificar um nome no menu Iniciar  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **opções** para abrir o **opções de publicação** caixa de diálogo.  
  
4.  Clique em **descrição**.  
  
5.  No **opções de publicação** caixa de diálogo, digite o nome a ser exibido em **nome do produto**.  
  
6.  Opcionalmente, você pode inserir um nome de editor em **nome do publicador**.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)