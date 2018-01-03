---
title: "Como especificar um ícone do aplicativo (Visual Basic, C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: ce92aef6f676cbdd35142f058312af90581900c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Como especificar um ícone do aplicativo (Visual Basic, C#)
A propriedade `Icon` de um projeto especifica o arquivo de ícone (.ico) que será exibido para o aplicativo compilado no Explorador de Arquivos e na barra de tarefas do Windows.  
  
 A propriedade `Icon` pode ser acessada no painel **Aplicativo** do **Designer de Projeto**, ele contém uma lista de ícones que foram adicionados a um projeto como recursos ou arquivos de conteúdo.  
  
> [!NOTE]
>  Depois de definir a propriedade do ícone para um aplicativo, talvez você também veja a propriedade `Icon` de cada **Janela** ou **Formulário** no aplicativo. Para obter informações sobre os ícones para aplicativos independentes do WPF (Windows Presentation Foundation), consulte a propriedade <xref:System.Windows.Window.Icon%2A>.  
  
### <a name="to-specify-an-application-icon"></a>Para especificar um ícone do aplicativo  
  
1.  No **Gerenciador de Soluções**, escolha um nó do projeto (não o nó **Solução**).  
  
2.  Na barra de menus, escolha **Projeto**, **Propriedades**.  
  
3.  Quando o **Designer de Projeto** for exibido, escolha a guia **Aplicativo**.  
  
4.  **(Visual Basic)**  Na lista **Ícone**, escolha um arquivo de ícone (.ico).  
  
     **C#** Próximo à lista **Ícone**, escolha o botão **\<Procurar...>** e navegue até o local do ícone de arquivo desejado.  
  
## <a name="see-also"></a>Consulte também  
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Gerenciando propriedades do aplicativo](../ide/application-properties.md)  
 [Como: adicionar ou remover recursos](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)