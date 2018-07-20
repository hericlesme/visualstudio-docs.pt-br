---
title: 'Como: automaticamente incrementar a publicação do ClickOnce versão | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beada30e45ce2d46500654bca5051bd51db02d66
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151958"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Como: automaticamente incrementar a publicação do ClickOnce versão
Ao publicar uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, alterando o `Publish Version` propriedade faz com que o aplicativo a ser publicado como uma atualização. Por padrão, o Visual Studio incrementa automaticamente o `Revision` número das `Publish Version` cada vez que você publica o aplicativo.  
  
 Você pode desativar esse comportamento na **Publish** página do **Designer de projeto**.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para desabilitar a incrementar automaticamente a versão de publicação  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **Publish Version** seção, desmarque as **incrementar automaticamente a revisão com cada versão** caixa de seleção.  
  
## <a name="see-also"></a>Consulte também  
 [Como: definir a publicação do ClickOnce versão](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)