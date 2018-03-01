---
title: 'Como: adicionar e remover pastas mapeadas | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 29809344ee8a3f446589ba84f2fc47b1cf407582
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Como adicionar e remover pastas mapeadas
  Algumas pastas usadas com frequência no SharePoint, como imagens e Layouts, profundamente são inseridas na hierarquia de arquivos. Você pode mapear essas pastas para um projeto do SharePoint para acessá-los mais facilmente. Pastas mapeadas são pastas no projeto do SharePoint que correspondem ao local físico dos arquivos na instalação do servidor do SharePoint.  
  
 Quando você implanta um aplicativo do SharePoint, o conteúdo da pasta mapeada e todas as subpastas são copiadas pelo pacote de solução (. wsp) para o servidor que está executando o SharePoint no local especificado na árvore de pastas do SharePoint. Esse local é determinado pelo **local de implantação** propriedade que é definida para a pasta mapeada. Todas as subpastas na pasta mapeada são relativos ao **local de implantação** da pasta mapeada. Observe que o **local de implantação** propriedade, não o nome da pasta mapeada, determina quais itens são implantados.  
  
 Você pode adicionar pastas mapeadas para um projeto usando comandos na barra de menu ou menu de atalho para o projeto. Você pode usar o **adicionar o SharePoint "Imagens" mapeado pasta** e **adicionar o SharePoint "Layouts" pasta** mapeado de comandos para adicionar essas pastas que são usadas com mais frequência. Você pode mapear qualquer uma das outras pastas do SharePoint disponíveis para seu projeto usando o **adicionar pasta do SharePoint mapeado** comando no menu de atalho e, em seguida, especificando as pastas no **adicionar pasta do SharePoint mapeado** caixa de diálogo.  
  
## <a name="adding-mapped-folders-to-a-project"></a>Adicionando pastas mapeadas a um projeto  
 O procedimento a seguir descreve como adicionar duas pastas mapeadas para um projeto do visual web part. Para começar, você deve criar um projeto do visual web part.  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>Para adicionar pastas mapeadas para um projeto  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda o **Visual Basic** ou **Visual C#** nó, expanda o **Office para o SharePoint** nó e, em seguida, Escolha o **soluções do SharePoint** nó.  
  
3.  Na lista de modelos de projeto, escolha o **Web Part do SharePoint 2013 Visual** modelo.  
  
4.  No **nome** , digite **TestProject1**e, em seguida, escolha o **Okey** botão.  
  
5.  No **Assistente de personalização do SharePoint**, escolha o **concluir** botão para manter as configurações padrão.  
  
6.  Em **Solution Explorer**, escolha o nó do projeto e, em seguida, na barra de menus, escolha **projeto**, **adicionar o SharePoint "Imagens" mapeado pasta**.  
  
     Uma pasta denominada **imagens** aparece em seu projeto e contém uma subpasta chamada TestProject1. Essa pasta mapeada contém imagens para o projeto do visual web part.  
  
7.  Em **Solution Explorer**, escolha o nó do projeto e, em seguida, na barra de menus, escolha **projeto**, **adicionar pasta do SharePoint mapeado** para exibir o **adicionar Pasta do SharePoint mapeado** caixa de diálogo.  
  
8.  Na exibição de árvore de pastas que estão disponíveis para mapeamento, escolha o **recursos** pasta e, em seguida, escolha o **Okey** botão.  
  
     Uma pasta denominada **recursos** aparece em seu projeto. Essa pasta pode armazenar itens como arquivos de recursos de cadeia de caracteres. Subpastas podem ser útil para organizar o conteúdo de uma pasta mapeada, mas eles são criados automaticamente quando você adiciona uma pasta mapeada usando o **adicionar pasta do SharePoint mapeado** comando. Para adicionar uma subpasta, escolha o **recursos** pasta e, em seguida, na barra de menus, escolha **projeto**, **nova pasta**.  
  
## <a name="changing-the-deployment-location-of-a-mapped-folder"></a>Alterando o local de implantação de uma pasta mapeada  
 Por padrão, pastas mapeadas são adicionadas a locais específicos em relação o caminho de instalação raiz do SharePoint, que indica o token {SharePointRoot}. No entanto, você pode alterar esse local, alterando o **local de implantação** propriedade da pasta mapeada. Cada pasta mapeada tem seu próprio **local de implantação** propriedade.  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Para alterar o local de implantação de uma pasta mapeada  
  
1.  No projeto que você criou anteriormente, escolha uma pasta mapeada.  
  
2.  No **propriedades** janela, escolha o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "elipse ASP.NET Mobile Designer")) botão o **implantação local** propriedade.  
  
3.  No **adicionar pasta do SharePoint mapeado** caixa de diálogo, navegue até a pasta na qual você deseja que a pasta mapeada para o ponto.  
  
4.  Escolha o nó e, em seguida, escolha o **Okey** botão.  
  
## <a name="renaming-or-removing-mapped-folders"></a>Renomear ou remover pastas mapeadas  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>Para renomear ou remover uma pasta mapeada  
  
1.  No projeto que você criou anteriormente, escolha uma pasta mapeada.  
  
2.  Para renomear a pasta mapeada, abra o menu de atalho, escolha **Renomear**, digite o novo nome e, em seguida, escolha a tecla Enter.  
  
     Como alternativa, você pode escolher a pasta mapeada que você deseja renomear, abra o **propriedades** janela e, em seguida, defina o valor da **nome da pasta** propriedade para o novo nome.  
  
3.  Para remover uma pasta mapeada do projeto, abra o menu de atalho, escolha **excluir**e, em seguida, escolha o **Okey** botão na caixa de diálogo para confirmar a remoção.  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  