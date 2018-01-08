---
title: "Como: personalizar um pacote de solução do SharePoint usando destinos do MSBuild | Microsoft Docs"
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
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4c0fbc4a2feb3abc92c47567dcb0ea3d425ddda1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Como personalizar um pacote de soluções do SharePoint usando destinos do MSBuild
  Usando destinos do MSBuild no prompt de comando, você pode personalizar como o Visual Studio cria arquivos de pacote do SharePoint (. wsp). Por exemplo, você pode personalizar as propriedades de MSBuild para alterar o diretório intermediário de empacotamento e os grupos de itens do MSBuild que especificam os arquivos enumerados.  
  
## <a name="customizing-and-running-msbuild-targets"></a>Personalizando e execução de destinos do MSBuild  
 Se você personalizar os destinos BeforeLayout e AfterLayout, você pode executar tarefas antes de layout do pacote, como adicionar, remover ou modificar arquivos que serão empacotados.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Para personalizar o destino BeforeLayout  
  
1.  Abra um editor, como o bloco de notas e, em seguida, adicione o código a seguir.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     Este exemplo exibe uma mensagem antes do empacotamento desse destino.  
  
2.  Nomeie o arquivo **CustomLayout.SharePoint.targets**e, em seguida, salve-o na pasta do projeto do SharePoint.  
  
3.  Abra o projeto, abra o menu de atalho e escolha **descarregar projeto**.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o projeto e, em seguida, escolha **editar***ProjectName***. vbproj** ou **Editar***ProjectName***. csproj**.  
  
5.  Após o `Import` linha no final do arquivo de projeto, adicione a linha a seguir.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Salve e feche o arquivo de projeto.  
  
7.  Em **Solution Explorer**, abra o menu de atalho para o projeto e, em seguida, escolha **recarregar projeto**.  
  
 Quando você publicar o projeto, a mensagem será exibida na saída antes do início de empacotamento.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Para personalizar o destino AfterLayout  
  
1.  Na barra de menus, escolha **arquivo**, **abrir**, **arquivo**.  
  
2.  No **abrir arquivo** caixa de diálogo, navegue até a pasta do projeto, escolha o arquivo CustomLayout.target e, em seguida, escolha o **abrir** botão.  
  
3.  Antes de `</Project>` marca, adicione o seguinte código:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     Este exemplo exibe uma mensagem depois que esse destino é empacotado.  
  
4.  Salve e feche o arquivo de destino.  
  
5.  Reinicie o Visual Studio e, em seguida, abra o projeto.  
  
 Quando você publicar o projeto, será exibida a mensagem de BeforeLayout antes do início de empacotamento e a mensagem AfterLayout aparece após a conclusão de empacotamento.  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  