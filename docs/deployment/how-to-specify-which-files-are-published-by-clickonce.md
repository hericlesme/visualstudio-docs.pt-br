---
title: "Como: especificar quais arquivos são publicados pelo ClickOnce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 68773435bc35a93ab49189306db532c68e2b8dad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Como especificar os arquivos a serem publicados pelo ClickOnce
Ao publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos de aplicativo, todos os não-código do projeto são implantados com o aplicativo. Em alguns casos, não pode ser ou precisa publicar certos arquivos, ou talvez você queira instalar determinados arquivos com base nas condições. O Visual Studio fornece os recursos para excluir arquivos, marcar arquivos como arquivos de dados ou de pré-requisitos e criar grupos de arquivos para instalação condicional.  
  
 Arquivos para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos são gerenciados no **arquivos de aplicativo** caixa de diálogo, acessível a partir de **publicar** página do **Designer de projeto**.  
  
 Inicialmente, há um grupo de arquivo único chamado **(obrigatório)**. Você pode criar grupos de arquivos adicionais e atribuir arquivos a eles. Não é possível alterar o **grupo de Download** para arquivos que são necessários para o aplicativo seja executado. Por exemplo, o aplicativo .exe ou arquivos marcado como arquivos de dados devem pertencer ao **(obrigatório)** grupo.  
  
 Status de publicação padrão valor de um arquivo é marcado com **(automática)**. Por exemplo, .exe do aplicativo tem um status de publicação de **incluir (Auto)** por padrão.  
  
 Arquivos com o **ação de compilação** propriedade definida como **conteúdo** são designados como arquivos de aplicativo e será marcado como incluído por padrão. Eles podem ser incluídos, excluídos ou marcados como arquivos de dados. As exceções são as seguintes:  
  
-   Arquivos de dados, como arquivos de banco de dados SQL (. mdf e.) e arquivos XML serão marcados como arquivos de dados por padrão.  
  
-   Referências a assemblies (arquivos. dll) são designadas como a seguir quando você adicionar a referência: se **Copy Local** é **False**, ela é marcada por padrão como um assembly de pré-requisito (**(pré-requisito Auto)**) que deve estar presente no GAC, antes do aplicativo está instalado. Se **Copy Local** é **True**, o assembly é marcado por padrão como um assembly de aplicativo (**incluir (Auto)**) e serão copiados para a pasta do aplicativo durante a instalação. Uma referência COM aparecerão no **arquivos de aplicativo** caixa de diálogo caixa (como um arquivo. ocx) somente se seu **isolado** está definida como **True**. Por padrão, ele será incluído.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Para adicionar arquivos à caixa de diálogo de arquivos do aplicativo  
  
1.  Selecione um arquivo de dados no **Gerenciador de soluções**.  
  
2.  Na janela Propriedades, altere o **ação de compilação** propriedade para o **conteúdo** valor.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>Para excluir arquivos de publicação do ClickOnce  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **arquivos de aplicativo** para abrir o **arquivos de aplicativo** caixa de diálogo.  
  
4.  No **arquivos de aplicativo** caixa de diálogo, selecione o arquivo que você deseja excluir.  
  
5.  No **Status da publicação** campo, selecione **excluir** na lista suspensa.  
  
### <a name="to-mark-files-as-data-files"></a>Para marcar os arquivos como arquivos de dados  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **arquivos de aplicativo** para abrir o **arquivos de aplicativo** caixa de diálogo.  
  
4.  No **arquivos de aplicativo** caixa de diálogo, selecione o arquivo que você deseja marcar como dados.  
  
5.  No **Status da publicação** campo, selecione **arquivo de dados** na lista suspensa.  
  
### <a name="to-mark-files-as-prerequisites"></a>Para marcar os arquivos como pré-requisitos  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **arquivos de aplicativo** para abrir o **arquivos de aplicativo** caixa de diálogo.  
  
4.  No **arquivos de aplicativo** caixa de diálogo, selecione o assembly de aplicativo (arquivo. dll) que você deseja marcar como um pré-requisito. Observe que o seu aplicativo deve ter uma referência para o assembly de aplicativo para que ele apareça na lista.  
  
5.  No **Status da publicação** campo, selecione **pré-requisito** na lista suspensa.  
  
### <a name="to-add-a-new-file-group"></a>Para adicionar um novo grupo de arquivos  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **arquivos de aplicativo** para abrir o **arquivos de aplicativo** caixa de diálogo.  
  
4.  No **arquivos de aplicativo** caixa de diálogo, selecione o **grupo** field para um arquivo que você deseja incluir no novo grupo.  
  
    > [!NOTE]
    >  Os arquivos devem ter o **ação de compilação** propriedade definida como **conteúdo** antes que os nomes de arquivo apareçam no **arquivos de aplicativo** caixa de diálogo.  
  
5.  No **grupo de Download** campo, selecione  **\<novo... >** na lista suspensa.  
  
6.  No **novo grupo** caixa de diálogo, insira um nome para o grupo e, em seguida, clique em **Okey**.  
  
### <a name="to-add-a-file-to-a-group"></a>Para adicionar um arquivo a um grupo  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **arquivos de aplicativo** para abrir o **arquivos de aplicativo** caixa de diálogo.  
  
4.  No **arquivos de aplicativo** caixa de diálogo, selecione o **grupo** field para um arquivo que você deseja incluir no novo grupo.  
  
5.  No **Download grupo** , selecione um grupo na lista suspensa.  
  
    > [!NOTE]
    >  Não é possível alterar o **grupo de Download** para arquivos que são necessários para o aplicativo seja executado.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)