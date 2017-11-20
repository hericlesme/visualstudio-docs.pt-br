---
title: "Como: automaticamente incrementar o ClickOnce publicar versão | Microsoft Docs"
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
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 71665ea5053a4d3ddbdb933d2ecdf4ea20ba83c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Como incrementar a versão da publicação do ClickOnce automaticamente
Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, alterando o `Publish Version` propriedade faz com que o aplicativo a ser publicado como uma atualização. Por padrão, o Visual Studio incrementa automaticamente o `Revision` número das `Publish Version` cada vez que você publicar o aplicativo.  
  
 Você pode desativar esse comportamento no **publicar** página do **Project Designer**.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para desabilitar automaticamente incrementando a versão de publicação  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **versão publicar** seção, desmarque o **incrementar automaticamente a revisão com cada versão** caixa de seleção.  
  
## <a name="see-also"></a>Consulte também  
 [Como definir a versão da publicação do ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)